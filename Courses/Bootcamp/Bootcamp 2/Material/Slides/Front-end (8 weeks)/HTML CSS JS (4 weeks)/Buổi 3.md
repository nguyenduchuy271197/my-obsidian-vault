- Project:
	- Template: https://www.w3schools.com/w3css/tryw3css_templates_architect.htm
	- Chrome Extensions:
		- Viewport resizer
		- VisBus
	- Steps:
		- Tạo github account và tạo project
		- Phân tích website:
			- Typography
			- Colors
			- Images
			- Shadows (bóng)
			- Border-radius (bán kính đường viền) (px / %)
			- Spacing
			- Elements and Components
			- Layout Patterns
		- Folder structure
		- Build project
			- Reset CSS
			- Base CSS
			- Main CSS
		- Elements and Components
		- Reponsive website
			- Breakpoints: 
				- Mobile: < 601px
				- Tablet: >= 601px
				- Desktop: >= 993px
					- Container: 1564px (nếu lớn hơn 1564px)
		- Test website
			- Link
			- Button
			- 

- Typography
	- Tạo ra bảng cho Typography


|           	| Font-family       	| Font-size      	| Font-weight   	| line-height      	| color          	| background-color 	| opacity     	|
|-----------	|-------------------	|----------------	|---------------	|------------------	|----------------	|------------------	|-------------	|
| Body      	| Verdana           	| 16px (default)    | 400 (default) 	| 22.5px           	| #000 (default) 	| #fff (default)   	| 1 (default) 	|
| Heading 1 	| Segoe UI          	| 36px           	| 700           	| 54px             	| #fff           	| #000             	| 0.75        	|
| Heading 2 	| Segoe UI          	| 24px           	| 400 (inherit) 	| 36px             	| #000 (inherit) 	| #fff (inherit)   	| 1 (inherit) 	|
| Heading 3 	| Segoe UI          	| 24px           	| 400 (inherit) 	| 36px             	| #000 (inherit) 	| #fff (inherit)   	| 1 (inherit) 	|
| Text      	| Verdana (inherit) 	| 15px          	| 400 (inherit) 	| 22.5px (inherit) 	| #000 (inherit) 	| #fff (inherit)   	| 1 (inherit) 	|

- Color:
	- Text:
		- primary: #000
	- Background:
		- primary: #fff 
- Images:
	- Thu thập hình ảnh

- Spacing:
	- Resource: https://carbondesignsystem.com/guidelines/spacing/overview/

- Elements and Components
	- Navigation Bar (Header)
	- Hero Section
	- Project Section
	- About Section
		- Card
	- Contact
		- Form
	- Location
	- Footer



- Reset CSS:
	- :focus:
		- outline: 0

	- a:
		- color: inherit
		- text-decoration: none

	- button:
		- font: inherit
		- display: block
		- border:none
		- cursor: pointer
		- background: transparent
		- 


	- form
		- input:
			- display: block
			- font-size: 100%
			- font: inherit


	- ol, ul:
		- list-style: none


	- Resource: https://meyerweb.com/eric/tools/css/reset/



	- Layout patterns
		- Container
		- Container-fluid



 - Folder structure:

```
landing-page  
 ┣ assets  
 ┃ ┣ css  
 ┃ ┃ ┣ _base.css  
 ┃ ┃ ┣ _main.css  
 ┃ ┃ ┗ style.css  
 ┃ ┣ img  
 ┃ ┃ ┣ members  
 ┃ ┃ ┃ ┣ member-1.jpeg  
 ┃ ┃ ┃ ┣ ...   
 ┃ ┃ ┣ projects  
 ┃ ┃ ┃ ┣ project-1.jpeg  
 ┃ ┃ ┃ ┣ ...   
 ┃ ┃ ┣ hero.jpeg  
 ┃ ┃ ┗ map.jpeg  
 ┗ index.html
```



- Note:
	- Thẻ img: Set display block bởi vì inline sẽ gây ra khoảng trắng ở dưới
	- Thẻ button và input không kế thừa font của thẻ cha -> Reset button và input
	- Text-transform cho các heading và các nội dung cần thiết
	- Sự khác nhau giữa width, min-width, max-width
	- Text-wrap: word-break -> Tránh bị overflow
	- Truncate đoạn văn bản
	- Vendor prefix: 

```css
.truncate {
  width: 250px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
```

```css
.line-clamp {
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;  
}
```

- Vendor Prefix:
	**-moz-**: Mozilla Firefox  
	**-webkit-**: Google Chrome, Apple Safari  
	**-o-**: Opera  
	**-ms**-: Microsoft Internet Explorer


- Test different browsers



- Sass
	- Live sass compiler: Để compile sass thành css
		- Configuration:
			- Compress css
			- Set đường dẫn chưa css file

	- Sass partial: Tách file style thành nhiều file Scss cho dễ debug
	- Sass variable: Sử dụng biến để tái sử dụng