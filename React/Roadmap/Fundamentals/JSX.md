Cú pháp thẻ này không phải là một chuỗi hay là HTML. Nó được gọi là JSX, và nó là một cú pháp mở rộng cho JavaScript. Facebook sử dụng JSX để biểu thị UI components

```none
const element = <h1>Hello, world!</h1>;
```


Việc sử dụng JSX trong ReactJS là không bắt buộc. Bạn có thể sử dụng chỉ JS thuần thôi. Nhưng có rất nhiều lý do cho việc nên sử dụng JSX trong ReactJS đấy.

-   Thứ nhất, JSX với cú pháp gần giống XML, cấu trúc cây khi biểu thị các attributes, điều đó giúp ta dễ dàng định nghĩa, quản lý được các component phức tạp, thay vì việc phải định nghĩa và gọi ra nhiều hàm hoặc object trong javascript. Khi nhìn vào cấu trúc đó cũng dễ dàng đọc hiểu được ý nghĩa của các component. Code JSX ngắn hơn, dễ hiểu hơn code JS.
-   Thứ 2, JSX không làm thay đổi ngữ nghĩa của Javascript
-   Thứ 3, với cách viết gần với các thẻ HTML, nó giúp những developers thông thường (ví dụ như các designer) có thể hiểu được một cách dễ dàng, từ đó có thể viết hoặc sửa code mà không gặp nhiều khó khăn. Ví du với đoạn code JSX như sau

Roadmap: [[React/Roadmap/Advanced/Roadmap Image]]

Next: [[Create-react-app]]