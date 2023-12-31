## پروژه بوت کمپ ترب - چت‌بات
### مقدمه
برای کسب‌ و کارها مبتنی بر SaaS یکی از مسائل اصلی پشتیبانی کاربرهاست. توسعه چت‌بات‌ از دو جهت برای این کسب و کارها اهمیت دارد:
- بهبود تجربه کاربر (چون کاربر بلافاصله پاسخ سوال یا مشکلش رو میگیره و دیگه نیاز نیست که صبر کنه.)
- کاهش هزینه عملیاتی (اپراتورهای کمتری برای پاسخ و حل مشکلات کاربران نیاز هست.)

استفاده از مدل‌های زبانی بزرگ یکی از روش‌های توسعه چت بات است.
این روش به خصوص در یکسال گذشته با معرفی مدل‌های زبانی GPT-3.5 و GPT-4 توسط OpenAI و ارائه API برای آن‌ها بیش از پیش مورد توجه قرار گرفته است. روش توسعه چت‌بات با استفاده از مدل‌زبانی اصطلاحا به
[Retrival augmented generation](https://www.promptingguide.ai/techniques/rag)
یا به اختصار RAG شناخته میشود. 

در این پروژه قصد داریم یک سایت توسعه دهیم که در آن کاربرها میتوانند برای دیتای مورد نظر خودشون chatBot بسازن.
به این ترتیب که ابتدا دیتای مورد نظرشون رو در نرم‌افزار وارد میکنن (knowledge base) و بعد میتونن چت باتی بسازن که با توجه به دیتای وارد شده در مرحله قبل به سوالات کاربرها جواب بده.

### نیازمندی‌های کلی پروژه
در ادامه کلیت موجودیت‌های موجود در پروژه و نیازمندی‌های هر موجودیت توضیح داده شده است:

#### کاربر:
- باید بتواند در سایت ثبت نام کند. (username-email-password)
- باید بتواند در سایت لاگین کند.
- بدون لاگین نباید به هیچ قسمتی از سایت دسترسی داشته باشد.
- سه نوع کاربر داریم:
  - کاربر عادی:‌ میتونه یک چت بات انتخاب کنه و باهاش چت کنه.
  - کاربر چت بات ساز: میتونه چت بات بسازه یا مشخصات و knowledge base چت بات‌های قبلی که خودش ساخته رو تغییر بده.
  - کاربر ادمین: میتونه از طریق torob-admin هر چیزی رو که خواست تغییر بده.
- کاربر باید بتونه تاریخچه گفتگوهاش رو ببینه و اگر خواست بتونه یک گفتگو رو ادامه بده.
- کاربر باید بتونه یک چت‌بات انتخاب کنه و باهاش یک گفتگوی جدید آغاز کنه.
- کاربر باید بتونه در متن پیام‌های گفتگوهای گذشته‌اش جستجو کنه.

#### چت بات:
- کاربرهای چت‌بات ساز میتونن با ثبت نام-عکس و توضیحات چت بات بسازن.
- پرامپت chatbot . هر چت بات یک custom prompt داره که با اون به chatGPT ریکوست میزنه.
[مثلا برای GPT4 که داخل bing سرچ میکنه پرامت اینه.](https://bard.google.com/chat/7b460eef98219ea7)
- فقط کاربری که یک چتبات رو ساخته میتونه مشخصاتش رو تغییر بده.
- میتونن چت‌بات‌هایی که خودشون ساختن رو فعال/غیرفعال کنن.

#### محتوای چت بات:
- هر چت‌بات یک سری محتوا داره که توسط کاربری که ساختنش میتونه ثبت یا ویرایش بشه.
- هر محتوا حداکثر ۸۰۰ کارکتر میتونه طول داشته باشه.

#### گفتگو:
- همه کاربرها میتونن یک چت بات رو انتخاب کنن و باهاش یک گفتگو جدید رو آغاز کنن.

#### پیام:
- هر کاربر بعد از انتخاب گفتگو میتونه پیام ارسال کنه و در ادامه chatbot بهش جواب میده و این فرآیند در هر گفتگو میتونه تا بینهایت ادامه پیدا کنه.

#### نظر بر روی پیام
- کاربر باید بتونه به پیام‌های چت بات like و dislike نشون بده و اگر کاربر dislike نشون داد باید بات یک پیام جدید به جای پیام قبلی بسازه و برای کاربر ارسال کنه.



### فاز اول:‌ تنظیمات اولیه و راه‌اندازی سایت. (تاریخ تحویل شنبه ۲۰ آبان)
- ساخت پروژه جنگو (۳۰ دقیقه)
- ساخت داکرفایل برای پروژه. (۳۰ دقیقه)
- دیپلوی پروژه با استفاده از همروش و ساخت پایپلاین CI/CD دارای سه مرحله بیلد/تست/دیپلوی (۱ ساعت)
- ساخت مدل‌های پروژه: (۱ ساعت)
  - کاربر
  - چت بات
  - محتوای چت بات
  - گفتگو
  - پیام
  - نظر کاربر بر روی پیام
- ساخت ادمین جنگو برای مشاهده و تغییر داده‌ها توسط کاربر ادمین. (۱ ساعت)
- پیاده سازی قابلیت ثبت نام و و ورود به سایت (۲ ساعت)
- نکته: در نهایت دیتابیس مورد استفاده در پروژه باید پستگرس باشه ولی چون پستگرس رو جلسه بعدی آموزش میدیم در این مرحله میتونید از دیتابیس sqlite برای دیپلوی کردن استفاده کنید ولی در فاز بعدی باید تغییر بدید.

### فاز دوم:‌ ساخت چت‌بات بدون داکیومنت‌های مشابه (تاریخ تحویل شنبه ۲۷ آبان)
- ساخت یک اپلیکیشن جدید برای دیتابیس پستگرس در دارکوب و اتصال به دیتابیس پستگرس (یک ساعت)
- نمایش لیست گفتگوهای گذشته به کاربر لاگین کرده. (با pagination) (یک ساعت)
- نمایش لیست چت‌بات‌های موجود به کاربر لاگین کرده. (یک ساعت)
- انتخاب چت بات و شروع یک گفتگوی جدید. (یک ساعت)
- امکان ارسال پیام توسط کاربر. (یک ساعت)
- اتصال به api مربوط به openAI ارسال پیام کاربر و prompt اولیه چت بات و نمایش پاسخ به کاربر. (یک ساعت)
- کاربر بتونه به پیام‌های ارسالی توسط چت بات امتیاز بده. (like-dislike) و اون‌هایی که dislike داده دوباره generate بشه. (یک ساعت)
- ساخته شدن title گفتگو به صورت خودکار با توجه به محتوای اولین پیام ارسالی توسط api مربوط به openAI (اولین پیام ارسالی رو بگیم خلاصه کنه و همون رو بزاریم عنوان)
- ادمین بتونه به کاربر‌‌هایی که میخواد دسترسی چت‌بات بده (از طریق جنگو ادمین.) 
- کاربری که دسترسی چت‌بات ساز داره بتونه لیست چت‌بات‌هایی که ساخته رو ببینه. (یک ساعت) (میشه این قابلیت از طریق جنگو ادمین پیاده‌سازی بشه.)
  - بتونه چت‌بات جدید بسازه. یا چت‌بات‌های قبلیش رو ویرایش کنه. (یک ساعت)
  - بتونه محتوا به چت بات اضافه یا کم کنه. (یک ساعت)
  - بتونه چت‌بات‌های قبلی رو فعال/غیرفعال کنه.
- بتونه امتیاز چت بات رو ببینه (تعداد لایک‌ها و دیسلایک‌هایی که به چت بات توسط کاربرها داده شده.) (میشه این قابلیت از طریق جنگو ادمین پیاده‌سازی بشه.)

### فاز سوم:‌ پیاده‌سازی قابلیت پیدا کردن داکیومنت‌های مشابه و جستجو در گفتگوهای گذشته (تاریخ تحویل ۵ آذر)
- محاسبه [embeding](https://simonwillison.net/2023/Oct/23/embeddings/) با استفاده از api مربوط به openAI و ذخیره در کنار محتوا. (۲ ساعت)
- تبدیل پیام کاربر به embeding و پیدا کردن محتواهای مشابه با استفاده از similarity مناسب. (۲ ساعت)
- ساخت دیتای تست و اندازه‌گیری دقت روش پیدا کردن similarity بر روی دیتای تست. (۱ ساعت)
- استفاده از الگوریتم similarity استفاده شده در مرحله قبلی برای پیدا کردن داکیومنت‌های مشابه و تغییر prompt وارسال پاسخ به کاربر به همراه مرحله retrival . (۲ ساعت)
- پیاده‌سازی قابلیت full text search برای گفتگو‌های قبلی کاربر. (۲ ساعت)
- نوشتن یک داکیومنت و توضیح کارهای انجام شده. (۳ ساعت)
- (اختیاری)‌ یکی از مشکلات جدی مدل‌های زبانی hallucination هست یعنی وقتی یک چیزی رو بلد نیستن شروع میکنن به چرت و پرت جواب دادن سعی کنید کمی در این مورد تحقیق کنید و کاری کنید که این hallucination رو در پاسخ‌ها کاهش بدید.
- (اختیاری) کار ویژه بر روی سیستم پیدا کردن محتواهای مشابه با کوئری کاربر.

### نکات
- برای ساخت و توسعه چت بات یک کتابخونه‌ای در پایتون توسعه داده شده به اسم
[langChain](https://python.langchain.com/)
در این پروژه نمیخوایم از این کتابخونه استفاده مستقیم بکنیم و میخوایم از اول یک چیزی خودمون بنویسیم ولی برای ایده گرفتن میتونید کد‌هاش رو نگاه کنید.
- برای دسترسی به api ارائه شده توسط openAi میتوانید از
[کتابخانه این شرکت](https://github.com/openai/openai-python/tree/main)
استفاده کنید. فقط مقدار base_url رو برابر https://openai.torob.ir قرار بدید. مقدار api_key هر فرد توسط منتورش در هفته آینده ارائه میشه. فقط میتونید از مدل‌های GPT-3.5 Turbo (برای generation) و ada v2 (برای embding)
- برای اینکه کارتون راحت‌تر بشه یک سری template برای صفحات آماده شده که نیاز نباشه htmlها رو از اول بزنید و سرعت کار بالاتر بره که ریپو پروژه در دسترستون قرار داده شده.
- برای اینکه بتونید چت باتتون رو تست کنیم یک دیتاست تستی تهیه شده که اون هم در قالب یک فایل csv در داخل پروژه قرار داره.

