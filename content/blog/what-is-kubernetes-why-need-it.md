+++
date = "2017-01-06T14:54:01+04:30"
draft = false
title = "کوبرنتیس چیست (Kubernetes) و چرا به آن نیاز دارید؟"

+++

کوبرنتیس چیست (Kubernetes) و چرا به آن نیاز دارید؟
===

[کوبرنتیس](http://kubernetes.io) پیاده سازی جدیدی از بیش از یک دهه تجربه گوگل در اجرای نرم افزارهای سمت سرور در مقیاس بسیار بالاست که به صورت متن باز (open source) در اختیار همه قرار گرفته است. این نرم افزار وظیفه اجرا و مدیریت کانتینرها روی سرورهای موجود در یک یا چند مرکز داده ها (data center) را به عهده دارد. برای درک بهتر این سیستم لازم است قدری با [مفاهیم اولیه کانتینرها مانند داکر](http://elastico.io/blog/docker-basic-concepts.html) آشنایی داشته باشید که میتوانید در همین سایت درباره آن بیشتر مطالعه کنید.

کوبرنتیس در واقع نسل سوم از این فنآوریست که از ابتدا به زبان گو (Go) پیاده سازی شده است. دو نسل قبلی آن برگ (Borg) نام داشته که پیاده سازی آن به زبان سی پلاس پلاس بوده است و گوگل همچنان از آن در محیط عملیاتی استفاده میکند. در کوبرنتیس یک یا چند کانتینر که به صورت مشترک یک برنامه کاربردی را تشکیل میدهند، به صورت واحدی جداگانه به نام پاد (pod) دسته بندی میشوند تا مدیریت و کشف (discovery) آنها آسانتر شود. مزیت اصلی این سیستم در این است که بدون نیاز به یک تیم بزرگ برای راه اندازی و نگهداری، میتوان آن را در مقیاس وسیع برای اجرای میلیاردها برنامه کاربردی به کار گرفت. از مزایای دیگر آن قابلیت اجرا بر روی بسترهای متفاوت است؛ از سرورهای یک مرکز داده های خصوصی گرفته تا سرویسهای ابری عمومی یا ترکیبی از هر دو.

به طور کلی هر شرکتی که یک یا چند سرویس نرم افزاری اجرا میکند به طور بالقوه در مرحله اول به کانتینرها و سپس به سیستمی مانند کوبرنتیس نیاز دارد. [دلیل اصلی نیاز به کانتینرها](http://elastico.io/blog/why-you-need-docker.html) امکان جداسازی (isolation) برنامه ها از یکدیگر در بهترین سطح ممکن طی فرآیند تولید، تست و در نهایت اجرا بر روی یک زیرساخت مشترک است. در مرحله بعد نیاز به کوبرنتیس پیدا میشود تا اجرای این کانتینرها بر روی دسته ای (cluster) از ماشینها را تسهیل کند. در واقع کوبرنتیس مانند سیستم عاملیست که بر روی تمام سرورهای شما به صورت یکپارچه اجرا میشود و به شما این امکان را میدهد که دیگر نگران هیچ ماشینی به طور خاص نباشید. اگر ظرفیت کافی در زیرساخت شما وجود داشته باشد، این سیستم به راحتی میتواند از دست دادن یک یا چند ماشین را برای شما به گونه ای مدیریت کند که کاربران هیچ تغییری در سرویسهای در حال اجرا بر روی این بستر احساس نکنند.

این سیستم امکاناتی مانند بررسی سلامت (health check) و تکثیر (replication) برنامه ها را به راحتی بر روی مجموعه سرورهای شما فراهم میکند. از دیگر قابلیتهای آن نیز داشتن ویژگیهای مناسب و سطح بالا، مانند کشف سرویسها (service discovery)، توزیع بار (load balancing) و مدیریت پیکربندی (configuration management) است که برای ساخت سیستمهایی با معماری مایکروسرویسی (micro-service architecture)  حیاتیست و برای تیمهای شما امکان تولید، تغییر و مقیاس پذیری (scaling) بخشهای مختلف هر سیستم را بر اساس شرایط مورد نیازتان فراهم میکند.

اگر چه بسیاری از نرم افزارها سعی میکنند این قابلیتها را در خود برنامه کاربردی پیاده کنند ولی تجربه نشان داده است که این کار با وجود صرف زمان و انرژی زیاد در اکثر موارد منجر به یک راه حل شکننده و غیر قابل نگهداری میشود که باید برای برنامه های بعدی از نو تکرار شود. کوبرنتیس با انتقال این دغدغه ها به لایه مناسب و آزاد کردن برنامه کاربردی از قید و بند آنها به شما کمک میکند که زمان را در جای مناسب و برای تولید ویژگیهای خاص برنامه کاربردی خودتان صرف کنید.

برای آشنایی بیشتر با این فنآوری میتوانید [ارایه ضبط شده کوبرنتیس](http://taakestan.com/index.php/2012-09-09-10-30-14/55-2016-08-30-kubernetes-docker-conf-tehran) در همایش داکر تهران  را بر روی سایت تاک مشاهده کنید. همچنین اگر فکر میکنید شرکت شما به چنین سیستمی نیاز دارد میتوانید به تیم الستیکو ایمیل بزنید (io.elastico AT gmail DOT com) تا در نیازسنجی و راه اندازی آن به شما کمک کنیم. 
