# Chapter 16 : Independence
--------------

Như chúng ta đã nói trước đây, một kiến trúc tốt buộc phải hỗ trợ:

- Các tình huống sử dụng (use case) và vận hành của hệ thống.
- Bảo trì hệ thống.
- Phát triển hệ thống.
- Triển khai hệ thống.

## Use Cases

Ý đầu tiên – các tình huống sử dụng – nghĩa là kiến trúc của hệ thống buộc phải hỗ trợ ý định của hệ thống. Nếu hệ thống là một ứng dụng giỏ hàng mua sắm, thì kiến trúc đó phải hỗ trợ các tình huống sử dụng giỏ hàng mua sắm. Quả thực, đây là mối quan tâm đầu tiên của kiến trúc sư, và là ưu tiên đầu tiên của kiến trúc đó. Kiến trúc phải hỗ trợ các tình huống sử dụng này.

Tuy nhiên, như chúng ta đã thảo luận ở trước, kiến trúc không nên ảnh hưởng nhiều đến hành vi của hệ thống. Có rất ít các lựa chọn hành vi mà kiến trúc có thể để mở. Nhưng ảnh hưởng không phải là tất cả. Điều quan trọng nhất mà một kiến trúc tốt có thể làm để hỗ trợ hành vi là làm rõ ràng và phơi bày hành vi đó ra để cho mục đích của hệ thống có thể thấy được ở cấp độ kiến trúc.

Một ứng dụng giỏ hàng mua sắm với một kiến trúc tốt sẽ trông giống như một ứng dụng giỏ hàng mua sắm. Các tình huống sử dụng của hệ thống đó sẽ có thể nhìn thấy rõ trong cấu trúc của hệ thống. Các lập trình viên sẽ không phải lùng tìm các hành vi, bởi vì những hành vi đó sẽ là các thành phần lớp đầu tiên nhìn thấy được ở cấp độ cao nhất của hệ thống. Những thành phần này là những lớp hoặc hàm hoặc module có vị trí nổi bật trong tổng thể kiến trúc, và chúng sẽ có tên và mô tả rõ ràng chức năng của chúng.

## Operation

Kiến trúc đóng một vai trò quan trọng và ít hình thức hơn trong việc hỗ trợ vận hành của hệ thống. Nếu hệ thống buộc phải xử lý 100.000 khách hàng mỗi giây, thì kiến trúc sẽ phải hỗ trợ lượng băng thông và thời gian phản hồi đó đối với mỗi tình huống sử dụng đòi hỏi yêu cầu như vậy. Nếu hệ thống phải tìm kiếm khối dữ liệu lớn chỉ trong vài mili-giây, thì kiến trúc sẽ phải được xây dựng để cho phép yêu cầu vận hành như vậy.

Đối với một số hệ thống, điều này có nghĩa là sắp xếp các thành phần xử lý của hệ thống thành một dãy các dịch vụ nhỏ có thể chạy song song trên nhiều máy chủ khác nhau. Đối với các hệ thống khác, nó có nghĩa là rất nhiều những thread (luồng) nhỏ nhẹ chia sẻ không gian địa chỉ của một process (tiến trình) nằm trong một bộ vi xử lý đơn. Một số hệ thống khác sẽ chỉ cần một vài process chạy trong các không gian địa chỉ riêng biệt. Và một vài hệ thống thậm chí có thể tồn tại là các chương trình nguyên khối đơn giản chạy trong một process đơn.

Nghe có vẻ lạ, nhưng quyết định này là một trong những lựa chọn mà một kiến trúc sư giỏi để mở. Một hệ thống được viết nguyên khối (monolith), và phụ thuộc vào cấu trúc nguyên khối, thì không thể dễ dàng nâng cấp được thành đa xử lý, đa luồng, hoặc các micro-service nếu nhu cầu phát sinh. Bằng cách so sánh, một kiến trúc duy trì được sự tách biệt đúng đắn giữa các component của nó, và không xác định sẵn phương tiện liên lạc giữa những component đó, thì sẽ dễ hơn nhiều để chuyển đổi qua các luồng, các process, và các dịch vụ khi nhu cầu vận hành của hệ thống thay đổi.

## Developmemt

Kiến trúc đóng một vai trò to lớn trong việc hỗ trợ môi trường phát triển. Đây là nơi luật Conway được áp dụng. Luật Conway nói rằng:

*Any organization that design a system will produce a design whose structure is a copy of the organization's communication structure.*

