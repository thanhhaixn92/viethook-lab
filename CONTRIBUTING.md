# Đóng góp vào sổ tay VietHook Lab

Repo này **chỉ chứa tài liệu Markdown**. Không gửi pull request mã nguồn ứng dụng vào đây.

## Nguyên tắc viết

1. **Tiếng Việt là ngôn ngữ gốc.** Thuật ngữ nhạc lý / NLP giữ song ngữ lần đầu xuất hiện, ví dụ: *thanh hỏi (hỏi, dipping tone)*.
2. **Cụ thể hơn trừu tượng.** Mỗi quy tắc cần 1 ví dụ câu hát tiếng Việt.
3. **Không tuyệt đối hóa thanh điệu.** Pop được phép phá luật; phải ghi *tradeoff* và hệ quả mất dấu.
4. **Không dán lời/audio có bản quyền.** Ví dụ phải tự viết hoặc public domain.
5. **Phân biệt heuristic và bằng chứng.** Khi trích Kirby & Ladd (2016) hoặc corpus, ghi nguồn. Khi là quy tắc sản phẩm, ghi “heuristic VietHook Lab”.
6. **Không công thức ±1 độc lập từng chữ.** Thanh phải xét theo *bigram / similar motion*, beat, duration, nguyên âm, phụ âm cuối.

## Cấu trúc file

```text
docs/       mô tả sản phẩm, kỹ thuật, kinh doanh
guides/     hướng dẫn thực hành theo vai trò
examples/   phiên dùng mẫu + checklist
research/   tóm tắt học thuật và cạnh tranh
```

Một file = một chủ đề. Tiêu đề H1 duy nhất. Mục lục ngắn nếu file > 400 dòng.

## Cách đề xuất thay đổi

1. Mở issue mô tả khoảng trống hoặc sai sót (ví dụ: “thiếu heuristic thanh ngã ở nốt cao kéo dài”).
2. Sửa file hiện có thay vì tạo file song song.
3. Pull request: tóm tắt *thay đổi hành vi sản phẩm* hoặc *thay đổi rubric*, không chỉ “update docs”.

## Rubric khi thêm quy tắc mới

Mỗi quy tắc Tone Engine / Hook Score cần đủ 4 phần:

| Phần | Câu hỏi |
|---|---|
| Điều kiện | Khi nào áp dụng? |
| Hành vi mặc định | Hệ thống làm gì? |
| Cảnh báo | Xanh / vàng / đỏ? |
| Gợi ý sửa | Đổi chữ, luyến, rút trường độ, dịch cao điểm… |

## Thuật ngữ bắt buộc giữ ổn định

Dùng đúng các tên này, không đổi lung tung:

- Tone Map, Tone Engine, Tone Fit
- Hook Canvas, Melody Lab, Hook Score
- A/B Lab, Listening Lab
- Tone lock, Lyric lock, Hook freeze
- similar / oblique / contrary motion
- mất dấu, ngân, luyến, láy, melisma

Xem [docs/20-thuat-ngu.md](docs/20-thuat-ngu.md).
