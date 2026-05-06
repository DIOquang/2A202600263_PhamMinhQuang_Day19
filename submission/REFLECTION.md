# Reflection — Lab 19

**Tên:** _2A202600263 Phạm Minh Quang_
**Cohort:** _A20-K1_
**Path đã chạy:** _lite_

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

- **Mixed:** Hybrid thắng tuyệt đối (~100% Precision@10) vì kết hợp được cả signal từ từ khóa (BM25) và ngữ nghĩa (Vector).
- **Exact:** BM25 thắng hoặc ngang hybrid vì query chứa chính xác thuật ngữ kỹ thuật, việc matching token trực tiếp là tối ưu nhất.
- **Paraphrase:** Vector (Semantic) thắng khi query dùng từ đồng nghĩa/diễn đạt khác. Tuy nhiên, ở bản "lite", model `bge-small-en` yếu với tiếng Việt; chuyển sang bản "docker" dùng `bge-m3` sẽ thấy semantic thắng rõ rệt.

**Khi nào KHÔNG dùng hybrid:**
1. **Pure BM25:** Khi tìm mã ID, SKU, hoặc tên riêng cực kỳ đặc thù mà "ngữ nghĩa" có thể gây nhiễu (hallucination), hoặc khi cần độ trễ cực thấp.
2. **Pure Vector:** Khi search theo concept, hình ảnh, hoặc corpus đa ngôn ngữ mà từ khóa không mang nhiều ý nghĩa.

---

## Điều ngạc nhiên nhất khi làm lab này

Sự khác biệt rõ rệt về hiệu năng giữa các embedding model (`bge-small-en` vs `bge-m3`) khi xử lý tiếng Việt. Nó cho thấy việc chọn model "phù hợp ngôn ngữ" quan trọng hơn chỉ là chọn model "to/mạnh".

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _None_
