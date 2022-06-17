Đối với các coder thì khái niệm về component thực sự không còn xa lạ, đối với 1 người mới bắt đầu thì nôn na component nghĩa là 1 thành phần. Nghĩ đơn giản vậy thôi, chúng ta có 1 ví dụ :

![[Pasted image 20220615204751.png]]


Ở trên là hình ảnh mô phỏng 1 trang web sau khi chúng ta đã hoàn thành. Dưới khái niệm component, chúng ta sẽ chia trang web trên thành nhiều các thành phần nhỏ lẽ, mỗi thành phần đó được gọi chung là 1 component.

![[Pasted image 20220615204842.png]]


Mỗi 1 ô trong dấu nét đứt đấy là một component, chúng ta có 1 component cha chứa tất cả đám con của nó, cái này lồng vào cái kia để tạo thành 1 website hoàn chỉnh. Nhìu vào có vẻ khó nhưng đừng sợ, chúng ta sẽ thử làm từng thứ 1.


Read more: https://viblo.asia/p/reactjs-components-in-react-1VgZvXgM5Aw



### Functional Component

```jsx
ReactDOM.render( 
<div> 
	<p>Hello, world!</p> 
</div>, 
document.querySelector("#container") 
);
```

### Class Component
```jsx
class HelloWorld extends React.Component { 
	//something here 
} 
ReactDOM.render( 
<div> 
	<p>Hello, world!</p> 
</div>, 
document.querySelector("#container") 
);
```


Roadmap: [[React/Roadmap/Advanced/Roadmap Image]]

Next: [[Props and State]]