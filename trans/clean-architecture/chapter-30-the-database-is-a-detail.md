# Chapter 30 : The database is a detail
----------------------

Từ quan điểm kiến trúc, cơ sở dữ liệu không phải là một thực thể – mức độ chi tiết của nó không tới mức của một thành phần kiến trúc. Mối quan hệ của nó tới kiến trúc của một hệ thống phần mềm giống mối quan hệ của một tay nắm cửa với kiến trúc của ngôi nhà hơn.

Tôi nhận ra rằng đây có thể là những lời gây chiến. Tin tôi đi, tôi đã có một cuộc chiến. Vì vậy hãy để tôi làm rõ: Tôi không nói về mô hình dữ liệu. Cấu trúc mà bạn đưa dữ liệu vào trong ứng dụng có ý nghĩa rất lớn tới kiến trúc của hệ thống của bạn. Nhưng cơ sở dữ liệu không phải là mô hình dữ liệu. Cơ sở dữ liệu là một phần của phần mềm. Cơ sở dữ liệu là một tiện ích cung cấp khả năng truy xuất tới dữ liệu. Từ quan điểm của kiến trúc, tiện ích đó không liên quan bởi vì nó là một chi tiết cấp thấp – một cơ chế. Và một kiến trúc sư tốt không cho phép các cơ chế cấp thấp lan tràn trong kiến trúc hệ thống.


## Relational Database
Edgar Codd đã định nghĩa các nguyên lý của cơ sở dữ liệu liên hệ (relational database) vào năm 1970. Đến giữa những năm 1980, mô hình liên hệ đã phát triển để trở thành dạng thống trị của việc lưu trữ dữ liệu. Có nhiều lý do tốt đẹp dẫn tới việc phổ biến này:

Mô hình liên hệ rất gọn gàng, có quy tắc, và bền vững. Nó là một công nghệ truy xuất và lưu trữ dữ liệu hoàn hảo.

Nhưng dù công nghệ đó có rực rỡ, hữu dụng, và nghe có vẻ toán học thế nào, thì nó vẫn chỉ là một công nghệ. Và điều đó có nghĩa nó là một chi tiết.

Trong khi các bảng liên hệ có thể thuận tiện cho một số dạng truy xuất dữ liệu nhất định, thì việc sắp xếp dữ liệu thành các hàng trong các bảng không có ý nghĩa kiến trúc quan trọng. Các use case của ứng dụng của bạn không nên biết hay quan tâm về những vấn đề như vậy. Thực vậy, các thông tin về cấu trúc bảng của dữ liệu phải được giới hạn cho những hàm tiện ích cấp thấp nhất ở các vòng tròn ngoài của kiến trúc này.

Nhiều framework truy cập dữ liệu cho phép các hàng và bảng dữ liệu được chuyển trong hệ thống như là những đối tượng. Việc cho phép như vậy là một sai lầm trong kiến trúc. Nó gắn kết các use case, các quy tắc nghiệp vụ, và thậm chí trong một số trường hợp là cả UI với cấu trúc quan hệ của dữ liệu.

## Why are databse systems so prevalent ?
Tại sao các hệ thống phần mềm và các doanh nghiệp phần mềm bị thống trị bởi các hệ thống cơ sở dữ liệu? Điều gì giải thích cho sự vượt trội của Oracle, MySQL, và SQL Server? Chỉ có một từ duy nhất: ổ đĩa cứng.

Ổ đĩa từ quay là phương tiện lưu trữ chính trong năm thập kỷ. Nhiều thế hệ lập trình viên không có sự lựa chọn nào khác về thiết bị lưu trữ. Công nghệ đĩa cứng đã phát triển từ những chồng đĩa khổng lồ đường kính 48 inch (xấp xỉ 1.2m) nặng hàng nghìn pound và lưu trữ được 20 megabyte, cho tới các đĩa mỏng, đường kính 3 inch, chỉ nặng vài gram và có thể lưu trữ hàng terabyte dữ liệu hoặc hơn nữa. Đó là cả một quãng đường dài. Và trong suốt quá trình đó, các lập trình viên đã bị cản trở bởi một nhược điểm chết người của công nghệ đĩa: Các đĩa cứng rất chậm.

