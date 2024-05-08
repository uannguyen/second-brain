
# Docker là gì ?

- Docker là một open platform để developing, shipping & running applications


# Docker dùng để làm gì ?

- Cho phép tách Applications khỏi cơ sở hạ tầng(infrastructure) để phân phối software nhanh chóng
- Manage infrastructure giống như cách manage applications
- Giảm độ trễ giữa writing code & running nó trong production (tận dụng các lợi thế như shipping, testing, deploying code) 

# Docker platform

- Docker đóng gói & run một App trong loosely isolated env(môi trường lỏng lẻo) gọi là container
	- Sự cô lập & security cho phép run nhiều containers đồng thời trên một máy chủ
	- Container chiếm dung lượng nhẹ & chứa mọi thứ cần thiết để run App
	- Có thể share containers cho người khác, đảm bảo các containers hoạt động giống nhau

- Docker có tool manage lifecycle của containers:
	- 