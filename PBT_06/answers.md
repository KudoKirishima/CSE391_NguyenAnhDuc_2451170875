# Câu A1 — Grid System

Cho HTML:
``
    <div class="container">
        <div class="row">
            <div class="col-12 col-md-6 col-lg-3">Box 1</div>
            <div class="col-12 col-md-6 col-lg-3">Box 2</div>
            <div class="col-12 col-md-6 col-lg-3">Box 3</div>
            <div class="col-12 col-md-6 col-lg-3">Box 4</div>
        </div>
    </div>
``
| Kích thước | < 768px | 768px - 991px | ≥ 992px |
|------------|---------|---------------|---------|
| Số cột | 1 cột | 2 cột | 4 cột |
| Box layout | Box 1, Box 2, Box 3, Box 4 xếp dọc | 2 box mỗi hàng | 4 box trên 1 hàng |

Giải thích:
- `col-12` nghĩa là ở mobile, mỗi box chiếm 12/12, tức là 100% chiều ngang
- `col-md-6` nghĩa là từ breakpoint md trở lên, mỗi box chiếm 6/12, tức là 50% chiều ngang
- `col-lg-3` nghĩa là từ breakpoint lg trở lên, mỗi box chiếm 3/12, tức là 25% chiều ngang

`col-md-6` nghĩa là:
- từ màn hình có độ rộng từ 768px trở lên thì cột đó chiếm 6 phần trong tổng 12 cột

Không cần viết `col-sm-12` vì:
- Bootstrap theo kiểu mobile-first
- khi đã có `col-12`, thì mặc định ở mobile nó đã full width rồi
- không cần lặp lại thêm một class tương đương

# Câu A2 — Utilities & Components

## 1) Giải thích class `d-none d-md-block`

- `d-none` nghĩa là ẩn element hoàn toàn
- `d-md-block` nghĩa là từ màn hình md trở lên thì element hiện ra dưới dạng block

Kết luận:
- dưới 768px: bị ẩn
- từ 768px trở lên: hiện ra

## 2) 5 spacing utilities

- `mt-3`: margin-top = 1rem
- `mb-4`: margin-bottom = 1.5rem
- `px-4`: padding-left và padding-right = 1.5rem
- `py-2`: padding-top và padding-bottom = 0.5rem
- `mb-auto`: margin-bottom = auto

## 3) Sự khác nhau giữa `.container`, `.container-fluid`, `.container-md`

- `.container`: có max-width theo từng breakpoint, thường dùng cho layout nội dung chính
- `.container-fluid`: luôn full width 100%, thường dùng cho banner, hero, footer
- `.container-md`: dưới md thì full width, từ md trở lên mới có max-width

---

# Câu C1 — Tùy biến Bootstrap

## 1) Muốn đổi màu `$primary` từ xanh mặc định sang `#E63946`, quy trình là gì

Theo em, muốn đổi màu `$primary` thì không làm bằng CDN mà phải dùng Bootstrap qua npm và file SASS

Các bước:
- cài `bootstrap` và `sass`
- tạo file SCSS riêng, ví dụ `custom.scss`
- import phần `functions` trước
- gán lại `$primary: #E63946`
- sau đó mới import Bootstrap
- compile SCSS thành CSS rồi link file CSS đó vào HTML

Ví dụ:

    @import "bootstrap/scss/functions";

    $primary: #E63946;

    @import "bootstrap/scss/bootstrap";

## 2) Tại sao không nên override trực tiếp `.btn-primary { background: red; }`

Không nên override trực tiếp vì:
- chỉ sửa được một phần giao diện
- dễ bị lệch với các component khác như alert, badge, link, form
- về sau khó maintain
- nếu đổi màu brand tiếp thì phải sửa lại nhiều chỗ

Dùng SASS variables tốt hơn vì:
- đổi một lần, nhiều component đổi theo
- đồng bộ hơn
- giống cách làm trong dự án thật

# Câu C2 — So sánh

## So sánh CSS thuần với Bootstrap cho navbar responsive và product card

### 1) Số dòng CSS cần viết
- CSS thuần: phải tự viết khá nhiều dòng CSS cho navbar, card, hover, responsive
- Bootstrap: gần như chỉ cần class trong HTML, ít hoặc không cần CSS riêng

### 2) Thời gian phát triển
- CSS thuần: lâu hơn vì phải tự code và test
- Bootstrap: nhanh hơn vì có component và utilities sẵn

### 3) Khả năng tùy biến
- CSS thuần: tùy biến cao nhất
- Bootstrap: nhanh nhưng nếu muốn khác hẳn giao diện mặc định thì phải customize thêm

### 4) Khi nào nên dùng Bootstrap
- khi cần làm nhanh
- khi làm admin panel, dashboard, prototype, bài tập deadline ngắn
- khi không có nhiều thời gian viết CSS từ đầu

### 5) Khi nào không nên dùng Bootstrap
- khi dự án cần giao diện riêng biệt theo brand mạnh
- khi cần tối ưu giao diện rất sâu và không muốn phụ thuộc nhiều vào framework