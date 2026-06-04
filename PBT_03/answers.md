# Câu A1 — 3 Cách nhúng CSS
## 1) Inline CSS
Ví dụ code:
```html
    <h1 style="color: blue;">ShopTLU</h1>
```
Ưu điểm:
- Viết nhanh
- Dễ thử style tạm thời cho một chỗ nhỏ

Nhược điểm:
- Khó quản lý khi code nhiều
- Không tái sử dụng được
- Làm HTML bị rối

Khi nào nên dùng:
- Chỉ nên dùng tạm thời hoặc khi cần chỉnh nhanh một element nhỏ

## 2) Internal CSS
Ví dụ code:
```html
    <head>
        <style>
            h1 {                
                color: blue;            
            }       
        </style>    
    </head>
```
Ưu điểm:
- Dễ dùng khi làm một trang đơn giản
- Không cần tạo file CSS riêng

Nhược điểm:
- Khó tái sử dụng cho nhiều trang
- Nếu project lớn thì khó maintain

Khi nào nên dùng:
- Dùng cho prototype, bài nhỏ hoặc trang đơn

## 3) External CSS
Ví dụ code trong HTML:
```html
    <head>
        <link rel="stylesheet" href="style.css">    
    </head>
```
Ví dụ code trong file CSS:
```css
    h1 {        
        color: blue;    
    }
```
Ưu điểm:
- Dễ quản lý
- Tái sử dụng cho nhiều trang
- Phù hợp với dự án thật
- Browser có thể cache file CSS

Nhược điểm:
- Phải tạo file riêng
- Ban đầu nhiều bước hơn inline hoặc internal

Khi nào nên dùng:
- Nên dùng trong hầu hết các dự án thật và bài tập lớn
