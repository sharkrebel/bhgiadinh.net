Website WordPress vẫn ở nguyên hosting (aaPanel, shared hosting), chỉ muốn đổi tên miền từ domainA.com → domainB.com, không phải chuyển hosting.

Dưới đây là cách làm đúng & an toàn nhất 👇

✅ TỔNG QUAN CÁC BƯỚC

Trỏ domainB.com về hosting hiện tại

Add domainB.com vào aaPanel

Đổi URL WordPress từ domainA → domainB

Redirect 301 domainA → domainB (rất quan trọng cho SEO)

Kiểm tra SSL & fix lỗi

🟢 BƯỚC 1: Trỏ domainB.com về hosting

Làm giống domainA trước đây:

Cách phổ biến

Trỏ A record:

@    → IP_HOSTING
www  → IP_HOSTING


⏱ Đợi 5–30 phút (có thể 24h)

🟢 BƯỚC 2: Thêm domainB.com vào aaPanel

Vào aaPanel → Website → Add site

Domain: domainB.com

Chọn thư mục giống domainA

/www/wwwroot/domainA.com


📌 Rất quan trọng: KHÔNG tạo thư mục mới

🟢 BƯỚC 3: Đổi URL WordPress
Cách an toàn nhất (không vào admin)

Mở file:

/wp-config.php


Thêm hoặc sửa:

define('WP_HOME','https://domainB.com');
define('WP_SITEURL','https://domainB.com');


👉 Lúc này web sẽ chạy bằng domainB.com

🟢 BƯỚC 4: Redirect 301 domainA → domainB (BẮT BUỘC)

Giữ SEO + tránh lỗi trùng nội dung

Cách 1: Redirect bằng aaPanel (khuyên dùng)

aaPanel → Website → domainA.com

Redirect

Type: 301

From: domainA.com

To: https://domainB.com

Cách 2: Redirect bằng .htaccess

Nếu không có menu Redirect:

RewriteEngine On
RewriteCond %{HTTP_HOST} ^(www\.)?domainA\.com$ [NC]
RewriteRule ^(.*)$ https://domainB.com/$1 [L,R=301]

🟢 BƯỚC 5: SSL cho domainB.com

aaPanel → Website → domainB.com

SSL → Let's Encrypt

Tick:

domainB.com

www.domainB.com

⚠️ CÁC VIỆC PHẢI KIỂM TRA
1️⃣ Link cũ trong database

Cài plugin Better Search Replace

Replace:

http://domainA.com → https://domainB.com


(Chạy chế độ dry-run trước)

2️⃣ Google Search Console

Add domainB.com

Dùng Change of Address

🎯 TÓM TẮT NHANH
Việc	Bắt buộc
Add domainB vào aaPanel	✅
Dùng chung thư mục	✅
WP_HOME + WP_SITEURL	✅
Redirect 301	✅
SSL	✅