---
slug: defensive-css
title: Defensive CSS
authors: [taitd]
tags: [css]
---

<!--truncate-->

Thông thường, chúng ta ước rằng có một cách để tránh xảy ra một số vấn đề hoặc hành vi CSS nhất định. Bạn biết đấy, nội dung của trang web là động và mọi thứ có thể thay đổi, do đó làm tăng khả năng xảy ra sự cố CSS hoặc một hành vi kỳ lạ.

Defensive CSS là một tập hợp các snippets có thể giúp bạn viết CSS được bảo vệ. Nói cách khác, bạn sẽ gặp ít vấn đề hơn trong tương lai. Nếu bạn theo dõi blog của tôi, bạn có thể đọc một bài viết trước đây của tôi có tên là “Tư duy đề phòng”. Bài viết này được xây dựng dựa trên nó và sẽ là một danh sách liên tục của các đoạn snippets.

## 1. Flexbox Wrapping

CSS flexbox là một trong những tính năng CSS Layout hữu ích nhất hiện nay. Thật hấp dẫn để thêm `display: flex` vào một wrapper và đặt các phần tử con cạnh nhau.

Vấn đề là khi không có đủ không gian hiển thị, theo mặc định, những item con đó sẽ không xếp thành một dòng mới. Chúng ta cần thay đổi hành vi đó bằng `flex-wrap: wrap`.

```css
.options-list {
  display: flex;
}
```

![defensive](../2021-12-15-defensive-css/image/defensive-1.png)

Khi có ít không gian hơn, các item sẽ bị tràn ra ngoài flex box. Điều đó nên được mong đợi và thực sự không phải là một "vấn đề".

![defensive](../2021-12-15-defensive-css/image/defensive-1-2.png)

Để ý xem các mục vẫn ở cạnh nhau. Để khắc phục điều đó, chúng ta cần cho phép gói flex.

Thông thường, chúng ta ước rằng có một cách để tránh xảy ra một số vấn đề hoặc hành vi CSS nhất định. Bạn biết đấy, nội dung của trang web là động và mọi thứ có thể thay đổi, do đó làm tăng khả năng xảy ra sự cố CSS hoặc một hành vi kỳ lạ.

Defensive CSS là một tập hợp các snippets có thể giúp bạn viết CSS được bảo vệ. Nói cách khác, bạn sẽ gặp ít vấn đề hơn trong tương lai. Nếu bạn theo dõi blog của tôi, bạn có thể đọc một bài viết trước đây của tôi có tên là “Tư duy đề phòng”. Bài viết này được xây dựng dựa trên nó và sẽ là một danh sách liên tục của các đoạn snippets.

## 2. Spacing

Các developer cần tính đến các độ dài nội dung khác nhau. Điều đó có nghĩa là, khoảng cách nên được thêm vào một component, mặc dù nó có vẻ như không cần thiết.

Trong ví dụ này, chúng ta có tiêu đề phần và action button ở phía bên phải. Hiện tại, nó có vẻ ổn. Nhưng hãy xem điều gì sẽ xảy ra khi tiêu đề dài hơn.

Nếu tiêu đề có khoảng cách và cắt bớt văn bản, chúng ta sẽ không gặp vấn đề như vậy.

```css
.section__title {
  margin-right: 1rem;
}
```

## 3. Nội dung dài

Việc tính toán nội dung dài là điều quan trọng khi xây dựng layout. Như bạn có thể thấy ở phần trước, phần tiêu đề bị cắt bớt khi quá dài. Đó là tùy chọn, nhưng đối với một số UI, điều quan trọng là phải tính đến điều đó.

Đối với tôi, đây là một cách tiếp defensive CSS. Thật tuyệt khi khắc phục “sự cố” trước khi nó thực sự xảy ra.

Đây là danh sách tên của user và hiện tại trông nó có vẻ hoàn hảo.

Tuy nhiên, vì đây là nội dung do người dùng tạo, chúng ta cần phải cẩn thận về cách bảo vệ bố cục trong trường hợp nội dung quá dài. Xem hình sau:

Trong các bố cục như vậy, tính nhất quán rất quan trọng. Để đạt được điều đó, chúng ta có thể cắt bớt tên bằng cách sử dụng `text-overflow`.

```css
.username {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
```

Nếu bạn muốn trau dồi kỹ năng xử lý nội dung dài trong CSS, tôi đã viết một bài viết chi tiết về chủ đề đó.

