# DECORATOR PATTERN

- Giới thiệu
- Đặt vấn đề
- Cách Decorator Pattern giải quyết vấn đề
- Structure 
- Ứng dụng
- Cách cài đặt Decorator Pattern Java Spring
- Mối liên hệ với các loại Design Pattern khác
- Applicability

## 1. Giới thiệu
- Decorator Pattern là một trong những Pattern thuộc nhóm cấu trúc (Structural Pattern), nó cho phép người dùng thêm các tác vụ, chức năng( method) mới vào một đối tượng, không sử dụng chiến lược thừa kế để để mở rộng thêm chức năng cho đối tượng mà dùng phương pháp bao bọc (wrap) cho lớp hiện có, mỗi khi muốn thêm chức năng mới, đối tượng hiện có được bao bọc ( wrap) lại và được trang trí (decorator thêm chức năng)
- Ý tưởng hiện tại của Decorator Pattern là không cần thay đổi code gốcApplicability , không cần thừa kế để mở rộng đối tượng 

## 2. Đặt vấn đề
decorator pattern with generic
- Hãy thử tưởng tượng hiện tại bạn đang có một Notification sdecorator pattern with genericervices cho phép client gửi các noti đến users liên quan đến các critial event.
- Ở phiên bản đầu tiên được phát triển cho Notification services này được xây dựng dựa trên lớp **Notifier** bao gồm các thuộc tính (attribute) cơ bản,  một constructor, và một chức năng (method) send.
- Method send này nhận vào các đối số là messages từ client và thực hiện send message đó cho danh sách email đã được pass vào trong đối tượng **Notifier** thông qua constructor của nó.5.Cách cài đặt Decorator Pattern Java Spring
- Một client khác sẽ sử dụng service này sẽ tạo và cấu hình lại **Notifier** , sau đó sử dụng để send noti khi các critial event xảy ra.

