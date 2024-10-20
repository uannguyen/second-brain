---
tags:
  - data_structure
---

 
![[queue.png]]

# Khái niệm

- Là cấu trúc dữ liệu dạng tuyến tính (linear) tuân theo nguyên tắc "First in first out" (FIFO)
- Phần tử được thêm vào đầu tiên sẽ được xóa đầu tiên (ngược lại với stack)

# Thuật ngữ

- Enqueue: Thêm 1 element vào phía sau(rear) queue
- Dequeue: Xóa 1 element ở phía trước(front) queue
- 
# Các loại Queues

![[ds-types-of-queue2.png]]

##  Simple Queue or Linear Queue

![[ds-types-of-queue3.png]]


```js
class Queue {
  constructor() {
    this.items = [];
  }

  // Add an element to the rear of the queue
  enqueue(item) {
    this.items.push(item);
  }

  // Remove and return the element at the front of the queue
  dequeue() {
    if (this.isEmpty()) {
      return "Queue is empty";
    }
    return this.items.shift();
  }

  // Return the element at the front of the queue without removing it
  front() {
    if (this.isEmpty()) {
      return "Queue is empty";
    }
    return this.items[0];
  }

  // Check if the queue is empty
  isEmpty() {
    return this.items.length === 0;
  }

  // Get the number of elements in the queue
  size() {
    return this.items.length;
  }
}

// Example usage:
const myQueue = new Queue();
myQueue.enqueue(1);
myQueue.enqueue(2);
myQueue.enqueue(3);

console.log("Queue:", myQueue.items);
console.log("Dequeue:", myQueue.dequeue()); // Removes and returns 1
console.log("Front:", myQueue.front()); // Returns 2
console.log("Queue Size:", myQueue.size()); // Returns 2
console.log("Is Empty:", myQueue.isEmpty()); // Returns false

```

## Circular Queue

![[ds-types-of-queue4.png]]


### Characteristics and features

- **Circular Structure**
- **Fixed Size**
- **FIFO (First-In-First-Out)
- **Enqueue**
- **Dequeue**
- **Circular Wraparound**
- **Efficient Use of Memory**

### Applications

- **Buffering:** Circular queues are used to implement buffers for data transmission, audio, video, or any stream of data. New data is continuously added to the rear of the queue, and old data is overwritten if the buffer is full.
    
- **Task Scheduling:** In operating systems, circular queues are used to implement task scheduling algorithms. Each task is placed in the queue, and the scheduler serves tasks in a circular manner.
    
- **Print Spooling:** Circular queues can manage print jobs in a printer's spooler, ensuring that older jobs are overwritten when new jobs arrive.
    
- **Real-Time Systems:** In real-time systems, circular queues are used for event handling, where events are processed in a circular manner

```js
class CircularQueue {
  constructor(maxSize) {
    this.maxSize = maxSize;
    this.queue = new Array(maxSize);
    this.front = -1;
    this.rear = -1;
    this.size = 0;
  }

  // Check if the queue is empty
  isEmpty() {
    return this.size === 0;
  }

  // Check if the queue is full
  isFull() {
    return this.size === this.maxSize;
  }

  // Enqueue (add) an element to the circular queue
  enqueue(item) {
    if (this.isFull()) {
      console.log("Queue is full. Cannot enqueue.");
      return;
    }

    if (this.isEmpty()) {
      this.front = 0;
    }

    this.rear = (this.rear + 1) % this.maxSize;
    this.queue[this.rear] = item;
    this.size++;
  }

  // Dequeue (remove) an element from the circular queue
  dequeue() {
    if (this.isEmpty()) {
      console.log("Queue is empty. Cannot dequeue.");
      return;
    }

    const item = this.queue[this.front];
    this.front = (this.front + 1) % this.maxSize;
    this.size--;

    if (this.size === 0) {
      this.front = -1;
      this.rear = -1;
    }

    return item;
  }

  // Get the front element without removing it
  peek() {
    if (this.isEmpty()) {
      console.log("Queue is empty. Cannot peek.");
      return;
    }
    return this.queue[this.front];
  }

  // Get the size of the circular queue
  getSize() {
    return this.size;
  }
}

// Example usage:
const maxSize = 5;
const circularQueue = new CircularQueue(maxSize);

circularQueue.enqueue(1);
circularQueue.enqueue(2);
circularQueue.enqueue(3);
circularQueue.enqueue(4);
circularQueue.enqueue(5);

console.log("circularQueue", circularQueue);
/**
 CircularQueue {
  maxSize: 5,
  queue: [ 1, 2, 3, 4, 5 ],
  front: 0,
  rear: 4,
  size: 5
}
 */

```


## Priority Queue

![[ds-types-of-queue5.png]]

- Xếp hàng theo độ ưu tiên, element nào có priority ưu tiên cao nhất sẽ được xếp trước. 
- Thường thì priority càng bé tương ứng mức độ ưu tiên cao hơn (vd: 3,1,2 => 1,2,3)


