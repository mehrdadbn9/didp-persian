## COMPOSITE

الگو composite از دسته دیزاین پترن ساختاری است که به  آبجکت ها این اجازه را می‌دهد که ساختار درختی داشته و  در حین کار با این ساختار را به عنوان آبجکت مجزا را دارد.


###  مشکل 😟

استفاده از الگوی کامپوزیت تنها زمانی معقول است که هسته مدل اپلیکیشن شمابه صورت یک درخت ارائه شده است.

به عنوان مثال، تصور کنید دو نوع آبجکت **محصولات**  و **جعبه ‌ها** وجود دارد. یک جعبه می‌تواند شامل  تعدادی محصول باشد. این جعبه ها می تواند شامل محصولات و یا شامل جعبه ‌های کوچکتر باشد.

![ترتیب قرارگیری محصولات می‌تواند متنوع باشد یا به شکل پکیج داخل جعبه در نظر گرفته شود که این پکیج‌ها داخل جعبه بزرگتری قرار می‌گیرد. تمام ساختار به شکل از بالا به پایین درنظر گرفته می ‌شود.](https://github.com/ftg-iran/didp-persian/blob/main/4-Catalog%20Of%20Design%20Patterns/images/diagrams/composite/problem-en.png?raw=true)
ترتیب قرارگیری محصولات می‌تواند متنوع باشد یا به شکل پکیج داخل جعبه در نظر گرفته شود که این پکیج‌ها داخل جعبه بزرگتری قرار می‌گیرد. تمام ساختار به شکل از بالا به پایین درنظر گرفته می ‌شود.

اگر تصمیم بگیریدیک سیستم سفارش ایجاد کنید که از این کلاس ها استفاده کند. سفارشات ممکن است شامل محصولات ساده و بدون بسته‌بندی باشد، همچنین جعبه ‌ها ممکن است شامل محصولات دیگر یا جعبه باشد. حال چطور باید قیمت کل این سفارش محاسبه شود؟

 شما می‌توانید از دسترسی مستقیم استفاده کنید: تمام جعبه‌ها را باز کنید و با درنظرگرفتن تمام محصولات هزینه را محاسبه کنید. این کار در دنیای واقعی امکان پذیر است؛ اما در برنامه، به سادگی تکرار یک لوپ نمی‌باشد. شما نیاز به اطلاعات کلاس‌های محصولات، جعبه‌ها و میزان تو در تو بودن یا سایر جرئیات خواهید داشت. تمام این موارد، دسترسی را عجیب و غیرممکن می‌کند.

 ###    راه‌حل 

 الگوی کامپوزیت پیشنهاد می‌کند که شما با محصولات و جعبه‌ها با یک اینترفیس معمول برای محاسبه قیمت کل کار کنید.

 این متد چگونه کار می‌کند؟ برای محصولات، به سادگی قیمت محصول را برمی‌گرداند. برای جعبه، موارد داخل جعبه بررسی می‌شود و زمانیکه قیمت آن جعبه خواسته شود قیمت کل جعبه برگردانده می‌شود. اگر یکی از این آیتم ها جعبه کوچکتری باشد،به همین ترتیب محاسبه می‌شودتا قیمت موارد داخلی حساب شود. یک جعبه یا پکیج  می‌تواند موجب هزینه بیشتر نهایی شود . 
 ![الگوی ترکیبی به شما این امکان را می دهد که یک رفتار را به صورت بازگشتی روی همه اجزای یک درخت  اجرا کند.](https://github.com/ftg-iran/didp-persian/blob/main/4-Catalog%20Of%20Design%20Patterns/images/diagrams/...)

بزرگترین مزیت این رویکرد این است که نیازی نیست به کلاس های مشخصی از اشیاء که درخت را تشکیل می دهند اهمیت دهید. نیازی نیست بدانید که آیا یک شی یک محصول ساده یا یک جعبه پیچیده وجود دارد. می توانید از طریق رابط مشترک با همه آنها یکسان رفتار کنید. وقتی یک متد را فراخوانی می کنید، خود اشیا درخواست را به درخت ارسال می کنند.

### در دنیای واقعی کامپوزیت  🚗![نمونه ای از ساختار نظامی.](https://github.com/ftg-iran/didp-persian/blob/main/4-Catalog%20Of%20Design%20Patterns/images/diagrams/...)
 
ارتش های اکثر کشورها به صورت سلسله مراتبی تشکیل شده اند. یک ارتش از چندین بخش تشکیل شده است. یک لشکر مجموعه ای از تیپ ها است و یک تیپ شامل جوخه هایی است که می توانند به جوخه ها تقسیم شوند. در نهایت، یک جوخه گروه کوچکی از سربازان واقعی است. دستورات در بالای سلسله مراتب داده می شود و به هر سطح منتقل می شود تا زمانی که هر سرباز بداند چه کاری باید انجام شود.


1.رابط ;کامپوننت عملیاتی را توصیف می کند که
هر دو عنصر ساده و پیچیده درخت.

2.برگ (leaf) یک عنصر اساسی درخت است که عناصر فرعی ندارد.
معمولاً اجزای برگ (leaf) بیشتر کار واقعی را انجام می دهند، زیرا کسی را ندارند که کار را به او واگذار کنند.

3.کانتینر (معروف به کامپوزیت) عنصری است که دارای عناصر فرعی است: برگ(leaf) ها یا سایر ظروف. یک کانتینر طبقات واقعی فرزندانش را نمی شناسد و با تمام عناصر فرعی فقط از طریق رابط کامپوننت کار می کند.

4.کلاینت با تمام عناصر از طریق رابط کامپوننت کار می کند. در نتیجه، مشتری می تواند با هر دو عنصر ساده یا پیچیده درخت به یک شکل کار کند.

### قطعه کد نمونه#️⃣  

در این مثال، الگوی **کامپوزیت** به شمااین امکان را می دهد که اشکال هندسی را در یک ویرایشگر گرافیکی پیاده سازی کنید.
![مثال ویرایشگر اشکال هندسی.](https://github.com/ftg-iran/didp-persian/blob/main/4-Catalog%20Of%20Design%20Patterns/images/diagrams/...)

کلاس ``CompoundGraphic`` ظرفی است که می‌تواند شامل هر تعداد زیر بخش از جمله اشکال ترکیبی دیگر باشد. یک شکل مرکب همان روش های یک شکل ساده را دارد. با این حال، به جای اینکه کاری را به تنهایی انجام دهد، یک شکل مرکب درخواست را به صورت بازگشتی به همه فرزندان خود ارسال می کند و نتیجه را «خلاصه» می کند.

کد کلاینت با همه اشکال از طریق رابط واحد مشترک برای همه کلاس ها کار می کند. بنابراین، مشتری این کار را نمی کند.

بنابراین، مشتری نمی داند که آیا با یک شکل ساده کار می کند یا یک شکل مرکب. مشتری می‌تواند با ساختارهای شی بسیار پیچیده کار کند، بدون اینکه به کلاس‌های منسجم که آن ساختار را تشکیل می‌دهند، کوپل شود.

بنابراین، مشتری نمی داند که آیا با یک شکل ساده کار می کند یا یک شکل مرکب. مشتری می‌تواند با ساختارهای شی بسیار پیچیده کار کند، بدون اینکه به کلاس‌های منسجمی که آن ساختار را تشکیل می‌دهند، کوپل شده باشد.
‍‍‍‍‍‍
```c++
// The component interface declares common operations for both
// simple and complex objects of a composition.
interface Graphic is
    method move(x, y)
    method draw()
// The leaf class represents end objects of a composition. A
// leaf object can't have any sub-objects. Usually, it's leaf
// objects that do the actual work, while composite objects only
// delegate to their sub-components.
class Dot implements Graphic is
    field x, y

    constructor Dot(x, y) { ... }

    method move(x, y) is
      this.x += x, this.y += y

    method draw() is
      // Draw a dot at X and Y.

// All component classes can extend other components.
class Circle extends Dot is
  field radius
  constructor Circle(x, y, radius) { ... }

method draw() is
  // Draw a circle at X and Y with radius R.

// The composite class represents complex components that may
// have children. Composite objects usually delegate the actual
// work to their children and then "sum up" the result.
class CompoundGraphic implements Graphic is
  field children: array of Graphic

  // A composite object can add or remove other components
  // (both simple or complex) to or from its child list.
  method add(child: Graphic) is
    // Add a child to the array of children.

  method remove(child: Graphic) is
    // Remove a child from the array of children.

  method move(x, y) is
    foreach (child in children) do
      child.move(x, y)

  // A composite executes its primary logic in a particular
  // way. It traverses recursively through all its children,
  // collecting and summing up their results. Since the
  // composite's children pass these calls to their own
  // children and so forth, the whole object tree is traversed
  // as a result.
  method draw() is
    // 1. For each child component:
    // - Draw the component.
    //  - Update the bounding rectangle.
    // 2. Draw a dashed rectangle using the bounding
    // coordinates.


// The client code works with all the components via their base
// interface. This way the client code can support simple leaf
// components as well as complex composites.
class ImageEditor is  
  field all: CompoundGraphic

  method load() is
    all = new CompoundGraphic()
    all.add(new Dot(1, 2))
    all.add(new Circle(5, 3, 10))
// ... 

// Combine selected components into one complex composite
// component.
method groupSelected(components: array of Graphic) is
  group = new CompoundGraphic()
  foreach (component in components) do
    group.add(component)
    all.remove(component)
all.add(group)
// All components will be drawn.
all.draw()
```

### 💡  قابلیت اجرا 
هنگامی که باید یک ساختار شی درخت مانند را پیاده سازی کنید از الگوی ترکیبی استفاده کنید.


✨ الگوی ترکیبی دو نوع عنصر اساسی را در اختیار شما قرار می دهد که یک رابط مشترک دارند: برگ های ساده و ظروف پیچیده. یک ظرف می تواند هم از برگ و هم از ظروف دیگر تشکیل شده باشد. این به شما امکان می دهد یک ساختار شی بازگشتی تودرتو که شبیه یک درخت است بسازید.

زمانی که می‌خواهید کد کلاینت هر دو عنصر ساده و پیچیده را به طور یکسان رفتار کند، از الگو استفاده کنید

✨ همه عناصر تعریف شده توسط الگوی ترکیبی یک رابط مشترک دارند. با استفاده از این رابط، کلاینت نیازی به نگرانی در مورد کلاس منسجم اشیایی که با آنها کار می کند، نخواهد بود

 ### 📋  چگونه پیاده سازی کنیم؟
1.مطمئن شوید که مدل اصلی برنامه شما می تواند به عنوان یک ساختار درختی نمایش داده شود. سعی کنید آن را به عناصر و ظروف ساده تقسیم کنید. به یاد داشته باشید که ظروف باید بتوانند هم عناصر ساده و هم سایر ظروف را در خود داشته باشند.

2.رابط کامپوننت را با لیستی از روش هایی که برای اجزای ساده و پیچیده معنادار است، اعلام کنید.

3.یک کلاس برگ برای نمایش عناصر ساده ایجاد کنید. یک برنامه ممکن است چندین کلاس برگ مختلف داشته باشد.

4.یک کلاس کانتینر برای نمایش عناصر پیچیده ایجاد کنید. در این کلاس، یک فیلد آرایه برای ذخیره ارجاعات به عناصر فرعی ارائه دهید. آرایه باید هم برگ و هم ظرف را ذخیره کند، بنابراین مطمئن شوید که با نوع رابط کامپوننت اعلام شده است.

هنگام پیاده‌سازی روش‌های رابط مؤلفه، به یاد داشته باشید که یک کانتینر قرار است بیشتر کار را به عناصر فرعی واگذار کند.
5. در نهایت روش های افزودن و حذف عناصر فرزند در ظرف را تعریف کنید.

به خاطر داشته باشید که این عملیات را می توان در رابط کامپوننت اعلام کرد. این امر اصل جداسازی رابط را نقض می کند زیرا متدها در کلاس برگ خالی خواهند بود. با این حال، مشتری قادر خواهد بود با همه عناصر به طور مساوی رفتار کند، حتی در هنگام ترکیب درخت

 ### ⚖️    سود و ضررها ؟
 ✔️ می توانید راحت تر با ساختارهای درختی پیچیده کار کنید: از چندشکلی و بازگشت به نفع خود استفاده کنید.

 ✔️ اصل باز/بسته شما می توانید انواع عناصر جدید را بدون شکستن کد موجود وارد برنامه کنید، که اکنون با درخت شی کار می کند..
 
 ✖️ ممکن است ارائه یک رابط مشترک برای کلاس هایی که عملکرد آنها بسیار متفاوت است دشوار باشد. در سناریوهای خاص، باید رابط مؤلفه را بیش از حد تعمیم دهید و درک آن را سخت‌تر کنید.

### 🔄  ارتباط با سایر الگو ها 

•  می‌توانید هنگام ایجاد درخت‌های **کامپوزیت** پیچیده از ‍**Builder** استفاده کنید زیرا می‌توانید مراحل ساخت آن را طوری برنامه‌ریزی کنید که به صورت بازگشتی کار کند.

• اغلب **Chain of Resposibility** 
 همراه با کامپوزیت استفاده می شود. در این حالت، هنگامی که یک جزء برگ درخواستی دریافت می کند، ممکن است آن را از طریق زنجیره تمام اجزای والد به ریشه درخت شی منتقل کند.

• شما می توانید از **Iterators** برای پیمایش از درختان **کامپوزیت** استفاده کنید

• می توانید از **Visitor** برای اجرای یک عملیات روی کل درخت **کامپوزیت** استفاده کنید.

 • می توانید گره های مشترک درخت **کامپوزیت** را به عنوان **Flyweights** پیاده سازی کنید تا مقداری RAM ذخیره کنید.

• **کامپوزیت** و **دکوریتور** نمودارهای ساختاری مشابهی دارند زیرا هر دو به ترکیب بازگشتی برای سازماندهی تعداد اشیا متکی هستند.

• دکوریتور مانند کامپوزیت است اما فقط یک جزء فرزند دارد. یک تفاوت مهم دیگر هم دکوریتور مسئولیت های بیشتری را به شی پیچیده اضافه می کند، در حالی که کامپوزیت فقط نتایج فرزندان خود را "خلاصه" می کند.

اگرچه ، الگوها می توانند با هم استفاده شوند: می توانید از دکوریتور برای گسترش رفتار یک شی خاص در درخت ترکیبی استفاده کنید.

طرح هایی که به شدت از کامپوزیت و دکوریتور استفاده می کنند اغلب می توانند از نمونه اولیه بهره ببرند. اعمال الگو به شما این امکان را می دهد که ساختارهای پیچیده را به جای بازسازی مجدد از ابتدا شبیه سازی کنید.