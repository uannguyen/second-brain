---
tags:
  - command
  - linux
  - ubuntu
  - killport
  - port
---

# Check port


```ts
// list port
netstat -tulnp
// Chỉ lấy port của node:
netstat -tulnp | grep node
```


```ts
// list port đang chạy
sudo lsof -i

// tìm 1 port cụ thể
sudo lsof -i :4043

// kill port dựa vào PID
sudo kill 23091
```

