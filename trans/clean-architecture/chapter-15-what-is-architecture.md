# Chapter 15 : What is Architecture ?
-----------------

Từ “kiến trúc” gợi nên những hình ảnh về quyền lực và huyền bí. Nó làm cho chúng ta nghĩ về những quyết định lớn lao và những năng lực về kỹ thuật sâu sắc. Kiến trúc phần mềm là đỉnh cao của các thành tựu kỹ thuật. Khi chúng ta nghĩ về một kiến trúc sư phần mềm, chúng ta sẽ nghĩ về một ai đó có quyền lực, và mệnh lệnh của người đó phải được tôn trọng. Có lập trình viên phần mềm trẻ đầy khát vọng nào mà lại không mơ về một ngày sẽ trở thành một kiến trúc sư phần mềm?

Nhưng kiến trúc phần mềm là gì? Một kiến trúc sư phần mềm làm cái gì, và anh ta hay cô ta thực hiện công việc khi nào?

Điều đầu tiên, một kiến trúc sư phần mềm là một lập trình viên; và vẫn sẽ tiếp tục là một lập trình viên. Bạn đừng bao giờ tin lời nói rằng các kiến trúc sư phần mềm đã lùi lại phía sau việc code để tập trung vào các vấn đề ở cấp cao hơn. Họ không phải như vậy! Các kiến trúc sư phần mềm là những lập trình viên giỏi nhất, và họ tiếp tục nhận những nhiệm vụ lập trình, trong khi đó họ cũng hướng dẫn phần còn lại của đội phát triển hướng tới một thiết kế mà có thể tối đa hóa được năng suất làm việc. Các kiến trúc sư phần mềm có thể không viết code nhiều như những lập trình viên khác, nhưng họ vẫn tiếp tục gắn bó với các nhiệm vụ về lập trình. Họ làm như vậy bởi vì họ không thể làm tốt công việc của họ nếu họ không được trải qua những vấn đề mà họ đang gặp phải khi lập trình.

Kiến trúc của một hệ thống phần mềm là hình thù của hệ thống phần mềm đó được đưa ra bởi những người sẽ xây dựng nên nó. Hình thù đó bao gồm sự phân chia hệ thống đó thành các component, sự sắp xếp của những component đó, và cách mà những component đó liên lạc với nhau.

Mục đích của hình thù đó là để tạo thuận lợi cho việc phát triển, triển khai, vận hành, và bảo trì hệ thống phần mềm nằm trong đó.

Chiến lược đằng sau việc tạo thuận lợi đó là để ngỏ càng nhiều lựa chọn càng tốt, càng lâu càng tốt.

Có lẽ phát biểu này gây ngạc nhiên cho bạn. Có lẽ bạn đã nghĩ mục tiêu của kiến trúc phần mềm là để làm cho hệ thống vận hành chính xác. Chắc chắn là chúng ta muốn hệ thống đó được vận hành chính xác, và chắc chắn kiến trúc của hệ thống bắt buộc phải hỗ trợ điều đó như là một trong những ưu tiên cao nhất của nó.

Tuy nhiên, kiến trúc của một hệ thống có rất ít ảnh hưởng đến việc hệ thống có hoạt động hay không. Có rất nhiều hệ thống ngoài kia vẫn làm việc tốt mà có những kiến trúc kinh khủng. Vấn đề của chúng không nằm ở khả năng vận hành; mà là vấn đề sẽ xảy ra trong quá trình triển khai, bảo trì, và phát triển tiếp tục.

Tôi không nói là kiến trúc không có vai trò gì trong việc hỗ trợ hệ thống hoạt động chính xác. Chắc chắn là có, và vai trò đó rất quan trọng. Nhưng vai trò đó là thụ động và chỉ ở bên ngoài, không phải là chủ động hoặc thiết yếu. Nếu có, chỉ có một số ít các lựa chọn hành vi mà kiến trúc của một hệ thống có thể để ngỏ.

