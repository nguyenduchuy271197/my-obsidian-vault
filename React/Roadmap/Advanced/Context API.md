Bạn đã bao giờ phải truyền một prop xuống 1 component trong React chỉ với mục đích truyền tiếp nó xuống component con của nó chưa? Đó chính xác là vấn đề mà React Context API cố gắng để cải thiện.

# Vấn đề

Hãy cùng xem ví dụ sau:

-   Chúng ta có một loại dữ liệu là 1 số với giá trị là 10.
-   Chúng ta cần dữ liệu này trong component Red và Green.
-   Component Green là con của component Blue, và Blue lại là con của component Red.
-   Vì vậy chúng ta sẽ cần phải gửi dữ liệu từ Red đến Blue chỉ để gửi nó tới Green.


![[Pasted image 20220616140708.png]]

Với hình trên thì code của chúng ta sẽ tương tự như sau:

```jsx
const Green = (props) => (
  <div className="green">{props.number}</div>
)
const Blue = (props) => (
  <div className="blue">
    <Green number={props.number} />
  </div>
)
 
class Red extends Component {
  state = {
    number : 10
  }
  render() {
    return  <div className="red">
      {this.state.number}
      <Blue number={this.state.number} />
    </div>
  }
}

```

Chúng ta đã gửi data xuống cho component Blue chỉ để truyền tiếp nó xuống cho Green. Đây mới chỉ là ví dụ đơn giản thôi. Thử tưởng tượng mọi chuyện sẽ tồi tệ thế nào nếu chúng ta có 10 tầng component lồng nhau.

Cho đến React 16.3 thì giải pháp cho vấn đề này là sử dụng Redux hoặc Mobx hoặc bất cứ thư viện nào để xử lý state. Nhưng giờ thì chúng ta đã có giải pháp nằm trong React luôn.

# Giải pháp: Quản lý state bằng React Context?

React Context cung cấp cho chúng ta cơ chế định nghĩa các data store và truy xuất chúng khi cần. Chúng ta không cần phải truyền data thông qua props nữa. Với React Context chúng ta có thể định nghĩa và sử dụng một thứ giống như là "global state" của ứng dụng vậy.

Roadmap: [[React/Roadmap/Advanced/Roadmap Image]]

Next: [[Refs]]

Related: [[useContext]]

Reference: https://viblo.asia/p/react-context-api-1VgZvE9RKAw


