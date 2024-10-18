
```ts
// <T> là kiểu dữ liệu 
interface Iterator<T> {
  getNext(): T | null;
  hasMore(): boolean;
}

// sử dụng
class NumberIterator implements Iterator<number> {
}

class ArrayIterator implements Iterator<number[]> {
}
```
