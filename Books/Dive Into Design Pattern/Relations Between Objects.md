\* Khái niệm: Trong OOP, R-B-Objects mô tả các mối quan hệ và tương tác giữa các đối tượng.

# Association - MQH kết hợp

![[oop-8.png]]

- 1 object sử dụng hoặc tương tác với một object khác

- Hiển thị bằng một arrow đơn giản được vẽ từ một object và chỉ vào object mà nó sử dụng

- Có thể có tương tác 2 chiều, trong case này, arrow có một điểm ở mỗi đầu

-  Mqh này có thể tạm thời hoặc lâu dài, mỗi object không nhất thiết phụ thuộc vào object khác.

```ts
class Customer {
    name: string;

    constructor(name: string) {
        this.name = name;
    }
}

class Order {
    customer: Customer;

    constructor(customer: Customer) {
        this.customer = customer;
    }

    getCustomer(): Customer {
        return this.customer;
    }
}

// Tạo một đối tượng Customer
const customer = new Customer("John Doe");

// Tạo một đối tượng Order và liên kết với đối tượng Customer
const order = new Order(customer);

// Truy cập thông tin của đối tượng Customer thông qua mối quan hệ liên kết
const customerOfOrder = order.getCustomer();
console.log(customerOfOrder.name); // Output: John Doe

```


# Dependency - MQH phụ thuộc

![[oop-9.png]]

- Là 1 biến thể yếu hơn của association, do ko có liên kết vĩnh viễn giữa objects

- 1 Object accepts 1 object khác như một method parameter, instantiates, hoặc sử dụng object khác

- Tồn tại giữa 2 classes nếu những thay đổi với definition của 1 class dẫn đến modifications 1 class khác

```ts
class Logger {
  log(message: string) {
    console.log(`[LOG] ${message}`);
  }
}

class UserManager {
  logger: Logger;

  constructor(logger: Logger) {
    this.logger = logger;
  }

  addUser(name: string) {
    this.logger.log(`Adding user: ${name}`);
    // Logic to add user...
  }
}

// class UserManager phụ thuộc vào class Logger
const logger = new Logger();
const userManager = new UserManager(logger);
userManager.addUser("Alice"); // Output: [LOG] Adding user: Alice
```


# Composition - MQH hợp thành


![[oop-10.png]]

- Kiểu 





