#foreach

# Lưu ý khi dùng forEach

- Không thể thoát khỏi vòng lặp khi đã bắt đầu
- Return chỉ dừng callback, nhưng vẫn loop qua những element kế tiếp

```js
[1,2,3,0].forEach(num => {
  console.log('prev', num)
  if (num > 1) return;
  console.log('after', num)
})
 // prev 1
 // after 1
 // prev 2
 // prev 3
 // prev 0
 // after 0
```


-  Có thể dùng throw Error để dừng (hơi chua)

```js

 array.forEach((number) => {
    console.log("Number:", number);
    if (number === 3) {
      throw new Error("Oops! Stopping the loop.");
    }
  });

```