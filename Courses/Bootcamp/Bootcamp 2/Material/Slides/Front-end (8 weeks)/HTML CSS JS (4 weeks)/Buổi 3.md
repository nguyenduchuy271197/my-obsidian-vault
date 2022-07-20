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
		- Reponsive website
			- Breakpoints: 
				- Mobile: < 601px
				- Tablet: >= 601px
				- Desktop: >= 993px
					- Container: 1564px (nếu lớn hơn 1564px)

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
		- font: inherit
		- color: inherit

	- button:
		- display: inline-block
		- border:none
		- outline:none
		- text-align:center
		- cursor: pointer


	- form
		- input:
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

