****Là kiểu dữ liệu của một biến***

# Primitive Data Types - Kiểu Dữ Liệu Nguyên Thủy

## Interger - Số nguyên

=> 0 ---> 9
![[Knowledge/Data Structures/Untitled.canvas]]
## Floating - Số thực, số thập phân

=> 0,1 ...

## Characters - Ký tự

=> `Chữ cái, Số, Biểu tượng, Ký tự đặc biệt, ...`

## Boolean

=> `True/False`

## String - Chuỗi

=> `"Hello World !"`

---
# Composite Data Types - Kiểu dữ liệu cấu trúc

-  Array - Mảng

=> `[{ ... }, { ... }]`

-  Object - Đối tượng

=> `{ key: value, ... }`

## **Special Data Types**

## Null và Undefined

## Function - Hàm

# User-Defined Data Types - Kiểu Dữ Liệu Tự Định Nghĩa

=> Tùy vào ngôn ngữ lập trình, cho phép tự định nghĩa và tạo cấu trúc dữ liệu phức tạp và tùy chỉnh riêng (`class` , `struct`, `...`)

```ts
// Có một ứng dụng quản lý thư viện => thông tin về sách như tên sách, tác giả, năm xuất bản, và số lượng.

// Tạo một kiểu dữ liệu mới cho Book
 type Book = { 
	 title: string; 
	 author: string;
 }; 
// Sử dụng kiểu dữ liệu Book để tạo biến sách
 const myBook: Book = { 
	 title: "Text",
	 author: "Text"
 }
```

# Kiểu Dữ Liệu Generic

=> Tùy vào ngôn ngữ lập trình, đa dạng và có thể tái sử dụng.

```ts
// Ta có Array<T> => T có thể là number, string, ...
const numberArray: Array<number> = [1, 2, 3, 4, 5];
const stringArray: Array<string> = ["apple", "banana", "cherry"];

```