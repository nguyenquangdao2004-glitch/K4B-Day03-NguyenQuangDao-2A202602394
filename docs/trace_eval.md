# 📊 BÁO CÁO THU HOẠCH NGHIỆM THU BÀI LAB 3 (BƯỚC 3 — SUBMISSION ARTIFACT)

> **Họ và Tên Học viên:** Nguyễn Quang Đạo  
> **Mã Sinh Viên / Mã Học viên:** 2A202602394  
> **Chủ đề Lựa chọn:** Gợi ý 1.1: Trợ lý Học vụ & Tra cứu Lịch hẹn VinUni  

---

## 1. BẢNG CHẤM ĐIỂM AGENTIC FIT SCORING MATRIX (ĐÁNH GIÁ CHỦ ĐỀ)

| Tiêu chí Đánh giá | Mức độ (1 - 5) | Giải trình chi tiết lý do chọn điểm |
| :--- | :---: | :--- |
| **1. Multi-step Reasoning** | 4 / 5 | Yêu cầu chuỗi suy luận: tra cứu thông tin sinh viên và cố vấn phụ trách trước, sau đó mới dùng dữ liệu đó để đặt lịch hẹn. |
| **2. Tool Interaction** | 5 / 5 | Bắt buộc kết nối CSDL học vụ qua MCP Server để lấy dữ liệu thực tế (GPA, email, cố vấn), tránh LLM bịa đặt (hallucination). |
| **3. Dynamic Decision** | 4 / 5 | Quyết định bước kế tiếp phụ thuộc vào kết quả quan sát (nếu sinh viên không tồn tại -> dừng và thông báo; nếu hợp lệ -> tiếp tục đặt lịch). |
| **4. Long Horizon Goal** | 3 / 5 | Hệ thống duy trì mục tiêu qua nhiều bước hội thoại và tool calls (nhận diện ý định -> tra cứu -> đặt lịch -> xác nhận). |
| **TỔNG ĐIỂM AGENTIC FIT** | **16 / 20** | *Nếu tổng điểm > 12/20: Bài toán rất phù hợp triển khai Agentic System.* |

---

## 2. TRÍCH XUẤT KẾT QUẢ WATERFALL TRACE LOG (SAU KHI CHẠY TEST SUITE TRÊN API THẬT)

> ⚠️ **YÊU CẦU NGHIỆM THU:** Mở tệp `.env` điền `GEMINI_API_KEY` (hoặc `OPENAI_API_KEY`) để kết nối LLM thật trước khi thực thi `python src/app.py --all`. Bài nộp chỉ dùng Mock Offline Provider sẽ không đạt điểm nghiệm thực tế.

Dán 1 đoạn trích xuất log tiêu biểu từ file `docs/trace_waterfall.json` sinh ra từ phản hồi LLM API thật:

```json
[
  {
    "step": 1,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên có mã SV9999999.",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "academic_query",
    "arguments": {
      "student_id": "SV9999999"
    },
    "observation": {
      "status": "NOT_FOUND",
      "message": "Không tìm thấy dữ liệu sinh viên có mã 'SV9999999'"
    },
    "latency_ms": 1709.84
  },
  {
    "step": 2,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên có mã SV9999999.",
    "action_type": "FINAL_ANSWER",
    "thought": "Tổng hợp kết quả từ MCP Server thành công.",
    "output": "Không tìm thấy dữ liệu sinh viên có mã 'SV9999999'",
    "latency_ms": 10.0
  }
]
```

---

## 3. TỔNG KẾT KẾT QUẢ NGHIỆM THU & NỘP BÀI

- [x] Đã cấu hình API Key trong `.env` và xác nhận Agent chạy mượt mà vòng lặp ReAct kết nối MCP Server.
- **Tổng số Test Cases đã chạy thành công:** 5 / 5 test cases.
- **Số lượt gọi Tool qua MCP Server chính xác:** 4 lượt (TC02, TC03, TC04, TC05).
- **Kết quả đẩy Repo nộp bài:** [x] Đã Commit và Push mã nguồn thành công lên GitHub cá nhân.

---

> ✅ **HOÀN TẤT NỘP BÀI:** Sao chép đường link GitHub Repository cá nhân của bạn và dán vào ô nộp bài trên hệ thống LMS VLearn để hoàn tất Bài Lab 3!