*Bất cứ tổ chức nào thiết kế một hệ thống sẽ tạo ra một thiết kế mà cấu trúc của nó là một bản sao cấu trúc liên lạc của tổ chức đó*

Một hệ thống buộc phải được phát triển bởi một tổ chức có nhiều đội và nhiều vấn đề sẽ phải có một kiến trúc tạo thuận lợi cho các hoạt động độc lập của những đội đó, để cho các đội đó không bị ảnh hưởng với đội khác trong suốt quá trình phát triển. Điều này có thể được thực hiện bằng cách phân chia hệ thống cho phù hợp thành những phần tách biệt nhau, các component có thể phát triển một cách độc lập nhau. Sau đó, những component đó có thể được phân cho những đội có thể làm việc độc lập với nhau.


## Deployment

Kiến trúc cũng đóng một vai trò to lớn trong việc xác định mức độ dễ dàng mà hệ thống sẽ được triển khai. Mục tiêu đặt ra là “khả năng triển khai ngay lập tức”. Một kiến trúc tốt sẽ không phải phụ thuộc vào hàng tá những script cấu hình nhỏ và những file tinh chỉnh phù hợp. Nó không đòi hỏi phải tạo thủ công các thư mục hoặc các file buộc phải được sắp xếp sẵn như vậy. Một kiến trúc tốt sẽ giúp cho hệ thống được triển khai ngay lập tức sau khi build.

Lại một lần nữa, điều này có thể thực hiện được thông qua việc phân chia và tách biệt một cách hợp lý các component của hệ thống, bao gồm những component chính gắn toàn bộ hệ thống lại với nhau và đảm bảo rằng mỗi component được khởi động, được tích hợp, và được giám sát một cách đúng đắn.

## Leaving options open

Một kiến trúc tốt sẽ cân bằng tất cả những vấn đề này với một cấu trúc component có thể thỏa mãn đồng thời tất cả. Nghe có vẽ dễ, đúng không nào? Đúng là đối với tôi thì rất dễ dàng để viết ra như vậy. Nhưng trong thực tế, để đạt được sự cân bằng này là điều khá khó khăn. Vấn đề là phần lớn chúng ta không biết được hết các tình huống sử dụng có thể xảy ra, hay chúng ta không biết hết về các ràng buộc vận hành, cấu trúc đội phát triển, hoặc các yêu cầu triển khai. Tệ hơn ngay cả khi chúng ta đã biết về chúng thì chúng cũng sẽ không tránh khỏi việc phải thay đổi khi hệ thống đi qua vòng đời của nó. Nói ngắn gọn, các mục tiêu mà chúng ta phải đi tới đều không rõ ràng và không cố định. Xin chào mừng các bạn đến với thế giới thực tế.

Nhưng tất cả không mất đi: Một số nguyên lý kiến trúc tương đối không đắt để triển khai và có thể giúp cân bằng được những vấn đề này, ngay cả khi bạn không có một bức tranh rõ ràng về các mục tiêu mà bạn phải đạt tới. Những nguyên lý này có thể giúp chúng ta phân chia hệ thống của chúng ta thành những component tách biệt và cho phép chúng ta để mở nhiều lựa chọn nhất có thể, trong lâu nhất có thể.

Một kiến trúc tốt sẽ làm cho hệ thống dễ dàng thay đổi theo tất cả các cách mà nó phải thay đổi, bằng cách là để mở các lựa chọn.

## Decoupling layers
Hãy xem các tình huống sử dụng sau. Kiến trúc sư muốn cấu trúc của hệ thống hỗ trợ tất các các tình huống sử dụng cần thiết, nhưng không biết được tất cả các tình huống sử dụng có thể có. Tuy nhiên, kiên trúc sư đã biết về mục đích cơ bản của hệ thống. Đó là một hệ thống giỏ hàng mua sắm, hoặc một hệ thống lên danh sách vật tư, hoặc một hệ thống xử lý đơn hàng. Vì vậy kiến trúc sư đó có thể áp dụng Nguyên Lý Đơn Nhiệm SRP và Nguyên Lý Khép Kín Chung CCP để tách biết những thứ có thể thay đổi vì những lý do khác nhau, và để tập hợp lại những thứ sẽ thay đổi vì cùng nguyên nhân – dựa trên ngữ cảnh mục đích của hệ thống.

