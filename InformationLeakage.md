# **4.1.1. Conduct Search Engine Discovery Reconnaissance for Information Leakage** 
---
## *Cách khai thác công cụ tìm kiếm liên quan đến Leak thông tin*

**1.Khái quát**
- Khi công cụ tìm kiếm làm việc, đòi hỏi Computer Programs phải thường xuyên thu thập dữ liệu từ vô số trang webs. (kiểu như crawling )
- Tìm kiếm trang web bằng 2 cách : 
    - Liên kết với trang web khác (đường link).
     Ví dụ : Google tìm thấy các trang thông qua các link có thể xuất hiện từ khóa hoặc các link liên kết mà nó có nói tới từ khóa đó. 
    - Hoặc tìm kiếm trên sitemaps. 
---

***Sitemap***
- Câu hỏi : Khi mà em muốn xem XML sitemap nhưng trang đó không cho phép, hoặc chỉ hiện 1 cách nhanh chóng rồi chuyển hướng, có thông báo XML không xem được thì mình phải làm như thế nào ạ ? 
- Chứa thông tin trang và các file trên web
- Có 2 loại phổ biến : XMl(dành cho Search Engine) hoặc HTML
- XML Sitemap : 
  - a. Show sitemap bằng cách thêm 1 số option sau URL : 
    - /sitemap.xml 
    - /sitemap_index.xml
    - /sitemap-index.xml
    - /sitemap.php
    - /sitemap.txt
    - /sitemap.xml.gz
    - /sitemap/
    - /sitemap/sitemap.xml
    - /sitemapindex.xml
    - /sitemap/index.xml
    - /sitemap1.xml
