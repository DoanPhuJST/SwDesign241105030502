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
- **2.1 Mô tả sự tương tác giữa các đối tượng thiết kế**
  - Khởi động quy trình:
    - SystemClock gửi thông báo đến PayrollController về thời gian chạy bảng lương.
  - Kiểm tra ngày thanh toán:
    - PayrollController kiểm tra ngày hiện tại để xác định xem có phải là ngày thanh toán không bằng cách gọi is payday().
  - Lấy số tiền thanh toán:
    - Nếu đây là ngày thanh toán, PayrollController gọi get pay amount() để lấy số tiền cho từng nhân viên.
  - Thu thập thông tin thẻ công:
    - Với mỗi nhân viên, PayrollController yêu cầu Timecard cung cấp thông tin giờ làm bằng cách gọi get timecard info().
  - Tính toán lương:
    - Dựa trên thông tin từ Timecard, PayrollController gọi calculatePay() để tính toán số tiền phải trả cho nhân viên.
  - Chọn phương thức thanh toán:
    - PayrollController hỏi nhân viên về phương thức thanh toán thông qua get payment method(). Nếu nhân viên chọn chuyển khoản ngân hàng, PayrollController sẽ đi đến bước gọi get bank info() để lấy thông tin tài khoản.
  - Gửi giao dịch tới ngân hàng:
    - PayrollController sẽ gửi thông tin giao dịch tới BankSystem bằng cách gọi send bank transaction(Paycheck, bank info) cho phép thực hiện thanh toán trực tiếp vào tài khoản của nhân viên.
  - In phiếu lương khi cần:
    -Nếu nhân viên chọn nhận séc, PayrollController sẽ gọi print(Paycheck) từ Printer để in bảng lương cho nhân viên.
- **2.2 Đơn giản hóa sơ đồ sequence bằng Subsystem**

