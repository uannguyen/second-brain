
\* Lập trình hướng đối tượng dựa trên bốn trụ cột, các khái niệm này phân biệt nó với các mô hình lập trình khác.


# Abstract - Trừu tượng

- Abstraction là 1 mô hình của đối tượng hoặc hiện tượng trong thế giới thực.
- Giới hạn trong một bối cảnh cụ thể
- Đại diện cho tất cả các chi tiết liên quan đến bối cảnh này với độ chính xác cao và bỏ qua các phần còn lại


![[oop-5.png]]

\* Mô tả: 
- Một class Airplane có thể tồn tại ở:
	1) Mô phỏng chuyến bay
	2) Booking vé máy bay
=> Ở case 1 class này giữ các chi tiết liên quan đến chuyến bay thực tế
=> Ở case 2, class chỉ quan tâm đến sơ đồ chỗ ngồi & chỗ ngồi nào có sẵn

# Encapsulation - Đóng gói

### Khái niệm

- Encapsulation là khả năng của một object ẩn các phần state và behavior của nó khỏi các object khác, chỉ hiển thị một giao diện hạn chế cho phần còn lại của chương trình
- Đóng gói một cái gì đó có nghĩa là làm cho nó private, và do đó chỉ có thể truy cập được từ bên trong methods của class riêng của nó. 
- Có một chế độ ít hạn chế hơn một chút được gọi là bảo vệ làm cho một thành viên của một class cũng có sẵn cho các subclasses
- Code Ex: 

```js
class Car {
    constructor(make, model, year) {
        this._make = make;    // Thuộc tính được ẩn
        this._model = model;  // Thuộc tính được ẩn
        this._year = year;    // Thuộc tính được ẩn
        this._isEngineStarted = false;  // Thuộc tính được ẩn
    }

    // Phương thức công khai để bắt đầu động cơ
    startEngine() {
        this._isEngineStarted = true;
        console.log("Động cơ đã được khởi động.");
    }

    // Phương thức công khai để dừng động cơ
    stopEngine() {
        this._isEngineStarted = false;
        console.log("Động cơ đã được tắt.");
    }

    // Phương thức công khai để kiểm tra trạng thái động cơ
    isEngineStarted() {
        return this._isEngineStarted;
    }
}

// Sử dụng
let myCar = new Car("Toyota", "Camry", 2020);
console.log("Trạng thái động cơ:", myCar.isEngineStarted()); // false, vì động cơ chưa được khởi động
myCar.startEngine(); // Khởi động động cơ
console.log("Trạng thái động cơ:", myCar.isEngineStarted()); // true, vì động cơ đã được khởi động
myCar.stopEngine(); // Tắt động cơ
console.log("Trạng thái động cơ:", myCar.isEngineStarted()); // false, vì động cơ đã được tắt

```


### Implement

![[oop-6.png]]

- Có FlyingTransport interface với method fly(origin, destination, passengers)
- Khi thiết kế một "Vận tải hàng không" simulator, có thể hạn chế Airport class để chỉ làm việc với các đối tượng triển khai FlyingTransport interface. 
- Sau đó bạn có thể chắc chắn rằng bất kỳ đối tượng nào được chuyển đến một đối tượng sân bay, cho dù đó là Máy bay, Trực thăng hay quái đản,... sẽ có thể đến hoặc khởi hành từ loại sân bay này

