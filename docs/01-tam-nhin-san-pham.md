# 01. Tầm nhìn sản phẩm

## Câu định vị

**VietHook Lab** là webapp giúp nhạc sĩ, producer, singer-songwriter, sinh viên âm nhạc và người sáng tác không chuyên **viết, kiểm tra, tối ưu và thử nghiệm hook giai điệu tiếng Việt** dựa trên thanh điệu, ngữ nghĩa, nhịp lời, nguyên âm, cấu trúc pop và phản hồi từ người nghe thật.

Tagline:

> Biến câu nói tiếng Việt thành giai điệu hook dễ nhớ, đúng thanh điệu và có khả năng lan truyền.

Một dòng cho slide:

> Tone-aware songwriting copilot cho nhạc Việt — không phải AI tạo bài hát đại trà.

---

## Vấn đề

Thị trường Việt Nam có nhiều nguồn dạy:

- hòa âm / phối khí
- làm beat / DAW
- sáng tác ca từ chung chung
- AI tạo nhạc full-song (Suno, Udio, v.v.)

Nhưng thiếu một công cụ tập trung vào **đơn vị nhỏ nhất quyết định hit**: câu hook tiếng Việt.

Câu hỏi cốt lõi chưa có nơi nào trả lời hệ thống:

> Làm sao viết một câu hook tiếng Việt vừa tự nhiên, vừa khớp thanh điệu, vừa dễ nhớ, vừa có tiềm năng viral?

Hệ quả thực tế:

| Hiện tượng | Vì sao xảy ra |
|---|---|
| “Mất dấu” khi hát | Melody đi ngược thanh, hoặc nốt cao kéo dài trên thanh hỏi/ngã/nặng |
| Hook na ná | Lặp contour 1–5–6–5, thiếu motif riêng, thiếu cao điểm |
| Lời hay nhưng khó hát | Nguyên âm đóng / phụ âm tắc đặt ở nốt cao dài |
| Hook quá dài cho TikTok | 13–16 âm tiết nhồi vào 4 nhịp, không có điểm cắt 15s |
| Lời và nhạc tách lớp | Học viên viết lời xong mới “phổ”, không cùng lúc tối ưu |

---

## Bốn khoảng trống VietHook Lab lấp

| Khoảng trống hiện tại | Cách giải quyết |
|---|---|
| Thiếu hệ thống “hook học” bằng tiếng Việt | Module dạy theo đơn vị câu hát 4–8 nhịp, rubric chấm điểm, bài tập có phản hồi |
| Thiếu công cụ kiểm tra giai điệu – thanh điệu | Tone Map: 6 thanh so với đường nét giai điệu, cảnh báo mất dấu |
| Lời và nhạc được dạy tách rời | Editor tích hợp: nhập lời → chọn mood/genre/BPM/key → sinh và chỉnh melody trên đúng câu chữ |
| Thiếu dữ liệu hook Việt Nam công khai | Corpus hook Việt hóa: metadata, nhịp, nguyên âm, thanh điệu, contour, độ dễ nhớ, phản hồi người nghe |

---

## Sản phẩm không phải gì

Không định vị VietHook Lab như:

- Suno / Udio cho tiếng Việt
- Karaoke AI
- Plugin hòa âm đầy đủ
- Marketplace beat
- Công cụ clone giọng ca sĩ
- “Hooktheory dịch ra tiếng Việt” (Hooktheory không hiểu thanh điệu)

Nếu marketing trượt sang “tạo bài hát bằng AI”, sản phẩm mất moat và bị so sánh sai sân.

---

## Sáu giá trị người dùng nhận được

1. **Viết hook nhanh hơn** — từ ý tưởng, cảm xúc, từ khóa, thể loại → nhiều biến thể câu hát.
2. **Kiểm tra tính tiếng Việt** — thanh điệu, nguyên âm, phụ âm cuối, nhịp âm tiết, ngữ điệu câu.
3. **Tối ưu độ dễ nhớ** — lặp, bất ngờ, phạm vi quãng, mật độ âm tiết, cao điểm cảm xúc.
4. **Thử nghiệm với người nghe thật** — link chia sẻ, bầu mù, comment, tỷ lệ nghe lại.
5. **Học qua phản hồi** — mỗi lỗi giải thích bằng tiếng người: *“chữ ‘mất’ thanh nặng đang nằm ở nốt cao kéo dài, dễ gây gượng”*.
6. **Xuất ra sản phẩm thực tế** — MIDI, audio demo, chord chart, lyric sheet, Hook Report.

---

## Đơn vị sản phẩm

Đơn vị không phải *bài hát*. Đơn vị là **hook**.

Hook ở đây gồm:

- 1–2 câu lời (thường 4 hoặc 8 nhịp, hoặc clip 15 giây)
- contour giai điệu + rhythm
- chord bed tối thiểu
- điểm cắt viral
- điểm số + giải thích

Mọi module xoay quanh vòng lặp: **viết → kiểm tra thanh → biến thể → chấm → thử tai người nghe**.

---

## Tuyên bố chất lượng

Một hook “đạt” theo VietHook Lab khi đồng thời:

- **Không đảo nghĩa** ở từ khóa do contrary motion
- **Hát được** trong tessitura pop phổ thông (khoảng 5–9 semitone cho hook dễ nhớ)
- **Nhớ được** sau 1–2 lần nghe (có motif lặp hoặc đối xứng A–A′–B–A″)
- **Cắt được** 5–15 giây mà vẫn thành câu
- **Giải thích được** vì sao điểm cao/thấp

Nếu chỉ “nghe hay” mà không giải thích được, đó chưa phải sản phẩm này.
