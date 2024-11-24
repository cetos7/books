# Chapter 28 : The test boundary
-----------------------

Vâng, điều đó đúng: Các bài kiểm tra là một phần của hệ thống, và chúng góp phần trong kiến trúc cũng giống như mọi thành phần khác của hệ thống. Trong một vài trường hợp, sự góp phần đó khá bình thường. Trong các trường hợp khác, nó có thể khá đặc biệt.

## Tests as system components
Có rất nhiều điều mơ hồ về các bài kiểm tra. Chúng có phải là một phần của hệ thống không? Chúng có tách biệt khỏi hệ thống không? Có những loại kiểm tra nào? Các bài unit test và integration test (kiểm tra tích hợp) là những thứ khác nhau phải không? Thế về các acceptance test (kiểm tra chấp thuận), functional test (kiểm tra chức năng), Cucumber test, TDD test, BDD test, component test.v.v. thì sao?

Cuốn sách này không có ý định lôi mọi người vào cuộc tranh luận đó, và thật may mắn là nó không cần thiết. Từ quan điểm kiến trúc, tất cả các bài kiểm tra đều giống nhau. Cho dù chúng là các bài kiểm tra siêu nhỏ được tạo bởi TDD, hoặc các bài kiểm tra lớn FitNesse, Cucumber, SpecFlow, hoặc Jbehave, chúng đều tương đương nhau về kiến trúc.

Bản chất các bài kiểm tra là tuân theo Quy Tắc Phụ Thuộc; chúng rất chi tiết và cụ thể; và chúng luôn phụ thuộc hướng vào trong code đang được kiểm tra. Thực tế, bạn có thế nghĩ các bài kiểm tra này là vòng tròn ngoài cùng trong kiến trúc. Không gì bên trong hệ thống phụ thuộc vào các bài kiểm tra, và các bài kiểm tra luôn phụ thuộc vào các component của hệ thống.

Các bài kiểm tra cũng có thể triển khai độc lập được. Thực tế, phần lớn thời gian chúng được triển khai trong các hệ thống kiểm tra, hơn là các hệ thống sản phẩm. Vì vậy, thậm chí ở trong các hệ thống không cần triển khai độc lập, thì các bài kiểm tra vẫn sẽ được triển khai độc lập.

Các bài kiểm tra là component hệ thống tách biệt nhất. Chúng không cần thiết cho sự vận hành hệ thống. Không ai phụ thuộc vào chúng. Vai trò của chúng là để hỗ trợ cho việc phát triển, không phải cho việc vận hành. Chưa hết, chúng là một thành phần hệ thống không kém gì so với bất kỳ thành phần nào khác. Trên thực tế, bằng nhiều cách chúng biểu diễn cho mô hình mà tất cả các component hệ thống khác phải tuân theo.

## Design for testabiliy

Sự tách biệt cực kỳ của các bài kiểm tra, kết hợp với thực tế là chúng thường không được triển khai, thường khiến cho các lập trình viên nghĩ rằng các bài kiểm tra nằm bên ngoài thiết kế của hệ thống. Đây là một quan điểm chết người. Các bài kiểm tra không được tích hợp tốt với thiết kế của hệ thống có khuynh hướng không vững chắc, và chúng làm cho hệ thống cứng nhắc và khó có thể thay đổi.

Dĩ nhiên vấn đề này là sự gắn kết. Các bài kiểm tra bị gắn kết chặt với hệ thống buộc phải thay đổi cùng với hệ thống. Thậm chí những thay đổi đơn giản nhất tới một component hệ thống cũng có thể khiến cho rất nhiều các bài kiểm tra bị fail hoặc yêu cầu phải thay đổi.

Tình huống này có thể trở nên cấp tính. Những thay đổi tới các component hệ thống chung có thể gây ra hàng trăm, hoặc thậm chí hàng nghìn các bài kiểm tra bị fail. Đây được biết đến là Vấn đề các bài kiểm tra mong manh (Fragile Tests Problem).

Không khó để thấy vấn đề này sẽ có thể xảy ra như thế nào. Lấy ví dụ, hãy tưởng tượng một bộ các bài kiểm tra dùng GUI để xác nhận các quy tắc nghiệp vụ. Các bài kiểm tra như vậy có thể bắt đầu trên màn hình đăng nhập và sau đó chuyển qua cấu trúc các trang cho đến khi chúng có thể kiểm tra các quy tắc nghiệp vụ cụ thể. Bất cứ thay đổi nào tới trang đăng nhập, hoặc cấu trúc chuyển trang đều có thể khiến cho một lượng khổng lồ các bài kiểm tra bị fail.

