

# Auto payment - Thanh toán tự động

https://hotro.finviet.com.vn/browse/IPM-473

*Mục đích: tự động thanh toán dịch vụ theo lịch đặt hàng tháng* 
## Dịch vụ: 
- Hóa đơn (Điện, Nước, ...)

## ==Chức năng==

###  Đăng ký:

 - Hiển thị ở screen Kết quả GD & Chi tiết GD
 - Thông tin hiển thị bao gồm:
 
```
Thông tin KH => Show từ GD trước đó
Tên dịch vụ (sname)
Mã dịch vụ (scode)
Mã NCC (pcode)
Tên NCC (pname)
Hạn mức thanh toán (amount_limit)
Ngày thanh toán (payment_date)
Ngày kết thúc thanh toán tự động (payment_end_date)
Nguồn tiền (Ví ECO - payment_channel = 1)
```

- Verify PIN trước khi thực hiện đky

### Cập nhật

Chỉ sửa được các thông tin sau:
- amount_limit
- payment_date
- payment_end_date

### Hủy đăng ký

=> Cập nhật status = 'inactive'

### View lịch sử

- Lọc theo mã KH
- Gồm 2 loại GD: manual và auto luôn
- Thêm label "Thanh toán tự động" cho các GD auto

### Bắn noti
*Hơi cấn do trước đây bắn noti từ bên BE*

## Vấn đề tồn đọng:

=> View history làm API mới hay app tự lọc từ syncTrans ?
=> Cơ chế bắn noti đã có, giờ mà thêm thì bị duplicate, ko thêm thì content không giống với yêu cầu

## ==Data Structure==

table name: service_auto_payments
Uniq key: scode, customerid

Schema:

- reference
- scode
- pcode
- acode
- customer_info: {
  customer_id,
  customer_name,
  customer_address
	}
- amount_limit
- payment_date
- payment_end_date
- payment_channel
- status: 'active' | 'inactive'

---
