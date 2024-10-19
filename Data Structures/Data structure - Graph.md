
# Khái niệm

- Là một loại DS phi tuyến tính (non-linear) bao gồm các đỉnh (node) và các cạnh. 

## Thuật ngữ

- Đỉnh liền kề là 2 đỉnh connect với nhau từ một canh
- Cạnh liền kề là 2 cạnh cùng connect với 1 đỉnh
- Degree (bậc): bậc của một node là số cạnh được connect với node đó. Node có bậc 0 là node bị cô lập (first node/last node)
- Path(con đường): một chuỗi các node được connect với nhau bằng các cạnh, độ dài của path là số cạnh mà nó chứa.

```txt
NodeA -> Node B -> Node C

=> path length = 2
```

- Cycle (Chu trình): Là một path bắt đầu và kết thúc tại cùng một node

```txt
NodeA - NodeB 
	|				|
NodeD	- NodeC
```

- Connected Graph (liên thông): các node phải liên thông, ko có node nào bị cô lập
- Complete Graph: mọi node được kết nối với tất cả các node khác. Một biểu đồ hoàn chỉnh chứa n(n-1)/2 cạnh trong đó n là số node trong biểu đồ
- Weighted Graph: mỗi cạnh được gán một số dữ liệu như chiều dài hoặc trọng lượng

## Graph vô hướng

- Giữa các đỉnh có cạnh liên kết và có thể đi từ A => hoặc từ B => A

![[graph-definition.png]]

### Applications

- Như trên FB, mỗi user là một Node và connection giữa các users là edge(cạnh)

## Graph có hướng

- Chỉ có thể đi theo hướng mũi tên

![[directed-and-undirected-graph.png]]