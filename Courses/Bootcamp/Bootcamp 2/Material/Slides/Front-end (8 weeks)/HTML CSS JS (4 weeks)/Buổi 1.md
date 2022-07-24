### Cài đặt các phần mềm:
- Slack
- Vscode
- Figma Desktop
- Git bash
- Github Desktop
- MongoDB Compass
- Postman
- Obsidian Vault (Notion)
- Tạo tài khoản CodeSandBox

---

### Github, Gihub usage:
- Tạo tài khoản github
- Tạo profile với https://gprm.itsvg.in/
- Tạo repository cho bootcamp note
- Tạo repository cho bootcamp code

---

### Obsidian Vault Usage:
- Cài đặt các plugin hỗ trợ cho việc note
- Tìm hiểu về Markdown
---

### Các extension:
- Auto rename tag
- live server
- Code Spell Checker: sửa lỗi chính tả
- CSS peek
- htmltagwrap
- HTML to CSS autocompletion
- HTML CSS Support
- IntelliSense for CSS class names in HTML
- Intellicode: Recommend những phương thức hay sử dụng
- Material Icon Theme
- prettier
- Mobile view
- Image Preview
- ionicons
---


### Các việc cần làm trước khi code
- Autosave
- Format on save
---

### Nội dung bài học:

---
-  Giới thiệu về HTML:
		- Là Hypertext Markup Language
		- Hypertext: heading, hình ảnh, video, paragraph, link
	
![[Screen Shot 2022-07-18 at 21.23.14.png]]

---
- Cấu trúc một document HTML
	- !DOCTYPE: Khai báo kiểu document là HTML
	- Thẻ head: Chứa những cấu hình của web như title, và những thứ liên quan tới SEO
	- Thẻ body: Chứa nội dung

---

- Text elements:
	- h1, h2...h6: Dành cho heading
	- p: Thường dành cho các đoạn văn, văn bản
	- strong: Thẻ này ít sử dụng, có thể dùng trong việc nhấn mạnh cụm từ nào đó
	- li: Thẻ này cho việc liệt kê danh sách
	- ul: Thẻ này luôn đi kèm với li (ngoài ra còn có ol)
---

- Images và thuộc tính:
	- Thẻ img
	- src: Bỏ src vào trong này
	- alt: (alternative text) dùng để thay thế ghi ảnh khi ảnh ko load được, ngoài ra nó có mục đích cho việc SEO
	- width: 100
	- heigh: 100
---

- Hyperlink
	- Thẻ a: Dùng để liên kết tới trang khác
	- href: Hypertext reference, đường dẫn để tham chiếu tới trang khác
	- target: blank
---

- Thẻ div: Là một box
---

- Cấu trúc trang web (Các thẻ Semantic)
	- Thẻ header
	- Thẻ article
	- Thẻ footer
	- Thẻ main
---


- Bài tập:
	- https://www.w3schools.com/html/exercise.asp

---

- Giới thiệu về CSS:
	- Cascading Style Sheet
	- font, text, spacing, layout,

![[Screen Shot 2022-07-18 at 22.31.57.png]]
---


- Các kiểu style trong CSS:
	- Inline, internal, external
---

- Style cho text:
	- font-family
	- font-size
	- font-weight
	- text-transform
	- text-style
	- line-height
	- text-align: center

![[Screen Shot 2022-07-18 at 22.35.05.png]]
---


- Kết hợp selector
	- h2, h3, h4 : Các selector có cùng styling -> DRY
	- section h1: Style các tag h1 trong thẻ section
---


- Class và id
	- Giống: 
		- khai báo tên cho các thẻ để có thể style hoặc là sử dụng tương tác trong DOM
		-  Có thể đặt nhiều class trong một thẻ
	- Khác:
		- Khi khác báo tên id cho thẻ nào đó thì sẽ ko dùng lại lần 2 nữa, còn class thì khai báo một lớp cho nhiều thẻ

		- Khai báo trong css thì id bắt đầu bằng #, class bắt đầu bằng .
---

