# Khái niệm

- "DRY" là viết tắt của "Don't Repeat Yourself," là một nguyên tắc quan trọng trong lập trình và quản lý mã nguồn.
- Nguyên tắc này khuyến khích việc tránh lặp lại mã nguồn mà không cần thiết trong dự án phần mềm.
- Mục tiêu của nguyên tắc DRY là giảm sự phụ thuộc và tăng tính duy trì của mã nguồn.


```js
// Hàm xử lý định dạng ngày tháng
function formatDate(date) {
  const options = { year: 'numeric', month: 'numeric', day: 'numeric' };
  return new Date(date).toLocaleDateString('en-US', options);
}

// Sử dụng hàm formatDate ở nhiều nơi
const currentDate = new Date();
const formattedDate1 = formatDate(currentDate);
console.log(`Formatted Date 1: ${formattedDate1}`);

const futureDate = new Date(currentDate);
futureDate.setDate(currentDate.getDate() + 7);
const formattedDate2 = formatDate(futureDate);
console.log(`Formatted Date 2: ${formattedDate2}`);

const pastDate = new Date(currentDate);
pastDate.setDate(currentDate.getDate() - 3);
const formattedDate3 = formatDate(pastDate);
console.log(`Formatted Date 3: ${formattedDate3}`);

```










