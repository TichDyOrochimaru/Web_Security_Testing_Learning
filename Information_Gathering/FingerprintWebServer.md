# **4.1.2. Fingerprint Web Server** 
---
## *Xác thực vân tay Web Server*

**1.Khái quát**
- Xác định kiểu (type) và phiên bản (version) của Web Server mà mục tiêu đang chạy trên đó. 
- Xác thực này thường có sẵn trong các công cụ kiểm tra tự động. 
- Hiểu cách công cụ xác định phần mềm.
- Xác định type của Web Server : để kiểm tra bảo mật xem web, app đó có dễ bị tấn công hay không. 
- Xác định version : Phiên bản càng cũ mà không được update, sửa đổi, có thể dễ bị khai thác, khám phá. 
___
**2. Mục tiêu**
Phát hiện vulnerabilities dựa trên việc xác định version và type. 

---
**3. How to Test**
- Banner Grabbing (Biểu ngữ)
- Eliciting Responses (Responses được gợi ý)
- Trong Responses thì chú ý tới các Request không đúng định dạng. 
- Sử dụng automated tools để scans. 
- Cố gắng đưa ra một số responses từ Web Server. Sau đó so sánh với Database (Database về các Responses và hành động đã biết), so khớp với một số loại server đã biết. 

---
**4.Banner Grabbing**
- Gửi HTTP request đến Web Server. 
- Kiểm tra response header. 
- Thường chứa thông tin quan trọng về Network Service, software name, version. 
- FPT Server, Web Server, SSH Server, SMTP Server thường để lộ thông tin quan trọng trong banner của họ. 
- Có nhiều tools hỗ trợ cho việc này. 
- Có thể thực hiện bằng Telnet cho HTTP requests. 
- Dùng openssl cho các SSL requests. 
- Trong một số trường hợp, một số ứng dụng có bảo mật thì nó sẽ xáo trộn, sửa đổi Header. 
- Cách gửi HTTP Request và xem Header : Em đã trình bày trong file "HTTP_HTTPS.md"
- Ở đây em lấy luôn ví dụ bên trong giáo trình : 
![](https://i.imgur.com/L2yiELY.jpg)
- Trong trường hợp không hiển thị rõ ràng đề mục, có thể căn cứ vào thứ tự các trường tiêu đề, đề mục hoặc nhìn vào giá trị được hiển thị để xem. Thứ tự tham khảo : 
    - Date
    - Server
    - Last-Modified 
    - ETag (Xác thực Web cache, đại diện cho phiên bản)
    - Accept-Ranges 
    - Content-Length
    - Connection 
    - Content-Type
- Thứ tự khác : 
   - Server 
   - Date 
   - Contentype

**How to Lauch ?**
- Scan để tìm ra các open port. 
- Sau khi xác định được target, gửi các packet hoặc kiểm tra traffic để biết thông tin. 
---
**5. Gửi Request không đúng định dạng**
- Web Server có thể xác định bằng cách kiểm tra Error Response. 
- Cố tình gửi sai Request buộc Server phải xuất dữ liệu ra. 
- Khi các trường, tiêu đề, đề mục bị dấu đi, việc kiểm tra này sẽ khả thi.(Do các mặc định trang bị lỗi, nó phải đưa các yếu tố phân biệt giữa các Web Server)

---
**6.Using Automated Scanning Tools**
- Tools có thể so sánh Response từ các Web Server. Một số công cụ có thể tham khảo : 
- Netcarft : Công cụ trực tuyến để quét các trang web, kể cả Web server. 
- Nikto : Quét command line mã nguồn mở 
- Nmap : Có GUI(Giao diện đồ họa), Zenmap. 
---
**7. Cách khắc phục**
- Thông tin của Server bị lộ, không nhất thiết phải là vulnerability nhưng nó sẽ hỗ trợ kẻ tấn công khai thác các lỗ hổng có thể tồn tại. 
- Có thể có một số biện pháp : 
    - Dấu thông tin Web Server trong các Header. 
    - Sử dụng reverse proxy server để tạo lớp bảo mật giữa Web Server với Internet. 
    - Luôn update Web Server. 