- Color:
	- Mô hình RGB: 
		- Tất cả các màu sắc đều được hình thành bởi sự kết hợp giữa ba màu sắc là Red, green và blue
		- Mỗi giá trị từ 0 -> 255
		- Kí hiệu trong css: rgb(255, 0, 0)
		- alpha: Độ trong suốt rgba(255, 0, 0, 0.5)
	- Hexadecimal:
		- #ffffff -> viết tắt thành #fff

	- Màu xám (gray):
		- Có tổng cộng 256 giá trị gray
		- Khi giá trị của 3 channels giống nhau -> tạo ra màu gray
		- vd: rgb(100,100,100)
	- Thường sử dụng:
		- color
		- background-color

---


- Pseudo classes (Lớp giả)
	- :first-child, :last-child
	- nth-child(even)
	- :not(:last-child)
---


- Styling cho thẻ a:
	- a:link -> Trạng thái ban đầu (chưa click vô lần nào)
	- a:visited -> Link đã từng click vô rồi
	- a:hover -> Khi di chuyển chuột lên link
	- a:active -> Lúc click chuột vô thẻ a
	- Kiểm tra bằng cách sử Chrome Dev Tool

---

- Conflict selectors (Sự xung đột giữa các selectors)
	- !important -> Inline -> Id -> class (pseudo-class) -> element (p, div, li) -> Universal selector
	- class -> có thể đặt nhiều class trong một thẻ
---


- Inheritance and Universal Selectors (Kế thừa)
	- CSS cho body font-family, font-size, các element con kế thừa những thuộc tính này
	- Tuy nhiên có vài thẻ ko kế thừa thuộc tính này như thẻ a
---


- Box model (Mô hình hộp)
	- Content: Nội dung (text, images, ...)
	- Padding: Khoảng cách từ nội dung đến viềng
	- Border: Viềng
	- Margin: Khoảng cách giữa các elements
	- Nếu set background-color thì phần padding và content sẽ được fill bởi color đó
	- Chiều dài (width) của box sẽ được tính = margin_left + border_left + padding_left + content + padding_right + border_right + margin_right
	- Tương tự với height
	- Thử thêm thuộc tính width và height và kiểm tra với Chrome Dev Tool
---

- Cách center một box
	- Set width cho box đó là 500px
	- Lúc này box sẽ chưa nằm ở giữa, bạn thêm cho nó thêm thuộc tính margin left và right là auto, thì lúc này nó sẽ center box cho bạn
	- Thường thì mình sẽ đặt class container

---

- Types of boxes (Các kiểu box)
	- Block:
		- Chiều dài chiếm 100% thẻ cha, không quan tâm tới độ dài của content
		- Các element sẽ stack lên nhau
		- Các thẻ: body, main, header, section, nav, aside, div, h1-h6, p, ul, ol, li, ...
		- Trong CSS: display: block

	- Inline:
		- Chiếm chiều rộng bằng content của nó
		- Không gây ra vấn đề break-line (đó là xuống dòng)
		- height và width không được apply
		- Paddings và margin chỉ được apply theo chiều ngang (left và right)
		- Các thẻ: a, img, strong, button, span
		- Trong CSS: display: inline

	- Inline-block:
		- Chiếm chiều rộng bằng content của nó
		- Không gây ra vấn đề break-line (đó là xuống dòng)
		- height và width được apply
		- Paddings và margin được apply
		- Trong CSS: display: inline-block

	- Lưu ý: Các bạn có thể thay đổi display của element để hợp với context lúc đó
---


- Positioning
	- Position: static
		- Normal flow
		- Element sẽ được đặt theo thứ tự như trong HTML

	- Position: relative
		- Normal flow
		- Element sẽ được đặt theo thứ tự như trong HTML
		- Tuy nhiên, bạn có thể thay đổi vị trí của element sử dụng top, right, bottom, left để thay đổi vị trí của nó
		- Xem vị trí element đang đứng là điểm quy chiếu
	- Position: absolute
		- Không bị ảnh hưởng bởi các element xung quanh, và overlap lên chúng
		- Bạn có thể thay đổi vị trí của element sử dụng top, right, bottom, left để thay đổi vị trí của nó
		- Xem vị trí của elemnent thẻ cha có chứa thuộc tính position là điểm quy chiếu
---


- Pseudo-elements:
	- Dùng để style cho các phần của 1 element
	- ::first-line: thêm một style cho dòng đầu tiên của text
	- ::first-letter: thêm một style cho chữ đầu tiên của text
	- ::before: thêm content trước content của element
	- ::after: thêm content sau content của element
