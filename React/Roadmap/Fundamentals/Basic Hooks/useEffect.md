-   Hooks là một tính năng mới được thêm vào React 16.8. Nó cho phép bạn có thể sử dụng state và các chứ năng khác của React mà không cần khởi tạo Class, điều đó có nghĩa là có thể sử dụng state trong functional component.
-   Effect Hook cho phép thực hiện side effect bên trong các _function component_

# 2. React hook và useEffect() là gì?

Khi tham khảo tài liệu trên ReactJS offical và tìm kiếm về _**useEffect**_, chúng ta sẽ có 1 típs như này:

	If you’re familiar with React class lifecycle methods, you can think of useEffect Hook as componentDidMount, componentDidUpdate, and componentWillUnmount combined.

Điều đó có nghĩa là: mục đích _**useEffect**_ để quản lý vòng đời của của một component và nó phục vụ chúng ta sử dụng trong _function component_ thay vì các _lifecycle_ như trước đây trong _class component._

Lifecycle method trong _class component_ thực sự rất quan trọng, đôi khi chúng ta muốn fetch dữ liệu từ API khi rendering 1 component, đôi khi chúng ta muốn thực hiện những action cụ thể khi component update,... 2 Methods được cho là quan trọng nhất chính là **componentDidMount** và **componentDidUpdate**.

_**useState**_ cho phép chúng ta sử dụng state trong functional components. _**useEffect**_ cho phép chúng ta sử lý logic trong lifecycle methods. Từ cái tên _**useEffect**_ chắc chúng ta cũng hiểu được hàm sẽ được gọi mỗi khi có gì đó ảnh hưởng đến components của bạn. Và thực sự nó giống với định nghĩa của **componentDidMount** và **componentDidUpdate**.

# 3. Cách sử dụng useEffect() trong nhiều trường hợp

Hãy thử viết một vài đoạn code để tìm hiểu **useEffect()**. Chẳng hạn chúng ta muốn khai báo thuộc tính trong state của 1 object, và 2 thuộc tính đó là name và familyName. Initial state sẽ là "name" và "family" và sau khi rendering, component sẽ thay đổi.

First step: Khởi tạo states

```jsx
import React, {useState} from 'react';

export const EffectDemo = () => {
    //State
    const [fullName, setFullName] = useState({name: 'name', familyName: 'family'});
    const [title,setTitle] = useState('useEffect() in Hooks');
    
    
    return(
        <div>
            <h1>Title: {title}</h1>
            <h3>Name: {fullName.name}</h3>
            <h3>Family Name: {fullName.familyName}</h3>
        </div>
    );
};
```

Second Step: khai báo **useEffect()**

```jsx
import React, {useEffect, useState} from 'react';

export const EffectDemo = () => {
    //State
    const [fullName, setFullName] = useState({name: 'name', familyName: 'family'});
    const [title,setTitle] = useState('useEffect() in Hooks');

    //useEffect
    useEffect(() => {
        setFullName({name:'TrungHC',familyName: 'HCT'});
    });

    return(
        <div>
            <h1>Title: {title}</h1>
            <h3>Name: {fullName.name}</h3>
            <h3>Family Name: {fullName.familyName}</h3>
        </div>
    );
};
```

như mọi người đã thấy, đối số của useEffect() là một hàm xử lý khi có gì thay đổi components. Sau đây là kết quả:

![[Pasted image 20220616112247.png]]

Như vậy kết quả đã như chúng ta mong muốn. Tuy nhiên check log đã, xem hàm useEffect này được gọi bao nhiêu lần

```jsx
import React, {useEffect, useState} from 'react';

export const EffectDemo = () => {
    //State
    const [fullName, setFullName] = useState({name: 'name', familyName: 'family'});
    const [title,setTitle] = useState('useEffect() in Hooks');

    //useEffect
    useEffect(() => {
        console.log('useEffect has been called!');
        setFullName({name:'TrungHC',familyName: 'HCT'});
    });

    return(
        <div>
            <h1>Title: {title}</h1>
            <h3>Name: {fullName.name}</h3>
            <h3>Family Name: {fullName.familyName}</h3>
        </div>
    );
};
```
Và đây là kết quả:

![[Pasted image 20220616112335.png]]

Như vậy đúng như những gì chúng ta hiểu, _**useEffect**_ sẽ được gọi mỗi khi components thay đổi, tuy nhiên ở đây thì đó không phải là thứ mà chúng ta mong muốn, hiện tại useEffect đang là một method giống như hàm **componentDidUpdate** vậy. Để cho giống với **componentDidUpdate** thực sự thì chúng ta cũng có thể điều khiển hàm _**useEffect**_ bằng câu lệnh điều kiện, nó chính là tham số thứ 2 của hàm _**useEffect().**_ Tham số thứ 2 của useEffect là một mảng, mảng này cho biết rõ chỉ gọi _**useEffect()**_ khi giá trị phần tử trong mảng thay đổi. Chẳng hạn:

```jsx
useEffect(() => {
  console.log('useEffect has been called!');
  setFullName({ name: 'TrungHC', familyName: 'HCT' });
}, [fullName.name]);
```

Như vậy hàm _**useEffect()**_ chỉ được gọi 2 lần: 1 lần khi render components, 1 lần khi set name thành "TrungHC".

Vậy nếu chúng ta muốn hàm useEffect() chỉ gọi 1 lần khi render components (tương đương với **componentDidMount**) thì như thế nào? Trong trường hợp này ta chỉ cần truyền tham số thứ 2 của _**useEffect()**_ là 1 hàm rỗng []


```jsx
useEffect(() => {
  console.log('useEffect has been called!');
  setFullName({ name: 'TrungHC', familyName: 'HCT' });
}, []);
```

Với hàm này thì _**useEffect()**_ sẽ giống hệt với **componentDidMount**

![[Pasted image 20220616112702.png]]

Và Lifecycle cuối cùng cũng hay sử dụng nữa là hàm componentWillUnmount, chúng ta cũng có thể sử dụng useEffect() định nghĩa hàm componentWillUnmount.

Như chúng ta đã biết thì **componentWillUnmount** sẽ chạy mỗi khi một component chuẩn bị remove khỏi tree DOM, cùng xét 1 ví dụ:

```jsx
() => {
  useEffect(() => {
    const clickWindow = () => console.log('1')
    window.addEventListener('click', clickWindow)

    // return 1 function, sẽ được gọi ngay trước khi componentWillUnmount
    return () => {
      window.removeEventListener('click', clicked)
    }
  }, [])

  return <div>F12 check log của trình duyệt!</div>
}
```

Thực tế thì _**useEffect**_ cho phép chúng ta return 1 function, function này sẽ thực thi trước khi mà component đó được Unmount.


Roadmap: [[Roadmap Image]]

Next: [[Context]]
Reference: https://viblo.asia/p/su-dung-useeffect-trong-reacthooks-1Je5EPbmlnL