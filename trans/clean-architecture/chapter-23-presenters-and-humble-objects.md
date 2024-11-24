# Chapter 23 : Presenters and Humble Objects
------------------

Trong Chương 22, chúng ta đã giới thiệu khái niệm các presenter. Các presenter là một dạng của mẫu thiết kế Humble Object, nó sẽ giúp chúng ta xác định và bảo vệ các ranh giới kiến trúc. Thực tế, Kiến Trúc Tinh Gọn trong chương trước là dạng đầy đủ của sự triển khai Humble Object.

## The Humble object pattern
Humble Object là một mẫu thiết kế được xác định ban đầu là một cách để giúp các tester tách biệt những hành vi khó kiểm tra khỏi những hành vi dễ kiểm tra. Ý tưởng này rất đơn giản: Chia các hành vi trong hai module hoặc lớp. Một module là humble; nó bao gồm tất cả những hành vi khó kiểm tra. Module còn lại bao gồm tất cả những hành vi có thể kiểm tra được, đã được loại bỏ khỏi humble object.

Lấy ví dụ, GUI khó thực hiện unit test bởi vì rất khó để viết các bài kiểm tra mà có thể nhìn vào màn hình và kiểm tra các thành phần thích hợp được hiển thị trên đó. Tuy nhiên, thực tế phần lớn hành vi của một GUI thì lại dễ dàng để kiểm tra. Bằng việc sử dụng mẫu thiết kế Humble Object, chúng ta có thể tách biệt hai loại hành vi này thành hai lớp khác nhau được gọi là Presenter và View.

## Presenters and views
View là Humble Object khó để kiểm tra. Code trong đối tượng này được giữ cho càng đơn giản càng tốt. Nó di chuyển dữ liệu vào GUI nhưng không xử lý dữ liệu đó.

Presenter là đối tượng kiểm tra được. Công việc của nó là nhận dữ liệu từ ứng dụng và định dạng nó để biểu diễn sao cho View chỉ cần đơn giản chuyển nó ra màn hình mà thôi. Lấy ví dụ, nếu ứng dụng muốn ngày tháng hiển thị trong một trường, nó sẽ đưa cho Presenter đối tượng Date. Presenter sau đó sẽ định dạng dữ liệu đó thành chuỗi thích hợp và đặt nó vào trong một cấu trúc dữ liệu đơn giản được gọi là View Model, nơi mà View có thể tìm thấy nó.

Nếu ứng dụng muốn hiển thị tiền trên màn hình, nó có thể truyền đối tượng Currency cho Presenter. Presenter sẽ định dạng dữ liệu đó với dấu thập phân và ký hiệu tiền tệ cho phù hợp, tạo ra một string mà nó có thể đặt vào trong View Model. Nếu giá trị tiền tệ cần được chuyển màu đỏ nếu âm, thì một cờ đơn giản trong View Model sẽ được đặt cho thích hợp.

Mọi nút trên màn hình đều sẽ có tên. Cái tên đó là một string trong View Model, được đặt ở đó nhờ Presenter. Nếu những nút đó cần được vô hiệu hóa màu xám, thì Presenter sẽ đặt một cờ thích hợp trong View Model. Mọi tên gọi của từng menu item đều là một string trong View Model, được nạp vào bởi Presenter. Các tên cho mọi radio button, check box, và text field cũng được nạp bởi Presenter vào các string và cờ boolean phù hợp trong View Model. Các bảng số liệu được hiển thị trên màn hình được nạp bởi Presenter, vào trong các bảng của các string được định dạng phù hợp trong View Model.

Bất cứ thứ gì và mọi thứ xuất hiện trên màn hình, và ứng dụng đó có một vài loại kiểm soát, được biểu diễn trong View Model dưới dạng một string, hoặc một boolean, hoặc một enum. View không làm gì khác ngoài nạp những dữ liệu đó từ View Model lên màn hình. Do vậy View được gọi là humble.

## Testing and Architecture
Đã từ lâu khả năng kiểm tra được đã được coi là một thuộc tính của một kiến trúc tốt. Mẫu thiết kế Humble Object là một ví dụ tốt, bởi vì việc tách rời các hành vi thành các phần có thể kiểm tra được và không thể kiểm tra được thường xác định nên một ranh giới kiến trúc. Ranh giới Presenter/View là một trong những ranh giới này, nhưng còn nhiều cái khác.

## Database gateways

