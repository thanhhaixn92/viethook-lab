# 10. Thuật toán: Tone-aware melody generation

Đây là **moat kỹ thuật**. Model không được tự do tạo melody rồi gắn lời.

---

## Đầu vào

Lời:

```text
L = [s₁, s₂, ..., sₙ]
```

Mỗi `sᵢ`: thanh `tᵢ`, nguyên âm `vᵢ`, coda `cᵢ`, trọng nghĩa `wᵢ`, vị trí nhịp `rᵢ`.

Melody ứng viên:

```text
M = [m₁, m₂, ..., mₙ]
```

Mỗi `mᵢ`: pitch (MIDI), duration, optional grace/slide (nhiều nốt con), chord tại thời điểm đó.

Một âm tiết hỏi/ngã **được phép** 2 nốt (dip). Âm tiết ngang thường 1 nốt.

---

## Hàm mục tiêu

```text
Score(M) =
    α ToneFit(M, L)
  + β Memorability(M)
  + γ Singability(M, L)
  + δ Groove(M, rhythm)
  + ε ChordFit(M, harmony)
  + ζ EmotionalPeak(M, L)
  − penalties
```

Gợi ý hệ số MVP (chuẩn hóa 0–1 trước khi nhân):

| Hệ số | Mode An toàn | Bắt tai | Cảm xúc | TikTok | Dân tộc | Rap/R&B |
|---|---:|---:|---:|---:|---:|---:|
| α ToneFit | 0.40 | 0.28 | 0.25 | 0.22 | 0.30 | 0.20 |
| β Memorability | 0.20 | 0.28 | 0.15 | 0.30 | 0.15 | 0.22 |
| γ Singability | 0.20 | 0.12 | 0.18 | 0.10 | 0.15 | 0.15 |
| δ Groove | 0.05 | 0.10 | 0.05 | 0.12 | 0.08 | 0.25 |
| ε ChordFit | 0.10 | 0.12 | 0.12 | 0.08 | 0.12 | 0.08 |
| ζ Peak | 0.05 | 0.10 | 0.25 | 0.18 | 0.20 | 0.10 |

Penalties: contrary trên keyword, leap vào stopword, coda tắc sustain, out-of-range, quá dày.

---

## ToneFit

Không tuyệt đối hóa: pop được phá luật có chủ đích. Cần mô hình **xu hướng tự nhiên**.

1. Gán mỗi thanh một *offset class*: High / Mid / Low / Extra-low (bảng Kirby & Ladd).
2. Bigram thanh → hướng mong đợi: up / down / level.
3. Bigram pitch (so sánh MIDI note của nốt chính, bỏ grace) → up / down / level.
4. similar = cùng hướng; oblique = một bên level; contrary = ngược.

```text
ToneFit ≈
    0.55 * similar_ratio
  + 0.25 * (1 - contrary_ratio_on_keywords)
  + 0.20 * intra_syllable_contour_fit
```

`intra_syllable_contour_fit`: hỏi nên có dip; ngã nên có gãy/nhấn; nặng duration ngắn.

### Mapping nội-âm-tiết (gợi ý nốt con)

| Thanh | Pattern nốt con (relative) |
|---|---|
| ngang | 0 |
| huyền | 0 hoặc 0 → −1 |
| sắc | 0 → +1 hoặc đích đã cao hơn trái |
| hỏi | −1 → 0 hoặc 0 → −2 → 0 |
| ngã | 0 → +1 với glottal-like rest rất ngắn / grace |
| nặng | 0 (short) |

Đây là *gợi ý articulation*, không phải bắt buộc MIDI thật 3 nốt mọi chỗ.

---

## Memorability

Điểm cao khi:

- Motif lặp 2–3 lần (khoảng pitch class, transpose được)
- Đối xứng A–A′–B–A″
- Keyword lặp
- Peak ở 60–80% câu
- Range 5–9 semitone
- Rest hợp lý
- Cắt được 1–2 câu 15 giây

Novelty penalty: nếu contour 4 nốt trùng quá nhiều variant vừa sinh → trừ để tránh 5 bản na ná.

---

## Singability

Điểm cao khi:

- Nốt cao rơi vào nguyên âm mở: a, o, ơ, ê…
- Ít cụm phụ âm tắc ở chữ ngân
- Leap lớn chỉ ở chữ cần kịch tính
- Có chỗ thở
- Hum được (contour rõ khi tắt lời)

---

## ChordFit

Nốt chính của âm tiết trên beat mạnh nên là chord tone (1, 3, 5, 7 tùy jazz). Passing note trên offbeat được phép. Tension 9/11 không đặt ở syllable nặng + sustain.

---

## Sinh melody — MVP

**Rule-based + beam search**, không cần GPU.

### Không gian nốt

Với mỗi syllable i, ứng viên pitch ∈ scale ∩ tessitura ∩ (chord tones nếu downbeat).

Grace cho hỏi/ngã được thêm *sau* khi chọn nốt chính.

### Beam search

```text
beam_size = 24 (an toàn) / 48 (bắt tai)
Với i = 1..n:
  với mỗi partial trong beam:
    thử pitch ứng viên
    cộng heuristic cục bộ:
      - similar motion so với syllable i-1
      - khoảng cách tới chord
      - proximity motif (nếu i lặp nhịp 1–2)
      - peak plan (chưa được phép peak quá sớm trừ TikTok)
  giữ top-k
Rerank full sequence bằng Score(M)
Lấy 3–5 bản đa dạng: clustering contour, 1 bản / cluster
```

Random seed theo `safety` và `mode` để tái lập được (`generator_version` + seed lưu trong project).

### Constraint solver nhẹ (tùy chọn)

Có thể mô hình như CSP: biến = pitch i, domain = scale, constraint contrary-forbidden trên keyword. Dùng backtracking nếu n ≤ 16.

---

## Version sau

- Music transformer / diffusion **có condition**: tone bigram, vowel openness, keyword mask
- RL tinh chỉnh policy để tối ưu Hook Score + vote A/B
- Fine-tune trên corpus user-consented / public domain / licensed — **không** scrape hit Vpop trái phép

Condition vector tối thiểu:

```text
[tone_id, openness, coda_type, is_keyword, beat_strength, chord_pcs...]
```

---

## Kiểm thử thuật toán (bắt buộc có fixture)

Bộ test không regression:

1. “đi về” (ngang–huyền) → pitch “về” không cao hơn “đi”
2. Keyword thanh sắc ở peak → pitch ≥ mọi nốt khác ±1
3. Thanh nặng cuối câu → duration ≤ 1 beat
4. Hỏi ở giữa câu ballad → có grace hoặc 2 nốt
5. Mode An toàn: contrary_ratio < 0.1
6. Mode TikTok: tồn tại cửa sổ 4 nhịp chứa keyword lặp

Fixture lời phải tự viết, không lấy hit.
