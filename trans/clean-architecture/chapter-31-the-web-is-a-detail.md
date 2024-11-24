# Chapter 31 : The web is a detail
-----------------------

Bạn là một lập trình viên vào những năm 1990? Bạn có nhớ cách mà web đã thay đổi mọi thứ không? Bạn có nhớ cách chúng ta nhìn vào kiến trúc client-server (máy khách-máy chủ) cũ rích của chúng ta với cái nhìn khinh bỉ khi đối diện với công nghệ mới đang tỏa sáng đó là Web không?

Thực tế là web không thay đổi bất cứ điều gì. Hay, ít nhất là nó không nên như vậy. Web chỉ là công nghệ mới nhất trong một loạt các dao động trong ngành công nghiệp của chúng ta đã đi qua từ những năm 1960. Sự thay đổi này di chuyển tới lui giữa việc đặt tất cả sức mạnh tính toán trong các máy chủ trung tâm và việc đặt tất cả sức mạnh tính toán tại các đầu cuối.

Chúng ta đã nhìn thấy một vài trong số những thay đổi này chỉ trong khoảng một thập kỷ gần đây kể từ khi web trở nên nổi bật. Lúc đầu, chúng ta đã nghĩ rằng tất cả sức mạnh tính toán nên đặt trong các trung tâm máy chủ, và các trình duyệt web là thứ ngu ngốc. Sau đó chúng ta đã bắt đầu đặt các applet trong các trình duyệt web. Nhưng chúng ta không thích điều đó, vì vậy chúng ta đã di chuyển nội dung động trở lại các máy chủ. Nhưng sau đó chúng ta lại không thích như vậy, vì vậy chúng ta đã sáng tạo ra Web 2.0 và di chuyển rất nhiều việc xử lý trở lại các trình duyệt web bằng Ajax và JavaScript. Chúng ta đã đi quá xa khi tạo ra những ứng dụng khổng lồ được viết để thực thi trong các trình duyệt web. Và bây giờ tất cả chúng ta đều thích thú khi kéo phần JavaScript đó trở về máy chủ bằng Node.

## The endless pendulum

Dĩ nhiên, không chính xác khi nghĩ rằng sự dao động này bắt đầu bởi web. Trước khi có web, chúng ta có kiến trúc client-server. Trước đó, chúng ta có các máy tính mini trung tâm với những dãy thiết bị đầu cuối câm (dumb terminal). Trước đó nữa, chúng ta có các máy mainframe với các thiết bị đầu cuối màn hình xanh lục thông minh (nó cũng rất giống với các trình duyệt web hiện đại). Trước đó nữa, chúng ta có các phòng máy tính và các thẻ đục lỗ…

Và câu truyện cứ thế tiếp diễn. Chúng ta dường như không thể hình dung ra nơi mà chúng ta muốn đặt sức mạnh tính toán. Chúng ta đi tới đi lui giữa việc tập trung và phân tán nó. Và tôi tưởng tượng rằng việc dao động này sẽ tiếp tục trong khoảng thời gian sắp tới.

Khi bạn nhìn vào điều đó trong tổng thể lịch sử của ngành IT, thì web không làm thay đổi bất cứ thứ gì. Web chỉ đơn giản là một trong nhiều dao động trong cuộc tranh đấu đã bắt đầu trước khi phần lớn chúng ta được sinh ra và sẽ tiếp tục sau khi phần lớn chúng ta đã nghỉ hưu.

Mặc dù, với vai trò là các kiến trúc sư, chúng ta phải có cái nhìn dài hạn. Sự dao động đó chỉ là các vấn đề ngắn hạn mà chúng ta muốn đẩy ra xa khỏi lõi trung tâm của các quy tắc nghiệp vụ của chúng ta.

Hãy để tôi nói cho bạn câu truyện về công ty Q. Công ty Q xây dựng một hệ thống tài chính cá nhân rất phổ biến. Đó là một ứng dụng desktop (máy để bàn) với một giao diện rất hữu dụng. Tôi đã rất thích sử dụng nó.

Sau đó đến thời của web. Trong lần phát hành tiếp theo, công ty Q đã thay đổi GUI để trông và hoạt động như một trình duyệt web. Tôi đã sững sờ! Thiên tài marketing nào đã quyết định một phần mềm tài chính cá nhân, chạy trên máy để bàn, lại phải có cảm giác như một trình duyệt web như vậy?

Dĩ nhiên, tôi ghét giao diện mới này. Hầu như mọi người khác cũng vậy – bởi vì sau một vài lần phát hành, công ty Q đã dần dần loại bỏ giao diện trình duyệt web và chuyển hệ thống tài chính cá nhân của nó trở về giao diện desktop thông thường.

