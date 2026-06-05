# Câu A1 — Viewport & Mobile-First

## 1) Thẻ meta viewport chuẩn

`<meta name="viewport" content="width=device-width, initial-scale=1.0">`

Giải thích:
- `name="viewport"`: cho trình duyệt biết đây là phần cấu hình viewport của trang
- `width=device-width`: chiều rộng của trang sẽ bằng chiều rộng thật của thiết bị
- `initial-scale=1.0`: mức zoom ban đầu là 1, không bị thu nhỏ hoặc phóng to sẵn

## 2) Nếu thiếu thẻ này, iPhone sẽ hiển thị trang như thế nào

Nếu thiếu thẻ này, iPhone sẽ giả sử trang web rộng khoảng 980px như desktop, sau đó tự thu nhỏ toàn bộ trang để nhét vừa màn hình, kết quả là chữ rất nhỏ, nút bấm khó bấm, người dùng phải zoom mới đọc được

## 3) Mobile-First và Desktop-First khác nhau thế nào

### Mobile-First
Viết CSS mặc định cho mobile trước, sau đó dùng `@media (min-width: ...)` để mở rộng cho tablet và desktop

Ví dụ:

    .box {
        width: 100%;
        padding: 12px;
    }

    @media (min-width: 768px) {
        .box {
            width: 50%;
        }
    }

### Desktop-First
Viết CSS mặc định cho desktop trước, sau đó dùng `@media (max-width: ...)` để giảm xuống cho tablet và mobile

Ví dụ:

    .box {
        width: 50%;
        padding: 20px;
    }

    @media (max-width: 768px) {
        .box {
            width: 100%;
        }
    }

### Tại sao Mobile-First được khuyên dùng

Theo em, Mobile-First được khuyên dùng vì:
- phù hợp với xu hướng người dùng truy cập bằng điện thoại nhiều hơn
- CSS gốc nhẹ hơn, tập trung vào nội dung quan trọng trước
- dễ mở rộng dần lên tablet và desktop bằng `min-width`
- phù hợp với cách Google ưu tiên mobile trước

# Câu A2 — Breakpoints

| Breakpoint | Kích thước | Thiết bị đại diện | Ví dụ số cột sản phẩm |
|-----------|------------|-------------------|-----------------------|
| Mobile | < 576px | iPhone SE, điện thoại nhỏ | 1 cột |
| Mobile L | ≥ 576px | điện thoại lớn, điện thoại ngang | 2 cột |
| Tablet | ≥ 768px | iPad dọc, tablet | 2 hoặc 3 cột |
| Desktop | ≥ 992px | laptop nhỏ | 3 cột |
| Desktop L | ≥ 1200px | desktop, laptop lớn | 4 cột |
| Desktop XL | ≥ 1400px | màn hình lớn | 4 hoặc 5 cột |

# Câu A3 — Media Queries

Cho CSS:

    .container { width: 100%; padding: 10px; }

    @media (min-width: 576px) { .container { width: 540px; } }
    @media (min-width: 768px) { .container { width: 720px; } }
    @media (min-width: 992px) { .container { width: 960px; } }
    @media (min-width: 1200px) { .container { width: 1140px; } }

| Chiều rộng màn hình | `.container` width |
|---------------------|--------------------|
| 375px (iPhone SE) | 100% |
| 600px | 540px |
| 800px | 720px |
| 1000px | 960px |
| 1400px | 1140px |

Giải thích ngắn:
- 375px chưa đạt 576px, nên dùng width mặc định là 100%
- 600px lớn hơn hoặc bằng 576px, nên nhận 540px
- 800px lớn hơn hoặc bằng 768px, nên nhận 720px
- 1000px lớn hơn hoặc bằng 992px, nên nhận 960px
- 1400px lớn hơn hoặc bằng 1200px, nên nhận 1140px

# Câu A4 — SCSS Basics

## 1) Variables

SCSS cho phép tạo biến bằng dấu `$`, giúp lưu màu, spacing, font hoặc breakpoint để dùng lại nhiều nơi

Ví dụ:
```
    $primary-color: #2563eb;

    .btn {
        background: $primary-color;
    }
```
## 2) Nesting

SCSS cho phép viết lồng nhau theo cấu trúc HTML hoặc component, giúp code gọn hơn và dễ đọc hơn

Ví dụ:
```
    .card {
        padding: 16px;

        .card-title {
            font-size: 20px;
        }

        &:hover {
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        }
    }
```
## 3) Mixins

Mixin giống như một đoạn CSS tái sử dụng được, có thể truyền tham số vào

Ví dụ:
```
    @mixin flex-center {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .box {
        @include flex-center;
    }
```
## 4) @extend / Inheritance

`@extend` cho phép một class dùng lại style của class khác

Ví dụ:
```
    .btn {
        padding: 10px 16px;
        border-radius: 6px;
    }

    .btn-primary {
        @extend .btn;
        background: blue;
        color: white;
    }
```
## Tại sao trình duyệt không đọc được file `.scss`

Trình duyệt chỉ đọc được CSS, không đọc trực tiếp được SCSS, vì SCSS là ngôn ngữ tiền xử lý, cần phải compile thành CSS trước rồi trình duyệt mới hiểu

## Cần bước gì để chuyển SCSS sang CSS

Cần có bước **compile SCSS → CSS**, có thể dùng:
- Live Sass Compiler trong VS Code
- hoặc lệnh như `npx sass style.scss style.css`

# Ghi chú B3 — SCSS Refactor

## Variables đã dùng
Em tạo các variables như:
- `$primary-color`
- `$secondary-color`
- `$surface-color`
- `$text-color`
- `$font-primary`
- `$breakpoint-tablet`
- `$breakpoint-desktop`
- `$spacing-sm`, `$spacing-md`, `$spacing-lg`

## Nesting
Em dùng nesting trong các block như:
- `.site-header`
- `.nav-menu`
- `.card`

Em cũng dùng parent selector `&` trong:
- `&:hover`
- `&.featured`

## Mixins
Em tạo 3 mixins:
- `respond-to($breakpoint)`
- `flex-center`
- `card-shadow`

## Compile SCSS → CSS
Lệnh compile em dùng là:

    npx sass scss/style.scss scss/style.css --watch