<div dir='rtl' style='text-align:justify'>

# مقدمه‌ای بر Apache Hadoop

## سخن آغازین
پیش از شروع توصیف ماهیت Apache Hadoop نیاز داریم با برخی مفاهیم بصورت کلی آشنا شویم تا دید جامعی از مسئله پیدا کرده، و در ادامه اهمیت راه‌حلی که این ابزار در اختیار ما قرار می‌دهد را درک کنیم.
مطالب ذکر شده در این تحقیق توسط عرفان جعفری، سرو هارتونیان و سروش پورنصیری گردآوری و تدوین شده‌اند.

## Big Data
مفهوم Big Data، به مجموعه‌های حجیم و پیچیده اطلاعات اشاره دارد که پردازش آن با استفاده از برنامه‌ها و متدهای سنتی، عملا غیرممکن است. این مجموعه‌های داده معمولاً دارای حجم عظیمی از داده‌های ساخت‌یافته، نیمه ساخت‌یافته و ناساخت‌یافته هستند که می‌توانند معانی‌ای فراتر از از ظاهرشان برای سازمان‌ها داشته باشند. بنابراین هم پردازش عادی و ظاهری آن‌ها اهمیت دارد و نیازمند ابزارهای خاص است، هم پردازش الهامات، یعنی اطلاعاتی که از دید مخفی هستند.

## Apache Hadoop
<div dir="rtl">Hadoop یک Framework نوشته شده به زبان برنامه‌نویسی جاوا است که بر روی مجموعه‌های سخت‌افزاری معمولی عمل می‌کند. قبل از Hadoop، ما از یک سیستم Single Node برای ذخیره و پردازش داده استفاده می‌کردیم. همچنین، وابسته به پایگاه داده‌های رابطه‌ای (RDBMS) بودیم که تنها داده‌های ساخت‌یافته را ذخیره می‌کرد. در ادامه توضیح می‌دهیم چرا برای حل مشکل داده‌های حجیم و پیچیده، Hadoop بهترین راه‌حل را ارائه می‌دهد.

## چرا از Hadoop استفاده کنیم؟

### مقیاس‌پذیری
مقیاس‌پذیری Hadoop به آن امکان می‌دهد که با توزیع بار بین چندین Node در یک خوشه، با تجمع داده‌های حجیم در یک سرور مقابله کند. با افزایش حجم داده، Hadoop با اضافه کردن Nodeهای بیشتر به خوشه (Cluster)، به راحتی می‌تواند مقیاس پیدا کند. این امر اطمینان حاصل می‌کند که وظایف پردازش به بهترین شکل و به موقع انجام شود.

### اطمینان از صحت داده
<div dir="rtl">Hadoop اطمینان از صحت داده را با تکرار داده بر روی چندین Node در خوشه فراهم می‌کند. اگر یک Node در حین پردازش داده شکست خورد، Hadoop می‌تواند داده را از Nodeهای دیگری که کپی تکراری دارند بازیابی کند. این امر اطمینان حاصل می‌کند که وظایف پردازش داده بدون وقفه ادامه پیدا می‌کند، حتی در صورت بروز Failure در یک Node.

### پردازش موازی
<div dir="rtl">Hadoop قابلیت پردازش موازی داده را نیز فراهم می‌کند. این کار با تقسیم مجموعه‌های بزرگ داده به بخش‌های کوچک‌تر و پردازش همزمان آنها بر روی Nodeهای مختلف در خوشه انجام می‌شود. این قابلیت پردازش موازی به طور قابل توجهی زمان مورد نیاز برای پردازش حجم بزرگی از داده را کاهش می‌دهد و منجر به تجزیه و تحلیل سریعتر داده و استخراج اطلاعات و کسب دانش می‌شود.




# اجزای Hadoop

## A. Hadoop File System (HDFS)

<div dir="rtl">HDFS یک جزء اساسی Apache Hadoop Framework است که برای ذخیره و مدیریت Big Data به صورت توزیع‌شده طراحی شده است.

### 1. Commodity Hardware
<div dir="rtl">HDFS بر روی Commodity Hardware عمل می‌کند که شامل اجزای استاندارد و آماده‌به‌کار است. این انتخاب طراحی به سازمان‌ها این امکان را می‌دهد که خوشه‌های Hadoop خود را با استفاده از سخت‌افزار مخصوص و Specialized ایجاد و نگهداری کنند. این امر برای سازمان‌ها امکان پذیری افزایش ذخیره‌سازی و پردازش خود را بدون نیاز به تجهیزات گران‌قیمت و ویژه فراهم می‌کند. استفاده از Commodity Hardware با هدف ارائه یک راه‌حل هزینه‌ای برای مدیریت مجموعه‌های حجیم داده هماهنگ است.

