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

