
***Khi viết code, nên tập trung vào sử dụng interface thay vì sử dụng implementation***

- Trong OOP, một interface định nghĩa các methods mà một object cần cung cấp, mà không cung cấp implementation cụ thể của chúng. Bằng cách này, khi viết code, chỉ quan tâm đến các methods được định nghĩa trong interface, mà không cần biết cụ thể đối tượng implement interface đó làm thế nào để hoàn thành công việc.

- Nguyên tắc này giúp tạo ra code flexible và dễ dàng maintain, vì nó giảm bớt sự phụ thuộc vào các implementation cụ thể. Thay vào đó, nó thúc đẩy việc sử dụng các khái niệm abstractions và interface, làm cho code dễ dàng reuse và replace.

---

- Có thể nói rằng thiết kế đủ linh hoạt nếu có thể dễ dàng mở rộng mà không phá vỡ code hiện có.

- một con mèo có thể ăn bất kỳ loại thức ăn nào linh hoạt hơn một con chỉ có thể ăn xúc xích

- Khi muốn tạo 2 classes tương tác với nhau, có thể để 1 lớp phụ thuộc vào lớp còn lại. Tuy nhiên có 1 cách khác linh hoạt hơn:

	+ Xác định chính xác những gì một object cần từ đối tượng kia: Nó execute những methods nào ?
	+ Mô tả các methods này trong một interface mới hoặc abstract class
	+ Làm cho class là một phụ thuộc implement interface này
	+ Bây giờ làm cho class thứ hai phụ thuộc vào interface này thay vì class cụ thể. Bạn vẫn có thể làm cho nó hoạt động với các objects của class ban đầu, nhưng kết nối bây giờ linh hoạt hơn nhiều
	

![[oop-14.png]]


***Before...***
```ts
class Cat {
  eat(sausage: Sausage): void {
    // ...
  }
}

class Sausage {
  // ...
}

const cat = new Cat();
const sausage = new Sausage();
cat.eat(sausage);

```
	

***After...***

```ts
interface Food {
  getNutrition: () => string;
}

class Sausage implements Food {
  constructor() {}

  getNutrition() {
    return "Sausage";
  }
}

class Cat {
  energy;
  constructor() {}
  eat(food: Food) {
    return `Eaten: ${food.getNutrition()}`;
  }
}

// create instance
const cat = new Cat();
const sausage = new Sausage();
cat.eat(sausage);

```

	
# Example

- Hãy tưởng tượng rằng bạn đang tạo một trình mô phỏng công ty phát triển phần mềm. Bạn có các lớp khác nhau đại diện cho các loại nhân viên khác nhau.

	![[oop-15.png]]
	

- Ban đầu, class Company Association chặt chẽ với nhau, mặc dù có sự khác biệt trong việc triển khai, chúng ta có thể khái quát các methods liên quan đến các công việc khác nhau

- và sau đó trích xuất một interface chung cho tất cả các class nhân viên

- sau đó, chúng ta có thể apply tính đa hình bên trong Company class, xử lý các objects nhân viên khác nhau thông qua Employee interface
	
	![[oop-16.png]]
	
	
- Company class vẫn gắn liền với các classes nhân viên

=> Điều này ko tốt vì nếu chúng ta giới thiệu các loại companies mới, làm việc với các loại employees khác, chúng ta sẽ override hầu hết class Company thay vì sử dụng lại code đó

- để solve, chúng ta có thể khai báo method getting employees như một abstract. Mỗi concrete company sẽ implement method này khác nhau, chỉ tạo những employees chúng cần

![[oop-17.png]]
	

- Sau khi thay đổi, class Company trở nên độc lập với các classes employees khác nhau




	
	

