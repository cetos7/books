# Chapter 3: Paradigm Overview
----------

Có 3 mô hình được đề cập trong chapter này đó là: structured programming (lập trình hướng cấu trúc), object-orient programming (lập trình hướng đối tượng), và functional programming (lập trình hàm).

## Structure programming
Paradigm đầu tiên được áp dụng (nhưng không phải mô hình đầu tiên được phát minh) là lập trình hướng cấu trúc, được khám phá bởi Dijkstra. Ông cho thấy rằng việc sử dụng các unrestrained jumps (các câu lệnh `goto`) sẽ không tốt cho cấu trúc chương trình. Và ta sẽ thay các jump đó bằng các cấu trúc quan thuộc như : `if/then/else` và `do/while/until`.

Ta có thể nói mô hình này như sau: 
> Structured programming imposes discipline on direct transfer of control. (Lập trình hướng cấu trúc áp dụng nghiêm ngặt đối với chuyển giao quyền điều khiển trực tiếp)

## Object-oriented programming
Mô hình thứ hai thâm chí được áp dụng trước 2 năm so với mô hình lập trình hướng cấu trúc ở trên. Hai người khám phá ra nó thấy rằng function call stack frame trong ALGOL có thể chuyển thành một heap. Do vậy, các biến local đã được khai báo bởi một function có thể tồn tại kể cả khi mà function đã được return. 

Function này sẽ là một constructor cho một class, các biến local đó chính là các biến instance, và các function lồng nhau hợp lại thành các method. Từ đó, ta sẽ khám phá được tính đa hình (polymorphism) thông qua việc sử dụng nghiêm ngặt các function pointer.

Ta thể tóm tắt lại mô hình này như sau:
> OOP imposes discipline on indirect transfer of control. (OOP áp dụng nghiêm ngặt đối với việc chuyển giao quyền điều khiển gián tiếp)


## Functional programming
Mô hình thứ 3, được áp dụng gần đây, nhưng lại là mô hình được khám phá ra đầu tiên, là kết quả của công trình của Alonzo Church là $\lambda$-calculus. Một khái niệm cơ bản của phép tính này là tính bất biến, nó cho rằng giá trị của các symbol không thay đổi, tức các ngôn ngữ functional sẽ không có câu lệnh gán (assignment statement). Trên thực tế, hầu hết các ngôn ngữ hướng hàm đều có một số phương thức thay đổi được giá trị của biến, nhưng chỉ với những nguyên tắc rất nghiêm ngặt.

Ta có thể tóm tắt lại mô hình này như sau:
> Functional programming imposes discipline upon assignment.