Điều gì sẽ thay đổi vì những lý do khác nhau? Có một vài thứ hiển nhiên. Giao diện người dùng thay đổi vì những lý do không liên quan gì tới các quy tắc nghiệp vụ. Các tình huống sử dụng có yếu tố của cả hai. Rõ ràng một kiến trúc sư giỏi sẽ muốn tách biệt phần UI của một tình huống sử dụng khỏi phần quy tắc nghiệp vụ theo cách mà chúng có thể được thay đổi độc lập với nhau, trong khi vẫn giữ cho những tình huống sử dụng đó nhìn thấy được và rõ ràng.

Bản thân các quy tắc nghiệp vụ có thể được gắn chặt với ứng dụng, hoặc chúng có thể tổng quát hơn. Lấy ví dụ, việc kiểm tra tính chính xác của các trường đầu vào là một quy tắc nghiệp vụ gắn chặt với chính ứng dụng. Ngược lại, việc tính toán lãi của một tài khoản và đếm số lượng kiểm kê là những quy tắc nghiệp vụ gắn chặt với kiến thức chuyên ngành. Hai loại quy tắc khác nhau này sẽ thay đổi ở những tốc độ khác nhau, và vì những lý do khác nhau – vì vậy chúng nên được tách biệt để chúng có thể được thay đổi một cách độc lập.

Cơ sở dữ liệu, ngôn ngữ truy xuất dữ liệu, và thậm chí là sơ đồ dữ liệu (schema) là các chi tiết kỹ thuật không liên quan gì tới các quy tắc nghiệp vụ hoặc giao diện UI. Chúng sẽ thay đổi với tốc độ, và vì những lý do độc lập so với những khía cạnh khác của hệ thống. Kết quả là kiến trúc nên tách biệt chúng khỏi phần còn lại của hệ thống để chúng có thể được thay đổi một cách độc lập với nhau.

Như vậy chúng ta sẽ thấy hệ thống được chia thành những lớp ngang tách rời – giao diện UI, các quy tắc nghiệp vụ cụ thể của ứng dụng, các quy tắc nghiệp vụ độc lập với ứng dụng, và cơ sở dữ liệu, tôi chỉ mới đề cập tới một vài thứ.

## Decoupling Use Cases
Những thứ nào khác sẽ thay đổi vì những lý do khác nhau? Đó là những tình huống sử dụng (use case)! Tình huống sử dụng để thêm một đơn hàng vào hệ thống tiếp nhận đơn nhàng hầu như sẽ chắc chắn thay đổi với một tốc độ khác, và vì những lý do khác, so với tình huống sử dụng mà người dùng xóa một đơn hàng khỏi hệ thống. Các tình huống sử dụng là một cách rất tự nhiên để phân chia hệ thống.

Ở cùng thời điểm, các tình huống sử dụng là các lát cắt dọc mỏng cắt qua các lớp ngang của hệ thống. Mỗi tình huống sử dụng dùng một vài UI, một vài quy tắc nghiệp vụ cụ thể của ứng dụng, một vài quy tắc nghiệp vụ độc lập với ứng dụng, và một vài chức năng của cơ sở dữ liệu. Do vậy, khi chúng ta chia hệ thống thành những lớp ngang, thì chúng ta cũng chia hệ thống thành những tình huống sử dụng dọc mỏng cắt qua những lớp ngang đó.

Để đạt được sự tách rời này, chúng ta tách biệt phần UI của tình huống sử dụng “thêm đơn hàng” khỏi phần UI của tình huống sử dụng “xóa đơn hàng”. Chúng ta làm tương tự với các quy tắc nghiệp vụ, và với cơ sở dữ liệu. Chúng ta giữ cho các tình huống sử dụng được phân tách theo chiều dọc của hệ thống.

Bạn có thể nhìn thấy mẫu thiết kế này tại đây. Nếu bạn tách rời các thành phần của hệ thống mà thay đổi vì những lý do khác nhau, thì bạn có thể tiếp tục thêm những tình huống sử dụng mới mà không gây ảnh hưởng tới những cái cũ. Nếu bạn cũng nhóm UI và cơ sở dữ liệu để hỗ trợ những tình huống sử dụng này, sao cho mỗi tình huống sử dụng một khía cạnh khác nhau của UI và cơ sở dữ liệu, thì sau đó việc thêm các tình huống sử dụng mới sẽ không bị ảnh hưởng tới những cái cũ.

