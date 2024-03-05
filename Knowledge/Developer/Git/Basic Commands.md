
# Init 

> Khởi tạo một repository Git mới trong thư mục hiện tại hoặc chuyển đổi một thư mục hiện có thành một repository Git

```ts
git init
```


# Clone

> Sao chép (clone) một repository Git từ một url về máy local

```ts
git clone $url
```


# Add

> Thêm một hoặc nhiều file hoặc thư mục vào `Staged Changes` để chuẩn bị cho việc commit.

```ts
// Thêm 1 file
git add $file_name

// Thêm tất cả
git add .
```


# Commit

> Commit code, chuẩn bị chờ push lên

```ts
git commit -m "$message"
```


# Status

- Kiểm tra các file thay đổi

```ts
git status
```

# Pull

- Pull code mới nhất về từ `remote repository`

```ts
git pull
git pull origin $branch
```


# Push

```ts
git push 
git push origin HEAD
```


# Branch

```ts
// List branch
git branch

// Tạo branch
git branch $branch_name

// Tạo và checkout qua branch 
git checkout -b $branch_name

// Xóa local branch
git branch -D $branch_name

// Xóa remote branch
git push origin :$branch_name

```