---

- Box-sizing:
	- Mặc định là content-box -> width = content
	- Set lại border-box -> width =  border_left + padding_left + content + padding_right + border_right (Mô tả bằng hình ảnh và giải thích lí do tại sao phải set border-box)
---

- Flexbox:
	- Review:
		- Display: block, inline, inline-block
		![[Pasted image 20220719103807.png]]


	- Định nghĩa:
		- Dùng cho việc layout theo không gian 1 chiều
		- Được sử dụng phổ biến nhất, linh hoạt và hiệu quả
	- Cách hoạt động
		- Flexbox bao gồm 2 thành phần chính: box cha và các box con nằm bên trong (flex-items)
		- **main start, main end, cross start, cross end:** Điểu bắt đầu của container theo main axis được gọi là main start, điểm kết thúc của container theo main axis gọi là main end, với cross start và cross cũng tương tự nhưng dựa theo cross axis.
		-   **main axis:** Trục này chính là hướng của các item hiển thị, mặc định thì sẽ chạy từ trái qua phải.
		-   **cross axis:** Trục này vuông góc với main axis`, `chạy từ trên xuống dưới.
		-   **main size:** Là kích thước của mỗi item dựa theo trục main axis.
		-   **cross size:** Là kích thước của mỗi item dựa theo trục cross axis.


	- Các thuộc tính của flex container
		- display: flex
		- flex-direction: row (mặc định)
		- flex-wrap: nowrap (mặc định)
		- justify-content: flex-start
		- align-items:stretch
		- gap: 0
		- align-self: auto | center | flex-start | stretch
		- flex-grow: 0 -> cho phép mở rộng element (0: no, 1: yes)
		- flex-shrink: 1 -> cho phép shrink element (0: no, 1: yes)
		- flex-basis: auto -> Định nghĩa chiều rộng của item
		- flex: 0 1 auto (Viết tắt của 3 cái thuộc tính trên)
		- order: 0 -> Controls order of items


	- flex-direction

		`flex-direction` dùng để chỉ định hướng hiển thì của các item, việc thay đổi hướng hiển thị flex cũng thể có thể cho phép ta thay đổi vị trí của các flex item.
		
		##### flex-direction: row
		
		`flex-direction: row` là giá trị mặc định khi sử dụng flexbox, không thực hiện bất kỳ thay đổi nào, chỉ đặt các item `từ trái qua phải` theo trục chính.


	
	- flex-direction: row-reverse

		Giống với tên gọi, `flex-direction: row-reverse` ngược lại với `row`, các item sẽ được đặt `từ phải qua trái`.

	- flex-direction: column

		Khi chúng ta xét `flex-direction: column`, lúc này trục chính sẽ đi từ trên xuống dưới vậy nên giờ đây các items sẽ được xếp chồng lên nhau.

	- flex-direction: column-reverse

		Khi đó các items sẽ được xếp chống lên nhau nhưng theo chiều ngược lại. Hay để ý sẽ thấy ở ví dụ trên (1) sẽ ở trên cùng, nhưng khi sử dụng `column-reverse` (1) sẽ ở dưới cùng.


	- flex-wrap

		`flex-wrap` dùng để kiểm soát việc bọc các items nằm gọn trong container. Nếu chúng ta giảm chiều rộng của trình duyệt, chúng ta có thể không nhìn thấy một số item trên cùng một dòng. Thuộc tính `flex-wrap` có thể giải quyết vấn đề đó:
		
		-   nowrap (mặc định): Không có gì thay đổi
		-   wrap: các items sẽ được bọc trọn trong container
		-   wrap-reverse


	- flex-flow

		`flex-flow` là cách viết rút gọn của `flex-direction` và `flex-wrap`. Trong `flex-flow` giá trị đầu tiên là `flex-direction` và thứ 2 là `flex-wrap`
	
	- justify-content

		`justify-content` dùng để căn chỉnh vị trí của các items so với trục chính(main axis). Có 6 giá trị có thể dùng đối với thuộc tính `justify-content`:
		
		-   flex-start: sẽ đặt item bắt đầu từ main start (và đây cũng là giá trị mặc định)
		-   flex-end:sẽ đặt item bắt đầu từ main end
		-   center: sẽ đặt tất cả item ở giữa trục main axis
		-   space-between: sẽ chia đều khoảng cách thừa và thêm nó vào giữa các item
		-   space-around: sẽ chia khoảng cách ở đầu và cuối. Khoảng cách ở đầu và cuối sẽ bằng 1 nửa khoảng cách ở giữa 2 item với nhau
		-   space-evenly: sẽ chia khoảng cách đều khoảng cách giữa các item với item, item và main start, item với main end bằng nhau

	- align-items

		Thuộc tính `align-items` dùng để xác định cách mà các flex item được đặt trong container dọc theo chiều cross axis.
		
		-   `align-items: stretch`: Chiều dài của item sẽ bằng chiều dài của cross axis.
		-   `align-items: flex-start`: Item được đặt ở điểm bắt đầu của cross start(trên cùng bên trái), và kích thước item không bị thay đổi.
		-   `align-items: flex-end`: Item được đặt ở điểm bắt đầu của cross end(dưới cùng bên trái)
		-   `align-items: center`: Item được đặt ở giữa điểm bắt đầu của cross start và điểm bắt đầu của cross end (ở giữa bên trái)
		-   `align-items: baseline`: Item sẽ được đặt dữ theo các ký tự thuộc item đó. Mục đích chính là căn chỉnh dữa liệu dòng văn bản của các item.


	- Source: https://viblo.asia/p/huong-dan-day-du-ve-css-flexbox-maGK7J9a5j2



	- CSS grid:
		- Dùng cho việc layout theo không gian 2 chiều (dĩ nhiên là 1 chiều vẫn được)
		- Grid container:
			- display: grid
			- grid-template-columns (300px, 1fr, repeat)
			- grid-template-rows
			- justify-items, align-items: Căn các items bên trong hàng và cột
			- justify-content, align-content: Căn cả grid bên trong container (nếu grid nhỏ hơn container)
			- gap
			- column-gap, row-gap

		- Grid items:
			- grid-column: start line /  end line (1 /  -1)
			- grid-row: start line / end line
			- Đặt grid item trong một cell nhất định dựa vào line numbers,  mở rộng (span) item cho nhiều cells


	- Web design rules:
		- Typography (Kiểu chữ)
		- Colors (màu sắc)
		- Images, illustration (hình ảnh và hình minh hoạ)
		- Icons
		- Shadows (bóng)
		- Border-radius (bán kính đường viền) (px / %)
		- Whitespace
		- Visual Hierarchy
		- User Experience (UX)
		- Elements and Components
		- Layout Patterns