## Decoupling Mode
Bây giờ hãy nghĩ về cái được đề cập ở gạch đầu dòng thứ hai, việc tách rời vận hành có nghĩa là gì. Nếu các khía cạnh khác nhau của các tình huống sử dụng phải được tách biệt, thì những cái phải chạy ở băng thông cao thì có vẻ như đã tách biệt khỏi những cái phải chạy ở băng thông thấp. Nếu UI và cơ sở dữ liệu được tách biệt khỏi các quy tắc nghiệp vụ, thì chúng có thể chạy trên các máy chủ khác nhau. Những cái đòi hỏi băng thông cao hơn có thể được chạy trên nhiều máy chủ.

Nói ngắn gọn, việc tách rời mà chúng ta đã làm vì mục đích của các tình huống sử dụng cũng có tác dụng với việc vận hành. Tuy nhiên, để tận dụng ưu thế của các lợi ích vận hành, việc tách rời buộc phải có một chế độ thích hợp. Để chạy trên những máy chủ khác nhau, các component được tách riêng không thể phụ thuộc vào nhau trong cùng một không gian địa chỉ của một bộ vi xử lý. Chúng phải là những dịch vụ độc lập, liên hệ với nhau qua mạng.

Nhiều kiến trúc sư gọi các component như vậy là “các dịch vụ” hay “micro-services” (vi dịch vụ). Quả thực, một kiến trúc dựa trên các dịch vụ thường được gọi là kiến trúc hướng dịch vụ (service-oriented architecture – SoA).

Nếu thuật ngữ đó làm bạn thấy sợ thì đừng lo lắng. Tôi sẽ không nói với bạn là SoA là kiểu kiến trúc tốt nhất, hoặc các micro-service là làn sóng của tương lai. Điểm tôi muốn nói ở đây là đôi khi chúng ta phải tách biệt các component của chúng ta tới cấp độ dịch vụ.

Hãy nhớ rằng một kiến trúc tốt sẽ để mở các lựa chọn. Việc tách rời chế độ là một trong những lựa chọn này.

Trước khi chúng ta khám phá chủ đề này xa hơn, chúng ta hãy nhìn vào hai gạch đầu dòng còn lại.

## Independent Develop-Ability
Gạch đầu dòng thứ ba là khả năng phát triển. Rõ ràng khi các component đã được tách rời một cách chắc chắn, thì sự trở ngại giữa các đội phát triển cũng được giảm nhẹ. Nếu các quy tắc nghiệp vụ không biết gì về UI, thì khi một đội tập trung vào UI sẽ không thể gây ảnh hưởng nhiều tới một đội tập trung vào các quy tắc nghiệp vụ. Nếu bản thân các tình huống sử dụng được tách rời khỏi nhau, thì một đội tập trung vào tình huống sử dụng addOrder sẽ không gây ảnh hưởng tới đội tập trung vào tình huống sử dụng deleteOrder.

Một khi các lớp layer và các tình huống sử dụng được tách rời, thì kiến trúc của hệ thống sẽ hỗ trợ cho việc tổ chức của các đội phát triển, cho dù họ được tổ chức theo các đội phát triển chức năng, đội phát triển component, đội phát triển layer, hoặc những cách tổ chức khác.


## Independent Deployability
Việc tách rời các tình huống sử dụng và các layer cũng tạo ra khả năng linh hoạt cao độ trong việc triển khai. Quả thực, nếu việc tách rời được thực hiện tốt, thì nó có thể chuyển đổi nóng giữa các layer và các tình huống sử dụng trong các hệ thống đang chạy. Việc thêm một tình huống sử dụng mới có thể đơn giản là việc thêm một vài file jar hoặc dịch vụ vào hệ thống trong khi không phải đụng gì tới phần khác của hệ thống

## Duplication 

Các kiến trúc sư thường rơi vào một cái bẫy – cái bẫy dựa trên nỗi sợ hãi của họ về việc lặp lại code.

Việc lặp lại code thông thường là một điều xấu trong phần mềm. Chúng ta đều không thích code bị lặp lại. Khi code thực sự bị lặp lại, thì chúng ta, được coi là những người chuyên nghiệp, sẽ có trách nhiệm giảm thiểu và loại bỏ nó.

Nhưng có các kiểu lặp lại khác nhau. Kiểu lặp lại thực sự, trong đó mỗi thay đổi tới một thực thể sẽ cần phải thay đổi tương tự cho tất cả những bản sao của thực thể đó. Sau đó là kiểu lặp lại nhầm hoặc tình cờ. Nếu hai phần code bị lặp lại phát triển theo hai hướng khác nhau – nếu chúng thay đổi ở các tốc độ khác nhau, và vì các lý do khác nhau – thì chúng không phải là kiểu lặp lại thực sự. Vài năm sau, xem lại chúng và bạn sẽ thấy chúng đã rất khác nhau.

