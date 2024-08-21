\* Khái niệm: Là ngôn ngữ ==đánh dấu nhẹ== cho văn bản, được thiết kế để đánh dấu văn bản một cách ==đơn giản==, ==dễ đọc==, ==dễ viết==.

=> VD ngôn ngữ đánh dấu nhẹ: Markdown, Textile, AsciiDoc, ...
=> VD ngôn ngữ đánh dấu nặng: HTML, ...

# Header - Tiêu đề

```
 # Text
```

# Bold - In đậm

```
 ** Text **
```

#  Italic - In nghiêng

```
 * Text *
```

=>  Bold and Italic - In đậm và in nghiêng

```
 *** Text ***
```

# Blockquotes - Trích dẫn

```
> Text
>> Text
```

# Lists - Danh sách

## Ordered Lists - Danh sách theo số thứ tự
```
	1. First item  
	2. Second item  
	3. Third item  
	4. Fourth item
```

##  Unordered Lists - Danh sách không có thứ tự

```
- First item
* First item
+ First item
```


# Code - Bọc text dạng mã

```
	`Text`
```

# Code Blocks - Bọc text dạng khối mã

```
	```js/ts/json...
		Text
	```
	
	~~~js/ts/json...
		Text
	~~~
```


#  Horizontal Rules - Tạo dấu gạch ngang


```
	***
	---
	_________________
```

`
# Links - Liên kết

```
[Text]($link "$title")
hoặc
[text]($link)
```


#  URLs and Email Addresses

```
	<https://www.markdownguide.org> => URL
	<fake@example.com>   => Email
```


# Images - Hình ảnh

```
	![Text]($file/link)
	
	[![Text]($file/link)]($viewLink)
```


#  Escaping Characters - Ký tự đặc biệt

```
 \* Text
 
 * ` \ _ {} [] <> () # + - . ! |
```


# Strikethrough - Gạch ngang Text

```
 ~~ Text ~~
```


# Table - Tạo bảng

```

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |

```


# Task Lists - Tạo danh sách nhiệm vụ

```
 - [] Text
 - [x] Text
```


# Highlight - Làm nổi bật Text

```
 == Text ==
```


# Subscript - Chỉ số (phía dưới)

```
 H<sub>2</sub>O
```

=> H<sub>2</sub>O


# Superscript - Chỉ số (phía trên)

```
 X<sup>2</sup>
```

=> X<sup>2</sup>


# Automatic URL Linking - Link liên kết tự động

```
 http://www.example.com
```


# Disabling Automatic URL Linking - Tắt link liên kết tự động

```
 `http://www.example.com`
```


# Underline - Gạch dưới

```
 <ins> Text </ins>
```


# Comments - Bình luận

```
 [Text]: 
```


# Obsidian

[[Obsidian]]
