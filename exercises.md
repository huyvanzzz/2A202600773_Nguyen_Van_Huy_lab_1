# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature thấp như 0.0, phản hồi thường ổn định, trực tiếp và ít biến thể giữa các lần gọi. Khi tăng lên 0.5 và 1.0, câu trả lời đa dạng hơn nhưng vẫn còn hợp lý; ở 1.5, mô hình có xu hướng sáng tạo hơn, đôi khi chọn chi tiết bất ngờ hơn và có rủi ro kém nhất quán hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ chọn khoảng 0.2 đến 0.4 cho chatbot hỗ trợ khách hàng, vì nhiệm vụ này cần câu trả lời nhất quán, rõ ràng và ít suy diễn. Mức này vẫn đủ linh hoạt để diễn đạt tự nhiên nhưng giảm nguy cơ trả lời quá sáng tạo.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Workload mỗi ngày là 10.000 * 3 * 350 = 10.500.000 token đầu ra. Với giá $0.010/1K token, GPT-4o tốn khoảng $105/ngày; với $0.0006/1K token, GPT-4o-mini tốn khoảng $6.30/ngày. Vì vậy GPT-4o đắt hơn khoảng 16.67 lần.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng hơn khi xử lý các tác vụ cần lập luận sâu, độ chính xác cao hoặc nội dung nhạy cảm như phân tích tài liệu pháp lý, tư vấn kỹ thuật phức tạp, hoặc tổng hợp quyết định kinh doanh quan trọng. GPT-4o-mini phù hợp hơn cho các tác vụ khối lượng lớn, rủi ro thấp như phân loại ticket, trả lời FAQ đơn giản, gợi ý câu chữ ngắn hoặc chatbot nội bộ cần tối ưu chi phí.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi dài hoặc người dùng cần cảm giác hệ thống đang làm việc ngay lập tức, ví dụ chatbot hỗ trợ, trợ lý viết nội dung, giải thích từng bước hoặc sinh mã. Việc hiển thị từng token giúp giảm cảm giác chờ đợi và cho phép người dùng đọc sớm trước khi câu trả lời hoàn tất. Non-streaming phù hợp hơn khi phản hồi ngắn, cần xử lý toàn bộ kết quả trước khi hiển thị, hoặc khi ứng dụng cần lưu, kiểm duyệt, định dạng JSON hay kiểm tra tính hợp lệ của câu trả lời trước khi đưa cho người dùng.


## Danh Sách Kiểm Tra Nộp Bài
- [x] Tất cả tests pass: `pytest tests/ -v`
- [x] `call_openai` đã triển khai và kiểm thử
- [x] `call_openai_mini` đã triển khai và kiểm thử
- [x] `compare_models` đã triển khai và kiểm thử
- [x] `streaming_chatbot` đã triển khai và kiểm thử
- [x] `retry_with_backoff` đã triển khai và kiểm thử
- [x] `batch_compare` đã triển khai và kiểm thử
- [x] `format_comparison_table` đã triển khai và kiểm thử
- [x] `exercises.md` đã điền đầy đủ
- [x] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
