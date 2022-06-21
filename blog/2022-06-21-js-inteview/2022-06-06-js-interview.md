---
slug: js-interview
title: Javascript interview
authors: [taitd]
tags: [javascript]
---

![Docusaurus Plushie](./banner.webp)

## 0. Table of Contents

- [0. Table of Contents](#0-table-of-contents)
- [1. Sự khác nhau giữa toán tử "==" và "===" trong JavaScript ?](#1-sự-khác-nhau-giữa-toán-tử--và--trong-javascript-)
- [2. JavaScript có phải là ngôn ngữ phân biệt chữ hoa chữ thường không (case-sensitive language)?](#2-javascript-có-phải-là-ngôn-ngữ-phân-biệt-chữ-hoa-chữ-thường-không-case-sensitive-language)
- [3. Có bao nhiêu cách để tạo 1 đối tượng trong JavaScript](#3-có-bao-nhiêu-cách-để-tạo-1-đối-tượng-trong-javascript)
  - [3.1. Object literal syntax](#31-object-literal-syntax)
  - [3.2. Object constructor](#32-object-constructor)
  - [3.3. Phương thức `Object.create()`](#33-phương-thức-objectcreate)
  - [3.4. ES6 Class](#34-es6-class)
- [4. Sự khác nhau giữa let và var trong JavaScript](#4-sự-khác-nhau-giữa-let-và-var-trong-javascript)
- [5. `const` là gì ?](#5-const-là-gì-)
- [6. Nêu các cách tạo một Array trong javascript ?](#6-nêu-các-cách-tạo-một-array-trong-javascript-)
- [7.Mục đích của từ khóa `this` trong JavaScript là gì?](#7mục-đích-của-từ-khóa-this-trong-javascript-là-gì)

## 1. Sự khác nhau giữa toán tử "==" và "===" trong JavaScript ?

Toán tử "==" và "===" được sử dụng để so sánh trong JavaScript. Toán tử "===" so sánh cân bằng nghiêm ngặt (strict equality), nó sẽ so sánh 2 giá trị và trả về true nếu chúng hoàn toàn bằng nhau (bằng cả giá trị và kiểu dữ liệu), trong khi toán tử “==” so sánh trừu tượng (abstract equality), nó cũng sẽ so sánh hai giá trị nhưng sẽ thực hiện ép kiểu nếu chúng không cùng kiểu dữ liệu.

Ví dụ:

```js
9 == "9" -> true
9 === "9" -> false
```

## 2. JavaScript có phải là ngôn ngữ phân biệt chữ hoa chữ thường không (case-sensitive language)?

JavaScript là ngôn ngữ có phân biệt chữ hoa chữ thường (case-sensitive language).
Ví dụ: các biến "myVar" và "MyVar" sẽ được coi là hai biến khác nhau.
Theo quy ước, các biến được đặt tên bằng camelCase, các lớp được đặt tên bằng PascalCase và các hằng được viết là SNAKE_CASE_ALL_CAPS.

## 3. Có bao nhiêu cách để tạo 1 đối tượng trong JavaScript

Có ít nhất bốn cách để tạo đối tượng trong JavaScript: sử dụng Object literal, hàm khởi tạo (object constructor), ES6 Class, hoặc với phương thức `Object.create()`.

### 3.1. Object literal syntax

Là kiểu cú pháp tạo object sử dụng cặp dấu ngoặc nhọn (curly braces) và bên trong đó là danh sách các thuộc tính (property) của object được biểu diễn dưới dạng key-value.

Đây là cách dễ nhất để tạo ra 1 object

Ví dụ:

```js
const obj = {
  foo: "bar",
  bar: 42,
  baz: true,
};
```

### 3.2. Object constructor

Cách đơn giản nhất để tạo một đối tượng rỗng là sử dụng hàm khởi tạo. Tuy nhiên hiện tại cách làm này không được khuyến khích.

```js
var object = new Object();
```

### 3.3. Phương thức `Object.create()`

`Object.create()` là một phương thức được giới thiệu trong ES5, nó được sử dụng để tạo một đối tượng mới bằng cách truyền prototype object làm tham số.

```js
var object = Object.create(null);
```

### 3.4. ES6 Class

ES6 giới thiệu tính năng Class để tạo các đối tượng.

```js
class Person {
  constructor(name) {
    this.name = name;
  }
}

var object = new Person("Sudheer");
```

**[⬆ Back to Top](#0-table-of-contents)**

## 4. Sự khác nhau giữa let và var trong JavaScript

| `var`                                                                                                                                                             | `let`                                                                                                 |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Nó đã có từ đầu của JavaScript                                                                                                                                    | Được giới thiệu ở ES6                                                                                 |
| Nó có phạm vi function (function scope)                                                                                                                           | Nó có phạm vi block (block scope), nếu ra khỏi scope được khai báo thì sẽ không thể sử dụng được nữa. |
| Có tính chất hoisting (nghĩa là dù khai báo ở đâu thì biến đều sẽ được đem lên đầu scope trước khi code được thực hiện), được khởi tạo với giá trị là `undefined` | Hoisting nhưng không có bất kỳ giá trị khởi tạo nào                                                   |

Lấy một ví dụ để thấy sự khác biệt

```js
function userDetails(username) {
  if (username) {
    console.log(salary); // undefined due to hoisting
    console.log(age); // ReferenceError: Cannot access 'age' before initialization
    let age = 30;
    var salary = 10000;
  }
  console.log(salary); //10000 (accessible to due function scope)
  console.log(age); //error: age is not defined(due to block scope)
}
userDetails("John");
```

**[⬆ Back to Top](#0-table-of-contents)**

## 5. `const` là gì ?

`const` là một từ khóa hoạt động rất giống với `let` trong JavaScript, nó cũng có scope là **block scope** và **hoisting**, tuy nhiên biến `const` nếu trường hợp kiểu của biến là **primitive** (bao gồm `string`, `number`, `boolean`, `null`, và `undefined`) thì chúng ta sẽ không thể tái khai báo hay cập nhật giá trị mới để thay thế cho giá trị trước đó của biến.

```js
const greeting = "say Hi";
greeting = "say Hello instead"; // error : Assignment to constant variable.

const greeting = "say Hi";
const greeting = "say Hello instead"; // error : Identifier 'greeting' has already been declared
```

Đối với trường hợp kiểu biến là **reference** (bao gồm `object`, `array`, và `function`) thì tuy không thể tái khai báo hay cập nhật giá trị của biến nhưng chúng ta vẫn có thể cập nhật giá trị cho thuộc tính của biến đó.

```js
const greeting = {
  message: "Hello",
  number: "five",
};

greeting.message = "say Hello instead";
console.log(greeting); // {message:"say Hello instead",number:"five"}
```

## 6. Nêu các cách tạo một Array trong javascript ?

Tạo một mảng trong JavaScript tương đối đơn giản. Lớp Array có một phương thức khởi tạo có thể được sử dụng để khởi tạo một mảng với một tập giá trị.

Ví dụ, đoạn code sau tạo một mảng có ba phần tử:

```js
const myArray = new Array(1, 2, 3);
```

Trong khi việc truyền nhiều param vào `new Array` sẽ hoạt động như mong đợi, nhưng khi chúng ta chỉ truyền một đối số duy nhất thì sẽ tạo ra một mảng trống có độ dài là đối số đó, ví dụ như sau:

```js
const myArray = new Array(5);
console.log(myArray);

// prints [<5 empty items>] which is just [undefined, undefined, undefined, undefined, undefined]
```

Nhưng vì mảng có độ dài thay đổi theo mặc định, nếu bạn chỉ muốn tạo một mảng trống và sau đó đẩy các phần tử vào nó, bạn có thể bỏ qua độ dài.

```js
const myArray = new Array();
myArray.push(1);
myArray.push(2);
myArray.push(3);
```

Trong cả hai trường hợp, mảng kết quả sẽ là kiểu **object** và sẽ có thuộc tính độ dài cho biết số phần tử trong mảng. Nhưng thông thường bạn sẽ làm điều đó bằng cách sử dụng array literal:

```js
const array = [1, 2, 3];
```

## 7.Mục đích của từ khóa `this` trong JavaScript là gì?

Từ khóa `this` trong JavaScript để đại diện cho một đối tượng.

Giá trị của điều này được xác định bởi cách một hàm được gọi (ràng buộc thời gian chạy). Nó không thể được đặt bằng cách gán trong khi thực thi và nó có thể khác nhau mỗi khi hàm được gọi. 3 phương pháp được sử dụng phổ biến nhất để kiểm soát liên kết này là Function.prototype.bind (), Function.prototype.call (), Function.prototype.apply () và ES2015 đã giới thiệu các hàm mũi tên không cung cấp liên kết này ( nó giữ nguyên giá trị này của ngữ cảnh từ vựng đi kèm).
