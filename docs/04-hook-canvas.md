# 04. Hook Canvas

Nơi bắt đầu mọi câu hook. Người dùng **không cần bắt đầu từ nốt nhạc**. Họ bắt đầu từ câu nói.

## Mục tiêu màn hình

Trong < 30 giây, thu đủ brief để Tone Engine và Melody Lab chạy được. Không hỏi nhạc lý nếu user chọn “chế độ đơn giản”.

---

## Input

### Bắt buộc

| Trường | Ví dụ | Ghi chú |
|---|---|---|
| Ý tưởng hoặc lời | “Buông tay nhưng vẫn nhớ” | Có thể là câu thô, chưa phải lời hát |
| Độ dài hook | 4 nhịp / 8 nhịp / 15 giây | Mặc định 8 nhịp |

### Khuyến nghị

| Trường | Ví dụ |
|---|---|
| Cảm xúc | nhớ, tiếc, buông, mời gọi, nổi loạn, chữa lành |
| Từ khóa bắt buộc có trong hook | “đêm”, “mưa”, “thôi”, “yêu”, “giấc mơ” |
| Thể loại | ballad, dance-pop, R&B, rap-pop, folk-pop, Vpop, TikTok pop |
| BPM | 72–96 ballad/R&B; 100–128 dance/TikTok |
| Key / mode | Eb major, D minor, A pentatonic… |
| Mức an toàn | quen thuộc / cân bằng / táo bạo |
| Ngũ cung / dân tộc | có / không |

### Ẩn ở chế độ đơn giản

Chord progression, range giọng, mật độ nốt, vị trí cao điểm. Melody Lab tự chọn default theo genre.

Producer mode mở thêm: dán chord kiểu `Am7 | G | F | Em7`, upload MIDI beat, chọn feel (straight / swing / R&B groove).

---

## Output tức thì (trước khi bấm “Sinh giai điệu”)

1. Tách âm tiết + Tone Map sơ bộ của *lời user gõ* (nếu đã là câu hát)
2. 5–10 câu gợi ý lời hook (nếu user mới có ý tưởng)
3. Cảnh báo mật độ: “13 âm tiết / 4 nhịp — hơi dày”
4. Cảnh báo nguyên âm: “câu kết bằng chữ có coda tắc, khó ngân”

Sau khi bấm **Sinh hook giai điệu**:

- 3–5 biến thể melody (tùy gói)
- Hook Score sơ bộ
- Cảnh báo thanh điệu đã gắn melody
- Nút Tinh chỉnh / So sánh / Export

---

## Ví dụ luồng

```text
User nhập:
“Buông tay nhưng vẫn nhớ, style R&B nhẹ, BPM 82, hook 8 nhịp”

Hệ thống gợi ý lời:
“Thôi thì mình buông, nhưng lòng chưa buông…”

Biến thể melody:
1. An toàn, lặp nhiều
2. Quãng nhảy ở chữ “nhớ”
3. Nguyên âm mở ở cuối câu
4. Post-chorus chant 15 giây
5. Pha ngũ cung nhẹ
```

Phiên đầy đủ: [examples/phien-buong-tay.md](../examples/phien-buong-tay.md).

---

## Quy tắc gợi ý lời (heuristic)

Khi user chưa có lời hoàn chỉnh:

1. Giữ từ khóa bắt buộc.
2. Ưu tiên câu 6–10 âm tiết cho 4 nhịp; 10–16 âm tiết cho 8 nhịp.
3. Đặt từ khóa cảm xúc gần vị trí peak mặc định (60–80% độ dài câu).
4. Kết câu bằng nguyên âm mở (`a`, `o`, `ơ`, `ê`, `i` ngân được) nếu genre ballad/R&B.
5. Tránh dồn 3+ thanh hỏi/ngã liên tiếp — khó gán luyến mà không sến.
6. Lặp từ khóa 2 lần nếu Memorability là ưu tiên (TikTok, chant).

Gợi ý lời **không được** copy cụm nổi tiếng. Nếu user dán câu quá giống hit, cảnh báo mềm (xem pháp lý).

---

## Trạng thái Canvas

```json
{
  "project_id": "hk_...",
  "brief": {
    "seed_text": "Buông tay nhưng vẫn nhớ",
    "emotion": ["tiec", "buong"],
    "keywords": ["buông", "nhớ"],
    "genre": "rnb_viet",
    "bpm": 82,
    "key": "C_minor",
    "bars": 8,
    "safety": "balanced",
    "pentatonic": false
  },
  "lyric_candidates": [],
  "selected_lyric": null
}
```

Canvas không lưu MIDI. MIDI thuộc Melody Lab.
