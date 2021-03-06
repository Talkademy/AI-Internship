

در این بخش به مرور مباحث یادگیری ماشین می‌پردازیم. پیش‌فرض ما در این جا این است که شما با این مباحث آشنایی دارید و این مباحث صرفا جنبه مرور و یادآوری دارد.

به طور کلی اگر بخواهیم یک دسته‌بندی از هوش مصنوعی ارائه دهیم می‌توانیم به شکل زیر اشاره کنیم:

![](AI_field.png)

به طور کلی یادگیری ماشین یک زیرمجموعه از هوش مصنوعی است که با سایر حوزه‌های هوش مصنوعی ارتباط تنگاتنگی دارد. اگر بخواهیم یک هدف کلی برای یادگیری ماشین مشخص کنیم می‌توانیم بگوییم که کار یادگیری ماشین تخمین تابع است. در واقع در حوزه یادگیری ماشین تلاش داریم تا روابط بین پدیده‌ها را با یک تابع مدل کنیم. این تابع می‌تواند با دریافت یک یا چند ورودی، یک یا چند خروجی را برای ما تولید کند.

اگر بخواهیم یک نگاه کلی به یادگیری ماشین بیندازیم و آن را با برنامه‌نویسی عادی مقایسه کنیم، می‌توانیم بگوییم که در برنامه‌نویسی، برنامه و داده ورودی به ماشین داده می‌شود و ماشین با اجرای برنامه بر روی داده ورودی، داده خروجی را تولید می‌کند. اما در یادگیری ماشین، نتوانیم برای تولید داده خروجی از ورودی برنامه‌ای بنویسیم. لذا هم داده ورودی و هم داده خروجی به ماشین داده می‌شود و از این جا به بعد، وظیفه‌ی به دست آوردن برنامه مناسب برای تولید خروجی از ورودی به عهده ماشین خواهد بود. به شکل زیر توجه کنید.

![](com.png)



اما برای این که ماشین بتواند رابطه بین ورودی و خروجی را تشخیص دهد باید روش‌ها و الگوریتم‌هایی را به ماشین بدهیم که بتواند رابطه بین ورودی و خروجی را تشخیص دهد. برخی از مهم‌ترین این الگوریتم‌ها در زیر لیست شده‌اند:

- Linear Regression

- Logistic Regression

- K-Nearset Neighbors (KNN)

- Support Vector Machine (SVM)

- Naive Bayes

- Decision Tree

- Random Forest

- Single Perceptron

- Neural Networks

- K-means

- Principal Component Analysis (PCA)


از بین این الگوریتم‌ها، 9 مورد ابتدایی را باناظر (supervised) گویند و مابقی را بدون‌ناظر یا (Unsupervised) گویند. در الگوریتم‌های باناظر بدین صورت عمل می‌شود که زوج داده ورودی و خروجی (یعنی ${(x,y) \in X \times Y}$) همزمان در دسترس ما است و مدل برای آموزش از آن استفاده می‌کند. اما در الگوریتم‌های بدون‌ناظر فقط داده ورودی در دسترس است و مدل هیچ‌گونه بازخوردی بابت خروجی‌ای که در هنگام آموزش تولید می‌کند دریافت نمی‌کند. 

اکنون به بررسی اجمالی چند مورد از این الگوریتم‌ها خواهیم پرداخت. 

## الگوریتم رگرسیون خطی

در الگوریتم رگرسیون خطی یک مدل خطی نظیر $\hat{y} = w.x + b$ با ضرایب $w=(w_1, w_2 ,..., w_k) \in \mathbb{R}^k$ و بایاس $b \in \mathbb{R}$ به دادگان برازش می‌شود. برای یافتن ضرایب و بایاس بهینه کافی است تا تابع خطا زیر را بهینه  کنیم:

$$\ell = \frac{1}{n-1} (y-\hat{y})^2 $$

که در رابطه فوق $n$ تعداد نمونه‌ها،  $y$ خروجی واقعی متناسب با ورودی $x$  و $\hat{y}$ خروجی پیش‌بینی شده مدل می‌باشد. برای پیاده‌سازی این بخش از کتابخانه sklearn پایتون استفاده خواهیم کرد. برای اطلاعات بیشتر به [این لینک](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html) مراجعه کنید. 





