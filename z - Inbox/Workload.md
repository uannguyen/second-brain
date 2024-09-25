---
tags: []
---


- [x] Viết ticket xin off ngày mai
- [ ] Tách FV project ra một vaul riêng, bỏ hết docs, file liên quan vào luôn (kể cả folder FV-Docs ở ngoài Desktop)
- [ ] 
# KPI
- [ ] Điền KPI tháng 8

# Merchant

- [ ] Xử cron TT40
- [ ] Chặn hủy LK bank nếu là bank cuối cùng (có thể hú Trung xử, check theo version release)
- [ ] Khi mở khóa cần update `unlocked_by_activated_rule_at` cho nó (VD case R5 sau khi mở khóa trong vòng bn ngày mà KH chưa thực hiện GD thì mới đc khóa tiếp)

# SmartPOS API

- [x] Api get setting
    - [x] Upload ảnh nhà mạng lên
- [x] topup
    - [x]  Xử lý chỗ update trans, call api ecopay update status cho api `topup`
- [x] Api postpaid
    - [x] Api get postpaid info
    - [x] Api pay postpaid
- [x] Api billpay
    - [x] Api get bill info
    - [x] Api pay bill
- [x] Api buycard (đt, game)
- [x] Update trans ecopay (`payment_status`, `received_amount`)
- [ ] 
- [x] Tạo acc cho smartpos bên `backend`
- [x] API ecopay get merchant profile(ko cần dùng)
- [x] Tích hợp đầu openapi
- [x] Có cần map lại response data từ bên openapi ?
    - [x] Khi call gạch nợ thì có trả về `code(mã lỗi)`, `message(nội dung)` 
- [ ] Flows quẹt thẻ: nếu thanh toán thành công mà gạch nợ(bill, ...) thất bại thì xử lý như nào ? Hoàn tiền hay gạch nợ lại ?
- [x] Xử lý GD được tạo ra bên phía smartpos ? (Mobile tự call tạo)
- [ ] Ko thấy tạo task trên Jira
- [x] Thêm cấu hình cho mấy dịch vụ viễn thông khác
- [ ] Map provider name billpay
- [ ] Check buycard 3G bên openapi
    - [ ] Tạm chờ check lại
- [x] Check get bill info evn ra có một bill
- [x] Up lại mấy hình provider
- [ ] 



#  webapp
- [x] thêm api retry khi GD failed
- [x] bắn thông báo qua pos khi create trans
- [x] apply cash_pos method khi thanh toán
- [x] update listTrans: transid ecopay, makh, payment_status, trans_status 
- [x] Zụ clear localStoraged
- [x] zụ `amount` của thẻ card khi quantity khác 1
- [x] ẩn mấy cái api ecom => performance
- [x] fix account này có thể lấy thông tin GD của account khác
- [x] Thêm `extra_data` lúc init GD ecopay
- [ ]  Check thanh toán các loại dịch vụ:
    - [ ] tuition
    - [ ] landline
    - [ ] credit
    - [ ] loan
    - [ ] Data card/Game card

- [ ] 
- [x] Thêm response cho api IPN (pos method)
- [x] Update thêm field `tax`, vào extra_data khi inti GD
- [ ] check api get-setting chỉ trả những field cần thiết
- [x] fix navigate vào screen từng dịch vụ luôn
- [x] update extra_data => `provider_name`, `provider_code`
- [x] check `merchan_bill_id` ko cho trùng (trừ case `failed`)
- [x] bắn postMessage khi request failed
- [x] Check sao khi thanh toán thành công ecopay bắn IPN status = `initial`
- [ ] Hỏi case status `processing` khi thanh toán bên connector thì sao ?
- [x] Sửa lại case partner check trans (sửa env `internal_username`)


# Eco game

- [x] Fix eco-game popup cộng lượt
- [x] setup `promotion_id` mảnh quà
- [x] sửa icon
- [x] fix quay trúng quà may mắn lần sau status bị null
- [x] lịch sử bỏ quà `may mắn lần sau` đi 
- [x] map lại screen page (`spin history`, `prize spin`)
- [x] thêm gift_type none ở portal
- [x] gắn vòng quay mới (map lại thứ tự quà)
- [x] Xuất file export lịch sử quay thưởng thiếu `Quà tặng`
- [x] Reupload spin banner
- [ ] Coi game phase 2 
- [ ] quét portal docs
- [ ] Chỉ được follow 1 store trong suốt chương trình
- [ ] 

# risk
- [x] tách rule 1
- [x] update rule 3: add thêm GD nếu rule đã tồn tại
- [x] update rule 3,4 
- [x] rule 3 4 10 11 - update bank ibft
- [x] check case first bank_map
- [x] Update thời gian cho các rules
- [x] Tạo file chạy cronjob cho các rules
- [x] Sửa portal
- [ ] improve rule 12,13 => dùng `count` thay vì `findOne`
- [x] fix rule 3 => GD bị lệch ngày
- [ ] 

# be docs
- [x] update file storaged
- [x] Update docs `trươnghai`
- [x] update docs `iomedia2`
- [ ] Thêm Openapi get bill


# Consumer

- [x] Forgot pass phase 2
- [ ] 










