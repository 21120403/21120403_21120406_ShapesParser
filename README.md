# __Tài liệu mô tả__

__Thành viên nhóm__

- Họ tên: Nguyễn Hoàng Quân -- MSSV: 21120403
- Email: 21120403@student.hcmus.edu.vn 

- Họ tên: Lê Viết Đạt Trọng -- MSSV: 21120416
- Email: 21120406@student.hcmus.edu.vn

## __Phân công__

     1. Nguyễn Hoàng Quân:
        + Các chức năng cơ bản (Tạo các class đối tượng hình học, các hàm cơ bản (print, sort,...)), thêm 2 đối tượng hình học.
        + Tìm hiểu và tách các đối tượng hình học ra các thư viện liên kết động (dll)
        + Tìm hiểu và viết tài liệu mô tả bằng Markdown

    2. Lê Viết Đạt Trọng:
        + Các chức năng nâng cao (design pattern, con trỏ thông minh,...)
        + Bắt các lỗi và xử lí các ngoại lệ.
## __Các chức năng đã làm__
1. Đọc danh sách các đối tượng hình học được lưu trong tập tin  shapes.txt
2. In ra màn hình danh sách các hình đã đọc
3. Sắp xếp các hình đã đọc tăng dần theo diện tích và in ra màn hình theo dạng cột
###  __Các yêu cầu nâng cao__
1. Sử dụng mẫu thiết kế design pattern
- Singleton
- Factory (cho việc parse)
- Strategy (cho việc hiển thị)
- Dependency injection
- Tách được các đối tượng hình học ra các thư viện liên kết động (dll)
2. Sử dụng con trỏ thông minh giải quyết các vấn đề về con trỏ
3. Comment đầy đủ ý nghĩa các hàm trong mã nguồn
4. Có bắt các lỗi và xử lí các ngoại lệ dễ nhận ra

###  __Các yêu cầu nâng cao tự tìm hiểu__
1. Bổ sung các đối tượng hình học khác ( 2 hình: Tam giác và Hình bình hành ) 
2. Tự phát sinh ra tài liệu mô tả hệ thống

### __Các điểm xem xét cộng thêm điểm__
1. Có tìm hiểu và tách được các đối tượng hình học ra các thư viện liên kết động (dll)
2. Thực hiện các design pattern theo yêu cầu
3. Sử dụng con trỏ thông minh giải quyết các vấn đề về con trỏ

### __Các điểm làm chưa tốt__
1. Các thư viện động dll vẫn chưa được tối ưu vẫn gặp nhiều vấn đề vẫn chưa giải quyết triệt để (các warning và messesges) nhưng vẫn có thể hoạt động
2. Không làm Unit test

## __Điểm đề nghị__
1. Nguyễn Hoàng Quân: 10
2. Lê Viết Đạt Trọng: 10

## __Tạo 1 Project DLL mới__

Đầu tiên chúng em sẽ tạo 1 Project mới, nhưng thay vì tạo vằng Empty Project thì chúng em đã hướng tới việc xây dựng tách các đối tượng hình học ra các thư viện liên kết động (.dll) để có thể dễ sửa chữa và thay đổi thế nên chúng em chọn Tạo 1 Console App để có thể sử dụng các thư viện liên kết động sẽ được xây dựng

