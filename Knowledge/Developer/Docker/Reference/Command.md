
#docker 

# Stop Container

```
docker stop $(docker ps -q)
```

# Remove container

```
// 1 container
docker rm $container_id

// buộc dừng và xóa all
docker rm -f $(docker ps -a -q)
```
