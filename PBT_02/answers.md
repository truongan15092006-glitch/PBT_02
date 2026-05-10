### CÂU A1
**Nguồn tham chiếu:** File: 05_forms_input_types.md
Phần: HTML5 Input Types và Form Validation

1. type="text" Giao diện: Ô nhập văn bản đơn dòng
Validation: Không có kiểm tra tự động
Use case: Nhập tên sản phẩm, tên người dùng trong form đăng ký hoặc tìm kiếm
2. type="email" Giao diện: Ô nhập text
Validation: Kiểm tra có định dạng email (có ký tự @ và domain hợp lệ)
Use case: Email đăng ký tài khoản, email nhận đơn hàng
3. type="password" Giao diện: Ô nhập text nhưng ẩn ký tự (••••)
Validation: Không kiểm tra nội dung mặc định
Use case: Nhập mật khẩu khi đăng nhập hoặc đăng ký
4. type="number" Giao diện: Ô nhập số, có nút tăng/giảm
Validation: Chỉ cho phép nhập số
Use case: Nhập số lượng sản phẩm trong giỏ hàng
5. type="tel" Giao diện: Ô nhập số điện thoại
Validation: Không bắt buộc format, nhưng hỗ trợ nhập số
Use case: Nhập số điện thoại giao hàng
6. type="date" Giao diện: Bộ chọn ngày (calendar picker)
Validation: Chỉ cho phép chọn ngày hợp lệ
Use case: Chọn ngày giao hàng hoặc ngày sinh
7. type="checkbox" Giao diện: Ô tick chọn
Validation: Có thể chọn hoặc không
Use case: Đồng ý điều khoản mua hàng, chọn nhiều sản phẩm phụ
8. type="radio" Giao diện: Nút chọn tròn, chỉ chọn 1 trong nhiều lựa chọn
Validation: Bắt buộc chọn một giá trị trong nhóm
Use case: Chọn phương thức thanh toán (COD, thẻ, ví điện tử)
9. type="file" Giao diện: Nút chọn file từ máy tính
Validation: Có thể giới hạn loại file (image/*, pdf…)
Use case: Upload ảnh sản phẩm hoặc ảnh chứng minh giao hàng
10. type="range" Giao diện: Thanh trượt
Validation: Giá trị nằm trong khoảng min–max
Use case: Lọc giá sản phẩm (ví dụ 0 → 10.000.000đ)
**CÂU A2
**Nguồn tham chiếu:** File: 07_form_validation.md
Phần: HTML5 Form Validation (required, type, min/max, pattern, minlength)

Trường hợp 1
<input type="text" required value="">

Dự đoán khi Submit:
Form sẽ không submit được.
Giải thích:
Thuộc tính required bắt buộc phải có dữ liệu. Vì user để trống (value="") nên trình duyệt sẽ chặn submit và hiển thị thông báo yêu cầu nhập dữ liệu.

Trường hợp 2
<input type="email" value="abc">

Dự đoán khi Submit:
Form không submit được.
Giải thích:
type="email" yêu cầu đúng định dạng email (phải có @ và domain). Giá trị abc không hợp lệ nên browser báo lỗi validation.

Trường hợp 3
<input type="number" min="1" max="10" value="15">

Dự đoán khi Submit:
Form không submit được.
Giải thích:
Giá trị 15 vượt quá giới hạn max="10". Browser kiểm tra range và chặn submit vì không nằm trong khoảng hợp lệ.

Trường hợp 4
<input type="text" pattern="[0-9]{10}" value="abc123">

Dự đoán khi Submit:
Form không submit được.
Giải thích:
pattern="[0-9]{10}" yêu cầu đúng 10 chữ số. Giá trị abc123 chứa chữ cái và không đủ 10 số nên không khớp regex → bị chặn submit.

Trường hợp 5
<input type="password" minlength="8" value="123">

Dự đoán khi Submit:
Form không submit được.
Giải thích:
minlength="8" yêu cầu mật khẩu ít nhất 8 ký tự. Giá trị chỉ có 3 ký tự nên không đạt điều kiện → browser hiển thị lỗi.

**CÂU A3
**Nguồn tham chiếu:** File: 07_form_validation.md
Phần: Accessibility (label, fieldset, aria-label)

1. Tại sao <label for="email"> quan trọng cho screen reader?

<label for="email"> dùng để liên kết nhãn với ô input thông qua thuộc tính id.
Đối với người dùng screen reader:
Khi focus vào input, hệ thống sẽ đọc nội dung của label
Giúp người dùng biết rõ ý nghĩa của trường nhập liệu (ví dụ: email, mật khẩu)
Tăng khả năng truy cập và dễ sử dụng cho người khiếm thị

Ví dụ:
<label for="email">Email</label>
<input id="email" type="email">

Nếu không có label, screen reader chỉ đọc “input field” mà không xác định được nội dung cần nhập.

2. Khi nào dùng <fieldset> + <legend>? Cho ví dụ
<fieldset> dùng để nhóm các trường input có liên quan với nhau trong một form.
<legend> dùng để đặt tiêu đề cho nhóm đó.
Dùng khi form có nhiều nhóm thông tin rõ ràng như thông tin cá nhân, thông tin giao hàng, thông tin thanh toán.

Ví dụ:
<fieldset>
    <legend>Thông tin giao hàng</legend>

    <label for="name">Tên</label>
    <input id="name" type="text">

    <label for="address">Địa chỉ</label>
    <input id="address" type="text">
</fieldset>

3. aria-label dùng khi nào? Tại sao không nên dùng khi đã có label?
aria-label dùng để cung cấp nhãn cho các phần tử không có nội dung hiển thị trên giao diện.
Ví dụ sử dụng đúng:
<button aria-label="Tìm kiếm">🔍</button>

Không nên dùng aria-label khi đã có <label> vì:
<label> đã cung cấp đầy đủ thông tin cho screen reader
aria-label sẽ ghi đè nội dung của label, gây trùng hoặc sai nghĩa
Làm giảm tính nhất quán và khó bảo trì code
Có thể gây nhầm lẫn cho công nghệ hỗ trợ

Ví dụ không nên dùng:
<label for="email">Email</label>
<input id="email" type="email" aria-label="User email">
 
**CÂU A4
**Nguồn tham chiếu:** File: 05_media_html.md
Phần: <img>, <video>, accessibility và performance optimization

1. loading="lazy" trên thẻ <img> là gì? Nó cải thiện gì? Khi nào không nên dùng?
loading="lazy" giúp trì hoãn việc tải hình ảnh cho đến khi người dùng cuộn đến gần vị trí của ảnh trên trang.

Lợi ích:
Giảm thời gian tải trang ban đầu (initial load)
Giảm băng thông sử dụng
Tăng hiệu suất website (performance)
Cải thiện trải nghiệm người dùng, đặc biệt trên mobile

Ví dụ:
<img src="product.jpg" loading="lazy" alt="Sản phẩm">

Khi KHÔNG nên dùng:
Ảnh nằm ở phần đầu trang (above the fold)
Logo hoặc ảnh quan trọng cần hiển thị ngay
Ảnh nền quan trọng cho trải nghiệm đầu tiên của người dùng
2. Vì sao nên cung cấp nhiều <source> trong <video>?
Trình duyệt khác nhau hỗ trợ các định dạng video khác nhau. Việc cung cấp nhiều <source> giúp đảm bảo video hoạt động trên nhiều trình duyệt và thiết bị.

Lợi ích:
Tăng khả năng tương thích (cross-browser compatibility)
Tránh lỗi không phát được video
Tối ưu trải nghiệm người dùng

Ví dụ:
<video controls>
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    <source src="video.ogg" type="video/ogg">
</video>

3. Các định dạng video web phổ biến
MP4 (H.264)
WebM (VP8/VP9)
Ogg (Theora)

4. Thuộc tính alt dùng để làm gì?

alt (alternative text) dùng để:
Mô tả nội dung hình ảnh khi ảnh không tải được
Hỗ trợ screen reader cho người khiếm thị
Tăng SEO cho website

5. Viết alt tốt cho từng trường hợp
a. Ảnh sản phẩm iPhone 16
<img src="iphone16.jpg" alt="iPhone 16 màu đen hiển thị mặt trước">
b. Ảnh trang trí (decorative)
<img src="decor.jpg" alt="">

Hoặc:
<img src="decor.jpg" alt="" aria-hidden="true">
→ Vì ảnh chỉ mang tính trang trí, không cần mô tả

c. Ảnh biểu đồ doanh thu Q1/2026
<img src="chart-q1-2026.jpg" alt="Biểu đồ doanh thu quý 1 năm 2026 tăng trưởng 15% so với quý trước">

** CÂU A5
**Nguồn tham chiếu:**
File: 05_media_html.md
Phần: Image semantics (<img>, <figure>, <figcaption>)

1. Khi nào dùng Cách 1 (<img> đơn lẻ)?
Cách 1 dùng khi hình ảnh chỉ mang tính minh họa đơn giản, không cần thêm ngữ cảnh hoặc mô tả phụ đi kèm.

Đặc điểm:
Chỉ có một ảnh
Không cần caption (chú thích)
Nội dung ảnh độc lập và đơn giản

Ví dụ thực tế:
Ảnh icon trong UI (ví dụ icon giỏ hàng)
Ảnh avatar người dùng trong comment
Ảnh minh họa nhỏ trong bài viết không cần chú thích

Ví dụ code:
<img src="avatar.jpg" alt="Ảnh đại diện người dùng">

2. Khi nào dùng Cách 2 (<figure> + <figcaption>)?

Cách 2 dùng khi hình ảnh có kèm theo chú thích hoặc có ý nghĩa nội dung đầy đủ cần được giải thích.

Đặc điểm:
Ảnh + nội dung mô tả đi kèm
Có thể đứng độc lập như một “khối nội dung”
Tăng semantic và accessibility

Ví dụ thực tế:
Ảnh sản phẩm trong trang thương mại điện tử (có tên + giá)
Biểu đồ thống kê dữ liệu trong báo cáo
Ảnh trong bài blog có chú thích giải thích nội dung

Ví dụ code:
<figure>
    <img src="product.jpg" alt="iPhone 16 Pro Max 256GB Titan">
    <figcaption>iPhone 16 Pro Max — 25.990.000đ</figcaption>
</figure>

3. So sánh nhanh
<img>: chỉ hiển thị ảnh, không có ngữ cảnh bổ sung
<figure>: nhóm ảnh + chú thích, mang tính nội dung hoàn chỉnh

**PHẦN C
**CÂU C1
**Nguồn tham chiếu:**
File: 07_form_validation.md
Phần: Form accessibility, validation, best practices

Lỗi và cách sửa
Lỗi 1: Dòng 2 — Input "Tên" không có <label> và không có id/name
Sửa: cần thêm label liên kết với input để hỗ trợ accessibility và screen reader
<label for="name">Tên:</label>
<input type="text" id="name" name="name" required>

Lỗi 2: Dòng 4 — input email không có id/name và không có required
Sửa: thêm label + validation cơ bản
<label for="email">Email:</label>
<input type="email" id="email" name="email" placeholder="Email của bạn" required>

Lỗi 3: Dòng 6 — password không có name/id và thiếu label
Sửa:
<label for="password">Mật khẩu:</label>
<input type="password" id="password" name="password" placeholder="Mật khẩu" required>

Lỗi 4: Dòng 7 — confirm password không có label và không có id/name
Sửa:
<label for="confirm_password">Nhập lại mật khẩu:</label>
<input type="password" id="confirm_password" name="confirm_password" required>

Lỗi 5: Dòng 9 — Phone dùng type="text" và set value cố định (sai best practice)
Sửa: dùng type="tel" và không set value mặc định
<label for="phone">Phone:</label>
<input type="tel" id="phone" name="phone" placeholder="0901234567" required>

Lỗi 6: Dòng 11–14 — <select> không có label và không có name
Sửa:
<label for="city">Thành phố:</label>
<select id="city" name="city">
    <option>Hà Nội</option>
    <option>TP.HCM</option>
</select>

Lỗi 7: Dòng 16–18 — checkbox không có input và không có liên kết label
Sửa:
<input type="checkbox" id="agree" name="agree" required>
<label for="agree">Tôi đồng ý điều khoản</label>

Lỗi 8: Dòng 20 — submit không nằm trong button semantic (best practice)
Sửa:
<button type="submit">Gửi</button>
Form sau khi sửa hoàn chỉnh
<form>

    <label for="name">Tên:</label>
    <input type="text" id="name" name="name" required>

    <label for="email">Email:</label>
    <input type="email" id="email" name="email" placeholder="Email của bạn" required>

    <label for="password">Mật khẩu:</label>
    <input type="password" id="password" name="password" placeholder="Mật khẩu" required>

    <label for="confirm_password">Nhập lại mật khẩu:</label>
    <input type="password" id="confirm_password" name="confirm_password" required>

    <label for="phone">Phone:</label>
    <input type="tel" id="phone" name="phone" placeholder="0901234567" required>

    <label for="city">Thành phố:</label>
    <select id="city" name="city">
        <option>Hà Nội</option>
        <option>TP.HCM</option>
    </select>

    <input type="checkbox" id="agree" name="agree" required>
    <label for="agree">Tôi đồng ý điều khoản</label>

    <button type="submit">Gửi</button>
</form>

** CÂU C2
**Nguồn tham chiếu:**
File: 07_form_validation.md
Phần: Validation patterns, client-side vs server-side validation, security basics

1. Regex pattern
CMND/CCCD (12 chữ số):

^[0-9]{12}$
Giải thích:

^ bắt đầu chuỗi
[0-9]{12} đúng 12 chữ số
$ kết thúc chuỗi

Số tài khoản (10–15 chữ số):

^[0-9]{10,15}$

Giải thích:
Cho phép số từ 10 đến 15 chữ số
Không cho phép ký tự khác ngoài số
2. HTML5 validation có đủ an toàn cho ngân hàng không?

Không đủ an toàn.
Lý do:
HTML5 validation chỉ chạy ở phía trình duyệt (client-side)
Người dùng có thể bypass bằng DevTools hoặc gửi request trực tiếp (Postman, curl)
Không đảm bảo dữ liệu an toàn trước tấn công hoặc giả mạo
→ Vì vậy, HTML5 chỉ dùng để hỗ trợ UX, không dùng để bảo mật

3. 3 loại validation HTML5 KHÔNG thể làm được (cần JavaScript)
Kiểm tra logic phức tạp giữa nhiều field
Ví dụ: password và confirm password phải giống nhau
Kiểm tra dữ liệu từ server (real-time validation)
Ví dụ: số tài khoản đã tồn tại hay chưa
Kiểm tra điều kiện bảo mật nâng cao
Ví dụ: password không nằm trong danh sách mật khẩu yếu (common password list)

4. 2 rủi ro nếu chỉ validate frontend
Bypass validation dễ dàng
Hacker có thể:
Tắt JavaScript
Sửa HTML trong DevTools
Gửi request trực tiếp → nhập dữ liệu sai vẫn lọt qua
Dữ liệu sai hoặc độc hại vào hệ thống backend
Có thể gây:
SQL Injection
Lỗi hệ thống
Sai lệch dữ liệu tài khoản ngân hàng