Mục đích chính của kiến trúc là hỗ trợ cho vòng đời của cả hệ thống. Kiến trúc tốt làm cho hệ thống dễ hiểu, dễ phát triển, dễ bảo trì, và dễ triển khai. Mục tiêu cuối cùng là để tối thiểu chi phí của toàn bộ vòng đời hệ thống và tối đa hóa năng suất làm việc của lập trình viên.

## Development
Một hệ thống phần mềm khó để phát triển thì có lẽ sẽ không khỏe mạnh và có được tuổi thọ lâu dài. Vì vậy kiến trúc của một hệ thống cần phải làm cho hệ thống đó dễ phát triển đối với những đội sẽ phát triển nó.

Cấu trúc đội phát triển khác nhau thể hiện các quyết định kiến trúc khác nhau. Một mặt, một đội nhỏ gồm năm lập trình viên có thể làm việc cùng nhau khá hiệu quả để phát triển nên một hệ thống phần mềm nguyên khối (monolithic system) mà không cần có các component hoặc interface được xác định tốt. Thực tế là một đội như vậy sẽ cảm thấy sự chặt chẽ của một kiến trúc là một trở ngại trong những ngày đầu phát triển. Đây có thể là lý do tại sao có quá nhiều hệ thống lại không có được một kiến trúc tốt: Chúng được bắt đầu làm mà không có kiến trúc, bởi vì đội phát triển khi đó nhỏ và không muốn bị trở ngại bởi một kiến trúc thượng tầng.

Mặt khác, một hệ thống đang được phát triển bởi năm đội phát triển khác nhau, mỗi đội bao gồm bảy lập trình viên, sẽ không thể tiến triển trừ khi hệ thống này được chia thành những component được thiết kế tốt với những interface ổn định đáng tin cậy. Nếu không có thêm yếu tố gì khác thì kiến trúc hệ thống đó có lẽ sẽ phát triển thành năm component – mỗi đội phát triển chịu trách nhiệm một component.

Kiến trúc mỗi đội một component như vậy không phải là kiến trúc tốt nhất cho việc triển khai, vận hành, và bảo trì hệ thống. Tuy nhiên, nó là kiến trúc mà đa phần các đội phát triển sẽ ngả về nếu họ đơn thuần chỉ bị thúc đẩy bởi lịch trình phát triển.

## Deployment
Để hiệu quả, một hệ thống phần mềm buộc phải có thể triển khai được. Chi phí triển khai càng cao thì hệ thống đó càng ít hữu dụng. Mục tiêu của kiến trúc phần mềm nên là làm cho một hệ thống có thể dễ dàng được triển khai chỉ với một thao tác.

Thật không may, chiến thuật triển khai hiếm khi được cân nhắc trong quá trình phát triển ban đầu. Điều này dẫn đến việc kiến trúc phần mềm có thể làm cho hệ thống dễ dàng để phát triển, nhưng lại rất khó để triển khai.

Lấy ví dụ, trong những ngày đầu phát triển một hệ thống, nhiều lập trình viên có thể quyết định dùng “kiến trúc micro-service” (kiến trúc vi dịch vụ). Họ có thể thấy rằng cách tiếp cận này làm cho hệ thống rất dễ để phát triển do ranh giới giữa các component là rất chắc chắn và các interface cũng tương đối ổn định. Tuy nhiên, khi đến lúc triển khai hệ thống, họ có thể mới thấy rằng số lượng các micro-service khiến cho họ phát nản; cấu hình các kết nối giữa chúng, và thời điểm khởi động chúng, cũng có thể trở thành một nguồn gây phát sinh lỗi lớn.

Nếu các kiến trúc sư xem xét các vấn đề triển khai này sớm, họ có thể đã quyết định lựa chọn ít service hơn, kết hợp giữa các service và các component trong chương trình và một phương tiện thích hợp hơn để quản lý các kết nối.

## Operation

