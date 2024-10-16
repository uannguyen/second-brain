# Định nghĩa

![[memory-management.png]]

- Là quá trình cấp phát bộ nhớ, sử dụng và giải phóng khi không còn dùng nữa.

# Tổng quan

- Những ngôn ngữ bậc thấp như C có cơ chế quản lý bộ nhớ như `malloc()` và `free()`.
- Tuy nhiên những ngôn ngữ bậc cao như `JS` thì quá trình này lại được auto, gọi là `garbage collection` 

# Khái niệm chính

### 1. Cấp Phát Bộ Nhớ (Memory Allocation)

- **Static Allocation:** Cấp phát tại thời điểm biên dịch, và không thể thay đổi kích thước sau khi biên dịch.
- **Dynamic Allocation:** Cấp phát tại thời điểm run, cho phép tăng giảm kích thước theo nhu cầu.

### 2. Giải Phóng Bộ Nhớ (Memory Deallocation)

- **Manual Deallocation:** Lập trình viên phải tự giải phóng bộ nhớ khi không còn cần sử dụng nữa.
- **Automatic Deallocation (Garbage Collection):** Hệ thống tự động giải phóng bộ nhớ không còn sử dụng, giảm gánh nặng cho lập trình viên.

### 3. Memory Leaks (Rò Bộ Nhớ)

- Xảy ra khi một phần của bộ nhớ được cấp phát nhưng không bao giờ được giải phóng, dẫn đến lãng phí tài nguyên và có thể làm gián đoạn hoạt động của chương trình.

### 4. Fragmentation (Rối Bộ Nhớ):

- **Internal Fragmentation:** Sự lãng phí bộ nhớ do phần nào đó của vùng nhớ đã được cấp phát nhưng không được sử dụng.
- **External Fragmentation:** Sự lãng phí bộ nhớ do sự gián đoạn của các phân vùng bộ nhớ.

### 5. Stack và Heap:
    
- **Stack:** Dùng để lưu trữ biến cục bộ và gọi hàm, có kích thước cố định.
- **Heap:** Dùng để lưu trữ dữ liệu có thể tồn tại lâu dài và cần sự linh hoạt về kích thước.

### 6. Memory Paging và Segmentation:
    
- **Memory Paging:** Phương pháp chia bộ nhớ thành các trang nhỏ để quản lý.
- **Memory Segmentation:** Phương pháp chia bộ nhớ thành các đoạn có kích thước khác nhau.
    
### 7. Virtual Memory (Bộ Nhớ Ảo):
    
-  Cho phép chương trình sử dụng bộ nhớ vượt ra ngoài dung lượng RAM vật lý, cung cấp ảo hóa và linh hoạt hơn trong việc quản lý bộ nhớ.

### 8. Memory Access và Con Trỏ:
    
  - Hiểu cách con trỏ và các thao tác truy cập bộ nhớ làm việc, giúp tránh lỗi truy xuất bộ nhớ không an toàn.
  
### 9. Memory Protection (Bảo Vệ Bộ Nhớ):
    
- Xác định quyền truy cập vào các vùng bộ nhớ để tránh việc truy xuất không hợp lệ.
    
### 10. **Memory Cache (Bộ Nhớ Đệm):**
    
-  Các cấp độ bộ nhớ tốc độ cao để tối ưu hóa việc truy xuất dữ liệu từ bộ nhớ chính.