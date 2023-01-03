# **4.1.2. HTTP and HTTPS** 
---
## *Giao thức HTTP và HTTPS*

**1.Khái niệm**

a. HTTP
- Hyper Text Transfer Protocol.
- Giao thức truyền văn bản siêu tốc.
- Hoạt động dựa trên mô hình Client - Server. 
- Là giao thức nằm trên TCP Layer. Không cung cấp tính bảo mật.  
- Kém an toàn hơn HTTP nhưng page loading nhanh hơn HTTPS.
- Giao thức không trạng thái, khi thực hiện xong công việc giữa Web Browser và Server thì kết nối sẽ bị mất. 

b. HTTPS 
- Chắc là phiên bản an toàn hơn so với giao thức HTTPS.(Có sử dụng Private key và Public key)
- Chuyển dữ liệu ở dạng mã hóa. 
- Khác với HTTP chủ yếu ở chỗ HTTPS sử dụng chứng chỉ SSL. 
- SSL mã hóa dữ liệu mà Client gửi đến Server. 
![Sự khác nhau giữa HTTP và HTTPS](https://i.imgur.com/dwVZvYh.png)

c. HTTP Request 
- Client gửi HTTP request cho server dưới dạng request message bao gồm một số thông tin : 
  - A Request Line
  - Không hoặc nhiều Header (General|Request|Enity) sau cùng là CRLF. 
  - Một dòng trống báo hiệu đã hết Header. 
  - Body.
- Request Line 
  - Bắt đầu bằng một phương thúc-  Request-URI - Protocol Version - CRLF.(Ngăn cách nhau bởi Space)
  - Request-Line = Method SP Request-URI SP HTTP-Version CRLF.
  
d. Client - Server 
- Thông thường Client là Web Browser của máy khác. 
- Server là host.
![Mô hình Client-Server](https://i.imgur.com/mguQGHx.png)
- User nhập URL -> Browser gửi request đến DNS Server. 
- DNS Server tra  địa chỉ Web Server -> Phản hổi Response với IP của Web Server. 
- Nhận được Response thì Browser gửi HTTP/HTTPS Request cho Web Server(do DNS Server cung cấp). 
- Server gửi các file cần thiết của trang web. 
- Browser render files -> Trang web được hiển thị.

e. HTTP/1.1
- Cái này em vẫn chưa hiểu rõ lắm về HTTP/1.1 với HTTP/1.0. 
- Theo ý hiểu thì phiên bản HTTP/1.1 sẽ connect được, hoạt động được với proxy. Cho phép gửi nhiều request một lúc. 
- Khối lượng công việc cần xử lý với tốc độ chắc nhanh hơn. Có nhiều domain name cùng trỏ đến địa chỉ IP thì máy chủ 
vẫn phân biệt được các trang web mình muốn target tới là trang nào.(Trường hợp nhiều tên miền cùng chia sẻ một địa chỉ 
Internet)

f. REQUEST-URI 
- Mã định danh source, xác định source nào sẽ được áp dụng request. 
- Để chỉ định một URI, thường thường người ta sử dụng : Request-URI = "*" | absoluteURI | abs_path | authority
    - Dấu * : Sử dụng khi HTTP Request không áp dụng cụ thể cho 1 source nào hết mà áp dụng cho chính server đó. 
    - absURI : Sử dụng khi HTTP Request thực hiện tới proxy. Proxy đó sẽ chuyển tiếp request từ cache rồi trả lại response. 
---
**2. Method**
- Chỉ ra phương thức được phép thực hiện/ thao tác với source. 
- Được xác định bởi URI. 
- Phân biệt chữ HOA, chữ thường, phải luôn được đề cập bằng chữ HOA. 
- Một số Method được hỗ trợ trong HTTP /1.1 :
    - GET : Chỉ có chức năng truy xuất thông tin từ Server bằng URI đã cho.
    - HEAD : Tương tự như GET, nhưng chỉ có Status Line(dòng trạng thái) và dòng tiêu đề. 
    - POST : Gửi dữ liệu đến Server(thông tin user, file upload,...) bằng các HTML forms. 
    - PUT : Thay thế các dữ liệu target bằng dữ liệu đã upload lên. 
    - DELETE : Xóa các dữ liệu target do URI cung cấp. 
    - CONNECT : Thiết lập kết nối đến Server bởi URI đã đưa. 
    - OPTION : Miêu tả các tùy chọn thao tác, giao tiếp đến dữ liệu target. 
    - TRACE (Dấu vết) : Thực hiện kiểm tra thông báo loop back cùng với path của dữ liệu target. 

---
**3. How to send HTTP Request on Google**
- F12 hoặc Right Click -> Inspect -> Network -> Refresh web. 
- Ví dụ : 
![F12](https://i.imgur.com/615o9EO.jpg)

---
**4. How to send HTTP Request by Python**

```python 
import requests
 
r = requests.get('https://www.actvn.edu.vn/')    #Gọi phương thức GET -> chuyển tới URL đích -> Trả về request.models.Response 
print(type(r))
print(r.status_code)                             #Status Line. Nếu giá trị = 200 -> Success
print(r.headers)                                 #Show ra các mục trong Header
print(r.headers['content-type'])                 #Xem Content-Type mà Server đã gửi
#print(r.text)                                   #Show ra toàn bộ nội dung trang
```
![](https://i.imgur.com/pCRT0Us.jpg)

***JSON***
- Ký hiệu đối tượng Java. 
- Định dạng nhẹ, dễ lưu trữ và chuyển dữ liệu.
- Thường được dùng để gửi dữ liệu từ Server đến trang Web. 
```python 
import requests
 
r = requests.get('http://httpbin.org/ip')
print(r.headers['content-type'])
print(r.text)
data = r.json()                                  #Chuyển đổi chuỗi JSON thành Python data structor, chứa khóa và địa chỉ IP của máy
print(data)
print(data['origin'])                            #Truy cập địa chỉ IP
```

***USER AGENT***
- Tác nhân người dùng, cái này liệu có phải để fake một số thông tin đăng nhập nhằm đánh lừa Server rằng đây là hành động
của Phần mềm/ Trình duyệt này, mô tả thiết bị hoặc trình duyệt mà nó đang gửi request. 
- Mỗi một trình duyệt lại có User Agent khác nhau. Kiểu như để sử dụng các trang web đơn giản hơn, với những 
trình duyệt cũ hơn hoặc là hiển thị các nội dung khác nhau với mỗi một hệ điều hành.
```python 
import requests
 
r = requests.get('http://httpbin.org/user-agent')
print(r.headers['content-type'])
print(r.text)
data = r.json()
print(data)
print(data['user-agent'])
```
- Server sẽ cho biết IP mình đang sử dụng, trình duyệt đang sử dụng khi truy cập trang Web. 
- Return lỗi khi Server thấy rằng đây là "Human Browser". 
!(User Agent)[https://i.imgur.com/g2qMdEN.jpg]

- Setting User Agent : Cái này là fake trình duyệt mình đang sử dụng, em nghĩ là vậy. 
```python 
import requests
 
r = requests.get('http://httpbin.org/user-agent',
headers = {'User-agent': 'Internet Explorer/2.0'})
print(r.headers['content-type'])
print(r.text)
data = r.json()
print(data)
print(data['user-agent'])
```

---
**5. How to send HTTP Request by tools**
- Đề cập trong một file khác trong chương này

