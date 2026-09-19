# Nghiên cứu: thanh điệu ↔ giai điệu tiếng Việt

Tài liệu này tóm tắt bằng chứng học thuật để **căn heuristic sản phẩm**, không thay paper gốc.

## Kết luận dùng được cho product

1. Ràng buộc text-setting tiếng Việt chủ yếu là **hướng chuyển giữa hai tiếng** (bigram), không phải pitch tuyệt đối từng nốt.
2. **Similar motion** được ưu tiên; **oblique** chấp nhận được (nhất là khi có thanh ngang); **contrary** hiếm và rủi ro đảo nghĩa.
3. Tránh contrary **quan trọng hơn** ép parallel 100%.
4. Công thức `sắc=+1, huyền=-1` độc lập từng chữ là **sai phương pháp**.

---

## Kirby & Ladd (2016)

*Tone-melody correspondence in Vietnamese popular song.* Proceedings of Tonal Aspects of Languages.

- Corpus: 20 ca khúc tân nhạc / popular Việt
- Similar motion (best model): **~77%**
- Contrary: khoảng **4%**, thường biên câu
- So sánh: Cantopop similar cao hơn (~91.8%); tiếng Việt chịu oblique nhiều hơn
- Phân tầng thanh để định nghĩa chuyển:

| Class | Thanh | Chao gợi ý |
|---|---|---|
| High | sắc, ngã | 24 ; 3ʔ5 |
| Mid | ngang | 33 |
| Low | huyền | 32 |
| Extra-low | nặng, hỏi | 21ʔ ; 21 |

Dataset bổ sung: Edinburgh DataShare [doi:10.7488/ds/1434](https://doi.org/10.7488/ds/1434).

**Hệ quả Lab:** mode An toàn tối ưu similar_ratio; không fail build nếu oblique trên chữ `thì`. Fail (điểm đỏ) nếu contrary trên keyword.

---

## Ca khúc nghệ thuật Việt Nam (Văn hóa Nghệ thuật)

Quan sát giáo khoa: tương tác **thuận chiều** bằng/trắc.

Thứ tự cao độ tương đối thường dạy:

```text
sắc ≥ ngã ≥ ngang ≥ huyền ≥ hỏi ≥ nặng
```

Giữa hai từ liên tiếp, giữ thứ tự này thì tai thường chấp nhận.

**Hệ quả Lab:** dùng như *prior* khi beam search chưa có context; Kirby bigram vẫn là luật chấm chính.

---

## Dân ca / toneume (Nhan, NYU)

Khái niệm: *syllamelis* (1 tiếng hát), *toneume* (nét thanh trong tiếng), *inter-toneume* (cầu nối hai tiếng). Rung / láy / hơi điệu (Bắc, Nam, Oán…) làm lệch nốt so với piano 12-TET.

**Hệ quả Lab:** grace/slide là first-class, không phải “ornament trang trí”. Mode dân tộc không quantize chết mọi micro-pitch; MVP piano roll 12-TET + ký hiệu láy là đủ.

---

## Ngũ cung Việt (heuristic pack)

Năm bậc (tương đương Cung–Thương–Giốc–Chủy–Vũ):

| Tên | Interval từ chủ (Cung = 0) | Ví dụ C |
|---|---|---|
| Cung | 0 | C |
| Thương | 2 | D |
| Giốc | 4 | E |
| Chủy | 7 | G |
| Vũ | 9 | A |

Solfege dân gian Nam Bộ thường gặp: **Hò Xự Xang Xê Cống**.

Hơi Bắc / Nam / Oán đổi *cách rung nhấn*, không chỉ set 5 nốt. Pack “dân tộc đương đại” MVP = pentatonic + 1–2 grace, chord pop nền. Không nhận claim “đúng hơi Oán” cho đến khi có chuyên gia.

---

## Phương ngữ

- **Bắc:** hỏi vs ngã tách — nên hiện dip/gãy nếu dialect = Bắc.
- **Nam:** hỏi/ngã gần hơn — nới penalty intra-syllable, **giữ** penalty contrary đảo nghĩa.

Chữ viết Quốc ngữ vẫn 6 dấu. Dialect chỉ đổi *độ phạt articulation*, không đổi tokenizer MVP.

---

## Việc chưa có paper đủ cho product

- Rubric viral 15s: **heuristic sản phẩm**, calibrate bằng A/B Lab
- Openness nguyên âm ↔ nốt cao: kinh nghiệm thanh nhạc + TTS; cần log “khó hát” từ user
- Vpop TikTok 2020s: chưa có corpus tone–melody public sạch pháp lý → synthetic + user-consent

Khi thêm rule mới: ghi “nguồn: Kirby 2016 / giáo khoa / heuristic Lab v1”.
