# 08. A/B & Listening Lab

Điểm khác biệt so với khóa học: hook được **thử như product**, không chỉ “thầy khen”.

MVP có thể chỉ like/comment trên link demo. A/B đầy đủ là Phase sau beta.

---

## Mục tiêu

Trong 10 người nghe, biết biến thể nào:

- dễ nhớ nhất
- muốn nghe lại
- hợp cảm xúc nhất
- dễ hát theo nhất
- đáng làm video ngắn nhất

Không hỏi “bài nào hay hơn” — quá mơ hồ.

---

## Link chia sẻ

```text
viethooklab.app/h/abc123
```

Landing nghe:

1. 1 câu ngữ cảnh (không spoiler “bản B táo bạo”)
2. Play 15 giây — không seek nếu chế độ blind
3. Bắt buộc chọn 1 nhãn trước khi comment
4. Optional: nghe lần 2 (đếm re-listen)

Metadata ẩn với listener: tên tác giả, nhãn mode (An toàn / TikTok…), điểm số.

---

## Blind test

- Ẩn tên tác giả, ẩn thứ tự biến thể (randomize A/B/C)
- Chỉ 15 giây
- Nâng cao: sau 30 giây, yêu cầu *gõ lại câu nhớ được* hoặc hát vào mic (web)

Sing-back rate = tỷ lệ nhớ đúng ≥ 60% từ khóa. Đây là gold label cho Memorability.

---

## So sánh biến thể

Bảng cho tác giả (không cho listener):

| Trục | A | B | C |
|---|---|---|---|
| Lời | … | … | … |
| Contour | 0 2 4 7 4 | 0 0 7 0 | … |
| Peak syllable | nhớ | buông | mưa |
| Tone Fit | 90 | 82 | 88 |
| Vote “dễ nhớ” | 12 | 31 | 9 |
| Re-listen | 0.22 | 0.41 | 0.18 |

Khi B thắng vote nhưng Tone Fit thấp: cảnh báo “tai thích, thanh đang rủi ro — cân nhắc sửa chữ trước khi thu”.

---

## Đo lường

| Metric | Định nghĩa |
|---|---|
| completion_rate | nghe hết 15s / số mở link |
| re_listen_rate | play ≥ 2 / số người nghe hết |
| vote_share | % chọn biến thể i theo từng nhãn |
| singback_rate | nhớ đúng keyword (nâng cao) |
| comment_useful | comment có ≥ 1 ý cụ thể (moderation heuristic) |

Không track danh tính listener nếu họ không đăng nhập. Cookie chỉ để chặn vote kép.

---

## Phạm vi MVP vs sau

| MVP | Sau |
|---|---|
| 1 link, 1–3 variant, like + 1 comment box | Blind, nhiều nhãn, sing-back |
| Không bắt login để nghe | Login để vote class / label |
| Không mic | Mic web, consent rõ |