Bây giờ hãy tưởng tượng hai tình huống sử dụng mà có cấu trúc màn hình tương tự nhau. Các kiến trúc sư sẽ cố gắng để chia sẻ code cho cấu trúc đó. Nhưng họ có nên như vậy không? Đó là kiểu lặp lại thực sự? Hay đó là kiểu lặp lại tình cờ?

Nhiều khả năng đó là tình cờ. Khi thời gian trôi qua, lạ một điều là hai màn hình này sẽ đi theo hai hướng khác nhau và cuối cùng trông sẽ rất khác nhau. Vì lý do này, chúng ta cần phải cẩn thận để tránh hợp nhất chúng vào với nhau. Nếu không, việc tách rời chúng sau này sẽ là một thử thách.

Khi bạn tách biệt theo chiều dọc các tình huống sử dụng với nhau, bạn sẽ gặp phải vấn đề này, và việc bạn cố gắng loại bỏ code lặp sẽ móc nối các tình huống sử dụng với nhau bởi vì chúng có các cấu trúc màn hình tương tự, hoặc các thuật toán tương tự, hoặc các truy xuất dữ liệu tương tự và/hoặc sơ đồ cơ sở dữ liệu tương tự. Hãy cẩn thận. Hãy chống lại sự ý tưởng lúc nào cũng phải loại bỏ code lặp lại. Hãy đảm bảo rằng phần code lặp đó là kiểu lặp thực sự.

Cũng tương tự như vậy, khi bạn tách biệt các layer theo chiều ngang, bạn có thể lưu ý thấy rằng cấu trúc dữ liệu của một dữ liệu nào đó trong cơ sở dữ liệu trông rất giống với cấu trúc dữ liệu của một màn hình nào đó. Bạn có thể sẽ cố gắng đơn giản truyền dữ liệu đó lên UI, thay là vì tạo ra một view model giống như vậy và copy các phần tử vào đó. Hãy cẩn thận: Việc lặp lại này hầu như chắc chắn là tình cờ. Việc tạo ra một view model riêng biệt không tốn nhiều công, nhưng nó sẽ giúp bạn giữ cho các lớp được tách rời một cách đúng đắn.

## Decoupling Modes (Again)
Trở lại các chế độ. Có nhiều cách để tách rời các layer và các tình huống sử dụng use case. Chúng có thể được tách rời ở cấp độ mã nguồn, ở cấp độ mã nhị phân (cấp triển khai), và ở cấp độ đơn vị thực thi (cấp dịch vụ).

- Cấp mã nguồn (Source level): Chúng ta có thể kiểm soát các phụ thuộc giữa các module mã nguồn để những thay đổi ở một module không buộc phải thay đổi hoặc phải biên dịch lại những cái khác (ví dụ Ruby Gems). Trong chế độ tách rời này, tất cả các component thực thi trong cùng một không gian địa chỉ, và liên hệ với nhau bằng việc gọi hàm đơn giản. Chỉ có một chương trình thực thi được nạp vào trong bộ nhớ máy tính. Người ta thường gọi đây là cấu trúc nguyên khối (monolithic structure).
- Cấp triển khai (Deployment level): Chúng ta có thể kiểm soát các phụ thuộc giữa các đơn vị triển khai được như các file jar, các file DLL, hoặc các thư viện chia sẻ, sao cho những thay đổi tới mã nguồn của một module không buộc những cái khác phải build lại và triển khai lại. Nhiều component có thể vẫn tồn tại trong cùng một không gian địa chỉ nhớ, và việc giao tiếp thông qua gọi hàm. Các component khác có thể tồn tại trong các process khác trong cùng một bộ vi xử lý, và giao tiếp thông qua các cơ chế giao tiếp interprocess (liên tiến trình), các socket hoặc bộ nhớ chia sẻ. Điều quan trọng ở đây là các component được tách rời đã được phân thành những đơn vị có thể triển khai độc lập với nhau như các file jar, các file Gem, hoặc các file DLL.
- Cấp dịch vụ (Service level) : Chúng ta có thể giảm các phụ thuộc xuống cấp độ của các cấu trúc dữ liệu, và giao tiếp đơn thuần qua các gói tin trong mạng, như vậy mỗi đơn vị thực thi sẽ hoàn toàn độc lập về mã nguồn và những thay đổi về file thực thi đối với những cái còn lại (ví dụ các dịch vụ hoặc các micro-service).