Nằm giữa use case interactor và cơ sở dữ liệu là các cổng vào cơ sở dữ liệu (database gateway[3]). Những cổng vào này là các interface đa hình bao gồm các method cho từng hành động tạo, đọc, sửa, hoặc xóa mà có thể được thực hiện bởi ứng dụng trên cơ sở dữ liệu. Lấy ví dụ, nếu ứng dụng cần biết họ của tất cả người dùng đã đăng nhập hôm qua, thì interface UserGateway sẽ có một method tên là getLastNameOfUsersWhoLoggedInAfter và lấy Date làm tham số của nó và trả về một danh sách họ của người dùng.

Nhắc lại là chúng ta không cho phép SQL tồn tại trong layer use case; thay vào đó, chúng ta dùng các gateway interface có các method thích hợp. Những gateway này được triển khai bởi các lớp trong layer cơ sở dữ liệu. Sự triển khai đó là một humble object. Nó đơn giản dùng SQL, hoặc bất cứ interface nào tới cơ sở dữ liệu đó, để truy cập tới dữ liệu được yêu cầu bởi mỗi method. Ngược lại, interactor không phải là humble bởi vì chúng đóng gói lại các quy tắc nghiệp vụ của ứng dụng cụ thể. Mặc dù chúng không phải humble, nhưng những interactor này lại có thể kiểm tra được, bởi vì các gateway này có thể được thay thế bởi các stub và test-double thích hợp.

## Data Mappers
Trở lại chủ đề về cơ sở dữ liệu, bạn nghĩ rằng các ORM như Hibernate sẽ thuộc về layer nào?

Đầu tiên, hãy đi thẳng vào vấn đề: Không có thứ gì gọi là một object relational mapper (ORM). Nguyên nhân rất đơn giản: Các đối tượng không phải là các cấu trúc dữ liệu. Ít nhất thì chúng không phải là cấu trúc dữ liệu từ quan điểm của người sử dụng chúng. Người dùng một đối tượng sẽ không thể nhìn thấy dữ liệu, do tất cả nó đều private. Những người dùng đó chỉ nhìn thấy các method public của đối tượng đó. Vì vậy, từ quan điểm của người dùng, một đối tượng đơn giản là một tập các hoạt động. Ngược lại, một cấu trúc dữ liệu là một tập các biến dữ liệu public không liên quan gì đến hành vi. ORM tốt hơn nên được đặt tên là “data mapper” bởi vì chúng nạp dữ liệu vào các cấu trúc dữ liệu từ các bảng cơ sở dữ liệu liên quan (relational database).

Các hệ thống ORM nên được coi là nằm ở đâu? Dĩ nhiên là trong layer cơ sở dữ liệu. Quả thực, ORM tạo thành một dạng khác của ranh giới Humble Object giữa các gateway interface và cơ sở dữ liệu

## Service Listeners
Thế còn về các dịch vụ thì sao? Nếu ứng dụng của bạn buộc phải liên lạc với các dịch vụ khác, hoặc nếu ứng dụng của bạn cung cấp một tập các dịch vụ, thì chúng ta sẽ thấy mẫu thiết kế Humble Object tạo ra một ranh giới dịch vụ chứ?

Dĩ nhiên! Ứng dụng đó sẽ nạp dữ liệu vào trong các cấu trúc dữ liệu đơn giản và sau đó truyền cấu trúc đó qua ranh giới tới module định dạng dữ liệu và gửi nó tới các dịch vụ bên ngoài. Ở phía đầu vào, các bộ lắng nghe dịch vụ (service listener) sẽ nhận dữ liệu từ interface dịch vụ và định dạng nó thành một cấu trúc dữ liệu đơn giản mà có thể được ứng dụng sử dụng. Cấu trúc dữ liệu đó sau đó được truyền qua ranh giới dịch vụ.

## Conclusion 
Ở mỗi ranh giới kiến trúc, chúng ta sẽ thấy mẫu thiết kế Humble Object nằm ở đâu đó. Sự liên lạc qua ranh giới đó sẽ hầu như luôn liên quan tới một vài dạng cấu trúc dữ liệu đơn giản, và ranh giới đó sẽ thường phân chia những thứ khó kiểm tra khỏi những thứ dễ kiểm tra. Việc sử dụng mẫu thiết kế này tại các ranh giới kiến trúc làm tăng đáng kể khả năng kiểm tra được của toàn bộ hệ thống.

