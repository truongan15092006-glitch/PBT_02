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

# Bài B1
## Các loại selector đã sử dụng
1. Element selector
Ví dụ:
table
body
footer
2. ID selector
Ví dụ:
#main-header
3. Class selector
Ví dụ:
.active
4. Descendant selector
Ví dụ:
nav a
5. Pseudo-class selector
Ví dụ:
nav a:hover
tr:nth-child(even)
tr:hover
## Giải thích
- Element selector:
chọn theo tên thẻ HTML.
- ID selector:
chọn phần tử có id cụ thể.
- Class selector:
chọn phần tử theo class.
- Descendant selector:
chọn phần tử con bên trong phần tử cha.
- Pseudo-class:
tác động khi có trạng thái đặc biệt như hover.

# Bài B2

## Phần 1 — Content-box vs Border-box

### Hộp 1 (content-box)

width = 300px
padding = 20px x 2 = 40px
border = 5px x 2 = 10px

Chiều rộng thực tế:
300 + 40 + 10
= 350px

---

### Hộp 2 (border-box)

width = 300px

Padding và border đã tính bên trong width.

Chiều rộng thực tế:
300px

---

## Giải thích sự khác biệt

- content-box:
width chỉ tính content.

- border-box:
width bao gồm:
content + padding + border.

Vì vậy border-box dễ kiểm soát layout hơn.

---

## Phần 2 — Layout 3 cột
### Nếu không dùng border-box
Sidebar:
250 + 30 padding
= 280px
Content:
500 + 40 padding
= 540px
Ads:
250 + 30 padding
= 280px
Tổng:
280 + 540 + 280
= 1100px
=> vượt quá container 1000px.

### Nếu dùng border-box
Padding được tính bên trong width.
Tổng
250 + 500 + 250
= 1000px
=> layout không bị vỡ.

# Bài B3

## Danh sách specificity
1. p
Specificity:
(0,0,1)
2. .text
(0,1,0)
3. .highlight
(0,1,0)
4. p.text
(0,1,1)
5. body p
(0,0,2)
6. body .text
(0,1,1)
7. p.highlight
(0,1,1)
8. #demo
(1,0,0)
9. #demo.text
(1,1,0)
10. #demo.text.highlight
(1,2,0)

## Màu cuối cùng
Màu:
gold
Vì: #demo.text.highlight
có specificity mạnh nhất:
(1,2,0)


## Nếu đổi thứ tự CSS
- Nếu specificity KHÁC nhau:
kết quả không đổi.
- Nếu specificity BẰNG nhau:
rule viết sau sẽ thắng.
Ví dụ:
.text và .highlight
đều có: (0,1,0)
Rule nào viết sau sẽ được áp dụng.

# Câu C1
## 1. Tính chiều rộng thực tế
### Sidebar
width = 300px
padding:
20px x 2 = 40px
border:
1px x 2 = 2px
Chiều rộng thực:
300 + 40 + 2 = 342px

### Content
width = 660px
padding:
30px x 2 = 60px
border:
1px x 2 = 2px
Chiều rộng thực:
660 + 60 + 2 = 722px

## 2. Giải thích layout bị vỡ
Tổng chiều rộng:
342 + 722 = 1064px
Container chỉ có:
960px
Vì tổng lớn hơn container nên content bị đẩy xuống dòng mới.

## 3. Hai cách sửa
### Cách 1 — Dùng border-box
Thêm:
box-sizing: border-box;
Lúc này:
padding và border được tính bên trong width.
Tổng:
300 + 660 = 960px
Layout không bị vỡ.

### Cách 2 — Không dùng border-box
Phải tự trừ padding + border khỏi width.
Sidebar:
300 - 40 - 2
= 258px content width
Content:
660 - 60 - 2 = 598px content width
Hoặc sửa trực tiếp:
.sidebar {
    width: 258px;
}
.content {
    width: 598px;
}
Lúc đó tổng thực:
300 + 660 = 960px

## 4. Kết luận
border-box giúp:
- dễ tính toán
- tránh vỡ layout
- quản lý responsive tốt hơn