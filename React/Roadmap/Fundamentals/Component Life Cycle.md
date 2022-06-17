Xin chào anh em, lâu lâu mình lại viết bài chia sẻ kiến thức mà mình đã tìm hiểu được. Thì hôm nay mình xin được viết về **Vòng đời của component** trong ReactJS. Như các bạn biết đấy khi ta học về một công nghệ mới nào đó thì chúng ta cần tập trung hiểu cái chủ đạo trong công nghệ đó. Vì thế nếu như để nói về ReactJS thì chúng ta sẽ thấy rằng `component` là thành phần quan trọng, và có rất nhiều thứ xoay quanh về nó. Chính vì để tìm hiểu kỹ hơn một chút ngoài `state, props,...` liên quan đến component thì chúng ta cũng nên tìm hiểu một chút về những phương thức lifecycle trong React. Đây chính là hình ảnh mình họa cho vòng đời của compponent trong React.


![[Pasted image 20220616083413.png]]

Nhìn vào hình ảnh trên thì có 3 phần chính chúng ta sẽ tìm hiểu đó chính là

-   Mounting
-   Updation
-   Unmounting

### Mounting

Rồi đầu tiên mình tra từ điển nghĩa của từ `Mounting` đó là `something on which something else is or can be attached`. Chắc hẳn các bạn cũng biết khái niệm **hook** rồi đúng không - tức là cho phép người dùng can thiệp vào quá trình cập nhật UI với những thay đổi của state hoặc props

Các bạn nhìn cột Mounting có 3 phướng thức lifecycle đó là

-   componentWillMount()
-   render()
-   componentDidMount()


Như các bạn thấy đấy khi chúng ta refresh lại trang web hoặc mới truy cập thì 3 method lifecycle này sẽ lần lượt chạy. Một khi mà component được render trong lần đầu tiên thì phương thức `componentWillMount` sẽ được gọi trước khi render. Chúng mình có thể hiểu như này, trước khi compont vô DOM bằng hàm render() thì hàm `componentWillMount()` sẽ được gọi. Chú ý chúng ta không nên gọi hàm `setStae()` trong hàm `componentWillMount()` vì nó chưa có DOM nào để tương tác.


`componentDidMount` sẽ được gọi sau khi render component, ở đây cũng là nơi thực hiện các hàm AJAX, axios request, DOM hay update state sẽ được thực thi tại đây. Phương thức này cũng được kết nối với các Framwork khác hay database. Chúng mình sẽ đặt hàm `setState()` ở đây để tương tác vì Component đã được vô DOM

```jsx
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';


class Demo extends Component {
    constructor(props) {
         super(props);
         // Don't do this!
         this.state = { color: 'green' };
    }
    componentWillMount() {
      console.log("componentWillMount da chay")
    }

    componentDidMount() {
        console.log("componentDidMount da chay")
    }
    
    render() {
        console.log("Ham render da duoc chay");
        return (
           <div>
              <button onClick={() =>  this.setState({color : 'aaaaa'})}>Submit</button>
                <p>{this.state.color}</p>
            </div> 

        )
    }
}
class App extends Component {
  render() {
    return (
      <div className="App">
        <header className="App-header">
          <img src={logo} className="App-logo" alt="logo" />
          <h1 className="App-title">Welcome to React</h1>
        </header>
        <Demo></Demo>
        <p className="App-intro">
          
        </p>
      </div>
    );
  }
}

export default App;
```


Chúng ta npm start và bật F12 lên và chúng ta được kết quả như sau

![[Pasted image 20220616091123.png]]


Vậy chúng mình có thể kết luận được khi mà Component được khởi tạo thì React sẽ follow theo trình tự như sau :

-   Khởi tạo class đã kế thừa từ Component
-   Khởi tạo giá trị mặc định cho Props
-   Khởi tạo giá trị mặc định cho State
-   Gọi hàm componentWillMount()
-   Gọi hàm render()
-   Gọi hàm componentDidMount()

# 2.Updation
## 2.1.Props && State/Users/huy/Desktop/component/src/index.js
/Users/huy/Desktop/component/src/Clock.jsx
![[Pasted image 20220616091321.png]]


Chúng mình sẽ đi tìm hiểu từng method một nhé

-   `componentWillReceiveProps()`: Chạy khi component con nhận props từ component cha. Sau khi nhận được props mới từ component cha rồi có thì component con có thể set lại state.
-   `shouldComponentUpdate()`: Hàm này có thể nói là nó tăng hiệu năng của React lên. Nếu như return `false` thì các phương thực `componentWillUpdate, render, componentDidUpdate` sẽ không được chạy nữa(vì mặc định nó return về true để chạy được 3 hàm tiếp theo, nhiều trường hợp mình không cần chạy 3 hàm tiếp theo).
-   `componentWillUpdate()`: Hàm này cũng giống như hàm `componentWillMount()` trước khi re-render ra Component. Nhưng chúng mình hầu hết không tương tác gì nhiều lắm trong hàm này, hàm `setState` hầu hết chúng mình sẽ sủ dụng trong hàm `componentWillReceiveProps`
-   `componentDidUpdate()`: hàm này được gọi đến sau khi đã re-render lại hay React đã cập nhật lại UI, nếu mà chúng ta muốn chạy animation thì đây chính là lúc chúng ta nên gọi trong hàm này.


# 3.Unmount

Quá trình unmounting xảy ra khi component bị remove khỏi DOM, hay nói một cách khác là hàm `componentWillUnmount` sẽ được gọi khi render ra không có component nào hoặc người dùng chuyển hướng trang web.


## Chú ý

Các bạn chú ý rằng khi khởi tạo Component chúng ta chỉ khởi tạo this.state đúng một lần. Mọi hành động làm thay đổi state trong nội tại của component đều phải sử dụng hàm `setState`, và bạn cần nên nhớ rằng hàm `setState` là hàm asyn nên sau khi chúng ta `setState` xong mà chúng ta truy cập ngay vào state vd như chúng ta in ra state vừa mới được set xong thì chúng ta sẽ không nhận được giá trị vừa mới set.






Roadmap: [[React/Roadmap/Advanced/Roadmap Image]]

Related: [[Component Life Cycle (cont)]]

Next:[[List and Key]]

Reference: https://viblo.asia/p/lifecycle-component-trong-reactjs-gGJ59jzxKX2