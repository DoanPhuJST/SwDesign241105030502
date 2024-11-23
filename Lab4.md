Họ và tên: Đoàn Phú  Mã sinh viên: 4451050696
Lab 4 - Thiết kế ca sử dụng cho hệ thống "Payroll System" dựa vào kết quả phân tích ca sử dụng và các phần tử thiết kế

**1. Usecase: Maintain Timecard**
- **1.1 Mô tả sự tương tác giữa các đối tượng thiết kế**
  - Employee ─> TimecardForm: Khởi động quy trình để duy trì thẻ chấm công.
  - TimecardForm ─> TimecardController: Yêu cầu hiển thị thẻ chấm công hiện tại.
  - TimecardController ─> ProjectManagementDatabase: Truy xuất mã chi phí và dữ liệu thẻ chấm công hiện tại.
  - TimecardForm: Hiển thị thẻ chấm công đã nhận.
  - Employee –> TimecardForm: Nhập giờ làm và lưu lại.
  - TimecardController -> ProjectManagementDatabase: cập nhật và lưu thẻ công lại vào cơ sở dữ liệu.
- **1.2 Đơn giản hóa sơ đồ sequence bằng Subsystem**

  ![Diagram](https://www.planttext.com/api/plantuml/png/Z99DJiD038NtFeMNiCW5ia2LqY0sHKZb0cvYXO7v2RO7AMTZmP6u0eDA8L8JbSKiRFdpytkQp_UFZHg9vU01zCL5bAGCOCuyuuvLQM3SsrIg2lVycZbsZ5j7Wr00eCwIO1j6doPc9CKMeCNg1XzTu8walqqIQWpaefLtwbvTmtnW3ZGfcYJlMMhidOwUfWNgR-gRVP3qp9tjA9PpPKj61rAkSM1hdaW6RbBFkegVkaSWYt2q1KsiLiuKjYo_tduMhAYTHNFkSI6_ie_bBcNHKXyjtUTmOD5_9gdqnfTYN4inZptPHNgMubmC03OS-_B1lW000F__0m00)


- **1.3 Mô tả hành vi lưu trữ**

**2. Usecase: RunPayroll**
- **1.1 Mô tả sự tương tác giữa các đối tượng thiết kế**
- **1.2 Đơn giản hóa sơ đồ sequence bằng Subsystem**

![Diagram](https://www.planttext.com/api/plantuml/png/b9D1KiCm34NtEeMcgtI6NY0Bw03PToWN48xQUcBBmPONEHiBZiGLS9e0YqwOTcNPqfE-BVdhutERbA9cxm1IPmLZI0oWLXtZIvOT3J4uXnlSytjcCOpFbewHF00P3H4RtximC2CbR01WFoHbZvjxdDcd83gk76iy5wlMSE5QY8zPi9-ERw1i6g6MXeUhaIFho23va6LHuQlrR2YsKxpEExHo20NvyU9cuJAiESe5Tgr4GyvaHyh5TmCstyopA7hMKsXlXDz8kd-rFfQ0gUkbmIpjH6WaIML4R92gOER4fhixl_6OQmr_rD9xcI076xsdCSU2v6X5YrbZFrg_XHQKDZLAK7iOgbLPaUOnMQq1jaLu-GNV0000__y30000)


  
