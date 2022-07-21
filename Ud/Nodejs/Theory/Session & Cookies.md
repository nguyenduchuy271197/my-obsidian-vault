# Session, Cookie và Cache, bạn đã thực sự hiểu chúng??


Session, Cookie, Cache có lẽ đây chính là 3 khái niệm được nhắc đến thường xuyên đối với các lập trình viên. Khi mới bắt đầu tập tành làm web, tôi rất hay nhầm lẫn giữa các khái niệm này, tôi không biết lúc nào thì mình nên dùng session, lúc nào mình nên dùng cookie, cache được dùng để làm gì.... Có lần chỉ một chức năng nhỏ để lưu lịch sử thao tác của người dùng trên trình duyệt , tôi đã cho nó vào hết Session và ném cả đám đó cho mentor của mình review, và dĩ nhiên, tôi bị mắng rất thậm tệ.... "Em có biết session là gì không?" "Em có biết cookie là gì không?", "Có biết cái gì cũng nhét hết vào session thế này sẽ làm ngốn rất nhiều bộ nhớ của server không?"..... Vâng tôi đã chẳng biết gì về những khái niệm đó cả, tôi dùng nó một cách vô tội vạ và chỉ quan tâm sao cho chức năng mình làm có thể chạy được mà chẳng quan tâm những cái tôi dùng có đúng mục đích hay không? có thực sự tận dụng nó một cách triệt để, và có thật sự tối ưu hay không? Thật ra thì ... tuổi trẻ mà, CỨ SAI ĐI VÌ CUỘC ĐỜI CHO PHÉP. Càng sai càng nhớ lâu, càng đau, càng nhớ đời. Nào chúng ta cùng tìm hiểu các khái niệm này nhé


### Session

Một session hay còn gọi là một phiên làm việc. Trong khoa học máy tính, Nó đơn giản là cách giao tiếp giữa client (ở đây là trình duyệt web hoặc ứng dụng trên thiết bị của bạn) với server. Một session bắt đầu khi client gửi request đến sever, nó tồn tại xuyên suốt từ trang này đến trang khác trong ứng dụng và chỉ kết thúc khi hết thời gian timeout hoặc khi bạn đóng ứng dụng. Giá trị của session sẽ được lưu trong một tệp tin trên máy chủ. Chính vì điều này, nếu bạn dùng session một cách vô tội vạ (giống như mình đã từng đó) thì sẽ khiến cho máy chủ phải lưu rất nhiều. Đặc biệt nếu ứng dụng đó có đến vài triệu người dùng chẳng hạn thì ... điều đó thật là kinh khủng. Thông thường chúng ta chỉ nên lưu trữ những thông tin tạm thời trong session VD như: thông tin đăng nhập, thông tin các sản phẩm trong giỏ hàng (đối với các trang web thương mại điện tử)...

Với mỗi session sẽ được cấp phát một định danh duy nhất SessionID. Khi kết thúc một phiên làm việc và bắt đầu một phiên mới, dĩ nhiên bạn sẽ được cấp một SessionID khác với trước đó.

Bạn đã bao giờ đặt ra câu hỏi rằng "sau khi tạo ra một session được lưu trên mấy chủ, thì làm thế nào hệ thống biết được rằng session đó là của client nào chưa?". Easy thôi, với mỗi session được tạo ra, đồng thời chúng sẽ tạo ra một tệp tin cookie lưu trên trình duyệt của bannj ứng với session đó. Như vậy chỉ cần so sánh tệp tin cookie bên phía client được gửi lên sever và tệp session được lưu trên server là ra ngay ý mà (ahaha)


### Cookie

Cũng giống như session, cookie cũng được dùng để lưu những thông tin tạm thời. Chính vì điều này khiến cho mình luôn bị nhầm lẫn giữa hai khái niệm hoài (bây giờ chắc đỡ hơn). Chỉ có điều, tệp tin cookie sẽ được truyền từ server tới browser và được lưu trữ trên máy tính của bạn khi bạn truy cập vào ứng dụng, Mỗi khi người dùng tải ứng dụng, trình duyệt sẽ gửi cookie để thông báo cho ứng dụng về hoạt động trước đó của bạn ![😦](media/😦.png) Đừng hỏi tại sao khi bạn vừa xem một chiếc đồng hồ cực đẹp trên một website mua sắm, đơn thuần chỉ là lướt qua như một cơn gió, vậy mà khi truy cập vào một trang web khác (có chạy quảng cáo) đã thấy cái đồng hồ đẹp lung linh đó bên dưới rồi =)) Rất nhiều những ứng dụng lợi dụng việc lưu trữ cookie trên trình duyệt để chạy quảng cáo, xây dựng hệ thống recommendation...

![[Pasted image 20220620082159.png]]

Và một điều vô cùng quan trọng là đừng bao giờ lưu trữ những thông tin quan trọng, yêu cầu tính bảo mật cao vào cookie, nó hoàn toàn có thể sửa đổi và đánh cắp, thấp chí có thể lợi dụng điều này để tấn công web site của bạn. (Minh toàn dùng extention "editthiscookie" của chrome để thay đổi cookie thôi à :v )

Mỗi cookie thường có khoảng thời gian timeout nhất định do lập trình viên xác định trước. Những thông tin được lưu vào cookie ví dụ như, thao tác người dùng, tần xuất ghé thăm website, thời gian truy cập... Tất cả chúng đều là những thông tin mang tính tạm thời và được lưu trong 1 khoảng thời gian ngắn.


### Cache

Cache là bộ nhớ đệm, vùng lưu trữ tạm thời trong máy tính. Nó khác với cookie ở chỗ thông tin lưu trữ ở đây là các tài liệu web, các hình ảnh, các video, HTML, .... Một phát kiến khá sáng suốt của con người trong thời kỳ công nghệ thông tin này để giảm tải băng thông, tăng tốc độ load, truy cập web. Bộ nhớ cache bao gồm bản sao các bit của trang Web được lưu trữ trên ổ đĩa cứng. Trình duyệt tải các bit khi bạn truy cập một trang Web nào đó, tốc độ truy cập sẽ nhanh hơn và tiết kiệm được băng thông khi "download". Bộ nhớ cache sẽ được lưu trữ cho đến khi bạn tự tay xóa nó đi. Do đó đừng dại mà xóa cache khi không cần thiết nhé (mình gỡ bỏ CCleaner trên máy tính từ lâu rồi (yaoming) )


Bộ nhớ cache chính là nơi trình duyệt của bạn lưu trữ những file coppy để bạn không phải tải lại lần nữa khi duyệt web. VD. Lần đầu khi bạn truy cập vào một trang web có rất nhiều hình ảnh, Bạn mất khoảng 1s để load xong trang (chắc do mạng cùi bắp), Nhưng nhờ có bộ nhớ cache, thời gian để bạn load trang có thể gần như là ngay lập tức luôn cũng được đó.


