
#docker 

# Stop Container

```
docker stop $(docker ps -q)
```

# Remove container

```sh
// 1 container
docker rm <container_id>

// buộc dừng và xóa all
docker rm -f $(docker ps -a -q)
```

# Build image

```sh
docker build -t <image_name> .
```


- `-t` => Đặt tên và tag cho image của bạn (ví dụ: `your_image_name:latest`)
- `-f <Dockerfile_name>` => Chỉ định file Dockerfile cụ thể (nếu file Dockerfile trùng tên thì khỏi cần)
- `.` => Đường dẫn đến context build (trong trường hợp này là thư mục hiện tại)
# Build container

```sh
docker run -d -n <container_name> -p <expose_port>:<container_port> <image_name> 
// -p => port
// -n => container name
```

# Truy cập container

```sh
docker exec -it <container_name> sh
```

# Kiểm tra container

- Thường thì khi run container rồi ta mới có thể truy cập vào được, nhưng lệnh dưới đây giúp ta truy cập vào container check luôn

```sh
docker run -it <image_name> /bin/sh
```