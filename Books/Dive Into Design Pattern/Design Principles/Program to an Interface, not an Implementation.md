
***Khi viết code, nên tập trung vào sử dụng interface thay vì sử dụng implementation***

- Trong OOP, một interface định nghĩa các methods mà một object cần cung cấp, mà không cung cấp implementation cụ thể của chúng. Bằng cách này, khi viết code, chỉ quan tâm đến các methods được định nghĩa trong interface, mà không cần biết cụ thể đối tượng implement interface đó làm thế nào để hoàn thành công việc.

- Nguyên tắc này giúp tạo ra code flexible và dễ dàng maintain, vì nó giảm bớt sự phụ thuộc vào các implementation cụ thể. Thay vào đó, nó thúc đẩy việc sử dụng các khái niệm abstractions và interface, làm cho code dễ dàng reuse và replace.

---

- Có thể nói rằng thiết kế linh hoạt đủ nếu có thể dễ dàng mở rộng mà không phá vỡ code hiện có.

- một con mèo có thể ăn bất kỳ loại thức ăn nào linh hoạt hơn một con chỉ có thể ăn xúc xích

- Khi muốn tạo 2 classes tương tác với nhau, có thể để 1 lớp phụ thuộc vào lớp còn lại. Tuy nhiên có 1 cách khác linh hoạt hơn:

	+ Xác định chính xác những gì một object cần từ đối tượng kia: Nó execute những methods nào ?
	+ Mô tả các methods này trong một interface mới hoặc abstract class
	+ Làm cho class là một phụ thuộc implement interface này
	+ 
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	

