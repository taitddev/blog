---
slug: destructuring-in-js
title: Destructuring Javascript là gì?
authors: [taitd]
tags: [javascript, destructuring]
---

![Docusaurus Plushie](./banner.webp)

Destructuring Javascript là gì? ES6 đã giới thiệu cho chúng ta một trong những tính năng trong ngôn ngữ JavaScript được chờ đợi nhất đó chính là: destructuring trong es6. Destructuring khái niệm là gì? Hiểu và sử dụng nó như thế nào? Thì trong bài viết này chúng ta cùng nhau xem xét cụ thể về cú pháp, và vì sao nó lại được các phà phát triển đánh giá cao.

<!--truncate-->

## 1. Destructuring Javascript là gì?

Destructuring là một cú pháp cho phép bạn gán các thuộc tính của một Object hoặc một Array. Điều này có thể làm giảm đáng kể các dòng mã cần thiết để thao tác dữ liệu trong các cấu trúc này. Có hai loại Destructuring: Destructuring Objects và Destructuring Arrays.

Rồi ok, chúng ta sẽ xem xét đoạn code sau, nếu bạn cảm thấy bối rối thì xong phim rồi đôi mắt biếc ơi =]]. Không sao đâu, tôi và nhiều developer javascript (devjs) cũng như bạn mà thôi, cũng đã cảm thấy bối rồi khi tính năng này được phát hành.

Ví dụ 1:

```js
var a, b;
[a, b] = [1, 2];
console.log(a, b); //1 2

//or

const [a, b] = [1, 2];
console.log(a, b); //1 2
```

Nếu như bạn cần một lời giải thích thì tôi sẽ sẵn lòng thôi. Trong dòng 1, chúng ta có 2 biến a và b trong array. Trong dòng tiếp theo, chúng ta thiết lập chúng và set chúng bằng với một arrays tương ứng. Trong các dòng tiếp theo, chúng tôi in các giá trị của a & b và chúng tôi nhận được 1 và 1 tương ứng là các phần tử trong mảng phía bên phải. Đó chính là Destructuring javascript. Nó thật là vi diệu phải không, chưa đâu đó chỉ là một ví dụ đơn giản để giúp devjs hiểu trước tạm thời thôi. Tiếp tục ta xem xét thêm một ví dụ nữa

Ví dụ 2:

```js
const [a, b, c] = [1, 2, 3, 4, 5];
console.log(a, b, c); // 1, 2, 3

const [a, b, ...c] = [1, 2, 3, 4, 5];
console.log(a, b, c); //1, 2, [3, 4, 5]
```

Giờ bạn thấy sao, hết bàng hoàng và bối rối ngoại trừ ...c đúng không? Ở trường hợp thứ nhất chúng ta cũng hiểu như ví dụ 1, các giá trị a, b, c tương ứng với những giá trị của array bên phía bên phải. Nhưng đối với ...c thì nó sẽ tương ứng với những giá trị còn lại tương ứng với kiểu của root (arrays). Hay trong ngôn ngữ javascript thì ...c chính là rest params hay rest es6.

Ngoài ra destructure params object cũng tương tư như arrays, chúng ta đi xem một ví dụ về việc sử dụng destructure trong object.

Ví dụ 3:

```js
const { a, b } = { a: 1, b: 2 };
console.log(a, b); // 1, 2

// add c

const { a, b, c } = { a: 1, b: 2, c: () => 3 };
console.log(a, b, c); // 1, 2, () => 3

// add ...c

const { a, b, ...c } = { a: 1, b: 2, c: () => 3, d: 4 };
console.log(a, b, c); // 1, 2, {d: 4, c: f} với f = () => 3
```

Việc sử dụng destructuring trong object cùng giống như array trong ví dụ đâu tiên, và sử dụng rest operator cũng có thể được dùng cùng với như ví dụ 1.

Nhìn vào cách sử dụng destructuring qua hai ví dụ trên thì nhiều bạn vẫn chưa cảm được lợi ích của việc sử destructuring trong cách viết code đúng không? Ủa tại sao lại dùng, nó quá lạ lẫm thà dùng cách cũ cũng được. Khoan, đừng rời bài viết này ngay khi bạn đã đến đây, chúng ta đã nói ngay lúc đầu, vì sao nó mạnh mẽ và đừng buông và bỏ nó. Tiếp theo, chúng ta sẽ xem nó giải quyết được những gì, và vì sao các nhà phát triền nổi tiêng đều có lý lẽ của riêng họ.

## 2. Destructuring là gì? Vì sao phải dùng?

## 2.1. Variable assignment

Hầu hết chúng ta đã làm việc với rest api khi return về một array hay object thì khi sử dụng destructuring lúc này thì quả là hiệu quả;

Ví dụ 4:

Chẳng hạn như chúng ta nhận được một response từ rest api. Chúng ta có thể gán ngay các biến và sử dụng.

```js
const res = [1, 2, 3, 4]; //res.response();
const [a, b, c] = res;
console.log(a, b, c); //1 2 3
```

### 2.2. Swapping

Nói đến Swapping thì cả một bầu trời hiện về, những thuật toán của các nhà phát triển lớn hầu như có nó. Vì vậy destructuring cũng có thể áp dụng trong hoàn cảnh này.

Ví dụ 5:

```js
var a = 1;
var b = 2;
var temp;
temp = a;
a = b;
b = temp;

console.log(a, b); //2, 1
```

Trước đó là a = 1, b = 2 sau khi gán tạm thì nó sẽ hoán đổi giá trị, giờ ta thử sử dụng destructuring trong Swapping:

```js
var a = 1;
var b = 2;
[a, b] = [b, a];
console.log(a, b); //2, 1
```

Wow, cũng hay đấy nhỉ =]]

### 2.3. Ignoring values

Ví dụ 6:

```js
const res = () => [1, 2, 3];
const [a, , b] = res();
console.log(a, b); //1,3
```

Chúng ta có thể bỏ qua giá trị 2 nhanh nhất có thể khi sử dụng destructuring.

### 2.4. Assignment to new variables

Gán giá trị cho một biến mới, chúng ta xem tiếp ví dụ tiếp
Ví dụ 7:

```js
const res = { blog: "anonystick.com", type: "javascript" };
const { blog: nameBlog, type: newType } = res;
console.log(nameBlog, newType); //anonystick.com, javascript
```

Giờ đây nameBlog, và newType là biến mới và cũng được set giá trị tương ứng.

### 2.5. Nested object and array destructuring

Ở trường hợp này thi tôi khuyên các bạn nên sử dụng vì trường hợp này rất nhiều trong mã code của chúng ta nhất là các bạn làm dưới nodejs or backend.
Ví dụ 8:

```js
const blogs = {
  anonystick: [
    {
      pageFacebook: "Tip javascript Viet Nam",
      likes: 4789,
      daily: 1323,
    },
  ],
};

const {
  anonystick: [{ pageFacebook: namePage, likes: numLikes, daily: numDaily }],
} = blogs;

console.log(namePage, numLikes, numDaily); //Tip javascript Viet Nam, 4789, 1323
```

Như chúng ta có thể thấy, dữ liệu đó là một đối tượng có một thuộc tính được gọi là vị trí lần lượt chứa một mảng có các phần tử là các đối tượng. Với việc sử dụng destructuring, chúng ta phải lấy các giá trị của tất cả các thuộc tính có trong đối tượng bên trong mảng cùng vị trí.

## 3. Destructuring assignment trong es6

Một ví dụ cuối cùng của bài viết hôm nay về "Destructuring javascript". Và đây là một ví dụ có thể sẽ gần gũi hơn những ví dụ trên, và nó rất phổ biến bao gồm cả tôi

Ví dụ 9

```js
const obj = await Model.getObject({ name: "anonystick", blog: "javascript" });

//model.js

modules.export = {
  getObject: async ({ name, blog }) => {
    console.log(name, blog);
  },
};
```

Trên ví dụ đó có sử dụng async/await trong es6. Các bạn đã sử dụng trường hợp lần nào chưa? Và nó hay hơn cách cũ không? Sẽ có một bải viết nói về các truyền tham số chuẩn như thế nào khi dùng Destructuring và cách cũ. Nhằm giúp các bạn so sánh được lợi ích của việc dùng Destructuring trong trường hợp này.

## 4. Kết Luận

Như vậy, trong bài viết này các bạn đã giúp tôi ôn luyện lại một phần nào về destructuring javascript. Thật sự mà nói, thì việc dùng nó có liên quan đến việc sử dụng nhiều trong dự án của mỗi chúng ta mà thôi. Các bạn cũng nên tìm hiểu những tính năng mới sắp ra mắt của 2020 đó là Es11, hiện đang ở stage 04 rồi đây. Nếu nó kích thích bạn tìm hiểu thì hãy vui vẻ tham quan bài viết này mà chúng tôi đã giới thiệu đến các bạn tuần trước và nó đạt tới gần 700 lượt share trong social đấy. Và nó đây: "New feature javascript - Cập nhật tính năng mới của javascript"

Thanks!! Nếu bạn cảm thấy hay, hãy giúp chúng tôi share nó nhé. Chụt chụt

Ngoài ra các bạn cũng nên tham khảo các bài viết dưới đây:

<https://www.carlrippon.com/clean-up-your-code-with-destructing/>

<https://www.freecodecamp.org/news/how-to-use-destructuring-in-javascript-to-write-cleaner-more-powerful-code-9d1b38794050/>