Chế độ nào tốt nhất để sử dụng?

Câu trả lời là khó có thể biết được chế độ nào là tốt nhất trong giai đoạn đầu của một dự án. Quả thực khi dự án dần trưởng thành, chế độ nào tối ưu cũng có thể bị thay đổi.

Lấy ví dụ, không khó để tưởng tượng ra một hệ thống có thể chạy thoải mái trên một máy chủ hiện tại có thể phát triển tới điểm mà một vài component của nó có thể chạy trên những máy chủ riêng. Trong khi hệ thống chạy trên một máy chủ đơn, việc tách rời ở cấp độ mã nguồn có thể là đủ. Tuy nhiên, về sau, nó có thể đòi hỏi sự tách rời ở các đơn vị có thể triển khai được, hoặc thậm chí là các dịch vụ.

Một giải pháp (có vẻ như đang phổ biến lúc này) là đơn giản tách rời mặc định ở cấp độ dịch vụ. Một vấn đề với phương pháp này đó là nó rất tốn kém và cổ vũ cho việc tách rời ở mức độ thô. Dù micro-service có “micro” thế nào đi chăng nữa thì việc tách rời ở cấp độ này cũng sẽ không đủ tinh.

Một vấn đề khác với việc tách rời ở cấp độ dịch vụ là nó rất tốn kém, cả về thời gian phát triển và về việc sử dụng tài nguyên hệ thống. Xử lý với các ranh giới dịch vụ không cần thiết là một sự lãng phí công sức, bộ nhớ, và xung nhịp xử lý. Và, đúng, tôi biết rằng hai cái cuối thì rẻ nhưng cái đầu tiên thì không.

Sự lựa chọn của tôi là đẩy việc tách rời tới điểm mà một dịch vụ có thể được hình thành, xem nó có cần thiết không; nhưng sau đó để cho các component trong cùng một không gian địa chỉ càng lâu càng tốt. Điều này để mở việc lựa chọn một dịch vụ.

Với cách tiếp cận này, ban đầu các component được tách rời ở cấp độ mã nguồn. Điều này có thể đủ tốt đối với khoảng thời gian vòng đời của dự án. Tuy nhiên, nếu các vấn đề triển khai và phát triển nảy sinh, thì việc hướng một số tách biệt lên cấp triển khai có thể là đủ dùng – ít nhất là lúc này.

Khi việc phát triển, triển khai, và các vấn đề vận hành tăng lên, tôi sẽ cẩn thận lựa chọn những đơn vị có thể triển khai được nào để chuyển thành các dịch vụ, và dần dần dịch chuyển hệ thống theo hướng đó.

Trải qua thời gian, nhu cầu vận hành của hệ thống có thể giảm. Cái trước đây yêu cầu tách rời ở cấp độ dịch vụ thì bây giờ có thể chỉ cần ở cấp độ triển khai hoặc thậm chí ở cấp độ mã nguồn.

Một kiến trúc tốt sẽ cho phép một hệ thống lúc sinh ra là nguyên khối, được triển khai trong một file đơn, nhưng sau đó sẽ lớn dần thành một bộ các đơn vị có thể triển khai độc lập với nhau, và sau đó tất cả đi lên thành các dịch vụ độc lập và/hoặc các micro-service. Sau đó, khi mọi thứ đổi thay, nó sẽ cho phép đảo lại tiến trình này và quay trở về kiến trúc nguyên khối.

Một kiến trúc tốt sẽ bảo vệ phần lớn mã nguồn khỏi những thay đổi này. Nếu để mở chế độ như là một lựa chọn thì các đợt triển khai cỡ lớn có thể dùng một chế độ, trong khi các đợt triển khai cỡ nhỏ có thể dùng một chế độ khác.

## Conclusion
Đúng, đây là một công việc khó khăn. Và tôi không nói rằng việc thay đổi các chế độ tách rời cần phải là một lựa chọn cấu hình đơn giản (mặc dù đôi khi điều này là thích hợp). Điều tôi muốn nói ở đây là chế độ tách rời của một hệ thống là một trong những thứ sẽ thay đổi theo thời gian, và một kiến trúc sư giỏi sẽ nhìn thấy trước và tạo những thuận tiện thích hợp cho những thay đổi này.


