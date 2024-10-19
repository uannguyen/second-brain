
- Lưu trữ data theo cặp key-value
- Lưu data theo thứ tự của hàm băm mà không phải thứ tự chèn.
- Map key & value với hashing (băm)
- Key là unique

=> Hoàn hảo cho việc tránh trùng lặp data, không tốt lắm nếu cần sắp xếp theo thứ tự nhất định.

# Code

- Tính toán ra một index của key trong array 

```js
class HashTable {
  constructor(size = 10) {
    this.size = size;
    this.table = new Array(size).fill(null).map(() => []);
  }

  // Hash function to convert a key into an index
  hash(key) {
    let hash = 0;
    for (let i = 0; i < key.length; i++) {
      hash = (hash << 5) + key.charCodeAt(i);
      hash = hash & hash; // Convert to 32-bit integer
      hash = Math.abs(hash); // Ensure non-negative
      hash = hash % this.size; // Ensure within array size
    }
    return hash;
  }

  // Insert a key-value pair into the hash table
  insert(key, value) {
    const index = this.hash(key);
    this.table[index].push({ key, value });
  }

  // Retrieve the value associated with a key
  get(key) {
    const index = this.hash(key);
    const bucket = this.table[index];

    for (const pair of bucket) {
      if (pair.key === key) {
        return pair.value;
      }
    }

    return undefined; // Key not found
  }

  // Check if a key exists in the hash table
  contains(key) {
    const index = this.hash(key);
    const bucket = this.table[index];

    for (const pair of bucket) {
      if (pair.key === key) {
        return true;
      }
    }

    return false; // Key not found
  }
}

// Example usage:
const myHashTable = new HashTable();

myHashTable.insert("name", "John");
myHashTable.insert("age", 25);
myHashTable.insert("city", "Example City");

console.log(myHashTable.get("name")); // Output: John
console.log(myHashTable.get("age")); // Output: 25
console.log(myHashTable.get("city")); // Output: Example City

console.log(myHashTable.contains("name")); // Output: true
console.log(myHashTable.contains("gender")); // Output: false

```


# Hashtable Separate Chaining

![[hash-table.png]]

- Giả sử khi hash 2 cặp key-value khác nhau, tuy nhiên lại cho ra cùng một index (do Array size ko đủ lớn) thì cần phải xử lý đó là lưu value cho cái index bị trùng đấy dạng Array, Link list, ...

# Ứng dụng

- Đếm giá trị lặp lại (VD đếm các chữ cái trùng lặp trong một chuỗi các chữ cái)