## مقدمه‌ای بر پردازش زبان طبیعی

در این بخش به بررسی پردازش زبان طبیعی می‌پردازیم. اما در ابتدا باید ببینیم که زبان طبیعی چیست. زبان‌هایی که می‌شناسیم عبارتند از زبان‌های توصیفی، زبان‌های برنامه‌نویسی و زبان‌های طبیعی. به عنوان نمونه می‌توان روابط ریاضی یا فرمول‌های شیمی را به عنوان زبان توصیفی در نظر گرفت. همچنین زبان‌هایی نظیر جاوا، پایتون و ... زبان‌های برنامه‌نویسی هستند. اما زبان طبیعی زبانی است که انسان‌ها از آن برای به تحریر درآوردن گفتار و آواها استفاده می‌کنند. نظیر زبان‌های انگلیسی، فارسی و آلمانی.  زبان طبیعی از حروف الفبا، از یک دیکشنری از کلمات و همچنین از جملات تشکیل شده است. زبان طبیعی به طور کلی در تکنولوژی‌های گفتاری و متنی مورد استفاده قرار می‌گیرد. 

برای استفاده از زبان طبیعی در تکنولوژی‌های گوناگون باید راهی پیدا کنیم تا زبان طبیعی را توسط ماشین پردازش کنیم. این نیاز باعث به وجود آمدن حوزه پردازش زبان طبیعی یا Natural Language Processing (NLP) شده است.

از جمله کاربردهای NLP در زمینه متن عبارتند از:

1. تشخیص درست نوشتار کلمات و گرامر (Spell and Grammar Checking)
2.  دسته‌بندی متون در چندین مقوله (Text Categorization)
3. بازیابی اطلاعات (Information Retrieval)
4. خلاصه‌سازی متن (Summarization)
5. استخراج اطلاعات (Information Extraction)
6. سیستم‌های پرسش و پاسخ (Question Answering)
7. ترجمه ماشینی (Machine Translation)
8. آنالیز معنایی جملات (Sentiment Analysis)
9. تشخیص کاراکترهای اوپیتکی از تصاویر (Optical Character Recognition)
10. پیش‌بینی کلمات در یک جمله ناقص (Word Prediction)

و در حوزه‌های مرتبط با گفتار کاربردهای NLP عبارتند از:

1. تشخیص گفتار یا تبدیل گفتار به متن (Speech Recognition)
2. سنتز گفتار یا تبدیل متن به گفتار (Speech Synthesis)
3. سیستم‌های دیالوگ گفتاری (Spoken Dialog Systems)

از جمله مواردی که در این بخش آورده شده است، شاید ترجمه ماشین آشناترین مورد باشد. در این صورت مسئله به دنبال آن هستیم که یک جمله را از یک زبان مبدا به یک زبان مقصد ترجمه کنیم. می‌دانیم که این صورت مسئله کاربرد گسترده‌ای دارد. سایرهای حوزه‌های مرتبط با NLP نیز همین گونه است. 



 علاوه بر کاربردهایی که از حوزه‌های مرتبط با NLP ذکر کردیم، تکنیک‌هایی نیز در این حوزه وجود دارد. از جمله تکنیک‌های موجود در NLP را نیز می‌توان به صورت زیر لیست کرد:

1. برچسب‌زنی نقش دستوری کلمات (Part Of Speech Tagging)
2. تشخیص موجودیت‌های نامدار جملات (Name Entity Recognition)
3. تجزیه جملات (Parsing)
4. رفع ابهام در حس کلمات (Word Sense Disambiguation)

از بین تکنیک‌های فوق تشخیص موجودیت نامدار در متن بسیار جالب توجه است. در این مسئله تشخیص داده می‌شود که آیا یک کلمه اسم خاص است یا خیر. به عنوان مثال آیا کلمه "apple" در یک جمله یک اسم خاص است یا خیر. اگر بله، چه نوع اسم خاصی است. یا در مسئله رفع ابهام کلمات، آیا کلمه "شیر" به شیر جنگل اشاره دارد یا شیر آب یا شیر خوردنی؟

توجه کنید که پردازش گفتار و پردازش زبان طبیعی یا متن دو حوزه مستقل هستند که با یکدیگر اشتراکات فراوانی دارند. لذا این دو را  یکی فرض نکنید. پردازش گفتار شاخه‌ای است که به بررسی آواها می‌پردازد. در صورتی که در NLP پردازشِ صرف بر روی متن آواها یعنی بر روی واج‌ها، کاراکترها، کلمات، زیرکلمات و جملات انجام می‌شود.

همان‌طور که دیدیم، برای این که بتوان یک جمله را پردازش کنیم باید بزرگ‌ترین واحد مد نظرمان را مشخص کنیم. یعنی واج، کاراکتر، زیرکلمه، کلمه یا جمله. هر یک از این واحدهای گفتاری ممکن است در کاربرد خاصی مورد استفاده قرار گیرند. اما به صورت عمومی ترجیحی برای هیچ کدام از آن‌ها وجود ندارد و ممکن است که در یک مسئله واحدهای کوچکتر نظیر واج و در مسئله دیگر واحدهای بزرگتر نظیر کلمه بهتر عمل کنند.

بدیهی است که هر واحدی از یک کلمه که انتخاب شود، باید یک دیکشنری به ازای آن واحد ساخته شود. یعنی به هر واحد زبانی یک اندیس اختصاص داده شود. به این عملیات توکن‌سازی یا Tokenization می‌گویند.





> تمرین1:  بیست جمله در زبان فارسی بنویسید و آن‌ها براساس کاراکتر و کلمه در زبان پایتون توکن‌سازی کنید (برای انجام این کار ابتدا در یک دیکشنری به هر کاراکتر یا کلمه یا عدد منحصر به فرد اختصاص دهید و سپس هر جمله را براساس یک دنباله از اعداد بنویسید).





> تمرین2: کتابخانه phonemizer را در زبان پایتون نصب کنید و سپس تمامی بیست جمله‌ای را که در تمرین قبل نوشته بودید به حالت واج بنویسید. سپس جملات را بر اساس واج توکن‌سازی کنید. 
>
> توجه: برای متوجه شدن واج‌های معادل با آواها، الفبای IPA را از [این جا](https://en.wikipedia.org/wiki/International_Phonetic_Alphabet) مطالعه کنید.





> تمرین3: در بسیاری از جملات زبان فارسی نیاز است که پس از یک کلمه از کسره استفاده شود. به عنوان مثال "کتابِ دوستِ علی". به این کسره که در انتهای یک کلمه می‌آید کسره اضافه می‌گویند. این کسره گاهی اوقات با حرف 'ی' نیز جایگزین می‌شود. 
>
> در بیست جمله‌ای که در دو تمرین قبل نوشتید کسره اضافه‌ها را به صورت دستی مشخص کنید و سپس با کتابخانه phonemizer جملات جدید را توکن‌سازی کنید.
