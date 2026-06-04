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
