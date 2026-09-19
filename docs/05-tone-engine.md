# 05. Tone Engine

Trái tim khác biệt của sản phẩm. Phần này khiến VietHook Lab **không phải Hooktheory bản tiếng Việt**.

Tone Engine trả lời: *câu hát này, với (hoặc chưa có) giai điệu kia, có nguy cơ mất dấu / gượng / đảo nghĩa không — và sửa thế nào?*

---

## Sáu thanh tiếng Việt

| Thanh | Dấu | Mô tả ngữ âm gợi ý (Bắc) | Xu hướng melody (heuristic, không đủ một mình) |
|---|---|---|---|
| ngang | không | bằng, mid-level ~33 | nốt ổn định, ít nhảy |
| huyền | `à` | đi xuống ~32 | xuống hoặc giữ thấp |
| sắc | `á` | đi lên ~24 | chuyển động lên hoặc nhấn cao |
| hỏi | `ả` | xuống rồi lên ~21 / 214 | luyến, dip, grace, 2 nốt |
| ngã | `ã` | gãy, lên có glottal ~3ʔ5 | cần melisma/gãy; dễ mất dấu nếu hát thẳng |
| nặng | `ạ` | thấp, dứt, checked ~21ʔ | nốt ngắn hoặc trầm, hợp kết câu |

Thứ tự cao độ tương đối thường gặp trong ca khúc nghệ thuật VN (heuristic giáo khoa, không phải luật vật lý):

```text
sắc  ≥  ngã  ≥  ngang  ≥  huyền  ≥  hỏi  ≥  nặng
```

Giữa hai chữ liên tiếp, chỉ cần **thứ tự cao độ không đảo ngược thứ tự thanh** thì tai tiếng Việt thường chấp nhận. Kirby & Ladd (2016) cho thấy ràng buộc thực nghiệm mạnh hơn nằm ở **hướng chuyển bigram**, không phải pitch tuyệt đối của từng nốt.

Chi tiết học thuật: [research/tone-melody-literature.md](../research/tone-melody-literature.md).

---

## Đơn vị phân tích: âm tiết, không phải từ

Mỗi syllable `sᵢ` có:

| Trường | Ký hiệu | Ví dụ “buông” |
|---|---|---|
| Chữ viết | orth | buông |
| Thanh | `tᵢ` | ngang |
| Âm đầu | initial | b |
| Nguyên âm / vần | `vᵢ` | uô |
| Phụ âm cuối | `cᵢ` | ng |
| Độ mở nguyên âm | openness | trung–mở |
| Có thể ngân dài? | sustain | có (coda mũi) |
| Trọng nghĩa | `wᵢ` | cao nếu là từ khóa |
| Vị trí nhịp | `rᵢ` | downbeat / offbeat |

Cấu trúc âm tiết tiếng Việt: **initial + rhyme (medial + vowel + coda) + tone**.

### Nguyên âm mở / đóng (singability)

| Dễ ngân ở nốt cao | Trung bình | Khó ngân dài / nốt cao |
|---|---|---|
| a, ă (ngắn), â (cẩn thận), o, ơ, ê | i, u, ư, ô | nguyên âm + coda tắc p/t/c/ch |

Coda mũi `m n ng` ngân được. Coda tắc `p t c ch` **cắt hơi** — phạt nặng nếu đặt ở nốt cao kéo dài.

---

## Tone Map

Mỗi âm tiết là một chip:

```text
[Thôi] [thì] [mình] [buông] [nhưng] [lòng] [chưa] [buông]
 ngang   huyền  huyền   ngang    ngang  huyền  ngang   ngang
```

Khi đã có melody:

```text
Melody:  C4  →  D4  →  E4  →  G4  →  E4  →  D4  →  C4  →  D4
Fit:     xanh   vàng  vàng   xanh   xanh  vàng  xanh   xanh
```

Màu:

| Màu | Ý nghĩa | Hành vi UI |
|---|---|---|
| Xanh | khớp tự nhiên | không cần hành động |
| Vàng | chấp nhận được, cần hát tinh tế | tooltip + gợi ý nhẹ |
| Đỏ | nguy cơ mất dấu / gượng / đảo nghĩa từ khóa | bắt buộc hiện gợi ý sửa |

---

## Similar / oblique / contrary (bắt buộc dùng)

**Cấm** công thức máy móc `sắc=+1, huyền=-1` độc lập từng chữ rồi gọi là “đã xử lý thanh”.

Chấm khớp theo **hướng chuyển giữa hai âm tiết liên tiếp** so với hướng pitch:

| Loại | Định nghĩa | Khuyến nghị |
|---|---|---|
| Similar / parallel | pitch cùng hướng chuyển thanh (theo tonal offset) | ưu tiên, đặc biệt ở từ khóa |
| Oblique | một bên giữ, một bên chuyển | cho phép, nhất là khi có thanh ngang |
| Contrary | pitch ngược hướng chuyển thanh | hạn chế ở hook; phạt nặng nếu là từ khóa |

