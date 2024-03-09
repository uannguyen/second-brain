
***Thành phần ưu tiên hơn thừa kế***

# Khái niệm

- Kế thừa(inheritance) rõ ràng và dễ nhất để reuse code giữa các classes.
- Tuy nhiên inheritance đi kèm với những cảnh báo rõ ràng khi program đã có hàng tấn class & giờ đây thay đổi anything là rất khó khăn

# Một số khó khăn

### Một lớp con không thể bỏ bớt interface của superclass


```ts
// Lớp cha
abstract class Animal {
  // Phương thức trừu tượng "bay"
  abstract fly(): void;

  // Phương thức không trừu tượng
  move(): void {
    console.log("Moving...");
  }
}

// Lớp con 1: Cat
class Cat extends Animal {
  eat() {
    console.log("Rice");
  }
  // mặc dù class Cat ko cần dùng method fly này nhưng vẫn phải declare vì class cha Animal có abstrac method fly
  fly(): void {
    console.log("Meow!");
  }
}

```

###