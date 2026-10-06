# Hồ sơ kiểm thử (QA/Testing) - Dự án Gốm Việt

Chào mừng bạn đến với kho lưu trữ hồ sơ kiểm thử cho **Website thương mại điện tử Gốm Việt Truyền Thống**. Kho lưu trữ này được xây dựng nhằm minh họa quy trình kiểm thử phần mềm từ khâu lập kế hoạch, thiết kế kịch bản, đến thực thi và báo cáo lỗi.

👤 **Người thực hiện:** Võ Hoàng Long
📅 **Ngày thực hiện:** 01/10/2026

---

## 🎯 1. Mục tiêu và Phạm vi kiểm thử
Dự án tập trung kiểm thử chức năng để đảm bảo chất lượng luồng trải nghiệm mua hàng cốt lõi trước khi phát hành:
* **Người dùng:** Đăng ký và đăng nhập tài khoản.
* **Giỏ hàng & Khuyến mãi:** Thêm sản phẩm, áp dụng mã giảm giá (coupon), tính phí vận chuyển và tổng tiền.
* **Luồng đặt hàng:** Thanh toán (COD, VietQR + SePay webhook) và quá trình hình thành đơn hàng.
* **Quản lý đơn hàng:** Chuyển trạng thái đơn hàng (Pending, Confirmed, Shipping...).

*(Ngoài phạm vi: VNPay/MoMo, Google SSO, kiểm thử tải, kiểm thử bảo mật chuyên sâu)*.

---

## 🛠 2. Chiến lược và Công cụ
* **Mức kiểm thử:** Functional Test (Kiểm thử thủ công) và Integration Test (API/Webhook).
* **Kỹ thuật thiết kế Test Case áp dụng:** 
  * Phân vùng tương đương (EP) & Giá trị biên (BVA).
  * Bảng quyết định (Decision Table).
  * Chuyển trạng thái (State Transition).
  * Đoán lỗi (Error Guessing).
* **Công cụ sử dụng:** Google Sheets, GitHub Issues, Postman.
* **Môi trường:** .NET 8, SQL Server LocalDB, Google Chrome, Microsoft Edge.

---

## 📊 3. Tóm tắt kết quả kiểm thử (Test Execution)
Quá trình thực thi kiểm thử đã mang lại các số liệu sau:
* **Tổng số Test Case:** 9
* **Passed:** 7 | **Failed:** 2 | **Blocked/Not Run:** 0
* **Tỷ lệ Pass:** 77.8%
* **Tổng số Bug phát hiện:** 2 Bug (Mức độ: Major)

---

## 🐞 4. Danh sách Bug tiêu biểu
Dưới đây là các lỗi nghiêm trọng (Major) được phát hiện bằng kỹ thuật Error Guessing trong luồng thanh toán, hiện đã được log chi tiết tại tab **[Issues]** của repository này:

1. **[BUG-001]: Tồn kho bị trừ âm khi hai người dùng đặt hàng cùng lúc**
   * *Mô tả:* Thiếu cơ chế xử lý đồng thời, dẫn đến việc sản phẩm có tồn kho = 1 nhưng vẫn cho phép 2 session đặt hàng thành công. 
2. **[BUG-002]: Sinh ra nhiều đơn hàng trùng lặp khi click liên tục vào nút Đặt hàng**
   * *Mô tả:* Thiếu cơ chế khóa (disable) nút bấm sau lần click đầu tiên, khiến hệ thống nhận nhiều request và tạo ra các mã đơn hàng khác nhau cho cùng một lượt thanh toán.

---

## 📁 5. Cấu trúc Repository
Các tài liệu chi tiết được lưu trữ trong thư mục gốc của repo:
* `TEST PLAN.pdf`: Kế hoạch kiểm thử tổng thể.
* `TestCases.xlsx`: Bảng chi tiết 9 kịch bản kiểm thử (Test Cases) và Danh sách lỗi (Bug List).
* `TEST REPORT.pdf`: Báo cáo tổng kết chất lượng hệ thống và khuyến nghị.