```js
class PriorityQueue {
  constructor() {
    this.items = [];
  }

  enqueue(element, priority) {
    const queueElement = { element, priority };

    if (this.isEmpty()) {
      this.items.push(queueElement);
    } else {
      let added = false;

      for (let i = 0; i < this.items.length; i++) {
        if (queueElement.priority < this.items[i].priority) {
          this.items.splice(i, 0, queueElement);
          added = true;
          break;
        }
      }

      if (!added) {
        this.items.push(queueElement);
      }
    }
  }

  dequeue() {
    if (this.isEmpty()) {
      return "Underflow";
    }
    return this.items.shift().element;
  }

  front() {
    if (this.isEmpty()) {
      return "No elements in Queue";
    }
    return this.items[0].element;
  }

  isEmpty() {
    return this.items.length === 0;
  }

  size() {
    return this.items.length;
  }

  print() {
    let result = "";
    for (let i = 0; i < this.items.length; i++) {
      result += `${this.items[i].element} - Priority: ${this.items[i].priority}\n`;
    }
    return result;
  }
}

// Example usage:
const priorityQueue = new PriorityQueue();

priorityQueue.enqueue("Task 1", 3);
priorityQueue.enqueue("Task 2", 1);
priorityQueue.enqueue("Task 3", 2);

console.log(priorityQueue.print());
/**
  Task 2 - Priority: 1
  Task 3 - Priority: 2
  Task 1 - Priority: 3
 */

```


# Dequeue - Double Ended Queue


![[ds-deque.png]]

- Khác với queue bình thường phải tuân theo principle FIFO, elements trong dequeue có thể được Add/Remove ở cả 2 đầu của hàng đợi


```js
class Deque {
  constructor() {
    this.items = [];
  }

  // Add element to the front of the deque
  addFront(element) {
    this.items.unshift(element);
  }

  // Add element to the rear of the deque
  addRear(element) {
    this.items.push(element);
  }

  // Remove and return the element from the front of the deque
  removeFront() {
    if (this.isEmpty()) {
      return "Underflow";
    }
    return this.items.shift();
  }

  // Remove and return the element from the rear of the deque
  removeRear() {
    if (this.isEmpty()) {
      return "Underflow";
    }
    return this.items.pop();
  }

  // Return the front element without removing it
  front() {
    if (this.isEmpty()) {
      return "No elements in Deque";
    }
    return this.items[0];
  }

  // Return the rear element without removing it
  rear() {
    if (this.isEmpty()) {
      return "No elements in Deque";
    }
    return this.items[this.items.length - 1];
  }

  // Check if the deque is empty
  isEmpty() {
    return this.items.length === 0;
  }

  // Return the size of the deque
  size() {
    return this.items.length;
  }

  // Print the elements of the deque
  print() {
    let result = "";
    for (let i = 0; i < this.items.length; i++) {
      result += `${this.items[i]} `;
    }
    return result.trim();
  }
}

// Example usage:
const deque = new Deque();

deque.addRear(1);
deque.addRear(2);
deque.addFront(3);

console.log("Deque:", deque.print());
// Deque: 3 1 2
```


## Linked List queue

```js
// Node class to represent each element in the linked list
class Node {
  constructor(data) {
    this.data = data;
    this.next = null;
  }
}

// Linked List Queue class
class LinkedListQueue {
  constructor() {
    this.front = null; // Front of the queue
    this.rear = null; // Rear of the queue
  }

  // Check if the queue is empty
  isEmpty() {
    return this.front === null;
  }

  // Enqueue (add an element to the rear of the queue)
  /**
   Lý do cần lưu cả biến rear & front là vì ngoài lần đầu thêm element vào queue khi nó empty
   thì từ lần sau:
   - gán node mới cho next của rear hiện tại
   - gán node mới = rear hiện tại
   */
  enqueue(data) {
    const newNode = new Node(data);
    if (this.isEmpty()) {
      this.front = newNode;
      this.rear = newNode;
    } else {
      this.rear.next = newNode;
      this.rear = newNode;
    }
  }

  // Dequeue (remove and return the element from the front of the queue)
  dequeue() {
    if (this.isEmpty()) {
      return "Underflow"; // Empty queue
    }

    const removedData = this.front.data;
    this.front = this.front.next;

    if (this.front === null) {
      this.rear = null; // Reset rear if the queue becomes empty
    }

    return removedData;
  }

  // Front (return the element at the front without removing it)
  frontElement() {
    if (this.isEmpty()) {
      return "No elements in Queue";
    }
    return this.front.data;
  }

  // Print the elements of the queue
  printQueue() {
    let result = "";
    let current = this.front;

    while (current !== null) {
      result += `${current.data} `;
      current = current.next;
    }

    return result.trim();
  }
}

// Example usage:
const linkedListQueue = new LinkedListQueue();

linkedListQueue.enqueue(1);
linkedListQueue.enqueue(2);
linkedListQueue.enqueue(3);

console.log(
  "Queue after enqueue:",
  linkedListQueue.printQueue(),
  linkedListQueue
);

// console.log("Dequeue:", linkedListQueue.dequeue());
// console.log("Front:", linkedListQueue.frontElement());

// console.log("Queue after dequeue:", linkedListQueue.printQueue());

```