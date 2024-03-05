
# Code reuse - Tái sử dụng mã

- Chi phí và thời gian là hai trong số các số liệu có giá trị nhất khi phát triển bất kỳ sản phẩm phần mềm nào.
- Ít time để dev hơn => đẩy SP ra thị trường sớm hơn so với đối thủ cạnh tranh
- Ít chi phí => tiết kiệm tiền

- Khái niệm về việc reuse code có vẻ tuyệt vời trên giấy, nhưng thực tế lại cho thấy việc làm cho code hiện có hoạt động trong một context mới thường đòi hỏi nhiều nỗ lực hơn. 
- Sự kết nối chặt chẽ giữa components, sự phụ thuộc vào các class cụ thể thay vì interfaces, các hoạt động cố định - tất cả điều này làm giảm tính flexibility của code và làm cho việc reuse code trở nên khó khăn hơn. 
- Điều này có nghĩa là, khi mã nguồn được viết một cách cố định và không flexibility, nó sẽ khó khăn hơn để reuse trong các dự án khác mà có yêu cầu hoặc context khác nhau.

- Tuy nhiên, đôi khi apply design pattern sẽ làm cho các thành phần trở nên phức tạp hơn.

### 3 level Reuse code

- **Cấp độ thấp nhất**: Tái sử dụng lớp: thư viện lớp, bộ chứa, có thể là một số "nhóm" lớp như bộ chứa / trình lặp.

- **Cấp độ cao nhất**: Framework.
	- rút ngắn các quyết định thiết kế
	- Xác định các khái niệm trừu tượng chính để giải quyết vấn đề, đại diện cho chúng bằng các classes và xác định các mối quan hệ giữa chúng

```ts
// Cấp độ thấp nhất: Tái sử dụng lớp
// Ta có một lớp đơn giản thể hiện một hình dạng hình vuông
class Square {
  constructor(sideLength) {
      this.sideLength = sideLength;
  }

  calculateArea() {
      return this.sideLength * this.sideLength;
  }
}

// Cấp độ cao nhất: Framework
// Ta tạo ra một framework đơn giản để thực hiện các phép kiểm tra đơn vị với Jest
const { test, expect } = require('@jest/globals');

test('Calculate square area', () => {
  // Tạo một hình vuông có cạnh là 5
  const square = new Square(5);
  // Kiểm tra xem phương thức tính diện tích của hình vuông hoạt động đúng không
  expect(square.calculateArea()).toBe(25);
});

```

- **Cấp độ middle**:
	- Chính là design patterns, nó nhỏ hơn và trừu tượng hơn Framework
	- Reuse ít rủi ro hơn frameworks
	- Patterns cho phép reuse các design ideas & các khái niệm độc lập với code cụ thể


# Extensibility - Khả năng mở rộng


Giả sử:
- Thường là khi hoàn thành first version của app, lúc đó chúng ta có cái nhìn tổng quan hơn về code, hiểu được nhiều khía cạnh hơn nên quay lại nhìn code cũ thì thấy tào lao vl.
- Thay đổi ngoài tầm kiểm soát, thay đổi ý tưởng, ...
- Muốn upgrade app lên 1 tầm cao mới mặc dù vesion hiện tại cũng ổn