> تمرین 1: تابع $y = sin(x) \;  0 \leq x \leq \frac{\pi}{2}$ را در نظر بگیرید. با استفاده از کتابخانه sklearn یک مدل رگرسیون خطی بر این تابع برازش کنید و خطای مدل خود را گزارش کنید.



## الگوریتم k نزدیک‌ترین همسایه (KNN)

برخلاف مدل رگرسیون خطی که یک مدل برای برازش توابع است، این الگوریتم یک دسته‌بندی است. این الگوریتم بدین صورت عمل می‌کند که فاصله یک داده ورودی را از تمامی دادگان ورودی موجود در مجموعه داده محاسبه می‌کند و سپس از بین k نمونه‌ای که از همه به داده ورودی جدید نزدیک‌تر هستند، کلاس‌های متناظر آن‌ها را در نظر می‌گیرد و بین آن کلاس‌ها رای‌گیری انجام می‌دهد و کلاسی که بیشترین تکرار را در بین این k همسایه داشته باشد به عنوان خروجی در نظر گرفته می‌شود. این الگوریتم به عنوان یک الگوریتم تنبل (lazy) شناخته می‌شود، زیرا فاز آموزش ندارد و هر مرتبه باید تمام دادگان را اسکن کند.



> تمرین2: دادگان دو کلاسه زیر را در نظر بگیرید:
>
> $x_1  = (1,1) $, $y_1 = 1$
>
> $x_2  = (0,1) $, $y_2 = 1$
>
> $x_3  = (2,4) $, $y_3 = -1$
>
> $x_4  = (-2,1) $, $y_4 = -1$
>
> $x_5  = (1,3) $, $y_5 = 1$
>
> $x_6  = (9,1) $, $y_6 = -1$
>
> اکنون با استفاده از الگوریتم KNN برای k=3 هم به صورت دستی و هم با استفاده از کتابخانه sklearn  کلاس متناظر با داده $x=(0, 0)$ را بیابید. برای آشنایی با نحوه آموزش مدل KNN با استفاده از کتابخانه sklearn  به [این لینک](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html) مراجعه کنید.



## الگوریتم بیز ساده (Naive Bayes)

الگوریتم بیز ساده همانند الگوریتم KNN یک دسته‌بند است. این الگوریتم مبتنی بر قانون بیز در احتمال طراحی شده است. اگر داده ورودی $x=(x_1, x_2, ..., x_n)$ در دسترس ما باشد و مسئله ما نیز شامل کلاس‌های $C_1, ..., C_k$ باشد، آنگاه برای این که مشخص شود داده ورودی $x$ به کدام کلاس تعلق دارد کافی است تا احتمال شرطی $P(C_i|x)$ که $i \in {1, ..., k}$ محاسبه شود. اکنون کافی است تا کلاس متناظر با بیشترین احتمال شرطی را انتخاب کنیم و به عنوان کلاس خروجی در نظر بگیریم. یعنی $C^* = \underset{C_i}{argmax P(C_i|x)}$. به این روش برای یافتن کلاس متناظر با داده، روش تخمین بیشینه درستنمایی یا Maximum Likelihood Estimation (MLE) میگویند.

اما بخش اصلی در اینجا محاسبه $P(C_i|x)$ می‌باشد. واضح است که نمی‌توان این احتمال را به صورت مستقیم از دادگان تخمین زد. به همین سبب از قاعده بیز در احتمال به صورت زیر کمک می‌گیریم:

 $$P(C_i|x) = \frac{P(x|C_i) P(C_i)}{P(x)}$$

در رابطه فوق به $P(x|C_i)$ احتمال درستنمایی (Likelihood) به $P(x)$ احتمال پیشین (Prior) به $P(C_i|x)$ احتمال پسین (Posterior) و به $P(x)$ احتمال شواهد (evidence) می‌گویند.

از آن جایی که $P(x)$ یک مقدار ثابت است و از آن‌جایی که محاسبه آن از طریق مجموعه دادگان به سادگی قابل انجام نیست لذا می‌توان احتمال شرطی فوق را به صورت زیر و با یک نسبت از احتمال اصلی نوشت:

