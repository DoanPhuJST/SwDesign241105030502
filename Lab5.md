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
  - Quản lý số giờ làm việc bằng thẻ chấm công của nhân viên.
  - Lấy danh sách thẻ chấm công từ cơ sở dữ liệu.
  - Hiển thị thông tin thẻ chấm công.
  - Cập nhật trạng thái thẻ chấm công.
  ### **_c) Management employee Subsystem_**



