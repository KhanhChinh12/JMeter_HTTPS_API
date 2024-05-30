# JMeter_HTTPS_API
## Kiểm tra hiệu năng trang web Blue Origin

### Mô tả: 
Sử dụng Apache JMeter để kiểm tra hiệu suất của trang web Blue Origin.

### Các bước thực hiện quá trình kiểm tra: 
 - Đầu tiên, thêm một User (Thread Group) vào Test Plan. Ở User sẽ xác định số lượng người dùng ảo (threads), thời gian khởi động (ramp-up period) và số lần lặp lại (loop count) cho thử nghiệm.
 - Thêm HTTP Request Sampler: Trong User, thêm một HTTP Request Sampler để xác định các yêu cầu HTTP sẽ được gửi tới trang web Blue Origin. Đặt "Server Name or IP" là "www.blueorigin.com" và "Path" là "/" để gửi yêu cầu tới trang chủ.

![Picture1](https://github.com/KhanhChinh12/JMeter_HTTPS_API/assets/145414389/4f8e4543-788e-49d6-ab34-e115beccc98b)

 - Thêm HTTP Request Sampler tiếp theo là "Destination". Với "Server Name or IP" là "www.blueorigin.com" và "Path" là /destinations/.

![Picture2](https://github.com/KhanhChinh12/JMeter_HTTPS_API/assets/145414389/d3bc0907-be1e-41cf-b80e-2c0f7da1c4a4)

 - Kiểm tra lần 1, thiết lập Number of Threads (users) là "1 user" và Ramp-Up Period là "1 giây".

![Picture5](https://github.com/KhanhChinh12/JMeter_HTTPS_API/assets/145414389/5d317364-15ad-4b6b-9bca-87238a6322a4)

- Sử dụng Listeners "View Results Tree" để thu thập và xem kết quả kiểm tra hiệu suất của website Blue Origin.

![Picture3](https://github.com/KhanhChinh12/JMeter_HTTPS_API/assets/145414389/40d04a1f-bb9e-41c3-b0fb-09c753979420)

 - Kết quả thu được hiển thị ở "View Results Tree" cho Blue Origin lần lượt:
   + Thời gian tải: 311 ms
   + Thời gian kết nối: 108 ms
   + Độ trễ: 310 ms
   + Kích thước phản hồi:
     + Kích thước trong byte: 174 byte
     + Byte đã gửi: 120 byte
     + Kích thước tiêu đề trong byte: 160 byte
     + Kích thước nội dung trong byte: 14 byte
    + Thông tin bổ sung:
      + Số lần lấy mẫu: 1
      + Lỗi: 0
      + Loại dữ liệu: "text"
      + Mã phản hồi: 308
      + Thông báo phản hồi: Permanent Redirect
      + Kiểu nội dung: text/plain
      + Mã hóa dữ liệu: null

  ![Picture4](https://github.com/KhanhChinh12/JMeter_HTTPS_API/assets/145414389/fc95da84-939f-48bc-8c77-63aafd6b5f22)

 - Đánh giá: hiệu suất trang web Blue Origin trong lần thử nghiệm 1 được đánh giá là tốt.
   + Thời gian tải trang: 311 ms là thời gian tải trang khá nhanh, nằm trong mức chấp nhận được.
   + Kết nối: Thời gian kết nối 108 ms và độ trễ 310 ms cũng nằm trong mức bình thường.
   + Kích thước phản hồi: Kích thước phản hồi 174 byte là một kích thước nhỏ, giúp giảm thiểu thời gian tải trang.

 ![Picture6](https://github.com/KhanhChinh12/JMeter_HTTPS_API/assets/145414389/3437f996-4712-4763-b82f-6504f615cbd4)






