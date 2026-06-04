# Câu A1 — Input Types

1. `type="text"` → Ô nhập văn bản thông thường → Có thể kiểm tra bằng `minlength`, `maxlength`, `pattern` → Dùng cho họ tên hoặc username trong form đăng ký tài khoản.

2. `type="email"` → Ô nhập text, trên một số thiết bị sẽ gợi ý bàn phím phù hợp → Browser tự kiểm tra định dạng email có hợp lệ hay không → Dùng cho email đăng ký tài khoản hoặc email nhận thông báo đơn hàng.

3. `type="password"` → Ô nhập có ký tự bị ẩn → Có thể kiểm tra bằng `minlength` và `pattern` → Dùng cho mật khẩu đăng ký hoặc đăng nhập.

4. `type="number"` → Ô nhập số, thường có nút tăng giảm → Có thể kiểm tra bằng `min`, `max`, `step` → Dùng cho số lượng sản phẩm cần mua.

5. `type="tel"` → Ô nhập số điện thoại, trên mobile thường hiện bàn phím số → Không tự kiểm tra số điện thoại đúng hay sai nếu không có `pattern` → Dùng cho số điện thoại giao hàng hoặc liên hệ khách hàng.

6. `type="date"` → Ô chọn ngày / date picker → Có thể kiểm tra bằng `min` và `max` → Dùng cho ngày sinh hoặc ngày giao hàng mong muốn.

7. `type="search"` → Ô tìm kiếm, thường có nút xóa nhanh trên một số trình duyệt → Không có validation mạnh → Dùng cho ô tìm kiếm sản phẩm trong trang E-Commerce.

8. `type="checkbox"` → Ô vuông để tích chọn hoặc bỏ chọn → Có thể dùng `required` nếu bắt buộc người dùng đồng ý → Dùng cho checkbox đồng ý điều khoản hoặc chọn nhận thông báo khuyến mãi.

9. `type="radio"` → Nút tròn để chọn một trong nhiều lựa chọn → Có thể dùng `required` để bắt buộc chọn một giá trị → Dùng cho chọn giới tính, phương thức thanh toán hoặc cách giao hàng.

10. `type="file"` → Nút chọn file từ máy tính → Có thể kết hợp `accept` và `multiple` → Dùng cho upload ảnh đại diện, ảnh xác nhận thanh toán hoặc file chứng từ.

**Nguồn tham chiếu:** `tuan_1_html5/07_forms_interactive.md` — phần `3. Core Technical Truth`; bảng `Tất cả Input Types HTML5`.

---

# Câu A2 — Validation Attributes

## Dự đoán kết quả khi bấm Submit

### Trường hợp 1
`<input type="text" required value="">`

- Dự đoán: Form **không submit được**.
- Lý do: Input này có `required` nhưng đang để trống, nên browser sẽ báo người dùng phải nhập trường này.

### Trường hợp 2
`<input type="email" value="abc">`

- Dự đoán: Form **không submit được**.
- Lý do: `type="email"` yêu cầu giá trị nhập vào phải đúng định dạng email. Chuỗi `"abc"` không có dạng email hợp lệ nên browser sẽ báo lỗi.

### Trường hợp 3
`<input type="number" min="1" max="10" value="15">`

- Dự đoán: Form **không submit được**.
- Lý do: Giá trị `15` lớn hơn `max="10"`, nên không thỏa điều kiện hợp lệ của trường number.

### Trường hợp 4
`<input type="text" pattern="[0-9]{10}" value="abc123">`

- Dự đoán: Form **không submit được**.
- Lý do: `pattern="[0-9]{10}"` yêu cầu phải là đúng 10 chữ số liên tiếp. Giá trị `"abc123"` không khớp pattern này.

### Trường hợp 5
`<input type="password" minlength="8" value="123">`

- Dự đoán: Form **không submit được**.
- Lý do: Trường password yêu cầu tối thiểu 8 ký tự nhưng `"123"` chỉ có 3 ký tự.

## So sánh với kết quả validation thực tế

Sau khi tạo file `validation_test.html` và bấm Submit để kiểm tra, quan sát thấy kết quả thực tế **khớp với dự đoán**:
- Trường hợp 1 báo thiếu dữ liệu bắt buộc.
- Trường hợp 2 báo sai định dạng email.
- Trường hợp 3 báo giá trị vượt quá giới hạn cho phép.
- Trường hợp 4 báo không đúng pattern.
- Trường hợp 5 báo chưa đủ số ký tự tối thiểu.