## 4. Ngăn hình ảnh bị kéo căng hoặc nén

Khi chúng ta không kiểm soát được tỷ lệ khung hình của hình ảnh trên trang web, tốt hơn hết bạn nên suy nghĩ trước và đưa ra giải pháp khi người dùng tải lên một hình ảnh không phù hợp với tỷ lệ khung hình.

Trong ví dụ sau, chúng tôi có một card component với một bức ảnh. Trông nó có vẻ ổn.

Tuy nhiên, khi người dùng tải lên một hình ảnh có kích thước khác, nó sẽ bị kéo giãn. Điều này không tốt. Hãy nhìn hình ảnh được kéo dài như thế nào!

Cách khắc phục đơn giản nhất cho điều đó là sử dụng CSS `object-fit`.

```css
.card__thumb {
  object-fit: cover;
}
```

Ở cấp độ dự án, tôi muốn thêm `object-fit` vào tất cả các hình ảnh để tránh việc hiển thị hình ảnh không mong muốn.

Tìm hiểu thêm về `object-fit` trong bài viết này trên Smashing Magazine.

## 5. Khóa Scroll Chaining

Bạn đã bao giờ mở một modal và bắt đầu cuộn trang, sau đó khi bạn cuộn đến cuối và tiếp tục cuộn, nội dung bên dưới modal thức (phần tử body) sẽ cuộn? Đây được gọi là scroll chaining.

Đã có một vài trick để làm cho nó hoạt động trong những năm qua, nhưng bây giờ, chúng ta có thể làm điều đó chỉ với CSS, nhờ thuộc tính CSS `‌overscroll-behavior`.

Để tránh điều đó trước thời hạn, chúng ta có thể thêm nó vào bất kỳ component nào cần cuộn (ví dụ: chat component, mobile menu...). Điều thú vị về thuộc tính này là nó sẽ không có hiệu lực cho đến khi có thao tác cuộn.

```js
.modal__content {
    overscroll-behavior-y: contain;
    overflow-y: auto;
}
```

Trong trường hợp bạn muốn tìm hiểu thêm về nó, tôi đã viết một bài chi tiết về điều đó.

## 6. CSS Variable Fallback

Các biến CSS ngày càng được sử dụng nhiều hơn trong thiết kế web. Có một phương thức mà chúng ta có thể áp dụng để sử dụng chúng theo cách không phá vỡ trải nghiệm, trong trường hợp giá trị biến CSS trống vì lý do nào đó.

Điều này đặc biệt hữu ích khi cung cấp giá trị của một biến CSS thông qua Javascript. Đây là một ví dụ:

```js
.message__bubble {
    max-width: calc(100% - var(--actions-width));
}
```

Biến `--actions-width` đang được sử dụng trong hàm `calc()` và giá trị của nó đến từ Javascript. Giả sử Javascript không thành công vì một lý do nào đó, điều gì sẽ xảy ra? `max-width` sẽ không tính đến.

Chúng ta có thể tránh điều đó trước thời hạn và thêm giá trị dự phòng vào `var()`.

```js
.message__bubble {
    max-width: calc(100% - var(--actions-width, 70px));
}
```

Bằng cách đó, nếu biến không được xác định, thì dự phòng `(70px)` sẽ được sử dụng. Cách tiếp cận này có thể được sử dụng trong trường hợp có khả năng biến có thể bị lỗi (ví dụ: đến từ Javascript). Nếu không, nó không cần thiết.

## 7. Cố định chiều rộng hoặc chiều cao.

### 7.1. Fixed Height

Tôi thường thấy 1 section có chiều cao cố định và nội dung lớn hơn chiều cao đó, dẫn đến bố cục bị hỏng. Không chắc nó trông như thế nào? Nó đây.

```css
.hero {
  height: 350px;
}
```

Để tránh nội dung bị rò rỉ ra khỏi `hero`, chúng ta cần sử dụng `min-height` thay vì `height`.

```css
.hero {
  min-height: 350px;
}
```

Bằng cách đó, nếu nội dung lớn hơn, layout sẽ không bị vỡ.

### 7.1. Fixed Width

Bạn đã bao giờ thấy button có label quá gần các cạnh trái và phải chưa? Điều này xảy ra là do bạn sử dụng chiều rộng cố định, như thế này:

```css
.button {
  width: 100px;
}
```

Nếu label của button dài hơn `100px`, nó sẽ gần với các cạnh. Nếu quá dài, phần text sẽ bị lọt ra ngoài button, điều này thực sự không tốt!

