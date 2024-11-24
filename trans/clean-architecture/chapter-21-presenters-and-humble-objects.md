# Chapter 21 : Streaming Architecture
------------------

Hãy tưởng tượng rằng bạn đang nhìn vào bản thiết kế của một tòa nhà. Tài liệu này được một kiến trúc sư chuẩn bị, và nó cung cấp cho bạn kế hoạch chi tiết để xây dựng. Vậy kế hoạch này nói cho bạn điều gì?

Nếu kế hoạch mà bạn đang xem là dành cho căn hộ của một gia đình thì bạn sẽ thấy một lối vào ở phía trước, tiền sảnh dẫn vào phòng khách, và có lẽ là một phòng ăn. Bếp sẽ cách không xa, gần với phòng ăn. Có lẽ sẽ có một khu vực nhỏ ngay cạnh nhà bếp, và có lẽ là một phòng sinh hoạt gia đình sẽ gần ngay đó. Khi bạn nhìn vào bản thiết kế đó, không có gì phải bàn cãi là bạn đang nhìn thấy ngôi nhà của một gia đình. Kiến trúc đó đã nói lên: “GIA ĐÌNH”.

Bây giờ cho là bạn đang nhìn vào kiến trúc của một thư viện. Bạn sẽ thấy một cổng vào lớn, một khu vực để kiểm soát vào/ra, các khu vực đọc sách, các phòng hội thảo nhỏ, và hết phòng này đến phòng khác chứa các giá sách cho tất cả các sách có trong thư viện. Kiến trúc đó đã nói lên: “THƯ VIỆN”.

Vậy thì kiến trúc ứng dụng của bạn nói lên điều gì? Khi bạn nhìn vào cấu trúc thư mục cấp trên cùng, và các file mã nguồn trong package cấp cao nhất, chúng có nói lên đó là “Hệ thống chăm sóc sức khỏe”, hoặc “Hệ thống kế toán”, hoặc “Hệ thống quản lý kho” không? Hay là chúng có nói lên “Rails”, hoặc “Spring/Hibernate”, hoặc là “ASP” không?

## The theme of an architecture
Quay trở lại và đọc cuốn sách của Ivar Jacobson về kiến trúc phần mềm: Kỹ Thuật Phần Mềm Hướng Đối Tượng (Object Oriented Software Engineering). Lưu ý phụ đề của cuốn sách: Cách Tiếp Cận Theo Use Case (Use Case Driven Approach). Trong cuốn sách này, Jacobson đưa ra quan điểm rằng kiến trúc phần mềm là cấu trúc để hỗ trợ các use case của hệ thống. Cũng như bản thiết kế cho một ngôi nhà hoặc một thư viện sẽ nói lên về các use case của tòa nhà đó, kiến trúc của một ứng dụng phần mềm cũng cần phải nói lên về các use case của ứng dụng đó.

Các kiến trúc không phải (hay không nên) là các framework. Kiến trúc không nên được cung cấp bởi các framework. Các framework là các công cụ được sử dụng, không phải là kiến trúc để phải tuân thủ theo. Nếu kiến trúc của bạn dựa trên các framework thì nó không thể dựa trên các use case của bạn.

## The purpose of an architecture
Kiến trúc tốt tập trung vào các use case sao cho kiến trúc sư có thể mô tả cấu trúc đó để hỗ trợ các use case mà không phải ủy thác cho các framework, các công cụ và môi trường. Lại một lần nữa, hãy xem bản thiết kế của một ngôi nhà. Vấn đề quan tâm đầu tiên của kiến trúc sư là đảm bảo rằng ngôi nhà có thể sử dụng được – không phải là đảm bảo ngôi nhà được làm từ gạch. Quả thực, kiến trúc sư rất nỗ lực để đảm bảo rằng chủ nhân ngôi nhà có thể tự đưa ra các quyết định về vật liệu bên ngoài (gạch, đá, hoặc gỗ) sau này, sau khi bản thiết kế đảm bảo tất cả các use case đã thỏa mãn.

