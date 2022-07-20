## Middleware là gì?

**Middleware** là những đoạn mã trung gian nằm giữa các request và response. Nó nhận các request, thi hành các mệnh lệnh tương ứng trên request đó. Sau khi hoàn thành nó response (trả về) hoặc chuyển kết quả ủy thác cho một **Middleware** khác trong hàng đợi.

![[Pasted image 20220617121249.png]]


## Ứng dụng Middleware là gì?

Hiện nay các Web [Framework](https://topdev.vn/blog/framework-la-gi/) tân tiến đều sử dụng nó như là một phần của ứng dụng để kết nối các phần khác lại với nhau. Đối với các ứng dụng web, việc sử dụng Middleware một cách hiệu quả giúp chúng ta có thể tối giản được số lượng dòng code phải viết trong ứng dụng.

Một ví dụ phổ biến mà chúng ta thường phải dùng Middleware đó là các trang chỉ dành riêng cho admin và không cho phép người dùng bình thường có thể truy cập.


## Tại sao nên sử dụng nó?

Với tư tưởng chung là cầu nối giữa tương tác của người dùng và hệ thống trong lập trình Web. **Middleware** sẽ đóng vai trò trung gian giữa **request/response** và các xử lý logic bên trong web server.

Do đó, Middleware trong các Framework cho ứng dụng Web ([Laravel](https://topdev.vn/it-jobs/laravel-kt108), [Django](https://topdev.vn/it-jobs/django-kt18), [Rails](https://topdev.vn/it-jobs/ruby-on-rails-kt25), [ExpressJS](https://topdev.vn/blog/tat-tan-tat-ve-express-js/)…), sẽ là các hàm được dùng để tiền xử lý, lọc các request trước khi đưa vào xử lý logic hoặc điều chỉnh các response trước khi gửi về cho người dùng.

## Hiểu các khái niệm cơ bản của Laravel Middleware

Trong bài viết này, mình sẽ lấy ví dụ là dùng framework Laravel để hiểu khái niệm về middleware. Chúng ta sẽ xem xét cách tạo middleware tùy chỉnh trong một ứng dụng Laravel.

Sau khi tạo middleware tùy chỉnh của bạn, chúng ta sẽ khám phá các tùy chọn có sẵn để đăng ký nó với Laravel để nó có thể thực sự được gọi trong luồng xử lý yêu cầu.


## Middleware trong Laravel là gì?

**Middleware** như  là một cơ chế cho phép bạn tham gia vào luồng xử lý request của một ứng dụng Laravel. Trong một quá trình xử lý route điển hình của Laravel khi thực thi việc xử lý yêu cầu và middleware là một trong những class mà ứng dụng phải thông qua.

Vậy chính xác thì việc xử lý luồng yêu cầu Laravel là gì? Ví dụ: cần xác thực người dùng để quyết định xem họ có được phép truy cập đến route hiện tại hay không.

-   Yêu cầu đăng nhập
-   Chuyển hướng người dùng
-   Thay đổi/chuẩn hoá các tham số
-   Xử lý response được ứng dụng Laravel tạo ra
-   …

Thực tế, Laravel mặc định đã có sẵn một số middleware quan trọng. Việc xác thực người dùng cũng được chính middleware này thực thi.