Sự ảnh hưởng của kiến trúc tới vận hành hệ thống có khuynh hướng ít nghiêm trọng hơn so với ảnh hưởng của kiến trúc tới quá trình phát triển, triển khai, và bảo trì phần mềm. Hầu như bất cứ khó khăn nào trong khi vận hành cũng có thể được giải quyết bằng cách bổ sung thêm phần cứng vào hệ thống mà không ảnh hưởng nhiều tới kiến trúc phần mềm.

Quả thực là chúng ta thấy điều này xảy ra suốt. Các hệ thống phần mềm có các kiến trúc không hiệu quả có thể thường làm cho công việc trở nên hiệu quả chỉ đơn giản bằng cách thêm thiết bị lưu trữ và thêm máy chủ. Thực tế ngày nay, phần cứng thì rẻ và con người thì đắt đỏ, điều này có nghĩa là các kiến trúc gây cản trở vận hành thì không tốn chi phí như các kiến trúc gây trở ngại cho việc phát triển, triển khai, và bảo trì phần mềm.

Tôi không nói rằng chúng ta không mong muốn một kiến trúc phù hợp tốt với việc vận hành của hệ thống. Đó chỉ là phương trình chi phí nghiêng hơn về phía phát triển, triển khai và bảo trì.

Phải nói rằng, có một vai trò khác mà kiến trúc phần mềm nắm giữ trong việc vận hành hệ thống: Một kiến trúc phần mềm tốt sẽ kết nối các nhu cầu vận hành của hệ thống.

Có lẽ một cách tốt hơn để nói về điều này đó là kiến trúc một hệ thống làm cho việc vận hành hệ thống trở nên rõ ràng đối với các lập trình viên. Kiến trúc cần làm sáng tỏ quá trình vận hành. Kiến trúc của hệ thống cần phải làm rõ được các trường hợp sử dụng, các chức năng, và các hành vi được yêu cầu của hệ thống đối với các thực thể lớp đầu tiên, những điểm mốc có thể nhìn thấy được đối với các lập trình viên. Điều này sẽ đơn giản hóa việc thấu hiểu hệ thống và do đó hỗ trợ rất lớn cho việc phát triển và bảo trì.

## Maintenance

Trong tất cả các khía cạnh của một hệ thống phần mềm, bảo trì là phần chi phí tốn kém nhất. Cuộc diễu hành không có hồi kết của những chức năng mới và những lối mòn không thể tránh được của những lỗi tồn tại và việc điều chỉnh sửa đổi sẽ tiêu tốn một lượng lớn nguồn nhân lực.

Chi phí bảo dưỡng chính là vào việc đào sâu tính toán và rủi ro. Việc đào sâu tính toán là chi phí tìm hiểu sâu vào phần mềm hiện có, cố gắng xác định vị trí tốt nhất và chiến thuật tốt nhất để thêm một chức năng mới hay để sửa một lỗi. Trong khi thực hiện những thay đổi như vậy, thì khả năng tạo ra những lỗi do vô ý là luôn luôn tồn tại, điều này sẽ tăng thêm chi phí rủi ro.

Một kiến trúc được suy tính cẩn thận sẽ giảm bớt được gánh nặng những chi phí này đi rất nhiều. Bằng việc phân tách hệ thống thành những component, và tách biệt những component này qua những interface ổn định, chúng ta có thể thắp sáng được con đường cho các chức năng trong tương lai và giảm đi đáng kể những rủi ro của những lỗi do thay đổi vô ý.

## Keeping options open

Như chúng ta đã mô tả trong chương trước, phần mềm có hai kiểu giá trị: giá trị hành vi của nó và giá trị cấu trúc của nó. Cái thứ hai có giá trị lớn hơn bởi vì nó là giá trị giúp cho phần mềm trở nên mềm.

Phần mềm được phát minh bởi vì chúng ta cần một cách để nhanh chóng và dễ dàng thay đổi hành vi của những cỗ máy. Nhưng tính linh động đó phụ thuộc lớn vào hình thù của hệ thống, sự sắp xếp của các component của nó, và cách mà những component này được liên kết với nhau.

