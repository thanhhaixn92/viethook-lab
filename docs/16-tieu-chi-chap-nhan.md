# 16. Tiêu chí chấp nhận (cho đội làm app sau này)

Repo này **không chứa app**. Khi triển khai sản phẩm, dùng checklist dưới đây. Không tick = chưa phải VietHook Lab.

## P0 — Tone Engine

- [ ] Tách đúng tiếng của câu có dấu, kể cả từ ghép 2 tiếng
- [ ] 6 thanh gán từ dấu chữ (không đoán)
- [ ] Chip Tone Map: orthography + tên thanh + màu
- [ ] Bigram similar / oblique / contrary, không chấm ±1 từng chữ
- [ ] Fixture `đi → về`: mode An toàn không để “về” cao hơn “đi”
- [ ] Cảnh báo đỏ chỉ ra **đúng chữ** + ≥ 1 gợi ý sửa tiếng Việt
- [ ] User override “phá luật có chủ đích” ghi `composition_notes`

## P0 — Melody Lab

- [ ] Sinh ≥ 3 variant từ cùng brief
- [ ] Thanh tham gia lúc search, không phải filter sau
- [ ] Playback synth loop + count-in
- [ ] MIDI 2 track mở được Ableton/Logic/FL, tempo đúng
- [ ] Tone lock / kéo nốt trên grid

## P0 — Score & Canvas

- [ ] 7 tiêu chí, trọng số đúng bảng v1
- [ ] Copy giải thích không chứa “error code”
- [ ] Canvas: seed text + BPM + key + genre + độ dài là đủ để sinh

## P1

- [ ] Link share nghe 15s
- [ ] Like + comment
- [ ] Hook Report HTML/PDF
- [ ] 3 style pack: ballad, R&B, TikTok

## Phi chức năng

- [ ] Flow 1 hoàn tất < 8 phút với user không biết nhạc lý (test 5 người)
- [ ] Mobile: 3 vùng editor không tràn ngang (chip + roll vuốt)
- [ ] Không vocal clone
- [ ] Terms dữ liệu trước public