Bây giờ hãy tưởng tượng bạn là một kiến trúc sư phần mềm tại Q. Hãy tưởng tượng một thiên tài marketing nào đó đã thuyết phục các quản lý cấp cao rằng toàn bộ UI phải thay đổi để trông giống như web. Bạn sẽ phải làm gì đây? Hay đúng hơn là bạn phải làm gì để bảo vệ ứng dụng của bạn khỏi thiên tài marketing đó?

Bạn nên tách rời các quy tắc nghiệp vụ của bạn khỏi phần UI. Tôi không biết là các kiến trúc sư của Q có làm như vậy không. Tôi mong một ngày sẽ nghe được câu truyện của họ. Nếu tôi ở đó vào thời điểm đó, tôi chắc chắn sẽ nỗ lực vận động hành lang để tách biệt các quy tắc nghiệp vụ khỏi GUI, bởi vì bạn sẽ không bao giờ biết được thiên tài marketing đó sẽ làm gì tiếp theo.

Bây giờ hãy xem công ty A, công ty tạo ra một dòng điện thoại thông minh đáng yêu. Gần đây nó đã phát hành một phiên bản nâng cấp “hệ điều hành” của chính nó (thật lạ là chúng ta có thể nói về hệ điều hành bên trong một chiếc điện thoai). Trong nhiều thứ, “hệ điều hành” đó đã thay đổi hoàn toàn giao diện của tất cả các ứng dụng. Tại sao? Tôi cho là có một thiên tài marketing nào đó đã nói như vậy.

Tôi không phải là một chuyên gia phần mềm của thiết bị đó, vì vậy tôi không biết việc thay đổi đó có khiến cho các lập trình viên gặp khó khăn đáng kể để làm cho ứng dụng của họ có thể chạy được trên điện thoại của hãng A không. Tôi hy vọng các kiến trúc sư ở A, và các kiến trúc sư của các ứng dụng, giữ giao diện UI của họ và các quy tắc nghiệp vụ tách biệt nhau, bởi vì ngoài kia luôn có những thiên tài marketing chỉ chờ cơ hội để làm cho code mà bạn tạo ra bị gắn kết chặt với nhau.

## The upshot
Kết luận cuối cùng đơn giản là: GUI là một chi tiết. Web là một dạng GUI. Vì vậy web cũng là một chi tiết. Và, với vai trò là một kiến trúc sư, bạn muốn đặt các chi tiết như vậy phía sau ranh giới mà bạn giữ chúng tách biệt khỏi phần quy tắc nghiệp vụ cốt lõi của bạn.

Hãy nghĩ về nó theo cách này: WEB là một thiết bị IO. Từ những năm 1960, chúng tôi đã học được giá trị của việc viết các ứng dụng mà độc lập với thiết bị. Khi bạn nghĩ về những rắc rối của việc kiểm tra xác nhận JavaScript hoặc các lời gọi AJAX kéo-và-thả, hoặc bất cứ widget và gadget nào khác mà bạn có thể đặt trên một trang web, bạn có thể dễ dàng tranh luận rằng việc độc lập về thiết bị là điều không thực tế.

Điều này đúng ở một khía cạnh nào đó. Sự tương tác giữa ứng dụng và GUI rất nhiều theo các cách khá đặc trưng cho loại GUI mà bạn sử dụng. Việc tương tác giữa một trình duyệt web và một ứng dụng web sẽ khác so với việc tương tác giữa GUI desktop và ứng dụng của nó. Việc cố gắng trừu tượng hóa việc tương tác đó, theo cách các thiết bị đã được trừu tượng hóa khỏi UNIX, dường như không thể thực hiện được.

Nhưng một ranh giới khác giữa UI và ứng dụng có thể được trừu tượng. Quy tắc nghiệp vụ có thể được nghĩ như là một bộ các use case, mỗi cái thực hiện một chức năng nào đó dưới danh nghĩa của một người dùng. Mỗi use case có thể được mô tả dựa trên dữ liệu đầu vào, quá trình xử lý thực hiện, và dữ liệu đầu ra.

Ở một điểm nào đó trong việc tương tác giữa UI và ứng dụng, dữ liệu đầu vào có thể nói là đã hoàn thiện, cho phép use case đó được thực thi. Khi hoàn thành, dữ liệu kết quả có thể được nạp trở lại vào sự tương tác giữa UI và ứng dụng đó.

Dữ liệu đầu vào hoàn thiện và dữ liệu đầu ra kết quả có thể được đặt vào trong các cấu trúc dữ liệu và được sử dụng làm các giá trị đầu vào và giá trị đầu ra cho một quy trình thực thi use case đó. Bằng phương pháp này, chúng ta có thể xem mỗi use case đang vận hành thiết bị IO của UI theo một cách độc lập với thiết bị.


## Conclusion
Loại trừu tượng này không dễ, và có thể sẽ mất vài lần lặp lại thì mới đúng. Nhưng nó có thể thực hiện được. Và vì thế giới này đầy rẫy những thiên tài marketing, nên không khó để đưa ra trường hợp mà nó thường sẽ trở thành rất cần thiết.

