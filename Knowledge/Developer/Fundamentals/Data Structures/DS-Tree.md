

# Tree - Cây

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