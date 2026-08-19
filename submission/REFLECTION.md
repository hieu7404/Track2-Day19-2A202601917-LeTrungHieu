# Reflection — Lab 19

**Tên:** Lê Trung Hiếu - 2A202601917    
**Cohort:** A20-K3  
**Path đã chạy:** lite  

---

## Câu hỏi (≤ 200 chữ)
> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

Qua thực nghiệm 50 câu query:
- **`exact`:** BM25 thắng (96.7%) nhờ bắt chính xác các từ khóa kỹ thuật có sẵn trong tài liệu.
- **`paraphrase`:** Vector xử lý tốt hơn khi câu hỏi dùng từ tiếng Việt diễn đạt lại ý thay vì từ khóa gốc.
- **`mixed`:** Hybrid thắng tuyệt đối (100%) và đạt điểm trung bình cao nhất (78.6%) nhờ RRF gom được ưu điểm của cả hai bên.

Tôi sẽ không dùng Hybrid khi:
1. Cần độ trễ cực thấp (< 2ms) và tối ưu CPU: lúc này BM25 là đủ tốt và nhẹ nhất.
2. Tra cứu dữ liệu định danh chính xác (như mã đơn hàng, ID người dùng, mã lỗi): không cần đến tìm kiếm vector.
---
## Điều ngạc nhiên nhất khi làm lab này
Khá bất ngờ khi thấy Post-filter sụt giảm recall về 0% khi lọc chặt, trong khi Filtered-ANN vẫn giữ trọn 100%. Ngoài ra, việc semantic cache có thể làm lộ dữ liệu giữa các khách hàng nếu quên bật namespace cũng là bài học bảo mật rất thực tế.

---
## Bonus challenge
- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