### 2. Name Node
<div dir="rtl">Name Node عنصری حیاتی در HDFS است که به عنوان نود اصلی در خوشه عمل می‌کند. این نود اطلاعات متا دیسک‌ها را مدیریت می‌کند که شامل اطلاعاتی در مورد نام‌های فایل، مجوزها و ساختار دایرکتوری‌ها است. Name Node موقعیت بلوک‌های داده و عملیات خواندن و نوشتن را هماهنگ می‌کند. به عنوان نقطه مرکزی مدیریت متا، Name Node نقش مهمی در حفظ ساختار کلی و سازمان فایل سیستم دارد.

### 3. Data Node
<div dir="rtl">بر خلاف Name Node، نودهای داده مسئول ذخیره داده‌های واقعی هستند. این نودها مدیریت دستگاه‌های ذخیره متصل به خود را دارند و فرآیند ذخیره و بازیابی بلوک‌های داده را انجام می‌دهند. نودهای داده داده‌ها را در سراسر خوشه توزیع و تکرار می‌کنند تا اطمینان از پایداری و دسترسی به داده‌ها باشد. با جدا کردن مدیریت متا (که توسط Name Node انجام می‌شود) از ذخیره داده‌ها (که توسط نودهای داده انجام می‌شود)، HDFS به معماری مقیاس‌پذیر و کارآمد دست می‌یابد.

### 4. Master-Slave Cluster
<div dir="rtl">HDFS از یک معماری Master-Slave استفاده می‌کند که نوعی از معماری‌های سیستم‌های توزیعی است. در این مدل، Name Node به عنوان Master عمل می‌کند و نودهای داده به عنوان Slaveها. نود Master مدیریت متا را انجام داده و عملیات کلی فایل سیستم را کنترل و نودهای Slave داده‌های واقعی را ذخیره و مدیریت می‌کنند. این معماری مقیاس‌پذیری و اطمینان از صحت را افزایش می‌دهد. افزودن نودهای داده بیشتر به خوشه امکان افزایش ظرفیت ذخیره و پردازش را از طریق مسیر افقی ممکن می‌سازد و تقاضای افزایشی از مجموعه‌های حجیم داده را توانمند می‌کند.

### 5. Distributed Manner
<div dir="rtl">HDFS داده‌ها را به صورت توزیع شده در سراسر چندین Data Node ذخیره می‌کند. هنگامی که یک فایل به سیستم وارد می‌شود، به بلوک‌ها تقسیم می‌شود و این بلوک‌ها به نودهای داده مختلف در خوشه توزیع می‌شوند. توزیع داده در سراسر چندین نود امکان پردازش موازی و بهره‌وری کارگر را فراهم می‌کند. این رویکرد ذخیره‌سازی توزیع‌شده نه تنها عملکرد را بهبود می‌بخشد بلکه اطمینان از صحت را فراهم می‌کند. کپی داده در نودها اطمینان می‌دهد که حتی اگر یک نود شکست خورد، داده قابل دسترس باقی می‌ماند و این به قابلیت اطمینان کلی سیستم کمک می‌کند.

### خلاصه
<div dir="rtl">در نتیجه، HDFS از Commodity Hardware برای مقیاس‌پذیری هزینه‌ای بهره می‌برد، از معماری Master-Slave برای مدیریت بهینه متا و داده استفاده می‌کند، و از رویکرد ذخیره‌سازی توزیع‌شده برای بهبود عملکرد و اطمینان از صحت بهره می‌برد. این ترکیب از ویژگی‌ها HDFS را به یک راه‌حل قدرتمند برای مدیریت Big Data در یک محیط توزیع‌شده تبدیل کرده است.

## B. MapReduce Hadoop
<div dir="rtl">MapReduce در Hadoop یک مدل برنامه‌نویسی و موتور پردازش است که برای پردازش و تجزیه و تحلیل حجم عظیمی از داده به صورت موازی در یک خوشه توزیع شده طراحی شده است.

### پردازش موازی
<div dir="rtl">یکی از قدرت‌های اصلی MapReduce، قابلیت بهره‌مندی از پردازش موازی است. در پردازش داده‌های سنتی، وظایف به ترتیب اجرا می‌شوند که به کاهش عملکرد منجر می‌شود هنگام برخورد با مجموعه‌های بزرگ داده. با MapReduce، داده به قطعات کوچک تقسیم شده و همزمان در نودهای مختلف یک خوشه پردازش می‌شوند. این توازن موازیسم به طور قابل توجهی پردازش داده را شتاب می‌دهد و برای مقابله با حجم عظیمی از داده‌ها مناسب است.