Để khắc phục điều đó, chúng ta chỉ cần thay thế `width` bằng `min-width`.

```css
.button {
  min-width: 100px;
}
```

## 8. Forgetting Background-Repeat

Thông thường, khi sử dụng hình ảnh lớn làm background, chúng ta có xu hướng quên tính đến trường hợp thiết kế được xem trên màn hình lớn. Background đó sẽ lặp lại theo mặc định.

Điều này gần như sẽ không hiển thị trên màn hình laptop, nhưng nó có thể được nhìn thấy rõ ràng trên màn hình lớn hơn.

Để tránh hành vi đó trước, hãy đảm bảo đặt lại `background-repeat`.

```css
.hero {
  background-image: url("..");
  background-repeat: no-repeat;
}
```

## 9. Vertical Media Queries

Đôi khi, thật hấp dẫn khi xây dựng một component và chỉ kiểm tra bằng cách thay đổi kích thước chiều rộng của trình duyệt. Thử nghiệm so với chiều cao của trình duyệt có thể cho thấy một số vấn đề thú vị.

Đây là một cái mà tôi đã thấy nhiều lần. Chúng ta có một component riêng với các liên kết chính và phụ. Các liên kết phụ nên được đặt ở dưới cùng.

Hãy xem xét ví dụ sau. Điều hướng chính và phụ có vẻ ổn. Trong ví dụ mà tôi đã thấy, developer đã thêm `position: sticky` vào điều hướng phụ để nó có thể dính vào phía dưới.

Tuy nhiên, nếu chiều cao trình duyệt nhỏ hơn, layout sẽ bị vỡ. 2 phần điều hướng bị chồng lên nhau.

Bằng cách sử dụng CSS vertical media queries, chúng ta có thể tránh được vấn đề đó.

```css
@media (min-height: 600px) {
  .aside__secondary {
    position: sticky;
    bottom: 0;
  }
}
```

Bằng cách trên, điều hướng phụ sẽ chỉ được dán ở dưới cùng nếu chiều cao của khung nhìn lớn hơn hoặc bằng 600px. Tốt hơn nhiều, phải không?

Có lẽ có nhiều cách tốt hơn để triển khai hành vi đó (như sử dụng `margin-auto`) nhưng tôi đang tập trung vào truy vấn dọc cho ví dụ này.

Nếu tôi muốn giải thích bằng cách sử dụng CSS vertical media query, tôi cần phải viết một bài báo viết đủ về nó. Tin tốt là tôi đã viết một bài, trong trường hợp bạn quan tâm.

## 10. Sử dụng Justify-Content: Space-Between

Trong một flex container, bạn có thể sử dụng `justify-content` để tạo khoảng cách giữa các item con với nhau. Với một số lượng item nhất định, bố cục sẽ ổn. Tuy nhiên, khi chúng tăng lên hoặc giảm đi, layout sẽ có vấn đề. Hãy xem xét ví dụ sau.

Chúng ta có một flex container với 4 item. Khoảng cách giữa mỗi item không phải là `gap` hoặc `margin`, nó ở đó bởi vì container có `justify-content: space-between`.

```css
.wrapper {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
```

Khi số lượng item ít hơn 4, đây là điều sẽ xảy ra.

Điều này không tốt. Có các giải pháp khác nhau cho vấn đề này:

- Margin
- Flexbox gap (Sử dụng thận trọng)
- Padding (Có thể được áp dụng cho phần tử cha của mỗi phần tử con)
- Thêm các phần tử trống để hoạt động như một bộ đệm.

Để đơn giản, tôi sẽ sử dụng khoảng `gap`.

```css
.wrapper {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}
```

## 11. Văn bản trên hình ảnh

Khi sử dụng văn bản trên hình ảnh, điều quan trọng là phải tính đến trường hợp hình ảnh không tải được. Khi đó, văn bản sẽ hiển thị như thế nào? Đây là một ví dụ.

Văn bản trông có thể đọc được, nhưng khi hình ảnh không tải được thì sẽ không.

Chúng tôi khắc phục điều đó một cách dễ dàng bằng cách thêm background vào phần tử &lt;img>. Nền này sẽ chỉ hiển thị nếu hình ảnh không tải được. Điều đó không thú vị phải không?

```css
.card__img {
  background-color: grey;
}
```

## 12. Hãy cẩn thận với các giá trị cố định trong CSS Grid
