PHẦN A — KIỂM TRA ĐỌC HIỂU (25 điểm)
Câu A1 (5đ) — 3 Cách nhúng CSS
## 1. Inline CSS
Ví dụ:
<p style="color:red;">Hello</p>
Ưu điểm:
- Nhanh
- Test nhanh
Nhược điểm:
- Khó bảo trì
- Không tái sử dụng
Khi dùng:
- Test nhanh
- Style riêng lẻ

## 2. Internal CSS
Ví dụ:
<style>
p {
    color: blue;
}
</style>
Ưu điểm:
- Gọn trong 1 file
Nhược điểm:
- Không tái sử dụng nhiều trang
Khi dùng:
- Website nhỏ
- Demo

## 3. External CSS
Ví dụ:
<link rel="stylesheet" href="style.css">
Ưu điểm:
- Dễ quản lý
- Tái sử dụng
Nhược điểm:
- Cần thêm file
Khi dùng:
- Dự án thực tế

## Cascade
Thứ tự ưu tiên:
Inline > Internal/External
Nếu specificity bằng nhau:
- Rule viết sau thắng

Câu A2 (8đ) — CSS Selectors — Dự đoán kết quả
1. h1
→ ShopTLU
2. .price
→ 25.990.000đ
→ 45.990.000đ
3. #app header
→ Toàn bộ thẻ header
4. nav a:first-child
→ Home
5. .product.featured h2
→ MacBook Pro
6. article > p
→ 25.990.000đ
→ Mô tả sản phẩm...
→ 45.990.000đ
→ Mô tả sản phẩm...
7. a[href="/"]
→ Home
8. .top-bar.dark h1
→ ShopTLU

# Câu A3

## Trường hợp 1

width = 400px
padding = 20px * 2 = 40px
border = 5px * 2 = 10px
Chiều rộng hiển thị:
400 + 40 + 10 = 450px
Không gian chiếm:
450 + margin trái phải 20px
= 470px

## Trường hợp 2

border-box:
width đã bao gồm padding + border
Chiều rộng hiển thị:
400px
Content thực:
400 - 40 - 10
= 350px
Không gian chiếm:
400 + 20
= 420px

## Margin Collapse
25px và 40px KHÔNG cộng.
Khoảng cách: 40px
Vì Browser lấy margin lớn hơn.

## Nâng cao
-10px + 40px
Khoảng cách: 30px

# Câu A4 (5đ) — Specificity (Độ ưu tiên)

Rule A: p
Specificity:
(0,0,1)
Rule B: .price
(0,1,0)
Rule C: #main-price
(1,0,0)
Rule D: p.price
(0,1,1)

Màu cuối: red
Vì ID mạnh nhất.
Nếu inline style:
style="color: orange"
Màu: orange
Inline mạnh hơn CSS thường.

Nếu Rule A có !important:
p {
 color:black !important;
}
Màu: black
Vì !important ưu tiên cao nhất.

