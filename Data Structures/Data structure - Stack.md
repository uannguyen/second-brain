---
tags:
  - data_structure
---


# Stacks (Ngăn xếp) 

![[stack.webp]]

## Khái niệm

- Là một cấu trúc dữ liệu tuyến tính (linear)
- Dùng để thực hiện các thao tác chèn và lấy ra theo nguyên tắc "Last In, First Out" (LIFO)
- Thường được sử dụng để theo dõi và quản lý một dãy các phần tử
- Dung lượng được xác định trước, tức là kích thước có giới hạn, nếu quá tải sẽ bị stack overflown

# Trách nhiệm

- **Quản lý Call Stack**: 

```js
// thirdFunction sẽ thực hiện xong đầu tiên và được xóa khỏi call stack, sau đó là secondFunction và firstFunction.

function firstFunction() {
  console.log("First function");
  secondFunction();
}

function secondFunction() {
  console.log("Second function");
  thirdFunction(); 
}

function thirdFunction() {
  console.log("Third function");
}

firstFunction(); 

```


- **Theo dõi biến cục bộ trong methods**:

```js
export const Type = {}; // global
class Heap {
  constructor() {}
  x = 0; // local
  hello() {
    const y = 0; // local
  }
}

```

## Methods

```js
push() // Thêm một phần tử vào đỉnh của ngăn xếp.

pop() // Loại bỏ và trả về phần tử ở đỉnh của ngăn xếp.

peek() // Trả về phần tử ở đỉnh của ngăn xếp mà không loại bỏ nó.

isEmpty() // Kiểm tra xem ngăn xếp có rỗng không.

size() // Trả về số lượng phần tử hiện có trong ngăn xếp.

clear() // Loại bỏ tất cả các phần tử khỏi ngăn xếp, làm cho ngăn xếp trở thành rỗng.

toArray() // Chuyển đổi ngăn xếp thành một mảng.

toString() // Chuyển đổi ngăn xếp thành một chuỗi.
```

=> Gợi nhớ: như một chồng sách, quyển nào bỏ vào sau cùng sẽ được lấy ra đầu tiên.

# Ứng dụng thực tế

- Open/Close ngoặc khi viết code
- History của browser (Quay lại/Chuyển tiếp trang)
- Ctrl + Z => undo
- Call func (mỗi func được call thì sẽ đẩy vào stack, khi handle xong thì lại xóa đi)

# Các loại Stack

- Với mảng (Array implementation of Stack): 

```js
class StackArray {
  constructor() {
    this.items = [];
  }

  push(item) {
    this.items.push(item);
  }

  pop() {
    if (this.isEmpty()) {
      return "Stack is empty";
    }
    return this.items.pop();
  }

  peek() {
    if (this.isEmpty()) {
      return "Stack is empty";
    }
    return this.items[this.items.length - 1];
  }

  isEmpty() {
    return this.items.length === 0;
  }

  size() {
    return this.items.length;
  }
}

// Sử dụng stack với mảng
const stackUsingArray = new StackArray();
stackUsingArray.push(1);
stackUsingArray.push(2);
stackUsingArray.push(3);

console.log(stackUsingArray.pop()); // 3
console.log(stackUsingArray.pop()); // 2
console.log(stackUsingArray.size()); // 1

```


- Với Linked List:

```js
class Node {
  constructor(data) {
    this.data = data;
    this.next = null;
  }
}

class StackLinkedList {
  constructor() {
    this.top = null;
  }

  push(item) {
    const newNode = new Node(item);
    newNode.next = this.top;
    this.top = newNode;
  }

  pop() {
    if (this.isEmpty()) {
      return "Stack is empty";
    }
    const item = this.top.data;
    this.top = this.top.next;
    return item;
  }

  peek() {
    if (this.isEmpty()) {
      return "Stack is empty";
    }
    return this.top.data;
  }

  isEmpty() {
    return this.top === null;
  }
}

// Sử dụng stack với danh sách liên kết
const stackUsingLinkedList = new StackLinkedList();
stackUsingLinkedList.push(1);
stackUsingLinkedList.push(2);
stackUsingLinkedList.push(3);

console.log(stackUsingLinkedList.pop()); // 3
console.log(stackUsingLinkedList.pop()); // 2
console.log(stackUsingLinkedList.isEmpty()); // false

```


# Câu hỏi interview phổ biến

- Evaluate postfix expression using a stack
- Sort values in a stack
- Check balanced parentheses in an expression
- 