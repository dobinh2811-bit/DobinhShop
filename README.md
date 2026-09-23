# REGEDIT STORE — Free Fire
Bộ giao diện storefront tĩnh, responsive, có giỏ hàng và tạo mã đơn demo.

## Deploy Cloudflare Pages
1. Giải nén ZIP.
2. Upload thư mục này lên Cloudflare Pages/hosting static.
3. Không cần build command; thư mục gốc chứa `index.html`.

## Lưu ý
Đây là frontend demo. Chức năng thanh toán thật và tự động giao file/key cần backend/API riêng (không nên nhúng secret/API key vào JavaScript phía trình duyệt).


## Kết nối API thanh toán
Trong `assets/app.js`, đổi `PAYMENT_API_URL` thành endpoint backend của bạn nếu muốn dùng API. Nếu để trống (`''`), website sẽ dùng QR Techcombank có sẵn và không còn báo lỗi kết nối API. Frontend gửi POST JSON:

```json
{
  "customer": {"name": "...", "contact": "..."},
  "items": [{"id": 1, "name": "Regedit Basic", "price": 29000}],
  "total": 29000,
  "currency": "VND"
}
```

Backend nên trả JSON có `order_code` và URL thanh toán ở một trong các trường `payment_url`, `checkout_url` hoặc `url`. Không đặt secret/API key của cổng thanh toán trong frontend; secret phải nằm ở backend.
