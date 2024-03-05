#github #git


# Config

```ts
// List remote name
git remote 

// show remote info
git remote show $remote_name

// add url remote
git remote add $remote_name $url

// delete remote
git remote remove $remote_name

```

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

// Chuyển đổi branch
git checkout $branch_name
```


# Merge

```ts
// merge code
git merge $branch_name
```


# Stash

> - Lưu trạng thái hiện tại của working directory và stage area vào stash
> - Thường dùng khi `pull` hoặc `checkout branch` mà không được, hoặc khi chưa muốn commit

```ts
// lưu 
git stash

// apply
git stash apply
```


# Log

> Coi lại các commit của repository

```ts
git log 
```

# Checkout File

> Hủy các thay đổi của file 

```ts
git checkout $file_name
```

# Rebase

```ts
git rebase
```


# Reset

```ts
git reset $commit_id
```


# Revert 

```ts
git revert $commit_id
```

# Cherry-pick

> Chọn một commit từ một branch và áp dụng nó vào branch hiện tại.

```ts
git cherry-pick $commit_id
```


# Tag

> Đánh dấu, thường dùng cho các phiên bản phát hành

```ts
// list tags
git tag

// add tag
git tag $tag_name $commit_id

// view tag
git show $tag_name

// push lên repo
git push $remote_name $tag_name

// delete local tag
git tag -d $tag_name

// delete remote tag
git push $remote_name --delete $tag_name
```

# Clean

> Xóa các file không được theo dõi
 
```ts
git clean
```