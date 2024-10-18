

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

