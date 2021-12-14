---
slug: everything-you-need-in-react-js
title: React.js from scratch - Phần 1
authors: [taitd]
tags: [react, javascript, webdev, 100daysofcode]
---

Trong series này, tôi sẽ chia sẻ tất cả những phần mà tôi nghĩ là quan trọng đối với bạn nếu bạn muốn học React hoặc nâng cao kiến ​​thức hiện tại của mình.

Let's get started 🚀

<!--truncate-->

## 1. React và JSX

React là một thư viện mã nguồn mở do Facebook tạo ra. Đây là một công cụ tuyệt vời để hiển thị giao diện Người dùng (UI) của các ứng dụng web hiện đại.

React sử dụng một phần mở rộng cú pháp của JavaScript được gọi là JSX cho phép bạn viết HTML trực tiếp trong JavaScript. Điều này có một số lợi ích, nó cho phép bạn sử dụng toàn bộ sức mạnh lập trình của JavaScript trong HTML và giúp giữ cho code của bạn có thể đọc được. Về phần lớn, JSX tương tự như HTML mà bạn đã học, tuy nhiên có một số điểm khác biệt chính sẽ được đề cập trong series này.

Ví dụ: vì JSX là một phần mở rộng cú pháp của JavaScript, bạn thực sự có thể viết JavaScript trực tiếp trong JSX. Để thực hiện việc này, bạn chỉ cần bao đoạn code mà bạn muốn được coi là JavaScript trong dấu ngoặc nhọn: `{'this is treated as JavaScript code'}`. Hãy ghi nhớ điều này, vì nó được sử dụng trong một số thử thách trong tương lai.

### JSX

```js
const JSX = <h1>Hello JSX</h1>;
const JS = (
  <div>
    <h1>Hello</h1>
    <p>Hello from p tag</p>
  </div>
);
```

### Comment

```js
const JSX = (
  <div>
    <h1>This is a block of JSX</h1>
    <p>Here's a subtitle</p>
    {/* this is a comment */}
  </div>
);
```

Render các phần tử HTML cho DOM Cho đến nay, bạn đã biết rằng JSX là một công cụ thuận tiện để viết HTML trong JavaScript. Với React, chúng ta có thể render JSX trực tiếp tới HTML DOM bằng cách sử dụng API render của React được gọi là ReactDOM. ReactDOM cung cấp một phương thức đơn giản để render các React elements tới DOM trông giống như sau: `ReactDOM.render (componentToRender, targetNode)`, trong đó đối số đầu tiên là React element hoặc component mà bạn muốn render và đối số thứ hai là DOM node mà bạn muốn render.

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

```js
const List = (props) => {
  {
    /* change code below this line */
  }
  return <p>{props.tasks.join(", ")}</p>;
  {
    /* change code above this line */
  }
};

class ToDo extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>To Do Lists</h1>
        <h2>Today</h2>
        {/* change code below this line */}
        <List tasks={["1", "1", "1"]} />
        <h2>Tomorrow</h2>
        <List tasks={["1", "1", "1"]} />
        {/* change code above this line */}
      </div>
    );
  }
}
```

Default props

```js
const ShoppingCart = (props) => {
  return (
    <div>
      <h1>Shopping Cart Component</h1>
      <p>{props.items}</p>
    </div>
  );
};
// change code below this line
ShoppingCart.defaultProps = {
  items: 0,
};
```

Ghi đè Default props

```js
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>;
};
Items.defaultProps = {
  quantity: 0,
};

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <Items quantity={10} />;
  }
}
```

Sử dụng PropTypes để xác định đạo cụ bạn mong đợi

Sử dụng PropTypes để xác định Props.

Import

```js
import PropTypes from "prop-types";
```

Code :

```js
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>;
};

Items.propTypes = {
  quantity: PropTypes.number.isRequired,
};

Items.defaultProps = {
  quantity: 0,
};

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <Items />;
  }
}
```

Truy cập Props bằng this.props

ES6 class component sử dụng một quy ước hơi khác để truy cập vào props.

Bất cứ khi nào bạn tham chiếu đến một class component trong chính nó, bạn sử dụng từ khóa `this`. Để truy cập vào props trong một class component, bạn đặt trước mã mà bạn sử dụng để truy cập nó với `this`. Ví dụ: nếu một ES6 class component có một prop là `data`, bạn viết `{this.props.data}` trong JSX.

```js
class ReturnTempPassword extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <p>
          Your temporary password is: <strong>{this.props.tempPassword}</strong>
        </p>
      </div>
    );
  }
}

class ResetPassword extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h2>Reset Password</h2>
        <h3>We've generated a new temporary password for you.</h3>
        <h3>Please reset this password from your account settings ASAP.</h3>
        <ReturnTempPassword tempPassword="xxxxxxxx" />
      </div>
    );
  }
}
```

