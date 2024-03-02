

## Khái niệm

- I/O là quá trình truyền data giữa máy tính và  các thiết bị ngoại vi, thiết bị lưu trữ hoặc thiết bị mạng, ..

- Trong software development, I/O thường dùng để dọc dữ liệu đầu vào từ user, truy cập tệp tin, ... và gửi dữ liệu đầu ra đến thiết bị hiển thị, ...

-  Ảnh hưởng đáng kể đến performance và sự phản ứng của ứng dụng phần mềm.
	
## Các kỹ thuật tối ưu performance

### Buffering - read file dạng buffer
### Bất đồng bộ

 Ví dụ có 10 users cùng req api `read-file`, nếu không dùng Asynchronous mà dùng Synchronous thì khi user đầu req tới,
 hàm đọc file sẽ bị blocking và những users sau sẽ bị pending.
Vấn đề xảy ra do cơ chế đồng bộ của nodejs.

### Ánh xạ bộ nhớ

## Kết

- Hiểu I/O rất quan trọng để phát triển các ứng dụng phần mềm tương tác với người dùng, thiết bị hoặc mạng