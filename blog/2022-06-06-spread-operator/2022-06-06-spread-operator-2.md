---
slug: spread-operator
title: 5 cách sử dụng Spread Operator trong javascript
authors: [taitd]
tags: [javascript, spread-operator]
---

![Docusaurus Plushie](./banner.webp)

<!--truncate-->

## 1. Spread Operator là gì?

"Spread Operator cho phép chuyển đổi một chuỗi thành nhiều argument (trong trường hợp gọi với hàm) hoặc thành nhiều phần tử (cho array). Thêm vào nữa nó cũng cho phép làm nhiệm vụ destructure. Operator này có syntax là 3 dấu chấm ..., khá là dị hợm và khó hiểu nhỉ, nhưng nói thế chứ cái splat bên Ruby cũng chẳng mấy dễ hiểu hơn cho người mới nhập môn."

Nếu thật sự bạn muốn hiểu kỹ hơn, có lẽ bạn nên dành thời gian cho [bài viết này](spread-operator-1). Bây giờ chúng ta có thể đi vào nội dung chính của bài viết này, các bạn có thể đọc chậm để hiểu hơn.

## 2. Copying array

Có lẽ đây là một trong những cách sử dụng phổ biến nhất của Spread Operator javascript.

```js
let arr = [1, 2, 3, 4];
let copy = [...arr];
// copy is [ 1, 2, 3, 4 ]
```

Lưu ý rằng copy chưa phải là một phương pháp "Deep copying".
Để hiểu thêm và Deep copying, bạn có thể đọc [bài viết này](shallow-copying-vs-deep-copying).

## 3. Concatenate arrays

Dựa trên ví dụ trước, bạn có thể tạo ra một new array thông qua nhiều array cho trước.

```js
let arr1 = [1, 2, 3, 4];
let arr2 = [5, 6, 7, 8];
let concat = [...arr1, ...arr2];
// concat is [ 1, 2, 3, 4, 5, 6, 7, 8 ]
```

## 4. Copy object

Cũng giống như ví dụ về array ở phần 1 thì object cũng tương tự

```js
let obj = { a: 1, b: 2, c: 3 };
let copy = { ...obj };
// copy is {a: 1, b: 2, c: 3}
```

Và sai lầm sẽ trả giá nếu bạn quên đi "three dot..."

```js
let obj = { a: 1, b: 2, c: 3 };
let copy = { obj };
// copy is { {a: 1, b: 2, c: 3} }
```

## 5. Merge object

Giờ đây khi Merge object chúng ta sẽ không cần đến sử dụng cách cũ `concat()`. Mà bạn có thể thực hiện nhanh chóng hơn với spread trong javascript.

```js
let obj1 = { a: 1, b: 2, c: 3 };
let obj2 = { d: 4, e: 5, f: 6 };

let merge = { ...obj1, ...obj2 };
// merge is {a: 1, b: 2, c: 3, d: 4, e: 5, f: 6}
```

## 6. Truyền đối số dưới dạng mảng

Đây là lúc spread operator bắt đầu thể hiện tính linh hoạt của nó. Trong ví dụ này, chúng ta đang truyền ba đối số vào một hàm. Spread operator được sử dụng với một mảng có ba phần tử

```js
function dev(x, y, z) {
  return x + y + z;
}

var args = [0, 1, 2];

dev(...args); // call function
```

Cả ba phần tử có thể được truyền vào dưới dạng đối số cho hàm.

## 7. Bonus - An Error

Mặc dù thực tế rằng spread operator trải đều hoạt động trên cả array và object, bạn không thể trộn và khớp các loại dữ liệu này với nhau. Như ví dụ dưới đây.

```js
let obj = { a: 1, b: 2, c: 3 };
let copy = [...obj]; // this won't work!
```