**Nguồn tham chiếu:** `tuan_1_html5/07_forms_interactive.md` — phần `3. Core Technical Truth`; mục `Validation Attributes`; phần `9. Summary — 5 điều quan trọng nhất`.

---

# Câu A3 — Accessibility

## 1) Tại sao `<label for="email">` quan trọng cho người dùng screen reader?

`<label for="email">` quan trọng vì nó giúp screen reader biết được ô input đó dùng để nhập gì. Khi `for` của label khớp với `id` của input, công cụ hỗ trợ sẽ đọc đúng tên trường, ví dụ “Email”. Ngoài ra, khi click vào label thì con trỏ cũng sẽ focus vào ô nhập tương ứng, nên thuận tiện hơn cho người dùng.

## 2) Khi nào dùng `<fieldset>` + `<legend>`? Cho ví dụ cụ thể.

`<fieldset>` và `<legend>` được dùng khi có một nhóm input liên quan với nhau. Cách này giúp chia form rõ ràng hơn và cũng tốt cho accessibility.

Ví dụ: nhóm chọn giới tính hoặc nhóm chọn phương thức thanh toán.

Ví dụ cụ thể:

- `<fieldset>` bao nhóm chọn phương thức thanh toán
- `<legend>` ghi “Phương thức thanh toán”
- Bên trong có các radio như COD, Chuyển khoản, Ví điện tử

## 3) `aria-label` dùng khi nào? Tại sao KHÔNG nên dùng `aria-label` khi đã có `<label>`?

`aria-label` thường dùng khi phần tử không có nhãn hiển thị rõ ràng, ví dụ một nút chỉ có icon. Khi đó `aria-label` giúp screen reader hiểu chức năng của phần tử.

Không nên dùng `aria-label` khi đã có `<label>` vì `<label>` đã là cách semantic và dễ hiểu hơn. Nếu đã có label rồi mà vẫn thêm `aria-label` không cần thiết thì có thể gây trùng lặp hoặc làm code rối hơn.

**Nguồn tham chiếu:** `tuan_1_html5/07_forms_interactive.md` — phần `3. Core Technical Truth`; mục `Accessibility — Form cho mọi người`; phần `9. Summary — 5 điều quan trọng nhất`.

---

# Câu A4 — Media

## 1) Giải thích `loading="lazy"` trên thẻ `<img>`. Nó cải thiện gì? Khi nào KHÔNG nên dùng?

`loading="lazy"` làm cho ảnh chỉ được tải khi người dùng cuộn gần đến ảnh đó. Cách này giúp trang tải nhanh hơn lúc đầu, giảm băng thông và cải thiện tốc độ load trang.

Tuy nhiên, không nên dùng `loading="lazy"` cho các ảnh quan trọng ở đầu trang như logo, ảnh hero hoặc ảnh đầu tiên người dùng nhìn thấy, vì các ảnh đó cần hiển thị ngay.

## 2) Tại sao nên cung cấp nhiều `<source>` trong thẻ `<video>`? Liệt kê ít nhất 3 format video web phổ biến.

Nên cung cấp nhiều `<source>` trong thẻ `<video>` để tăng khả năng tương thích với nhiều trình duyệt khác nhau. Nếu trình duyệt không hỗ trợ format này thì có thể dùng format khác.

Ba format video web phổ biến là:
- `mp4`
- `webm`
- `ogg`

## 3) Thuộc tính `alt` trên `<img>` dùng để làm gì? Viết `alt` tốt cho 3 trường hợp.

Thuộc tính `alt` dùng để mô tả nội dung ảnh cho screen reader và cũng hiển thị khi ảnh bị lỗi không tải được.

### a) Ảnh sản phẩm iPhone 16
`alt="iPhone 16 màu đen nhìn từ mặt trước"`

### b) Ảnh trang trí (decorative)
`alt=""`

### c) Ảnh biểu đồ doanh thu Q1/2026
`alt="Biểu đồ doanh thu quý 1 năm 2026 của cửa hàng"`

**Nguồn tham chiếu:** `tuan_1_html5/06_graphics_multimedia.md` — phần `3. Core Technical Truth`; mục `<img> — Best Practices`; phần `7. Common Misconceptions`; phần `9. Summary — 5 điều quan trọng nhất`.

