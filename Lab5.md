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
  ### **_b) Run_Payroll_**
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
    - Employee: Thực thể lưu trữ thông tin nhân viên.
    - EmployeeDatabase: Cơ sở dữ liệu nhân viên.



