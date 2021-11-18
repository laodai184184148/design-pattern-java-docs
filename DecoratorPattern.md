# DECORATOR PATTERN

- Giới thiệu
- Đặt vấn đề
- Cách mà Decorator Pattern giải quyết vấn đề
- Structure 
- Ứng dụng
- Cách cài đặt Decorator Pattern Java Spring
- Pros và Cons khi sử dụng Decorator
- Mối liên hệ với các loại Design Pattern khác
- Code ví dụ\

## 1. Giới thiệu
- Decorator Pattern là một trong những Pattern thuộc nhóm cấu trúc (Structural Pattern), nó cho phép người dùng thêm các tác vụ, chức năng( method) mới vào một đối tượng, không sử dụng chiến lược thừa kế để để mở rộng thêm chức năng cho đối tượng mà dùng phương pháp bao bọc (wrap) cho lớp hiện có, mỗi khi muốn thêm chức năng mới, đối tượng hiện có được bao bọc ( wrap) lại và được trang trí (decorator thêm chức năng)
- Ý tưởng hiện tại của Decorator Pattern là không cần thay đổi code gốc , không cần thừa kế để mở rộng đối tượng 

## 2. Đặt vấn đề

- Hãy thử tưởng tượng hiện tại bạn đang có một Notification services cho phép client gửi các noti đến users liên quan đến các critial event.
- Ở phiên bản đầu tiên được phát triển cho Notification services này được xây dựng dựa trên lớp **Notifier** bao gồm các thuộc tính (attribute) cơ bản,  một constructor, và một chức năng (method) send.
- Method send này nhận vào các đối số là messages từ client và thực hiện send message đó cho danh sách e mail đã được pass vào trong đối tượng **Notifier** thông qua constructor của nó.
- Một client khác sẽ sử dụng service này sẽ tạo và cấu hình lại **Notifier** , sau đó sử dụng để send noti khi các critial event xảy ra.

- ![alt text](https://user-images.githubusercontent.com/57431066/142334969-7bb38abf-2e84-411f-9d88-93f9a3987360.png)

