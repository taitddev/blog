---
slug: reactjs-interview
title: React Interview
authors: [taitd]
tags: [reactjs]
---

### Table of Contents

| No. | Questions                        |
| --- | -------------------------------- |
|     | **Core React**                   |
| 1   | [React là gì ?](#1-react-là-gì-) |

## Core React

### 1. React là gì ?

React là một **thư viện JavaScript front-end mã nguồn mở** được sử dụng để xây dựng giao diện người dùng, đặc biệt là cho single-page applications. React được tạo ra bởi [Jordan Walke](https://github.com/jordwalke), một kỹ sư phần mềm làm việc cho Facebook. React lần đầu tiên được triển khai trên News Feed của Facebook vào năm 2011 và trên Instagram vào năm 2012.

### 2. Các tính năng chính của React là gì?

- Nó sử dụng **VirtualDOM** thay vì RealDOM vì các thao tác trên RealDOM rất tốn kém.
- Hỗ trợ **server-side rendering**.
- Tuân theo luồng dữ liệu một chiều hoặc ràng buộc dữ liệu.
- Sử dụng các UI components có thể **tái sử dụng**

### 3. JSX là gì ?

_JSX_ là một là một cú pháp mở rộng cho JavaScript (từ viết tắt của _JavaScript XML_). Chúng ta sử dụng JSX để biểu thị UI components

Trong ví dụ dưới đây, văn bản bên trong thẻ `<h1>` được trả về dưới dạng hàm JavaScript cho render function.

```jsx harmony
class App extends React.Component {
  render() {
    return (
      <div>
        <h1>{"Welcome to React world!"}</h1>
      </div>
    );
  }
}
```

### 4. Sự khác biệt giữa Element và Component?

_Element_ là một đối tượng đơn giản mô tả những gì bạn muốn xuất hiện trên màn hình dưới dạng các DOM node hoặc các component khác. _Elements_ có thể chứa các _Elements_ khác trong props của chúng. Khi một element được tạo, nó không bao giờ bị thay đổi (mutated).

Biểu diễn đối tượng của React Element sẽ như sau:

```javascript
const element = React.createElement("div", { id: "login-btn" }, "Login");
```

Hàm `React.createElement()` ở trên trả về một đối tượng:

```
{
  type: 'div',
  props: {
    children: 'Login',
    id: 'login-btn'
  }
}
```

Và cuối cùng nó render với DOM bằng cách sử dụng `ReactDOM.render()`:

```html
<div id="login-btn">Login</div>
```

Một **component** có thể được khai báo theo nhiều cách khác nhau. Nó có thể là một class có phương thức `render()` hoặc nó có thể được định nghĩa như một function. Trong cả hai trường hợp, nó lấy props làm input và trả về cây JSX làm output:

```javascript
const Button = ({ onLogin }) => (
  <div id={"login-btn"} onClick={onLogin}>
    Login
  </div>
);
```

Sau đó, JSX được chuyển sang `React.createElement()` function tree:

```javascript
const Button = ({ onLogin }) =>
  React.createElement("div", { id: "login-btn", onClick: onLogin }, "Login");
```

1. ### How to create components in React?

   There are two possible ways to create a component.

   1. **Function Components:** This is the simplest way to create a component. Those are pure JavaScript functions that accept props object as the first parameter and return React elements:

      ```jsx harmony
      function Greeting({ message }) {
        return <h1>{`Hello, ${message}`}</h1>;
      }
      ```

   2. **Class Components:** You can also use ES6 class to define a component. The above function component can be written as:

      ```jsx harmony
      class Greeting extends React.Component {
        render() {
          return <h1>{`Hello, ${this.props.message}`}</h1>;
        }
      }
      ```

   **[⬆ Back to Top](#table-of-contents)**
