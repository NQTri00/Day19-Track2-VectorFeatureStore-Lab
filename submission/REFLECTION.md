# Reflection — Lab 19

**Tên:** Ninh Quang Trí
**Cohort:** 2A202600249
**Path đã chạy:** lite

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

**Trả lời:**
- **Exact queries:** Pure BM25 thường thắng. Do BM25 bắt chính xác các keyword, mã lỗi, hoặc từ chuyên ngành mà không bị nhiễu bởi các "từ đồng nghĩa" (vốn hay bị đánh giá sai trong không gian vector).
- **Paraphrase queries:** Pure Vector thắng. Vì nó hiểu được ngữ nghĩa và ý định của người dùng, ngay cả khi họ sử dụng các từ vựng hoàn toàn khác so với trong tài liệu gốc.
- **Mixed queries:** Hybrid search thắng. Thuật toán Reciprocal Rank Fusion (RRF) kết hợp hoàn hảo cả việc match keyword chính xác lẫn context ngữ nghĩa.

**Khi nào KHÔNG dùng hybrid:**
- Dùng **pure BM25** khi user tìm kiếm các exact matches cực kỳ cụ thể như: part numbers, mã SKU, error logs, hoặc số thẻ. Cố gắng tính toán ngữ nghĩa ở đây chỉ làm giảm độ chính xác và tốn kém tài nguyên không cần thiết.
- Dùng **pure vector** khi user đặt câu hỏi hoàn toàn bằng ngôn ngữ tự nhiên, rất trừu tượng, mô tả triệu chứng thay vì dùng keyword, hoặc không biết từ khóa chuyên ngành chính xác.

---

## Điều ngạc nhiên nhất khi làm lab này

Việc có thể dễ dàng setup một feature store chuẩn hóa với Feast (dùng Parquet cho offline và SQLite cho online) ngay trên local, và thấy rõ tính năng Point-In-Time (PIT) join giúp ngăn chặn triệt để data leakage khi build training data.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
