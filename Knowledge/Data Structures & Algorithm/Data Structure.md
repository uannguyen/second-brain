**Tổng hợp kiến thức về Data Structure **

Nó là cái gì ?



# ==Array== - Mảng

## Element - Phần tử

## Index - Chỉ mục

## Size - Kích thước

## Truy cập và sửa đổi

## Multidimensional Arrays - Mảng đa chiều

## Thao tác cơ bản
=> 


---

 
# ==Linked List== - Danh sách liên kết

- Lưu trữ nhiều giá trị 

---

# ==Stacks== - Ngăn xếp

- Là một cấu trúc dữ liệu trừu tượng
- Dùng để thực hiện các thao tác chèn và lấy ra theo nguyên tắc "Last In, First Out" (LIFO)
- Thường được sử dụng để theo dõi và quản lý một dãy các phần tử
- Methods:

```text
push(item) Thêm một phần tử vào đỉnh của ngăn xếp.

pop() Loại bỏ và trả về phần tử ở đỉnh của ngăn xếp.  

peek() Trả về phần tử ở đỉnh của ngăn xếp mà không loại bỏ nó.

isEmpty() Kiểm tra xem ngăn xếp có rỗng không.  

size() Trả về số lượng phần tử hiện có trong ngăn xếp.

clear() Loại bỏ tất cả các phần tử khỏi ngăn xếp, làm cho ngăn  
xếp trở thành rỗng.

toArray() Chuyển đổi ngăn xếp thành một mảng.

toString() Chuyển đổi ngăn xếp thành một chuỗi.
```


=> Gợi nhớ: như một chồng sách, quyển nào bỏ vào sau cùng sẽ được lấy ra đầu tiên.

---

# ==Queue== - Hàng đợi


---

# ==Tree== - Cây

![[tree.png]]

## Là cấu trúc dữ liệu thể hiện dữ liệu phân cấp

## Key points - Điểm chính


- Tập hợp các đối tượng, thực thể (node) và liên kết với nhau để thể hiện hoặc mô phỏng một hệ thống phân cấp.
- Phi tuyến tính (ko lưu trữ data 1 cách tuần tự) và là một cấu trúc phân cấp (các phần tử được sắp xếp theo nhiều cấp độ).
- Node gốc ở trên cùng, mỗi node có thể chứa kiểu dữ liệu bất kì.
- Node con chứa dữ liệu và liên kết/tham chiếu từ node cha.

## Basic terms - Thuật ngữ cơ bản

- Root
- Child node - Nút con
- Parent - Nút cha
- Sibling - Anh chị em
- Leaf Node - Nút lá: node ngoài cùng, ko có node con nào.
- Internal nodes - Các nút bên trong: Có ít nhất một nút con.
- Ancestor node - Nút tổ tiên: Nút 1, 2, 5 là tổ tiên của nút 10.
- Descendant - Hậu duệ:  Nút 10 là hậu duệ của nút 5.

## Properties - Thuộc tính

- 




## General Tree - Cây tổng hợp

- Không có bất kì cấu hình & giới hạn số lượng children.

```
       A
     / | \
    B  C  D
       / \
      E   F
     /
    G
```

## Binary Tree - Cây nhị phân

- Tối đa 2 children ở mỗi node

```
	1
 /  \
 9   3
/  \
4   5

```


## Binary Search Tree - Cây tìm kiếm nhị phân 

- Tối đa 2 children ở mỗi node
- Left children < Parent Node < Right children

```
	  1
  /  \
 2    3
/  \    
4   5

```


## AVL Tree - Cây nhị phân đặc biệt








--- 

# ==Graph== - Đồ thị

---

# ==Heap== - Ngăn xếp ưu tiên

---

# ==Hash Table== - Bảng băm

Lưu data theo thứ tự của hàm băm mà không phải thứ tự chèn.

=> Hoàn hảo cho việc tránh trùng lặp data, không tốt lắm nếu cần sắp xếp theo thứ  tự nhất định.


---

# Dictionary - Từ điển

Gồm cặp key: value
Tránh trùng lặp data