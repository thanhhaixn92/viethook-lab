# 11. Mô hình dữ liệu

Hai kho: **Vietnamese Tone Lexicon** (từ điển âm tiết) và **Hook Corpus** (feature đã tách, không cần full lời/audio bản quyền).

---

## 11.1 Vietnamese Tone Lexicon

Mỗi hàng ~ 1 âm tiết hợp lệ (tiếng).

| Trường | Ví dụ |
|---|---|
| syllable | buông |
| tone | ngang |
| initial | b |
| medial | u |
| vowel | ô |
| coda | ng |
| openness | 0.65 |
| sustainable | true |
| natural_contour | level |
| default_weight | 0.4 |
| synonyms | thả, xa, rời |

Nguồn khởi tạo:

- Từ điển âm tiết mở + bảng chữ Quốc ngữ
- NLP tiếng Việt (underthesea normalize)
- Chuyên gia âm nhạc hiệu đính top 2.000 tiếng hay gặp trong hook
- User feedback (nút “chữ này khó hát”)

Không cần neural TTS lexicon ở MVP. Openness gán rule:

```text
a, o, ơ, ê     → 0.8–1.0
ô, e, i         → 0.5–0.7
u, ư            → 0.3–0.5
+ coda p/t/c/ch → × 0.3  (không sustain)
+ coda m/n/ng   → giữ
```

---

## 11.2 Hook Corpus — schema

Không lưu full lyrics/audio có bản quyền. Lưu feature.

```json
{
  "hook_id": "hk_00123",
  "source_type": "user_generated",
  "license": "user_consent_anonymous",
  "genre": "vpop_ballad",
  "bpm": 76,
  "key": "C_major",
  "syllable_count": 9,
  "bar_length": 4,
  "tone_sequence": ["ngang", "huyen", "sac"],
  "vowel_openness_score": 0.72,
  "melodic_contour": [0, 2, 4, 7, 4, 2, 0, 1],
  "interval_range_semitones": 7,
  "repetition_ratio": 0.45,
  "peak_position": 0.68,
  "has_post_chorus": false,
  "hook_score_auto": 79,
  "hook_score_human": 82,
  "memorability_vote": 0.74,
  "singalong_rate": 0.51,
  "tags": ["chia_tay", "buon", "ngan", "de_nho"],
  "generator_version": "rule_beam_v1"
}
```

`melodic_contour` là interval relative từ nốt đầu, không phải MIDI tuyệt đối — dễ so sánh giữa các key.

`source_type`: `user_generated | public_domain | licensed | synthetic`.

---

## 11.3 Project file (user)

```json
{
  "project_id": "p_...",
  "created_at": "2026-09-19T00:00:00Z",
  "brief": {},
  "lyric": {
    "text": "Thôi thì mình buông, nhưng lòng chưa buông",
    "syllables": []
  },
  "tone_map": [],
  "variants": [
    {
      "variant_id": "v_...",
      "mode": "catchy",
      "notes": [],
      "chords": [],
      "score": {},
      "composition_notes": []
    }
  ],
  "share": { "slug": "abc123", "blind": true }
}
```

---

## 11.4 Nguồn hợp pháp

Được:

- Public domain (thơ / ca khúc hết hạn)
- User upload có điều khoản đồng ý chia sẻ **feature ẩn danh**
- Synthetic (tự sinh rồi gắn label)
- Đối tác trường / label cấp phép

Không:

- Scrape lời + audio hit Vpop hàng loạt để train
- Lưu full stem vocal user nếu họ không opt-in
- Tái nhận diện người nghe A/B

Xem [15-phap-ly-dao-duc.md](15-phap-ly-dao-duc.md).

---

## 11.5 Stopwords và từ khóa

Stopword chức năng (linh hoạt thanh hơn): *thì, mà, và, của, là, những, các, một, trong, cho, với, để, không, rất, đã, sẽ, đang…*

Keyword = overlap với brief + danh từ/động từ có `wᵢ` cao. POS tagging (underthesea) hỗ trợ, nhưng user highlight đè được.
