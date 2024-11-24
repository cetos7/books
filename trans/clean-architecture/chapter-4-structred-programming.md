# Chapter 4 : Structured Programming
------------

Edsger Wybe Dijkstra sinh ra ở Rotterdam năm 1930. Ông ấy đã sống sót khỏi cuộc dội bom vào Rotterdam trong Chiến Tranh Thế Giới II, cùng với sự chiếm đóng của người Đức tại Hà Lan, và vào năm 1948, ông đã tốt nghiệp trường trung học với điểm số cao nhất có thể về toán, lý, hóa, và sinh học. Vào tháng 3 năm 1952, ở tuổi 21 (và chỉ 9 tháng trước khi tôi sinh ra), Dijkstra nhận một công việc tại Trung Tâm Toán Học Amsterdam với vai trò như là một lập trình viên đầu tiên của Hà Lan.

Năm 1955, khi đã làm một lập trình viên được ba năm, và trong khi vẫn là một sinh viên, Dijkstra đã kết luận rằng những thử thách trí tuệ của lập trình cao hơn hẳn những thử thách trí tuệ của vật lý lý thuyết. Kết quả là ông đã chọn lập trình làm sự nghiệp lâu dài của mình.

Năm 1957, Dijkstra kết hôn với Maria Debets. Vào lúc đó, mọi người sẽ phải tuyên bố rõ nghề nghiệp của mình trong buổi lễ đám cưới tại Hà lan. Các quan chức Hà Lan đã không chấp nhận “lập trình viên” là nghề của Dijkstra; bởi vì họ chưa từng nghe thấy một ngành nghề nào như vậy. Để thỏa mãn được yêu cầu, Dijkstra đã phải chọn “nhà vật lý lý thuyết” để làm tên công việc của mình.

Là một phần trong quyết định theo đuổi nghiệp lập trình, Dijsktra đã trao đổi với sếp của ông, Adriaan van Wijngaarden. Dijkstra đã lo lắng là sẽ không có ai xác định được một nguyên tắc, hoặc mối quan hệ khoa học của lập trình, và do đó ông sẽ không được coi trọng. Sếp của ông đáp lại rằng Dijkstra có thể sẽ là một trong những người đầu tiên khám phá ra được những nguyên tắc đó, nhờ vậy mà sẽ có thể giúp phát triển phần mềm thành một môn khoa học.

Dijkstra đã bắt đầu sự nghiệp của mình trong kỷ nguyên của các ống chân không, khi mà những chiếc máy tính vô cùng lớn, mong manh, chậm chạp, không đáng tin cậy, và (theo những tiêu chuẩn của ngày nay) cực kỳ bị giới hạn. Trong những năm đầu tiên đó, các chương trình được viết bằng số nhị phân, hoặc bằng hợp ngữ rất thô sơ. Việc viết chương trình được thực hiện bằng các dạng vật lý như băng giấy hoặc các tấm thẻ đục lỗ. Việc chỉnh sửa/biên dịch/kiểm tra có thể phải mất hàng giờ nếu không muốn nói là nhiều ngày.

Đó là môi trường ban sơ mà Dijkstra đã tìm ra những khám phá vĩ đại của ông.

## Proof 
Vấn đề mà Dijkstra đã nhận ra từ sớm đó là việc lập trình rất khó, và những lập trình viên làm việc không được tốt. Một chương trình dù ở mức độ khó thế nào cũng bao gồm quá nhiều chi tiết cho bộ não con người có thể quản lý được mà không cần sự trợ giúp nào. Chỉ cần bỏ sót dù chỉ là một chi tiết nhỏ cũng sẽ dẫn đến các chương trình trông có vẻ là sẽ hoạt động được, nhưng lại bị thất bại theo nhiều cách đáng kinh ngạc.

Giải pháp của Dijkstra là áp dụng nguyên tắc chứng minh toán học. Tầm nhìn của ông là xây dựng một cấu trúc phân cấp Euclid của các định đề, định lý, hệ quả và bổ đề. Dijkstra nghĩ rằng các lập trình viên có thể sử dụng hệ thống phân cấp đó theo cách mà các nhà toán học làm. Nói cách khác, các lập trình viên sẽ sử dụng các cấu trúc đã được chứng minh và gắn chúng lại với nhau bằng mã mà sau đó họ sẽ tự chứng minh tính chính xác.