Các bài kiểm tra mong manh thường có hiệu ứng bảo toàn làm cho hệ thống trở nên cứng nhắc. Khi các lập trình viên nhận ra rằng những thay đổi đơn giản tới hệ thống cũng có thể khiến cho một lượng lớn các bài kiểm tra bị fail, thì họ có thể sẽ không muốn thay đổi. Lấy ví dụ, hãy tưởng tượng cuộc đối thoại giữa đội phát triển và đội marketing yêu cầu một thay đổi đơn giản tới cấu trúc chuyển trang sẽ khiến cho 1000 bài kiểm tra bị fail.

Giải pháp là hãy thiết kế để có thể kiểm tra được. Quy tắc đầu tiên của thiết kế phần mềm luôn luôn giống nhau dù cho mục đích kiểm tra được hay cho bất cứ lý do nào khác: Không được phụ thuộc vào những thứ dễ thay đổi. GUI là thứ dễ thay đổi. Các bộ kiểm tra vận hành hệ thống thông qua GUI chắc chắn là dễ fail. Do đó thiết kế hệ thống, và các bài kiểm tra, sao cho các quy tắc nghiệp vụ có thể được kiểm tra mà không cần sử dụng GUI.

## The testing API
Cách để đạt được mục tiêu này là tạo ra một API cụ thể mà các bài kiểm tra có thể dùng để xác nhận tất cả các quy tắc nghiệp vụ. API này nên có “siêu quyền lực” cho phép các bài kiểm tra không bị ràng buộc bởi bảo mật, tránh các tài nguyên tốn kém (như cở sở dữ liệu), và buộc hệ thống trong trạng thái có thể kiểm tra được. API này sẽ là một tập hợp cha của bộ các interactor và interface adapter được sử dụng bởi giao diện người dùng.

Mục đích của API kiểm tra là tách rời các bài kiểm tra khỏi ứng dụng. Việc tách rời này không chỉ tách các bài kiểm tra với UI: Mục tiêu là tách rời cấu trúc các bài kiểm tra khỏi cấu trúc của ứng dụng.

### Structural Coupling
Gắn kết cấu trúc là một trong những dạng gắn kết kiểm tra khỏe nhất và dai dẳng nhất. Hãy tưởng tượng một bộ kiểm tra có một lớp kiểm tra cho mọi lớp sản phẩm (production class), và một bộ các method kiểm tra cho mọi method sản phẩm (production method). Một bộ kiểm tra như vậy bị gắn kết sâu sắc đối với cấu trúc của ứng dụng.

Khi một trong những method hoặc lớp sản phẩm bị thay đổi, thì một số lượng lớn các bài kiểm tra cũng sẽ buộc phải thay đổi. Hệ quả là các bài kiểm tra dễ fail, và chúng làm cho code sản phẩm trở nên cứng nhắc.

Vai trò của API kiểm tra là ẩn đi cấu trúc của ứng dụng khỏi các bài kiểm tra. Điều này cho phép code sản phẩm được refactor lại và phát triển theo nhiều cách mà không ảnh hưởng đến các bài kiểm tra. Nó cũng cho phép các bài kiểm tra được refactor và phát triển theo nhiều cách mà không ảnh hưởng đến code sản phẩm.

Sự tách biệt khi phát triển này là cần thiết bởi vì khi thời gian trôi qua, các bài kiểm tra có khuynh hướng trở nên cụ thể hơn. Ngược lại, code sản phẩm có khuynh hướng trở nên trừu tượng và tổng quát hơn. Việc gắn kết cấu trúc quá chặt sẽ ngăn chặn – hoặc ít nhất là cản trở – sự phát triển cần thiết này, và ngăn code sản phẩm được trở nên tổng quan và linh động.

### Security
“Siêu quyền lực” của API kiểm tra có thể rất nguy hiểm nếu chúng được triển khai trong các hệ thống sản phẩm. Nếu đây là một vấn đề, thì API kiểm tra, và các phần nguy hiểm của nó cần phải được giữ trong một component tách riêng, có thể triển khai độc lập.


## Conclusion
Các bài kiểm tra không nằm ngoài hệ thống; đúng hơn là chúng là một phần của hệ thống và phải được thiết kế tốt nếu chúng cung cấp được các lợi ích về sự ổn định và hồi quy mong muốn. Các bài kiểm tra không được thiết kế như là một phần của hệ thống sẽ có khuynh hướng dễ fail và khó có thể bảo trì được. Những bài kiểm tra thường bị bỏ quên trong quá trình bảo trì – bị loại bỏ vì chúng quá khó để bảo trì được.

