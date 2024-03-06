***Đóng gói những gì khác nhau***


***Xác định các khía cạnh của app mà có thể thay đổi & tách biệt chúng ra khỏi các phần giữ nguyên***


- Mục tiêu chính là giảm thiểu ảnh hưởng gây ra khi thay đổi code

- EX minh họa: Giả sử program là một con tàu, và những phần code cần changes là những quả mìn ở dưới thân tàu.
	- Nếu trúng mìn, con tàu sẽ chìm
	- Biết điều này, ta có thể chia con tàu thành các khoang độc lập được niêm phong an toàn
	- Bây giờ, nếu con tàu đâm vào mìn, toàn bộ con tàu vẫn nổi và chỉ có 1 khoang xảy ra vấn đề

=> Có thể cô lập các phần của programs khác nhau trong các module độc lập, bảo về các phần code còn lại khỏi tác động bất lợi


# Encapsulation on a method level

### Context

- 1 web ecommerce
- có 1 method `getOrderTotal` tính tổng tiền, bao gồm thuế
- code về tax có thể thay đổi trong tương lai => tax tùy theo country, state, event city
=> `getOrderTotal` method sẽ be changes khá thường xuyên nên tách ra method mới, giả sử tương lai method `getTaxRate` quá phức tạp thì cũng có thể dễ dàng tách ra thành 1 class dễ dàng


***Before...***
```ts
function getOrderTotal(order) {
  let total = 0;

  for (const item of order.lineItems) {
    total += item.price * item.quantity;
  }

  if (order.country === "US") {
    total += total * 0.07; // US sales tax
  } else if (order.country === "EU") {
    total += total * 0.2; // European VAT
  }

  return total;
}
```


***After...***
```ts
function getOrderTotal(order) {
  let total = 0;

  for (const item of order.lineItems) {
    total += item.price * item.quantity;
  }

  total += total * getTaxRate(order.country);
  return total;
}

function getTaxRate(country) {
  if (country === "US") {
    return 0.07; // US sales tax
  } else if (country === "EU") {
    return 0.2; // European VAT
  } else {
    return 0;
  }
}
```


# Encapsulation on a class level

- Thay vì để tất cả những gì liên quan đến thuế trong class Order, ta có thể tách thêm 1 class Tax. 

***Before...***
![[oop-12.png]]


***After...***
![[oop-13.png]]