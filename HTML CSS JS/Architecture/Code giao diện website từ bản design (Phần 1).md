  
Quá trình tạo markup giao diện từ bản thiết kế nên tiến hành theo các bước sau để triển khai viết khoa học, dễ debug

-   Phân tích layout tổng quát, chia thành từng block nhỏ
-   Phân tích từng block một gồm các element nào
-   Triển khai code từng block


### Vài quy tắc

**1. Từ trên xuống dưới**  
**2. Từ ngoài vào trong**  
Dùng container hay container-fluid  
`.container-fluid` khi được áp dụng cho một phần tử sẽ làm cho phần tử này có chiều rộng 100%  
`.container`khi được áp dụng cho một phần tử sẽ làm cho phần tử này có chiều rộng dựa trên kích thước chiều rộng màn hình của các thiết bị  
**3. Từ trái sang phải**  
Xác định row, columns

### Bước 1. Phân tích layout, xác định các block

Ở bước này, nhìn vào bản thiết kế được Designer tạo thành file Photoshop .psd hoặc trên figma dưới dạng các layout gồm nhiều thành phần ghép vào nhau.  
  
Dựa vào đó ta xác định bố cục của một page gồm những thành phần nào để xác định cách triển khai mã nguồn HTML khi code ra page đó

Một cách phân tích bố cục layout điển hình như sau:

```pug
body
   header
      section.top-bar
      section.nav-bar
   main
      section1
      section2
      ...
   footer
```

### Bước 2. Phân tích từng block

Sau khi đã phân tích được layout chung của trang web và xác định các block lớn tạo nên giao diện cho page đó. Chúng ta đi sâu phân tích các block thành các element nhỏ hơn để code từng element nhỏ đó tạo ra giao diện.

Ví dụ như phần header của trang Viblo có giao diện như sau:

![[Pasted image 20220617124529.png]]

Từ bản thiết kế này ta xác định header gồm một thanh navbar, thanh navbar gồm Logo ở bên trái rồi đến phần chọn trang con, phần tìm kiếm và nút bấm menu người dùng

Ví dụ về phân tích phân tích layout, phân tích các elements trong từng block của trang Viblo như sau:

![[Pasted image 20220617124620.png]]


### Bước 3. Triển khai viết mã nguồn

Viết mã nguồn để tạo ra giao diện sẽ bao gồm 3 phần chính đó là mã nguồn HTML, CSS (SCSS, SASS), Javascript và Jquery

1.  Mã nguồn HTML: sử dụng các thẻ để xác định bộ khung cho page đó
2.  Mã nguồn CSS: Sử dụng hệ thống selector (tag, class, id,...) để tạo phong cách và định kiểu cho HTML. Nó có thể điều khiển định dạng của nhiều trang web cùng lúc để tiết kiệm công sức cho người viết web. Nó phân biệt cách hiển thị của trang web với nội dung chính của trang bằng cách điều khiển bố cục, màu sắc, và font chữ.
3.  Mã nguồn Js và Jquey: sử dụng dùng để xử lý động cho trang web, điều khiển các hoạt động click, hover, scroll,..các thành phần trong web

#### Viết mã nguồn HTML

Để viết mã nguồn tạo ra bộ khung cho trang web ở đây mình sẽ dùng pug và HTML5 như [bài viết trước đó](https://viblo.asia/p/bat-dau-code-frontend-oOVlYbBo58W) mình đã có nói  
Hệ thống các thẻ (tag) mà HTML5 cung cấp các bạn có thể xem ở [w3school](https://www.w3schools.com/html/default.asp). Mình phân nó thành một số nhóm thẻ sau:  

-   Nhóm thẻ cấu trúc: tạo ra bố cục cho page
-   Nhóm thẻ heading: tạo ra phần tiêu đề
-   Nhóm thẻ xác định văn bản: tạo nội dung cho page
-   Nhóm thẻ danh sách: tạo nội dung kiểu danh sách
-   Nhóm thẻ liên kết, media: tạo ảnh, video, liên kết cho page
-   Nhóm thẻ tạo bảng: tạo bảng dữ liệu hoặc tạo layout
-   Nhóm thẻ liên quan đến form: tạo form nhập liệu

=> Từ các nhóm thẻ này, chúng ta sẽ tạo ra được phần khung. Sau đó chúng ta sẽ viết mã nguồn CSS để biến bản design thành giao diện web  
  
_**Một số lưu ý khi code HTML tạo bộ khung cho page:**_

-   Sử dụng thẻ section và div để tạo các block, các element
-   Một số block chung nên viết riêng thành một file như sidebar, navbar, header, footer,..
-   Xác định name, khai báo class, id đặt tên theo chuẩn BEM khi website gồm nhiều page phức tạp

#### Đặt tên theo chuẩn BEM

BEM là viết tắt của Block-Element-Modifier, là một tiêu chuẩn quy ước đặt tên cho các tên lớp CSS. BEM giúp cho việc code Frontend dễ đọc và dễ hiểu hơn, dễ làm việc và dễ mở rộng cũng như bảo trì khi làm việc với CSS.  
Quy ước đặt tên

```css
.block {} /* Block */
.block__element {}  /* Element */
.block--modifier {}  /* Modifier */
```

