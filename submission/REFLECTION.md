# Reflection — Lab 19

**Tên:** Nguyễn Việt Hoàng
**Cohort:** A20-K2
**Path đã chạy:** Lite
---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

- **BM25 thắng ở `exact`**: Thuật toán dựa trên đối sánh từ khoá (TF-IDF), cực kỳ chính xác khi truy vấn chứa nguyên văn các thuật ngữ trong tài liệu.
- **Vector (Semantic) thắng ở `paraphrase`**: Do có khả năng "hiểu" ngữ nghĩa, tìm được tài liệu kể cả khi dùng từ đồng nghĩa và không trùng keyword.
- **Hybrid thắng tuyệt đối ở `mixed`**: Nhờ kết hợp RRF, vừa bắt dính các từ khoá kỹ thuật quan trọng (BM25) vừa nắm bắt được ý chính qua ngữ nghĩa (Vector).

**Khi nào KHÔNG dùng Hybrid:**
- **Chỉ dùng BM25:** Khi tìm kiếm tra cứu các mã ID sản phẩm, tên riêng, mã lỗi (những từ không có ngữ nghĩa Vector) hoặc hệ thống eo hẹp tài nguyên, yêu cầu độ trễ cực thấp.
- **Chỉ dùng Vector:** Khi truy vấn chủ yếu là câu hỏi ngôn ngữ tự nhiên dài, hoặc hệ thống muốn tối ưu chi phí hạ tầng (không muốn duy trì song song 2 index BM25 và Vector).
---

## Điều ngạc nhiên nhất khi làm lab này

Chỉ với vài dòng code áp dụng công thức Reciprocal Rank Fusion (RRF) cực kỳ đơn giản `1 / (k + rank)`, độ chính xác của tìm kiếm trên thực tế (mixed query) được cải thiện một cách rõ rệt.
---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
