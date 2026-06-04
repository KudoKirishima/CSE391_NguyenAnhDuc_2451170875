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

# Câu A2 — CSS Selectors — Dự đoán kết quả

## Kết quả của từng selector

1. `h1`  
   → Chọn: `ShopTLU`

2. `.price`  
   → Chọn: `25.990.000đ`, `45.990.000đ`

3. `#app header`  
   → Chọn phần `<header>` nằm trong `#app`, tức là khu vực chứa: `ShopTLU`, `Home`, `Products`, `About`

4. `nav a:first-child`  
   → Chọn: `Home`

5. `.product.featured h2`  
   → Chọn: `MacBook Pro`

6. `article > p`  
   → Chọn các thẻ `<p>` là con trực tiếp của `article`, gồm:
   - `25.990.000đ`
   - `Mô tả sản phẩm...`
   - `45.990.000đ`
   - `Mô tả sản phẩm...`

7. `a[href="/"]`  
   → Chọn: `Home`

8. `.top-bar.dark h1`  
   → Chọn: `ShopTLU`

# Câu A3 — Box Model — Tính toán kích thước

## Trường hợp 1: `content-box` (mặc định)

    .box-1 {
        width: 400px;
        padding: 20px;
        border: 5px solid black;
        margin: 10px;
    }

- Chiều rộng hiển thị = `400 + 20 + 20 + 5 + 5 = 450px`
- Không gian chiếm trên trang = `450 + 10 + 10 = 470px`

---

## Trường hợp 2: `border-box`

    .box-2 {
        box-sizing: border-box;
        width: 400px;
        padding: 20px;
        border: 5px solid black;
        margin: 10px;
    }

- Chiều rộng hiển thị = `400px`
- Kích thước content thực tế = `400 - 20 - 20 - 5 - 5 = 350px`
- Không gian chiếm trên trang = `400 + 10 + 10 = 420px`

---

## Trường hợp 3: Margin collapse

    .box-a { margin-bottom: 25px; }
    .box-b { margin-top: 40px; }

- Khoảng cách giữa `box-a` và `box-b` = `40px`
- Không phải `65px` vì margin dọc giữa hai block element sẽ bị **collapse**, tức là không cộng lại mà chỉ lấy giá trị lớn hơn

### Nâng cao
Nếu `.box-a` có `margin-bottom: -10px` và `.box-b` có `margin-top: 40px` thì khoảng cách sẽ là:

- `40px + (-10px) = 30px`

# Câu A4 — Specificity (Độ ưu tiên)

Cho các rules:

    p { color: black; }                    /* Rule A */
    .price { color: blue; }                /* Rule B */
    #main-price { color: red; }            /* Rule C */
    p.price { color: green; }              /* Rule D */

## 1) Specificity score

- Rule A: `p` → `(0, 0, 1)`
- Rule B: `.price` → `(0, 1, 0)`
- Rule C: `#main-price` → `(1, 0, 0)`
- Rule D: `p.price` → `(0, 1, 1)`

## 2) Element sẽ có màu gì?

Element sẽ có **màu đỏ**.  
Lý do là Rule C dùng ID selector `#main-price`, có specificity cao hơn các rule còn lại nên sẽ thắng.

## 3) Nếu thêm inline style

Nếu element là:

    <p class="price" id="main-price" style="color: orange;">

thì element sẽ có **màu cam**.  
Lý do là inline style có độ ưu tiên cao hơn CSS thông thường.

## 4) Nếu Rule A thêm `!important`

Ví dụ:

    p { color: black !important; }

thì element sẽ có **màu đen**.  
Lý do là `!important` có độ ưu tiên cao hơn các rule thông thường khác.

# Câu B1 — Các loại selector đã dùng

Trong file `style.css`, em đã dùng ít nhất 5 loại selector khác nhau:

1. **Element selector**: `body`, `header`, `main`, `footer`
2. **Class selector**: `.active`
3. **ID selector**: `#profile-title`
4. **Descendant selector**: `nav a`, `table th`, `table td`
5. **Pseudo-class selector**: `nav a:hover`, `tbody tr:nth-child(even)`, `tbody tr:hover`

# Câu B2 — Box Model Lab

## Phần 1

Hộp 1 (content-box): chiều rộng thực tế = `350px`  
Hộp 2 (border-box): chiều rộng thực tế = `300px`

Giải thích sự khác biệt:
- Với `content-box`, `width: 300px` chỉ tính cho phần content, nên phải cộng thêm `padding` và `border`
- Với `border-box`, `width: 300px` đã bao gồm cả content, padding và border

## Phần 2

Layout 3 cột không dùng `border-box` bị vượt quá `1000px` vì:
- Cột trái: `250 + 15 + 15 = 280px`
- Cột giữa: `500 + 20 + 20 = 540px`
- Cột phải: `250 + 15 + 15 = 280px`

Tổng thực tế:
- `280 + 540 + 280 = 1100px`

Vì tổng lớn hơn `1000px` nên layout bị vỡ.

Khi dùng `border-box`, padding nằm bên trong chiều rộng đã khai báo nên tổng 3 cột vẫn đúng `1000px`.

# Câu B3 — Specificity Battle

## 1) 10 rules + specificity score

1. `*` → `(0, 0, 0)`
2. `p` → `(0, 0, 1)`
3. `body p` → `(0, 0, 2)`
4. `.text` → `(0, 1, 0)`
5. `.highlight` → `(0, 1, 0)`
6. `p.text` → `(0, 1, 1)`
7. `p.highlight` → `(0, 1, 1)`
8. `.text.highlight` → `(0, 2, 0)`
9. `#demo` → `(1, 0, 0)`
10. `p#demo.text.highlight` → `(1, 2, 1)`

## 2) Element cuối cùng hiển thị màu gì? Tại sao?

Element cuối cùng hiển thị **màu deeppink**.  
Lý do là selector `p#demo.text.highlight` có specificity cao nhất nên thắng các rule còn lại.

## 3) Nếu thay đổi thứ tự rules trong CSS file, kết quả có đổi không?

Nếu chỉ thay đổi thứ tự giữa các rule có specificity khác nhau thì thường **không đổi**, vì rule có specificity cao hơn vẫn thắng.  
Tuy nhiên, nếu đổi thứ tự giữa các rule có **cùng specificity** và cùng target một element thì rule viết sau sẽ thắng.

