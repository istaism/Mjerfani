# نسخه بازطراحی‌شده وب‌سایت محمدجواد عرفانی

این پروژه مستقیماً از قالب و محتوای فایل اصلی شما ساخته شده است. نام، حوزه‌های فعالیت، پنل دانش گوگل، اینستاگرام، یوتیوب، اسپاتیفای، تلگرام و شماره تماس همان اطلاعات نسخه اولیه هستند؛ طراحی و زیرساخت SEO از نو ارتقا یافته‌اند.

## استقرار سریع روی Cloudflare Pages

1. وارد Cloudflare Dashboard شوید.
2. به بخش Workers & Pages بروید و یک پروژه Pages بسازید.
3. پوشه پروژه را با Direct Upload بارگذاری کنید یا آن را به GitHub وصل کنید.
4. این سایت build ندارد؛ خروجی همان ریشه پوشه است.
5. در بخش Custom domains دامنه mjerfani.nx.kg را اضافه کنید.
6. رکورد DNS قدیمی یا متضاد این hostname را حذف کنید تا Pages رکورد صحیح را بسازد.

## خطای فعلی دامنه

در زمان بررسی، سایت زنده پاسخ 502 Bad Gateway با پیام Certificate verify failed: hostname mismatch می‌داد.

تا رفع این خطا، گوگل و کاربران به HTML سایت دسترسی ندارند.

- اگر از Cloudflare Tunnel استفاده می‌کنید و Origin شما HTTP است، سرویس را به‌شکل http://localhost:PORT تعریف کنید.
- اگر Origin شما HTTPS است، مقدار Origin Server Name باید دقیقاً با نام داخل SAN/CN گواهی مبدأ یکی باشد.
- اگر رکورد نارنجی Cloudflare به هاست وصل است، گواهی معتبر شامل mjerfani.nx.kg را روی مبدأ نصب و سپس SSL/TLS را روی Full (strict) قرار دهید.
- اگر به Cloudflare Pages مهاجرت می‌کنید، دامنه را از بخش Custom domains همان پروژه اضافه کنید؛ این مسیر مشکل گواهی مبدأ قبلی را حذف می‌کند.

استفاده دائمی از No TLS Verify یا پایین‌آوردن امنیت SSL راه‌حل نهایی نیست.

## بعد از استقرار

این چهار مسیر را تست کنید:

- https://mjerfani.nx.kg/ باید 200 باشد.
- https://mjerfani.nx.kg/robots.txt باید 200 باشد.
- https://mjerfani.nx.kg/sitemap.xml باید 200 باشد.
- یک نشانی ناموجود باید 404 باشد.

سپس:

1. دامنه را در Google Search Console تأیید کنید.
2. https://mjerfani.nx.kg/sitemap.xml را در بخش Sitemaps ثبت کنید.
3. در URL Inspection ابتدا Test Live URL و سپس Request Indexing را بزنید.
4. صفحات واقعی و معتبر خود را به این دامنه لینک کنید.

## فایل‌ها

- index.html: سایت کامل، CSS و JavaScript در یک فایل
- assets: فونت محلی، favicon و تصویر شبکه اجتماعی
- robots.txt: اجازه خزش
- sitemap.xml: نقشه سایت
- _headers: هدرهای Cloudflare Pages
- _redirects: انتقال index.html به ریشه
- 404.html: صفحه 404 با noindex

هیچ کدی ایندکس فوری را تضمین نمی‌کند؛ اما پس از رفع 502، این نسخه از نظر فنی قابل خزیدن و ایندکس است.
