---
slug: reactjs-interview-senior
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
