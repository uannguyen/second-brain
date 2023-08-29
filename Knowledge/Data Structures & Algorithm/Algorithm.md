
# Define - Khái niệm 

- Thuật toán là ==một tập hợp các bước hoặc hướng dẫn== để ==giải quyết một bài toán==, ==nhiệm vụ== nào đó.
- Ví dụ - Thuật toán cộng hai số:
	1. Lấy hai số đầu vào
	2. Thêm số bằng toán tử +  
	3. Hiển thị kết quả

# Tại sao cần Thuật toán ?

- **Khả năng mở rộng**: Giải quyết các vấn đề ==lớn== & phức tạp => ==nhỏ== => ==nhỏ hơn==
- **Hiệu suất**: tối ưu ==thời gian thực thi & tài nguyên==

  => Nếu bài toán có thể ==dễ dàng chia thành các bước nhỏ hơn== nghĩa là bài toán đó ==có thể thực hiện được==

# Characteristics - Đặc điểm

- **Input/Output** => phải được ==xác định chính xác==
- **Tính rõ ràng** (**Unambiguity**)  =>  Mỗi bước phải ==rõ ràng mạch lạc==
- **Tính hữu hạn** (**Finiteness**) => lệnh ==phải đếm được==
- **Tính hiệu quả** (**Effectiveness**) => ==Hiệu quả & phù hợp nhất== trong số nhiều cách khác nhau
- **Ngôn ngữ độc lập** (**Language independent**) => Có thể ==tái sử dụng== cho nhiều ==ngôn ngữ lập trình khác nhau==

# Dataflow -  Luồng

- **Problem** => Vấn đề
- **Algorithm** => Thuật toán 
- **Input** => Đầu vào
- **Processing unit** => Xử lí
- **Output** => Đầu ra

# Factors - Yếu tố

- **Modularity** (**Tính mô-đun**): Chia vấn đề thành các mô-đun nhỏ
- **Correctness** (**Tính đúng đắn**): Tạo ra Output như mong muốn
- **Maintainability** (**Khả năng bảo trì**): Dễ dàng bảo trì
- **Functionality** (**Chức năng**):  xem xét các bước hợp lý khác nhau để giải quyết vấn đề trong thế giới thực
- **Robustness** (**Tính mạnh mẽ**): Xác định rõ vấn đề
- **User-friendly** (**Thân thiện với người dùng**): Dễ dàng giải thích
- **Simplicity** (**Tính đơn giản**): Đơn giản thì dễ hiểu
- **Extensibility** (**Khả năng mở rộng**)


# Major categories - Các thuật toán chính
- **Sort (Sắp xếp)**
- **Search (Tìm kiếm)**
- **Delete (Xóa)**
- **Insert (Chèn)**
- **Update (Cập nhật)**

# Algorithm Complexity - Độ phức tạp của thuật toán

*Đo lường ==mức độ tăng của thời gian== hoặc ==tài nguyên== (thường là bộ nhớ) mà một thuật toán sử dụng khi ==đầu vào của nó tăng== lên. Hiểu được hiệu suất của thuật toán trong các tình huống khác nhau và giúp chọn lựa thuật toán phù hợp cho một vấn đề cụ thể*

## **Time complexity (Thời gian)**
- Thời gian để hoàn thành một nhiệm vụ cụ thể
- Phụ thuộc vào ==kích thước data đầu vào==
- Thuật toán có ==độ phức tạp thời gian thấp hơn== thường được ==ưa chuộng== vì chúng ==chạy nhanh hơn== trên ==lượng dữ liệu lớn==
- Các loại biểu đồ phổ biến:
	- O(1) (hằng số)
	- O(log n) (logarithmic)
	- O(n) (tuyến tính)
	- O(n log n) (quasilinear)
	- O(n^2) (quadratic)
	- O(2^n) (exponential)
## **Space complexity (Không gian)**

- Lượng bộ nhớ mà mà thuật toán sử dụng để hoàn thành nhiệm vụ
- Phụ thuộc vào ==kích thước data đầu vào==
- Thuật toán có ==độ phức tạp không gian thấp hơn== thường được ==ưa chuộng== trên các ==hệ thống có tài nguyên hạn chế==