$$P(C_i|x) \propto P(x|C_i) P(C_i)$$

همچنین از آنجایی که $x=(x_1, ..., x_n)$ لذا محاسبه $P(x|C_i)$ به سادگی قابل انجام نیست. لذا  برای انجام این کار از فرض ساده‌سازی زیر استفاده می‌کنیم:

$$P(x|C_i) = \prod_{j=1}^{n} P(x_j|C_i)$$



## الگوریتم درخت تصمیم (Decision Tree)

الگوریتم درخت تصمیم، یک الگوریتم یادگیری باناظر است که بیشتر در حوزه داده کاوی مورد استفاده قرار می‌گیرد. دلیل این امر نیز این است که الگوریتم درخت تصمیم توانایی بالایی در نمایشِ نحوه و مسیر طی شده برای دسته‌بندی یک نمونه از داده را دارد. این الگوریتم بیشتر برای مسائل دسته‌بندی مورد استفاده قرار می‌گیرد. اما می‌توان با انجام تغییراتی، از آن در مسائل رگرسیون نیز استفاده نمود. اما ما در این جا صرفا به مسائل دسته‌بندی می‌پردازیم.

همان طور که از آن این الگوریتم مشخص است، باید با اتخاذ تصمیماتی، و در طی چند مرحله، هر نمونه از داده دسته‌بندی شود. برای این کار بدین صورت عمل می‌کنیم که در هر مرحله یک ویژگی از نمونه را در نظر می‌گیریم و همچنین تمامی حالات ممکن برای آن ویژگی را از مجموع داده استخراج می‌کنیم. اکنون اگر بتوانیم با همین ویژگی نمونه را دسته‌بندی کنیم کار تمام است. در غیر این صورت ویژگی دیگری را در نظر می‌گیریم و تمامی حالات ممکن برای آن ویژگی را نیز استخراج می‌کنیم. مجدد اگر بتوانیم با این ویژگی داده را دسته‌بندی کنیم، کار تمام است. در غیر این صورت به سراغ ویژگی بعدی می‌رویم. این کار را آن قدر تکرار می‌کنیم که دیگر ویژگی‌ای باقی نماند.

فرایند انتخاب ویژگی و همچنین حالات ممکن برای آن ویژگی را می‌توان در یک درخت نشان داد که در این درخت راس‌ها همان ویژگی‌ها و یال‌ها همان حالات ممکن هستند. همچنین برگ‌ها در این درخت همان کلاس‌های ما هستند.

یک مثال دسته‌بندی از افرادی که در حادثه تایتانیک زنده مانده‌اند یا مرده‌اند  را در شکل زیر مشاهده می‌کنید.

