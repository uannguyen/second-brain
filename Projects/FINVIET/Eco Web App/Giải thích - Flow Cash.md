
![[CyHome-flow-cash.drawio.png]]





***CHÚ THÍCH

 * Mỗi dịch vụ VAS thanh toán qua cổng **Eco Pay** sẽ được cấu hình một **Store Account** khác nhau để nhận diện. Ví dụ: CyHome1, Cyhome2, ...
 * Mỗi đối tác sẽ được cấu hình một **Partner Account** riêng biệt ở máy chủ **BE Merchant B2B**. Ví dụ: CyHome1

Mục 1.1:
- Khi User của CyHome App thông qua **Eco Web App** thực hiện thanh toán qua cổng **Eco Pay** thành công, tiền thanh toán của User sẽ chuyển đến ví của **ECO Pay**.

	=> **Eco Pay** giữ tiền và tiền nhận được sẽ được chuyển về **Store Account** tương ứng từng dịch vụ.

Mục 1.2:
- Khi User thanh toán ở cổng **Eco Pay** thành công và máy chủ **BE Eco Web App** xác nhận giao dịch đã thành công, máy chủ **BE Eco Web App** sẽ tiến hành gửi yêu cầu đến máy chủ **BE Merchant B2B** để thực hiện xử lý dịch vụ(**VAS**) tương ứng.

Mục 1.3: 
- Khi nhận được yêu cầu từ máy chủ **Eco Web App**, máy chủ **Merchant B2B** thực hiện giao dịch thanh toán các dịch vụ(**VAS**) tương ứng với máy chủ nhà cung cấp **BE Provider**. Tiền từ ví của của CyHome được cấu hình ở **BE Merchant B2B** sẽ chuyển đến ví của **Nhà cung cấp**

=> **BE Merchant B2B** sử dụng tiền từ **Partner Account**(CyHome) để thanh toán cho bên nhà cung cấp.( mbf.airtime, mbf.code, ... )