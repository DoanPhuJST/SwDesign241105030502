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
**- 1.2 Đơn giản hóa sơ đồ sequence bằng Subsystem**

  ![Diagram](https://www.planttext.com/api/plantuml/png/Z99DJiD038NtFeMNiCW5ka2LqY0sHKZb0cx62WFp4smFKWx52LYmu41SWQ1IY21HMSp2bZy_lwTvVtbTgv5OYG507tn2oSe0vYqmRbcLEiQT3MDLuOuV2wUMSUEf4ue0r5eMR68Vyi2CfDW0D5XTuAsFt9AuoonnXP5yil4TksVdC1sO0dLE9Za4bXMwj-S-q313_KnziZUIxxcrBQNnNDcGqPwKLzYnrNSa7TVPiIxYn-u1A2ASR4OJguKpXQt8jxUl1GjgVw9nNdzvdCbltCTobOleM1yiNPUuPz5_9gdqnATYN4gnz8xi93r9SIe606jERlnW7m000F__0m00)