![alt-text](https://i.imgur.com/Cf46Mbz.png)

Sau đó chúng em tạo các thư viện liên kết động để có thể dùng cho Console App
  
    - Đầu tiên chúng em sẽ tạo 1 thư viện động (Dynamic-Link Library DLL) với tên là Shapes để tạo lớp cha Shape sẽ được các lớp con (các đối tượng hình học) kế thừa.
  
![alt-text](https://learn.microsoft.com/en-us/cpp/build/media/create-new-dll-project-2019.png?view=msvc-170)
![alt-text](https://i.imgur.com/ntmdXXA.png)

    - Sau đó chúng em sẽ bắt đầu cài đặt Header lớp Shapes.
        + Hãy chú ý đến phần Preprocessor statements ở đầu file. Công dụng của Statements này là để khi Thư viện Shapes.dll được build thì sẽ báo với Compiler và Linker sẽ xuất 1 Function hoặc 1 biến Variable từ thư viện DLL sẽ được dùng cho các ứng dựng Applications khác.
    - Tham khảo để biết thêm: https://learn.microsoft.com/en-us/cpp/cpp/dllexport-dllimport?view=msvc-170

![alt-text](https://i.imgur.com/S7R2nr9.png)

    - Và với việc các hàm Public của lớp cha đều là hàm Virtual thế nên chúng em sẽ tiến hành cài đặt các đối tượng hình học kế thừa lớp Shape. Tương tự với việc tạo Thư viện động Shapes, chúng em sẽ tạo các thư viện động cho các đối tượng hình học.

![alt-text](https://i.imgur.com/TrbEF0m.png)

    - Và cũng tương tự chúng em sẽ cái đặt Header và CPP cho các đối tượng hình học. Ví dụ ở đây là đối tượng hình học Circle, và các đối tượng hình học khác cũng sẽ được cái đặt tương tự.

![alt-text](https://i.imgur.com/9aIcJyW.png)

![alt-text](https://i.imgur.com/9aIcJyW.png)

## __Để Add DLL Header vào Include path__

    - Khi cài đặt bạn có thể để ý 1 việc bất thường đó chính là: Tại sao lại không thể Include được thư viện Shapes.h

Câu trả lời đó chính là do Circl DLL vẫn chưa được add với Header Shapes DLL và để khắc phục vấn đề này chúng ta chỉ cần đơn giản là link chúng lại với nhau

    - Đầu tiên chúng ta nhấn chuột phải vào Project DLL cần link chọn Configuration Properties > C/C++ > General. Trong khung Drop-down control kế khung Additional Include Directories > chọn Edit. Và do Circle DLL và Shapes DLL nằm cùng 1 solution và vậy nên địa chỉ sẽ được cài đặt như sau: "..\".
    - Và sau đó chúng ta đã có thể dùng Header lớp cha Shapes DLL trên các lớp con DLL

![alt-text](https://i.imgur.com/BKCjFv0.png)

## __Cài đặt Client app__

    - Kế đến chúng ta sẽ cài đặt hàm main (Console Application mà chúng ta đã cài đặt lúc bắt đầu)
    - Và để sử dụng các DLL project khác thì chúng ta lại cần add với Header Shapes DLL và các DLL của các đối tượng hình học cần dùng. Và do main của chúng ta không nằm cùng với DLL Shapes nên chúng ta cần chỉ sửa lại Include Directories sao cho phù hợp

![alt-text](https://i.imgur.com/ZIU48pE.png)

    - Bây giờ Code của chúng ta có thể được compiled, nhưng vẫn chưa được linked. Nếu chúng ta build Client app, thì sẽ báo lỗi LNK2019. Đó là do Project đang thiếu 1 vài thông tin: Bạn vẫn chưa xác định rằng Project đang phụ thuộc vào Shapes.lib DLL và các đối tượng hình học như Cirle.lib. Và bạn vẫn chưa bảo Linker cách để tìm những file .lib đấy

## __Add thư viện DLL Import vào project__

    - Chúng ta vào Properties của Project main chọn Configuration Properties > Linker > Input > Additional Dependencies > Edit
    - Chúng ta chỉ cần Add những thư viện chúng ta cần: Shapes.lib; Circle.lib,....

![alt-text](https://i.imgur.com/Hnvh0wP.png)

    - Tiếp đến chúng chọn Configuration Properties > Linker > General > Additional Library Directories > Edit
    - Chúng ta chỉ dẫn cụ thể đến nơi chứa các thư viện .lib DLL. Bạn có thể dùng $(IntDir) để tự động Macro để Linker có thể tìm thấy DLL cần thiết.

![alt-text](https://i.imgur.com/JD2Bufc.png)

    - Sau đó mọi thứ đã có vẻ ổn thỏa và tiếp đến chúng em xây dựng các hàm hỗ trợ, các chức năng cho chương trình theo yêu cầu. Bao gồm các hàm Parse các đối tượng hình học (CircleParser, ....), các hàm giúp hỗ trợ việc hiển thị Display ra màn hình (Display,...), các hàm đọc file và tách file (Reader,...).

![alt-text](https://i.imgur.com/GPHxV5H.png)

## __Chạy thử chương trình__

    - Nếu như mọi thứ đều ổn thì khi chúng ta Build solution thì mọi thứ sẽ trông như thế này: 

![alt-text](https://i.imgur.com/02L9kB8.png)

    - Chúng ta có thể chạy thử chương trình bằng Ctrl + F5 hoặc chúng ta có thể vào folder Debug hoặc Release tùy theo cài đặt và chọn file main.exe để kiểm thử

![alt-text](https://i.imgur.com/fzlv0eC.png)

    - Chúng ta kiểm thử với file shapes.txt theo quy định: 

![alt-text](https://i.imgur.com/r4KBpeM.png)

![alt-text](https://i.imgur.com/IUl4Kdn.png)

# __Cách chương trình hoạt động__
## __1. Tạo ra các đối tượng hình học__
Tạo ra một Abstract class(class Shape), lớp này cung cấp một định nghĩa về hình học và cấu trúc chung cho các lớp con.

![alt-text](https://i.imgur.com/Lon1Uco.png)

Các lớp Circle, Parallelogram, Rectangle, Square, Triangle kế thừa từ Shape

![alt-text](https://i.imgur.com/QHPAlND.png)

![alt-text](https://i.imgur.com/A1tQbmP.png)

![alt-text](https://i.imgur.com/2yORod8.png)

![alt-text](https://i.imgur.com/7ImZ0vk.png)

![alt-text](https://i.imgur.com/T7rNjTt.png)

## __2. Đọc file__

Đọc để lấy thông tin từ file shapes.txt.

Tạo một class Reader dùng để đọc file (Sử dụng Singleton Design Pattern) để đảm bảo rằng chỉ một đối tượng được tạo và file chỉ được đọc duy nhất một lần trong quá trình chạy chương trình.

![alt-text](https://i.imgur.com/vzsfx93.png)

Bắt đầu chương trình, khởi tạo đối tượng bằng phương thức GetInstance

![alt-text](https://i.imgur.com/jgVWve8.png)

Sử dụng hàm regex pattern để kiểm tra định dạng của dòng dữ liệu đọc được

![alt-text](https://i.imgur.com/aBFf0TN.png)

![alt-text](https://i.imgur.com/V6TVh1P.png)

## __3. Phân tách dữ liệu__

Tạo một class Iparser dùng để phân tách các dòng dữ liệu đã đọc được, phân tách chúng thành các đối tượng hình học

![alt-text](https://i.imgur.com/oGVHy0L.png)

Các class CircleParser, ParallelogramParser, RectangleParser, SquareParser, TriangleParser kế thừa từ IParser.

![alt-text](https://i.imgur.com/jhAvfhy.png)

![alt-text](https://i.imgur.com/60LYmL4.png)

![alt-text](https://i.imgur.com/V26oElp.png)

![alt-text](https://i.imgur.com/VDCescc.png)

![alt-text](https://i.imgur.com/lxODw8v.png)

Tạo một class ParserFactory sử dụng Factory Design Pattern để tạo ra các đối tượng hình học và Dependency Injection để tiêm động các đối tượng hình học vào trong chương trình

![alt-text](https://i.imgur.com/NViX0O4.png)

Muốn sử dụng các đối tượng hình học nào, ta chỉ cần đăng kí đối tượng đó với nhà máy

![alt-text](https://i.imgur.com/bluGIEB.png)

## __4. Quản lý các đối tượng hình học__

Tạo ra một class ListShape để quản lý các đối tượng hình học 

![alt-text](https://i.imgur.com/SZsdPcu.png)

Lấy dữ liệu từ danh sách đã đọc được từ Reader, sau đó tách từng dòng dữ liệu trả về các đối tượng hình học, sau đó thêm đối tượng đó vào trong danh sách các đối tượng hình học:

![alt-text](https://i.imgur.com/bEr14rF.png)

## __5. Hiển thị ra màn hình các đối tượng hình học__

Tạo ra một abstract class(class Display) sử dụng Strategy Design Pattern để tùy chọn thuật toán cho việc in

![alt-text](https://i.imgur.com/DAwRCKi.png)

Tạo ra một class DisplayFile: kế thừa từ class Display dùng để hiển thị các dòng dữ liệu sau khi đã đọc file 

![alt-text](https://i.imgur.com/WPmPp1X.png)

Tạo ra một class DisplayNormal: kế thừa từ class Display dùng để hiển thị các dòng dữ liệu sau khi sắp xếp các đối tượng hình học theo danh sách tăng dần diện tích.

![alt-text](https://i.imgur.com/Z0LWUmj.png)

Để sắp xếp tăng dần, sử dụng thuật toán MergeSort trong class ListShape, vì thuật toán MergeSort có độ phức tạp ổn định O(nlogn) nên danh sách có nhiều dòng dữ liệu hơn thì thời gian sắp xếp vẫn nhanh hơn so với các thuật toán khác

Ở hàm main, sau khi đã đọc xong file thì in ra nội dung file đã đọc, sắp xếp danh sách và in ra kết quả cuối cùng 

![alt-text](https://i.imgur.com/wo2Oc5l.png)

