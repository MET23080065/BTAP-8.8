# BÁO CÁO KIỂM THỬ CUỐI CÙNG (TEST REPORT)

## 1. Tổng quan kết quả kiểm thử (Summary)

* **Tổng số Test Cases:** 10
* **Số Test Pass (Thành công):** 10
* **Số Test Fail ban đầu:** 01 (Test case TC06)
* **Tỷ lệ Pass cuối cùng:** 100% (Sau khi sửa lỗi code dựa trên phân tích của AI)

---

## 2. Chi tiết Lỗi phát hiện & Quy trình sửa lỗi (Bug Analysis & Fix)

### 🔴 Lỗi phát hiện (Test Fail ban đầu)
* **Mã Test Case bị lỗi:** `TC06 - Boundary Case` (Mật khẩu dưới 8 ký tự).
* **Hiện tượng:** Khi truyền vào mật khẩu dài 7 ký tự (`1234567`), kiểm thử báo **FAIL** vì hệ thống vẫn chấp nhận mật khẩu này thay vì báo lỗi.

### 🤖 AI phân tích nguyên nhân gốc rễ (Root Cause)
* AI Agent đã phân tích đoạn code xử lý và phát hiện điều kiện kiểm tra độ dài đang ghi sai:
  * **Code cũ bị lỗi:** `if len(password) < 7:` (Chỉ chặn mật khẩu dưới 7 ký tự, dẫn đến 7 ký tự vẫn vượt qua).

### 🛠️ Đã sửa code & Test lại (Re-test)
* **Cách sửa:** Đổi điều kiện kiểm tra độ dài thành `if len(password) < 8:`.
* **Kết quả Re-test:** Chạy lại bộ test tự động, tất cả 10 Test Cases chuyển sang trạng thái **PASS** (Màu xanh).

---

## 3. Nhật ký Minh chứng Hình ảnh (Evidence)

*(Hình ảnh minh chứng được đính kèm chi tiết trong thư mục `evidence/`)*

1. **Phân tích dự án:** `evidence/01_code_analysis.png`
2. **Tạo Test Case tự động:** `evidence/02_generated_tests.png`
3. **Chạy Test lần 1 (Có 1 Fail):** `evidence/03_run_test_fail.png`
4. **AI phân tích nguyên nhân lỗi:** `evidence/04_ai_debug_analysis.png`
5. **Sửa code:** `evidence/05_fix_code.png`
6. **Chạy lại Test (Pass tất cả):** `evidence/06_retest_pass.png`

---

## 4. Đánh giá sự hỗ trợ của AI Agent & Quyết định của Sinh viên

### 🤖 AI Agent đã hỗ trợ những gì?
* Phân tích nhanh mã nguồn để xác định các chức năng cốt lõi cần kiểm thử.
* Tự động sinh mã nguồn Automated Test với đầy đủ các loại test case (Normal, Edge Case, Boundary,...).
* Đọc Log lỗi (Error Stacktrace) và chỉ ra chính xác dòng code bị sai logic.

### 👨‍💻 Sinh viên đã tự kiểm tra và quyết định gì?
* **Hiểu bản chất kiểm thử:** Sinh viên nhận biết được lỗi ở TC06 là lỗi kiểm tra giá trị biên (Boundary Case) đối với độ dài chuỗi mật khẩu.
* **Đánh giá giải pháp của AI:** AI đề xuất 2 giải pháp (dùng thư viện ngoài hoặc sửa câu lệnh `if`). Sinh viên đã chọn cách chỉnh sửa câu lệnh `if len(password) < 8` để tối ưu dung lượng và không làm phức tạp hóa mã nguồn.
* **Xác nhận lại kết quả:** Trực tiếp chạy lệnh kiểm thử trên Terminal để kiểm chứng kết quả Pass trước khi lưu báo cáo.
