### Refs cung cấp cho chúng ta cách access đến các DOM nodes hoặc React elements được tạo ra trong method render

## Giới thiệu về `refs`

Trong data flow của React, `props` là cách để các parent components tương tác với các child components. Để updated child componnent, bạn cần re-render nó với các `props` mới. Nhưng sẽ có một số trường hợp cần bắt buộc phải updated các child component bên ngoài data flow của React. Các child component có thể là 1 instance của React Component hoặc có thể là DOM element. Cho những trường hợp này, chúng ta có thể sử dụng `react Refs`.

## Một số trường hợp dùng `refs`

-   Control focus; get text của DOM element; get state value(play/pause/timeline) của media playback,... nói chung là dùng trong những trường hợp các data này không cần đưa vào `state` của component.
-   Trigger các transitions, animations: sử dụng `refs` khi một element cần trigger animation/transition của một element khác
-   Tích hợp với các Third-party DOM libraries


## Sử dụng `useRef` của react hooks

```jsx
const refContainer = useRef(initialValue);
```

Đoạn code ở trên, chúng ta sẽ khởi tạo 1 `ref` object có `.current` property với `initialValue`. `useRef` sẽ cho cùng 1 `ref` object trên mỗi lần render.

-   Nếu `ref` object này là 1 `DOM element` thì chúng ta có thể manipulated các `DOM element` này như `pure javascript` thường làm.
-   Nếu `ref` object này là 1 `javascript object` thì các object này sẽ tồn tại trong scope của component như 1 `plain javascript object` thông thường.

## Các ví dụ:

### Điều khiển focus của input:

Ở ví dụ này, chúng ta sẽ sử dụng `userRef` để tham chiếu tới input element, sau đó sẽ thực hiện focus input khi click button

```jsx
import React, { useRef } from "react";

function App() {
  const inputEl = useRef(null);

  const onButtonClick = () => {
    inputEl.current.focus();
  };

  return (
    <div className="App">
      <h2>Use refs to control focus</h2>
      <input ref={inputEl} />
      <button onClick={onButtonClick}>Focus the input</button>
    </div>
  );
}
```

Demo: [https://codesandbox.io/s/dawn-thunder-w9hur](https://codesandbox.io/s/dawn-thunder-w9hur)

### Set/Get giá trị trước đó của state:

Ở ví dụ này; sẽ có 1 input, nhập một vài ký tự và thực hiện `blur` input đó, chúng ta sẽ check xem `previous value`, `current value` sau mỗi lần blur input (case này trong thực tế là: nếu sau mỗi lần blur mà giá trị trước và sau khi blur có thay đổi thì thực hiện call api, ngược lại nếu không thay đổi thì không làm gì cả)


```jsx
import React, { useRef, useState } from "react";

function App() {
  const prevValue = useRef("");
  const [value, setValue] = useState("");

  const onInputChange = e => {
    setValue(e.target.value);
  };

  const onInputBlur = () => {
    console.log(`Previous value: ${prevValue.current}`);
    console.log(`Current value: ${value}`);
    prevValue.current = value;
  };

  return (
    <div className="App">
      <h2>Use refs to set/get previous state's value</h2>
      <input value={value} onBlur={onInputBlur} onChange={onInputChange} />
      <div>Type something, blur input and check result in console.log</div>
    </div>
  );
}

```

Demo: [https://codesandbox.io/s/hungry-glade-d7mjb](https://codesandbox.io/s/hungry-glade-d7mjb)


Roadmap: [[Roadmap Image]]

Next: [[Render Props]]

Reference: https://viblo.asia/p/refs-trong-react-la-gi-va-mot-so-truong-hop-su-dung-refs-RnB5p4y65PG