![Ví dụ sitemapXML](https://i.imgur.com/9tWorCO.jpg)
    - Ngoài ra còn 1 số định dạng như /rss /, /rss.xml, /atom.xml 
    
  - b. Dùng Google Search Console (là admin hoặc được cấp quyền truy cập) 
    - Đăng nhập vào GSC
![Ví dụ SMapGSC](https://seocrawl.com/wp-content/uploads/2021/08/Google-Search-Console-Sitemaps-blurred.png)
    - Tìm tới Sitemaps
![Ví dụ SMapGSC](https://seocrawl.com/wp-content/uploads/2021/08/Submitted-sitemaps-Chess.com-Seach-Console-blurred.png)

  - c. Dùng toán tử tìm kiếm của GG (Google Search Operators)
       - Sử dụng lệnh "filetype:" + "site:"
![Ví dụ dùng GSO](https://i.imgur.com/FMyfwuM.jpg)
       - File XML được tìm thấy 
![](https://i.imgur.com/Mebp8QS.jpg)
---
***Tiếp tục phần 1***
- Nếu 1 trang web có sử dụng file "robots.txt", nó sẽ liệt kê các trang web mà không muốn Search Engine tìm thấy.
- Dùng Search Engine để tìm, dò, khám phá trên các trang web/ ứng dụng web. 
- Để khám phá hoặc thăm dò trang web thì Search Engine có thể dùng cách trực tiếp hoặc gián tiếp.
- Trực tiếp : Những thứ liên quan đến indexes, thông tin liên quan từ caches.
- Gián tiếp : Tìm hiểu cách design, thông tin config,... bằng cách tìm trên các group news, webites, forums(diễn đàn).
- Thu thập dữ liệu xong -> Dựa vào tags hoặc thuộc tính để lập các index. 
---
**2.Mục tiêu phần này**
- Hiểu về cách mà ứng dụng, hệ thống, trang web nó design như thế nào, những cái gì mình có thể khai thác được từ nó.
- Sử dụng Search Engine trực tiếp trên trang web đó hoặc gián tiếp trên trang web bên thứ 3. 
---
**How to Test**
- Sử dụng Search Engien để tìm kiếm thông tin nhạy cảm, dễ bị Leak, có thể : 
  - Sơ đồ mạng, config mạng. 
  - Các post, email được lưu bởi admin hoặc key staff. 
  - Thủ tục đăng nhập (Username, password, khóa private,...)
  - Cloud service,...
  - Error message content
  - Test, các phiên bản của web,... 
---
 **Search Engine**
- Mỗi công cụ khác thì có kết quả khác.
- Một số công cụ tìm kiếm: 
  - Baidu (bên China)
  - Bing (Microsoft), phổ biến thứ 2. 
  - Binsearch.infor (Tìm kiếm nhị phân)
  - DuckDuckGo 
  - Google (Sử dụng hệ thống ranking để tìm ra kết quả trả về, có hỗ trợ toán tử tìm kiếm)
  - Startpage (Tìm kiếm dựa trên Google, không thu thập thông tin cá nhân, các log)
  - Shodan (Cái này tìm kiếm các dịch vụ được kết nối Internet)
  - Cả DuckDuckGo, StartPage đều không lưu thông tin user -> Giảm thiểu việc bị leak thông tin tester.
---
**Toán tử tìm kiếm**
- Thường sẽ khai thác các thông tin : 
    - site : Khi có 1 URL, cái này sẽ show ra phạm vicuar trang web 
    - inurl : chỉ trả lại kết quả chứa các key mình tìm
    - intitle : chỉ trả lại kết quả có chứa key trong page title
    - intext / inbody : tìm kiếm từ khóa trong phần body của trang web
    - filetype : match với các loại file đặc biệt, ví dụ như .png ,.pdf, .xml, php,...
Ngoài ra còn có : 
    - *,OR,AND, |, (), -, .., $, @, in , etc... 
    - define  : Tìm định nghĩa 1 từ. VD : define:enormity
![](https://i.imgur.com/b2OPyHS.jpg)
    - weather : Liên quan đến thời tiết 
    - map : VD map:houston
    - allintext : Tìm tất cả các thuật ngữ 
    - inanchor : Tìm các trang web được liên kết với anchor đó

**Ví dụ về SITE**
- Trong phần này, em sử dụng công cụ tìm kiếm chủ yếu là Google.
- site: Không có truy vấn, không xếp hạng kết quả. Nó sẽ hiển thị URL ngắn nhất liên quan đến keywords,tìm kiếm từ tên miền...Hạn chế kết quả tìm được trong 1 khoảng nhất định.
- Ví dụ 1 : Nếu không dùng query "site" thì kết quả cho ra ![Không dùng site](https://i.imgur.com/8uPkIDI.jpg)
- Còn nếu dùng query "site :" thì kết quả tìm kiếm bị giới hạn lại
![Tìm kiếm theo từ khóa](https://i.imgur.com/pnEzfwe.jpg)
- Ví dụ 2 : Show ra kết quả từ miền testphp.com. Trong khi không dùng site thì Google sẽ search ra khoảng 1.900.000 kết quả 
![Tìm kiếm theo Domain](https://i.imgur.com/wXeaYXE.jpg)
- Ví dụ 3 : Show ra kết quả, trang bắt đầu từ https://.../ và có liên quan đến apple
![Tìm kiếm web có chứa nội dung trên URL](https://i.imgur.com/YjnmF7l.jpg)

**Ví dụ khác**
- Ví dụ với filetype : 
![Filetype](https://i.imgur.com/nKRoY2G.jpg)
- Kết hợp các query 
![Tìm file butterfly với định dạng PNG](https://i.imgur.com/2K4exqP.jpg)

---
**Xem nội dung Cache - Bộ nhớ đệm**
- Nội dung tìm kiếm đã được index. Em nghĩ cái này có phải sẽ dùng nhiều khi mình làm Catching đúng không ạ ?
- Dùng "cache:" để xem các thay đổi, tính từ lúc nội dung đó được gán index, hoặc bị xóa. Nguồn có thể xem cache được bây giờ nhiều nhất là Google, không phải lúc nào cũng tìm kiếm được cache.
- Ví dụ để tìm kiếm, xem juice-shop.herokuapp.com khi nó được lưu trong bộ nhớ cache. 
![](https://i.imgur.com/y3tLh07.jpg)
---
**Google Hacking or Dorking**
- Kỹ thuật xâu chuỗi các toán tử tìm kiếm được hỗ trợ, để khám phá, khai thác được thông tin các file, loại file, thông tin dễ bị lộ,...
- Hay theo ý hiểu của em thì nó là kỹ thuật sử dụng công cụ tìm kiếm là Google. Kết hợp với các toản tử, các ứng dụng của Google để tìm kiếm thông tin mình cần (về user,password,version, filetype, ...) hoặc lỗ hổng bảo mật nếu có.
- Dork giúp khám phá thêm các thông tin, có thể là : 
   - Footholds
   - File có chứa usernames
   - File có chứa passwords
   - Thư mục nhạy cảm?
   - Phát hiện Web server 
   - File dễ bị tấn công 
   - Server dễ bị tấn công
   - Thông báo lỗi 
   - File chứa thông tin bẫy 
   - Thông tin mua sắm trực tuyến dễ bị lộ

- Ví dụ trên exploit-db (Công cụ khai thác Database)
    Tại đây em thấy khá nhiều Dork để thử 
![](https://i.imgur.com/oamewQD.jpg)
    Show ra 1 vài email và password : site:pastebin.com "*@gmail.com password"
![](https://i.imgur.com/jebnN81.jpg) 
![](https://i.imgur.com/YJGHmFN.jpg)
    Hoặc là tìm user,pass,name,key trong file SQL : filetype:sql intext:password | pass | passwd intext:username intext:INSERT INTO `users` VALUES
![](https://i.imgur.com/5ERYdMe.jpg)

---
**Cách khắc phục**
- Xem xét kỹ lưỡng, thường xuyên, xem thông tin nào dễ bị lộ, thông tin nào dễ bị nhắm đến như design hoặc config,...

**Thực hành** 
- site:juice-shop.herokuapp.com
- Tìm kiếm từ khóa liên quan đến admin :
site:juice-shop.herokuapp.com inurl:admin 
- Phần body chắc có từ khóa user,password,admin gì đó :
site:juice-shop.herokuapp.com intext:admin | user | password | pass
- Thử site:juice-shop.herokuapp.com intitle:login
-  site:juice-shop.herokuapp.com filetype:pdf 