---

# Câu A5 — So sánh `<figure>` vs `<img>`

## Khi nào dùng Cách 1?

Cách 1 chỉ dùng thẻ `<img>` thì phù hợp khi chỉ cần hiển thị ảnh đơn lẻ và không cần chú thích đi kèm.

### Ví dụ thực tế:
1. Logo thương hiệu ở đầu trang.
2. Ảnh icon minh họa nhỏ trong một khối nội dung.

## Khi nào dùng Cách 2?

Cách 2 dùng `<figure>` + `<figcaption>` thì phù hợp khi ảnh cần có chú thích hoặc cần gắn với một nội dung giải thích rõ ràng.

### Ví dụ thực tế:
1. Ảnh sản phẩm trên trang chi tiết sản phẩm kèm tên và giá.
2. Ảnh biểu đồ hoặc ảnh minh họa trong bài viết có phần chú thích bên dưới.

Theo em, nếu ảnh chỉ để hiển thị đơn giản thì dùng `<img>` là đủ. Nếu ảnh cần mô tả thêm hoặc có chú thích liên quan thì nên dùng `<figure>` và `<figcaption>`.

**Nguồn tham chiếu:** `tuan_1_html5/06_graphics_multimedia.md` — phần `2. Big Picture — Bản đồ Media trong HTML`; phần `3. Core Technical Truth`; phần `9. Summary — 5 điều quan trọng nhất`.

# Câu C1 — Debug Form

Lỗi 1: Thẻ `<form>` thiếu `action` và `method`.  
Sửa: `<form action="#" method="POST">`

Lỗi 2: Input “Tên” không có `<label>`, `id`, `name`, và chưa có `required`.  
Sửa: `<label for="name">Tên:</label> <input type="text" id="name" name="name" required>`

Lỗi 3: Input email không có `<label>`, `id`, `name`, và nên có `required`.  
Sửa: `<label for="email">Email:</label> <input type="email" id="email" name="email" placeholder="Email của bạn" required>`

Lỗi 4: Hai ô password không có `<label>`, `id`, `name` rõ ràng.  
Sửa: thêm label, id, name cho từng ô.

Lỗi 5: Ô password thiếu validation cơ bản như `required` và `minlength`.  
Sửa: `<input type="password" id="password" name="password" required minlength="8">`

Lỗi 6: Số điện thoại đang dùng `type="text"` chưa phù hợp.  
Sửa: đổi thành `type="tel"` và thêm `pattern="[0-9]{10}"`.

Lỗi 7: `<select>` chưa có `<label>` và chưa có option mặc định.  
Sửa: thêm `<label for="city">` và option `-- Chọn thành phố --`.

Lỗi 8: Phần “Tôi đồng ý điều khoản” chưa có checkbox và chưa bắt buộc chọn.  
Sửa:
```html
<label for="agree">
    <input type="checkbox" id="agree" name="agree" required>
    Tôi đồng ý điều khoản
</label>
```

# Câu C2 — Thiết kế chiến lược Validation
## 1) Pattern regex
- CMND/CCCD đúng 12 chữ số:    `pattern="[0-9]{12}"`
- Số tài khoản từ 10 đến 15 chữ số:    `pattern="[0-9]{10,15}"`
## 2) HTML5 validation đã đủ an toàn cho ứng dụng ngân hàng chưa?
Theo em là **chưa đủ**. HTML5 validation chỉ chạy ở phía trình duyệt nên người dùng có thể sửa HTML, tắt validation hoặc gửi request bằng công cụ khác. Vì vậy vẫn phải kiểm tra lại ở backend.
## 3) Ba loại validation HTML5 không thể tự làm tốt
1. So sánh hai trường với nhau, ví dụ nhập lại PIN có giống PIN hay không.  2. Kiểm tra logic phức tạp phụ thuộc nhiều điều kiện khác nhau.  3. Kiểm tra dữ liệu theo thời gian thực như báo độ mạnh của PIN/mật khẩu.
## 4) Hai rủi ro bảo mật nếu chỉ validate ở Frontend
1. Người dùng có thể bypass validation và gửi dữ liệu sai lên server.  2. Dữ liệu độc hại hoặc dữ liệu không hợp lệ có thể đi vào hệ thống.