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