Cách tốt nhất để bạn giữ cho phần mềm được “mềm” là hãy để càng nhiều lựa chọn mở càng tốt, và càng lâu càng tốt. Lựa chọn là cái gì mà chúng ta cần phải để mở? Chúng là những chi tiết không quan trọng.

Tất cả các hệ thống phần mềm có thể được phân thành 2 thành phần chính: quy tắc nghiệp vụ và các chi tiết. Thành phần quy tắc nghiệp vụ thể hiện tất cả những quy định và quy trình nghiệp vụ. Phần quy tắc này là nơi mà giá trị thực sự của hệ thống tồn tại.

Các chi tiết là những thứ cần để cho phép con người, các hệ thống khác, và các lập trình viên liên lạc được với những quy tắc nghiệp vụ này, nhưng nó lại hoàn toàn không ảnh hưởng đến hành vi của những quy tắc này. Chúng bao gồm những thiết bị IO vào ra, các cơ sở dữ liệu, các hệ thống web, các máy chủ, các framework, các giao thức liên lạc…

Mục tiêu của kiến trúc sư là tạo ra một hình dạng của hệ thống có thể nhận diện được những quy tắc nghiệp vụ như là phần thiết yếu nhất của hệ thống trong khi đó làm cho các phần chi tiết không liên quan tới những quy tắc nghiệp vụ này. Điều này cho phép những quyết định về những chi tiết này có thể được trễ lại hoặc trì hoãn.

Lấy ví dụ:

Tôi nghĩ lúc này bạn đã nắm được vấn đề. Nếu bạn có thể phát triển chính sách cấp cao mà không liên hệ gì với các chi tiết quanh nó, thì bạn có thể làm trễ và trì hoãn các quyết định về những chi tiết đó trong một thời gian dài. Và bạn chờ đợi những quyết định này càng dài thì bạn càng có nhiều thông tin để làm cho quyết định đó trở nên đúng đắn.

Điều này cũng cho phép bạn lựa chọn để thử những thí nghiệm khác nhau. Nếu bạn có một phần của chính sách cấp cao đã hoạt động, và nó không biết gì về cơ sở dữ liệu, thì bạn có thể thử kết nối nó với vài cơ sở dữ liệu khác nhau và kiểm tra khả năng áp dụng và hiệu năng xem thế nào. Với các hệ thống web, framework về web, và thậm chí bản thân web cũng giống như vậy.

Bạn càng để ngỏ những lựa chọn càng dài thì bạn càng có thể chạy nhiều thử nghiệm, bạn càng có thể thử được nhiều thứ, và bạn càng có nhiều thông tin cho tới khi bạn đạt tới điểm mà những quyết định này không thể trì hoãn được nữa.

Điều gì sẽ xảy ra nếu quyết định này lại được thực hiện bởi một người khác? Điều gì sẽ xảy ra nếu công ty của bạn buộc bạn phải dùng một cơ sở dữ liệu nhất định, hoặc một máy chủ web nhất định, hoặc một framework nhất định? Một kiến trúc sư giỏi sẽ coi như là những quyết định đó chưa hề có, và thiết kế hệ thống đó để cho những quyết định như vậy vẫn có thể được trì hoãn hoặc được thay đổi càng lâu càng tốt.

Một kiến trúc sư giỏi sẽ tạo ra tối đa các quyết định cần xem xét.

## Device Independence

Một ví dụ về cách suy nghĩ này đó là chúng ta hãy quay lại những năm 1960, khi đó các máy tính vẫn còn ở độ tuổi thiếu niên và phần lớn các lập trình viên là những nhà toán học hoặc các kỹ sư từ các ngành khác (và hơn 1/3 trong số đó là phụ nữ).

Trong những ngày đó chúng tôi đã có rất nhiều sai lầm. Dĩ nhiên, chúng tôi không biết rằng chúng là những sai lầm tại thời điểm đó. Làm thế nào chúng tôi có thể biết được cơ chứ?

Một trong những sai lầm này là gắn chặt code của chúng tôi trực tiếp với các thiết bị IO vào ra. Nếu chúng tôi cần in một thứ gì đó trên một máy in, chúng tôi viết code dùng những câu lệnh IO để điều khiển chiếc máy in đó. Như vậy code của chúng tôi đã bị phụ thuộc vào thiết bị.

