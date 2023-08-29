


![[CyHome-flow-payment.drawio.png]]





***CHÚ THÍCH

Mục 1.1: Người dùng yêu cầu mở webview ECO Web App từ CyHome App
- User từ **CyHome App** truy cập vào Webview  **Eco Web App** thông qua các icon tương ứng của dịch vụ VAS.
 - Sau khi vào được **Eco Web App** , User nhập thông tin của dịch vụ cần thanh toán và tiến hành thanh toán.

Mục 1.2: User nhập thông tin của dịch vụ & nhấn "Thanh toán"
- Khi User nhấn **"Thanh toán"** , phía máy chủ **BE Eco Web App** sẽ gửi một yêu cầu tạo giao dịch thanh toán đến máy chủ **BE Eco Pay**.
	+ Nếu thành công, máy chủ **BE Eco Pay** sẽ trả về thông tin giao dịch thanh toán bao gồm đường dẫn thanh toán.
	+ Sau đó, máy chủ **BE Eco Web App** sẽ trả về đường dẫn thanh toán cho **Eco Web App**.

Mục 1.3: Mở URL cổng Eco Pay để thực hiện thanh toán 
- User mở cổng thanh toán **Eco Pay** từ đường dẫn vừa được trả về để thực hiện thanh toán.
- Ở màn hình thanh toán **Eco Pay**, User chọn phương thức thanh toán, điền thông tin và thực hiện thanh toán.(Các PTTT được cấu hình ở Eco Pay)
	- Nếu thanh toán thành công:
		- Chuyển hướng từ cổng thanh toán **Eco Pay** về lại giao diện của **Eco Web App**.
		+ Máy chủ **BE Eco Pay** gửi yêu cầu IPN thông báo kết quả giao dịch đến máy chủ **BE Eco Web App**.

Mục 1.4: Gửi yêu cầu đến máy chủ Merchant B2B để thực hiện xử lý dịch vụ VAS
- Sau khi nhận thông báo kết quả và xác nhận giao dịch thanh toán thành công, máy chủ **BE Eco Web App** tiến hành gửi yêu cầu đến máy chủ **BE Merchant B2B** để thực hiện xử lý dịch vụ VAS tương ứng.
- Sau đó, máy chủ **BE Eco Web App** phản hồi kết quả dịch vụ **Thành công**/**Thất bại** đến người dùng.