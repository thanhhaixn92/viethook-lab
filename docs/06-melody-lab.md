# 06. Melody Lab

Melody Lab **không tạo nhạc ngẫu nhiên**. Nó tạo giai điệu dưới ràng buộc của lời, thanh điệu, scale, chord, BPM, style.

Nguyên tắc vàng:

> Không được sinh melody rồi gắn lời. Thanh điệu phải có mặt trong quá trình tìm nốt.

---

## Ràng buộc đầu vào

| Nhóm | Tham số |
|---|---|
| Lời | danh sách âm tiết đã gán thanh |
| Hòa âm | key, mode/scale, chord/bar |
| Thời gian | BPM, feel (straight, swing, R&B, dance, ballad), số nhịp |
| Phong cách | style pack, mức lặp motif, vị trí cao điểm |
| Giọng | tessitura (mặc định C4–A4 với nữ pop, G3–E4 nam — user đổi được) |
| Mật độ | sparse / medium / dense |
| Cấu trúc | 2 / 4 / 8 nhịp; có post-chorus / chant hay không |

Scale hỗ trợ: major, natural/harmonic minor, pentatonic major/minor, modal (dorian, mixolydian), jazz-pop (thêm 9/13 như passing), folk Việt (ngũ cung Cung/Thương/Giốc/Chủy/Vũ).

---

## Sáu chế độ sinh

| Mode | Ưu tiên | Đặc trưng | Rủi ro |
|---|---|---|---|
| An toàn | Tone Fit, singability | Ít nhảy, lặp bậc 1–3–5, similar motion cao | Dễ nhàm |
| Bắt tai | Memorability + surprise nhẹ | Motif 2 ô, 1 lần nhảy 4–7 semitone đúng từ khóa | Na ná pop |
| Cảm xúc | Emotional peak, range rộng | Peak rõ 60–80%, ballad sustain nguyên âm mở | Khó hát |
| TikTok | Viral snippet | 1 câu, lặp từ khóa, rest trước punch, cắt 15s | Nông nghĩa |
| Dân tộc đương đại | Ngũ cung + láy/ngân | Tránh bán cung; grace; vẫn chord pop | Sến nếu láy nhiều |
| Rap / R&B hook | Groove, chant | Nhiều 16th, ít leap, ad-lib slot | Dễ đều đều |

Default khi user không chọn: map từ genre Canvas.

Số biến thể MVP: **3** (An toàn, Bắt tai, đúng genre). Pro: 5, gồm TikTok + Dân tộc hoặc Cảm xúc.

---

## Công cụ chỉnh

- Piano roll đơn giản: kéo nốt theo grid 1/8 (ballad 1/4).
- Chỉnh trường độ, rest.
- Thêm luyến / slide / grace note (bắt buộc với hỏi/ngã đỏ).
- Đổi chord theo bar.
- Đổi rhythm pattern (push/pull 1/16).

Ba khóa:

| Khóa | Giữ | Đổi |
|---|---|---|
| **Tone lock** | lời + thanh | chỉ melody |
| **Lyric lock** | melody + rhythm | gợi ý đổi lời khớp thanh |
| **Hook freeze** | câu hook chính | biến thể pre/post |

Lyric lock là đường sang tính năng nâng cao “lyric rewriter” (không MVP). MVP chỉ hiện 3–5 câu thay thế.

---

## Playback và export

MVP:

- Synth lead (saw/square nhẹ + pluck chord)
- Đếm 1 bar trước
- Loop hook
- Nút hum (mute lyric visual, chỉ contour) để test “nhớ giai điệu không cần lời”

Export:

| Format | Nội dung |
|---|---|
| MIDI | track 1 melody (velocity theo trọng nghĩa), track 2 chord pad, tempo meta |
| WAV/MP3 demo | synth, không vocal clone |
| JSON | syllables + notes + score — để tái mở project |

Không watermark MIDI ở Pro. Free có marker text `VietHook Lab` ở MIDI lyric event.

---

## Piano roll: quy tắc UX

- Mỗi cột = 1 syllable (không phải 1 beat). Beat hiện ở ruler phía trên.
- Chip lời nằm ngay trên nốt, màu Tone Map.
- Kéo nốt ra ngoài scale: snap về chord tone gần nhất, hoặc giữ nếu user tắt snap.
- Nhảy > 7 semitone: toast vàng “quãng rộng — chỉ nên đặt ở từ khóa”.

Người không biết nhạc lý vẫn chỉnh được vì họ kéo **chữ**, không đọc tên nốt. Tên nốt hiện nhỏ, không bắt buộc.

---

## Chord templates mặc định

| Genre | Tiến trình 4 bar (I = tonic) |
|---|---|
| Ballad Vpop | I – V – vi – IV |
| Dance-pop | I – vi – IV – V |
| R&B | ii7 – V7 – Imaj7 – vi7 |
| Minor emo | i – VI – III – VII |
| Folk pentatonic | I5 – bVII – IV – I5 |
| Chant | i – i – i – i (hoặc i – bVI) |

Producer có thể dán numeral hoặc absolute (`F | C | Dm | Bb`).