### اهمیت معماری Master-Slave
<div dir="rtl">MapReduce از معماری Master-Slave استفاده می‌کند که آن را از روش‌های سنتی پردازش متمایز می‌کند. در یک چارچوب MapReduce، نود Master هماهنگی و مدیریت اجرا را انجام می‌دهد، در حالی که نودهای Slave وظایف پردازش موازی را انجام می‌دهند. این معماری به MapReduce امکان افزایش افقی با افزودن نودهای بیشتر به خوشه را می‌دهد، که آن را به یک راه‌حل موثر برای پردازش Big Data تبدیل می‌کند. توزیع وظایف در نودهای مختلف، سرعت پردازش و تحمل اشکال را افزایش می‌دهد و اطمینان از تحلیل کارآمد مجموعه‌های حجیم داده را فراهم می‌کند.

## مراحل MapReduce


#### مرحله تقسیم:
   داده ورودی به قطعات مدیریت‌پذیر تقسیم می‌شود. هر تقسیم توسط یک مپر مستقل پردازش می‌شود.

#### مرحله Map:
   - مپر ورودی تقسیم شده را پردازش کرده و مجموعه جفت کلید-مقداری ایجاد می‌کند. در مثال شکل نشان داده شده، هر جفت نشان‌دهنده یک کلمه و تعداد تکرار آن (۱) است.

#### مرحله Shuffle و Sort:
   - خروجی مرحله Map بر اساس کلیدها مخلوط و مرتب می‌شود. این مرحله اطمینان می‌دهد که همه تکرارهای یک کلمه با هم گروه‌بندی شده و آماده برای مرحله بعدی هستند.

#### مرحله Reduce:
   - ردیوسر جفت‌های کلید-مقدار مرتب شده را دریافت کرده و عملیات تجمیع یا محاسبه مورد نیاز را انجام می‌دهد. در مثال شکل نمایش داده شده، تعداد تکرارها برای هر کلمه جمع‌آوری می‌شود تا خروجی نهایی به دست آید.

### خلاصه

<div dir="rtl">به طور خلاصه، Hadoop MapReduce از قدرت پردازش موازی بهره می‌برد که امکان تحلیل کارآمد Big Data را فراهم می‌کند. معماری Master-Slave، قابلیت افزایش افقی و مراحل خوش تعریف تقسیم، مپ، مخلوط و مرتب‌سازی و ردیوس از MapReduce یک ابزار ارزشمند برای پردازش Big Data در اکوسیستم Hadoop می‌سازد.

## Hadoop YARN

<div dir="rtl">Hadoop YARN (Yet Another Resource Negotiator) یک لایه مدیریت منابع در Hadoop است که برای مدیریت و برنامه‌ریزی منابع به صورت کارآمد برای پردازش توزیع‌شده طراحی شده است.

### سیستم‌های عامل سنتی در مقابل YARN
<div dir="rtl">هنگامی که در سیستم‌های عامل سنتی منابع در یک دستگاه مدیریت می‌شوند، YARN این مفهوم را به مدیریت منابع در یک خوشه از دستگاه‌ها گسترش می‌دهد. در یک سیستم عامل، منابع به فرآیندها در یک نود تخصیص داده می‌شوند، در حالی که YARN بر روی یک خوشه عمل کرده و تخصیص منابع را در سراسر چندین نود مدیریت می‌کند. این رویکرد توزیعی به YARN امکان می‌دهد که به صورت مقیاس‌پذیرتر و کارآمدتری نسبت به سیستم‌های عامل سنتی با Big Data مدیریت شود.

### مدیر منابع و نود منیجر
<div dir="rtl">YARN از یک معماری Master-Slave برای مدیریت خوشه استفاده می‌کند. **مدیر منابع** به عنوان Master عمل می‌کند و تخصیص منابع را در سراسر تمام خوشه نظارت می‌کند. هر نود در خوشه دارای یک **نود منیجر** است که مسئول مدیریت منابع در آن نود خاص است. همکاری بین مدیر منابع و نود منیجرها تضمین می‌کند که منابع بهینه مورد استفاده قرار گیرند در سراسر کل خوشه.

### برنامه‌ریزی کارآمد وظایف
<div dir="rtl">YARN برنامه‌ریزی کارآمد وظایف را با اختصاص پویا منابع به برنامه‌ها بر اساس نیازهای آنها تسهیل می‌کند. این امکان را فراهم می‌کند که چندین برنامه به صورت همزمان منابع را در یک خوشه به اشتراک بگذارند. قابلیت یارانه‌گذاری YARN و تخصیص و مدیریت پویا منابع به ارتقاء کلی بهره‌وری خوشه انجام می‌دهد و آن را به یک ابزار قدرتمند برای بارهای کاری متنوع و تقاضای متغیر منابع تبدیل می‌کند.