Một kiến trúc sư phần mềm tốt cho phép các quyết định về framework, cơ sở dữ liệu, máy chủ web, và các vấn đề môi trường khác và các công cụ có thể được trì hoãn và đưa ra trễ nhất có thể. Framework là các lựa chọn được để mở. Một kiến trúc tốt giúp nó không cần thiết phải quyết định sử dụng Rail, hoặc Spring, hoặc Hibernate, hoặc Tomcat, hoặc MySQL cho đến mãi về sau của dự án. Một kiến trúc tốt cũng sẽ giúp bạn dễ dàng thay đổi về những quyết định này. Một kiến trúc tốt sẽ nhấn mạnh các use case và tách rời chúng khỏi các vấn đề bên ngoài.

## But what about the web ?
Web có phải là một kiến trúc hay không? Thực tế hệ thống của bạn được phát hành trên web có thể hiện kiến trúc hệ thống của bạn không? Dĩ nhiên là không! Web là một cơ chế phát hành – một thiết bị IO – và kiến trúc ứng dụng của bạn nên đối xử với nó như vậy. Thực tế là ứng dụng của bạn được phát hành qua web là một chi tiết và không nên làm lấn át cấu trúc hệ thống của bạn. Quả thực, quyết định về việc ứng dụng của bạn sẽ được phát hành qua web là một trong những điều bạn nên trì hoãn lại. Kiến trúc hệ thống của bạn không nên quan tâm về việc nó sẽ được phát hành như thế nào. Bạn nên có thể phát hành nó dưới dạng một ứng dụng console, hoặc một ứng dụng web, hoặc một ứng dụng desktop, hoặc thậm chí là một ứng dụng dịch vụ web, mà không tạo ra những thay đổi phức tạp đối với kiến trúc cơ bản.

## Frameworks are tools, not ways of line
Framework có thể rất mạnh mẽ và rất hữu dụng. Các tác giả của framework thường tin tưởng rất sâu sắc đối với framework của họ. Các ví dụ họ viết về cách sử dụng framework của họ đã cho thấy quan điểm của một người tin tưởng thực sự. Các tác giả khác viết về framework đó cũng thường là các tín đồ chân chính của nó. Họ cho bạn thấy cách sử dụng framework. Họ thường coi hãy để framework đó chứa đựng tất cả, lan tỏa tất cả, làm tất cả mọi thứ cho các ứng dụng

> This it not the position you want to take.

Bạn hãy nhìn các framework này với một ánh mắt cảnh giác. Nhìn nó một cách hoài nghi. Đúng, nó có thể hữu ích, nhưng giá phải trả là gì? Hãy tự hỏi về cách bạn sử dụng nó, và cách bạn bảo vệ chính mình khỏi nó. Hãy nghĩ về cách bạn có thể bảo toàn được tầm quan trọng của use case trong kiến trúc của bạn. Hãy phát triển một chiến thuật để ngăn cho framework đó lấn át kiến trúc của bạn.


## Testable architectures
Nếu toàn bộ kiến trúc hệ thống của bạn là các use case, và nếu bạn phải sử dụng framework thì bạn cần phải có thể unit test tất cả những use case đó mà không cần có sự hiện diện của framework đó. Bạn không nên cần một máy chủ web đang hoạt động để chạy các bài kiểm tra của bạn. Bạn không nên cần kết nối tới cơ sở dữ liệu để chạy được các bài kiểm tra của bạn. Các đối tượng Entity của bạn nên là những đối tượng thô mà không có bất cứ phụ thuộc nào với framework hoặc với cơ sở dữ liệu hoặc với những thứ phức tạp nào khác. Các đối tượng use case của bạn nên phối hợp với các đối tượng Entity của bạn. Cuối cùng, tất cả chúng cần phải kiểm tra được tại chỗ mà không cần có bất cứ sự phức tạp nào của framework

## Conclusion

Kiến trúc của bạn cần phải nói với người đọc về hệ thống đó, không phải là về framework mà bạn đã dùng trong hệ thống của bạn. Nếu bạn đang xây dựng một hệ thống chăm sóc sức khỏe, thì khi một lập trình viên mới nhìn vào kho chứa mã nguồn, thì điều ấn tượng đầu tiên của họ phải là “Ồ, đây là một hệ thống chăm sóc sức khỏe.” Những lập trình viên mới này cần có thể học được tất cả các use case của hệ thống, mặc dù vẫn không biết hệ thống đó được phát hành như thế nào. Họ có thể tới gặp bạn và nói:

> "We see some things that look like models - but where are the views and controllers ?"

Và bạn nên đáp lại:

> "Oh, those are details that needn't concern us the moment. We will decide about them l
