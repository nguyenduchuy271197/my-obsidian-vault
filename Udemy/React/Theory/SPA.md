Chào các bạn,

Cách đây 5 năm (chừng 2015), mình có nghe tới khái niệm **Single Page Application** và mon men tìm hiểu. Sau khi thực hiện vài project thử nghiệm theo kiểu Single Page Application, mình đã hiểu nó là gì, và theo cảm nhận của mình tại thời điểm đó thì “**Single Page Application sẽ là xu hướng lập trình web trong tương lai**“. Vậy **Single Page Application là gì**, nó khác gì với kiểu lập trình web truyền thống, và tính đến nay (2020) thì Single Page Application có phải là xu hướng hay không thì các bạn hãy theo dõi trong bài viết này nhé.


Lưu ý: Đây là một bài viết “dài dòng”, vì mình không chỉ muốn bạn biết Single Page Application là gì, mà mình còn muốn bạn hiểu nó, hiểu lý do tại sao nó ra đời cũng như những lưu ý khi lập trình web theo kiểu Single Page Application.


## I. SINGLE PAGE APPLICATION LÀ GÌ? TẠI SAO SINGLE PAGE APPLICATION RA ĐỜI.

### 1.1 Single Page Application là gì?

**Single Page Application** (gọi tắt là SPA) là tên gọi chung cho một kiểu lập trình web.

Trang web khi lập trình theo kiểu SPA thường sẽ đem lại **trải nghiệm mượt mà**, khiến người dùng có cảm giác như đang sử dụng một **ứng dụng mobile** chứ không phải một trang web (thực tế code một website theo kiểu SPA khá giống với việc code một ứng dụng mobile).

Nếu bạn muốn trải nghiệm thử một website code theo kiểu SPA thì có lẽ bạn đã… trải nghiệm trước đó rồi, vì các website lớn như facebook.com, google.com, youtube.com, twitter.com đều được code theo kiểu SPA. Dễ thấy các website kể trên đều có trải nghiệm mượt mà, mà nổi bật nhất chính là **không bị khựng lại** ở thao tác chuyển từ trang này sang trang kia.

Vậy tại sao công nghệ này lại có tên là **Single Page Application** – cái tên này nghe hơi khó hiểu với những bạn mới bắt đầu. Thực ra là bạn sẽ hiểu ngay khi code thử một project theo kiểu SPA. Nhưng mình có thể giải thích nhanh cho bạn thế này.

```
Sở dĩ có tên là **Single Page Application** là do các website code theo kiểu này **chỉ cần 1 trang duy nhất để xử lý tất cả** các tính năng.  
  
Ví dụ:  
– domain.com/admin/#/login  
– domain.com/admin/#/change-password  
– domain.com/admin/#/account  
– domain.com/admin/#/dashboard  
  
Trên là 4 tính năng khác nhau, nhưng chúng đều được xử lý tại 1 trang duy nhất là trang domain.com/admin. Đương nhiên là mỗi tính năng sẽ hiển thị một giao diện khác nhau, nhưng điều mình muốn nhấn mạnh là nó **đều được xử lý tại trang domain.com/admin**. Còn lý do tại sao nó lại chỉ xử lý tại một trang thì mời bạn theo dõi tiếp trong nội dung bài viết.  
  
**Lưu ý**: Các ký tự nằm phía sau dấu # trên url đều không có tác dụng trong việc phân biệt trang. Nghĩa là domain.com/admin/#/bla-bla-bla thì cũng vẫn là trang doamin.com/admin
```

### 1.2 Tại sao SPA ra đời

Để hiểu hơn về SPA, thì chúng ta nên biết tại sao nó lại xuất hiện trên trái đất này.

Trước khi SPA ra đời, việc lập trình web thường tuân theo mô hình MVC (kiểu lập trình truyền thống). Cách hoạt động thường là client gửi request tới server, server xử lý request và response cho client. Những gì mà client nhận được thường là nội dung của một trang web hoàn chỉnh với HTML, CSS, JS. Nói tóm lại, server gần như làm tất cả mọi thứ, thằng client chỉ việc nhận kết quả (kiểu không “nàm” mà vẫn có ăn).

Thao tác server xử lý request và response đầy đủ HTML, CSS, JS còn được gọi là **Server Side Rendering** (thiên hạ vẫn gọi tắt là SSR).

Tuy nhiên, khi các trang web ngày càng trở nên **phức tạp** và tập trung hơn vào **trải nghiệm người dùng** thì SSR không đáp ứng được do SSR là tập trung xử lý ở server, trong khi trải nghiệm người dùng thì tập trung xử lý ở client.

