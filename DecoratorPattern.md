# DECORATOR PATTERN

- Giới thiệu
- Đặt vấn đề
- Cách Decorator Pattern giải quyết vấn đề
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
- Method send này nhận vào các đối số là messages từ client và thực hiện send message đó cho danh sách email đã được pass vào trong đối tượng **Notifier** thông qua constructor của nó.
- Một client khác sẽ sử dụng service này sẽ tạo và cấu hình lại **Notifier** , sau đó sử dụng để send noti khi các critial event xảy ra.

- ![alt text](https://user-images.githubusercontent.com/57431066/142334969-7bb38abf-2e84-411f-9d88-93f9a3987360.png)

- Vấn đề đặt ra ở đây là sau này khi mà **User** mong muốn rằng service này sẽ không chỉ gửi notification thông qua email, mà họ còn muốn thông qua nhiều nền tảng kác như là **SMS** , **FaceBook**, từ đó các lớp  **SMS** và **FaceBook** sẽ được kế thừa các thuộc tính và method (extends ) từ lớp **Notifier** ban đầu.
- ![alt text](https://user-images.githubusercontent.com/57431066/142399244-f1186a54-d010-4e32-a518-8fb4d078278a.png)
- Và xử lý vấn đề theo cách này lại sinh ra một vấn đề khác, chẳng hạn client mong muốn cùng một lúc sẽ gửi 2 loại notification **SMS** và **FaceBook** , thì tương tự solution ở trên developer lại tạo ra một lớp **SMS + FaceBook** thì khi client mong muốn gửi thêm nhiều loại tổ hợp noti thì các lớp của ta sẽ trở thành như sau.
- ![alt text](https://user-images.githubusercontent.com/57431066/142431182-2e0855db-d957-4b1b-9648-4d182e3eb037.png)

## 3.Cách Decorator Pattern giải quyết vấn đề

- Decorator pattern còn có một thuật ngữ dùng để thay thế khác gọi là **Wrapper** , chỉ cần dựa vào cái tên **Wrapper** thì ta đã có thể hình dung được ý tưởng của Decorator là gì rồi phải không nào . **Wrapper** là một object mà ở đó ta có thể liên kết với các targer object khác . **Wrapper** và các object được Wrapper đều thực hiện cùng các method giống nhau và **Wrapper** liên kết với target thông qua các method này , tuy nhiên wrapper có thể thay đổi kết quả của các method này bằng cách thêm một vài tính năng mới nào đó tùy thuộc vào logic ngiệp vụ vào trước và sau khi **Wrapper** gửi request đến object được wrapper.
- **Wrapper** sẽ chấp nhận các wrapped object mà implement cùng một interface với nó,do đó nó có thể cho phép bạn wrapp một đối tượng trong nhiều **Wrapper**.
- Decorator Pattern giải quyết vấn đề nêu ở trên bằng cách đưa method cơ bản nhất là **Email notification** vào đổi tượng gốc và đưa các phường thức send notification khác vào trong các **Wrapper** khác.
- ![alt text](https://user-images.githubusercontent.com/57431066/143668970-79e47a70-e6af-41d5-8a66-b15498b2e3e2.png)
## 4.Structure
-![alt text](https://user-images.githubusercontent.com/57431066/143669467-2b0e1ac6-3c1f-4206-936d-89cf46e773f3.png)

