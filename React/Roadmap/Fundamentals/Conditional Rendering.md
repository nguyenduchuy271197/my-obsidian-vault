Trong conditional render một component sẽ quyết định sẽ trả về element gì dựa trên một hay nhiều điều kiện được đưa ra.

Cách đơn giản nhất để dùng conditional rendering là sử dụng câu lệnh if else trong hàm render(). Tưởng tượng bạn không muốn render component của bạn vì nó không có các props cần thiết. Ví dụ, một component List sẽ không nên được render nếu list đó không có item nào bên trong. Bạn có thể sử dụng if để làm điều này:

```jsx
function List({ list }) {
  if (!list) {
    return null;
  }

  return (
    <div>
      {list.map(item => <ListItem item={item} />)}
    </div>
  );
}

```

Component mà return null tất nhiên sẽ không render ra gì cả. Tuy nhiên, ta nên hiện 1 đoạn text để báo cho người dùng rằng List đó rỗng để tăng trải nghiệm cho người dùng.

```jsx
function List({ list }) {
  if (!list) {
    return null;
  }

  if (!list.length) {
    return <p>Xin lỗi, danh sách trống.</p>;
  } else {
    return (
      <div>
        {list.map(item => <ListItem item={item} />)}
      </div>
    );
  }
}

```

Kết quả đạt được là List có thể sẽ hoặc không render ra gì cả, render ra text, hoặc một danh sách các item. Câu lệnh if-else là lựa chọn cơ bản nhất cho việc conditional rendering trong React.


#### Ternary operation (toán tử 3 ngôi)

Bạn có thể làm cho câu lệnh if-else trở nên ngắn gọn hơn bằng cách sử dụng ternary operation: `condition ? expr1 : expr2`

Ví dụ, tưởng tượng bạn có một switch để chuyển đổi giữa 2 chế độ Xem và Chỉnh sửa trong component của bạn. Bạn có thể dùng boolean để quyết định xem element nào sẽ được trả về.

```jsx
function Item({ item, mode }) {
  const isEditMode = mode === 'EDIT';

  return (
    <div>
      { isEditMode
        ? <ItemEdit item={item} />
        : <ItemView item={item} />
      }
    </div>
  );
}

```

Nếu mỗi nhánh của ternary operation lớn dần lên, bạn có thể cho chúng vào trong ngoặc đơn.

```jsx
function Item({ item, mode }) {
  const isEditMode = mode === 'EDIT';

  return (
    <div>
      {isEditMode ? (
        <ItemEdit item={item} />
      ) : (
        <ItemView item={item} />
      )}
    </div>
  );
}

```

Ternary operation cũng làm conditional rendering trở nên đơn giản hươn if-else. Bạn có thể viết theo kiểu inline ngay ở hàm return.

#### Logic + toán tử &&

Ta sẽ thường dùng cách này khi muốn render ra element hoặc ko render ra gì cả (null). Ví dụ bạn có một spinner thể hiện việc đang load dữ liệu. Nếu load xong thì nó sẽ biến mất. Bạn có thể làm nó với 2 cách để cập ở trên:


```jsx
function LoadingIndicator({ isLoading }) {
  if (isLoading) {
    return (
      <div>
        <Spinner />
      </div>
    );
  } else {
    return null;
  }
}

```

```jsx
function LoadingIndicator({ isLoading }) {
  return (
    <div>
      { isLoading
        ? <Spinner />
        : null
      }
    </div>
  );
}

```

Nhưng có một cách khác hay hơn để thay thế cho việc phải return null. Sử dụng `logic + toán tử &&` giúp bạn điều kiện của bạn return null dễ dàng hơn.

Vậy cách đó là gì và nó hoạt động như thế nào? Trong JavaScript `true && 'Hello World'` luôn trả về `‘Hello World’`. Còn `false && 'Hello World'` luôn trả về `false`.

```jsx
const result = true && 'Hello World';
console.log(result);
// Hello World
```

```jsx
const result = false && 'Hello World';
console.log(result);
// false
```

Trong React ta cũng có thể sử dụng phương pháp này. Nếu điều kiện trả về là `true`, biểu thức phía sau `toán tử &&` sẽ là output. Nếu điều kiện trả về `false`, React sẽ bỏ qua và không xử lý biểu thức đó.

```jsx
function LoadingIndicator({ isLoading }) {
  return (
    <div>
      { isLoading && <p>Loading...</p> }
    </div>
  );
}
```


Roadmap: [[Roadmap Image]]
Next: [[Component Life Cycle]]