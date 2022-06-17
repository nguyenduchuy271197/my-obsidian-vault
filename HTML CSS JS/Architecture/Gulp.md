### Gulp là gì?

**Gulp** là một công cụ giúp bạn tự động hóa nhiều task (nhiệm vụ) trong quá trình phát triển web. Nó thường được sử dụng để làm các tác vụ front end như:

-   Tạo ra một web server.
-   Reload trình duyệt một cách tự động bất cứ khi nào một file được lưu.
-   Sử dụng các preprocessor giống như Sass hoặc LESS.
-   Tối ưu hóa các tài nguyên như CSS, JavaScript và hình ảnh. Đây không phải là một danh sách toàn diện về những thứ mà Gulp có thể làm. Nếu muốn, bạn có thể tạo một generator web site tĩnh. Gulp cực kỳ mạnh mẽ, nhưng bạn cần học cách sử dụng Gulp nếu muốn tạo ra một quá trình (process) của riêng mình. Bài viết này sẽ giúp bạn có những kiến thức cơ bản về Gulp sau đó bạn có thể tự mình khám phá mọi thứ. Trước khi đi sâu vào Gulp, hãy nói về lý do tại sao bạn sử dụng Gulp mà không phải các công cụ khác.

### Cái chúng ta sẽ làm

Khi kết thúc bài viết này, bạn sẽ có một workflow thực hiện các task sau:

-   Tạo ra một web server.
-   Biên dịch Sass thành CSS.
-   Refesh trình duyệt tự động bất cứ khi nào bạn lưu một file.
-   Tối ưu hóa các tài nguyên (CSS, JS, fonts, và hình ảnh) cho phiên bản production.

Bạn cũng sẽ học cách nối một chuỗi các task khác nhau vào một lệnh đơn giản. Hãy bắt đầu bằng cách cài đặt Gulp trên máy tính của bạn.

### Cài đặt Gulp

Bạn cần cài đặt Node.js trước khi có thể cài đặt Gulp.

Sau khi đã cài đặt Node, bạn có thể cài đặt Gulp bằng cách sử dụng lệnh sau:

```bash
$ sudo npm install gulp -g
```

_**Những khái niệm cơ bản trên tôi thảm khảo trên blog của techmaster [https://techmaster.vn/posts/34204/gulp-cho-nguoi-moi-bat-dau](https://techmaster.vn/posts/34204/gulp-cho-nguoi-moi-bat-dau) (Nguồn Techmaster )**_

```bash
npm init  // This will run through creating the package.json file
npm install -g gulp  // If you haven't installed gulp globally before
npm install --save-dev gulp
npm install --save-dev gulp-sass
```

Tạo **gulpfile.js** để build scss to css

```js
var gulp = require('gulp');
var sass = require('gulp-sass');

gulp.task('styles', function() {
    gulp.src('sass/**/*.scss')
        .pipe(sass().on('error', sass.logError))
        .pipe(gulp.dest('./css/'))
});

//Watch task
gulp.task('default',function() {
    gulp.watch('sass/**/*.scss',['styles']);
});
```

_**Đây là cấu trúc dự án của mình**_

![[Pasted image 20220617131715.png]]

Bây giờ bạn vào thư mục **sass** , bạn tạo ra file styles.scss bạn viết mở 1 đoạn style demo nhỏ Sau đó bạn mở cmd lên bạn chạy lệnh sau

```bash
gulp 
```

Sau đó bạn vào file CSS bạn thấy nó sẽ tự đông build ra file css cho các bạn

Vậy là xong rồi , đây là 1 bài hướng dẫn nhỏ về convert từ **SCSS to CSS** , nhưng gulp ngoài việc build scss qua css cho bác bạn thì nó có thể làm những việc khác như build các file _**TypeScript to JS**_ , và nhiều vấn đề khác , để hiểu rõ hơn về gulp thì các bạn lên trang chủ của Gulp để tìm hiểu kĩ hơn về nó .
