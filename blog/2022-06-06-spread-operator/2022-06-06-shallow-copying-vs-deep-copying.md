---
slug: shallow-copying-vs-deep-copying
title: Sự khác nhau giữa Shallow copying và Deep copying trong object javascript.
authors: [taitd]
tags: [javascript, spread-operator]
---

![Docusaurus Plushie](./banner.webp)

Shallow copying vs Deep copying trong Object javascript. Nghe tiêu đề thôi cũng gây war rồi. Nhưng mới đây, trong vụ phỏng vấn dev js thì có hỏi câu hỏi copy object javascript này, dù kết quả có tiến bộ hơn những đợt phỏng vấn cách đây vài tháng nhưng đa số các bạn hiểu về câu hỏi này nhưng vẫn trả lời chưa rõ hoặc không giải thích được.

Tôi đoán nguyên nhân là có thể không hiểu sâu vấn đề đó, hoặc có xử lý qua rồi nhưng không save lại để hiểu code đó chạy làm gì? Vậy cho nên, dù chủ đề copy object trong javascript cũng được giải thích nhiều trên các blog lập trình, nhưng chúng ta cũng nên nói qua và rõ hơn một chút về vấn đề này.

Đầu tiên chúng ta nói đến có bao nhiêu cách copy một object trong javascript hay object assign array, phần này chúng ta chưa nói đến khái niệm shallow copy và deep copy ở đây. Thực tế, chúng ta thấy copy object diễn ra hằng ngày, diến ra với mỗi một project, với một lập trình viên chứ không riêng gì một deverloper javascript (devjs).

Nó thật sự đơn giản với những bạn nào đã từng trải qua và xử lý nó. Nhưng với những bạn chưa biết hoặc chưa từng nghe đến khái niệm này thì quả là một vấn đề khó và mông lung. Cho nên bài viết này chúng ta nên chia sẻ một cách dễ hiểu và tường minh hơn, để cho những bạn thuộc trường hợp trên hiểu rõ hơn. Thôi, vào chủ để chính cho nhanh. OK.

<!--truncate-->

## 1. Các cách copy object trong javascript

Đương nhiên là nhiều cách chứ không riêng gì 3 cách chuẩn bị nói dưới đây, nhưng đây là những cách phổ biến và được sử dụng rộng rãi nhất nên chúng ta mới đề cập ở đây.

### 1.1. `Object.assign()` method

Sử dụng method Object.assign() copy object :

```js
const obj = { a: 1, b: 2, c: 3 };

const clone = Object.assign({}, obj);

console.log(clone); // {a:1,b:2,c:3};
```

### 1.2. Spread Operator Es6

```js
const obj = { a: 1, b: 2, c: 3 };

const clone = { ...obj };

console.log(clone); // {a:1,b:2,c:3};
```

### 1.3. Sử dụng JSON.parse() và JSON.stringify()

```js
const student = {
  name: "taitd",
  age: 18,

  mark: {
    math: 10,
    english: 7,
  },
};

const clonedStudent = JSON.parse(JSON.stringify(student));

console.log(clonedStudent);
```

Notes: Trong 3 cách copy object trên thì 2 trong số đó là thuộc shallow copy, đó là `Object.assign()`, và Spread Operator. Còn deep Copy chính là cách thứ 3 - Sử dụng `JSON.parse()` và `JSON.stringify()`.

Và tại sao lại nói như vậy chúng ta tiếp tục đi tìm hiểu sự khác nhau giữa shallow copy và deep copy trong javascript.

## 2. Shallow copying và Deep copying

Shallow copying nhiệm vụ của nó chỉ copy những giá trị nông (theo như trả lời phỏng vấn) nghĩa là nó chỉ sao chép các giá trị đối tượng bình thường nhưng các giá trị lồng nhau vẫn sử dụng reference đến một đối tượng ban đầu.

Notes: reference type trong javascript tổng thể có 3 loại: Array, function và object. Chúng ta cùng nhau xem lại ví dụ 1.3 bên trên để hiểu rõ hơn về shallow copy object js khi sử dụng spread operator

Ví dụ:

```js
const student = {
  name: "taitd",
  age: 18,

  mark: {
    math: 10,
    english: 7,
  },
};

const shallowClone = { ...student };

student.mark.math = 9; // chúng ta thay đổi giá trị math của object gốc

console.log(student); // kết quả cho chúng ta thấy mark.math được update = 9

console.log(shallowClone); // nhưng object mà chúng ta clone ra cũng bị thay đổi theo shallowClone.mark.math = 9
```

Qua ví dụ chúng ta thấy: Chúng ta thay đổi giá trị math của object gốc student = 9, nhưng object mà chúng ta clone ra cũng bị thay đổi theo `mark:{math: 10,english: 7}`, chuyện quái gì vậy? Đơn giản đó là nó vẫn giữ những giá trị reference của object gốc (object mark của shallowClone vẫn đang trỏ cùng vùng nhớ với object gốc).

Giờ chúng ta qua deep copy. Nếu bạn hiểu shallow copy rồi thì deep copy đơn giản là cũng giống như clone shallow nhưng các giá trị reference trong object gốc không bị thay đổi trong object clone.

Ví dụ về deep clone sử dụng sử dụng JSON.parse() và JSON.stringify()

```js
const student = {
  name: "taitd",
  age: 18,

  mark: {
    math: 10,
    english: 7,
  },
};

const deepClone = JSON.parse(JSON.stringify(student));
student.mark.math = 9;
console.log(deepClone);
```

Ta thấy, khi update `mark.math = 9` thì object gốc đã thay đổi nhưng object clone thì không bởi vì nó không phải là reference type của object gốc nữa rồi.

OK, Xong việc giải thích trên bài này giúp các bạn hình dung ra sự khác biệt giữa shallow và deep copy nhưng bạn hãy copy code và chạy trên nodejs or console browser để thấy cụ thể và hiểu hơn, điều đó chắc chắn hơn nhiều.

## 3. Sự hạn chế khi dùng deep copy trong JSON

Thêm một chi tiết nữa đó là một nhược điểm khi sử dụng deep copy JSON.parse() và JSON.stringify() đó là đôi khi bị miss những tham số của bạn, nêu tham số đó bạn gán underfined hoặc NaN...

Ví dụ:

```js
const clone = JSON.parse(
  JSON.stringify({
    a: new Date(),
    b: NaN,
    c: new Function(),
    d: undefined,
    e: function () {},
    f: Number,
    g: false,
    h: Infinity,
  })
);

console.log(clone);
```

Thử test trên console của chrome xem sao:

```js
{a: '2022-06-06T13:30:22.493Z', b: null, g: false, h: null}
```

Các bạn thấy đấy một số params đã mất đi không một lời từ biệt, chính vì vậy hãy cẩn thận những gì javascript mang lại cho chúng ta. Điều đó không đùa được với một dev js chuyên nghiệp.
