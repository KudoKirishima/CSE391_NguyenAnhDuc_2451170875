# Câu A1 — HTTP & Browser

1. Khi gõ https://shopee.vn vào trình duyệt và ấn Enter. Các bước xảy ra sẽ là:

Bước 1: Trình duyệt thực hiện "DNS lookup" để tìm IP của website (shopee.vn)

Bước 2: Sau khi có được IP, trình duyệt sẽ gửi "request" (yêu cầu) từ máy người dùng qua Internet và đến "server" (máy chủ)

Bước 3: Server sau khi nhận được request thì sẽ bắt đầu tìm tài nguyên để trả về (VD: HTML của trang web)

Bước 4: Server sẽ gửi lại "HTTP response" cho trình duyệt

Bước 5: Sau khi nhận dữ liệu, bắt đầu "parse HTML" để tạo cấu trúc trang

Bước 6: Trình duyệt sẽ tiếp tục tải thêm các tài nguyên khác như CSS và JavaScript (JS)

Bước 7: Trình duyệt thực hiện "parse CSS" sau đó sẽ "Execute" (thực thi) JS nếu có

Bước 8: Cuối cùng, trình duyệt thực hiện "Layout → Paint → Composite" để "render" giao diện ra màn hình 

Nguồn tham chiếu: Chương 1 của tuần 1 tại phần 0, phần 2 và phần 3

2. Trong DevTools của Chrome, tab Network cho ta thấy thông tin:

- Các request được gửi đi
- Các response mà server trả về
- Tên file hoặc tài nguyên được tải
- Các "status code" (Mã trạng thái) như là '200', '404', '500', '301'.
- Loại tài nguyên như HTML, CSS, JS và ảnh
- Thời gian tải của từng request và tổng thời gian tải trang


<img width="625" height="746" alt="vdnetwork" src="https://github.com/user-attachments/assets/5df051dd-cb95-4f9f-8c66-da53a30bca84" />

# Câu A2 - Semantic HTML

Theo em, trang web bị đánh giá SEO thấp là do đang dùng quá nhiều thẻ <div> cho những phần không cần nhất thiết phải dùng hoặc đã có ý nghĩa rõ ràng như: đầu trang (header), menu (nav), ...

Tóm gọn lại có ít nhất là 4 lỗi như sau:

- Dùng thẻ <div class="header"> cho đầu trang thay vì thẻ <header>

- Dùng thẻ <div class = "menu"> thay vì thẻ <nav>

- Dùng thẻ <div class="main"> thay vì thẻ <main>

- Dùng thẻ <div class="footer"> thay vì thẻ <footer>

Để sửa lại thì sẽ thành:

<header>
    <div class="logo">ShopTLU</div>
    <nav>
        <div><a href="/">Trang chủ</a></div>
        <div><a href="/products">Sản phẩm</a></div>
    </nav>
</header>
<main>
    <div class="product">
        <div class="title">iPhone 16 Pro</div>
        <div class="price">25.990.000đ</div>
        <div class="image"><img src="iphone.jpg"></div>
    </div>
</main>
<footer>© 2026 ShopTLU</footer>

