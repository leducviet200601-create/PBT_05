1. Thẻ meta viewport chuẩn
<meta name="viewport" content="width=device-width, initial-scale=1.0">
Giải thích từng phần
width=device-width
Đặt chiều rộng trang bằng đúng chiều rộng thiết bị
Ví dụ: iPhone, Android sẽ lấy đúng màn hình thật (không zoom ảo)
initial-scale=1.0
Mức zoom ban đầu = 100%
Không phóng to / thu nhỏ khi mở trang
2. Nếu KHÔNG có thẻ viewport

iPhone sẽ:

Hiển thị trang như website desktop thu nhỏ lại
Nội dung rất nhỏ
Người dùng phải zoom mới đọc được

 Hiện tượng:

Font chữ bé
Layout bị co lại
Trải nghiệm rất xấu trên mobile
 3. Mobile-First vs Desktop-First
 Mobile-First (khuyến khích dùng)

Viết CSS cho điện thoại trước, rồi mở rộng lên màn hình lớn

Ví dụ:
/* Mobile (mặc định) */
body {
  font-size: 14px;
  background: white;
}

/* Tablet trở lên */
@media (min-width: 768px) {
  body {
    font-size: 16px;
  }
}

/* Desktop */
@media (min-width: 1024px) {
  body {
    font-size: 18px;
  }
}
 Desktop-First

 Viết CSS cho máy tính trước, rồi thu nhỏ xuống mobile

Ví dụ:
/* Desktop (mặc định) */
body {
  font-size: 18px;
}

/* Tablet */
@media (max-width: 768px) {
  body {
    font-size: 16px;
  }
}

/* Mobile */
@media (max-width: 480px) {
  body {
    font-size: 14px;
  }
}
 4. So sánh nhanh
Mobile-First	Desktop-First
Viết từ nhỏ → lớn	Viết từ lớn → nhỏ
Dùng min-width	Dùng max-width
Ưu tiên mobile	Ưu tiên desktop
Hiện đại hơn	Cũ hơn
 5. Vì sao Mobile-First được khuyên dùng?
1. Người dùng mobile nhiều hơn desktop
Phần lớn traffic đến từ điện thoại
2. Hiệu năng tốt hơn
Load CSS nhẹ trước cho mobile
Sau đó mới mở rộng
 3. Dễ mở rộng giao diện
Thiết kế từ đơn giản → phức tạp
Ít lỗi responsive hơn
 4. Google ưu tiên mobile
SEO tốt hơn (Mobile-first indexing)

Câu A2 :
 1. Breakpoints chuẩn (phổ biến – Bootstrap)

Bootstrap dùng hệ breakpoints như sau:

 XS (Extra small)
 < 576px
 Thiết bị: điện thoại nhỏ
 Layout: 1 cột
 SM (Small)
 ≥ 576px
Điện thoại lớn / màn nhỏ
 Layout: 1–2 cột
 MD (Medium)
 ≥ 768px
 Tablet
 Layout: 2–3 cột
 LG (Large)
 ≥ 992px
 Laptop
 Layout: 3–4 cột
 XL (Extra large)
 ≥ 1200px
Desktop lớn
 Layout: 4–6 cột
 XXL (Extra extra large)
 ≥ 1400px
Màn hình rất lớn
 Layout: 6+ cột

 3. Ví dụ lưới sản phẩm (Product Grid)
 Mobile (XS–SM)

 1 cột

.product {
  width: 100%;
}
 Tablet (MD ≥768px)

 2–3 cột

@media (min-width: 768px) {
  .product {
    width: 50%;
  }
}
 Laptop (LG ≥992px)

 3–4 cột

@media (min-width: 992px) {
  .product {
    width: 33.33%;
  }
}
🖥 Desktop (XL ≥1200px)

4–6 cột

@media (min-width: 1200px) {
  .product {
    width: 25%;
  }
}

Câu A3 :
Chiều rộng màn hình	|.container width
375px (iPhone SE) |	100% (≈ 375px)
600px |	540px
800px| 720px
1000px|	960px
1400px|1140px

Câu A4 :
1. Variables (Biến trong SCSS)

SCSS cho phép dùng biến để lưu giá trị và tái sử dụng nhiều lần. Biến bắt đầu bằng ký hiệu $.

Ví dụ:

$primary-color: blue;

h1 {
  color: $primary-color;
}

button {
  background: $primary-color;
}
2. Nesting (CSS lồng nhau)

Nesting cho phép viết CSS theo dạng lồng giống cấu trúc HTML, giúp code dễ đọc hơn.

Ví dụ:

nav {
  background: black;

  ul {
    list-style: none;

    li {
      display: inline-block;

      a {
        color: white;
      }
    }
  }
}
3. Mixins (@mixin, @include)

Mixin dùng để gom nhóm các đoạn CSS và tái sử dụng nhiều lần.

Ví dụ:

@mixin center {
  display: flex;
  justify-content: center;
  align-items: center;
}

.box {
  @include center;
}
4. @extend (Inheritance)

@extend dùng để kế thừa style từ một class khác.

Ví dụ:

.button {
  padding: 10px;
  border: none;
}

.btn-primary {
  @extend .button;
  background: blue;
}
5. Vì sao trình duyệt không đọc được SCSS?
Vì trình duyệt chỉ hiểu CSS, HTML, JavaScript. SCSS là ngôn ngữ tiền xử lý nên không chạy trực tiếp được.

6. Cần làm gì để dùng SCSS?
Cần biên dịch SCSS sang CSS bằng trình biên dịch (compiler).
