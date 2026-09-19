# 07. Hook Score

Mỗi hook có điểm tổng 0–100 và 7 điểm thành phần. Rubric **minh bạch**: user thấy trọng số, lý do, cách tăng điểm.

Score không phải tiên tri hit. Score là **checklist kỹ thuật + tai nghe có cấu trúc**.

---

## Trọng số

| Tiêu chí | Trọng số | Ý nghĩa |
|---|---:|---|
| Tone Fit | 25% | Giai điệu khớp thanh điệu tiếng Việt |
| Memorability | 20% | Lặp, motif, đối xứng, độ dài vừa |
| Singability | 15% | Quãng, nguyên âm, phụ âm, hơi thở |
| Lyrical Clarity | 10% | Nghĩa rõ, từ khóa mạnh, ít rác |
| Groove / Rhythm | 10% | Nhịp lời cuốn, rest đúng chỗ |
| Emotional Peak | 10% | Cao điểm rõ, rơi vào chữ đáng |
| Viral Snippet | 10% | Cắt 5–15 giây vẫn thành câu |

Tổng = Σ (điểm_tiêu_chí × trọng_số). Mỗi tiêu chí 0–100.

---

## Cách chấm (heuristic MVP, rule-based)

### Tone Fit (25%)

Bắt đầu 100, trừ:

| Sự kiện | Trừ (từ khóa) | Trừ (chữ thường) |
|---|---:|---:|
| Contrary motion | 18 | 8 |
| Huyền đi lên + sustain > 1 beat | 14 | 6 |
| Hỏi/ngã nốt cao dài không luyến | 16 | 8 |
| Nặng sustain > 1 beat ở pitch cao | 12 | 6 |
| Sắc đi xuống ở downbeat | 10 | 4 |

Sàn 0. Cộng tối đa +8 nếu similar motion ≥ 85% bigram.

### Memorability (20%)

Cộng khi:

- Motif lặp 2–3 lần (pitch class sequence n-gram)
- Cấu trúc A–A′–B–A″ hoặc chant lặp từ khóa ≥ 2
- Peak nằm 60–80% thời lượng
- Range 5–9 semitone
- Có rest ≥ 1 beat trước punch

Trừ khi: câu 2 ≥ 13 âm tiết trên 4 nhịp; không lặp gì; range < 3 semitone (bằng phẳng) hoặc > 12 (khó nhớ).

### Singability (15%)

Cộng: nốt cao nhất rơi vào nguyên âm mở; coda mũi ở sustain; leap lớn chỉ 1 lần.

Trừ: coda tắc ở nốt dài; 2 leap ≥ 7 semitone liên tiếp; câu không có chỗ thở 4 nhịp.

### Lyrical Clarity (10%)

- Có đúng keyword user yêu cầu
- 1 ý chính / 1 hook
- Không nhồi 3 hình ảnh khác nhau
- Từ chức năng không chiếm peak

### Groove (10%)

- Syncopation vừa genre (R&B cần; ballad không nhồi 16th)
- Không dồn 4 tiếng vào beat 1 rồi trống beat 2–3 vô nghĩa
- Onset syllable khớp grid ± 1/16

### Emotional Peak (10%)

- Tồn tại 1 nốt/cụm cao nhất hoặc dài nhất
- Peak trùng từ khóa cảm xúc
- Sau peak có hạ (không cao mãi)

### Viral Snippet (10%)

- Tồn tại cửa sổ 15s (hoặc 4 nhịp) tự chứa: từ khóa + motif + rest
- Câu độc lập nghĩa (không cần verse để hiểu)
- Có “hook trong hook”: 3–6 tiếng lặp được

---

## Giọng giải thích (bắt buộc)

Không in “Tone Fit = 72”. Phải in tiếng người.

```text
Tổng điểm: 78/100

Điểm mạnh:
- Từ khóa “buông” lặp 2 lần, dễ nhớ.
- Nguyên âm mở ở cuối câu giúp ngân tốt.
- Cao điểm rơi vào chữ “nhớ”, hợp cảm xúc.

Cần cải thiện:
- “mình” thanh huyền nhưng đang đi lên mạnh, dễ mất dấu nhẹ.
- Câu thứ 2 có 13 âm tiết, hơi dài cho hook 4 nhịp.
- Quãng C4→A4 đang rơi vào chữ không quan trọng.
  Có thể chuyển cao điểm sang chữ “đau”.

Gợi ý nhanh:
- Rút gọn: “Thôi buông tay, lòng chưa buông”
- Dịch cao điểm sang chữ “buông”
- Thêm nghỉ 1 beat trước chữ “nhớ”
```

Mỗi gợi ý là action: [Áp dụng] gắn vào editor.

---

## Band điểm (để UI không chỉ là số)

| Band | Điểm | Nhãn |
|---|---|---|
| 90–100 | Sẵn sàng test tai người nghe | Xuất sắc kỹ thuật |
| 75–89 | Đáng giữ, còn 1–2 điểm đỏ | Tốt |
| 60–74 | Có nền, cần sửa thanh hoặc dài | Đạt |
| 40–59 | Dễ gượng hoặc khó nhớ | Cần làm lại |
| 0–39 | Contrary nặng / không hát được | Gỡ cấu trúc |

Nhãn **không** dùng chữ “hit”, “viral chắc”. Viral Snippet chỉ nói *tiềm năng cắt clip*.

---

## Calibrate sau này

Khi có A/B Lab:

- Hồi quy điểm thành phần với *re-listen rate* và *sing-back rate*
- Không thay trọng số im lặng; version rubric (`hook_score_v1`, `v2`)
- Human override của giảng viên lưu riêng, không đè rule mặc định