Trên một đĩa cứng, dữ liệu được lưu trữ trong các rãnh tròn (circular track). Những track này được chia thành các sector mà có thể lưu trữ được một số lượng byte nhất định, thường là 4K. Mỗi đĩa có thể có hàng trăm rãnh, và có thể có hàng tá đĩa. Nếu bạn muốn đọc một byte cụ thể nào trên đĩa, bạn phải di chuyển đầu đọc vào đúng rãnh, đợi cho đĩa quay tới đúng sector, đọc tất cả 4K của sector đó vào RAM, và sau đó đánh chỉ số vào trong bộ nhớ đệm RAM để lấy được byte mà bạn muốn. Và tất cả điều đó tốn thời gian – nhiều mili-giây.

Mili-giây nghe không có vẻ như nhiều lắm, nhưng một mili-giây tức là lâu hơn một triệu lần so với chu kỳ của phần lớn các bộ vi xử lý. Nếu dữ liệu không nằm trên ổ đĩa, nó có thể được truy cập chỉ trong nano-giây, thay vì nhiều mili-giây.

Để giảm thiểu độ trễ thời gian do đĩa cứng, bạn cần đặt chỉ mục, bộ nhớ đệm, và các truy vấn được tối ưu hóa; và bạn cần một số dạng phương tiện thông thường để biểu diễn dữ liệu sao cho các chỉ mục, các bộ nhớ đệm, và các truy vấn này biết được chúng đang làm việc với cái gì. Nói ngắn gọn, bạn cần một hệ thống quản lý và truy cập dữ liệu. Trải qua nhiều năm, những hệ thống này được chia thành hai loại riêng biệt: hệ thống file và hệ thống quản lý dữ cơ sở dữ liệu quan hệ (Relational Database Management System – RDBMS).

Các hệ thống file được dựa trên tài liệu. Chúng cung cấp một cách tự nhiên và thuận tiện để lưu trữ toàn bộ tài liệu. Chúng hoạt động tốt khi bạn cần lưu trữ và lấy một bộ các tài liệu bởi tên gọi, nhưng chúng không cung cấp nhiều tiện ích khi bạn tìm kiếm nội dụng của những tài liệu này. Bạn có thể dễ dàng tìm một file tên là login.c, nhưng sẽ khó và chậm chạp khi bạn tìm mọi file .c mà có một biến tên là x trong đó.

Các hệ thống cơ sở dữ liệu được dựa trên nội dung. Chúng cung cấp một cách tự nhiên và thuận tiện để tìm các bản ghi (record) dựa trên nội dung của chúng. Chúng rất tốt để liên kết nhiều bản ghi dựa trên nội dung mà tất cả chúng đều chia sẻ. Nhưng không may thay, chúng lại khá kém trongg việc lưu trữ và truy xuất các tài liệu không rõ ràng.

Cả hai hệ thống này tổ chức dữ liệu trên đĩa cứng sao cho nó có thể được lưu trữ và truy cập theo cách hiệu quả nhất có thể, tùy theo nhu cầu truy cập cụ thể của chúng. Mỗi loại đều có một sơ đồ riêng để đánh chỉ mục và sắp xếp dữ liệu. Ngoài ra, mỗi loại cuối cùng cũng sẽ đưa dữ liệu liên quan vào trong RAM, nơi mà chúng có thể được thao tác nhanh chóng.

## What if there were no disk ?
Đĩa cứng đã từng thịnh hành trước đây, thì bây giờ chúng đang biến mất dần dần. Sớm muộn chúng cũng sẽ ra đi giống như băng từ, đĩa mềm, và đĩa CD. Chúng đang được thay thế bởi RAM.

Hãy hỏi chính mình câu hỏi này: Khi tất cả các đĩa cứng biến mất, và tất cả dữ liệu của bạn được lưu trữ trong RAM, thì bạn sẽ tổ chức dữ liệu đó như thế nào? Bạn sẽ tổ chức nó thành các bảng và truy cập nó bằng SQL chứ? Bạn sẽ tổ chức nó thành các file và truy cập nó qua một thư mục chứ?

Dĩ nhiên là không. Bạn sẽ sắp xếp nó thành các linked list (danh sách liên kết), tree (cây), hash table (bảng băm), stack (chồng), queue (hàng đợi), hoặc bất cứ cấu trúc dữ liệu nào khác, và bạn sẽ truy cập nó dùng các con trỏ hoặc tham chiếu – bởi vì đó là những gì các lập trình viên làm.