- Components và layout patterns:
	- Accordion
	- Carousel
	- Table
	- Pagnination
	- Hero Section
	- Layout Structure


- Make a great website
	- Define:
		- Định nghĩa ra người sử dụng website của chúng ta
		- Website này về cái gì
	- Plan
		- Lên plan và thu thập các nội dung của website như: copy (text), images, videos, etc
		- Bạn nên cung cấp cho khách hàng vài content free trên mạng
		- Nếu site lớn thì bạn nên tạo ra một sitemap
	- Sketch
		- Nghĩ về các component bạn cần, sau đó bạn sử dụng nó trong layout pattern của bạn 
		- Sketch chúng trên giấy
	- Design and build
		- Design trên Figma, Photoshop dựa vào bản sketch và content khách hàng cung cáp
		- Layout và components: (colors, typography, icons, etc)
	- Test and optimize
		- Đảm bảo website của các bạn đều work trên tất cả các web browser (Chrome, Firefox, Safari, Edge)
		- Test website trên mobile
		- Tối ưu hình ảnh
		- Chạy Lighthouse để xem report
		- Cải thiện SEO
	- Launch
		- Upload tất cả các files đến hosting platform (Netlify)
		- Có thể chọn và mua domain name
	- Maintain and update
		- Cái đặt analytics software (Google analytics) để lấy thông kê về người sử dụng website
		- Tạo blog là cách để giúp user visit website nhiều hơn




- Project: Làm một trang landing page
	- Make a responsive website (mobile-first)
	- Smooth scrolling
	- Thêm favicon và meta description
	- Tối ưu hình ảnh (Image Optimization) với Sqooush
	- Deploy trên Netlify


```css
body {
	margin:0;
	padding:0;
}
```