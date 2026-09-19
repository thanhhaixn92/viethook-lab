# 15. Pháp lý, đạo đức và rủi ro

## Dữ liệu

| Được | Không |
|---|---|
| Public domain | Scrape lyrics/audio hit để train |
| User consent, opt-in feature ẩn danh | Lưu full vocal stem im lặng |
| Synthetic | Tái nhận diện listener A/B |
| Hợp đồng trường / label | Đoạn văn bản quyền trong example docs |

Terms phải nói rõ:

- User giữ bản quyền hook họ viết
- License hạn chế cho VietHook Lab: chạy model chấm, hiện demo, thống kê ẩn danh
- Corpus chỉ lưu feature trừ khi user opt-in lời đầy đủ
- Xóa tài khoản = xóa project; feature thống kê có thể giữ dạng irretrievable

---

## AI vocal

Nếu có demo hát:

- Giọng tổng hợp trung tính
- Không clone nghệ sĩ / user nổi tiếng
- Nhãn rõ “AI demo”
- Watermark tùy chọn
- Không deepfake gây nhầm lẫn

MVP: **không vocal AI**. Synth lead là đủ.

---

## Similarity / “đạo nhạc”

Công cụ so n-gram melody/rhythm/lyric **chỉ cảnh báo**:

> Câu melody có 78% tương đồng motif với một hook trong corpus *công khai*.

Không dùng chữ “đạo”, “steal”, “infringe”. Không expose bài có bản quyền. Pháp chế review trước khi bật public.

---

## Rủi ro sản phẩm

| Rủi ro | Mức | Giảm thiểu |
|---|---|---|
| Tone model cứng, giết nghệ thuật | Cao | Override, “phá luật có chủ đích”, mode Creative |
| Melody na ná nhau | Trung | Diversity penalty, style pack, seed |
| Thiếu dữ liệu hook Việt hợp pháp | Cao | User-consented, PD, synthetic, đối tác giáo dục |
| User không hiểu nhạc lý | Trung | Chip lời, kéo chữ, hum-to-hook sau |
| Pháp lý scrape | Cao | Không lưu full copyrighted; terms rõ |
| Khó monetize (nhạy giá) | Trung | Freemium, gói SV, B2B education/label |
| Bị coi là AI nhạc generic | Cao | Tone Map demo 10 giây; rubric; cộng đồng |
| Feedback cộng đồng rác | Trung | Bắt comment theo chip; mod; thưởng nhận xét cụ thể |

---

## An toàn nội dung

- Từ chối tạo lời kích động thù ghét / tình dục trẻ em
- Challenge có quy tắc cộng đồng
- Không biến mic sing-back thành kho giọng để clone

---

## Checklist pháp lý trước public beta

- [ ] Terms + Privacy tiếng Việt, đoạn dữ liệu training tách riêng
- [ ] Consent checkbox khi “đóng góp hook ẩn danh vào corpus”
- [ ] DMCA / form gỡ nội dung
- [ ] Không ví dụ lời hit trong docs/marketing
- [ ] Nút xóa project và xóa account
- [ ] AI demo (nếu có) luôn gắn nhãn
