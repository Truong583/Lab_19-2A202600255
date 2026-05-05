# Reflection — Lab 19

**Tên:** _<Phạm Đình Trường>_
**Cohort:** _2A202600255_


---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

- **Exact queries:** BM25 thắng hoặc tương đương Hybrid vì các từ khóa kỹ thuật xuất hiện chính xác trong corpus là signal cực mạnh.
- **Paraphrase queries:** Semantic (Vector) thắng nhờ khả năng hiểu ngữ nghĩa, tuy nhiên model `bge-small-en` có hạn chế với tiếng Việt nên Hybrid giúp ổn định kết quả hơn.
- **Mixed queries:** Hybrid thắng rõ rệt vì kết hợp được ưu điểm của cả hai: độ chính xác của từ khóa và độ bao phủ của ngữ nghĩa thông qua RRF.

**Khi nào không dùng Hybrid:**
1. **Latency budget cực thấp:** Pure BM25 (SQLite/Elastic) nhanh hơn đáng kể so với việc phải chạy thêm model embedding.
2. **Hệ thống đơn giản:** Nếu dữ liệu nhỏ và người dùng chỉ tìm theo ID/Mã sản phẩm (exact match), BM25 là đủ.
3. **Cực hạn về tài nguyên:** Không có GPU/RAM để load model embedding lớn.

---

## Điều ngạc nhiên nhất khi làm lab này

Sự đơn giản của RRF (1/(k+rank)) nhưng lại mang lại hiệu quả cực kỳ mạnh mẽ trong việc kết hợp các kết quả tìm kiếm khác nhau mà không cần tuning phức tạp.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_

