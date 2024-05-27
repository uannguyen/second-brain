
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

# Build container

```sh
docker run -d -n <container_name> -p <expose_port>:<container_port> <image_name> 
// -p => port
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