
*Trong OOP, concept `Encapsulation` được sử dụng để làm cho các member(field, method, ...) trong class ở chế độ public hoặc private. Tức là một class có thể control được khả năng hiển thị của data members*

- Có 3 loại access modifiers: `public`, `private`, `protected`

## public

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


## private

- Chỉ có thể accessed trong chính class đó mà không thể accesible bên ngoài class

```ts
class Employee {
    private empCode: number;
    empName: string;
}

let emp = new Employee();
emp.empCode = 123; // Compiler Error
emp.empName = "Swati";//OK
```


## protected

- Có thể accessed trong chính class đó và subclass đã `extend` class đó, mà không thể accessible từ bên ngoài

```ts
class Employee {
    public empName: string;
    protected empCode: number;

    constructor(name: string, code: number){
        this.empName = name;
        this.empCode = code;
    }
}

class SalesEmployee extends Employee{
    private department: string;
    
    constructor(name: string, code: number, department: string) {
        super(name, code);
        this.department = department;
    }
}

let emp = new SalesEmployee("John Smith", 123, "Sales");
emp.empCode; //Compiler Error
```