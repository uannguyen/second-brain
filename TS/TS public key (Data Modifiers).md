


- Mặc định thì all members của class là `public`
- Có thể được accessed anywhere mà không có bất kỳ hạn chế nào

```ts
class Employee {
	public empCode: string;
	empName: string;
}

let emp = new Employee();
emp.empCode = 123;
emp.empName = "Swati";
```
