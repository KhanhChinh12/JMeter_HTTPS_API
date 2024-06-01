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

#### Kiểm tra lần 1

 - Thiết lập Number of Threads (users) là "1 user" và Ramp-Up Period là "1 giây".

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
 
#### Kiểm tra lần 2

 - Với thiết lập Number of Threads (users) là 4 users. Ramp-up period (seconds) ở đây là 1 giây. Loop Count được đặt là 2 lần. Tùy chọn Infinite cho phép chạy lặp lại vô hạn.

![Picture7](https://github.com/KhanhChinh12/JMeter_HTTPS_API/assets/145414389/27bf2095-faa9-47d2-a654-6e24d47be0b3)

 - Kết quả nhận được ở lần kiểm tra thứ 2, lần lượt:
   + Mỗi yêu cầu HTTP được liệt kê theo thứ tự thực hiện. Các yêu cầu Blue Origin và Destination được hiển thị với biểu tượng đánh dấu thành công (màu xanh).
   + Chi tiết kết quả của yêu cầu HTTP:
     + Thread Name: Tên của Thread thực hiện yêu cầu, ở đây là User 1-2.
     + Load time: Thời gian tải trang (627 ms).
     + Connect Time: Thời gian kết nối (11 ms).
     + Latency: Độ trễ (109 ms).
     + Size in bytes: Kích thước của dữ liệu trả về (53247 bytes).
     + Sent bytes: Số byte đã gửi (398 bytes).
     + Headers size in bytes: Kích thước của header trả về (3173 bytes).
     + Body size in bytes: Kích thước của nội dung trả về (50074 bytes).
     + Sample Count: Số lần mẫu (1).
     + Error Count: Số lỗi (0).
     + Response code: Mã phản hồi HTTP (200).

![Picture8](https://github.com/KhanhChinh12/JMeter_HTTPS_API/assets/145414389/ac5796a6-9bfc-4423-9c49-5962057ee9c0)

 - Đánh giá kết quả kiểm tra lần 2:
   +  Trang web có thời gian phản hồi và độ trễ khá tốt.
   +  Máy chủ phản hồi nhanh và ổn định, không gặp lỗi khi xử lý yêu cầu.
   +  Kết quả này cho thấy trang web Blue Origin đang hoạt động tốt dưới điều kiện kiểm tra hiện tại.

![Picture9](https://github.com/KhanhChinh12/JMeter_HTTPS_API/assets/145414389/098988b1-98a0-42bb-bdbb-adb0c7639844)

### Đánh giá tổng quan qua 2 lần kiểm tra hiệu năng của Blue Origin

 - Thời gian lấy mẫu (Sample Time):
   + Ở lần kiểm tra đầu tiên, thời gian lấy mẫu cho Blue Origin là 3460 ms, trong khi đó lần kiểm tra thứ hai giảm đáng kể xuống trung bình 1223 ms. Điều này cho thấy rằng kết quả lần đầu có thể bị ảnh hưởng bởi yếu tố nào đó (có thể do tải mạng hoặc các yếu tố khác) nhưng sau đó đã hoạt động ổn định hơn.
   + Thời gian lấy mẫu của Destination cũng giảm từ 1856 ms xuống còn 1206 ms. Đây là một cải thiện rõ rệt.
 
 - Dung lượng dữ liệu gửi (Sent Bytes):
   + Không có sự thay đổi lớn về dung lượng dữ liệu gửi giữa hai lần kiểm tra cho cả Blue Origin và Destination. Điều này cho thấy các yêu cầu gửi đi có kích thước tương tự nhau trong cả hai lần kiểm tra.

 - Độ trễ (Latency):
   + Độ trễ của Blue Origin đã giảm từ 221 ms xuống 121 ms, cho thấy hiệu suất đã được cải thiện trong lần kiểm tra thứ 2.
   + Độ trễ của Destination cũng giảm từ 211 ms xuống 115 ms.

### Kết luận chung: 
 - Hiệu suất của trang web Blue Origin đã cải thiện rõ rệt giữa hai lần kiểm tra, đặc biệt là về thời gian phản hồi và độ trễ.
 - Các chỉ số về dung lượng dữ liệu gửi không thay đổi nhiều, cho thấy các yêu cầu gửi đi là tương tự nhau trong cả hai lần kiểm tra.
 - Trang web Blue Origin đã có sự cải thiện về hiệu suất trong lần kiểm tra thứ 2 với thời gian phản hồi nhanh hơn và độ trễ thấp hơn.

## Kiểm tra hiệu năng của API thời tiết

### Mô tả: 
Sử dụng Apache JMeter để kiểm tra hiệu suất của API thời tiết.

### Các bước thực hiện quá trình kiểm tra: 
 -  Thực hiện cấu hình một yêu cầu HTTP GET đến API thời tiết "api.weatherapi.com/v1/current.json" với 2 tham số: "key" và "q". Tham số "key" chứa khóa "API key" và tham số "q" chứa tên thành phố "London".

![Picture12](https://github.com/KhanhChinh12/JMeter_HTTPS_API/assets/145414389/b0e87679-885f-4742-822a-473f4f5ccba3)

 - Cài đặt User (Thread Group) để thực hiện kiểm tra hiệu suất của API với 6 người dùng giả lập, thời gian khởi động trong 2 giây và mỗi người dùng thực hiện các yêu cầu 1 lần.

![Picture11](https://github.com/KhanhChinh12/JMeter_HTTPS_API/assets/145414389/d5e59a81-627b-41e5-b8dc-06939462b5ec)

 - Thiết lập Response Assertion để kiểm tra mã phản hồi của API.

 - Nếu Response Code bằng 200 thì yêu cầu thực hiện thành công, còn nếu không thì yêu cầu thực hiện thất bại. 

![Picture13](https://github.com/KhanhChinh12/JMeter_HTTPS_API/assets/145414389/81c5371e-bdad-4739-8660-5bba837b1216)

 - Kết quả hiển thị ở "View Results Tree" cho lần kiểm tra này:
   + Tên: Weather API.
   + Tên luồng: User 1-2.
   + Thời gian tải: 179 ms.
   + Thời gian kết nối: 90 ms.
   + Độ trễ: 179 ms.
   + Kích thước (byte): 1454 byte.
   + Byte đã gửi: 179 byte.
   + Kích thước tiêu đề (byte): 647 byte.
   + Kích thước nội dung (byte): 807 byte.
   + Số lượng mẫu: 1.
   + Số lỗi: 0.
   + Loại dữ liệu: "text"|"bin" (text).
   + Mã phản hồi: 200.
   + Thông báo phản hồi: OK.
 
 - API đã trả về thành công với thời gian phản hồi trung bình là 179 ms.

![Picture14](https://github.com/KhanhChinh12/JMeter_HTTPS_API/assets/145414389/9eb1d4e9-8729-4f97-ad8c-0e4a5a7c6a77)

### Đánh giá:
 - Điểm mạnh:
   + Thời gian phản hồi nhanh: Thời gian phản hồi trung bình cho API là 179 ms, đây là thời gian phản hồi khá nhanh. Cho thấy API có thể xử lý các yêu cầu một cách nhanh chóng và hiệu quả.
   + Tỷ lệ lỗi thấp: API có độ ổn định cao và ít xảy ra lỗi.
   + Kích thước dữ liệu nhỏ: Kích thước dữ liệu trung bình cho phản hồi API là 1454 byte, đây là kích thước dữ liệu tương đối nhỏ. API có thể truyền tải dữ liệu một cách hiệu quả.

 - Điểm yếu:
   + Thời gian tải trung bình cho API là 179 ms, đây là một thời gian tải khá lâu.
   + Độ trễ trung bình cho API là 179 ms, đây là một độ trễ khá cao.

![Picture15](https://github.com/KhanhChinh12/JMeter_HTTPS_API/assets/145414389/edb32843-8fec-405d-b2f9-144b968a2e6e)

### Kết luận: 

Nhìn chung, API "Weather API" có hiệu năng khá tốt. Tuy nhiên, có một số điểm yếu cần được cải thiện, chẳng hạn như thời gian tải và độ trễ.