Corpus tân nhạc ~**77% similar**; contrary ~**4%**, thường ở biên câu. Hệ quả sản phẩm:

> Tránh contrary quan trọng hơn ép parallel tuyệt đối mọi chỗ.

### Phân tầng thanh để tính bigram (Kirby & Ladd, best model)

| Nhóm offset | Thanh |
|---|---|
| High | sắc (24), ngã (3ʔ5) |
| Mid | ngang (33) |
| Low | huyền (32) |
| Extra-low | nặng (21ʔ), hỏi (21) |

Ví dụ đảo nghĩa:

- “đi” (ngang) → “về” (huyền): giữ rồi **xuống** = similar.
- Đưa “về” **cao hơn** “đi” dễ nghe như “vé” (sắc). Tránh.

---

## Penalty mặc định

Đỏ khi một trong các điều sau xảy ra **và** `wᵢ` cao (từ khóa / hook):

1. Thanh huyền nhưng melody đi lên mạnh **và** kéo dài
2. Thanh sắc nhưng melody đi xuống ở trọng âm
3. Thanh hỏi / ngã đặt ở nốt cao dài **không** có luyến / dip / grace
4. Thanh nặng kéo dài trên nốt cao (dễ thành huyền hoặc sắc tùy cách hát)
5. Contrary motion trên bigram từ khóa
6. Nguyên âm đóng hoặc coda tắc ở nốt cao kéo dài
7. > 3 âm tiết nhồi vào 1 beat ở ballad
8. Cao điểm rơi vào chữ chức năng (`thì`, `mà`, `của`, `là`) thay vì từ khóa

Vàng khi điều kiện trên xảy ra ở chữ chức năng, hoặc contrary nhẹ ở biên câu.

---

## Gợi ý sửa (bắt buộc có khi đỏ)

Hệ thống đề xuất theo thứ tự ít phá nghĩa → nhiều phá nghĩa:

1. Thêm nốt luyến / slide / grace (giữ lời)
2. Rút trường độ chữ đang gượng
3. Dịch cao điểm sang chữ khác (cùng câu)
4. Đổi nhịp ngắt / thêm rest 1 beat
5. Đổi chữ đồng nghĩa cùng trường nghĩa, ưu tiên thanh dễ hơn
6. Đổi trật tự cụm, giữ keyword

Ví dụ copy:

```text
Cảnh báo:
Chữ “hỏi” đang nằm ở nốt cao kéo dài mà không có luyến,
dễ bị nghe thành thanh khác.

Gợi ý:
- Thêm nốt trượt xuống–lên trước nốt chính
- Hoặc chuyển trọng tâm cao độ sang chữ “nhớ”
- Hoặc rút ngắn trường độ của chữ này
```

Copy phải chỉ **đúng chữ**, không nói chung “giai điệu chưa khớp”.

---

## Dialect mode (heuristic, không tuyệt đối)

| | Bắc | Nam |
|---|---|---|
| hỏi vs ngã | tách rõ hơn → nên thể hiện dip/gãy nếu user chọn giọng Bắc | gần nhau hơn → linh hoạt hơn |
| nặng | dứt, checked rõ | thường thấp, ngắn |
| Áp dụng | phạt nặng hơn nếu hát thẳng hỏi/ngã | penalize chủ yếu contrary + đảo nghĩa |

Mặc định MVP: **Northern orthographic tones** (dấu chữ viết) + dialect flag chỉ đổi độ phạt, không đổi tokenizer.

---

## Pipeline kỹ thuật gợi ý

```text
NFC normalize
  → tách câu
  → tách tiếng (khoảng trắng + từ điển âm tiết hợp lệ)
  → mỗi tiếng: tone from diacritic, initial, vowel, coda
  → gán trọng nghĩa (keyword overlap + stopword list)
  → ước lượng syllables/beat từ BPM + bars
  → ToneMap pre-melody
  → (nếu có M) so khớp bigram + duration + openness
  → warnings + fix-its
```

Thanh lấy từ **chữ viết có dấu**. Không đoán thanh từ audio ở MVP.

Công cụ NLP hỗ trợ: `underthesea.text_normalize`, `word_tokenize` — nhưng đơn vị hát là **tiếng / âm tiết**, không phải multiword token. Cần lớp tách tiếng riêng (khoảng trắng + từ điển 1 tiếng). Từ ghép “ngày mai” = 2 syllable.

---

## Override nghệ thuật

User luôn được phép giữ contrary motion. UI hiện:

```text
Phá luật có chủ đích
“về” đi lên — có thể nghe như “vé”. Vẫn giữ?
[Giữ và ghi chú]  [Sửa giúp]
```

Mọi override ghi vào `composition_notes`. Hook Score Tone Fit vẫn trừ điểm, nhưng không chặn export.