- ![alt text](https://user-images.githubusercontent.com/57431066/142334969-7bb38abf-2e84-411f-9d88-93f9a3987360.png)

- Vấn đề đặt ra ở đây là sau này khi mà **User** mong muốn rằng service này sẽ không chỉ gửi notification thông qua email, mà họ còn muốn thông qua nhiều nền tảng kác như là **SMS** , **FaceBook**, từ đó các lớp  **SMS** và **FaceBook** sẽ được kế thừa các thuộc tính và method (extends ) từ lớp **Notifier** ban đầu.
- ![alt text](https://user-images.githubusercontent.com/57431066/142399244-f1186a54-d010-4e32-a518-8fb4d078278a.png)
- Và xử lý vấn đề theo cách này lại sinh ra một vấn đề khác, chẳng hạn client mong muốn cùng một lúc sẽ gửi 2 loại notification **SMS** và **FaceBook** , thì tương tự solution ở trên developer lại tạo ra một lớp **SMS + FaceBook** thì khi client mong muốn gửi thêm nhiều loại tổ hợp noti thì các lớp của ta sẽ trở thành như sau.
- ![alt text](https://user-images.githubusercontent.com/57431066/142431182-2e0855db-d957-4b1b-9648-4d182e3eb037.png)

## 3.Cách Decorator Pattern giải quyết vấn đề
decorator pattern with generic
- Decorator pattern còn có một thuật ngữ dùng để thay thế khác gọi là **Wrapper** , chỉ cần dựa vào cái tên **Wrapper** thì ta đã có thể hình dung được ý tưởng của Decorator là gì rồi phải không nào . **Wrapper** là một object mà ở đó ta có thể liên kết với các targer object khác . **Wrapper** và các object được Wrapper đều thực hiện cùng các method giống nhau và **Wrapper** liên kết với target thông qua các method này , tuy nhiên wrapper có thể thay đổi kết quả của các method này bằng cách thêm một vài tính năng mới nào đó tùy thuộc vào logic ngiệp vụ vào trước và sau khi **Wrapper** gửi request đến object được wrapper.
- **Wrapper** sẽ chấp nhận các wrapped object mà implement cùng một interface với nó,do đó nó có thể cho phép bạn wrapp một đối tượng trong nhiều **Wrapper**.
- Decorator Pattern giải quyết vấn đề nêu ở trên bằng cách đưa method cơ bản nhất là **Email notification** vào đổi tượng gốc và đưa các phường thức send notification khác vào trong các **Wrapper** khác.
- ![alt text](https://user-images.gi-thubusercontent.com/57431066/143668970-79e47a70-e6af-41d5-8a66-b15498b2e3e2.png)
## 4.Structure
-![alt text](https://user-images.githubusercontent.com/57431066/143669467-2b0e1ac6-3c1f-4206-936d-89cf46e773f3.png)
- **Component** : định nghĩa interface của đối tượng mà ta muốn wrap nó
- **Concreate Component** : định nghĩa các hành vi của đổi tượng được wrap
- **Base Decorator** : lớp trừu tượng chứa một tham chiếu đến đối tượng được wrap, định nghĩa của **Base Decorator** phù hợp với interface của **Component**, constructor của đối số sẽ là đối tượng được trang trí thêm chức năng, và **Base Decorator** có thể bắt các đối tượng được wrapp thực hiện các phương thức của nó
- **Concrete Decorators** : dùng để định nghĩa các phương thức khác được trang trí thêm vào **Concreate Component**,và thực hiện các phương thức mới của chúng trước hoặc là sau khi thực hiện phương thức mẹ của **Base Decorator**

## 5.Cách cài đặt Decorator Pattern Java Spring
- **Component** : đĩnh nghĩa interface của đối tượng được wrap
``` 
interface Component {
    void draw();
}
```
- **Concreate Component** : định nghĩa đối tượng cụ thể ta muốn warp, ở đây là "ScrollbarWindow" và "IconWindow"
```ScrollbarWindow
class ScrollbarWindow extends Decorator {
    String scrollbar = "scrollbar";
    public ScrollbarWindow(Component component) {
        super(component);
    }
    @Override public void draw() {super.draw();
        System.out.println("Draw " + scrollbar);
    }
}
```
```
class IconWindow extends Decorator {
    String icon = "icon";
    public IconWindow(Component component) **Base Decorator**{
        super(component);
    }
    @Override public void draw() {
        super.draScrollbarWindoww();
        System.out.println("Draw " + icon);
    }
}
```
- **Base Decorator** : lớp trang trí gốc, bao bọc lấy component cần được trang trí và đồng thời định nghĩa các phương thức phù hợp với **Component**

```
class Decorator implements Component {
    Component component;
    public Decorator(Component component) {
        this.component = component;**Concreate Component**
    }
    @Override public void draw() {
        component.draw();
    }
}
```
- **Concrete Decorators** : các lớp trang trí cụ thể bao bọc lấy các **Concreate Component**, định nghĩa lại các phương thức của **Base Decorator** hoặc là dữ nguyên và trang trí cho **Concreate Component** các phương thức mới.
```
class ScrollbarWindow extends Decorator {
    String scrollbar = "scrollbar";
    public ScrollbarWindow(Component component) {
        super(component);
    }
    @Override public void draw() {super.draw();
        System.out.println("Draw " + scrollbar);
    }
}
```
```
class IconWindow extends Decorator {
    String icon = "icon";
    public IconWindow(Component component) {
        super(component);
    }
    @Override public void draw() {
        super.draw();
        System.out.println("Draw " + icon);
    }
}
```
## 6. Mối liên hệ với các loại Design Pattern khác
- **Adapter** : **Adapter** bao bọc lấy đối tượng để thay đổi interface của chúng, trong khi decorator bao bọc lấy đối tượng để bổ sung thêm hành vi cho nó.
- **Composite** : **Decorator** cũng có thể xem như là **Composite** với duy nhất một component con, ngoài ra, **Decorator** trang trí thêm các phương thức vào component con trong khi **Composite** thì sẽ tổng hợp kết quả của các thằng con lại thay vì xem phương thức tổng hợp như một decorator.
- **Strategy** : **Decorator** bao bọc và làm thay đổi bên ngoài đối tượng , trong khi **Strategy** thì tác động vào và làm thay đổi bên trong của đổi tượng.
- **Factory Method** : Factory Method đôi khi được sử dụng với Decorator để dùng cho lớp khởi tạo các loại component,  ví dụ :
- - Các lớp khởi tạo creator component có sứ dụng decorator, sử dụng interface và các lớp ở ví dụ trên
```
interface Creator {
Component createWindow();
}
class ScrollbarWindowCreator implements Creator {
@Override public Component createWindow() {
return new ScrollbarWindow(new Window());
}
```
```
}
class IconWindowCreator implements Creator {
@Override public Component createWindow() {
return new IconWindow(new ScrollbarWindow(new Window()));
}
```
## 7.Applicability 
- Hãy sử dụng **Decorator** trong trường hợp ta cần thêm một hành vi hay phương thức nào đó vào trong một đối tượng theo runtime mà không muốn phải chính sửa code của đối tượng đó
- Hãy sử dụng **Decorator** trong trường hợp ta bất khả thi trong việc sử dụng extends để kế thừa các phương thức của đối tượng, ví dụ trong nhiều trường hợp , nhiều loại ngôn ngữ lập trình sử dụng từ khóa **final** để ngăn ngừa trường hợp một lớp mở rộng ra quá lớn để rồi khó quản lý và maintance, đối với các lớp final, cách duy nhât để sử dụng lại các phương thức gốc của nó là sử dụng **Decorator** để bao bọc nó lại.
- Một số ứng dụng của **Decorator Pattern ** trong thư viện java core.
- - Có thể bạn chưa biêt , một trong những thư viện mà chúng ta hay sử dụng là Stream API được thiết kế theo **Decorator Pattern**, ở đây tất cả các lớp con của InputStream, OutPutStream, Reader, Writer đều nhận vào biến khởi tạo cùng loại
