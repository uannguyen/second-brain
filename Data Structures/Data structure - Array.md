
# Array (Mảng)

![[ds-array.png]]

>Mảng là một tập hợp các phần tử có cùng kiểu dữ liệu, được sắp xếp theo thứ tự và có thể truy cập thông qua chỉ số (index)

## Properties of array (Thuộc tính):

- Cùng kiểu dữ liệu, mỗi phần tử có cùng kích thước là 4 byte
- Các phần tử được lưu trữ tại các vị trí có bộ nhớ liền kề, phần tử đầu tiền được lưu ở vị trí bộ nhớ nhỏ nhất
- Có thể truy cập ngẫu nhiên (ex: arr[0], arr[1], ...)

## Why are arrays required ? (Tại sao cần có mảng?)

- Sắp xếp & tìm kiếm dễ dàng
- Xử lý nhiều giá trị cùng lúc nhanh chóng, dễ dàng
- Lưu nhiều giá trị chỉ với một biến duy nhất

## Memory allocation of an array (Cấp phát bộ nhớ của mảng)

![[ds-array2.png]]

=> Mảng 5 phần tử, địa chỉ cơ sở của mảng là 100 byte (arr[0]), kích thước dữ liệu là 4 byte

- Cách tính Base Address của một mảng:

```
 Cho arr = [2,4,5,7,9]

 Công thức:
 Byte address of element arr[i]  = base_address + size * (i - first_index)

=> arr[2] = 100 + 4 * (2 - 0)

```

## Complexity (Độ phức tạp)

- **Time Complexity (Thời gian)**

| Operation | Average Case | Worst Case |
| --------- | ------------ | ---------- |
| Access    | O(1)         | O(1)       |
| Search    | O(n)         | O(n)       |
| Insertion | O(n)         | O(n)       |
| Deletion  | O(n)         | O(n)       |

- Space Complexity (Không gian)

> Trường hợp xấu nhất là O(n)

## Advantages (Ưu điểm)

- Truy cập nhanh chóng (thông qua index)
- Duyệt phần tử đơn giản, chỉ cần tăng base address của mảng để truy cập từng phần tử một
- Phù hợp các case cố định kích thước

## Disadvantages (Nhược điểm)

- Mỗi element đồng nhất data type (tùy thuộc vào programming languages)
- Bộ nhớ tĩnh (memory allocation) ko thể thay đổi
- Lãng phí memory nếu lưu trữ element ít hơn size đã khai báo
- Kích thước của mảng phải được biết trước
- Các phần tử được lưu trữ liên tục trong bộ nhớ => chèn một phần tử vào phải dịch chuyển các phần tử khác


# Array 2D (Mảng 2 chiều)

*Là mảng trong mảng, số phần tử của cột & hàng ko nhất thiết phải bằng nhau* 

```json
[
	[ 1, 2, 3 ],
	[ 4, 5, 6 ],
	[ 7, 8, 9 ],
	[ 10, 11, 12 ]
]
```

## Cấu trúc dữ liệu


![[ds-2d-array.png]]

## Mapping 2D array to 1D array

-  Row Major ordering (Thứ tự hàng chính)
	
	![[ds-2d-array-row-major-ordering2.png]]

```js
// Mảng 2D mẫu
const twoDimArray = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];

// Ánh xạ thành mảng 1D bằng Row Major Ordering
const oneDimArray = [];
for (let i = 0; i < twoDimArray.length; i++) {
  for (let j = 0; j < twoDimArray[i].length; j++) {
    oneDimArray.push(twoDimArray[i][j]);
  }
}

console.log(oneDimArray);
// [1, 2, 3, 4, 5, 6, 7, 8, 9]
```


-  Column Major ordering (Thứ tự cột chính)

![[ds-2d-array-column-major-ordering2.png]]

```js
// Mảng 2D mẫu
const twoDimArray = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];

// Ánh xạ thành mảng 1D bằng Column Major Ordering
const oneDimArray = [];
const numRows = twoDimArray.length;
const numCols = twoDimArray[0].length;

for (let j = 0; j < numCols; j++) {
  for (let i = 0; i < numRows; i++) {
    oneDimArray.push(twoDimArray[i][j]);
  }
}

console.log(oneDimArray);
// [1, 4, 7, 2, 5, 8, 3, 6, 9]
```


## Tính Base Address

Theo hàng
Address(a[i][j]) = B. A + (i * n + j) * size   


Theo cột 
Address(a[i][j]) =B.A + ((j * m)+i) * Size 

- B.A là địa chỉ cơ sở (Base Address) của mảng.
- i là chỉ số hàng.
- j là chỉ số cột.
- n là số cột của mảng đa chiều.
- m là số hàng của mảng đa chiều
- Size là kích thước của mỗi phần tử mảng (trong byte).

# Câu hỏi phỏng vấn phổ biến

- Find the second minimum element of an array
- First non-repeating integers in an array
- Merge two sorted arrays
- Rearrange positive and negative values in an array
