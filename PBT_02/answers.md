# Câu A1 — Input Types

1. `type="text"` → Ô nhập văn bản thông thường → Có thể kết hợp `minlength`, `maxlength`, `pattern` để kiểm tra → Dùng cho họ tên hoặc username trong form đăng ký tài khoản.

2. `type="email"` → Ô nhập text bình thường, trên một số thiết bị sẽ gợi ý bàn phím phù hợp → Browser tự kiểm tra định dạng email có hợp lệ hay không → Dùng cho email đăng ký tài khoản hoặc email nhận thông báo đơn hàng.

3. `type="password"` → Ô nhập có ký tự bị ẩn đi → Có thể kiểm tra bằng `minlength` và `pattern` → Dùng cho mật khẩu đăng ký hoặc đăng nhập tài khoản.

4. `type="number"` → Ô nhập số, thường có nút tăng giảm ở cạnh phải → Có thể kiểm tra bằng `min`, `max`, `step` → Dùng cho số lượng sản phẩm cần mua.

5. `type="tel"` → Ô nhập số điện thoại, trên mobile thường hiện bàn phím số → Không tự kiểm tra số điện thoại đúng hay sai nếu không có `pattern` → Dùng cho số điện thoại giao hàng hoặc liên hệ khách hàng.

6. `type="date"` → Hiển thị ô chọn ngày / date picker → Có thể kiểm tra bằng `min` và `max` → Dùng cho ngày sinh hoặc ngày giao hàng mong muốn.

7. `type="search"` → Ô tìm kiếm, thường có biểu tượng hoặc nút xóa nhanh trên một số trình duyệt → Không có validation mạnh, chủ yếu phục vụ giao diện tìm kiếm → Dùng cho ô tìm kiếm sản phẩm trong trang E-Commerce.

8. `type="checkbox"` → Ô vuông để tích chọn hoặc bỏ chọn → Có thể dùng `required` nếu bắt buộc người dùng đồng ý → Dùng cho checkbox đồng ý điều khoản hoặc chọn nhận thông báo khuyến mãi.

9. `type="radio"` → Nút tròn để chọn một trong nhiều lựa chọn → Có thể dùng `required` để bắt buộc chọn một giá trị → Dùng cho chọn giới tính, phương thức thanh toán hoặc cách giao hàng.

10. `type="file"` → Nút chọn file từ máy tính → Có thể kết hợp `accept` và `multiple` → Dùng cho upload ảnh đại diện, ảnh xác nhận thanh toán hoặc file chứng từ.