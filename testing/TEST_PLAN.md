# KẾ HOẠCH KIỂM THỬ (TEST PLAN)

## 1. Thông tin chung
* **Dự án:** Kiểm thử chức năng Quản lý Tài khoản / Đăng nhập & Đăng ký bằng AI Agent.
* **Môi trường & Công cụ:** 
  * Ngôn ngữ/Framework: Python (Pytest) / JavaScript (Jest)
  * Công cụ hỗ trợ AI: ChatGPT / Claude / GitHub Copilot
  * Quản lý mã nguồn: GitHub

## 2. Mục tiêu kiểm thử
* Sử dụng AI Agent để phân tích mã nguồn và tự động tạo bộ test case.
* Đảm bảo bao phủ các trường hợp kiểm thử quan trọng: Luồng bình thường, Dữ liệu sai/rỗng, Giá trị biên, Trường hợp đặc biệt (Edge Case) và Xử lý lỗi.

---

## 3. Danh sách 10 Test Cases (Kế hoạch kiểm thử)

| STT | Mã TC | Phân loại | Mô tả kịch bản (Scenario) | Dữ liệu đầu vào (Input) | Kết quả kỳ vọng (Expected Result) |
|---|---|---|---|---|---|
| 1 | TC01 | Normal | Đăng ký tài khoản mới với thông tin hợp lệ | Email: `user@example.com`<br>Password: `Password123` | Đăng ký thành công, trả về trạng thái 200/201 |
| 2 | TC02 | Normal | Đăng nhập hệ thống với thông tin chính xác | Email: `user@example.com`<br>Password: `Password123` | Đăng nhập thành công, trả về Token xác thực |
| 3 | TC03 | Invalid Data | Đăng ký với định dạng Email không hợp lệ | Email: `user_invalid_email`<br>Password: `Password123` | Báo lỗi định dạng Email không hợp lệ |
| 4 | TC04 | Empty Data | Để trống trường Mật khẩu khi đăng ký | Email: `user@example.com`<br>Password: `""` | Báo lỗi Mật khẩu không được để trống |
| 5 | TC05 | Boundary Case | Kiểm tra Mật khẩu đúng độ dài tối thiểu (8 ký tự) | Password: `12345678` | Kiểm tra thành công (Hợp lệ) |
| 6 | TC06 | Boundary Case | Kiểm tra Mật khẩu dưới độ dài tối thiểu (7 ký tự) | Password: `1234567` | Báo lỗi Mật khẩu phải có ít nhất 8 ký tự |
| 7 | TC07 | Edge Case | Đăng ký tên người dùng chứa ký tự Unicode/Tiếng Việt | Name: `Nguyễn Văn A #$%` | Hệ thống xử lý đúng và lưu trữ an toàn |
| 8 | TC08 | Edge Case | Gửi dữ liệu chuỗi cực dài vào ô Input | Input: Chuỗi 5000 ký tự | Hệ thống tự cắt ngắn hoặc báo lỗi giới hạn độ dài |
| 9 | TC09 | Error Handling | Đăng ký tài khoản với Email đã tồn tại | Email đã có trong cơ sở dữ liệu | Báo lỗi Email đã được sử dụng (HTTP 409) |
| 10 | TC10 | Error Handling | Gửi Request bị lỗi định dạng JSON | Payload JSON bị mất dấu ngoặc/cú pháp | Trả về lỗi Bad Request (HTTP 400) |