Nhìn lại việc sử dụng props với Stateless Functional Components.

Một Stateless Functional Components là bất kỳ hàm nào bạn viết chấp nhận các props và trả về JSX. Mặt khác, một stateless component là một class kế thừa từ React.Component, nhưng không sử dụng trạng thái bên trong (được đề cập trong phần sau). Một stateful component là một class component duy trì trạng thái bên trong của chính nó. Bạn có thể thấy các stateful components được gọi đơn giản là các components hoặc các React components.

Một mô hình phổ biến là cố gắng giảm thiểu trạng thái và tạo các stateless functional components bất cứ khi nào có thể. Điều này giúp chúng ta quản lý các state ở một khu vực cụ thể trong ứng dụng. Đổi lại, điều này cải thiện sự phát triển và bảo trì ứng dụng của bạn bằng cách giúp bạn dễ dàng theo dõi sự thay đổi của các state.

```js
class CampSite extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <Camper />
      </div>
    );
  }
}
class Camper extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <p>{this.props.name}</p>
      </div>
    );
  }
}
Camper.defaultProps = {
  name: "CamperBot",
};
Camper.propTypes = {
  name: PropTypes.string.isRequired,
};
```

Tạo một Stateful Component.

Một trong những kiến thức quan trọng nhất trong React là state. State bao gồm bất kỳ dữ liệu nào mà ứng dụng của bạn cần biết, có thể thay đổi theo thời gian. Bạn muốn ứng dụng của mình phản hồi với các thay đổi của state và render lại giao diện người dùng khi state thay đổi. React cung cấp một giải pháp tốt để quản lý các state.

Bạn có thể tạo state trong React component bằng cách khai báo một thuộc tính `state` trong phương thức khởi tạo của component class. Điều này khởi tạo component với state khi nó được tạo. Thuộc tính `state` phải được đặt thành một JavaScript `object`. Khai báo như sau:

```js
this.state = {
  // describe your state here
};
```

Render state trong UI.

Khi bạn xác định initial state (trạng thái ban đầu) của một component, bạn có thể hiển thị bất kỳ phần nào của nó trong UI. Nếu một component là trạng thái, nó sẽ luôn có quyền truy cập vào dữ liệu ở `state` trong phương thức `render()` của nó. Bạn có thể truy cập dữ liệu bằng `this.state`.

Nếu bạn muốn truy cập một giá trị trạng thái trong giá trị trả về của phương thức render, bạn phải đặt giá trị đó trong dấu ngoặc nhọn.

`State` là một trong những tính năng mạnh mẽ nhất của React component. Nó cho phép bạn theo dõi dữ liệu quan trọng trong ứng dụng của mình và hiển thị UI để phản hồi lại những thay đổi trong dữ liệu này. Nếu dữ liệu của bạn thay đổi, UI của bạn sẽ thay đổi. React sử dụng cái được gọi là DOM ảo (Virtal DOM), để theo dõi những thay đổi đằng sau hậu trường. Khi state được cập nhật, nó sẽ kích hoạt re-render các component sử dụng dữ liệu đó - bao gồm cả các thành phần con đã nhận data như là 1 props. React cập nhật DOM thực, nhưng chỉ khi cần thiết. Điều này có nghĩa là bạn không phải lo lắng về việc thay đổi DOM. Bạn chỉ cần khai báo UI sẽ trông như thế nào.

Lưu ý rằng nếu bạn tạo ra một stateful component, không có component nào khác biết `state` của nó. `state` của nó được đóng gói hoàn toàn hoặc cục bộ cho component đó, trừ khi bạn truyền `state` cho một component con dưới dạng `props`. Khái niệm `state` được đóng gói này rất quan trọng vì nó cho phép bạn viết một số logic nhất định, sau đó có logic đó được chứa và cô lập ở một nơi trong code của bạn.

```js
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: "freeCodeCamp",
    };
  }
  render() {
    return (
      <div>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
}
```

Render state trong UI theo cách khác.

Có một cách khác để truy cập `state` của một component. Trong phương thức `render()`, trước câu lệnh `return`, bạn có thể viết JavaScript trực tiếp. Ví dụ: bạn có thể khai báo các hàm, truy cập dữ liệu từ `state` hoặc `props`, thực hiện tính toán trên dữ liệu này, v.v. Sau đó, bạn có thể gán bất kỳ dữ liệu nào cho các biến mà bạn có quyền truy cập trong câu lệnh `return`.

```js
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: "freeCodeCamp",
    };
  }
  render() {
    const name = this.state.name;
    return (
      <div>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
}
```

## Tài liêu tham khảo

<https://dev.to/dev117uday/everything-you-need-in-react-js-1akj>