![](https://upload.wikimedia.org/wikipedia/commons/e/eb/Decision_Tree.jpg)

در درخت تصمیم، مسئله اساسی این است که کدام ویژگی در هر مرحله از ساخت درخت انتخاب شود یا به عبارت بهتر، معماری درخت چگونه باشد؟ برای پاسخ به این سوال باید گفت که در الگوریتم درخت تصمیم فرایند یافتن معماری مناسب برای درخت، همزمان با فرایند آموزش انجام می‌شود. لذا برای انجام این کار روش‌های مختلفی ارائه شده است که چند مورد آن در زیر لیست شده‌اند.

1. ID3
2. C4.5
3. CART
4. CHAID
5. MARS

با استفاده از [این مقاله](https://cis.temple.edu/~giorgio/cis587/readings/id3-c45.html)، الگوریتم‌های ID3 و C4.5 را مطالعه کنید.

سوال اساسی دیگری که ممکن است در درخت تصمیم پرسیده شود این است که آیا نیاز است تمامی ویژگی‌ها را درخت مورد استفاده قرار دهیم؟ پاسخ این سوال خیر است و همیشه نیاز به استفاده از تمامی ویژگی‌ها نیست و استفاده از تمامی ویژگی‌ها، در برخی مواقع، می‌تواند باعث بیش‌برازش مدل شود. به فرایند حذف ویژگی‌ها کم اهمیت، هرس کردن (pruning) می‌گویند. از مقاله فوق این مفهوم را به صورت کامل مطالعه کنید.

## الگوریتم K-means

این الگوریتم یک الگوریتم خوشه‌بندی است و در واقع یک الگوریتم بدون‌ناظر است. این الگوریتم دارای یک پیش‌فرض اولیه است و این پیش‌فرض نیز این است که k خوشه داریم و می‌خواهیم کلیه دادگان را در این $k$  خوشه افراز کنیم. 

این الگوریتم بدین صورت عمل می‌کند که ابتدا $k$ داده فرضی را به عنوان مراکز خوشه‌ها، ابتدا به صورت تصادفی مقداردهی اولیه می‌کند و سپس فاصله‌ی  هر یک از نمونه‌های موجود در دادگان را تا هر خوشه محاسبه می‌کند. سپس هر نمونه را به خوشه‌ای اختصاص می‌دهد که از آن کمترین فاصله را دارد. اکنون با استفاده از نمونه‌های موجود در هر خوشه یک مرکز خوشه جدید محاسبه می‌شود. هر مرکز خوشه جدید در واقع میانگین تمامی نمونه‌های موجود در آن خوشه خواهد. اکنون مجدد فاصله هر مرکز خوشه تا هر نمونه محاسبه می‌شود و هر خوشه شامل نمونه‌هایی خواهد بود که از آن مرکز کمترین فاصله را دارند. این فرایند تا جایی ادامه پیدا می‌کند که هیچ مرکز خوشه‌ای تغییر پیدا نکند.

برای فهم بهتر الگوریتم به [این ویدئو](https://www.youtube.com/watch?v=hDmNF9JG3lo) از andrew ng  مراجعه کنید.



> تمرین3: دادگان زیر را با استفاده از الگوریتم K-means در دو خوشه، خوشه‌بندی کنید.  :
>
> $x_1  = (1,1) $
>
> $x_2  = (0,1) $
>
> $x_3  = (2,4) $
>
> $x_4  = (-2,1) $
>
> $x_5  = (1,3) $
>
> $x_6  = (9,1) $
>
> توجه کنید که این کار هم باید به صورت دستی و هم با پیاده‌سازی برنامه در پایتون انجام شود. برای سهولت می‌توانید از کتابخانه sklearn  در [این لینک](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html) استفاده کنید.







## الگوریتم تحلیل مولفه اساسی (PCA)

در الگوریتم تحلیل مولفه اساسی هدف این است که ابعاد دادگان را کاهش داده و به عبارتی تعداد ویژگی‌های موجود در دادگان را کاهش دهیم. نکته مهم در این الگوریتم این است که پس از اعمال آن به دادگان، ماهیت تمامی ویژگی‌های موجود در دادگان تغییر می‌کند. به عبارت دیگر، پس از اعمال این الگوریتم به دادگان، کلیه‌ی ویژگی‌ها تغییر می‌کنند و دیگر ویژگی‌های سابق نخواهند بود.

اگر در مجموعه دادگان مورد استفاده، $n$ ویژگی وجود داشته باشد، الگوریتم PCA می‌تواند دقیقا $n$ ویژگی با ماهیت جدید برای تولید کند، با این تفاوت که ویژگی‌ها بر اساس درجه اهمیتی که دارند مرتب شده‌اند. اکنون می‌توانیم $k$ ویژگی با درجه اهمیت کم را حذف کنیم و صرفا $n-k$ ویژگی با درجه اهمیت بیشتر را نگه داریم.

برای تفسیر این الگوریتم براساس نمادهای ریاضی، فرض کنید $X \in \mathbb{R}^{d \times n}$ یک ماتریس است که در برگیرنده تمامی دادگان ما است. 

این ماتریس به گونه‌ای است که در ستون‌های آن، نمونه‌ها و در سطرهایش، ویژگی‌ها قرار گرفته‌اند. 

اکنون در ابتدا از این ماتریس میانگین ستونی می‌گیریم و میانگین به دست آمده را از تک تک ستون‌های ماتریس حذف می‌کنیم تا میانگین این ماتریس صفر شود. فرض کنید ماتریس جدید به دست آمده $\hat{X}$ باشد. اکنون به صورت زیر ماتریس کوواریانس را محاسبه می‌کنیم:

$$C = \frac{1}{n-1} \hat{X}^T \hat{X} \in \mathbb{R}^{d \times d}$$ 

اکنون ماتریس $C$ را با استفاده از تجزیه مقدار ویژه به صورت زیر تجزیه می‌کنیم:

$$C = U\Lambda U^T = (U\Lambda^{\frac{1}{2}})(U\Lambda^{\frac{1}{2}})^T$$ 

که در این رابطه ماتریس $U$ ماتریس‌ متعامد است. توجه کنید که ماتریس متعامد ماتریسی است که ضرب آن در تنهاده‌اش (از سمت راست، چپ یا هر دو طرف) برابر ماتریس همانی شود.

 همچنین ماتریس $\Lambda$ یک ماتریس قطری است. 

اکنون عناصر روی قطر ماتریس $\Lambda$ مشخص‌کننده میزان اهمیت هر یک از $n$ ویژگی جدید به دست آمده است. این مقادیر از درجه اهمیت زیاد به کم روی قطر مرتب شده‌اند. بنابراین با توجه به این مقادیر می‌توان تصمیم گرفت که چه تعدادی از ویژگی‌ها حفظ و چه تعداد از آن‌ها کنار گذاشته شود. قبل از ادامه کار تبدیل زیر را می‌سازیم:

$$T = U\Lambda^{\frac{1}{2}} \in \mathbb{R}^{d \times d}$$

حال فرض کنید بخواهیم $k$ ویژگی را حذف کرده و $d-k$ ویژگی را نگه داریم. در این حالت کافی است تا $k$ سطر از ماتریس $T$ را حذف کنیم و ماتریس $T_k \in \mathbb{R}^{(d-k) \times d}$ را بسازیم.

به ازای هر داده جدید چون $x$ ابتدا میانگین $X$ را از آن کم می‌کنیم و سپس با ماتریس تبدیل $T_k$ به فضای جدید منتقل می‌کنیم و ویژگی‌های متناظر را در فضای جدید به دست می‌آوریم.:

$$x^{'} = T_k(x-\mu)$$

توجه کنید که در این جا $\mu$ میانگین ستونی ماتریس $X$ است.



> تمرین4: الگوریتم PCA را بر روی مجموعه اعداد دست‌نویس اعمال کنید. فرایند کاهش بعد را به گونه‌ای انجام دهید که بردار به دست آمده به ازای هر تصویر، شامل 98 درصد از اطلاعات تصویر باشد.
>
> توجه: برای این که $n$ درصد از اطلاعات را در فرایند کاهش بعد حفظ کنید باید بردارهای ویژه‌ای را انتخاب کنید که مجموع مقادیر ویژه آن‌ها $n$ درصد از مجموع کل مقادیر ویژه‌ها باشد.





## مفهوم ensemble modeling 

تا این جای کار آموختید تا برای هر مجموعه داده یک مدل یادگیر اختیار کنید و آن را روی آن مجموعه داده آموزش دهید. اما گاهی اوقات یک مدل یادگیر به تنهایی نمی‌تواند عملکرد خوبی را از خود به نمایش بگذارد. به همین سبب در چنین شرایطی، می‌توان چندین مدل یادگیر آموزش داد و آن‌ها را با هم ترکیب کرد تا یک مدل یادگیر واحد ساخته شود که هر کدام ضعف دیگری را جبران می‌کنند. به فرایند ساخت چنین مدلی ensemble modeling  گویند. 

دو شیوه بسیار مرسوم برای ensemble modeling عبارتند از: 

1. Boosting
2. Bootstrap aggregating (Bagging)

با استفاده از [این مقاله](https://en.wikipedia.org/wiki/Ensemble_learning) در ویکی‌پدیا دو روش فوق را مطالعه کنید.

از بین روش‌های Boosting  دو روش AdaBoost و XGBoost را از [این مقاله](https://algotech.netlify.app/blog/xgboost/) مطالعه کنید.

همچنین برای Bagging الگوریتم جنگل تصادفی (Random Forest) که بر مبنای الگوریتم درخت تصمیم است را از [این مقاله](https://www.section.io/engineering-education/introduction-to-random-forest-in-machine-learning/) مطالعه کنید.