Lấy ví dụ, khi tôi viết các chương trình PDP-8 in trên máy in từ xa teleprinter, tôi đã dùng một bộ câu lệnh điều khiển máy trông như sau:


```
PCTCHR,	0
        TSF
        JMP .-1
        TLS
        JMP I PRTCHR
```

PCTCHR là một thủ tục để in một ký tự lên trên máy teleprinter. Số 0 bắt đầu được dùng làm vị trí lưu đối với địa chỉ trả về. (Đừng hỏi). Câu lệnh TSF bỏ qua câu lệnh tiếp theo nếu máy teleprinter đã sẵn sàng để in một ký tự. Nếu máy teleprinter bận thì lệnh TSF sẽ thực hiện lệnh JMP .-1, lệnh này nhảy trở lại lệnh TSF. Nếu máy in đã sẵn sàng, thì TSFsẽ bỏ qua lện TLS, gửi ký tự trong thanh ghi A tới máy in. Sau đó lệnh JMP I PRTCHRtrở về hàm gọi.

Lúc đầu cách làm này hoạt động tương đối ổn. Nếu chúng tôi cần đọc các tấm thẻ từ đầu đọc thẻ, thì chúng tôi sẽ dùng code để giao tiếp trực tiếp với đầu đọc thẻ. Nếu chúng tôi cần đục lỗ thẻ, chúng tôi sẽ viết code để điều khiển trực tiếp máy đục. Các chương trình này đều đã hoạt động hoàn hảo. Vậy chúng tôi biết đây là một sai lầm như thế nào?

Một bộ rất lớn các thẻ đục lỗ khó có thể quản lý được. Chúng có thể bị mất, bị gãy, bị vặn, bị xáo trộn, hoặc bị rơi. Các tấm thẻ riêng lẻ có thể bị mất và các tấm thẻ thêm có thể bị chèn vào giữa. Vì vậy việc nhất quán dữ liệu trở thành một vấn đề lớn.

Các cuộn băng từ là một giải pháp. Chúng tôi có thể di chuyển các chương trình lên băng từ. Nếu bạn làm rơi một cuộn băng từ thì các dữ liệu cũng không thể bị xáo trộn. Bạn không thể vô tình làm mất một dữ liệu, hoặc chèn một dữ liệu trống bằng việc chỉ đơn giản cầm cuộn băng từ đó. Băng từ an toàn hơn rất nhiều. Nó cũng đọc và ghi nhanh hơn, và cũng rất dễ dàng để tạo ra các bản sao lưu dữ liệu.

Thật không may, tất cả phần mềm của chúng tôi được viết để điều khiển các đầu đọc thẻ và các máy đục thẻ. Những chương trình này phải được viết lại để dùng được với băng từ. Đó là một khối lượng công việc to lớn.

Tới cuối những năm 1960, chúng tôi đã học được bài học này – và chúng tôi đã sáng chế ra tính độc lập với thiết bị. Các hệ điều hành vào những ngày đó đã trừu tượng hóa các thiết bị IO vào trong những hàm phần mềm để xử lý các đơn vị dữ liệu cũng giống như những tấm thẻ. Các chương trình gọi các dịch vụ hệ điều hành mà những dịch vụ trừu tượng đó được kết nối tới các đầu đọc thẻ, băng từ, hoặc bất cứ thiết bị ghi dữ liệu nào khác.

Ngày nay các chương trình tương tự có thể đọc và ghi các tấm thẻ, hoặc đọc ghi các cuộn băng mà không cần bất cứ thay đổi nào. Nguyên lý Mở-Đóng đã được sinh ra từ đó (nhưng chưa được đặt tên).

## Junk Mail

