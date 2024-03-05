# Khái niệm 

- SOLID là 5 nguyên tắc quan trọng khi thiết kế phần mềm nhằm thiết kế mã nguồn linh hoạt, dễ bảo trì và mở rộng.
- Được thiết lập để giúp phát triển phần mềm có tính tái sử dụng cao, dễ đọc.

# Định nghĩa

## 1. S (Single Responsibility Principle)

> ***Nguyên tắc trách nhiệm duy nhất***

- Mỗi class hoặc module nên chỉ có một trách nhiệm duy nhất. Điều này giúp dễ bảo trì và hiểu mã nguồn.

```js
// Đây là một module thực hiện chức năng tính toán
class Calculator {
  static add(a, b) {
    return a + b;
  }

  static subtract(a, b) {
    return a - b;
  }
}

// Đây là một module thực hiện chức năng hiển thị kết quả
class ResultDisplayer {
  static display(result) {
    console.log(`Kết quả là: ${result}`);
  }
}

// Sử dụng hai module trên để thực hiện tính toán và hiển thị kết quả
const a = 5;
const b = 3;

const sum = Calculator.add(a, b);
ResultDisplayer.display(sum);

```

### 2. O (Open/Closed Principle)

>***Nguyên tắc Mở/Đóng***

- Một class nên được thiết kế để có thể mở rộng mà không làm thay đổi mã nguồn hiện tại.

```js
// Không tốt: Phải sửa đổi mã nguồn để thêm chức năng mới
class Rectangle {
  width: number;
  height: number;

  constructor(w: number, h: number) {
    this.width = w;
    this.height = h;
  }
}

// Không tốt: Phải sửa đổi mã nguồn để thêm chức năng mới
class Circle {
  radius: number;

  constructor(r: number) {
    this.radius = r;
  }
}

// Tốt: Sử dụng OC-P, mở rộng thông qua kế thừa và sử dụng interface
interface Shape {
  area(): number;
}

class Rectangle implements Shape {
  width: number;
  height: number;

  constructor(w: number, h: number) {
    this.width = w;
    this.height = h;
  }

  area(): number {
    return this.width * this.height;
  }
}

class Circle implements Shape {
  radius: number;

  constructor(r: number) {
    this.radius = r;
  }

  area(): number {
    return Math.PI * this.radius * this.radius;
  }
}

```
## 3. L (Liskov Substitution Principle)

>***Nguyên tắc thay thế Liskov***

- Trong một chương trình, các object của class con có thể thay thế class cha mà không làm thay đổi tính đúng đắn của chương trình.

```json
// Không tốt: Violating LSP
class Bird {
  fly() {
    console.log("I can fly");
  }
}

class Penguin extends Bird {
  // Penguins can't fly, violating LSP
  fly() {
    console.log("I can't fly");
  }
}

// Tốt: Keeping LSP
interface Flyable {
  fly(): void;
}

class Bird implements Flyable {
  fly() {
    console.log("I can fly");
  }
}

class Penguin implements Flyable {
  fly() {
    console.log("I can't fly");
  }
}
```

## 4. I (Interface Segregation Principle)

>***Nguyên tắc phân tách Interface***

- Thay vì dùng 1 interface lớn, ta nên tách thành nhiều interface nhỏ, với nhiều mục đích cụ thể.

```js
// Không tốt: Violating ISP
interface Worker {
  work(): void;
  eat(): void; // Violating ISP for workers who don't eat during work
}

class OfficeWorker implements Worker {
  work() {
    console.log("Working in the office");
  }

  eat() {
    console.log("Eating lunch");
  }
}

// Tốt: Following ISP
interface Workable {
  work(): void;
}

interface Eatable {
  eat(): void;
}

class OfficeWorker implements Workable, Eatable {
  work() {
    console.log("Working in the office");
  }

  eat() {
    console.log("Eating lunch");
  }
}

```

## 5. D (Dependency Inversion Principle)

>***Nguyên tắc đảo ngược phụ thuộc***

- Các module cấp cao không nên phụ thuộc trực tiếp vào các module cấp thấp.
- Cả hai nên phụ thuộc vào các abstraction. Abstraction không nên phụ thuộc vào chi tiết; chi tiết nên phụ thuộc vào abstraction.

```js
// Không tốt: High-level module depends on low-level module
class LightBulb {
  turnOn() {
    console.log("LightBulb turned on");
  }

  turnOff() {
    console.log("LightBulb turned off");
  }
}

class Switch {
  bulb: LightBulb;

  constructor(bulb: LightBulb) {
    this.bulb = bulb;
  }

  operate() {
    // High-level module (Switch) depends on low-level module (LightBulb)
    if (/* some condition */) {
      this.bulb.turnOn();
    } else {
      this.bulb.turnOff();
    }
  }
}

// Tốt: Following DIP
interface Switchable {
  turnOn(): void;
  turnOff(): void;
}

class LightBulb implements Switchable {
  turnOn() {
    console.log("LightBulb turned on");
  }

  turnOff() {
    console.log("LightBulb turned off");
  }
}

class Switch {
  device: Switchable;

  constructor(device: Switchable) {
    this.device = device;
  }

  operate() {
    // High-level module (Switch) depends on abstraction (Switchable)
    if (/* some condition */) {
      this.device.turnOn();
    } else {
      this.device.turnOff();
    }
  }
}

```

