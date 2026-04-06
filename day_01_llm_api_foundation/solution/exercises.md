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
> Khi temperature thấp (0.0 - 0.5), các câu trả lời rất ổn định, tập trung vào các sự thật phổ biến (như hang Sơn Đoòng) với văn phong trang trọng. Khi temperature cao hơn (1.0 - 1.5), mô hình trở nên "sáng tạo" hơn, có thể thay đổi chủ đề (như chuyển sang cà phê) hoặc thay đổi cách diễn đạt linh hoạt hơn qua mỗi lần gọi.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt temperature từ 0.0 đến 0.2. Lý do là vì trong hỗ trợ khách hàng, sự chính xác, nhất quán và đáng tin cậy là quan trọng nhất; chúng ta cần chatbot trả lời cùng một thông tin đúng đắn cho cùng một câu hỏi thay vì đưa ra các câu trả lời ngẫu nhiên hay sáng tạo quá mức.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> GPT-4o đắt hơn GPT-4o-mini khoảng 16.7 lần ($0.010 / $0.0006). Với 10.5 triệu token (10k user * 3 call * 350 token), chi phí GPT-4o sẽ là ~$105 trong khi GPT-4o-mini chỉ tốn ~$6.3.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng khi cần khả năng lý luận phức tạp, giải quyết các tác vụ đòi hỏi sự chính xác cao về logic hoặc phân tích dữ liệu đa bước (như phân tích tài chính sâu). GPT-4o-mini tốt hơn cho các tác vụ lặp đi lặp lại khối lượng lớn, độ trễ thấp như phân loại email, tóm tắt văn bản ngắn hoặc chatbot trả lời các câu hỏi FAQ cơ bản.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất trong các ứng dụng tương tác thời gian thực như chatbot hoặc trợ lý ảo, nơi trải nghiệm người dùng phụ thuộc nhiều vào cảm nhận về độ trễ. Việc hiển thị từng phần kết quả ngay khi được sinh ra giúp người dùng cảm thấy hệ thống phản hồi nhanh và tự nhiên hơn. Ngược lại, non-streaming phù hợp hơn trong các tác vụ xử lý nền hoặc khi cần kết quả hoàn chỉnh và có cấu trúc rõ ràng (ví dụ JSON để phục vụ API downstream), như batch processing, data pipelines hoặc các tác vụ không yêu cầu tương tác trực tiếp.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
