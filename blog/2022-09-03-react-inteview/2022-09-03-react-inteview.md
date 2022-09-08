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

### 1. ReactJS là gì?

ReactJS là **thư viện front-end JavaScript mã nguồn mở (open-source front-end JavaScript library)** được sử dụng để xây dựng giao diện người dùng (UI) đặc biệt là đối với single-page applications.

React được tạo ra bởi [Jordan Walke](https://github.com/jordwalke), một kỹ sư phần mềm làm việc cho Facebook. React lần đầu tiên được triển khai trên News Feed của Facebook vào năm 2011 và trên Instagram vào năm 2012.

### 4. Các trình duyệt web có đọc JSX một cách trực tiếp được không ?

Trình duyệt web không thể đọc JSX một cách trực tiếp. Điều này là do chúng được xây dựng để chỉ đọc các đối tượng JS thông thường và JSX không phải là một đối tượng JavaScript thông thường.

Để trình duyệt web có thể đọc được tệp JSX, tệp cần được chuyển đổi thành một đối tượng JavaScript thông thường. Để làm điều này, cần có sự hỗ trợ của WebPack hoặc Babel.

### 5. DOM ảo (Virtual DOM) là gì?

DOM là viết tắt của Document Object Model. DOM đại diện cho một tài liệu HTML có cấu trúc cây logic. Mỗi nhánh của cây kết thúc bằng một nút và mỗi nút chứa các đối tượng.

React giữ một bản “đại diện” nhưng nhẹ hơn của DOM “thực” trong bộ nhớ, gọi là DOM ảo (Virtual DOM). Khi trạng thái của một đối tượng (object) thay đổi, DOM ảo chỉ thay đổi đối tượng đó trong DOM thực, thay vì cập nhật tất cả các đối tượng.

### 6. Tại sao nên sử dụng React thay vì các framework khác, ví dụ như Angular?

| No.                                      | Questions                                                                                                                                                                                                                                                                                    |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dễ dàng tạo các ứng dụng động            | React giúp tạo các ứng dụng web động dễ dàng hơn vì ít code hơn mà lại cung cấp nhiều chức năng hơn, trong khi với các ứng dụng JavaScript, cách code thường có xu hướng trở nên phức tạp.                                                                                                   |
| Hiệu suất cải thiện                      | React sử dụng DOM ảo, giúp các ứng dụng web hoạt động nhanh hơn. Virtual DOM so sánh trạng thái trước đó của nó và chỉ cập nhật các thành phần có trạng thái thay đổi trong DOM thực thay vì cập nhật tất cả các thành phần, như các ứng dụng web thông thường.                              |
| Các thành phần có thể tái sử dụng        | Các components là nền tảng của bất kỳ ứng dụng React nào và một ứng dụng đơn lẻ thường bao gồm nhiều components. Các components này có logic và các điều khiển riêng và chúng có thể được tái sử dụng thông qua ứng dụng, do đó làm giảm đáng kể thời gian phát triển một ứng dụng.          |
| Luồng dữ liệu một chiều                  | React tuân theo luồng dữ liệu một chiều. Điều này có nghĩa là khi thiết kế một ứng dụng React, chúng ta thường lồng các thành phần con vào bên trong các thành phần mẹ. Và vì dữ liệu chảy theo một hướng, nên việc debug và biết vấn đề xảy ra ở đâu trong ứng dụng sẽ trở nên dễ dàng hơn. |
| Các công cụ chuyên dụng để debug dễ dàng | Facebook đã phát hành một tiện ích mở rộng Chrome mà chúng ta có thể sử dụng để debug các ứng dụng React. Điều này làm cho quá trình gỡ lỗi React cho các ứng dụng web nhanh hơn và dễ dàng hơn.                                                                                             |

### 7. Điểm khác biệt giữa tiêu chuẩn ES6 và ES5 ?

Đây là một vài trường hợp mà cú pháp ES6 khác so với cú pháp ES5:

- Components và Function
- exports vs export
- require vs import

### 6. Sự kiện (Event) trong React là gì?

Sự kiện là một hành động mà người dùng hoặc hệ thống có thể kích hoạt bằng cách chẳng hạn như nhấn phím, nhấp chuột, v.v.

Các sự kiện React được đặt tên bằng camelCase.

Với JSX, bạn chuyển một hàm làm trình xử lý sự kiện, thay vì một chuỗi trong HTML.

### 7. Làm thế nào để tạo một sự kiện (event) trong React?

### 10. Sự kiện tổng hợp (Synthetic event) trong React là gì?

Sự kiện tổng hợp (Synthetic event) kết hợp phản hồi của các sự kiện gốc của trình duyệt khác nhau thành một API, đảm bảo rằng các sự kiện nhất quán trên các trình duyệt khác nhau.
Ứng dụng phải nhất quán bất kể đang chạy trên trình duyệt nào. Ở đây, PreventDefault là một sự kiện tổng hợp.

### 12. Vì sao phải sử dụng key trong danh sách ?

Key rất quan trọng trong danh sách bởi vì:

Key là một định danh độc nhất và nó được sử dụng để xác định những mục nào đã thay đổi, được cập nhật hoặc bị xóa khỏi danh sách.
Key cũng giúp xác định thành phần nào cần được render lại thay vì lần nào cũng render lại tất cả các thành phần. Do đó, key giúp làm tăng hiệu suất, vì chỉ các thành phần được cập nhật mới được render lại.

### 1. Làm thế nào để áp dụng validation trên Props trong ReactJS ?

Khi ứng dụng đang chạy ở development mode, React sẽ tự động kiểm tra tất cả các props mà chúng ta thiết lập trên component để đảm bảo chúng phải đúng và đúng kiểu dữ liệu. Đối với trường hợp loại dữ liệu không chính xác, nó sẽ tạo ra các thông báo cảnh báo trong `console` dành cho development mode và nó bị tắt ở production mode để không bị ảnh hưởng hiệu suất. Các prop bắt buộc được xác định bằng `isRequired`.

Cách phổ biến nhất để áp dụng validation trên props là sử dụng thư viện `prop-types`

### 2. StrictMode trong React là gì ?

StrictMode của React là một component trợ giúp sẽ giúp bạn viết các React component tốt hơn, bạn có thể bọc một tập hợp các component bằng `<StrictMode />` và về cơ bản nó sẽ:

- Xác minh rằng các component bên trong đang tuân theo một số phương pháp được đề xuất và cảnh báo bạn nếu không có trong bảng điều khiển.
- Xác minh rằng các deprecated-method không được sử dụng và nếu chúng được sử dụng ở strict-mode, sẽ cảnh báo bạn trong bảng điều khiển.
- Giúp bạn ngăn ngừa một số tác dụng phụ bằng cách xác định các nguy cơ tiềm ẩn.

### 3. React Hooks là gì ?

Hooks là một bổ sung mới chỉ có từ React 16.8. Chúng cho phép bạn sử dụng state và các tính năng khác của React mà không cần viết một class.
Với Hooks, bạn có thể trích xuất logic state từ một component để nó có thể được kiểm tra độc lập và sử dụng lại.
Hooks cho phép bạn sử dụng lại logic state mà không thay đổi cấu trúc phân cấp các component của bạn. Điều này giúp bạn dễ dàng chia sẻ Hooks giữa nhiều components hoặc với cộng đồng.

### 4. useState() trong React là gì ?

`useState` là một trong những React hook tích hợp sẵn. `useState` trả về một bộ giá trị trong đó tham số đầu tiên là `state` hiện tại và `setState` là phương thức cho phép chúng ta cập nhật lại giá trị của `state`.

### 5. Children prop là gì ?

Children là prop (this.prop.children) cho phép bạn chuyển các components dưới dạng dữ liệu đến các components khác.

### 6. Tại sao ReactJS sử dụng className thay vì thuộc tính class?

`class` là một từ khóa trong javascript và tuy nhiên react sử dụng JSX - là một phần mở rộng của javascript. Và JSX sử dụng `className` thay vì `class`.

### 7. Tại sao nên dùng fragment thay vì div ?

Dưới đây là lý do tại sao các fragment được đề xuất:

- Fragment nhanh hơn một chút và sử dụng ít bộ nhớ hơn mà không cần tạo thêm một nút DOM. Điều này chỉ có lợi thực sự đối với những tree rất lớn và sâu.
- Một số cơ chế CSS như Flexbox và CSS Grid có mối quan hệ cha-con đặc biệt, và việc thêm các div ở giữa khiến khó giữ được bố cục mong muốn.
- Trình kiểm tra DOM, debug ít lộn xộn hơn

### 8. Có nên cập nhật state trực tiếp không, tại sao?

Nếu bạn cố gắng cập nhật state trực tiếp thì nó sẽ không re-render Component.
Thay vào đó hãy sử dụng phương thức `setState()`. Nó lên lịch cập nhật cho đối tượng state của một Component. Khi state thay đổi, Component phản hồi bằng cách render