Quả thực là nếu bạn nghĩ cẩn thận về vấn đề này, bạn sẽ nhận ra rằng đây là thứ mà bạn đã làm. Mặc dù dữ liệu được lưu trữ trong một cơ sở dữ liệu hoặc một hệ thống file, nhưng bạn vẫn đọc nó vào RAM và sau đó bạn tổ chức lại nó thành các list, set, stack, queue, tree hay bất cứ cấu trúc dữ liệu nào thuận tiện cho bạn. Bạn sẽ không để dữ liệu ở dạng file hay dạng bảng.

## Details
Thực tế này là lý do tại sao tôi nói cơ sở dữ liệu là một chi tiết. Nó chỉ là một cơ chế chúng ta dùng để di chuyển dữ liệu qua lại giữa bề mặt của đĩa cứng và RAM. Cơ sở dữ liệu thực sự không có gì khác ngoài một thùng lớn chứa các bit, nơi mà chúng ta lưu trữ dữ liệu của mình lâu dài. Nhưng chúng ta hiếm khi dùng dữ liệu ở dạng đó.

Do vậy, từ quan điểm kiến trúc, chúng ta không nên quan tâm về dạng của dữ liệu xem nó trên bề mặt của một đĩa từ quay hay không. Thực vậy, chúng ta không nên thừa nhận rằng đĩa cứng tồn tại.


## But what about performance ? 
Hiệu năng có phải là một vấn đề quan tâm trong kiến trúc không? Dĩ nhiên là có – nhưng khi nói tới việc lưu trữ dữ liệu, thì vấn đề đó có thể được đóng gói lại toàn bộ và tách biệt khỏi các quy tắc nghiệp vụ. Đúng, chúng ta cần lấy dữ liệu vào và ra khỏi thiết bị lưu trữ dữ liệu một cách nhanh chóng, nhưng đó là một vấn đề quan tâm ở cấp thấp. Chúng ta có thể giải quyết vấn đề đó với các cơ chế truy cập dữ liệu cấp thấp. Nó không liên quan gì đến kiến trúc tổng thể của hệ thống của chúng ta.

## Anecdote
Vào cuối những năm 1980, tôi làm trưởng nhóm phần mềm tại một công ty khởi nghiệp, đang cố gắng xây dựng và cho ra thị trường một hệ thống quản lý mạng có thể đo đạc được tính toàn vẹn liên lạc của các đường dây viễn thông T1. Hệ thống này lấy dữ liệu từ các thiết bị ở đầu cuối của những đường truyền đó, và sau đó chạy một chuỗi các thuật toán dự đoán để phát hiện và báo cáo các vấn đề.

Chúng tôi sử dụng nền tảng UNIX, và chúng tôi lưu trữ dữ liệu của mình trong các file truy cập ngẫu nhiên đơn giản. Chúng tôi không cần cơ sở dữ liệu quan hệ bởi vì dữ liệu của chúng tôi có rất ít mối quan hệ giữa các nội dung. Tốt hơn là lưu nó trong các tree và linked list trong những file truy cập ngẫu nhiên này. Nói ngắn gọn, chúng ta lưu dữ liệu ở dạng mà thuận tiện nhất để nạp vào RAM nơi mà nó có thể được thao tác.

Chúng tôi đã thuê một quản lý marketing cho dự án khởi nghiệp này – một anh chàng am hiểu và tốt bụng. Nhưng anh ấy ngay lập tức đã nói với tôi rằng chúng tôi phải có một cơ sở dữ liệu quan hệ trong hệ thống này. Đó không phải là một lựa chọn và cũng không phải là một vấn đề về kỹ thuật – nó là một vấn đề về marketing.

Điều này chả có nghĩa gì đối với tôi. Tại sao tôi lại muốn sắp xếp lại các linked list và tree của tôi thành một đống các hàng và bảng được truy cập qua SQL? Tại sao tôi lại phải sử dụng tất cả những lãng phí và đắt đỏ của một hệ thống RDBMS lớn khi chỉ cần một hệ thống file truy cập ngẫu nghiên đơn giản là đủ? Vì vậy tôi đã đấu tranh với anh ta, bằng cả miệng và tay chân.

