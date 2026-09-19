# 19. Pitch nội bộ / gọi vốn (1–2 trang)

## Problem

Người sáng tác nhạc Việt thiếu công cụ giúp viết hook giai điệu **vừa tự nhiên với tiếng Việt, vừa dễ nhớ, vừa có khả năng lan truyền**. Khóa học hiện có dạy hòa âm, phối khí, làm beat hoặc sáng tác chung chung — ít đi sâu vào quan hệ **thanh điệu × ca từ × nhịp lời × melody**.

AI full-song không giải quyết: không chỉnh được đơn vị hook, không giải thích mất dấu, khó đưa MIDI có kiểm soát vào DAW.

## Solution

**VietHook Lab** — webapp tone-aware songwriting copilot:

1. Nhập lời / ý tưởng
2. Phân tích thanh điệu tiếng Việt (Tone Map)
3. Sinh nhiều biến thể hook có ràng buộc
4. Chấm Hook Score (dễ nhớ / khớp lời / dễ hát / cắt 15s)
5. A/B với người nghe thật
6. Export MIDI + Hook Report

## Why now

- Vpop và TikTok âm nhạc Việt cần hook ngắn, dễ nhớ
- AI melody đã đủ rẻ, nhưng **chưa có ràng buộc ngôn ngữ địa phương**
- Chưa có công cụ chuyên sâu cho hook tiếng Việt
- Nghiên cứu tone–melody (Kirby & Ladd 2016, ~77% similar motion) đủ để làm heuristic MVP, không cần đợi dataset hit bản quyền

## Product in one loop

```text
Câu nói → Tone Map → 5 biến thể → Score → Tai người nghe → MIDI
```

## Moat

- Vietnamese tone–melody dataset + lexicon
- Hook scoring rubric gắn A/B
- Community feedback loop
- Giáo dục âm nhạc + workflow producer (MIDI)

Không phải moat: “có GPT viết lời”. Lời chỉ là một lớp.

## Business

Freemium cá nhân (≈ 99–199k VND/tháng) → Pro → Team/Studio → Education license.

## Traction plan (12 tháng)

Beta kín 100–300 → public freemium → challenge tuần → B2B nhạc viện.

KPI 12 tháng: 20–50k registered, 5–10k MAU, conversion 3–5%, D30 25–35%.

## Ask (điền khi dùng)

- Seed / grant: để làm lexicon + MVP generator + 30 phỏng vấn
- Đối tác: 1 nhạc viện + 1 collective producer
- Pháp lý dữ liệu: 1 buổi review terms

## Demo 60 giây

1. Dán: “Thôi thì mình buông, nhưng lòng chưa buông”
2. Chip đỏ/vàng hiện trên chữ huyền đi lên
3. Sinh 3 bản, nghe 8 nhịp
4. Bản bắt tai 86 điểm — export MIDI

Câu chốt:

> Đây không phải AI hát thay bạn. Đây là kính hiển vi cho câu hát tiếng Việt.
