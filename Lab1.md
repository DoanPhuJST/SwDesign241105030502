Họ tên: Đoàn Phú
Mã sinh viên: 4451050696


**Lab1: Phân tích kiến trúc và ca sử dụng hệ thống "Payroll System" trong file tài liệu yêu cầu đính kèm.**
  
  **1. Phân tích kiến trúc**

  - *Kiến trúc đề xuất: Model-VIew-Controller (MVC)*
  - *Lý do chọn kiến trúc này:*
    - Mã nguồn dễ bảo trì và mở rộng: Kiến trúc MVC giúp mã nguồn dễ bảo trì, có thể mở rộng và phát triển một cách dễ dàng.
    - Các thành phần có thể kiểm tra độc lập: Các thành phần của nó có thể được kiểm tra riêng biệt từ các thành phần người dùng.
    - Phát triển song song các thành phần: Có thể phân chia phát triển các thành phần khác nhau một cách song song.
    - Sử dụng mô hình Front Controller: Chỉ sử dụng mô hình Front Controller, trong đó mỗi yêu cầu được xử lý bởi một bộ điều khiển duy nhất.
    - Dễ dàng cho các nhóm phát triển lớn: Một nhóm lớn các nhà thiết kế và phát triển web có thể tạo và duy trì các ứng dụng web với nó.
    - Kiểm tra từng lớp và đối tượng riêng biệt: Bạn có thể kiểm tra tất cả các lớp và đối tượng riêng lẻ vì chúng đều độc lập với nhau.
    - Hành động của bộ điều khiển có thể nhóm logic: Các hành động của bộ điều khiển có thể được nhóm lại một cách logic bằng cách sử dụng các mẫu thiết kế MVC.
  - *Ý nghĩa từng thành phần:*
    _Gồm 3 thành phần chính:_
    - Model(M): là nơi lưu trữ dữ liệu và logic. Ví dụ, khi Controller truy xuất thông tin khách hàng từ cơ sở dữ liệu, dữ liệu được chuyển đổi giữa các thành phần controller hoặc giữa các yếu tố logic nghiệp vụ. 
     Nó thao tác dữ liệu và gửi lại cơ sở dữ liệu, hoặc được sử dụng để hiển thị thông tin tương tự.
    - View(V): đại diện cho cách dữ liệu được trình bày trong ứng dụng (UI). Các view được tạo ra dựa trên dữ liệu thu thập từ model. Bằng cách yêu cầu thông tin từ model, sau đó sẽ trả kết quả tới người dùng. 
     Ngoài việc hiển thị dữ liệu từ các biểu đồ, sơ đồ và bảng, view còn hiển thị dữ liệu từ các nguồn khác.
    - Controller(T): là thành phần xử lý tương tác của người dùng. Dữ liệu đầu vào của người dùng được controller phân tích và xử lí, khi người dùng thao tác bất kì với hệ thống controller sẽ gửi thông tin đến 
     model để xử lí và sau đó trả về kết quả view
  -*Biểu đồ package mô tả kiển trúc:*
