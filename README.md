# VietHook Lab

**Phòng thí nghiệm hook tiếng Việt**

> Biến câu nói tiếng Việt thành giai điệu hook dễ nhớ, đúng thanh điệu và có khả năng lan truyền.

Đây là **sổ tay sản phẩm và hướng dẫn chuyên sâu** — không phải mã nguồn ứng dụng. Bộ tài liệu này dùng để:

- Định vị sản phẩm *tone-aware songwriting copilot* cho nhạc Việt
- Hướng dẫn nhạc sĩ, producer, giảng viên và kỹ sư triển khai
- Chuẩn hóa rubric Hook Score, Tone Map và thuật toán sinh giai điệu
- Làm tài liệu nội bộ, giáo trình, hoặc brief cho đội phát triển

**Định vị một câu:** VietHook Lab giúp người sáng tác **viết, kiểm tra, tối ưu và thử nghiệm hook giai điệu tiếng Việt** dựa trên thanh điệu, ngữ nghĩa, nhịp lời, nguyên âm, cấu trúc pop và phản hồi người nghe thật.

---

## Đây không phải AI tạo nhạc đại trà

Trung tâm không phải “bấm nút ra bài hát”. Trung tâm là:

- lời tiếng Việt
- thanh điệu
- ngữ nghĩa
- nhịp câu
- cảm xúc
- khả năng hát lại
- phản hồi người nghe

AI chỉ gợi ý. Người viết vẫn quyết định.

Câu hỏi sản phẩm phải trả lời được:

1. Câu hook này có bị **mất dấu** không?
2. Chữ nào nên đặt ở **cao điểm** giai điệu?
3. Nguyên âm nào **dễ ngân** hơn?
4. Câu này có đủ ngắn để thành hook **15 giây** không?
5. Nên **lặp từ khóa** ở đâu?
6. Giai điệu có quá bằng phẳng hay quá nhảy quãng?
7. Biến thể nào dễ nhớ hơn: an toàn, bắt tai, dân tộc, TikTok, ballad?
8. Làm sao sửa câu hát mà **không phá nghĩa**?

---

## Mục lục sổ tay

### Sản phẩm

| File | Nội dung |
|---|---|
| [docs/01-tam-nhin-san-pham.md](docs/01-tam-nhin-san-pham.md) | Vấn đề, khoảng trống thị trường, giá trị cốt lõi |
| [docs/02-nguoi-dung-va-vi-the.md](docs/02-nguoi-dung-va-vi-the.md) | Persona, JTBD, khác biệt cạnh tranh |
| [docs/03-kien-truc-module.md](docs/03-kien-truc-module.md) | 6 module chính và ranh giới trách nhiệm |
| [docs/04-hook-canvas.md](docs/04-hook-canvas.md) | Nơi bắt đầu mọi câu hook |
| [docs/05-tone-engine.md](docs/05-tone-engine.md) | Trái tim khác biệt: thanh điệu ↔ giai điệu |
| [docs/06-melody-lab.md](docs/06-melody-lab.md) | Sinh và chỉnh giai điệu có ràng buộc |
| [docs/07-hook-score.md](docs/07-hook-score.md) | Rubric 0–100 minh bạch |
| [docs/08-ab-listening-lab.md](docs/08-ab-listening-lab.md) | A/B test với người nghe thật |
| [docs/09-hoc-tap-cong-dong.md](docs/09-hoc-tap-cong-dong.md) | Micro-lesson, challenge, feedback clinic |

### Kỹ thuật & dữ liệu

| File | Nội dung |
|---|---|
| [docs/10-thuat-toan-sinh-giai-dieu.md](docs/10-thuat-toan-sinh-giai-dieu.md) | Tone-aware melody generation (moat kỹ thuật) |
| [docs/11-mo-hinh-du-lieu.md](docs/11-mo-hinh-du-lieu.md) | Lexicon, corpus hook, schema JSON |
| [docs/12-giao-dien-va-user-flow.md](docs/12-giao-dien-va-user-flow.md) | UI spec, 3 user flow mẫu |

### Lộ trình, kinh doanh, pháp lý

| File | Nội dung |
|---|---|
| [docs/13-mvp-va-lo-trinh.md](docs/13-mvp-va-lo-trinh.md) | MVP 90 ngày + lộ trình 12 tháng |
| [docs/14-kinh-doanh-va-kpi.md](docs/14-kinh-doanh-va-kpi.md) | Freemium, giá, KPI |
| [docs/15-phap-ly-dao-duc.md](docs/15-phap-ly-dao-duc.md) | Bản quyền, dữ liệu, AI vocal, rủi ro |
| [docs/19-pitch-noi-bo.md](docs/19-pitch-noi-bo.md) | Bản pitch ngắn để trình bày / gọi vốn |

### Hướng dẫn thực hành

| File | Dành cho |
|---|---|
| [guides/viet-hook-tieng-viet.md](guides/viet-hook-tieng-viet.md) | Nhạc sĩ / singer-songwriter |
| [guides/producer-daw.md](guides/producer-daw.md) | Producer / beatmaker |
| [guides/giao-vien-nhac-vien.md](guides/giao-vien-nhac-vien.md) | Giảng viên, lớp sáng tác |
| [guides/tone-map-howto.md](guides/tone-map-howto.md) | Cách đọc Tone Map và sửa mất dấu |
| [docs/20-thuat-ngu.md](docs/20-thuat-ngu.md) | Glossary |

### Ví dụ & nghiên cứu

| File | Nội dung |
|---|---|
| [examples/phien-buong-tay.md](examples/phien-buong-tay.md) | Session R&B: “buông tay nhưng vẫn nhớ” |
| [examples/phien-troi-mua.md](examples/phien-troi-mua.md) | Session ballad: “trời mưa / đừng quay lại” |
| [examples/checklist-hook.md](examples/checklist-hook.md) | Checklist chấm hook trước khi export |
| [research/tone-melody-literature.md](research/tone-melody-literature.md) | Kirby & Ladd, tân nhạc, dân ca |
| [research/canh-tranh.md](research/canh-tranh.md) | Hooktheory, AI music, khóa học VN |

---

## Vòng lặp cốt lõi (MVP)

```text
Nhập lời / ý tưởng
        ↓
Tách âm tiết + gán thanh điệu
        ↓
Tone Map (xanh / vàng / đỏ)
        ↓
Sinh 3–5 biến thể giai điệu có ràng buộc
        ↓
Hook Score + giải thích tiếng Việt
        ↓
Chỉnh nốt → nghe thử → export MIDI / chia sẻ
```

Sáu module đầy đủ:

```text
VietHook Lab
├── 1. Hook Canvas
├── 2. Tone Engine
├── 3. Melody Lab
├── 4. Hook Score
├── 5. A/B & Listening Lab
└── 6. Learn & Community
```

---

## Nguyên tắc thiết kế (không thỏa hiệp)

1. **Lời đi trước nốt.** Người dùng bắt đầu từ câu nói, không từ piano roll.
2. **Thanh điệu là ràng buộc sinh, không phải lớp sơn sau.** Không được tạo melody rồi dán lời.
3. **Giải thích được.** Mọi cảnh báo đỏ phải nói được *chữ nào, vì sao, sửa thế nào*.
4. **Phá luật có chủ đích.** Override luôn được phép, nhưng phải ghi chú.
5. **Không scrape lời/audio bản quyền** để train khi không có cơ sở pháp lý.
6. **Không clone giọng nghệ sĩ.** Demo vocal chỉ dùng giọng tổng hợp trung tính, gắn nhãn AI.

---

## Đọc nhanh theo vai trò

| Bạn là | Đọc trước |
|---|---|
| Founder / product | `01`, `02`, `13`, `14`, `19` |
| Nhạc sĩ | `guides/viet-hook-tieng-viet.md`, `05`, `07`, `examples/` |
| Producer | `guides/producer-daw.md`, `06`, `12` |
| Giảng viên | `guides/giao-vien-nhac-vien.md`, `07`, `09` |
| Kỹ sư / ML | `05`, `10`, `11`, `research/` |
| Pháp chế | `15` |

---

## Đóng góp

Xem [CONTRIBUTING.md](CONTRIBUTING.md). Tài liệu dùng tiếng Việt làm ngôn ngữ gốc; thuật ngữ nhạc lý / NLP giữ song ngữ khi cần.

## Giấy phép

Nội dung sổ tay: [CC BY 4.0](LICENSE). Tên sản phẩm **VietHook Lab** giữ cho dự án này.

## Nguồn nghiên cứu chính

- Kirby, J. & Ladd, D. R. (2016). *Tone-melody correspondence in Vietnamese popular song.* Tonal Aspects of Languages.
- Kirby & Ladd dataset: [Edinburgh DataShare](https://doi.org/10.7488/ds/1434)
- Văn hóa Nghệ thuật: tương quan thanh điệu — cao độ trong ca khúc nghệ thuật Việt Nam
- Hệ thống ngũ cung Việt: Cung / Thương / Giốc / Chủy / Vũ; Hò–Xự–Xang–Xê–Cống
