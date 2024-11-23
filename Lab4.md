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
  - Nhập dữ liệu:
    - Người dùng (Employee) nhập giờ làm việc và các mã liên quan vào biểu mẫu TimecardForm.
  - Lưu dữ liệu:
    - Sau khi nhập xong, hệ thống thực hiện lưu thẻ công bằng cách gửi yêu cầu từ TimecardForm đến TimecardController.
    - TimecardController gọi phương thức để cập nhật (updateTimecard()) trong ProjectManagerDatabase.
    - ProjectManagerDatabase nhận dữ liệu thẻ công và lưu lại (saveTimecard).
- **1.4 Tinh chỉnh mô tả luồng sự kiện**
  - Người khởi động: Nhân viên (Employee) thực hiện hành động "Maintain Timecard."
  - Luồng sự kiện chính:
    - Nhân viên chọn duy trì thẻ chấm công trên giao diện (maintainTimecard()).
    - TimecardForm gửi yêu cầu tới TimecardController để hiển thị thẻ công hiện tại.
    - TimecardController truy vấn mã chi phí và thẻ công từ ProjectManagerDatabase.
    - Dữ liệu nhận được từ cơ sở dữ liệu được gửi lại qua TimecardForm để hiển thị.
  - Luồng sự kiện lưu:
    - Nhân viên nhập giờ làm việc và yêu cầu lưu (enterHoursForChargeNumbers()).
    - TimecardForm gửi yêu cầu lưu tới TimecardController.
    - TimecardController gửi lệnh cập nhật đến cơ sở dữ liệu qua ProjectManagerDatabase.
- **1.5 Hợp nhất các lớp và hệ thống con**
  - Hợp nhất TimecardController và ProjectManagerDatabase:
    - Vì chức năng của TimecardController chủ yếu là trung gian, bạn có thể cân nhắc gộp lớp này vào ProjectManagerDatabase để giảm số bước giao tiếp.
    - Tích hợp chức năng của TimecardForm:
    - Tích hợp phần kiểm tra và hiển thị trực tiếp vào giao diện người dùng thay vì sử dụng một lớp riêng TimecardForm, nếu cần đơn giản hóa.
  - Hệ thống sau tinh chỉnh:
    - Nhân viên tương tác trực tiếp với hệ thống thông qua giao diện chính.
    - ProjectManagerDatabase chịu trách nhiệm xử lý cả phần truy vấn lẫn cập nhật thẻ công.
    - Dữ liệu được trả về trực tiếp mà không cần qua các bước trung gian.
   





**2. Usecase: RunPayroll**
- **1.1 Mô tả sự tương tác giữa các đối tượng thiết kế**

- **1.2 Đơn giản hóa sơ đồ sequence bằng Subsystem**

![Diagram](https://www.planttext.com/api/plantuml/png/b9D1KiCm34NtEeMcgtI6NY0Bw03PToWN48xQUcBBmPONEHiBZiGLS9e0YqwOTcNPqfE-BVdhutERbA9cxm1IPmLZI0oWLXtZIvOT3J4uXnlSytjcCOpFbewHF00P3H4RtximC2CbR01WFoHbZvjxdDcd83gk76iy5wlMSE5QY8zPi9-ERw1i6g6MXeUhaIFho23va6LHuQlrR2YsKxpEExHo20NvyU9cuJAiESe5Tgr4GyvaHyh5TmCstyopA7hMKsXlXDz8kd-rFfQ0gUkbmIpjH6WaIML4R92gOER4fhixl_6OQmr_rD9xcI076xsdCSU2v6X5YrbZFrg_XHQKDZLAK7iOgbLPaUOnMQq1jaLu-GNV0000__y30000)

- **1.3 Mô tả hành vi lưu trữ**

- **1.4 Tinh chỉnh mô tả luồng sự kiện**

- **1.5 Hợp nhất các lớp và hệ thống con**

**3. Usecase: Login**
- **1.1 Mô tả sự tương tác giữa các đối tượng thiết kế**
  - Người Dùng ─> LoginForm: Khởi động quy trình đăng nhập bằng cách nhập thông tin đăng nhập.
  - LoginForm ─> LoginController: Gửi yêu cầu đăng nhập với thông tin người dùng.
  - LoginController ─> AuthenticationService: Xác thực thông tin người dùng bằng cách gọi phương thức authenticateUser().
  - AuthenticationService ─> UserDatabase: Truy xuất thông tin người dùng để xác thực.
  - UserDatabase: Trả về kết quả xác thực cho AuthenticationService.
  - AuthenticationService ─> LoginController: Trả kết quả xác thực cho LoginController.
 - LoginController ─> LoginForm: Thông báo kết quả đăng nhập (thành công hoặc thất bại).
- **1.2 Đơn giản hóa sơ đồ sequence bằng Subsystem**

![Diagram](https://www.planttext.com/api/plantuml/png/T95DJiD038NtFeMNiCW5ia1599MGK8KQSO0XTOF5n2DiJoNEne8ZSGKcANyHxT8pt_Epdp_UtbVcGJsF4S2UML2J4O2pHy9jbllmgYb6hB2ZbqpI4pOS1WqZGEWzAMw6dBZ9Cc0mR05QhAxkqi2oJZhMEBUVwujB-7al3Cx5JHAV34XhrCd1bl3l_oIvplv4ujm7voGTwO5xgh5FicSTY-OaC2aVZBG97XwD9YDNfWFD3hUoBmFDV6dmXyFgl6Ffa5MsP3dwUTkl89OxBeJ_TlpEvHZUAVeON-7Q6hjiHcPOph0E76a702kINJdd9m000F__0m00)

- **1.3 Mô tả hành vi lưu trữ**
  - Người dùng bắt đầu đăng nhập:
    - Người dùng (User) tương tác với giao diện LoginForm bằng cách nhập tên đăng nhập và mật khẩu, sau đó gửi yêu cầu đăng nhập bằng cách gọi phương thức login().
  - Xác thực thông tin đăng nhập:
    - LoginForm gọi phương thức authenticateUser() trên LoginController để xử lý thông tin đăng nhập.
    - LoginController yêu cầu AuthenticationService xác thực thông tin người dùng.
    - AuthenticationService gọi phương thức getUserInfo() từ UserDatabase để lấy thông tin người dùng dựa trên tên đăng nhập.
    - UserDatabase trả về thông tin người dùng cho AuthenticationService.
    - AuthenticationService kiểm tra thông tin và xác thực người dùng.
  - Thông báo kết quả:
    - AuthenticationService trả kết quả xác thực (thành công hoặc thất bại) về LoginController.
    - LoginController gửi thông báo kết quả đăng nhập trở lại LoginForm.
    - LoginForm hiển thị kết quả đăng nhập cho người dùng (chào mừng khi đăng nhập thành công hoặc thông báo lỗi khi thất bại).
- **1.4 Tinh chỉnh mô tả luồng sự kiện**

- **1.5 Hợp nhất các lớp và hệ thống con**
  - LoginForm: Chứa các trường nhập liệu cho tên đăng nhập và mật khẩu, và các phương thức để gửi yêu cầu đăng nhập.
  - LoginController: Đóng vai trò là trung gian, xử lý yêu cầu đăng nhập từ LoginForm và giao tiếp với AuthenticationService.
  - AuthenticationService: Xử lý việc xác thực người dùng, xác minh thông tin đăng nhập bằng cách truy vấn UserDatabase.
  - UserDatabase: Lưu trữ thông tin người dùng và cung cấp phương thức để truy xuất thông tin khi cần thiết.


  