Vào cuối những năm 1960, tôi làm việc cho một công ty chuyên in thư rác cho các khách hàng. Các khách hàng gửi cho chúng tôi các cuộn băng từ với dữ liệu bao gồm tên và địa chỉ của các khách hàng của họ, và chúng tôi sẽ viết ra những chương trình để in những mẩu quảng cáo được cá nhân hóa một cách đẹp đẽ.

Bạn biết là nó kiểu kiểu thế này:

Xin chào Ông Martin,

Xin chúc mừng!

Chúng tôi đã chọn ÔNG trong số những người sinh sống ở Witchwood Lane được mời tham gia vào sự kiện một lần duy nhất tuyệt vời của chúng tôi…

Các khách hàng gửi cho chúng tôi các cuộn biểu mẫu thư khổng lồ đã ghi tất cả nội dung trừ tên và địa chỉ, và bất cứ thành phần nào khác mà họ muốn chúng tôi in. Chúng tôi viết các chương trình tách tên, địa chỉ, và các thành phần khác khỏi cuộn băng từ, và in những thành phần này vào chính xác nơi mà chúng cần xuất hiện trên biểu mẫu thư.

Các cuộn biểu mẫu thư này nặng tới 500-pound (khoảng 227 kg) và bao gồm hàng nghìn ký tự. Các khách hàng đã gửi cho chúng tôi hàng trăm cuộn như vậy. Chúng tôi in từng cái riêng rẽ.

Đầu tiên, chúng tôi có một máy IBM 360 thực hiện việc in ấn trên máy in dòng duy nhất của nó. Chúng tôi có thể in vài nghìn bức thư này mỗi ca. Thật không may, điều này gắn chặt với một cỗ máy rất đắt tiền trong một khoảng thời gian rất dài. Vào những ngày đó, IBM 360 được cho thuê với giá hàng chục ngàn đô-la một tháng.

Vì vậy chúng ta đã nói với hệ điều hành sử dụng băng từ thay vì máy in dòng. Chương trình của chúng tôi không quan tâm, bởi vì chúng được viết để dùng các IO trừu tượng của hệ điều hành.

Cỗ máy 360 đó có thể tạo ra cả một cuộn băng trong mười phút và vì vậy – đủ để in vài cuộn thư mẫu. Các cuộn băng được lấy từ bên ngoài phòng vi tính và gắn lên các đầu đọc băng từ được kết nối với các máy in ngoại tuyến. Chúng tôi có năm chiếc như vậy, và chúng tôi chạy cả năm chiếc máy in này 24 giờ mỗi ngày, 7 ngày mỗi tuần, in ra hàng trăm nghìn lá thư rác mỗi tuần.

Quả thật, giá trị của việc độc lập thiết bị thật là to lớn! Chúng tôi có thể viết các chương trình của mình mà không cần biết hoặc quan tâm tới thiết bị nào sẽ được sử dụng. Chúng tôi có thể kiểm tra những chương trình này bằng các máy in cục bộ được kết nối với máy tính. Sau đó chúng tôi có thể nói với hệ điều hành “in” sang băng từ và chạy ra hàng trăm nghìn bức thư mẫu.

Các chương trình của chúng tôi có hình dạng. Hình dạng đó tách biệt chính sách khỏi chi tiết. Chính sách đó ở đây là định dạng của dữ liệu tên và địa chỉ. Chi tiết ở đây là thiết bị. Chúng tôi đã trì hoãn lại quyết định về việc thiết bị nào chúng tôi sẽ sử dụng.

## Physical Addressing
Vào đầu những năm 1970, tôi làm việc trong một hệ thống kế toán lớn cho một hiệp hội xe tải địa phương. Chúng tôi có một ổ đĩa 25MB mà trên đó chúng tôi lưu các dữ liệu về Agents, Employers, và Members. Dữ liệu khác nhau thì có kích thước khác nhau, vì vậy chúng tôi đã định dạng những cylinder đầu tiên của đĩa sao cho mỗi sector chỉ có cỡ của một dữ liệu Agent. Vài cylinder tiếp theo được định dạng để có các sector vừa với dữ liệu Employer. Những cylinder cuối cùng được định dạng để vừa với dữ liệu Member.

