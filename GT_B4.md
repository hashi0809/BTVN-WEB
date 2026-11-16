# BTVN 4

## 1. Sửa lỗi Layout (Box Model)

Component gốc bị lệch kích thước vì mọi phần tử mặc định là `content-box`:
`width` chỉ tính phần ruột (content), còn `padding` và `border` bị cộng thêm ra ngoài.

Phần ruột của form rộng 356px (card 420px trừ padding 32px mỗi bên của `.card-body`):

- Ô input: `width: 100%` = 356px ruột, cộng padding ngang 16px × 2 + border 1px × 2
  → tổng 390px, **tràn ra ngoài 34px**.
- Nút submit: `width: 100%` = 356px ruột, cộng padding ngang 24px × 2
  → tổng 404px, **tràn ra ngoài 48px**.

Cách sửa: thêm 1 rule ở đầu file CSS:

```css
* {
  box-sizing: border-box;
}
```

Với `border-box`, `width` khai bao nhiêu là tổng chiều rộng đúng bấy nhiêu,
padding và border nằm gọn bên trong. Input và nút trở về đúng 356px, thẳng hàng với form.

## 2. Hai bản Typography: px và rem

- `typography-px.css` — bản **px**: cỡ chữ khai trực tiếp bằng pixel (24px, 14px, 15px, 16px).
- `typography-rem.css` — bản **rem**: cùng các cỡ chữ đó nhưng quy đổi sang rem.
- `style.css` — bản chính, nội dung giống bản rem; `BTVN_B4.html` đang link vào file này.

Bảng quy đổi (1rem = 16px, bằng font-size của thẻ `html`):

| Phần tử | Bản px | Bản rem |
| --- | --- | --- |
| Tiêu đề h1 | 24px | 1.5rem |
| Chữ mô tả, label | 14px | 0.875rem |
| Chữ trong ô input | 15px | 0.9375rem |
| Chữ trên nút | 16px | 1rem |

Khác biệt:

- **px là đơn vị tuyệt đối**: khai 16px thì luôn là 16px, bất kể cài đặt của người dùng.
- **rem là đơn vị tương đối**: nó ăn theo font-size của thẻ `html`. Chỉ cần đổi
  `html { font-size: 20px; }` là toàn bộ chữ trong bản rem phóng to theo tỉ lệ
  (1.5rem thành 30px, 1rem thành 20px...), bố cục chữ vẫn hài hòa.
  Bản px muốn phóng to thì phải sửa từng dòng một.
- Vì rem ăn theo cỡ chữ gốc nên nó **tôn trọng cài đặt cỡ chữ của người dùng**
  trong trình duyệt (người khiếm thị tăng cỡ chữ hệ thống thì chữ web to theo);
  px thì bỏ qua cài đặt đó. Đây là lý do làm web thật người ta chuộng rem cho cỡ chữ,
  còn px hợp cho những thứ cần cố định tuyệt đối như border 1px.

**Cách xem bản px:** đổi đường dẫn stylesheet trong `BTVN_B4.html` từ `style.css` thành `typography-px.css`.
**Cách xem bản rem:** giữ nguyên `style.css` (hoặc đổi thành `typography-rem.css`).

Thử nhanh: mở bản rem, sửa `font-size` của `html` từ 16px thành 20px rồi tải lại trang —
chữ cả card to lên thấy rõ. Làm y vậy với bản px thì không có gì thay đổi.

## 3. Đánh giá lý thuyết

Hoàn thành Quiz 4 (làm trực tiếp trên hệ thống của lớp).
