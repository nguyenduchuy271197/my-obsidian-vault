Trong bài viết lần này, chúng ta sẽ xem xét về **useCallback**, một trong những **hook** được giới thiệu từ bản cập nhật của **React**, và tìm hiểu xem làm thế nào để chúng ta sử dụng **useCallback** tốt.

## Giới thiệu sơ về `useCallback`

`useCallback` là được sử dụng để tối ưu quá trình **render** của **React functional components**. Nó sẽ rất hữu ích đối với trường hợp một thành phần (component) liên tục được hiển thị lại không cần thiết trong quá trình xử lý sự kiện người dùng và có hành vi chức năng phức tạp. Chúng ta sẽ xem xét thông qua ví dụ đơn giản về cách triển khai hook này để xem cách nó có thể giúp chúng ta đạt hiệu quả thế nào trong quá trình xử lý **re-rendering** của **component**.

Hãy nhớ rằng **React** đã rất nhanh, tối ưu hiệu xuất chỉ nên sử dụng cho những component có khả năng chậm, xử lý tác vụ nặng. Khi đó, chúng ta sẽ xem xét xử dụng `useCallback` làm một phần hỗ trợ tối ưu hiện xuất trong các hook.

Nào, bây giờ hãy xem xét ví dụ đơn giản qua `Counter` Component nhé:

Hãy nhớ rằng **React** đã rất nhanh, tối ưu hiệu xuất chỉ nên sử dụng cho những component có khả năng chậm, xử lý tác vụ nặng. Khi đó, chúng ta sẽ xem xét xử dụng `useCallback` làm một phần hỗ trợ tối ưu hiện xuất trong các hook.

Nào, bây giờ hãy xem xét ví dụ đơn giản qua `Counter` Component nhé:

```jsx
import React, { useState, useCallback } from 'react'

function Counter() {
	const [count, setCount] = useState(0);
	const [countOther, setCountOther] = useState(0);
	
	const increase = () => setCount(count + 1);
	const decrease = () => setCount(count - 1);
	
	const increaseOther = () => setCountOther(countOther + 1);
	const decreaseOther = () => setCountOther(countOther + 1);
	
	return (
			<>
				<div>Count: {count}</div>
				<button onClick={increase}>+</button>
				<button onClick={increase}>-</button>

				<div>Count other: {countOther}</div>
				<button onClick={increaseOther}>+</button>
				<button onClick={decreaseOther}>-</button>
			</>
	)
}

export default Counter;
```

Điều này khá đơn giản, chúng ta có biến **2 state** nắm giữ số đếm và 4 hàm để thay đổi con số của 2 state trên. Tuy nhiên, vấn đề ở đây là mỗi lần thành phần `Counter` này re-render, tất cả 4 hàm, `increase`, `decrease`, `increaseOther`, `decreaseOther` sẽ bị khởi tạo lại.

Chúng ta có thể thấy điều đó bằng cách sử dụng `Set` và thêm các hàm vào bên trong `Set` mỗi lần `Counter` re-render. Tại sao lại là `Set`. Đây là đối tượng lưu trữ phần tử có tính duy nhất, không trùng lặp.

```jsx
import React, { useState, useCallback } from 'react'

const storeSet = new Set(); 

function Counter() {
	const [count, setCount] = useState(0);
	const [countOther, setCountOther] = useState(0);
	
	const increase = () => setCount(count + 1);
	const decrease = () => setCount(count - 1);
	
	const increaseOther = () => setCountOther(countOther + 1);
	const decreaseOther = () => setCountOther(countOther + 1);
	
	storeSet.add(increase);
	storeSet.add(decrease);
	storeSet.add(increaseOther);
	storeSet.add(decreaseOther);
	
	console.log(storeSet);
	
	return (
			<>
				<div>Count: {count}</div>
				<button onClick={increase}>+</button>
				<button onClick={increase}>-</button>

				<div>Count other: {countOther}</div>
				<button onClick={increaseOther}>+</button>
				<button onClick={decreaseOther}>-</button>
			</>
	)
}

export default Counter;
```

Nào, bây giờ cùng kiểm tra thử nhé?. Mỗi lần bạn **click** vào bất kì nút tăng giảm sẽ thấy hiển thị giá trị của `storeSet`. Bạn sẽ thấy chúng tăng giá trị mỗi lần hiển thị, điều này cho thấy mỗi lần thành phần `re-render` sẽ tạo ra phiên bản hoàn toàn mới của các hạm được tạo ra.

Về cốt lõi, vấn đề này là do cách `JavaScript` xác định bình đẳng hàm.

## Function Equality trong Javascript

Hãy xem ví dụ bên dưới trong đó chúng ta có hàm `factory` đang trả về một hàm khác.


```js
function factory() {
	return (a,b) => a + b;
}

const functionA = factory();
const functionB = factory();

functionA(1,2); // 3
functionB(1,2); // 3

console.log(functionA === functionB) // false
console.log(functionA === functionA) // true
```