Chúng tôi có một kỹ sư phần cứng tại công ty này, người đã đảm nhận thánh ca RDBMS đó. Anh ta được thuyết phục rằng hệ thống phần mềm của chúng tôi cần một RDBMS vì các lý do kỹ thuật. Anh ta tổ chức các cuộc họp với ban lãnh đạo công ty sau lưng tôi, vẽ ra các hình cây gậy trên bảng trắng với một ngôi nhà nằm thăng bằng trên một cái cột, và anh ta hỏi các vị lãnh đạo đó, “Chúng ta sẽ xây một ngôi nhà trên một cái cột chứ?”. Anh ta ám chỉ thông điệp là một RDBMS lưu giữ các bảng của nó trong các file truy cập ngẫu nhiên thì có thể đáng tin cậy hơn các file truy cập ngẫu nhiên mà chúng tôi đang sử dụng.

Tôi đã chiến đấu với anh ta. Tôi đã chiến đấu với anh chàng marketing. Tôi mắc kẹt với các nguyên tắc kỹ thuật của mình khi phải đối mặt với sự thiếu hiểu biết đang kinh ngạc đó. Tôi đã chiến đấu, và chiến đấu, và chiến đấu.

Cuối cùng, tay lập trình viên phần cứng đã được thăng chức lên thay tôi trở thành quản lý dự án phần mềm này. Cuối cùng, họ đã đặt một RDBMS vào hệ thống tội nghiệp đó. Và, cuối cùng, họ đã hoàn toàn đúng và tôi đã sai.

Không phải vì lý do kỹ thuật, hãy nhớ rằng: Tôi đã đúng về điều đó. Tôi đã đúng khi chống lại việc đưa một RDBMS vào trong lõi kiến trúc của hệ thống. Nguyên nhân tôi đã sai là bởi vì các khách hàng của chúng tôi mong muốn chúng tôi có một cơ sở dữ liệu quan hệ. Họ không hề biết họ sẽ làm gì với nó. Họ không có bất cứ cách thực tế nào sử dụng dữ liệu quan hệ đó trong hệ thống của chúng tôi. Nhưng đó không thành vấn đề: Các khách hàng của chúng tôi hoàn toàn mong đợi một RDBMS. Nó đã trở thành một hạng mục mà tất cả những người mua phần mềm có trong danh sách của họ. Không hề có cơ sở lý luận – hợp lý gì về mặt kỹ thuật. Đó chỉ là một nhu cầu phi lý, hoàn toàn vô căn cứ, nhưng nó không kém phần thực tế.

Nhu cầu đó đến từ đâu? Nó xuất phát từ các chiến dịch marketing cực kỳ hiệu quả được triển khải bởi các nhà cung cấp cơ sở dữ liệu vào thời điểm đó. Họ đã thuyết phục được các lãnh đạo cấp cao rằng “tài sản dữ liệu” doanh nghiệp của họ cần được bảo vệ, và các hệ thống cơ sở dữ liệu mà họ cung cấp là một phương tiện lý tưởng cho sự bảo vệ đó.

Chúng ta có thể nhìn thấy các chiến dịch marketing dạng tương tự ngày nay. Từ “enterprise” và thuật ngữ “Kiến Trúc Hướng Dịch Vụ” (Service-Oriented Architecture) liên quan nhiều đến hoạt động marketing hơn là thực tế.

Tôi phải làm gì trong tình huống hồi đó? Tôi có nên gắn chặt một RDBMS ở một phía của hệ thống và cung cấp một kênh truy cập dữ liệu an toàn và hạn hẹp nào đó tới nó, đồng thời vẫn duy trì các file truy cập ngẫu nhiên trong lõi của hệ thống đó không? Điều mà tôi đã làm ư? Tôi đã nghỉ việc và trở thành một nhà tư vấn.


## Conclusion
Cấu trúc tổ chức dữ liệu, mô hình dữ liệu có ý nghĩa về mặt kiến trúc. Các công nghệ và các hệ thống di chuyển dữ liệu vào và ra khỏi bề mặt đĩa từ quay thì không phải như vậy. Các hệ thống cơ sở dữ liệu quan hệ buộc dữ liệu được sắp xếp thành các bảng và truy cập bằng các câu lệnh SQL liên quan nhiều tới cái sau hơn là cái trước. Dữ liệu là thứ quan trọng. Còn cơ sở dữ liệu thì chỉ là một chi tiết.

