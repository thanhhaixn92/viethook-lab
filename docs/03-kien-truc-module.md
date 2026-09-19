# 03. Kiến trúc 6 module

```text
VietHook Lab
│
├── 1. Hook Canvas     nhập ý tưởng, lời, genre, mood, BPM, key
├── 2. Tone Engine     phân tích thanh điệu + ngữ điệu lời
├── 3. Melody Lab      sinh và chỉnh giai điệu theo ràng buộc
├── 4. Hook Score      chấm dễ nhớ, khớp lời, singability, viral
├── 5. A/B Lab         so sánh biến thể, thu phản hồi người nghe
└── 6. Learn           bài học ngắn, challenge, clinic, corpus
```

Mỗi module có **input / output / không làm gì**. Tránh biến Melody Lab thành DAW, tránh biến Learn thành LMS đầy đủ ở MVP.

---

## 1. Hook Canvas

**Làm:** thu thập ý định sáng tác. Người dùng bắt đầu từ câu nói.

Input: chủ đề, từ khóa, genre, BPM, key/mode, độ dài hook, mức táo bạo, có ngũ cung hay không.

Output: brief nội bộ (`HookBrief`) đưa sang Tone Engine và Melody Lab.

**Không làm:** sinh MIDI, chấm điểm chi tiết, A/B.

Chi tiết: [04-hook-canvas.md](04-hook-canvas.md).

---

## 2. Tone Engine

**Làm:** tách âm tiết, gán 6 thanh, nguyên âm, coda, trọng nghĩa, mật độ/nhịp, cảnh báo mất dấu.

Output: `ToneMap` — mảng chip âm tiết + cờ xanh/vàng/đỏ + gợi ý sửa lời *trước cả khi có melody*.

Khi đã có melody: so khớp bigram thanh ↔ bigram pitch (similar / oblique / contrary).

**Không làm:** quyết định nốt cụ thể.

Chi tiết: [05-tone-engine.md](05-tone-engine.md).

---

## 3. Melody Lab

**Làm:** tìm melody tối ưu hóa Hook Score dưới ràng buộc của Tone Engine + scale + chord + BPM + style pack.

Sáu chế độ sinh: An toàn, Bắt tai, Cảm xúc, TikTok, Dân tộc đương đại, Rap/R&B.

Công cụ: piano roll đơn giản, Tone lock / Lyric lock / Hook freeze.

**Không làm:** phối full band, master, clone vocal.

Chi tiết: [06-melody-lab.md](06-melody-lab.md), [10-thuat-toan-sinh-giai-dieu.md](10-thuat-toan-sinh-giai-dieu.md).

---

## 4. Hook Score

**Làm:** chấm 0–100 với 7 tiêu chí có trọng số, giải thích tiếng Việt, gợi ý sửa.

**Không làm:** tuyên bố “hit chắc” hoặc “đạo nhạc”. Similarity check (nếu có) chỉ là cảnh báo motif, không kết luận pháp lý.

Chi tiết: [07-hook-score.md](07-hook-score.md).

---

## 5. A/B & Listening Lab

**Làm:** link ` /h/{id} `, nghe 15 giây, bầu mù, đo nghe lại, comment ngắn.

**Không làm:** mạng xã hội đầy đủ, feed, inbox.

Chi tiết: [08-ab-listening-lab.md](08-ab-listening-lab.md).

---

## 6. Learn & Community

**Làm:** micro-lesson 2–3 phút gắn đúng lỗi vừa gặp; challenge tuần; clinic có rubric.

**Không làm:** thay thế khóa học 6 tháng.

Chi tiết: [09-hoc-tap-cong-dong.md](09-hoc-tap-cong-dong.md).

---

## Luồng dữ liệu

```text
HookBrief ──► ToneMap ──► MelodyCandidate[] ──► ScoredHook[]
                                │                      │
                                └──── editor tweaks ───┘
                                           │
                                           ▼
                                    ShareLink / MIDI / Report
                                           │
                                           ▼
                                    ListeningVotes ──► corpus features
```

Mọi thực thể có `id` ổn định. Variant là con của một `HookProject`. Không ghi đè bản gốc khi sinh biến thể.

---

## Ranh giới kỹ thuật (MVP)

| Lớp | Công nghệ gợi ý | Ghi chú |
|---|---|---|
| NLP tiếng Việt | underthesea (tokenize, normalize) + rule tách âm tiết/thanh | Thanh lấy từ dấu chữ viết, không cần ASR |
| Phonology | bảng grapheme → initial / vowel / coda / tone | Xem lexicon |
| Sinh melody | rule-based + beam search trên scale/chord | Chưa cần transformer |
| Playback | synth lead (Web Audio / Tone.js) | Không deepfake vocal |
| Export | MIDI type 1, 1 track melody + 1 track chord | Quantize theo grid BPM |
| Lưu trữ | project JSON; corpus chỉ *feature*, không full audio copyrighted | |

---

## Style pack (gói phong cách)

Mỗi pack là cấu hình, không phải model riêng:

| Pack | Chord template | Rhythm | Contour | Vocab gợi ý |
|---|---|---|---|---|
| Vpop ballad | I–V–vi–IV chậm | straight, nhiều nốt trắng | quãng rộng hơn, peak muộn | mưa, nhớ, thôi, đừng |
| Dance-pop | I–vi–IV–V | four-on-floor, syllable dày | motif 2 ô lặp | đêm, cháy, theo |
| R&B Việt | ii–V–I / minor 7 | swing nhẹ, syncopation | luyến hỏi/ngã | buông, gần, chậm |
| Folk-pop Bắc | pentatonic Cung/Vũ | vừa phải | láy, ngân | chiều, đò, làng |
| Rap chant | 1–2 chord loop | 16th, rest có chủ đích | ít nhảy quãng | điệp từ khóa |
| TikTok 15s | 2 chord | hook 1 câu + rest | lặp mạnh, peak sớm | mệnh lệnh ngắn |

Pack “dân tộc đương đại” dùng ngũ cung Cung–Thương–Giốc–Chủy–Vũ (Hò–Xự–Xang–Xê–Cống) nhưng vẫn cho chord pop hiện đại ở nền.