Trong giai đoạn này, người ta nghĩ cái gì thuộc về client thì hãy để client xử lý và bắt đầu tách bạch vai trò của client với server. Lúc này, [jQuery](https://jquery.com/) và các jQuery plugin được tận dụng triệt để, [ajax](https://www.w3schools.com/js/js_ajax_intro.asp) được mọi người biết đến nhiều hơn. Nhưng sau cùng, các thư viện xử lý ở client giai đoạn đó (mà chủ yếu là jQuery) vẫn thô sơ, khó đáp ứng được các xử lý phức tạp tại client.

```
**Nói thêm**  
Mình từng mất ăn mất ngủ với jQuery vì gặp những lỗi khó hiểu như [duplicate click event](https://stackoverflow.com/questions/1558377/jquery-prevent-duplicate-function-assigned), và việc cập nhật lại DOM thông qua các hàm append(), html(), prepend() khiến mình phát ngán vì lặp đi lặp lại quá nhiều lần.  
  
Nhưng cũng phải thông cảm rằng jQuery sinh ra là để làm việc với DOM, nó giúp mình chèn một đoạn HTML vào đâu đó, sửa text hay thay đổi CSS. Mình không thể kỳ vọng thêm gì ở nó được.
```

Sau giai đoạn này, ý tưởng về một kiểu lập trình mà có thể xử lý ở client nhiều hơn ra đời, đó chính là SPA.

Có thể coi SPA như một bước ngoặt lớn của lập trình web, bởi SPA đẩy mạnh hơn các thao tác xử lý ở client, nâng cao vai trò của frontend và giảm bớt “gánh nặng” cho backend (cũng có thể nói SPA làm tách bạch frontend và backend). Các frontend developer lúc này cũng cần quan tâm hơn tới các [design pattern](https://phambinh.net/bai-viet/mot-so-design-patterns-co-the-su-dung-trong-javascript-phan-1/), cấu trúc dự án, cấu trúc dữ liệu thay vì chỉ quan tâm tới UI, UX.


## II. CÁCH HOẠT ĐỘNG CỦA WEB SPA KHÁC GÌ WEB TRUYỀN THỐNG

Xin lỗi vì hơi dài dòng, nhưng để hiểu về SPA, thật sự bạn nên hiểu những “thứ dài dòng” phía trước.

Có 2 đặc điểm lớn ảnh tạo nên sự khác biệt về cách hoạt động của web SPA so với web truyền thống là:

-   Web SPA có backend và frontend rõ ràng.
-   Web SPA sẽ đẩy mạnh xử lý ở frontend.

Chúng ta sẽ đi làm rõ từng ý một.

### 2.1 Web SPA có backend và frontend rõ ràng.

Lập trình theo kiểu truyền thống, backend và frontend chưa có sự phân định rõ ràng. Ví dụ như [Laravel Framework](https://phambinh.net/danh-muc/laravel-framework/), bạn vẫn có thể code PHP trong thành phần View. Nhưng với SPA thì khác, backend và frontend tách bạch tới nỗi chúng có thể nằm ở 2 dự án khác nhau:

-   Website code theo kiểu truyền thống chỉ cần 1 dự án, nhưng website code theo kiểu SPA có thể cần 2 dự án: 1 dự án cho backend và 1 dự án cho frontend.
-   Theo ý tưởng của SPA, backend và frontend được coi là 2 dự án khác nhau, mặc dù chúng sinh ra là để dành cho nhau.
-   Việc trao đổi dữ liệu giữa backend và frontend thường qua các Restful API, định dạng dữ liệu thường là JSON.

Cách hoạt động giữa frontend và backend của website kiểu SPA có thể được mô tả như sau:

-   Khi người dùng truy cập vào các trang web, frontend sẽ là thành phần tiếp nhận request chứ không phải backend – hay có thể nói là web SPA thực hiện routing ở frontend thay vì backend như kiểu lập trình truyền thống.
-   Sau khi tiếp nhận request, frontend sẽ biết được người dùng muốn sử dụng tính năng nào, tính năng này cần những dữ liệu gì, sau đó mới gửi request tới backend, yêu cầu backend trả về dữ liệu mong muốn.
-   Frontend nhận dữ liệu từ backend (thường là dạng json), và dựa vào dữ liệu này để render ra nội dung trang web hoàn chỉnh.

Thao tác render ở frontend (client) còn được gọi là **Client Side Rendering**.

Đọc tới đây thì bạn đã hiểu tại sao SPA lại xử lý tất cả tại một trang chưa?  
  
Là vì SPA luôn chỉ có 1 trang để tiếp nhận request và thực hiện routing, giống như nhiều PHP framework thường tiếp nhận request thông qua file index.php vậy.

### 2.2 Web SPA đẩy mạnh xử lý ở frontend.

Với web SPA, frontend đảm nhiệm hoàn toàn việc render giao diện và xử lý các thay đổi trên giao diện, backend chỉ là thằng đứng chờ xem frontend yêu cầu dữ liệu gì thì trả về cái đó.

Web SPA yêu cầu xử phức tạp ở frontend, vì thế mà frontend thường sẽ áp dụng một framework hay thư viện nào đó về SPA để xử lý như angular, vuejs hoặc reactjs. Những framework hay thư viện này sẽ giúp developer dễ dàng phát triển một SPA hơn, và tất nhiên chúng đều được code bằng [JavaScript](https://phambinh.net/bai-viet/hoc-javascript-trong-15-phut/).


Bạn có thể đã biết về kiến trúc MVC ở backend, nhưng bạn có biết ở frontend cũng có thể áp dụng MVC không? Thật vậy, để xử lý các yêu cầu phức tạp ở frontend, các framework SPA cũng hoạt động theo một kiến trúc cụ thể, có thể là MVC (Angular) hoặc MV-VM (VueJS, ReactJS).


Bạn không cần tìm hiểu kỹ về kiến trúc MVC hay MV-VM ở frontend vội, mà chỉ cần biết rằng code SPA bằng các framework chuyên về SPA sẽ đơn giản hơn nhiều so với việc code bằng jQuery hoặc một kiến trúc nào đó do bạn tự nghĩ ra (nếu bạn quá giỏi thì mình không nói nhé).


## III. BẮT ĐẦU LẬP TRÌNH WEB THEO KIỂU SPA NHƯ THẾ NÀO

Bắt đầu thì không khó, nhưng đòi hỏi bạn phải kiên trì. Bởi nếu bạn quá quen thuộc với kiểu lập trình web truyền thống, thì sẽ mất một thời gian đủ lâu để thay đổi lối tư duy sang code kiểu SPA (backend và frontend tách biệt). Đôi khi bạn sẽ phân vân không biết cái này nên code ở backend hay frontend.

```
Nhớ rằng hãy kiên trì khi bắt đầu code SPA
```

Về việc nên chọn framework SPA nào để bắt đầu, thì mình gợi ý bạn nên chọn VueJS. Vì nó có cú pháp trong sáng, dễ hiểu hơn Angular và ReactJS.

-   Trang chủ: [https://vuejs.org](https://vuejs.org/)
-   Trang tài liệu Tiếng Việt: [https://vi.vuejs.org](https://vi.vuejs.org/)
-   Diễn đàn: [https://forum.vuejs.org](https://forum.vuejs.org/)
-   Facebook group tại Việt Nam: [https://fb.com/groups/vuejsvietnam](https://www.facebook.com/groups/vuejsvietnam/)
-   Các khóa học miễn phí: [https://vueschool.io/courses?filter=free-courses](https://vueschool.io/courses?filter=free-courses)

Bạn cũng có thể tìm thấy rất nhiều video về VueJS trên youtube nữa.


```
Lưu ý: Code web SPA có lối tư duy rất khác code theo kiểu truyền thống, code SPA gần với code ứng dụng mobile hơn.
```

## IV. MỘT SỐ LƯU Ý KHI TRIỂN KHAI WEB THEO SPA

Nếu bạn định triển khai một dự án web SPA **nghiêm túc** thì đây là một số lưu ý:

-   **Web SPA không giành cho các developer thiếu kinh nghiệm với frontend**: Nếu bạn chưa thông thạo HTML, CSS, JS, ajax, [es6](https://phambinh.net/bai-viet/tom-gon-javascript-es6-trong-10-phut/) thì hãy trau dồi kiến thức trước khi triển khai web SPA.
-   **Web SPA sẽ không tốt cho SEO**: nội dung được render dưới client khiến bot google không đọc được, nên không tốt cho SEO. (Sẽ có cách khắc phục nhưng mình sẽ trình bày trong bài viết khác).
-   **Sẽ có nhiều bài toán mới phát sinh như**: xác thực tài khoản, animation loading, lazyload.
-   **Thời gian hoàn thiện**: Việc tách ra 2 dự án backend và frontend riêng biệt sẽ khiến nhiều bạn nghĩ rằng code SPA sẽ lâu hơn code kiểu truyền thống. Nhưng không phải vậy, tùy từng dự án mà thời gian hoàn thiện web SPA sẽ nhanh hoặc chậm hơn so với kiểu code truyền thống.
-   **SPA phù hợp với các dự án**: Các dự án cần maintain, có định hướng phát triển lâu dài. Các phần mềm dịch vụ ([SAAS](https://vi.wikipedia.org/wiki/Ph%E1%BA%A7n_m%E1%BB%81m_d%E1%BA%A1ng_d%E1%BB%8Bch_v%E1%BB%A5)). Các dự án tập trung nhiều vào UX.

## V. SPA CÓ PHẢI LÀ XU HƯỚNG LẬP TRÌNH WEB TRONG TƯƠNG LAI?

Thật sự rất khó để trả lời cho câu hỏi này. Tuy không dám khẳng định SPA là xu hướng, nhưng với cách hoạt động của SPA thì trong khoảng 5 năm gần đây (2015 – 2020) nó đã xuất hiện trên nhiều phần mềm dịch vụ lớn. Công ty mình đang làm cũng vừa triển khai vài dự án dưới dạng SPA, các ông lớn công nghệ như Google, Facebook cũng đều áp dụng SPA trên sản phẩm của mình. Nếu như SPA không phải là xu hướng, thì ít nhất nó cũng đã tìm được “thị phần” cho riêng mình, cũng đủ tự tin để “cạnh tranh” với kiểu lập trình truyền thống.


Reference: https://phambinh.net/bai-viet/single-page-application-la-gi-co-phai-la-xu-huong-lap-trinh-web-trong-tuong-lai/


