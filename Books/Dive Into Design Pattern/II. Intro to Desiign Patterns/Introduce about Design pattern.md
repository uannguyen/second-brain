
# Design pattern là gì ?

- Là giải pháp điển hình cho các vấn đề thường xảy ra trong software design. Giống như bản thiết kế được tạo sẵn có thể tùy chỉnh để giải quyết vấn đề thiết kế định kỳ trong code.

- Pattern không thể chỉ đơn giản là tìm và sao chép vào program như cách có thể làm với funtions or libraries có sẵn.
- Một pattern không phải là một đoạn code cụ thể, mà là một khái niệm chung để giải quyết một vấn đề cụ thể.
- Có thể theo dõi các chi tiết của pattern và implement một giải pháp phù hợp với hiện thực của chương trình của bạn. 

- Pattern khá giống với Algorithm:
	- Algorithm thường mô tả một tập hợp rõ ràng các hành động để đạt được một mục tiêu cụ thể
	- Pattern là một mô tả cấp cao hơn về một solution, không chỉ mô tả cách giải quyết vấn đề mà còn cung cấp một cái nhìn tổng quan về solution mà không cung cấp chi tiết cụ thể của steps hay thứ tự thực hiện
	- Code của cùng 1 pattern được áp dụng cho 2 program khác nhau có thể khác nhau

	- Một sự tương tự là công thức nấu ăn:
		- Cả 2 đều có các bước cụ thể để đạt được một mục tiêu
		- Nhưng một pattern lại giống như một bản thiết kế:  thấy kết quả và đặc điểm của nó, nhưng có thể tự quyết định thứ tự cụ thể của việc thực hiện

# Pattern bao gồm những gì ?


- **Intent** (**Mục đích**): Mô tả ngắn gọn cả vấn đề và giải pháp
	- Cung cấp cái nhìn tổng quan về lý do tại sao mẫu thiết kế được sử dụng và những vấn đề cụ thể mà nó giải quyết
	
- **Motivation** (**Dẫn chứng**): Giải thích thêm về vấn đề và giải pháp mà mẫu thiết kế làm cho nó trở nên khả thi
	- Cung cấp một cái nhìn chi tiết hơn về nguyên nhân và lý do tại sao mẫu thiết kế được áp dụng, và làm thế nào nó giải quyết vấn đề được mô tả

- **Structure** (**Cấu trúc**): Hiển thị mỗi phần của mẫu thiết kế và cách chúng liên quan đến nhau
	- Có thể hiểu được các thành phần cơ bản của mẫu thiết kế và cách chúng tương tác với nhau để tạo ra một giải pháp hoàn chỉnh

- **Code Example**(**Ví dụ mã**): Cho ví dụ cụ thể của 1 program language để dễ hiểu và hình dung


# Phân loại patterns

\* Design pattern khác nhau bởi sự phức tạp, mức độ chi tiết và quy mô của ứng dụng được thiết kế

\* Patterns cơ bản và cấp thấp nhất thường được gọi là idioms
\* Idioms thường apply only single programing language

\* Patterns phổ quát nhất và cấp cao là architectural patterns.
\* Architectural patterns có thể implement cho hầu hết mọi programing language
> - Ví dụ, một mẫu kiến trúc phổ biến là MVC (Model-View-Controller), nó quy định cách dữ liệu (Model), giao diện người dùng (View) và logic điều khiển (Controller) tương tác với nhau trong một ứng dụng web.
> - Một ví dụ khác là mẫu kiến trúc Microservices, nó mô tả cách một ứng dụng được phân chia thành các dịch vụ độc lập nhau, mỗi dịch vụ chỉ chịu trách nhiệm cho một phần nhỏ cụ thể của chức năng tổng thể của ứng dụng. Điều này giúp tăng tính mở rộng, hiệu suất và quản lý của hệ thống



### **Creational Patterns:**
- Cung cấp cơ chế tạo object để tăng tính linh hoạt và tái sử dụng code hiện có

```ts
--- Factory Pattern

/*
	Một method hoặc class được sử dụng để tạo ra các object mà không cần phải chỉ định rõ class cụ thể của object đó
*/

// Abstract Product
interface Product {
  operation(): string;
}

// Concrete Products
class ConcreteProduct1 implements Product {
  operation(): string {
    return "ConcreteProduct1";
  }
}

class ConcreteProduct2 implements Product {
  operation(): string {
    return "ConcreteProduct2";
  }
}

// Creator
abstract class Creator {
  abstract factoryMethod(): Product;

  someOperation(): string {
    const product = this.factoryMethod();
    return `Creator: The same creator's code has just worked with ${product.operation()}`;
  }
}

