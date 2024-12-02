Họ và tên: Đoàn Phú        -        Mã sinh viên: 4451050696

# Payroll System Subsystem Design
  - Hệ thống được chia thành 4 hệ thống con chính, mỗi hệ thống con đảm nhiệm các chức năng cụ thể
## **1 Distribute Subsystem Behavior to Subsystem Elements**
  ### **_a) Maintain_Timecard Subsystem_**
  - Chức năng chính: Quản lý thời gian làm việc và trạng thái thẻ chấm công.
  - Thành phần chính:
    - TimecardForm: Giao diện nhập liệu giờ làm việc và trạng thái thẻ.
    - TimecardController: Xử lý nghiệp vụ một cách logic liên quan đến thông tin thẻ chấm công.
    - ProjectManagementDatabase: Lấy danh sách thông tin của thẻ chấm công.
  ### **_b) Run_Payroll Subsystem_**
  - Chức năng chính: Tính toán lương và thanh toán lương cho nhân viên.
  - Thành phần chính:
    - SystemClockInterface: Hiển thị để người dùng tương tác với hệ thống  
    - PayrollController: Quản lý logic nghiệp vụ liên quan đến tính toán lương.
    - BankSystemProxy: Kết nối với ngân hàng để chuyển khoản lương.
    - PrinterServiceProxy: In phiếu tiền lương.
    - PayrollDatabase: Lưu trữ thông tin tiền lương.
  ### **_c) Management employee Subsystem_**
  - Chức năng chính: Quản lý thông tin nhân viên và trạng thái (đang làm việc, bị xóa, nghỉ việc).
  - Thành phần chính:
    - Employee: Đối tượng lưu trữ thông tin nhân viên.
    - EmployeeDatabase: Cơ sở dữ liệu nhân viên.
  ### **_d) Scheduler Subsystem_**
  - Chức năng chính: Kích hoạt quy trình tính lương theo lịch đẫ cài đặt .
  - Thành phần chính:
    - SystemClock: Kích hoạt quy trình Run Payroll theo thời gian được xác định trước.
## **2 Document Subsystem Elements**
  ### **_a) Timecard Subsystem_**
    - Quản lý thông tin giờ làm việc của nhân viên.
    - Lấy danh sách thẻ chấm công từ cơ sở dữ liệu.
    - Cập nhật trạng thái và hiển thị thông tin thẻ chấm công.
  ### b) Payroll Processing Subsystem
    - Xử lý tính toán lương cho từng nhân viên dựa trên giờ làm việc theo trạng thái của tháng làm việc đó.
    - Thực hiện thanh toán chuyển khoản thông qua ngân hàng hoặc in phiếu lương nếu nhận tiền mặt.
    - Lưu thông tin tiền lương vào cơ sở dữ liệu.
  ### **_c) Employee Management Subsystem_**
    - Lưu trữ thông tin nhân viên.
    - Cập nhật trạng thái nhân viên (đang làm việc hoặc bị xóa).
    - Cung cấp thông tin cho các hệ thống con khác.
  ### **_d) Scheduler Subsystem_**
    - Kích hoạt quy trình tính lương tự động vào thời gian xác định sẵn.
## **3 Describe Subsystem Dependencies**
  - Timecard Subsystem phụ thuộc vào Employee Management Subsystem để lấy các thông tin nhân viên liên quan đến việc tính toán lương.
  - Payroll Processing Subsystem phụ thuộc vào:
    - Employee Management Subsystem để lấy danh sách các nhân viên có trạng thái("đang làm việc").
    - Timecard Subsystem để lấy thông tin giờ làm việc của từng nhân viên.
  - Scheduler Subsystem không phụ thuộc vào các hệ thống con nào nhưng kích hoạt quy trình hoạt động Payroll Processing Subsystem.
## **4 Checkpoint**
  - Phân chia hợp lý: Các hệ thống đảm nhận mỗi nhiệm vụ khác nhau, với các thành phần được phân chia rõ ràng.
  - Tính dễ bảo trì: Các hệ thống con dễ bảo trì khi có sự thay đổi và các sự cố bên ngoài.
  - Phụ thuộc rõ ràng: Các hệ thống con có quan hệ với nhau để cùng thực hiện một nhiệm vụ nào đó.
  - Tính mở rộng: Các hệ thống con có thể mở rộng hoặc thay đổi mà không ảnh hưởng đến toàn bộ hệ thống.
  
      



