---
tags:
  - algorithm
---


Đo lường mức độ tăng của thời gian hoặc tài nguyên (thường là bộ nhớ) mà một thuật toán sử dụng khi đầu vào của nó tăng lên. Hiểu được hiệu suất của thuật toán trong các tình huống khác nhau và giúp chọn lựa thuật toán phù hợp cho một vấn đề cụ thể_


# **Time complexity (Thời gian)**

- Thời gian để hoàn thành một nhiệm vụ cụ thể
- Phụ thuộc vào kích thước data đầu vào
- Thuật toán có độ phức tạp thời gian thấp hơn thường được ưa chuộng vì chúng chạy nhanh hơn== trên lượng dữ liệu lớn
- Các loại biểu đồ phổ biến:

1. **O(1) (hằng số)**
     => Thời gian thực hiện không phụ thuộc vào kích thước input

```
	const arr = [2,1,4,...,100]
	arr[1]
	arr[100]
	=> truy cập giá trị cùng 1 mốc thời gian
```

2. **O(log n) - Logarithmic:** 
 -  Độ phức tạp này tăng chậm hơn theo cấp số học. 
 - Chia dữ liệu thành các phần nhỏ hơn và loại trừ một phần của dữ liệu trong mỗi bước.
 - Tìm kiếm hiệu quả trên DS lớn hơn mà không cần nhiều bước so sánh
 
 ```
**Ví dụ:** 
 Cho môt mảng (đã sắp xếp) các số nguyên từ 1-100, tìm giá trị 99 ở trong mảng.

 => Dùng thuật toán "Binary Search" để giải quyết
```

3. **O(n) - Tuyến Tính:** 
 - Độ phức tạp này tăng tỷ lệ tuyến tính với số lượng phần tử đầu vào. 
 - Thường phải duyệt qua tất cả các phần tử ít nhất một lần.
 
```
 **Ví dụ:** 
 Duyệt qua danh sách các môn học trong một trường học để tìm môn  học có số sinh viên nhiều nhất. Nếu có 100 môn học, bạn phải     kiểm tra tất cả 100 môn.
```

4. **O(n log n) - Quasilinear:** 
 - Độ phức tạp này tăng chậm hơn so với O(n^2) nhưng nhanh hơn so với O(n).

```
**Ví dụ:** 
Sắp xếp một danh sách chưa sắp xếp. Thuật toán sắp xếp nhanh (Quick Sort) có độ phức tạp O(n log n).
```
   
5. **O(n^2) - Quadratic:** 
 - Độ phức tạp này tăng theo bình phương của số lượng phần tử đầu vào.
 - Thường cần lặp qua tất cả cặp phần tử.

```
**Ví dụ:** 
Sắp xếp một danh sách bằng thuật toán sắp xếp nổi bọt (Bubble Sort). Độ phức tạp là O(n^2).
```

6. **O(2^n) - Exponential:** 
 - Độ phức tạp này tăng theo cấp số học rất nhanh và là một trong những độ phức tạp tồi nhất. 
 - Một thuật toán với độ phức tạp này thường phải duyệt qua tất cả các tập con của đầu vào.

```
**Ví dụ:**
Giải thuật động lực cho bài toán thập hàm (Traveling Salesman Problem) không tối ưu. Độ phức tạp là O(2^n).
```


# **Space complexity (Không gian)**

- Lượng bộ nhớ mà mà thuật toán sử dụng để hoàn thành nhiệm vụ
- Phụ thuộc vào kích thước data đầu vào
- Thuật toán có độ phức tạp không gian thấp hơn thường được ưa chuộng trên các hệ thống có tài nguyên hạn chế