// Concrete Creators
class ConcreteCreator1 extends Creator {
  factoryMethod(): Product {
    return new ConcreteProduct1();
  }
}

class ConcreteCreator2 extends Creator {
  factoryMethod(): Product {
    return new ConcreteProduct2();
  }
}

// Client Code
function clientCode(creator: Creator) {
  console.log(creator.someOperation());
}

clientCode(new ConcreteCreator1());
clientCode(new ConcreteCreator2());

```


### **Structural patterns:** 

- Giải thích cách lắp ráp objects & class thành các cấu trúc lớn hơn, trong khi vẫn giữ cho các cấu trúc linh hoạt và hiệu quả


```ts
--- Composite Pattern
/*
 Một object có thể bao gồm một hoặc nhiều objects khác theo cùng một interface chung, tạo thành một cấu trúc cây
*/

// Component
interface Component {
  operation(): string;
}

// Leaf
class Leaf implements Component {
  operation(): string {
      return 'Leaf';
  }
}

// Composite
class Composite implements Component {
  protected children: Component[] = [];

  add(component: Component): void {
      this.children.push(component);
  }

  remove(component: Component): void {
      const componentIndex = this.children.indexOf(component);
      if (componentIndex !== -1) {
          this.children.splice(componentIndex, 1);
      }
  }

  operation(): string {
      const results: string[] = [];
      this.children.forEach(child => {
          results.push(child.operation());
      });
      return `Branch(${results.join('+')})`;
  }
}

// Client Code
const leaf1 = new Leaf();
const leaf2 = new Leaf();
const composite = new Composite();
const composite2 = new Composite();

composite.add(leaf1);
composite.add(leaf2);
composite2.add(composite);
console.log(composite2.operation());

```



### **Behavioral patterns:**

- Chăm sóc giao tiếp hiệu quả và phân công trách nhiệm giữa các objects.


```ts
--- Observer Pattern

/*
	Nơi một object (được gọi là Subject) duy trì danh sách các đối tượng quan sát (Observers) và thông báo cho chúng khi trạng thái của nó thay đổi. Điều này giúp các đối tượng liên quan đến nhau có thể tương tác mà không cần biết đến sự tồn tại của nhau
*/


// Subject
interface Subject {
  attach(observer: Observer): void;
  detach(observer: Observer): void;
  notify(): void;
}

// Concrete Subject
class ConcreteSubject implements Subject {
  private observers: Observer[] = [];

  attach(observer: Observer): void {
      this.observers.push(observer);
  }

  detach(observer: Observer): void {
      const observerIndex = this.observers.indexOf(observer);
      if (observerIndex !== -1) {
          this.observers.splice(observerIndex, 1);
      }
  }

  notify(): void {
      console.log('ConcreteSubject: Notifying observers...');
      this.observers.forEach(observer => {
          observer.update(this);
      });
  }

  someBusinessLogic(): void {
      console.log('\nConcreteSubject: I\'m doing something important.');
      this.notify();
  }
}

// Observer
interface Observer {
  update(subject: Subject): void;
}

// Concrete Observer
class ConcreteObserverA implements Observer {
  update(subject: Subject): void {
      if (subject instanceof ConcreteSubject) {
          console.log('ConcreteObserverA: Reacted to the event.');
      }
  }
}

class ConcreteObserverB implements Observer {
  update(subject: Subject): void {
      if (subject instanceof ConcreteSubject) {
          console.log('ConcreteObserverB: Reacted to the event.');
      }
  }
}

// Client Code
const subject = new ConcreteSubject();
const observerA = new ConcreteObserverA();
const observerB = new ConcreteObserverB();

subject.attach(observerA);
subject.attach(observerB);

subject.someBusinessLogic();
subject.detach(observerB);

subject.someBusinessLogic();

```


# Why Should I Learn Patterns?

- **Design patterns**: là một bộ công cụ gồm các giải pháp đã được thử nghiệm và kiểm tra cho các vấn đề phổ biến trong sofware design
- Giúp giải quyết tất cả các vấn đề bằng cách sử dụng principles của object-oriented design.
- Các mẫu thiết kế xác định một ngôn ngữ chung mà bạn và đồng đội của bạn có thể sử dụng để giao tiếp hiệu quả hơn. Bạn có thể nói, "Ồ, chỉ cần sử dụng Singleton cho điều đó", và mọi người sẽ hiểu ý tưởng đằng sau đề xuất của bạn. Không cần phải giải thích singleton là gì nếu bạn biết mẫu và tên của nó