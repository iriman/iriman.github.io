---
layout: doc-rtl
title: افزونهٔ Opendata - داده از صفحه‌گسترده
permalink: /fa/josm/opendata-plugin/
lang: fa
category: josm
---

افزونهٔ Opendata - استفاده از دادهٔ ذخیره‌شده در صفحه‌گسترده
============


- TOC
{:toc}

این راهنما توضیح می‌دهد چگونه داده‌هایی را که در قالب صفحه‌گسترده هستند به OpenStreetMap اضافه کنیم. این داده‌ها مثلاً ممکن است از طریق بررسی میدانی با استفاده از ابزارهایی نظیر ODK و Kobo جمع‌آوری شده باشند.

**لطفاً توجه کنید، چنانچه داده‌ای که در نظر دارید به OpenStreetMap اضافه نمایید تحت نام «درون‌برد» (import) قرار می‌گیرد، بایستی [در ویکی OpenStreetMap صفحهٔ راهنمای درون‌برد](https://wiki.openstreetmap.org/wiki/Import/Guidelines) را مطالعه کنید. اگر کوچک‌ترین تردیدی دارید، بهتر است اول مشورت بگیرید!**


نصب افزونهٔ Opendata
--------------------------

اگر تا کنون این افزونه را نصب نکرده‌اید، با دنبال کردن راهنمای نصب افزونه‌ها در [افزونه‌های JOSM](/fa/josm/josm-plugins) آن را نصب کنید.

![Opendata][]

بعد از نصب، روی Opendata preferences کلیک کنید:
![Opendata preferences][]
تا به ماژول‌های اختصاصی‌تر دسترسی پیدا کنید:

![Opendata modules][]

این راهنما تنها عملکردهای اولیهٔ افزونه را شامل می‌شود و هیچ ماژولی بار نشده است.

آماده‌سازی صفحه‌گسترده 
-------------------------

صفحهٔ ویکی در <https://wiki.openstreetmap.org/wiki/JOSM/Plugins/OpenData> دربارهٔ قالب‌هایی که می‌توان استفاده کرد اطلاعات دقیق‌تری می‌دهد. برای اهداف خودمان فرض می‌کنیم که صفحه‌گسترده در قالب انحصاری **‎.xlsx** دانلود و به ما منتقل شده است. این قالب در افزونهٔ opendata بار نمی‌شود.

- صفحه‌گسترده را در برنامهٔ متن‌بازی مانند LibreOffice باز کنید. این نرم‌افزار برای اکثر سیستم‌عامل‌ها در <http://www.libreoffice.org/> در دسترس است.
- سپس آن را در قالب متن‌باز ذخیره کنید. صفحه‌گستردهٔ ما که **shops.xlsx** نام داشت به **shops.ods** تبدیل می‌شود.

گرچه اکنون امکان بارکردن صفحه‌گسترده در josm وجود دارد، بهتر است قبل از انجام این کار اصلاحاتی انجام دهیم تا فرآیند آسان‌تر شود.

### طول و عرض جغرافیایی

افزونهٔ OpenData توانایی خوبی برای استخراج طول و عرض جغرافیایی از صفحه‌گسترده‌ها دارد، اما اگر شک دارید بهتر است که سرستون‌ها را به قالبی ساده‌تر تغییر دهید:

![latitude longitude][]

می‌شود:

![latitude longitude corrected][]

### کلید و مقدار

#### تگ نام

هدف فعلی ما اصلاح صفحه‌گسترده است تا اطلاعات در قالب موردانتظار OpenStreetMap باشد. سرستون‌ها **کلید** خواهد بود و دادهٔ درون صفحه‌گسترده **مقدار** است. برای صفحه‌گستردهٔ سادهٔ ما، سرستون اول را از **name_of_the_shop** به **name** اصلاح کنید. با توجه به قالب کلید=مقدار، اولین سطر صفحه‌گستردهٔ ما می‌شود: 
**name=Tony's Supermarket**

اگر صفحه‌گستردهٔ شما بیش از یک نام دارد، مانند **نام محلی** یا **نام رسمی**، لطفاً صفحهٔ ویکی در <https://wiki.openstreetmap.org/wiki/Names> را مطالعه کنید. در این صفحه لیست کاملی از تگ‌های نام وجود دارد و بنابراین به‌روزرسانی موردنظر شما می‌تواند شامل همهٔ نام‌هایی که احتمالاً مورداستفاده یا جستجو قرار می‌گیرند بشود.

#### ستون‌های بدون سرستون

اگر سرستون یک ستون را حذف کنید، اما دادهٔ زیر آن را نگه دارید، این داده از دید JOSM پنهان می‌شود.

![opendata 1][]

#### ستون‌هایی حاوی داده از کلیدهای متفاوت

![opendata mixed][]

شخصی که نقشه‌برداری را طراحی می‌کند و شخصی که این نقشه‌برداری را انجام می‌دهد، اغلب از برچسب‌ها و مقدارهایی که در OpenStreetMap تکامل یافته‌اند آگاه نیستند. ستون **shop** در صفحه‌گستردهٔ من در واقع حاوی دادهٔ دو برچسب مختلف است. بنابراین صفحه‌گسترده نیاز به اصلاح دارد. سرستون **Type of shop** را برای دادهٔ زیر می‌توان به **shop** تغییر داد:  
  shop=supermarket  
  shop=convenience  
  shop=hairdresser  

اما **restaurant** و **fast_food** از کلید **amenity** هستند.

ستونی جدید با سرستون **amenity** باید درج شود و داده منتقل شود. درنتیجه صفحه‌گستردهٔ ما این‌گونه می‌شود:

![opendata shop amenity][]

#### زیرتگ‌ها

سرستون **Does_the_shop_have_toilet_faci** در طول فرآیند بررسی کوتاه شده است و در اصل این بوده **Does the shop have toilet facilities?‎**


گرچه برچسب جداگانه‌ای برای توالت‌ها وجود دارد و معمولاً به گرهی درون یک ساختمان اضافه می‌شود، اما این برچسب در واقع به توالت‌های عمومی اشاره دارد. اگر نقشه‌برداری را خودمان انجام می‌دادیم، دقیقاً می‌دانستیم منظور از پرسش و پاسخ چه چیزی است، اما اگر این اطلاعات به ما منتقل شده است، احتمالاً لازم است بررسی کنیم منظور چه بوده است. همچنین بسیار مفید است اگر بتوانید سوالات نقشه‌برداری را در تلفن بار کنید و یک نقشه‌برداری «ساختگی» انجام دهید تا طرح سوالات را متوجه شوید. قبل از اصلاح صفحه‌گسترده، خواندن دقیق صفحهٔ ویکی <https://wiki.openstreetmap.org/wiki/Tag:amenity%3Dtoilets> و مطالعهٔ نقشه‌برداریِ اصلی، کار لازمی است. به‌طور خاص، صفحهٔ ویکی شامل این اطلاعات است: 

- *لطفاً از toilet=yes (مفرد) استفاده نکنید. به‌طور کلی توالت‌های خصوصی را نقشه‌کشی نکنید. در بسیاری از ساختمان‌ها برای کارکنان و مالکان توالت‌هایی وجود دارد، اما رسم این‌ها در نقشه ممکن است باعث مناقشات بی‌اساس یا انتظارات غیرواقعی شود. برای جایی که انتظار می‌رود سرویس بهداشتی قابل‌استفاده داشته باشد (مثل ایستگاه قطار یا نقطهٔ شروع مسیر) اما سرویس بهداشتی عمومی ندارد از تگ toilets=no استفاده کنید.*

تمام تلاشم را کردم که از توصیه‌های ویکی پیروی کنم و در نتیجه صفحه‌گستردهٔ اصلاح‌شدهٔ من برای اطلاعات توالت‌ها این‌گونه شد:

![opendata toilets][]


من سرستون تعدادی از ستون‌ها را خالی کردم، بنابراین دادهٔ آن‌ها هنگام ویرایش در JOSM دیده نخواهد شد.

بارکردن صفحه‌گسترده در JOSM
---------------------------------

روی این دکمه کلیک کنید ![josm open][] سپس به پوشه‌ای که صفحه‌گسترده را ذخیره کرده‌اید بروید و آن را در JOSM باز کنید.

![opendata pop up][]  

پنجرک بالاپَری احتمالاً ظاهر خواهد شد که از شما می‌خواهد projection method مورداستفاده هنگام جمع‌آوری داده‌ها را تأیید کنید. افزونهٔ OpenData تلاش می‌کند تا «شیوهٔ تصویرکردن» به‌کاررفته را محاسبه کند و آن را به‌عنوان محتمل‌ترین گزینه ارائه دهد. جز در مواردی که نقشه‌بردار در تنظیمات این را تغییر داده باشد، کار معقولی است اگر شیوهٔ پیشنهادی را بپذیرید، اما هنگام ویرایش بررسی کنید آیا نقاط در مکان‌های موردانتظار قرار گرفته‌اند یا خیر.

![opendata spreadsheet loaded][]

تبریک! بخش سخت کار را پشت سر گذاشته‌اید و تقریباً آماده‌اید که OpenStreetMap را با دادهٔ جدید نقشه‌برداری خود روزآمد کنید.

استفاده از افزونهٔ ToDo
----------------------

در JOSM همهٔ موارد اضافه‌شده از طریق صفحه‌گستردهٔ خود را به یکی از این روش‌ها انتخاب کنید:

- زوم را کم کنید تا همه قابل‌مشاهده باشند. سپس درحالی‌که دکمهٔ چپ ماوس را پایین نگه داشته‌اید، ماوس را از بالا چپ به پایین راست بکشید، یا
- **Ctrl+F** را بزنید تا جستجو کنید - من **name** را جستجو کردم زیرا در هر 5 نقشه‌برداری‌ام وجود دارد.

مطمئن شوید همهٔ اقلام نقشه‌برداری‌شدهٔ خود را انتخاب کرده‌اید: در صفحه‌گستردهٔ من پنج قلم نقشه‌برداری‌شده وجود دارد و باید 5 شیء را انتخاب نموده باشم.

![5 selected][]

در پنجرک افزونهٔ ToDo، روی **Add** کلیک کنید.

![opendata todo add][]

و فهرست اقلامی که باید اضافه کنم در پنجرک ظاهر می‌شود.

![opendata todo loaded][]

بارکردن دادهٔ OpenStreetMap در لایهٔ مجزا
-------------------------------------------

روی بالاترین آیتم در لیست ToDo خود دوبارکلیک کنید، که درنتیجه آن را در پنجرهٔ ویرایش در مرکز قرار می‌دهد. سپس روی آیکون دانلود کلیک کنید ![download][]

هنگامی که پنجرهٔ دانلود ظاهر می‌شود، مطمئن شوید که تیک ![download new layer][] را بزنید (پایین سمت چپ در تصویر بعدی) تا دادهٔ OSM با دادهٔ صفحه‌گستردهٔ شما مخلوط نشود. توجه: در نسخه‌های جدیدتر JOSM این تیک جای خود را به دکمه‌ای با عنوان مشابه داده است، بنابراین در نسخه‌های جدیدتر مستقیماً روی خود دکمهٔ Download as new layer کلیک کنید.

![download dialog][]


مقایسهٔ داده بین لایه‌ها
------------------------------------

دادهٔ نگهداری‌شده در صفحه‌گستردهٔ خود را در برابر دادهٔ موجود در OpenStreetMap به‌دقت بررسی کنید. روش‌هایی برای کپی‌کردن برچسب‌ها یا بخش‌هایی از برچسب‌ها بین لایه‌ها وجود دارد (منوی **Tools** و **More Tools** را ببینید یا فصل‌های قبلی در Learnosm را بخوانید). در بسیاری از موارد دادهٔ جدید را با دادهٔ موجود ادغام خواهید کرد. به‌دقت داده را بررسی کنید، اگر لازم است تاریخچه و منبع را برای عارضه‌های مختلف بررسی کنید. همیشه ممکن است دادهٔ موجود در OpenStreetMap جدیدتر یا درست‌تر از دادهٔ صفحه‌گستردهٔ شما باشد.

وقتی اطلاعات یکی از سطرهای صفحه‌گسترده را آپلود کردید، دکمهٔ **Mark** در افزونهٔ ToDo را بزنید تا به مورد بعدی بروید. اگر مورد بعدی خارج از منطقه‌ای است که قبلاً دانلود کرده‌اید، باید دادهٔ بیشتری از OSM دانلود کنید.


[Opendata]: /images/josm/opendata-plugin.png
[Opendata preferences]: /images/josm/opendata-preferences.png
[Opendata modules]: /images/josm/opendata-modules.png
[latitude longitude]: /images/josm/opendata-latitude-longitude.png
[latitude longitude corrected]: /images/josm/opendata-latitude-longitude-corrected.png
[opendata 1]: /images/josm/opendata-1.png
[opendata mixed]: /images/josm/opendata-mixed.png
[opendata shop amenity]: /images/josm/opendata-shop-amenity.png
[opendata toilets]: /images/josm/opendata-toilets.png
[josm open]: /images/josm/josm_open-file.png
[opendata pop up]: /images/josm/opendata-wgs84-popup.png
[opendata spreadsheet loaded]: /images/josm/opendata-spreadsheet-loaded.png
[5 selected]: /images/josm/opendata-5-selected.png
[opendata todo add]: /images/josm/opendata-todo-add.png
[opendata todo loaded]: /images/josm/opendata-todo-loaded.png
[download]: /images/josm/josm-download-button.png
[download dialog]: /images/josm/josm_download-dialog.png
[download new layer]: /images/josm/download-as-new-layer.png