Dĩ nhiên, để làm được điều này, Dijkstra đã nhận ra rằng ông phải trình diễn một kỹ thuật để viết ra các chứng minh cơ bản của các thuật toán đơn giản. Điều này ông thấy là khá thử thách.

Trong suốt thời gian nghiên cứu, Dijkstra đã khám phá ra rằng việc sử dụng các câu lệnh `goto` ngăn cản các module tách nhỏ thành những đơn vị nhỏ hơn, do đó nó ngăn cản việc sử dụng phương pháp chia để trị cần thiết cho các chứng minh hợp lý.

Tuy nhiên việc sử dụng câu lệnh `goto` trong các trường hợp khác không gây ra vấn đề này. Dijkstra đã nhận ra rằng những trường hợp dùng `goto` được thì tương ứng với các cấu trúc điều khiển lặp và lựa chọn đơn giản như `if/then/else` và `do/while`. Các module mà nó chỉ dùng những loại cấu trúc điều khiển này có thể chia nhỏ đệ quy thành những đơn vị có thể chứng minh được.

Dijkstra đã biết rằng những cấu trúc điều khiển đó, khi kết hợp với việc thực thi tuần tự thì rất đặc biệt. Tất cả những điều này được phát hiện hai năm trước khi mà Bohm và Jacopini, chứng minh rằng tất cả các chương trình có thể được xây dựng từ chỉ ba cấu trúc: chuỗi tuần tự, lựa chọn, và vòng lặp.

Khám phá này rất đáng lưu ý: Chính cấu trúc điều khiển để tạo ra một module có thể chứng minh được là cùng một tập các cấu trúc điều khiển tối giản thì từ đó có thể xây dựng được tất cả các chương trình. Do đó lập trình cấu trúc đã ra đời.

Dijkstra đã chỉ ra rằng các câu lệnh tuần tự có thể được chứng minh là đúng thông qua phép liệt kê đơn giản. Kỹ thuật này lần tìm theo phương pháp toán học các đầu vào của chuỗi cho tới các đầu ra của chuỗi. Cách tiếp cận này không khác gì so với bất kỳ chứng minh toán học thông thường nào.

Dijkstra đã giải quyết vấn đề lựa chọn thông qua việc áp dụng lại phương pháp liệt kê. Mỗi đường dẫn qua vùng lựa chọn đã được liệt kê. Nếu cả hai con đường cuối cùng tạo ra kết quả toán học thích hợp, thì chứng minh đó là chắc chắn.

Vấn đề vòng lặp thì hơi khác một chút. Để chứng minh một phép lặp là đúng, Dijkstra đã phải sử dụng quy nạp. Ông đã chứng minh trường hợp 1 bằng phép liệt kê. Sau đó, ông chứng minh trường hợp rằng nếu N được cho là đúng, thì N + 1 sẽ đúng, một lần nữa bằng phép liệt kê. Ông cũng chứng minh tiêu chí bắt đầu và kết thúc của phép lặp bằng phép liệt kê.

Những chứng minh như vậy rất tốn công sức và phức tạp – nhưng chúng là những chứng minh. Với sự phát triển của chúng, ý tưởng rằng một hệ thống phân cấp Euclid của các định lý có thể được xây dựng dường như có thể đạt được.

## A Harmful Proclamation

Năm 1968, Dijkstra đã viết một bài báo cho biên tập viên của CACM, được đăng trên số tháng ba. Tiêu đề của bài báo này là “Câu Lệnh Goto Có Thể Coi Là Gây Hại”. Bài báo này đã phác thảo lập trường của ông về ba cấu trúc điều khiển này.

Và thế giới lập trình bắt đầu bốc hỏa. Vào thời điểm đó chúng tôi chưa có Internet, vì vậy người ta đã không thể đăng lên những tấm hình meme kinh tởm chế giễu Dijkstra, và họ cũng không thể thiêu sống ông trên mạng. Nhưng họ có thể, và họ đã làm, viết các bức thư cho những biên tập viên của nhiều tạp chí đã xuất bản.

