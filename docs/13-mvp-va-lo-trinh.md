# 13. MVP và lộ trình

Vòng lặp MVP:

> Nhập lời → Phân tích thanh điệu → Sinh giai điệu → Chấm điểm → Xuất MIDI/audio đơn giản.

Không làm full 6 module cho “đẹp sơ đồ”.

---

## 90 ngày

### Phase 1 — Lời và thanh (tuần 1–3)

- Editor nhập lời
- Tách âm tiết
- Gán thanh, nguyên âm, coda
- Tone Map
- Cảnh báo đỏ/vàng/xanh **chưa cần melody** (mật độ, openness, 3 hỏi liên tiếp)

**Done khi:** dán “Thôi thì mình buông, nhưng lòng chưa buông” ra đúng 8 chip thanh ngang/huyền.

### Phase 2 — Melody có ràng buộc (tuần 4–7)

- BPM, key, scale, chord template
- Sinh 3 biến thể 4 và 8 nhịp
- Chỉnh nốt cơ bản
- Playback synth
- Export MIDI
- Similar/contrary trên bigram

**Done khi:** fixture “đi về” không bao giờ gán “về” cao hơn “đi” ở mode An toàn.

### Phase 3 — Hook Score (tuần 8–10)

- Tone Fit, Memorability, Singability
- Text gợi ý sửa tiếng Việt
- Nút [Áp dụng] cho 1–2 fix-it đơn giản (rút duration, dịch peak)

**Done khi:** cùng 1 lời, variant contrary nặng có điểm Tone Fit thấp hơn variant similar ≥ 15 điểm.

### Phase 4 — Lưu và chia sẻ (tuần 11–13)

- Tài khoản
- Nhiều variant / project
- Link nghe demo
- Like + comment ngắn

**Done khi:** người lạ mở link, nghe, like, không cần hiểu nhạc lý.

---

## Cấm làm ở MVP

- AI giọng hát deepfake / clone nghệ sĩ
- Train trên lyrics/audio bản quyền lớn
- Phối khí đầy đủ, auto-master
- Native mobile app
- Marketplace beat
- Phân tích TikTok (crawl view, sound ID)
- Dialect Bắc–Trung–Nam đầy đủ
- Hum-to-hook
- Similarity “đạo nhạc” công khai

---

## 12 tháng

| Tháng | Việc |
|---|---|
| 1–2 | Phỏng vấn 20–30 nhạc sĩ/producer/SV; lexicon v1; wireframe; rubric; tư vấn pháp lý dữ liệu |
| 3–4 | MVP core (Canvas, Tone Map, generator, synth, MIDI, account) |
| 5–6 | Beta kín 100–300 user; cải Tone Fit; so sánh variant; Hook Report |
| 7–8 | Public beta; landing; freemium; challenge tuần; payment |
| 9–10 | Model có constraint; lyric rewriter; hum-to-hook prototype; style pack |
| 11–12 | Dashboard GV; lớp học; workflow label; API/export; tổng kết corpus |

---

## Tính năng nâng cao (sau MVP)

Xem mô tả đầy đủ trong đề xuất gốc; checklist ngắn:

1. **Hum-to-hook** — mic → contour → gợi ý lời khớp thanh
2. **Lyric rewriter** — giữ melody, đổi chữ đồng nghĩa
3. **Dialect mode** — Bắc / Trung / Nam heuristic
4. **Style pack** — Vpop 2010s, R&B Việt, folk Bắc, vọng cổ đương đại, TikTok 15s
5. **Similarity check** — cảnh báo n-gram, không kết luận đạo
6. **AI vocal demo** — giọng trung tính, watermark, nhãn AI, không deepfake

### Lyric rewriter — ví dụ chuẩn

```text
Hiện tại: “Em rời đi trong mưa”
Vấn đề: “rời” huyền nhưng melody đi lên mạnh
Gợi ý:
- “Em đi trong cơn mưa”
- “Mưa rơi khi em đi”
- “Em bước đi trong mưa”
```

---

## Definition of Done sản phẩm (chung)

Một bản build gọi là dùng được khi:

- [ ] User không biết nhạc lý hoàn tất Flow 1 trong < 8 phút
- [ ] Tone Map đúng trên 50 câu fixture nội bộ
- [ ] MIDI mở được trong Ableton / Logic / FL
- [ ] Mọi cảnh báo đỏ có gợi ý sửa tiếng Việt
- [ ] Không có vocal clone
- [ ] Terms có mục dữ liệu và bản quyền