Tại đây, chúng ta tạo ra `functionA` và `functionB` thông qua `factory()`. Bạn có thể tìm hiểu thêm về hàm trong JavaScript thông qua [First-class Function](https://developer.mozilla.org/en-US/docs/Glossary/First-class_Function), nghĩa là chúng được thể hiện dưới dạng các đối tượng thông thường. Đối tượng hàm có thể trả về một hàm khác (giống như hàm `factory`).

Bạn có thể thấy rằng, mặc dù `functionA` và `functionB` đều đến từ cùng một hàm `factory` và cùng làm một việc. chúng vốn dĩ là các đối tượng khác nhau, vì vậy, chúng không thể bằng nhau. Bất kì hàm JavaScript nào chỉ có thể bằng chính nó.

Bây giờ cùng trở lại với **React**, khi một thành phần `re-render`, mọi hàm bên trong nó sẽ bị `recreated`. `useCallback` làm cho nó có thể được `memoize` lại (hay là **cache**) **instance** hàm giữa những lần `render`. Điều này có ý nghĩa thay vì tạo lại đối tượng hàm mới, chúng ta có thể sử dụng lại cùng một đối tượng giữa các lần hiển thị.

Hãy cùng cập nhật cho các hàm increase/decrease sử dụng `useCallback`

```jsx
const increase = useCallback(() => setCount(count + 1), [count]);
const decrease = useCallback(() => setCount(count - 1), [count]);
	
const increaseOther = useCallback(() => setCountOther(countOther + 1), [countOther]);
const decreaseOther = useCallback(() => setCountOther(countOther + 1), [countOther]);
```


Lưu ý, cách chúng ta sử dụng tham số bên trong mảng, phụ thuộc vào một trong các tham số bên trong hàm `useCallback`. Miễn là các giá trị trong mảng phụ thuộc giống nhau giữa các lần hiển thị, **React** sẽ tiếp tục sử dụng phiên bản được `memoized` (cached) của hàm. Nếu các giá trị bên trong mảng phụ thuộc, thay đổi giữa các lần hiển thị, React sẽ tạo lại hàm.

Trong trường hợp này, khi chúng ta thử ấn button `increase` phía trên sau khi bọc các hàm setState lại bằng `useCallback` , kiểm tra hiển thị giá trị của `storeSet` chúng ta chỉ thấy duy nhất có một giá trị được tăng thêm, tiếp tục ấn button `increase` chúng ta vẫn không thấy giá trị thay đổi.

Mặc dù đây là một ví dụ rất đơn giản, nhưng chúng ta có thể thấy cách sử dụng `useCallback` để tối ưu hóa các thành phần có các chức năng phức tạp hoặc tốn nhiều tài nguyên.

## Khi nào không nên sử dụng `useCallback`

Tuy nhiên, hãy đảm bảo rằng điều này không đi quá đà. `useCallback` cũng sỡ hữu nhược điểm,, chủ yếu là độ phức tạp của mã. Ở đây có rất nhiều trường hợp không hợp lý khi thêm `useCallback` và chúng ta phải chấp nhận để hàm khởi tạo lại. Như đã nói, `useCallback` cũng sở hữu nhược điểm về hiệu xuất, vì nó vẫn phải chạy trên mọi thành phần `render`.

Trong ví dụ này, `useCallback` thực chất sẽ không giúp tối ưu, vì chúng ta tạo đang tạo xử lý `handleClick` cho cả quá trình render của thành phần khác.

```jsx
const ComponentA = () => {
	const [count, setCount] = useState(0)
	const handleClick = useCallback(() => setCount(count + 1), [count]);
	
	return <ButtonWrap onClick={handleClick} />
}

const ButtonWrap = ({children, ...props}) => {
	return <button {...props}>Button Children</button>
}
```

Trong trường hợp này, `useCallback` sẽ không phát huy được nhiều tác dụng của nó.

Khi nghĩ về các nâng cấp hiệu suất như sử dụng `useCallback`, luôn phải đo lường tốc độ của các thành phần component của bạn trước khi bắt đầu tối ưu hoá chúng. Việc tối ưu hoá không cần thiết sẽ khiến code của bạn trở nên rườm rà, phức tạp và có thể khó bảo trì về sau.

## Kết luận

`useCallback` là một `react hook` mạnh mã để tối ưu hoá **React component** phức tạp bởi vì chúng sẽ lưu trữ lại các hàm giữa những lần render.

Trước khi làm việc với `useCallback`, đảm bảo bạn đã phân tích những điều sau:

-   Tốc độ tăng có đảm bảo độ phức tạo của vẫn giữ được ở mức cần thiết ?
-   Sử dụng `useCallback` có đảm bảo tăng tốc độ cho thành phần được sử dụng?

Roadmap: [[React/Roadmap/Advanced/Roadmap Image]]

Next: [[useRef]]

Reference: https://codestus.com/posts/huong-dan-su-dung-usecallback-trong-react