Những bức thư đó không phải cái nào cũng lịch sự. Một số cực kỳ tiêu cực; một số khác lên tiếng ủng hộ mạnh mẽ lập trường của ông. Và vì vậy trận chiến đã được bắt đầu, và cuối cùng nó kéo dài khoảng một thập kỷ.

Cuối cùng thì cuộc tranh luận cũng chấm dứt. Lý do rất đơn giản: Dijkstra đã thắng. Khi các ngôn ngữ máy tính phát triển, câu lệnh goto luôn di chuyển về phía sau, cho đến khi nó biến mất hoàn toàn. Hầu hết các ngôn ngữ hiện đại đều không có câu lệnh goto — và tất nhiên, LISP không bao giờ làm như vậy.

Ngày nay tất cả chúng ta đều là những lập trình viên cấu trúc, mặc dù không phải tất cả đều lựa chọn như vậy. Nó chỉ đơn giản là các ngôn ngữ lập trình của chúng ta không cho phép chúng ta lựa chọn việc sử dụng việc chuyển giao điều khiển trực tiếp một cách vô kỷ luật nữa mà thôi.

Một số có thể chỉ ra câu lệnh break trong Java hoặc các exception cũng là dạng lệnh tương tự goto. Trên thực tế, những câu lệnh này không phải là sự chuyển giao quyền kiểm soát hoàn toàn không hạn chế như các ngôn ngữ cũ hơn như Fortran hoặc COBOL đã từng có. Thực vậy, ngay cả những ngôn ngữ vẫn hỗ trợ từ khóa goto cũng thường giới hạn mục tiêu vào trong phạm vi của hàm hiện tại.

## Functional Decomposition

Lập trình cấu trúc cho phép các module được phân tách đệ quy thành những đơn vị nhỏ có thể chứng minh được, điều này có nghĩa là những module đó đã được phân tách chức năng. Bạn có thể nhận một vấn đề lớn và phân nhỏ nó thành những chức năng ở tầm cao. Mỗi chức năng này có thể lại được phân tách thành những chức năng ở cấp thấp hơn, đến vô cùng. Hơn nữa, mỗi hàm được phân tách có thể được thể hiện bằng cách dùng các cấu trúc điều khiển hạn chế của lập trình cấu trúc.

Việc xây dựng dựa trên nền tảng này, các nguyên tắc như phân tích cấu trúc và thiết kế cấu trúc đã trở nên phổ biến vào cuối những năm 1970 và trong suốt những năm 1980. Những người như Ed Yourdon, Lary Constantine, Tom DeMarco, và Meilir Page-Jones đã quảng bá và phổ biến những kỹ thuật này trong suốt thời kỳ đó. Bằng cách tuân thủ những nguyên tắc này, những lập trình viên có thể chia nhỏ những hệ thống lớn thành những module và những thành phần mà có thể tiếp tục được chia nhỏ hơn nữa thành những hàm chứng minh được.

## No formal proofs
Nhưng các chứng minh thì không bao giờ có. Hệ thống phân cấp các định lý Euclid không bao giờ được xây dựng. Và các lập trình viên nhìn chung chưa bao giờ thấy lợi ích của việc chứng minh từng chức năng nhỏ là đúng. Cuối cùng, giấc mơ của Dijkstra đã tan thành mây khói. Rất ít lập trình viên ngày nay tin rằng các chứng minh chính thức là cách thích hợp để tạo ra những phần mềm chất lượng cao.

Tất nhiên, hình thức, phong cách Euclid, chứng minh toán học không phải là chiến lược duy nhất để chứng minh điều gì đó đúng. Một chiến lược rất thành công khác là phương pháp khoa học.

## Science to the rescue

