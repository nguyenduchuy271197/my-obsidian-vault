## Làm việc với React, bạn có thể gặp phải thuật ngữ Luồng dữ liệu đơn hướng. Nó có nghĩa là gì?

Luồng dữ liệu đơn hướng không phải là một khái niệm dành riêng cho React, nhưng với tư cách là một nhà phát triển JavaScript, đây có thể là lần đầu tiên bạn nghe thấy nó.

Nói chung, khái niệm này có nghĩa là dữ liệu có một và chỉ một cách để được chuyển đến các phần khác của ứng dụng.

Trong React, điều này có nghĩa là:

-   trạng thái được chuyển đến chế độ xem và cho các thành phần con
-   các hành động được kích hoạt ReadOnly
-   các hành động có thể cập nhật trạng thái
-   thay đổi trạng thái được chuyển đến chế độ xem và các thành phần con

ReadOnly là kết quả của trạng thái ứng dụng. Trạng thái chỉ có thể thay đổi khi các hành động xảy ra. Khi các hành động xảy ra, trạng thái được cập nhật.

Nhờ liên kết một chiều, dữ liệu không thể lưu chuyển theo cách ngược lại (ví dụ như sẽ xảy ra với liên kết hai chiều) và điều này có một số ưu điểm chính:

-   nó ít bị lỗi hơn vì bạn có nhiều quyền kiểm soát hơn đối với dữ liệu của mình
-   nó dễ dàng hơn để gỡ lỗi, như bạn biết_gì_đến từ_Ở đâu_
-   nó hiệu quả hơn, vì thư viện đã biết ranh giới của từng phần của hệ thống là gì

Một trạng thái luôn được sở hữu bởi một Thành phần. Bất kỳ dữ liệu nào bị ảnh hưởng bởi trạng thái này chỉ có thể ảnh hưởng đến các Thành phần bên dưới nó: con của nó.

Việc thay đổi trạng thái trên một Thành phần sẽ không bao giờ ảnh hưởng đến cha mẹ, anh chị em của nó, hoặc bất kỳ Thành phần nào khác trong ứng dụng: chỉ là con của nó.v

