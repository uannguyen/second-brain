
# Encapsulate What Varies(Đóng gói những gì khác nhau) 


***Xác định các khía cạnh của app mà có thể thay đổi & tách biệt chúng ra khỏi các phần giữ nguyên***


- Mục tiêu chính là giảm thiểu ảnh hưởng gây ra khi thay đổi code

- EX minh họa: Giả sử program là một con tàu, và những phần code cần changes là những quả mìn ở dưới thân tàu.
	- Nếu trúng mìn, con tàu sẽ chìm
	- Biết điều này, ta có thể chia con tàu thành các khoang độc lập được niêm phong an toàn
	- Bây giờ, nếu con tàu đâm vào mìn, toàn bộ con tàu vẫn nổi và chỉ có 1 khoang xảy ra vấn đề

=> Có thể cô lập các phần của programs khác nhau trong các module độc lập, bảo về các phần code còn lại khỏi tác động bất lợi


# Encapsulation on a method level


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