![Diagram](https://www.planttext.com/api/plantuml/png/b9D1KiCm34NtEeMcgtI6NY0Bw03PToWN48xQUcBBmPONEHiBZiGLS9e0YqwOTcNPqfE-BVdhutERbA9cxm1IPmLZI0oWLXtZIvOT3J4uXnlSytjcCOpFbewHF00P3H4RtximC2CbR01WFoHbZvjxdDcd83gk76iy5wlMSE5QY8zPi9-ERw1i6g6MXeUhaIFho23va6LHuQlrR2YsKxpEExHo20NvyU9cuJAiESe5Tgr4GyvaHyh5TmCstyopA7hMKsXlXDz8kd-rFfQ0gUkbmIpjH6WaIML4R92gOER4fhixl_6OQmr_rD9xcI076xsdCSU2v6X5YrbZFrg_XHQKDZLAK7iOgbLPaUOnMQq1jaLu-GNV0000__y30000)

- **2.3 Mô tả hành vi lưu trữ**
  - Khởi động quy trình tính lương:
    - System Clock khởi động quy trình bằng cách gọi phương thức run payroll(). Quy trình này được kiểm soát bởi PayrollController.
  - Kiểm tra ngày thanh toán:
    - PayrollController kiểm tra xem đây có phải là ngày thanh toán hay không bằng cách gọi phương thức is payday().
  - Lấy thông tin về số tiền thanh toán:
    - Nếu đúng là ngày thanh toán, PayrollController sẽ gọi get pay amount() để lấy thông tin về số tiền phải trả cho từng nhân viên.
  - Thu thập thông tin thẻ công:
    - Đối với mỗi nhân viên, PayrollController sẽ yêu cầu thông tin thẻ công bằng cách gọi get timecard info() từ Timecard, thu thập số giờ làm việc.
  - Tính toán tiền lương:
    - Gọi phương thức calculatePay() để tính toán số tiền lương dựa trên thông tin thẻ công và phương thức thanh toán.
  - Chọn phương thức thanh toán:
    - PayrollController sẽ yêu cầu nhân viên chọn phương thức thanh toán bằng cách gọi get payment method(). Tùy thuộc vào lựa chọn của nhân viên (trực tiếp hoặc in séc), quy trình sẽ tiếp tục khác nhau.
  - Lưu thông tin ngân hàng:
    - Nếu nhân viên chọn trực tiếp vào tài khoản ngân hàng, PayrollController sẽ gọi get bank info() để lấy thông tin cần thiết.
  - Tạo và gửi giao dịch ngân hàng:
    - Nếu là thanh toán trực tiếp, PayrollController sẽ tạo một giao dịch với BankSystem bằng cách gọi send bank transaction(Paycheck, bank info), trong đó Paycheck chứa các thông tin thanh toán như số tiền.
    - Ngân hàng sẽ xử lý và gửi giao dịch thông qua send transaction().
  - In bảng lương nếu cần:
  - Nếu nhân viên chọn in, PayrollController sẽ yêu cầu Printer in bảng lương bằng cách gọi print(Paycheck).
  - Kết thúc quy trình:
    - Chương trình hoàn thành quy trình tính lương với việc gửi thông báo cho phù hợp, và lưu giữ tất cả thông tin hợp lệ cho việc báo cáo sau này
- **2.4 Tinh chỉnh mô tả luồng sự kiện**
Luồng sự kiện chính (Run Payroll):
  - Khởi động quá trình:
  - Sự kiện bắt đầu: SystemClock kích hoạt quy trình tính bảng lương bằng cách gửi thông báo cho PayrollController với phương thức run payroll().
  - Xác định ngày thanh toán:
    - PayrollController kiểm tra xem hiện tại có phải là ngày thanh toán không bằng cách gọi is payday().
  - Nếu không phải: Gửi thông báo đến nhân viên và kết thúc quy trình.
  - Lấy thông tin nhân viên:
  - Cho mỗi nhân viên trong hệ thống:
    - PayrollController gọi get pay amount() để lấy số tiền thanh toán.
    - PayrollController yêu cầu thông tin công việc từ Timecard và PurchaseOrder (nếu có), phương thức get timecard info() cho giờ làm việc và get PO info() cho các giao dịch hoa hồng.
  - Tính lương:
    - PayrollController thực hiện calculatePay() với thông tin đã thu thập để tính toán tổng lương cho từng nhân viên.
  - Chọn và xác nhận phương thức thanh toán:
  - PayrollController hỏi nhân viên về phương thức thanh toán:
  - Nếu nhân viên chọn chuyển khoản trực tiếp:
    - Lấy thông tin ngân hàng từ get bank info().
    - Tạo giao dịch thanh toán và gửi đến BankSystem bằng send bank transaction(Paycheck, bank info) để thực hiện chuyển khoản.
  - Nếu nhân viên chọn in séc:
  - Gọi phương thức print(Paycheck) từ Printer để tạo phiếu lương.
  - Kết thúc quy trình:
    - Sau khi hoàn tất tất cả các giao dịch, gửi thông báo cho nhân viên về kết quả thanh toán (qua email hoặc tin nhắn).
- **2.5 Hợp nhất các lớp và hệ thống con**
  - Các lớp chính
    - Payroll System:
      - Phương thức: runPayroll(), isPayday(), getPayAmount(), calculatePay(), getPaymentMethod(), getBankInfo()
      - Thuộc tính: Danh sách nhân viên.
    - Employee:
      - Phương thức: getTimecardInfo(), getPaymentMethod(), getBankInfo()
      - Thuộc tính: ID, tên, thông tin ngân hàng, số giờ làm việc.
    - Timecard:
      - Phương thức: getTimecardInfo(), save()
      - Thuộc tính: Thông tin về giờ làm việc.
    - BankSystem:
      - Phương thức: sendTransaction(Paycheck, bankInfo)
      - Thuộc tính: Danh sách giao dịch.
    - Printer:
      - Phương thức: print(Paycheck)
      - Thuộc tính: Loại máy in
  - Hệ thống con
    - Hệ thống Giao dịch Ngân hàng: Xử lý các giao dịch tài chính, thông qua lớp BankSystem.
    - Hệ thống In ấn: Quản lý việc in các phiếu lương thông qua lớp Printer.



**3. Usecase: Login**
- **3.1 Mô tả sự tương tác giữa các đối tượng thiết kế**
  - Người Dùng ─> LoginForm: Khởi động quy trình đăng nhập bằng cách nhập thông tin đăng nhập.
  - LoginForm ─> LoginController: Gửi yêu cầu đăng nhập với thông tin người dùng.
  - LoginController ─> AuthenticationService: Xác thực thông tin người dùng bằng cách gọi phương thức authenticateUser().
  - AuthenticationService ─> UserDatabase: Truy xuất thông tin người dùng để xác thực.
  - UserDatabase: Trả về kết quả xác thực cho AuthenticationService.
  - AuthenticationService ─> LoginController: Trả kết quả xác thực cho LoginController.
 - LoginController ─> LoginForm: Thông báo kết quả đăng nhập (thành công hoặc thất bại).
- **3.2 Đơn giản hóa sơ đồ sequence bằng Subsystem**

![Diagram](https://www.planttext.com/api/plantuml/png/T95DJiD038NtFeMNiCW5ia1599MGK8KQSO0XTOF5n2DiJoNEne8ZSGKcANyHxT8pt_Epdp_UtbVcGJsF4S2UML2J4O2pHy9jbllmgYb6hB2ZbqpI4pOS1WqZGEWzAMw6dBZ9Cc0mR05QhAxkqi2oJZhMEBUVwujB-7al3Cx5JHAV34XhrCd1bl3l_oIvplv4ujm7voGTwO5xgh5FicSTY-OaC2aVZBG97XwD9YDNfWFD3hUoBmFDV6dmXyFgl6Ffa5MsP3dwUTkl89OxBeJ_TlpEvHZUAVeON-7Q6hjiHcPOph0E76a702kINJdd9m000F__0m00)

- **3.3 Mô tả hành vi lưu trữ**
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
- **3.4 Tinh chỉnh mô tả luồng sự kiện**
  - Người dùng (User):
    - Người dùng mở giao diện đăng nhập và nhập tên đăng nhập, mật khẩu, sau đó nhấn nút xác nhận.
    - Phương thức startLogin() trên LoginForm được gọi, khởi động quy trình đăng nhập.
  - LoginForm:
    - Thu thập thông tin đăng nhập từ người dùng (tên đăng nhập và mật khẩu).
    - Gửi yêu cầu requestLogin() đến LoginController để xử lý thông tin đăng nhập.
    - Xác thực thông tin đăng nhập:
  - LoginController:
    - Nhận yêu cầu từ LoginForm và gọi phương thức authenticateUser() của AuthenticationService để xác minh thông tin.
  - AuthenticationService:
    - Xử lý xác thực bằng cách gọi phương thức retrieveLoginInformation() trên UserDatabase để truy vấn thông tin tài khoản của người dùng dựa trên tên đăng nhập.
  - UserDatabase:
    - Truy xuất thông tin tài khoản (bao gồm tên đăng nhập, mật khẩu được mã hóa, và các thông tin liên quan khác) từ cơ sở dữ liệu.
    - Trả kết quả về cho AuthenticationService qua phương thức returnResult().
  - AuthenticationService:
    - So sánh thông tin được cung cấp bởi người dùng (từ LoginController) với dữ liệu nhận được từ UserDatabase.
    - Nếu thông tin hợp lệ, xác thực thành công. Nếu không, xác thực thất bại.
    - Trả kết quả (thành công hoặc thất bại) về LoginController.
  - Thông báo kết quả:
    - LoginController:
      - Nhận kết quả xác thực từ AuthenticationService.
      - Gửi thông báo kết quả (thành công hoặc thất bại) trở lại cho LoginForm qua phương thức returnResult().
    - LoginForm:
    - Hiển thị thông báo phù hợp cho người dùng:
      - Nếu thành công: Chào mừng người dùng và chuyển họ đến màn hình chính của hệ thống.
      - Nếu thất bại: Hiển thị thông báo lỗi và yêu cầu người dùng thử lại.
- **3.5 Hợp nhất các lớp và hệ thống con**
  - LoginForm: Chứa các trường nhập liệu cho tên đăng nhập và mật khẩu, và các phương thức để gửi yêu cầu đăng nhập.
  - LoginController: Đóng vai trò là trung gian, xử lý yêu cầu đăng nhập từ LoginForm và giao tiếp với AuthenticationService.
  - AuthenticationService: Xử lý việc xác thực người dùng, xác minh thông tin đăng nhập bằng cách truy vấn UserDatabase.
  - UserDatabase: Lưu trữ thông tin người dùng và cung cấp phương thức để truy xuất thông tin khi cần thiết.


  