### چگونگی عمل YARN (مثال: اجرای یک کار MapReduce)

#### Resource Request
   - یک برنامه (برای مثال، یک کار MapReduce) درخواست منابع را به مدیر منابع ارسال می‌کند.

#### Resource Allocation
   - مدیر منابع منابع را بر اساس نیازهای برنامه اختصاص می‌دهد. هر منبع تخصیص داده شده توسط یک **Container** نمایان می‌شود.

#### Node Manager Execution
   - مدیر منابع، نود منیجرها را به اجرای Containerها دستور می‌دهد. هر نود منیجر مسئول اجرای Containerها بر روی نود مربوطه است.

#### Task Execution
   - در هر Container، وظایف برنامه (مانند وظایف map و reduce در یک کار MapReduce) به صورت مستقل اجرا می‌شوند.

#### De-allocation
   - هنگامی که برنامه کامل شود، مدیر منابع، دسترسی را لغو می‌کند و آن‌ها را برای برنامه‌های دیگر در دسترس می‌گذارد.

<div dir="rtl">معماری ماژولار و انعطاف‌پذیر YARN به آن امکان می‌دهد که از چارچوب‌های برنامه‌های مختلف خارج از MapReduce پشتیبانی کند، که آن را به یک راه‌حل چندمنظوره و گسترده در اکوسیستم Hadoop تبدیل می‌کند.

### خلاصه

به‌صورت خلاصه، Hadoop YARN مدل مدیریت منابع سنگین سیستم‌های عامل سنتی را در Hadoop گسترش داده و منابع را به طور بهینه برای پردازش توزیع‌شده برنامه‌ریزی می‌کند. معماری Master-Slave، برنامه‌ریزی کارآمد وظایف، و تخصیص و مدیریت دینامیک منابع آن را به یک ابزار حیاتی برای مدیریت و بهینه‌سازی منابع در محیط‌های پردازش داده بزرگ می‌کند.

# سخن پایانی: هماهنگی اکوسیستم Hadoop

تعامل بین اجزای کلیدی اکوسیستم Hadoop - سیستم فایل توزیع‌شده Hadoop (HDFS)، MapReduce و Yet Another Resource Negotiator (YARN) - یک چارچوب قدرتمند و جامع برای پردازش و مدیریت Big Data در محیط‌های توزیع‌شده ایجاد می‌کند.

## HDFS

<div dir="rtl"> HDFS به عنوان ستون فقرات عمل کرده و یک راه‌حل ذخیره‌سازی قابل اعتماد و قابل مقیاس فراهم می‌کند. قابلیت بهره‌وری از Commodity Hardware، معماری Master-Slave و رویکرد ذخیره‌سازی توزیع‌شده از HDFS مراحل پردازش بعدی را فراهم می‌کند.

## MapReduce

<div dir="rtl">MapReduce بر روی HDFS عمل کرده و قابلیت پردازش موازی را برای تحلیل و استخراج اطلاعات ارائه می‌دهد. همچنین ذکر شد معماری Master-Slave، قابلیت مقیاس‌پذیری افقی را به همراه دارد و مراحل خوش تعریف  MapReduce را به یک ابزار مهم برای مواجهه با Big Data می‌سازد.

## YARN

<div dir="rtl"> YARN (Yet Another Resource Negotiator) هماهنگی مدیریت منابع را در کل خوشه از Hadoop انجام می‌دهد. معماری Master-Slave، برنامه‌ریزی Efficient وظایف و تخصیص و مدیریت دینامیک منابع، باعث می‌شود YARN نقشی اساسی در بهینه‌سازی منابع در محیط‌های پردازش داده بزرگ داشته باشد.

## سخن پایانی

در نهایت، مراحل اجرایی و اجزای Hadoop یک اکوسیستم یکپارچه ایجاد می‌کند که ذخیره‌سازی داده، پردازش موازی و مدیریت منابع را یک‌جا ارائه می‌دهد. این رویکرد یک راه‌حل قوی برای سازمان‌ها با چالش‌های پردازش و استخراج اطلاعات ارزشمند از حجم عظیمی از داده‌ها فراهم می‌کند.

## منابع و ماخذ
- https://www.youtube.com/watch?v=iANBytZ26MI
- https://www.geeksforgeeks.org/hadoop-tutorial