Khoa học là một phần căn bản khác của toán học, trong đó các lý thuyết và định luật khoa học không thể được chứng minh chính xác. Tôi không thể chứng minh cho bạn rằng định luật chuyển động thứ hai của Newton, F=ma, hay định luật hấp dẫn, F=Gm1m2/r2, là chính xác. Tôi có thể chứng minh được những định luật này cho bạn, và tôi có thể đo đạc được xem độ chính xác của chúng tới bao nhiêu con số sau dấu phẩy, nhưng tôi không thể chứng minh chúng theo cách chứng minh bằng toán học. Dù tôi có thực hiện bao nhiêu cuộc thí nghiệm hay thu thập được bao nhiêu bằng chứng kinh nghiệm đi chăng nữa, thì cũng luôn luôn sẽ có khả năng một vài thí nghiệm nào đó sẽ chỉ ra rằng những định luật chuyển động và hấp dẫn đó là không chính xác.

Đó là bản chất của các thuyết và định luật khoa học: Chúng có thể tái hiện được nhưng không chứng minh được.

Và chúng ta đang đặt cược cuộc sống của chính mình vào những định luật này hàng ngày. Mỗi lần bạn đi lên một chiếc ô tô, bạn đặt cược sinh mạng của mình vào công thức F=ma như là một mô tả đáng tin cậy về cách thế giới này vận hành. Mỗi lần bạn bước một bước, bạn đặt cược sức khỏe và sự an toàn của mình vào công thức F=Gm_1m_2/r^2 là chính xác.

Khoa học không làm việc bằng cách chứng minh các phát biểu là đúng, mà thay vào đó là chứng minh các phát biểu là sai. Những phát biểu mà chúng ta không thể chứng minh là sai được, dù có nỗ lực đến thế nào, thì khi đó chúng ta có thể cho rằng nó đủ đúng với mục đích của chúng ta.

Dĩ nhiên, không phải tất cả các phát biểu đều có thể chứng minh được. Phát biểu “đây là một lời dối trá” không đúng cũng chẳng sai. Nó là một trong những ví dụ đơn giản nhất của một phát biểu mà không thể chứng minh được.

Cuối cùng, chúng ta có thể nói rằng toán học là nguyên tắc của việc chứng minh những phát biểu có thể chứng minh được là đúng. Khoa học, ngược lại, là nguyên tắc của việc chứng minh những phát biểu không thể chứng minh được là sai.

## Tests
Dijkstra đã từng nói, “Việc kiểm tra chỉ ra sự hiện diện, không phải là sự vắng mặt của các bug (lỗi)”. Nói cách khác, một chương trình có thể được chứng minh chạy không đúng bằng một bài kiểm tra, nhưng nó không thể được chứng minh là chính xác. Tất cả các bài kiểm tra có thể thực hiện, sau đủ nỗ lực kiểm tra, sẽ cho phép chúng ta xem như một chương trình đủ chính xác cho mục đích của chúng ta.

Hệ quả của thực tế này thật đáng kinh ngạc. Việc phát triển phần mềm không phải là một nỗ lực toán học, mặc dù nó dường như vận dụng các cấu trúc toán học. Đúng hơn là phần mềm giống như một môn khoa học. Chúng ta cho thấy sự đúng đắn bằng cách không chứng minh được sự không đúng, mặc dù chúng ta đã có thể cố gắng hết sức.

## Conclusion

Khả năng tạo ra những đơn vị lập trình có thể kiểm chứng được đã làm cho lập trình cấu trúc có giá trị ngày nay. Đây là nguyên nhân mà các ngôn ngữ lập trình hiện đại không hỗ trợ các câu lệnh goto không hạn chế. Hơn nữa, ở cấp kiến trúc phần mềm, đó là lý do tại sao chúng ta vẫn coi việc phân tách chức năng là một trong những phương pháp thực tiễn tốt nhất của chúng ta.

Ở mỗi cấp, từ những hàm nhỏ nhất cho tới các component lớn nhất, thì phần mềm cũng giống như một môn khoa học và do đó được dẫn dắt bởi khả năng kiểm chứng được. Những kiến trúc sư phần mềm cố gắng để định nghĩa ra các module, các component, và các dịch vụ mà có thể dễ dàng kiểm chứng được. Để làm được như vậy, họ sử dụng những nguyên tắc hạn chế tương tự như lập trình cấu trúc, mặc dù ở cấp độ cao hơn nhiều.