# 12. Giao diện và user flow

## 12.1 Dashboard

- Project gần đây (hook score, genre, ngày)
- Hook score trung bình 7 ngày
- Thử thách tuần
- Gợi ý học cá nhân: “Bạn hay bị mất dấu ở thanh hỏi”
- CTA duy nhất nổi: **Tạo hook mới**

Không nhồi feed xã hội lên trên CTA.

---

## 12.2 Hook Editor (3 vùng)

```text
┌─────────────────────────────────────────────┐
│ Lyrics / Tone Map                           │
│ [Thôi] [thì] [mình] [buông] …               │
├─────────────────────────────────────────────┤
│ Piano roll / Melody contour                 │
│ ●──●──●──●──●                               │
├─────────────────────────────────────────────┤
│ BPM  key  scale  chord  |  Sinh  Score  Export │
└─────────────────────────────────────────────┘
```

Mobile: xếp dọc cùng 3 vùng; piano roll vuốt ngang; chip lời sticky.

Màu Tone Map không chỉ dựa vào đỏ/xanh thuần — kèm icon ↗ ↘ ⤵ cho hướng thanh, để người mù màu vẫn đọc được.

---

## 12.3 Variant comparison

```text
A An toàn     81
B Bắt tai     86
C TikTok      84
D Dân tộc     79
E Ballad peak 88
```

Mỗi card: play, Tone Fit mini-bar, vị trí peak, độ lặp, [Chọn làm bản chính].

So sánh contour: overlay 2 polyline, không waveform phức tạp ở MVP.

---

## 12.4 Hook Report (PDF/HTML)

- Lời + syllables
- Contour (SVG)
- Tone Map
- Điểm + mạnh/yếu + gợi ý
- Chord chart chữ
- Đính MIDI / audio

Dùng để: nộp bài, gửi ca sĩ, gửi producer, pitch label, portfolio.

---

## 12.5 Flow 1 — Có lời, chưa có nhạc

```text
1. Hook Canvas
2. Dán câu / ý tưởng
3. Chọn genre, BPM, key, cảm xúc
4. Tách âm tiết + thanh
5. Xem Tone Map
6. Sinh hook giai điệu
7. 5 biến thể
8. Nghe, chỉnh nốt/nhịp
9. Hook Score
10. Export MIDI hoặc share link
```

## 12.6 Flow 2 — Producer có beat

```text
1. Nhập BPM, key, chord (hoặc MIDI)
2. Từ khóa cảm xúc
3. Gợi ý lời ngắn
4. Sinh melody theo groove
5. Tone Fit
6. Variant chant / post-chorus
7. Export MIDI vào DAW
8. Thu ca sĩ / synth demo
```

## 12.7 Flow 3 — Sinh viên

```text
1. GV giao đề: hook 8 nhịp, chia tay, ballad
2. SV viết lời, xem thanh
3. Nộp 2 biến thể
4. Bạn học bầu mù
5. GV nhận xét trên timeline/chip
6. Lưu portfolio kỹ năng
```

---

## 12.8 Copy UI (giọng)

- Xưng “bạn”. Không xưng “user”.
- Cảnh báo đỏ: cụ thể chữ, không “error 412”.
- Nút chính: **Sinh giai điệu**, **Nghe thử**, **Xuất MIDI**, **Lấy ý kiến**.
- Tránh từ: “algorithm”, “inference”, “model output”. Có thể: “gợi ý”, “máy chấm”, “biến thể”.

Empty state Canvas:

> Dán một câu tiếng Việt. Ví dụ: “Thôi thì mình buông, nhưng lòng chưa buông.”