```ts
// Định nghĩa giao diện 'FlyingTransport'
interface FlyingTransport {
    fly(origin: string, destination: string, passengers: number): void;
}

// Lớp 'Airplane' triển khai giao diện 'FlyingTransport'
class Airplane implements FlyingTransport {
    fly(origin: string, destination: string, passengers: number): void {
        console.log(`Đang bay từ ${origin} đến ${destination} với ${passengers} hành khách.`);
    }
}

// Lớp 'Helicopter' triển khai giao diện 'FlyingTransport'
class Helicopter implements FlyingTransport {
    fly(origin: string, destination: string, passengers: number): void {
        console.log(`Đang bay từ ${origin} đến ${destination} với ${passengers} hành khách.`);
    }
}

// Lớp 'Airport' tương tác chỉ với các đối tượng triển khai giao diện 'FlyingTransport'
class Airport {
    private _flyingTransports: FlyingTransport[] = [];

    // Phương thức để thêm flying transport vào sân bay
    addFlyingTransport(flyingTransport: FlyingTransport): void {
        this._flyingTransports.push(flyingTransport);
    }

    // Phương thức để phục vụ một chuyến bay
    serveFlight(origin: string, destination: string, passengers: number): void {
        this._flyingTransports.forEach(flyingTransport => {
            flyingTransport.fly(origin, destination, passengers);
        });
    }
}

// Sử dụng
const airport = new Airport();

const airplane = new Airplane();
const helicopter = new Helicopter();

airport.addFlyingTransport(airplane);
airport.addFlyingTransport(helicopter);

airport.serveFlight("Hanoi", "Ho Chi Minh", 150);
```


# Inheritance - Kế thừa

\* Khái niệm: Kế thừa là khả năng xây dựng các class mới trên các class hiện có.

- Hệ quả của việc sử dụng kế thừa là subclasses có cùng interface với parent class.
- Không thể ẩn một method trong subclasses nếu nó được khai báo ở superclass. 
- Subclass phải implement tất cả abstract methods của parent class ngay cả khi chúng không có ý nghĩa
- Subclass chỉ có thể extend 1 superclass
- Mặt khác, class có thể implement nhiều interfaces cùng 1 lúc, tuy nhiên nếu superclass implement interface nào đó thì tất cả subclasses đều phải implement interface đó.

Code ex:

```ts
// Lớp cha với một phương thức trừu tượng và một phương thức thông thường
abstract class Animal {
    abstract makeSound(): void;

		// không phải là abstract method nên không required
    eat(): void {
        console.log('Animal is eating...');
    }
}

// Lớp con kế thừa từ lớp cha
class Dog extends Animal {
// method này required, do class Dog kế thừa từ abstract class Animal nên những abstract methods phải được triển khai.
    makeSound(): void {
        console.log('Woof woof!');
    }
}
```


# Polymorphism - Đa hình

\* Khái niệm: Polymorphism là khả năng của một program phát hiện real class của một object và gọi việc implementation nó ngay cả khi real type của nó không được biết trong current context

- Polymorphism  là khả năng của các object trong OOP để thay đổi hành vi của chúng dựa trên loại của object được gọi
- Polymorphism cho phép một program gọi một method của một object mà không cần biết object đó thuộc về lớp nào cụ thể, mà chỉ cần biết object đó triển khai method đó
- Cho phép các object của các subclass có thể được xử lý như là các object của superclass của chúng. Cụ thể, polymorphism cho phép các  methods của  superclasses có thể được override trong các subclasses và được gọi một cách động dựa trên loại của đối tượng được tạo trong thời gian chạy

![[oop-7.png]]

Code ex:

```ts
// Lớp cha
class Animal {
  sound: string;

  constructor(sound: string) {
    this.sound = sound;
  }

  makeSound(): void {
    console.log(this.sound);
  }
}

// Lớp con kế thừa từ lớp cha và ghi đè phương thức makeSound()
class Dog extends Animal {
  constructor() {
    super("Woof woof!");
  }
}

// Lớp con khác kế thừa từ lớp cha và ghi đè phương thức makeSound()
class Cat extends Animal {
  constructor() {
    super("Meow meow!");
  }
}

// Hàm sử dụng polymorphism
function makeAnimalSound(animal: Animal): void {
  animal.makeSound();
}

// Sử dụng
const dog = new Dog();
const cat = new Cat();

makeAnimalSound(dog); // Output: Woof woof!
makeAnimalSound(cat); // Output: Meow meow!

```

- Ví dụ trên ta thấy func `makeAnimalSound` thực thi method `makeSound` và không cần biết đối số `animal` truyền vào là của `cat` hay `dog` mà chỉ cần quan tâm chúng đều thực thi method `makeAnimalSound`