![Diagram](https://www.planttext.com/api/plantuml/png/X5LBJiCm4Dtd55PNxQ8R3e3Q4XP8HLGDi9_Qqs9mx6hiW2BKax7WI5m19v0sFoTUU95vzdj-yydFr_V2EY2NfIew0d-30xB91d8oIh4ajmxJ2VkCc5_bTi4GMjGEd3IQhI57gd35uWgiPPFRzAXCZiZkj4FQ0ySwg5oFCaKE96ppyoOZ_W8MsGC9f7QGS8-4ckCbS6fpBqKgjRIEm1aQ4B0Kef8vdJL3CIfq68e-7GLSedTwRsg8Fpcdg6dQAhDIerUtDWV9WxPv_rFlBKkGtcMFv1jGF5EUF045bBU5RSXuP-p_BHrHDQBA_21JakrIwIfOc-WPb2myw8btg9e93H9kaHiI5RZ4XbX3eChwOc_Q7uC3jkIypC28zriy6YjzwUJTYk4rUuix-okZ7n3EmIXZXGnJ1X1ZoHX_QztgWHSFm3eQphDXYFtIctsipVuCwmeWXWjbL_WpEjWgfCS4Csi7KQr9DuXTum5uNZJuAtB7xa5xkMMvnYisZLTNi_EfK-I7J--KdWlpeUVNWMaK1ORK-LItYQA-nchWQrv62zIY-Dly0W00__y30000);

 **2. Cơ chế phân tích**
  - Xác thực và ủy quyền (Authentication & Authorization):
    - Lý do: Đảm bảo chỉ những người dùng hợp lệ mới có thể truy cập hệ thống.
  - Xử lý lỗi (Error Handling):
    - Lý do: Xác định cơ chế xử lý lỗi và thông báo lỗi cho người dùng.
  - Tích hợp hệ thống cũ (Legacy System Integration):
    - Lý do: Đảm bảo hệ thống mới hoạt động mượt mà với cơ sở dữ liệu quản lý dự án hiện có.
  - Caching:
    - Lý do: Sử dụng bộ nhớ đệm để cải thiện hiệu suất hệ thống.
      
 **3. Phân tích ca sử dụng Payment**
  - Sơ đồ squence:

   

    
![Diagram](https://www.planttext.com/api/plantuml/png/R971IWCn48RlynJ3NlPKIdliGGghY0UX6ANdc9ssmIIp9hF2Ffi77ybNSDQsAor2Jl_t_KCc-VxyMXUnMVeO0CgRJvYv481u2OILeVUUaYEyzNQVRQm0wkU3BwZ7Ol5fhrRmYT1nZ9G4O5x3dn7x87u65qOz1x1EEEDTx08FHF3AVMfj7h3Qs66K6awIEGJA5Tg23RXZC0c6yeTtz4iDQE15s-U1JrGwJkM8juk9dygNU0a0voBERh315HeAv0HFFZwI7BY5PiH6yIQperAkkHdvTgd2IzTQeV_vGlazoRGzFgGTWzOKJjaAzGbsFiUh6QV9UkKrfLP_xGS00F__0m00)

  - Sơ đồ mô tả lớp phân tích:

 ![Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3XTNSNPcda9HVd4g5rTgNabcIQM2Qsv1Vav-PMfgK6fnGNuUK0Og4P1OcGjameMval9Byr8IY-0oplbv9KNvEJcfHGfSoH0sJ2eujQWiCnce1vMleAkBgHct6hZLc2emNSt5vP2QbmBq90000F__0m00)

  - Giải thích

    - PaymentController: Điều khiển việc chọn phương thức thanh toán, sử dụng PaymentService để xử lý logic nghiệp vụ.

    - PaymentService: Xử lý nghiệp vụ liên quan đến việc chọn phương thức thanh toán, truy cập EmployeeRepository để lấy thông tin nhân viên và PaymentRepository để cập nhật phương thức thanh toán.

    - EmployeeRepository: Cung cấp các phương thức để truy cập thông tin nhân viên từ cơ sở dữ liệu.   

    - PaymentRepository: Cung cấp các phương thức để cập nhật phương thức thanh toán của nhân viên trong cơ sở dữ liệu.


4. Phân tích ca sử dụng Maintain Timecard
    
 **4. Phân tích ca sử dụng Maintain Timecard**
  - Sơ đồ squence:

    
![Diagram](https://www.planttext.com/api/plantuml/png/P95DQiD034RtEeNmngiGacKM8U2MqcqdDEl9M4b5voUTaGCvMnOzKgzGkSOseJ2hxtrFICpF_NjNn6RfWWSednmnfq80mk89AqDV7KL7-CJsd6se0Ehz1nVKPx5mF6lBSoHqAGIA0h2iOMw4pWiluA5HBm6iavJnELnykX71CNMnjVc6rPu3EPlR9aN9oNlA5Tg23RWXc1k6yfKT_M43EfX5_N7a6vLBYcN0XzN4H_kHhm5WD76nnGOtQBfZOC5HWAO7Hi6xzTnQeHcP7XtMlMIl__ALvYyaqxNu6ay9jAvmoZQe5vyuXyaU5YY5KzJjTXHR_QDV0000__y30000)

  - Sơ đồ mô tả lớp phân tích:

    ![Diagram](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3XTNSNPcda9HVd4g5rTgNabcIQM2Qsv1Vav-PMfgK6fnGNuUK0Og4PAPcvgSM9G25-TAoY_DIqaiGaWvv-UL5ENdvAGMAN0bGzXmkU3KehBCPA0kD045NLqi-l6fWZi0YnfCrtDnEQJcfG0z2m000F__0m00)


  - Giải thích

    - TimecardController: Điều khiển việc nộp thông tin thời gian làm việc, sử dụng TimecardService để xử lý logic nghiệp vụ.

    - TimecardService: Xử lý nghiệp vụ liên quan đến việc nộp thông tin thời gian làm việc, truy cập EmployeeRepository để lấy thông tin nhân viên và TimecardRepository để lưu thông tin thời gian làm việc.

    - EmployeeRepository: Cung cấp các phương thức để truy cập thông tin nhân viên từ cơ sở dữ liệu.

    - TimecardRepository: Cung cấp các phương thức để lưu thông tin thời gian làm việc vào cơ sở dữ liệu.
  
    
 **5. Hợp nhất kết quả phân tích**
  - Sơ đồ mô tả lớp phân tích:



