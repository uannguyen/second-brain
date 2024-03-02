
\* Khái niệm: là một mô hình lập trình dựa trên khái niệm `đóng gói các phần dữ liệu & hành vi liên quan` thành các gói đặc biệt, gọi là các đối tượng, được xây dựng từ một tập hợp các `bản thiết kế`  gọi là các lớp(classes).

# Objects, classes


![[oop-1.png]]

- Giả sử có 1 con mèo tên Oscar
- Oscar là 1 object và là 1 instance của Cat class
- Mỗi cat có nhiều thuộc tính tiêu chuẩn (name, age, sex, ...). Là các field của class
- Tất cả cats cũng có những hành vi tương tự: breathe, eat, run, ... Chúng là các phương thức của class.
- Các fields & methods được tham chiếu như các thành viên của lớp của chúng.

- Dữ liệu được lưu trữ bên trong `các fields của đối tượng thường được tham chiếu dưới dạng State` và tất cả `các methods của đối tượng xác định bahavior của nó`.

	+ State đại diện cho các thuộc tính hoặc thông tin cụ thể về đối tượng
	+ Behavior đại diện cho các methods hoặc features mà đối tượng có thể thực hiện

- Code ex:

```js
class Oscar {
  // Fields (State)
  name;
  sex;
  age;
  weight;
  color;

  // Methods (Behavior)
  breathe() {}
  eat() {}
  run() {}
  sleep() {}
  meow() {}
}

const oscar1 = new Oscar();
// oscar1 là 1 instance của class Oscar

const oscar2 = new Oscar();
// oscar2 là 1 instance của class Oscar

// => mỗi instance được tạo ra là 1 object độc lập và riêng biệt mặc dù chúng giữ 1 bản sao Fields & Methods từ class
```



# Class hierarchies - Hệ thống phân cấp class

- parent class => super classes
- child class => subclasses
- child class kế thừa state & behavior từ parent class
- Childs class có thể mở rộng state & behavior so với parent class, và cũng có thể override chúng.


![[oop-3.png]]

- Class `Cat/Dog` kế thừa mọi thứ từ 2 class parent là `Animal, Organism`

![[oop-4.png]]

- Code example:

```js 
// Superclass 
class Organism {
  // Fields (State)
  name;
  age;

  // Methods (Behavior)
  breathe() {
    console.log("Breathing...");
  }
  eat() {
    console.log("Eating...");
  }
  sleep() {
    console.log("Sleeping...");
  }
}

// Parent class
class Animal extends Organism { // inheritance
  // Fields (State)
  name;
  age;

  // Methods (Behavior)
  breathe() {
    console.log("Breathing...");
  }
  eat() {
    console.log("Eating...");
  }
  sleep() {
    console.log("Sleeping...");
  }
}

// Subclass Cat
class Cat extends Animal { // inheritance
  // Additional field
  color;

  // Additional method
  meow() {
    console.log("Meow!");
  }
}

// Subclass Dog
class Dog extends Animal { // inheritance
  // Additional field
  breed;

  // Additional method
  bark() {
    console.log("Bark!");
  }
}

```