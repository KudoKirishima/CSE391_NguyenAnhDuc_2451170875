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

# Câu B3 — SCSS Refactor

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

# Câu C1 — Phân tích trang web thực

Em chọn trang: Shopee

## 1) Ở kích thước Mobile, khoảng 375px
- Navigation thay đổi: menu đầy đủ không hiện hết như desktop, giao diện ưu tiên thanh tìm kiếm và các nút quan trọng hơn
- Lưới content thay đổi: số cột sản phẩm giảm xuống, thường còn 1 hoặc 2 cột tùy khu vực
- Elements bị ẩn trên mobile: một số banner lớn, menu phụ hoặc thông tin ít quan trọng có thể bị ẩn hoặc rút gọn
- Font size: font thường nhỏ gọn hơn desktop để phù hợp màn hình nhỏ

## 2) Ở kích thước Tablet, khoảng 768px
- Navigation thay đổi: vẫn là dạng ngang nhưng thoáng hơn mobile, có thể hiện được nhiều menu hơn
- Lưới content thay đổi: thường tăng lên 2 hoặc 3 cột
- Elements bị ẩn: ít hơn mobile, nhưng vẫn có thể rút gọn một số phần phụ
- Font size: lớn hơn mobile một chút, dễ đọc hơn

## 3) Ở kích thước Desktop, khoảng 1440px
- Navigation thay đổi: menu đầy đủ, hiển thị ngang rõ ràng
- Lưới content thay đổi: nhiều cột hơn, thường 4 hoặc 5 cột tùy khu vực
- Elements bị ẩn: gần như không bị ẩn, nhiều thành phần được hiển thị đầy đủ hơn
- Font size: nhìn chung thoáng hơn và cân đối hơn mobile

## 4) Media queries quan sát được
Sau khi mở DevTools và xem phần Styles, em thấy trang có dùng media queries để thay đổi layout theo chiều rộng màn hình, ví dụ:
- media query cho màn hình nhỏ hơn để giảm số cột
- media query cho màn hình lớn hơn để tăng số cột và hiện thêm nội dung

# Câu C2 — Thiết kế Responsive Strategy

## 1) Wireframe cho Mobile

    ┌────────────────────────┐
    │ Logo + nút gọi đặt bàn │
    ├────────────────────────┤
    │      Hero image        │
    ├────────────────────────┤
    │     Form đặt bàn       │
    ├────────────────────────┤
    │   Grid ảnh món ăn 1 cột│
    ├────────────────────────┤
    │     Google Maps        │
    ├────────────────────────┤
    │       Footer           │
    └────────────────────────┘

Theo em ở mobile:
- không nên hiện quá nhiều phần ngang
- form nên đặt sớm để người dùng thao tác nhanh
- grid ảnh nên để 1 cột
- bản đồ nên để bên dưới
- không cần sidebar riêng

## 2) Wireframe cho Tablet

    ┌──────────────────────────────────┐
    │ Logo + số điện thoại đặt bàn     │
    ├──────────────────────────────────┤
    │            Hero image            │
    ├──────────────────────────────────┤
    │         Form đặt bàn             │
    ├──────────────────────────────────┤
    │      Grid ảnh món ăn 2 cột       │
    ├──────────────────────────────────┤
    │          Google Maps             │
    ├──────────────────────────────────┤
    │             Footer               │
    └──────────────────────────────────┘

Theo em ở tablet:
- vẫn ưu tiên form nằm trên
- ảnh món ăn có thể chia 2 cột
- bản đồ để dưới form hoặc dưới gallery
- layout chưa cần chia nhiều cột như desktop

## 3) Wireframe cho Desktop

    ┌──────────────────────────────────────────────────┐
    │ Logo                     Số điện thoại đặt bàn   │
    ├──────────────────────────────────────────────────┤
    │                  Hero image toàn trang           │
    ├──────────────────────────────┬───────────────────┤
    │      Grid ảnh món ăn         │    Form đặt bàn  │
    │          3 cột               │                   │
    ├──────────────────────────────┴───────────────────┤
    │                 Google Maps full width           │
    ├──────────────────────────────────────────────────┤
    │                     Footer                       │
    └──────────────────────────────────────────────────┘

Theo em ở desktop:
- có thể chia 2 cột lớn, một bên là ảnh món ăn, một bên là form đặt bàn
- grid ảnh có thể 3 cột
- bản đồ đặt full width phía dưới
- không cần sidebar riêng nếu trang chỉ tập trung vào đặt bàn và xem món

## 4) CSS skeleton theo Mobile-First
```
    * {
        box-sizing: border-box;
    }

    body {
        margin: 0;
        font-family: Arial, sans-serif;
    }

    .page {
        display: grid;
        grid-template-columns: 1fr;
        gap: 16px;
        padding: 16px;
    }

    .header,
    .hero,
    .booking-form,
    .gallery,
    .map,
    .footer {
        background: #f3f4f6;
        padding: 16px;
        border-radius: 8px;
    }

    .gallery-grid {
        display: grid;
        grid-template-columns: 1fr;
        gap: 16px;
    }

    @media (min-width: 768px) {
        .gallery-grid {
            grid-template-columns: repeat(2, 1fr);
        }
    }

    @media (min-width: 1024px) {
        .content {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 20px;
        }

        .gallery-grid {
            grid-template-columns: repeat(3, 1fr);
        }
    }
```
## 5) Giải thích ngắn
- Mobile mặc định dùng 1 cột để dễ đọc và dễ thao tác
- Tablet tăng lên 2 cột cho gallery
- Desktop chia khu vực ảnh và form thành 2 cột lớn
- Cách này đúng theo hướng Mobile-First, viết từ nhỏ đến lớn bằng min-width