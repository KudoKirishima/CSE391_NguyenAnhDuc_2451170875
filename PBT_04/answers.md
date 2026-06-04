# Câu A1 — 5 Loại Positioning

| Position | Vẫn chiếm chỗ trong flow? | Tham chiếu vị trí | Cuộn theo trang? | Use case |
|----------|----------------------------|-------------------|------------------|----------|
| `static` | Có | Không dùng `top/right/bottom/left`, nằm theo flow bình thường | Có | Layout mặc định của phần lớn element |
| `relative` | Có | So với vị trí gốc của chính nó | Có | Dịch nhẹ element hoặc làm mốc cho phần tử con `absolute` |
| `absolute` | Không | Tổ tiên gần nhất có `position` khác `static` | Có | Badge, dropdown, tooltip, overlay nhỏ |
| `fixed` | Không | Viewport | Không | Nút chat, nút lên đầu trang, header cố định |
| `sticky` | Có | Ban đầu theo flow, khi chạm ngưỡng thì bám theo viewport | Ban đầu có cuộn, đến ngưỡng thì dính lại | Sticky header, sticky sidebar |

## Câu hỏi thêm: Khi nào `absolute` tham chiếu `body`? Khi nào tham chiếu parent?

Theo em, `absolute` sẽ tham chiếu đến **tổ tiên gần nhất có `position` khác `static`**. Đó chính là ý của khái niệm **nearest positioned ancestor**.

- Nếu phần tử cha có `position: relative`, `absolute`, `fixed` hoặc `sticky` thì phần tử `absolute` sẽ lấy cha đó làm mốc tọa độ.
- Nếu cha trực tiếp không có `position` phù hợp, browser sẽ tiếp tục tìm lên các phần tử phía trên.
- Nếu không tìm thấy tổ tiên nào có `position` khác `static`, thì phần tử `absolute` sẽ bám theo trang, thường có thể hiểu là theo `html/body`.

Ví dụ:
- Parent có `position: relative` → con `absolute` bám theo parent
- Parent là `static`, nhưng ông nội là `relative` → con `absolute` bám theo ông nội
- Không có ancestor nào phù hợp → con `absolute` bám theo trang

# Câu A2 — Flexbox vs Grid

## Trường hợp 1

`.container { display: flex; }`  
`.item { flex: 1; }`

**Dự đoán bố cục:**  
4 items sẽ nằm trên **1 hàng**, mỗi item có chiều rộng bằng nhau.

Text art:

| item 1 | item 2 | item 3 | item 4 |

---

## Trường hợp 2

`.container { display: flex; flex-wrap: wrap; }`  
`.item { width: 45%; margin: 2.5%; }`

**Dự đoán bố cục:**  
Mỗi item chiếm khoảng `45% + 2.5% + 2.5% = 50%` chiều ngang, nên sẽ có **2 item mỗi hàng**.  
6 items sẽ thành **3 hàng, mỗi hàng 2 cột**.

Text art:

| item 1 | item 2 |
| item 3 | item 4 |
| item 5 | item 6 |

---

## Trường hợp 3

`.container { display: flex; justify-content: space-between; align-items: center; }`

**Dự đoán bố cục:**  
3 items nằm trên **1 hàng**, khoảng cách giữa các item được dàn đều theo chiều ngang, và các item được căn giữa theo chiều dọc.

Text art:

| item 1           item 2           item 3 |

---

## Trường hợp 4

`.container { display: grid; grid-template-columns: 200px 1fr 200px; gap: 20px; }`

**Dự đoán bố cục:**  
3 items nằm trên **1 hàng** theo 3 cột:
- cột 1 rộng `200px`
- cột 2 rộng `1fr` (co giãn phần còn lại)
- cột 3 rộng `200px`

Text art:

| 200px |  --- 1fr ---  | 200px |
| item1 |      item2    | item3 |

---

## Trường hợp 5

`.container { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; }`

**Dự đoán bố cục:**  
Grid có **3 cột bằng nhau**.  
7 items sẽ xếp thành **3 hàng**:
- hàng 1: 3 item
- hàng 2: 3 item
- hàng 3: 1 item

Item cuối cùng sẽ nằm ở **hàng 3, cột 1**.

Text art:

| item 1 | item 2 | item 3 |
| item 4 | item 5 | item 6 |
| item 7 |        |        |

# Câu C1 — Flexbox vs Grid: Khi nào dùng gì?

1. Navigation bar ngang (logo + menu + buttons)  
→ Dùng Flexbox  
Vì đây là layout một chiều theo hàng ngang. Flexbox rất hợp để căn trái, giữa, phải và căn giữa theo chiều dọc.

2. Lưới ảnh Instagram (3 cột đều nhau, số ảnh không biết trước)  
→ Dùng Grid  
Vì đây là layout dạng lưới, cần chia cột đều nhau và các item có thể tự xuống hàng.

3. Layout blog: main content + sidebar  
→ Dùng Grid  
Vì đây là bố cục chia cột rõ ràng, Grid giúp chia vùng main và sidebar dễ hơn.

4. Footer với 4 cột thông tin  
→ Dùng Grid  
Vì footer có nhiều cột song song, Grid giúp chia 4 cột đều nhau gọn hơn.

5. Card sản phẩm (ảnh trên, text giữa, nút dưới — nút luôn dính đáy)  
→ Dùng Flexbox  
Vì bên trong card là bố cục một chiều từ trên xuống dưới. Dùng flex-direction: column và margin-top: auto cho nút là phù hợp.

# Câu C2 — Debug Flexbox

## Lỗi 1: Cards không đều chiều cao, nút "Mua" bị nhảy lên/xuống

Nguyên nhân:  
Các card có lượng nội dung khác nhau nên chiều cao mỗi card khác nhau. Ngoài ra, nút chưa được đẩy xuống cuối card nên vị trí không đều.

Cách sửa:

    .card-container {
        display: flex;
        flex-wrap: wrap;
        gap: 20px;
    }

    .card {
        width: 30%;
        margin: 1.5%;
        display: flex;
        flex-direction: column;
    }

    .card img {
        width: 100%;
    }

    .card .btn {
        padding: 10px;
        margin-top: auto;
    }

Giải thích:  
- display: flex và flex-direction: column trên .card giúp sắp xếp nội dung theo chiều dọc  
- margin-top: auto đẩy nút xuống cuối card  

## Lỗi 2: Muốn items nằm giữa cả ngang lẫn dọc trong container 100vh, nhưng item vẫn dính góc trái trên

Nguyên nhân:  
Container .hero mới chỉ có display: flex nhưng chưa có thuộc tính căn giữa theo chiều ngang và chiều dọc.

Cách sửa:

    .hero {
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .hero-content {
        text-align: center;
    }

Giải thích:  
- justify-content: center căn giữa theo chiều ngang  
- align-items: center căn giữa theo chiều dọc  

## Lỗi 3: Sidebar bị co lại khi content quá dài

Nguyên nhân:  
Trong Flexbox, item có thể bị co nếu không chặn việc co lại. Sidebar đang có width: 250px nhưng vẫn có thể bị shrink.

Cách sửa:

    .layout {
        display: flex;
    }

    .sidebar {
        width: 250px;
        flex-shrink: 0;
    }

    .content {
        flex: 1;
    }

Giải thích:  
- flex-shrink: 0 giúp sidebar giữ nguyên chiều rộng 250px  
- .content dùng flex: 1 để chiếm phần không gian còn lại  