Chúng tôi đã viết để phần mềm của chúng tôi biết về cấu trúc chi tiết của ổ đĩa. Nó biết rằng ổ đĩa có 200 cylinder và 10 head, và mỗi cylinder có hàng tá các sector mỗi head. Nó biết cylinder nào lưu trữ dữ liệu Agents, Employers, và Members.

Tất cả những thứ này được gắn cứng trong code.

Chúng tôi đã giữ một chỉ mục trên ổ đĩa để cho phép chúng tôi tìm kiếm mỗi Agents, Employers, và Members. Chỉ mục này lại nằm trong một bộ các cylinder khác trên ổ đĩa được định dạng đặc biệt. Chỉ mục Agent là tậphợp các dữ liệu bao gồm ID của một agent, và số cylinder, số head, và số sector của dữ liệu Agent đó. Employers và Members có các chỉ mục tương tự. Members cũng được giữ trong một danh sách liên kết kép (doubly linked list) trên ổ đĩa. Mỗi dữ liệu Member lưu giữ số cylinder, head, và sector của dữ liệu Member tiếp theo, và của dữ liệu Member trước đó.

Điều gì sẽ xảy ra nếu chúng tôi cần nâng cấp sang một ở đĩa mới – có nhiều head hơn, hoặc có nhiều cylinder hơn, hoặc có nhiều sector trên mỗi cylinder hơn? Chúng tôi đã phải viết một chương trình đặc biệt để đọc vào dữ liệu cũ từ ổ đĩa cũ, và sau đó ghi lại chúng vào ổ đĩa mới, chuyển dịch tất cả các số cylinder/head/sector. Chúng tôi cũng phải thay đổi tất cả những phần gắn cứng trong code của chúng tôi – và các phần gắn cứng đó thì xuất hiện ở khắp mọi nơi! Tất cả những quy định nghiệp vụ đều biết về sơ đồ cylinder/head/sector một cách chi tiết.

Rồi một ngày nọ, một lập trình viên có kinh nghiệm hơn gia nhập đội ngũ của chúng tôi. Khi anh ấy nhìn thấy những gì chúng tôi đã làm, thì anh ấy mặt cắt không còn một hột máu, và anh ấy nhìn vào chúng tôi một cách kinh hoàng, như thể chúng tôi là những người ngoài hành tinh vậy. Sau đó anh ấy đã nhẹ nhàng khuyên chúng tôi nên thay đổi sơ đồ địa chỉ sang dùng địa chỉ tương đối.

Người đồng nghiệp thông minh đó của chúng tôi đã đề nghị chúng tôi xem ổ đĩa là một dãy tuyến tính khổng lồ các sector, mỗi cái được đánh địa chỉ bởi một số tự nhiên liên tiếp. Sau đó chúng tôi có thể viết một thủ tục chuyển đổi nhỏ biết cấu trúc vật lý của ổ đĩa, và có thể dịch địa chỉ tương đối đó sang số cylinder/head/sector một cách nhanh chóng.

May mắn cho chúng tôi, chúng tôi đã nghe theo lời khuyên của anh ấy. Chúng tôi đã thay đổi chính sách cấp cao của hệ thống để nó không biết gì về cấu trục vật lý của ổ đĩa. Điều đó cho phép chúng tôi tách biệt quyết định về cấu trúc ổ đĩa khỏi ứng dụng.

## Conclusion

Hai câu truyện trong chương này là ví dụ về những dự án nhỏ nhưng những nguyên lý đó cũng vẫn được các kiến trúc sư áp dụng trong các dự án lớn. Các kiến trúc sư tách biệt cẩn thận phần chi tiết khỏi phần chính sách, và sau đó tách riêng phần chính sách khỏi phần chi tiết kỹ càng đến mức mà các chính sách không hề biết chút gì về chi tiết và không phụ thuộc vào phần chi tiết chút nào. Các kiến trúc sư giỏi thiết kế ra chính sách để cho các quyết định về các chi tiết có thể được trễ lại và trì hoãn càng lâu càng tốt.