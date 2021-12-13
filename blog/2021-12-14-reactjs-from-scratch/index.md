---
slug: everything-you-need-in-react-js
title: React.js from scratch - Phần 1
authors: [taitd]
tags: [react, hello, docusaurus]
---

Render các phần tử HTML cho DOM Cho đến nay, bạn đã biết rằng JSX là một công cụ thuận tiện để viết HTML trong JavaScript. Với React, chúng ta có thể render JSX trực tiếp tới HTML DOM bằng cách sử dụng API render của React được gọi là ReactDOM. ReactDOM cung cấp một phương thức đơn giản để render các React elements tới DOM trông giống như sau: `ReactDOM.render (componentToRender, targetNode)`, trong đó đối số đầu tiên là React element hoặc component mà bạn muốn render và đối số thứ hai là DOM node mà bạn muốn render. N

Như bạn mong đợi, `ReactDOM.render()` phải được gọi sau khai báo phần tử JSX, giống như cách bạn phải khai báo các biến trước khi sử dụng chúng.

```js
const JSX = (
  <div id="challenge-node">
    <h1>Hello World</h1>
    <p>Lets render this to the DOM</p>
  </div>
);
// change code below this line
ReactDOM.render(JSX, document.getElementById("challenge-node"));
```

## Xác định một lớp HTML trong JSX

Bây giờ bạn đã cảm thấy thoải mái khi viết JSX, bạn có thể tự hỏi nó khác với HTML như thế nào.

Cho đến nay, có vẻ như HTML và JSX hoàn toàn giống nhau.

Một điểm khác biệt chính trong JSX là bạn không còn có thể sử dụng `class` để định nghĩa các lớp HTML. Điều này là do `class` là một từ dành riêng trong JavaScript. Thay vào đó, JSX sử dụng className.

Trên thực tế, quy ước đặt tên cho tất cả các thuộc tính HTML và tham chiếu sự kiện trong JSX trở thành camelCase. Ví dụ: sự kiện click chuột trong JSX là `onClick`, thay vì `onclick`. Tương tự, `onchange` trở thành `onChange`. Mặc dù đây là một sự khác biệt nhỏ, nhưng hãy ghi nhớ nó.

```js
const JSX = (
  <div className="myDiv">
    <h1>Add a class to this div</h1>
  </div>
);
```

## Tạo một Stateless Functional Component

Component là thành phần cốt lõi của React. Mọi thứ trong React đều là một Component và ở đây bạn sẽ học cách tạo một Component.

Có hai cách để tạo một React Component. Cách đầu tiên là sử dụng JavaScript function. Định nghĩa một component theo cách này sẽ tạo ra một **_stateless functional component_**. Khái niệm state trong một ứng dụng sẽ được đề cập trong phần sau. Bây giờ, hãy nghĩ về stateless component như một thành phần có thể nhận data và render data, nhưng không quản lý hoặc theo dõi các thay đổi đối với data đó.

Để tạo một functional component, bạn chỉ cần viết một hàm JavaScript trả về JSX hoặc `null`. Một điều quan trọng cần lưu ý là React yêu cầu tên hàm của bạn phải bắt đầu bằng một chữ cái viết hoa.

```js
const MyComponent = function () {
  return <div>Hello</div>;
};
```

## Tạo một React Component

Cách khác để xác định một React Component là với cú pháp ES6 `class`. Trong ví dụ sau, lớp `Kitten` kế thừa từ `React.Component`:

```js
const ChildComponent = () => {
  return (
    <div>
      <p>I am the child</p>
    </div>
  );
};

class ParentComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>I am the parent</h1>
        <ChildComponent />
      </div>
    );
  }
}
```

Render các component lồng nhau

```js
const TypesOfFruit = () => {
  return (
    <div>
      <h2>Fruits:</h2>
      <ul>
        <li>Apples</li>
        <li>Blueberries</li>
        <li>Strawberries</li>
        <li>Bananas</li>
      </ul>
    </div>
  );
};

const Fruits = () => {
  return (
    <div>
      <TypesOfFruit />
    </div>
  );
};

class TypesOfFood extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        <Fruits />
      </div>
    );
  }
}
```

Một ví dụ khác:

```js
class Fruits extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h2>Fruits:</h2>
        <NonCitrus />
        <Citrus />
      </div>
    );
  }
}

class TypesOfFood extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        <Fruits />
        <Vegetables />
      </div>
    );
  }
}
```

## Truyền props cho một Stateless Functional Component

Trong React, bạn có thể truyền props, hoặc thuộc tính cho các component con. Giả sử bạn có một component `App` render một component con có tên là `Welcome`, đây là một stateless functional component.

```js
const CurrentDate = (props) => {
  return (
    <div>
      <p>The current date is: {props.date}</p>
    </div>
  );
};

class Calendar extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>What date is it?</h3>
        <CurrentDate date={Date()} />
      </div>
    );
  }
}
```

Truyền props là một mảng
