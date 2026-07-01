<div dir="rtl">
## مقدمه
`"راست"` (`Rust`) یک زبان جدید هست که کتاب های آموزشی خوبی هم داره، اما گاهی اوقات خوندن اونها سخت هست، بدلیل اینکه اکثرا برای کسانی که انگلیسی زبان اولشون هست نوشته شده‌اند.

این کتاب سعی میکنه زبان `Rust` رو به شیوا ترین شکل ممکن اموزش بده.

"راست" زبانی کاملا جدید است‌‌،با این حال در حال حاضر خیلی محبوب شده، دلیلش این هست که سرعت و کنترلی مثل زبان های `C/CPP` رو میده و همچنین امنیت حافظه‌(`Memory Safety`) زبان های سطح بالا داره. `Rust` این کار های را با چند ایده‌ی جدید انجام میده که گاهی با روش های زبان های دیگه متفاوت هست، این یعنی چیز های جدیدی برای یادگیری وجود داره.
`Rust` زبانی هست که برای درک مفاهیم اون باید کمی در مورد اونها فکر کنید.
اما اگر قبلا تجربه کار با زبانی که برای "کد خوب نوشتن" ساخته شده، دارید، احتمالا مشکلی نخواهید داشت.

## فهرست

- [Part 1 - Rust in your browser](#part-1---rust-in-your-browser)
  - [Rust Playground](#rust-playground)
  - [🚧 and ⚠️](#-and-️)
  - [Comments](#comments)
  - [Types](#types)
    - [Primitive types](#primitive-types)
  - [Type inference](#type-inference)
    - [Floats](#floats)
  - [Printing 'hello, world!'](#printing-hello-world)
    - [Declaring variables and code blocks](#declaring-variables-and-code-blocks)
  - [Display and debug](#display-and-debug)
    - [Smallest and largest numbers](#smallest-and-largest-numbers)
  - [Mutability (changing)](#mutability-changing)
    - [Shadowing](#shadowing)
  - [The stack, the heap, and pointers](#the-stack-the-heap-and-pointers)
  - [More about printing](#more-about-printing)
  - [Strings](#strings)
  - [const and static](#const-and-static)
  - [More on references](#more-on-references)
  - [Mutable references](#mutable-references)
    - [Shadowing again](#shadowing-again)
  - [Giving references to functions](#giving-references-to-functions)
  - [Copy types](#copy-types)
    - [Variables without values](#variables-without-values)
  - [Collection types](#collection-types)
    - [Arrays](#arrays)
  - [Vectors](#vectors)
  - [Tuples](#tuples)
  - [Control flow](#control-flow)
  - [Structs](#structs)
  - [Enums](#enums)
    - [Enums to use multiple types](#enums-to-use-multiple-types)
  - [Loops](#loops)
  - [Implementing structs and enums](#implementing-structs-and-enums)
  - [Destructuring](#destructuring)
  - [References and the dot operator](#references-and-the-dot-operator)
  - [Generics](#generics)
  - [Option and Result](#option-and-result)
    - [Option](#option)
    - [Result](#result)
  - [Other collections](#other-collections)
    - [HashMap (and BTreeMap)](#hashmap-and-btreemap)
    - [HashSet and BTreeSet](#hashset-and-btreeset)
    - [BinaryHeap](#binaryheap)
    - [VecDeque](#vecdeque)
  - [The ? operator](#the--operator)
    - [When panic and unwrap are good](#when-panic-and-unwrap-are-good)
  - [Traits](#traits)
    - [The From trait](#the-from-trait)
    - [Taking a String and a &str in a function](#taking-a-string-and-a-str-in-a-function)
  - [Chaining methods](#chaining-methods)
  - [Iterators](#iterators)
    - [How an iterator works](#how-an-iterator-works)
  - [Closures](#closures)
    - [|_| in a closure](#_-in-a-closure)
    - [Helpful methods for closures and iterators](#helpful-methods-for-closures-and-iterators)
  - [The dbg! macro and .inspect](#the-dbg-macro-and-inspect)
  - [Types of &str](#types-of-str)
  - [Lifetimes](#lifetimes)
  - [Interior mutability](#interior-mutability)
    - [Cell](#cell)
    - [RefCell](#refcell)
    - [Mutex](#mutex)
    - [RwLock](#rwlock)
  - [Cow](#cow)
  - [Type aliases](#type-aliases)
    - [Importing and renaming inside a function](#importing-and-renaming-inside-a-function)
  - [The todo! macro](#the-todo-macro)
  - [Rc](#rc)
  - [Multiple threads](#multiple-threads)
  - [Closures in functions](#closures-in-functions)
  - [impl Trait](#impl-trait)
  - [Arc](#arc)
  - [Channels](#channels)
  - [Reading Rust documentation](#reading-rust-documentation)
    - [assert_eq!](#assert_eq)
    - [Searching](#searching)
    - [[src] button](#src-button)
    - [Information on traits](#information-on-traits)
  - [Attributes](#attributes)
  - [Box](#box)
  - [Box around traits](#box-around-traits)
  - [Default and the builder pattern](#default-and-the-builder-pattern)
  - [Deref and DerefMut](#deref-and-derefmut)
  - [Crates and modules](#crates-and-modules)
  - [Testing](#testing)
    - [Test-driven development](#test-driven-development)
  - [External crates](#external-crates)
    - [rand](#rand)
    - [rayon](#rayon)
    - [serde](#serde)
    - [regex](#regex)
    - [chrono](#chrono)
  - [A tour of the standard library](#a-tour-of-the-standard-library)
    - [Arrays](#arrays-1)
    - [char](#char)
    - [Integers](#integers)
    - [Floats](#floats)
    - [Bool](#bool)
    - [Vec](#vec)
    - [String](#string)
    - [OsString and CString](#osstring-and-cstring)
    - [Mem](#mem)
    - [Prelude](#prelude)
    - [Time](#time)
    - [Other-macros](#other-macros)
  - [Writing macros](#writing-macros)
- [Part 2 - Rust on your computer](#part-2---rust-on-your-computer)
  - [Cargo](#cargo)
  - [Taking_user_input](#taking-user-input)
  - [Using files](#using-files)
  - [Cargo doc](#cargo-doc)
  - [The end?](#the-end)
  - [Credits](#credits)


# Part 1 - Rust in your browser

این کتاب دو بخش داره:

در بخش اول هر چقدر که میشه `Rust` رو توی مرورگر یاد میگیریم. میتونیم خیلی چیزها رو رو بدون نصب کردن `Rust` یاد بگیریم. پس بخش اول طولانی هست.

در بخش  دوم که کار هایی رو انجام میدیم که بدون نصب کردن `Rust` امکانش رو نداریم، برای مثال:
کار با فایل ها، تعامل با کاربر، تنظیمات شخصی و...

پس بخش دوم کوتاه تر هست :)

## Rust Playground

شاید نخواید فعلا `Rust` رو نصب کنید، مشکلی نیست. میتونید به این لینک ([https://play.rust-lang.org](https://play.rust-lang.org/)) برید و کد `Rust` بنویسید و اجرا کنید، تقریبا اکثر تمرین هایی که در این کتاب هست رو میتونید در مرورگر اجرا کنید و نتیجه‌اش رو ببینید.

یکسری نکات در مورد زمین بازی `Rust`:

\- با `Run` میتونید کدتون رو اجرا کنید.

\- دو حالت برای کامپایل کردن کد وجود داره:

&emsp;-> در حالت `Debug`، کد سریع کامپایل میشه اما کند اجرا میشه. (در مقایسه با حالت `Release`)

&emsp;-> در حالت `Release`، کد کند کامپایل میشه اما سریع اجرا میشه. (در مقایسه با حالت `Debug`)

\- با کلیک بر روی `Share`  میتونید `URL` کدی که نوشتید را دریافت کنید و اون رو با دیگران به اشتراک بزارید.

\- ابزار ها:

&emsp;-> ابزار، `Rustfmt` فرمت به کد میده و تمیز و مرتبش میکنه.

&emsp;-> ابزار، `Clippy` اطلاعات و جزئیاتی در مورد کد میده.

\- گزینه‌ی `Config` هم برای تنظیم کردن محیط به کار میره.

### اگر میخواهید `Rust` رو نصب کنید، این لینک ([https://www.rust-lang.org/tools/install](https://www.rust-lang.org/tools/install)) رو دنبال کنید. به طور معمول باید از `rustup` برای نصب `Rust` استفاده کنید

## 🚧 and ⚠️

در این کتاب در بعضی مواقع با کد هایی روبرو میشیم که کار نمیکنند، یعنی کامپایل نمیشند. اون کد ها همیشه علامت 🚧 یا ⚠️ رو دارند.

علامت 🚧 به معنای این هست که کد کامل نیست.

علامت ⚠️ به معنای این هست که کد و کامپایل نمیشود.

زبان `Rust` برای اجرای کد ها نیاز به `fn main()` (تابع اصلی) دارد، گاهی در این کتاب فقط تکه کد هایی را میبینیم که درون `fn main()` نیستند. آن کد ها مشکلی ندارند و کار میکنند، فقط نیاز دارند درون `fn main()` باشند.

## Comments

کامنت ها متن هایی هستند که به برنامه‌نویس‌ها کمک میکنند کد را بهتر و سریعتر درک کنند.
همچنین کمک میکنند در آینده کدتون رو بهتر بفهمید. (خیلی‌ها کد خوبی مینویسند اما بعد فراموش میکنند که اصلا چی نوشتند !)

برای کامنت نوشتن در `Rust` معمولا از `//` استفاده میکنیم.

```rust
fn main() {
    // Rust programs start with fn main()
    // You put the code inside a block. It starts with { and ends with }
    let some_number = 100; // We can write as much as we want here and the compiler won't look at it
}
```

کامپایلر با دیدن `//` میفهمه که قراره یک خط کامنت نوشته بشه، و به طور کلی خط رو نادیده میگیره چون کامنت ها به برنامه‌نویس ها کمک میکنند و کامپیوتر نیازی به اونها نداره.

یک نوع دیگه کامنت هم هست که با `/*` شروع میشه و با `*/` تموم میشه، این نوع کامنت ها برای نوشتن بین کد ها کاربرد دارند.

```rust
fn main() {
    let some_number/*: i16*/ = 100;
}
```

برای کامپایلر, `;let some_number/*: i16*/ = 100` میشه `;let some_number = 100`.

همچنین این روش کامنت گذاری برای زمان هایی که نیاز به نوشتن کامنت هایی چند خطی  هست، کاربردی هست.
در مثال زیر ما میتونستیم برای هم خط از `//`  استفاده کنیم, اما اینطوری بهتره :)

کامپایلر زمانی که `/*` رو میبینه هرچیزی که بعدش باشه رو نادیده میگیره تا زمانی که به `*/` برسه، اونوقت میفهمه که کامنت تموم شده.

```rust
fn main() {
    let some_number = 100; /* Let me tell you
    a little about this number.
    It's 100, which is my favourite number.
    It's called some_number but actually I think that... */

    let some_number = 100; // Let me tell you
    // a little about this number.
    // It's 100, which is my favourite number.
    // It's called some_number but actually I think that...
}
```

## Types

زبان `Rust` نوع های زیادی داده که با اون ها میتونیم با اعداد، کاراکترها، و... کار کنیم. بعضی ها ساده هستند و بعضی ها پیچیده، شما حتی میتونید نوع خودتونم بسازید. (اره شما هم که اصلا نمیدونستید struct چیه !)

### Primitive types

زبان `Rust` نوع های ساده‌ای داره که بهشون میگیم **`primitive types` (نوع های اولیه)**.

با نوع `integer` (عدد صحیح) و `char` (کاراکتر) شروع میکنیم.

دو نوع کلی `integer` وجود داره :

\* اول از همه بزارید بفهمیم علامت چی هست ! ما به طور کلی دو علامت برای اعداد داریم، `+` و `-` که منفی یا مثبت بودن یک عدد رو نشون میدن.

- Unsigned (بدون علامت)

مقداری که میخواد در این نوع ذخیره بشه **نباید** علامت داشته باشه، **یعنی فقط اعداد مثبت درون این نوع ذخیره میشند**.
- Signed (علامت دار)

مقداری که میخواد در این نوع ذخیره بشه میتونه علامت داشته، **یعنی میتونه مثبت یا منفی باشه**.


نوع های `Signed integer` اینها هستند: `i8`, `i16`, `i32`, `i64`, `i128`, and `isize`.

نوع های `Unsigned integer` اینها هستند: `u8`, `u16`, `u32`, `u64`, `u128`, and `usize`.

عدد بعد از حرف `i` یا `u` میزان فضایی که اون نوع اشغال میکنه رو بر حسب بیت(`bit`) نشون میده.

هرچه میزان فضای اشغال شده بیشتر باشد، آن متغییر میتواند عدد بزرگ‌تری را در حافظه نگهداری کند.

برای مثال :

نوع `u8` میتواند اعداد بین بازه‌ی `0` تا `255` را نگهداری کند.

نوع `u16` میتواند اعداد بین بازه‌ی `0` تا `65535` را نگهداری کند.

نوع `u128` میتواند اعداد بین بازه‌ی `0` تا `340282366920938463463374607431768211455` را نگهداری کند.

نوع `i8` میتواند اعداد بین بازه‌ی `128-` تا `127` را نگهداری کند.

نوع `i16` میتواند اعداد بین بازه‌ی `32768-` تا `32767` را نگهداری کند.

نوع `i128` میتواند اعداد بین بازه‌ی `170141183460469231731687303715884105728-` تا `170141183460469231731687303715884105727` را نگهداری کند.

### خب فهمیدیم `Signed` و `Unsigned` چیه ! حالا این `isize` و `usize` جی هستند؟

خب، حرف `` و `` اولشون که مشخص هست که `Signed` و `Unsigned` بودن رو مشخص میکنند اما این ها چه مقدار فضا از حافظه اشغال میکنند ؟!

خب اون بستگی به **معماری** سیستم عاملی که برنامه روش اجرا میشه داره، برای مثال:

در یک سیستم x64:

`isize` -> `i64`

`usize` -> `u64`

در یک سیستم x32:

`isize` -> `i32`

`usize` -> `u32`

### خب چرا باید سایز رو خودمون مشخص کنیم و به طور کل چرا سایز های مختلفی وجود دارند؟

خب برنامه هایی که ما مینویسیم با داده ها سروکار دارند و داده ها باید ذخیره و پردازش بشند، این دو عمل، منابع محدود سیستم رو مصرف میکنند، پس به عنوان برنامه‌نویس باید در مصرف منابع سیستم تا جایی که میتونیم صرفه‌جویی کنیم، یکی از مزیت های `Rust` این است که قابلیت این کار را به برنامه‌نویس میدهد.

جواب سرراست نبود؟

<div dir="rtl">
خب به دو نکته توجه کنید:

- منابع برای ذخیره سازی داده در یک سیستم محدود هست

- هر چه داده سایز داده کمتر باشه، پردازش اون آسون‌تر هست

با توحه به دو نکته بالا، بیاید فکر کنیم که نیاز داریم عدد `10-` رو ذخیره کنیم و بعد هم روش پردازشی انجام بدیم، در این نقطه باید تصمیم بگیریم که برای دخیره این داده چه نوع و سایزی انتخاب کنیم.

خب این داده یک عدد صحیح هست، پس باید `Integer` انتخاب کنیم. اما دو نکته دیگر هم وجود دارد، اولا این `Integer` باید `Signed` باشد یا `Unsigned` و دوما اینکه چه سایزی باید داشته باشد؟!

خب این عدد منفی است‌، به معنای دیگر یغنی علامت‌دار(`Signed`) است، پس باید اون رو باید در یک نوع `Signed` ذخیره کرد.

و اما چه سایزی برای این مقدار مناسب هست، عدد کوچیکی است پس باید هشت بیت برایش کافی باشد.

خب همه این اطلاعاتی که میدونستید رو گفتم که به این اشاره کنم که اهمیت سایز میتونه چقدر در کارایی برنامه تآثیرگذار باشد.

اگر همین مقدار کوچک را در یک نوع `i8` ذخیره کنیم چنین فضایی را اشغال خواهد کرد:

`11110110`

اما اگر همین مقدار را در یک نوع `i128` ذخیره کنیم، چنین فضایی را در حافظه اشغال خواهد کرد:
`11111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111110110`

اون دو نکته‌ای که گفته بودم رو یادتون هست؟
ایناهاش :

- منابع برای ذخیره سازی داده در یک سیستم محدود هست

- هر چه داده سایز داده کمتر باشه، پردازش اون اسون‌تر هست

خب فکر کنم الان واضح هست که انتخاب کدوم نوع میتونه باید بشه که ما در مصرف منابع سیستم صرفه کنیم؟
(اگه حواست نبود باید بگم که `i8` جواب بود!)


### خب برسیم به نوع `char`، در `Rust` کاراکتر ها در نوع `char` ذخیره میشوند.
هر `char` برابر یک عدد است، برای مثال:

کاراکتر `A` برابر عدد `65` است.

و میگن کاراکتر `友` هم برابر با عدد `21451` است. (مثل اینکه این کاراکتر در چینی یعنی **دوست** !)


و خب این یعنی `Rust` به صورت پیشفرض از `Unicode` برای نمایش کاراکتر ها استفاده میکنه.
</div>

```rust
fn main() {
    let first_letter = 'A';
    let space = ' '; // A space inside ' ' is also a char
    let other_language_char = 'Ꮔ'; // Thanks to Unicode, other languages like Cherokee display just fine too
    let cat_face = '😺'; // Emojis are chars too
}
```
کاراکتر های مرسوم شماره هایی کمتر از `256` دارند، و به همین دلیل میتوانند در نوع `u8` ذخیره شوند. اگر یادتون باشه `u8` بازه‌ای از `0` تا `256` رو پوشش میداد. پس `Rust` میتونه به راحتی یک `u8` رو به یک `char` تبدیل کنه.

با استفاده از کلمه‌کلیدی `as` میتونیم یک نوع رو به یک نوع دیگه تبدیل کنیم،‌ البته اگه امکانش وجود داشته باشه. تبدیل با استفاده از `as` کاربردی هست به این دلیل که راست خیلی سخت‌گیر است و به همین دلیل میتونه ایمنی رو رعایت کنه.
همچنین `Rust` برای تبدیل با استفاده از `as` همیشه باید نوع متغییر هارو به درستی بدونه. به همین دلیل کد زیر کامپایل نمیشه:

```rust
fn main() { // main() is where Rust programs start to run. Code goes inside {} (curly brackets)

    let my_number = 100; // We didn't write a type of integer,
                         // so Rust chooses i32. Rust always
                         // chooses i32 for integers if you don't
                         // tell it to use a different type

    println!("{}", my_number as char); // ⚠️
}
```

دلیلش رو میتونید در پیغام خطایی که کامپایلر داده ببینید:
```text
error[E0604]: only `u8` can be cast as `char`, not `i32`
 --> src\main.rs:3:20
  |
3 |     println!("{}", my_number as char);
  |                    ^^^^^^^^^^^^^^^^^
```
همونطور که میبینید کامپایلر میگه که نمیتونم یک `i32` رو به `char` تبدیل کنم و فقط میتونم `u8` رو به `char` تبدیل کنم. دلیلش این هست که امکان این وجود داره که مقداری که درون `i32 ` ذخیره شده برابر یک کاراکتری نباشه.
برای مثال ما میتونیم مقدار `666-` رو در یک `i32` ذخیره کنیم اما هیچ کاراکتری با این مقدار وجود نداره، پس کامپایلر نمیتونه اون مقدار رو به کاراکتر تبدیل کنه.

اما خوشبختانه ما میتونیم این مشکل رو جل کنیم، به این صورت که اول `i32` رو به `u8` تبدیل میکنیم و بعد، `u8` رو به `char` تبدیل میکنیم.

```rust
fn main() {
    let my_number = 100;
    println!("{}", my_number as u8 as char);
}
```

الان کاراکتر `d` رو چاپ میکنه به این دلیل که کاراکتر `d` برابر عدد `100` هست.

البته روش اسون ترش این هست که در هنگام تعریف متغییر به کامپایلر بگیم این متغییر نوعش `u8` هست.(در غیر این صورت همانطور که دیدیم، کامپایلر به طور پیشفرض مقدار هر عدد صحیحی که نوعش مشخص نباشه رو `i32` در نظر میگیره)

```rust
fn main() {
    let my_number: u8 = 100; //  change my_number to my_number: u8
    println!("{}", my_number as char);
}
```
<div dir="rtl">


زبان `Rust` نوع `usize` رو برای *`indexing`* استفاده میکنه.(`indexing` یعنی کدوم ایتم اول هست، کدوم دوم و ...)

به دلایل زیر، برای اینکار نوع `usize` بهترین انتخاب هست: 

- یک `index` نمیتونه مقدار منفی داشته باشه، پس باید `Unsigned` باشه.
- باید بتونه مقدار های بزرگ رو در خودش نگه داره، چون امکان داره چیز های زیادی رو `index` کنیم. **اما**
- نوعش نمیتونه `u64` باشه، به این دلیل که سیستم های x32 نمیتونند از `u64` استفاده کنند

پس `Rust` از `usize` استفاده میکنه که سیستم بتونه بزرگ ترین عددی که میتونه استفاده کنه رو برای `indexing` استفاده کنه.

### بیاید کمی بیشتر در مورد `char` یاد بگیریم.
دیدید که `char` همیشه یک کاراکتر هست ، هنگام تعریف به جای `""` از `''` استفاده میکنیم.


نوع `char` همیشه `4` بایت هست (`32bit`)، به این دلیل که `4` بایت برای ذخیره‌ی هر نوع کاراکتری کافی هست.

- حروف پایه‌ای و سمبول‌ ها معمولا به `1` تا `4` بایت نیاز دارند: `a b 12 + - = $ @`
- باقی حروف مثل حروف خاص المانی به `2` تا `4` بایت نیاز دارند: `ä ö ü ß è é à ñ`
- حروف کره‌ای، ژاپنی یا چینی به `3` تا `4` بایت نیاز دارند: `国 안 녕`


هنگام استفاده از کاراکترها به عنوان بخشی از یک رشته(`String`)، رشته به گونه ای کدگذاری می شود که کمترین مقدار حافظه مورد نیاز برای هر کاراکتر را استفاده کنند.

با استفاده از `()len.` میتونیم سایز یک `String` رو بگیریم.
</div>

```rust
fn main() {
    println!("Size of a char: {}", std::mem::size_of::<char>()); // 4 bytes
    println!("Size of string containing 'a': {}", "a".len()); // .len() gives the size of the string in bytes
    println!("Size of string containing 'ß': {}", "ß".len());
    println!("Size of string containing '国': {}", "国".len());
    println!("Size of string containing '𓅱': {}", "𓅱".len());
}
```

خروجیش:

```text
Size of a char: 4
Size of string containing 'a': 1
Size of string containing 'ß': 2
Size of string containing '国': 3
Size of string containing '𓅱': 4
```

میتونید ببینید که `a` یک بایت هست، `ß` دو بایت هست، `国` سه بایت هست، و `𓅱` چهار بایت هست.

```rust
fn main() {
    let slice = "Hello!";
    println!("Slice is {} bytes.", slice.len());
    let slice2 = "안녕!"; // Korean for "hi"
    println!("Slice2 is {} bytes.", slice2.len());
}
```

خروجیش:

```text
Slice is 6 bytes.
Slice2 is 7 bytes.
```
متغییر `slice` شش کاراکتر هست و سایزش `6` بایت هست، **اما** ``slice2`` سه کاراکتر هست و سایزش `7` بایت هست.

خب اگه `()len.` سایز یک `String` رو به بایت میده، چطوری میتونیم بفهمیم یک سایز(طول کاراکترهاش چقدر هست ؟)

بعدا مفصل در مورد اینها صحبت میکنیم اما چون پرسیدی میگم. با استفاده از `.chars().count()` میتونیم طول تعدار کاراکتر های یک `String` رو بدست بیاریم.

```rust
fn main() {
    let slice = "Hello!";
    println!("Slice is {} bytes and also {} characters.", slice.len(), slice.chars().count());
    let slice2 = "안녕!";
    println!("Slice2 is {} bytes but only {} characters.", slice2.len(), slice2.chars().count());
}
```

خروجیش:

```text
Slice is 6 bytes and also 6 characters.
Slice2 is 7 bytes but only 3 characters.
```

## Type inference

استنتاج نوع یعنی شما میتونید نوع یک متغییر رو مشخص نکنید، اما کامپیایلر اون رو بر اساس مقدارش انتخاب کنه. کامپایلر برای کامپایل کد همیشه لازم داره نوع هم متغییر رو بدونه، اما همیشه لازم نیست به طور مشخص برنامه‌نویس نوع رو مشخص کنه، معمولا هم برنامه‌نویس همیشه نوع رو مشخص نمیکنه و از قابلیت استنتاج نوع استفاده میکنه.برای مثال در کد `;let number = 8`، نوع متغییر `number` میشه `i32`. این به دلیل این اتفاق میوفته که کامپایلر این نوع رو انتخاب میکنه.اما در کد `;let number: u8 = 8`، همیشه نوع متغییر `number` یک `u8` هست. چون ما مشخص کردیم که `u8` باشه.

<div dir="rtl">
پس معمولا کامپایلر میتونه نوع متغییر رو انتخاب کنه، اما بعضی وقت ها به دلایل زیر لازم هست که برنامه‌نویس نوع رو مشخص کنه:

- زمانی که داریم یک عمل پیچیده انجام میدیم که کامپایلر نمیتونه نوع رو مشخص کنه

- زمانی که یک نوع دیگه به غیر از نوعی که کامپایلر مشخص میکنه رو لازم دارید، مثلا `i128` و نه `i32`

برای مشخص کردن نوع یک متغییر باید یک `:` بعد از اسم متغییر بزارید و بعد نوع رو بنویسیم.

</div>

```rust
fn main() {
    let small_number: u8 = 10;
}
```
برای مشخص کردن نوع اعداد میتونیم نوع رو بعد از مقدار هم بنویسیم.

```rust
fn main() {
    let small_number = 10u8; // 10u8 = 10 of type u8
}
```
همچنین برای اینکه عدد راحت خونده بشه میتونیم از `_` در بین اعداد استفاده کنیم.
```rust
fn main() {
    let small_number = 10_u8; // This is easier to read
    let big_number = 100_000_000_i32; // 100 million is easy to read with _
}
```

استفاده از `_`، عدد رو تغییر نمیده و فقط برای راحت‌تر خونده شدن عدد استفاده میشه و همچنین مهم نیست که از چند‌تا `_` استفاده میکنیم.

```rust
fn main() {
    let number = 0________u8;
    let number2 = 1___6______2____4______i32;
    println!("{}, {}", number, number2);
}
```

کد بالا مقدار `0, 1624` رو چاپ میکنه.

### Floats
نوع `Float` برای نگهداری اعداد اعشاری/ممیز‌دار استفاده میشه. برای مثال `5.5` یک `Float` هست. `6` یک `Integer` و `6.0` یک `Float` و همچنین حتی `6.` هم یک `Float` هست.

```rust
fn main() {
    let my_float = 5.; // Rust sees . and knows that it is a float
}
```
در `Rust`، دو نوع `Float` داریم: `f32` و `f64`

مثل `Integer` ها عدد بعد از `f` تعداد بیت هایی که نوع میتونه نگهداری کنه رو مشخص میکنه. و همچنین اگر نوع رو مشخص نکنید کامپایلر به طور پیشفرض از `f64` استفاده میکنه.

یک نکته این هست که، `Rust` به طور پیشفرض اجازه نمیده نوع های غیر همسان در کنار هم استفاده بشند. پس نمیتونیم یک `f32` رو با `f64` جمع بزنیم.


```rust
fn main() {
    let my_float: f64 = 5.0; // This is an f64
    let my_other_float: f32 = 8.5; // This is an f32

    let third_float = my_float + my_other_float; // ⚠️
}
```
وقتی سعی بر اینکار کنید، `Rust` چنین چیزی میگه:

```text
error[E0308]: mismatched types
 --> src\main.rs:5:34
  |
5 |     let third_float = my_float + my_other_float;
  |                                  ^^^^^^^^^^^^^^ expected `f64`, found `f32`
```
کامپایلر میگه که `expected 'f64', found 'f32'` (`من فلان نوع رو انتظار داشتم، اما فلان نوع رو گرفتم`)


```rust
fn main() {
    let my_float: f64 = 5.0; // The compiler sees an f64
    let my_other_float: f32 = 8.5; // The compiler sees an f32. It is a different type.
    let third_float = my_float + // You want to add my_float to something, so it must be an f64 plus another f64. Now it expects an f64...
    let third_float = my_float + my_other_float;  // ⚠️ but it found an f32. It can't add them.
}
```
پس وقتی کامپایلر میگه که `"expected (type), found (type)"` (`من فلان نوع رو انتظار داشتم، اما فلان نوع رو گرفتم`). میتونیم بفهمیم که مشکل از نوع ها هست و کامپایلر فلان رو انتظار داشت اما فلان رو بهش دادیم.

البته در مورد که در مورد `Integer` ها هست راحت میشه درستش کرد، با استفاده از `as` میتونیم نوع `f32` رو به یک `f64` تبدیل کنیم:

```rust
fn main() {
    let my_float: f64 = 5.0;
    let my_other_float: f32 = 8.5;

    let third_float = my_float + my_other_float as f64; // my_other_float as f64 = use my_other_float like an f64
}
```

یا حتی از قابلیت استنتاج نوع (اره واقعا اسم غریبیه) استفاده کنیم. پس `Rust` (بهتره بگیم کامپایلر) نوع هر دو متغییر رو `f64` مشخص میکنه و خب پس هر دو یک عدد هستند و مشکلی برای استفاده اونها کنار هم دیگه نداریم.

```rust
fn main() {
    let my_float = 5.0; // Rust will choose f64
    let my_other_float = 8.5; // Here again it will choose f64

    let third_float = my_float + my_other_float;
}
```
کامپایلر `Rust` باهوش هست و زمانی که `f32` لازم هست از `f64` استفاده نمیکنه:

```rust
fn main() {
    let my_float: f32 = 5.0;
    let my_other_float = 8.5; // Usually Rust would choose f64,

    let third_float = my_float + my_other_float; // but now it knows that you need to add it to an f32. So it chooses f32 for my_other_float too
}
```

## Printing 'hello, world!'

وقتی یک پروژه‌ی جدید با استفاده از `cargo` شروع میکنید همیشه این کد درش هست.

بعدا میبینیم `cargo` چی هست، فعلا بدونید که یک `package manager` هست. یه چیزی مثل `pip` در `python`.

```rust
fn main() {
    println!("Hello, world!");
}
```
<div dir="rtl">


- `fn` یعنی میخوام یک فانکشن بسازم,
- `main` اسم فانکشنی هست که برنامه از اونجا شروع میشه,
- `()` یعنی این فانکشن برای اجرا به ورودی نیاز نداره.

`{}` یک  **`code block`** ایجاد میکنه. این فضایی هست که کد درش قرار میگیره.

`println!` یک ماکرو(**`macro`**) هست که چیزی رو توی `stdout` چاپ میکنه. یک **`macro`** مثل یک فانکشن هست. ماکرو ها یک `!` بعد از اسمشون دارند، بعدا در مورد ماکرو بیشتر میخونیم، اما فعلا یادتون باشه که `!` نشون میده که ما در حال اجرای یک ماکرو هستیم.


در ادامه کمی در مورد `";"` یاد میگیریم، اما فعلا بزارید یکم روی چاپ تمرکز کنیم و عدد `8` رو با متن دلخواه چاپ کنیم:

</div>

```rust
fn main() {
    println!("Hello, world number {}!", 8);
}
```
<div dir="rtl">

علامت `{}` در `println!` یه این معنی هست که "متغییر رو بزار اینجا"، خروجی کد با این هست:

`Hello, world number 8!`


میتونیم هر چندتا چیز که میخواییم پرینت کنیم، همونطور که قبلا هم کردیم:

</div>

```rust
fn main() {
    println!("Hello, worlds number {} and {}!", 8, 9);
}
```

چنین چیزی رو پرینت میکنه:  `Hello, worlds number 8 and 9!`.

خب بیاید یک فانکشن درست کنیم:

```rust
fn number() -> i32 {
    8
}

fn main() {
    println!("Hello, world number {}!", number());
}
```

<div dir="rtl">


این کد هم همچنان `Hello, world number 8!` رو پرینت میکنه.

وقتی راست `()number` رو میبینه، میفهمه که یک فانکشن هست که:

- چیزی به عنوان ورودی **نمیگیره**

- یک `i32` به عنوان خروجی برمیگردونه. علامت `->` (بهش میگن "فلش لاغر") نشون میده که خروجی فانکشن چی هست

نکته، فانکشن ها همیشه خروجی دارند، حتی اگه یک فانکشن رو بدون خروجی هم تعریف کنیم باز هم یک `()` بر میگردونه. که این یعنی `()` به معنای هیچی هست.

توی فانکشن فقط مقدار `8` هست. به این دلیل که `;`‌ای وجود نداره این مقدار به عنوان خروجی برمیگرده. اگر `;` میزاشتیم چیزی به عنوان خروجی برنمیگردوند (بهتره بگیم یک `()` برمیگردوند). اما اگه `;` میزاشتیم `Rust` این کد رو کامپایل نمیکرد، به این دلیل که خروجی این فانکشن باید `i32` باشه اما اونوقت یک `()` بر میگردوند:

</div>

```rust
fn main() {
    println!("Hello, world number {}", number());
}

fn number() -> i32 {
    8;  // ⚠️
}
```

```text
5 | fn number() -> i32 {
  |    ------      ^^^ expected `i32`, found `()`
  |    |
  |    implicitly returns `()` as its body has no tail or `return` expression
6 |     8;
  |      - help: consider removing this semicolon
```
این خطا به این معنی هست که "تو به من گفتی که `()number` یک `i32` برمیگردونه اما `;` رو گذاشتی که باعث میشه این فانکشن `()` برگردونه"، پس کامپایلر پیشنهاد میکنه که `;` رو پاک کنیم.

دلیل اینکه این فانکشن `()` برمیگردونه این نیست که جلوی یک مقدار `;` گذاشتیم، بلکه دلیلش این هست که فانکشن تموم شده و هنوز چیزی به عنوان خروجی برنگردونده شده.

نکته اگه فانکشن تموم بشه و چیزی به عنوان خروجی برگردونده نشه، `()` به عنوان خروجی در نظر گرفته میشه.

### ما معمولا نمیگیم که یک فانکشن `()` برمیگردونه، بلکه میگیم فانکشن چیزی بر نمیگردونه اما خب اصولیش این هست که بگیم `()` برمیگردونه

اگه تجربه‌ی برنامه‌نویسی داشته باشید میدونید که برای برگردوندن یک خروجی از یک فانکشن از کلمه‌کلیدی `return` استفاده میکنیم.

پس چرا زمانی که `;` رو پاک میکنیم مقدار رو به عنوان خروجی برمیگردونه؟

دلیلش این هست که در `Rust` برای برگردوندن مقدار از فانکشن دو روش وجود داره:

- با استفاده از `return`

- و روش خلاصه‌تر این هست که مقدار رو بدون `;` بزاریم، مثل همونکاری که اول کردیم (رایج‌تر هست)

همچنین در روش استفاده از `return`، میتونیم `;return 8` رو بنویسیم، اما مرسوم‌تر هست که `;` رو پاک کنیم پس در نهایت بهتره از شیوه‌ی `return 8` استفاده کنیم.

وقتی میخوایم متغییری به فانکشنی بفرستیم باید درون قسمت `()` فانکشن اسم و نوع متغییر رو درخواستی رو مشخص کنیم.

```rust
fn multiply(number_one: i32, number_two: i32) { // Two i32s will enter the function. We will call them number_one and number_two.
    let result = number_one * number_two;
    println!("{} times {} is {}", number_one, number_two, result);
}

fn main() {
    multiply(8, 9); // We can give the numbers directly
    let some_number = 10; // Or we can declare two variables
    let some_other_number = 2;
    multiply(some_number, some_other_number); // and put them in the function
}
```
همچنین میتونیم خروجی هم داشته باشیم:
```rust
fn multiply(number_one: i32, number_two: i32) -> i32 {
    let result = number_one * number_two;
    println!("{} times {} is {}", number_one, number_two, result);
    result // this is the i32 that we return
}

fn main() {
    let multiply_result = multiply(8, 9); // We used multiply() to print and to give the result to multiply_result
}
```

### Declaring variables and code blocks

با استفاده از `let` میتونیم متغییر بسازیم:
```rust
fn main() {
    let my_number = 8;
    println!("Hello, number {}", my_number);
}
```
متغییر ها فقط درون بلوکی که تعریف میشند در دسترس هستند و به محض اتمام اون بلوک از بین میرند.

در مثال زیر، `my_number` در انتهای بلوکی که تعریف شده از بین میره و دیگه در دسترس نیست. به همین دلیل کد زیر کامپایل نمشه.

```rust
fn main() {
    {
        let my_number = 8; // my_number starts here
                           // my_number ends here!
    }

    println!("Hello, number {}", my_number); // ⚠️ there is no my_number and
                                             // println!() can't find it
}
```

ما میتونیم از یک بلوک کد مقداری رو هم برگردونیم:
```rust
fn main() {
    let my_number = {
    let second_number = 8;
        second_number + 9 // No semicolon, so the code block returns 8 + 9.
                          // It works just like a function
    };

    println!("My number is: {}", my_number);
}
```
اگه `;` رو به کد اضافه کنیم، اون بلاک چیزی بر نمیگردونه (البته ما میدونیم که `()` برمیگردونه)

```rust
fn main() {
    let my_number = {
    let second_number = 8; // declare second_number,
        second_number + 9; // add 9 to second_number
                           // but we didn't return it!
                           // second_number dies now
    };

    println!("My number is: {:?}", my_number); // my_number is ()
}
```
این چی بود؟ چرا برای چاپ متغییر از `{:?}` به جای `{}` استفاده کردیم؟ الان در موردش صحبت میکنیم...

## Display and debug

متغییر های ساده در `Rust` میتونند با استفاده از `{}` پرینت بشند، اما بعضی متغییر ها  هم هستند که باید به اصطلاح **`Debug Print`** بشند. **`Debug Print`** یه جورایی پرینت برای برنامه‌نویس ها هست، اطلاعات بیشتری نشون میده و به همین دلیل شاید خیلی تر و تمیز به نظر نیاد.

چطوری بفهمیم به `{:?}` نیاز داریم به جای `{}` ؟ خب کامپایلر بهت میگه ! برای مثال:

```rust
fn main() {
    let doesnt_print = ();
    println!("This will not print: {}", doesnt_print); // ⚠️
}
```

وقتی این کد رو اجرا میکنید، کامپایلر چنین چیزی میگه:

```text
error[E0277]: `()` doesn't implement `std::fmt::Display`
 --> src\main.rs:3:41
  |
3 |     println!("This will not print: {}", doesnt_print);
  |                                         ^^^^^^^^^^^^ `()` cannot be formatted with the default formatter
  |
  = help: the trait `std::fmt::Display` is not implemented for `()`
  = note: in format strings you may be able to use `{:?}` (or {:#?} for pretty-print) instead
  = note: required by `std::fmt::Display::fmt`
  = note: this error originates in a macro (in Nightly builds, run with -Z macro-backtrace for more info)
```

خب خیلی چیز گفت، اما بخش مهمش اونجاست که میگه `you may be able to use {:?} (or {:#?} for pretty-print) instead`.

خب این یعنی این که شما باید از `{:?}` یا `` یا `` استفاده کنید.

خب `:#?` چی هست ؟

این ها همون کار `{}` رو میکنند اما سعی میکنند کمی تر و تمیز‌تر به نظر بیان.

خب پس وقتی داریم از `{}` برای پرینت استفاده میکنیم داریم `Display` میکنیم و وقتی از `{:?}` یا `{:#?}` استفاده میکنیم داریم `Debug` میکنیم.

(البته منظورم `Display Printing` و `Debug Printing` هست)
خب پس `Display`، یعنی استفاده از `{}` برای پرینت و `Debug` یعنی استفاده از `{:?}` یا `{:#?}` برای پرینت.

یک نکته‌ی دیگه: میتونیم از `print!` به جای `println!` استفاده کنیم اگه نمیخوام بعد از چاپ بره سر خط:

```rust
fn main() {
    print!("This will not print a new line");
    println!(" so this will be on the same line");
}
```

این رو پرینت میکنه: `This will not print a new line so this will be on the same line`.

### Smallest and largest numbers

اگه میخوای کوچیک‌ترین و بزرگ‌ترین عددی که نوع های `Integer` میتونند نگهداری کنند رو ببینی، میتونی بعد از اسم نوع از `MIN` و `MAX` استفاده کنی:

```rust
fn main() {
    println!("The smallest i8 is {} and the biggest i8 is {}.", i8::MIN, i8::MAX); // hint: printing std::i8::MIN means "print MIN inside of the i8 section in the standard library"
    println!("The smallest u8 is {} and the biggest u8 is {}.", u8::MIN, u8::MAX);
    println!("The smallest i16 is {} and the biggest i16 is {}.", i16::MIN, i16::MAX);
    println!("The smallest u16 is {} and the biggest u16 is {}.", u16::MIN, u16::MAX);
    println!("The smallest i32 is {} and the biggest i32 is {}.", i32::MIN, i32::MAX);
    println!("The smallest u32 is {} and the biggest u32 is {}.", u32::MIN, u32::MAX);
    println!("The smallest i64 is {} and the biggest i64 is {}.", i64::MIN, i64::MAX);
    println!("The smallest u64 is {} and the biggest u64 is {}.", u64::MIN, u64::MAX);
    println!("The smallest i128 is {} and the biggest i128 is {}.", i128::MIN, i128::MAX);
    println!("The smallest u128 is {} and the biggest u128 is {}.", u128::MIN, u128::MAX);

}
```

چنین چیزی رو پرینت میکنه:

```text
The smallest i8 is -128 and the biggest i8 is 127.
The smallest u8 is 0 and the biggest u8 is 255.
The smallest i16 is -32768 and the biggest i16 is 32767.
The smallest u16 is 0 and the biggest u16 is 65535.
The smallest i32 is -2147483648 and the biggest i32 is 2147483647.
The smallest u32 is 0 and the biggest u32 is 4294967295.
The smallest i64 is -9223372036854775808 and the biggest i64 is 9223372036854775807.
The smallest u64 is 0 and the biggest u64 is 18446744073709551615.
The smallest i128 is -170141183460469231731687303715884105728 and the biggest i128 is 170141183460469231731687303715884105727.
The smallest u128 is 0 and the biggest u128 is 340282366920938463463374607431768211455.
```

## Mutability (changing)

وقتی یک متغییر با استفاده از `let` تعریف میکنی، به طور پیشفرض تغییر‌ناپذیر هست (مقدارش عوض نمیشه)

پس کد زیر کار نمیکنه:

```rust
fn main() {
    let my_number = 8;
    my_number = 10; // ⚠️
}
```

کامپایلر میگه: `error[E0384]: cannot assign twice to immutable variable my_number`.

اما بعضی وقت‌ها لازم داریم که متغییر تغییرپذیر باشه، برای اینکار میتونیم کلمه‌کلیدی ‌`mut` رو بعد از `let` بنویسیم:

```rust
fn main() {
    let mut my_number = 8;
    my_number = 10;
}
```

حالا برنامه کامپایل میشه.

اما همچنان نمیتونیم نوع یک متغییر رو عوض کنیم، حتی اضافه کردن `mut` هم این اجازه رو به ما نمیده. پس این کد کار نمیکنه:

```rust
fn main() {
    let mut my_variable = 8; // it is now an i32. That can't be changed
    my_variable = "Hello, world!"; // ⚠️
}
```
کامپایلر این خطا رو میده: `expected integer, found &str`

در مورد `&str` بعدا یاد میگیریم.

### Shadowing

سایه زدن (`Shadowing`) یعنی، با استفاده از `let` یک متغییر جدید بسازیم اما **همنام متغییری که وجود داره**. این عمل به نظر میاد شبیه به `Mutability` هست، **`اما کامل متفاوت هست`**.

قابلیت `Shadownig` چیزی شبیه به این هست:

```rust
fn main() {
    let my_number = 8; // This is an i32
    println!("{}", my_number); // prints 8
    let my_number = 9.2; // This is an f64 with the same name. But it's not the first my_number - it is completely different!
    println!("{}", my_number) // Prints 9.2
}
```
خب حالا متغییر `my_number` اولی نابود شده؟ **به هیچ وجه، فقط رفته زیر سایه‌ی `my_number` دومی**

چون این دو متغییر در یک بلوک هستند، `my_number` اولی غیرقابل دسترس هست و با صدا زدن اسمش به `my_number` دومی دسترسی پیدا میکنیم.

اما اگه در بلوک های مختلف باشند، به هر کدام در بلوک خودشان دسترسی داریم:

```rust
fn main() {
    let my_number = 8; // This is an i32
    println!("{}", my_number); // prints 8
    {
        let my_number = 9.2; // This is an f64. It is not my_number - it is completely different!
        println!("{}", my_number) // Prints 9.2
                                  // But the shadowed my_number only lives until here.
                                  // The first my_number is still alive!
    }
    println!("{}", my_number); // prints 8
}
```

پس وقتی یک متغییر رو سایه میزنید (خودتون میفهمید چی میگم)، اون رو از بین نمیبرید فقط غیرقابل دسترسیش میکنید، و از اون به بعد اسم اون متغییر به متغییر جدیدی که ساختید اشاره میکنه، البته تا زمانی که متغییر جدید نابود نشده، بعد از اینکه متغییر جدید همه چی به روال سابق بر میگرده.

خب حالا مزیت سایه زنی چی هست؟ وقتی خوبه که لازم دارید یک مقدار یک متغییر رو بار ها تغییر بدید، مثلا عملیات ریاضی انجام بدید باهاش:

```rust
fn times_two(number: i32) -> i32 {
    number * 2
}

fn main() {
    let final_number = {
        let y = 10;
        let x = 9; // x starts at 9
        let x = times_two(x); // shadow with new x: 18
        let x = x + y; // shadow with new x: 28
        x // return x: final_number is now the value of x
    };
    println!("The number is now: {}", final_number)
}
```

بدون `Shadowing` میتونست چیزی شبیه به این کد بشه:

```rust
fn times_two(number: i32) -> i32 {
    number * 2
}

fn main() {
    // Pretending we are using Rust without shadowing
    let final_number = {
        let y = 10;
        let x = 9; // x starts at 9
        let x_twice = times_two(x); // second name for x
        let x_twice_and_y = x_twice + y; // third name for x!
        x_twice_and_y // too bad we didn't have shadowing - we could have just used x
    };
    println!("The number is now: {}", final_number)
}
```

## The stack, the heap, and pointers

<div dir="rtl">
           
در `Rust`، `Stack`، `Heap` و `Pointers`، بسیار مهم هستند.

خب، `Stack` و `Heap` دو مکان مختلف در حافظه(`RAM`) هستند، تفاوت های مهم‌شون اینها هستند:

- قسمت `Stack` خیلی سریع هست، اما `Heap` به اندازه‌ی `Stack` سریع نیست، اما نمیتونیم برای همه چیز از `Stack` استفاده کنیم، به دلیل اینکه:

- راست لازم داره که سایز یک متغییر رو در زمان کامپایل بدونه، پس نوع های اولیه مثل `i32` همیشه میرند توی `Stack`، به این دلیل که سایزشون مشخص هست. همیشه میدونیم که `i32` چهار بایت فضا اشغال میکنه، پس `i32` میتونه بره داخل `Stack`

- اما بعضی نوع ها  وجود دارند که سایزشون در زمان کامپایل مشخص نیستند، و خب `Stack` هم که به سایز نیاز داره. پس چیکار کنیم؟ اول از همه داده رو داخل `Heap` قرار میدیم، به این دلیل که برای ذخیره سازی داده در `Heap` نیازی به سایز داده نداریم. و بعد برای پیدا کردن اون داده، یک `Pointer` به اون داده درست میکنیم و این `Pointer` رو میتونیم در `Stack` ذخیره کنیم، به این دلیل که سایز `Pointer` مشخص هست. و بعد برای دسترسی به داده، اول میریم سراغ `Pointer` اون به ما میگه که ادرس داده در `Heap` کجاست، و خب بعد میتونیم به اون داده دسترسی داشته باشیم.

اشاره گر (`Pointer`)، به نظر پیچیده میاند، اما خب میتونیم فکر کنیم که شبیه به فهرست مطالب کتاب ها هستند، یک کتاب رو تصور کن:

```text
کتاب من

فهرست مطالب

فصل                             صفحه

فصل اول  : زندگی‌ام                    1
فصل دوم  : گربه‌ام                    15
فصل سوم : شغلم                     23
فصل چهارم: خانواده‌ام                   30
فصل پنجم : برنامه های اینده‌ام            43
```

خب میتونید بهش مثل پنجتا `Pointer` نگاه کنیدِ، میتونید به اطلاعاتی که بهش اشاره میکنند دسترسی داشته باشید، برای مثال: فصل `زندگیم` کجاست؟ در ادرس `43` (به ادرس `43` **اشاره** میکنه).

به `Pointer` هایی که در `Rust` استفاده میشود، معمولا **`Reference`** میگن.(در کلمه `Reference` یعنی "`مرجع`")

نکته‌ی مهمی که باید در موردش بدونید این هست که یک `Reference` به ادرس حافظه‌ی یک "مقدار" اشاره میکند. وقتی از یک `Reference` استفاده میکنیم به این معنی هست که  **مقدار** رو به امانت(قرض) گرفتیم، اما صاحبش نیستیم. مثل همون مثال کتاب هست: **فهرست مطالب** صاحب اطلاعاتی نیست، بلکه این یک فصل هست که صاحب اطلاعات هست.

در `Rust` قبل یک `Reference` یک علامت `&` وجود داره. پس:

- کد `;let my_var = 8` یک متغییر میسازه، اما
- کد `;let my_ref = &my_var` یک `Reference` میسازه
میتونید کد `;my_ref = &my_var` رو اینطوری بخونید: "متغییر `my_ref` یک `Reference` به متغییر `my_var` هست"

این به این معنی هست که `my_ref` فقط به داده‌ی درون `my_var` دسترسی داره، اما صاحبش همچنان متغییر `my_var` هست.

**`بحث مالکیت در "Rust" بسیار مهم هست`**

ما همچنین میتونیم `Reference` یک `Reference`، داشته باشیم. تعدادش هم مهم نیست.

</div>

```rust
fn main() {
    let my_number = 15; // This is an i32
    let single_reference = &my_number; //  This is a &i32
    let double_reference = &single_reference; // This is a &&i32
    let five_references = &&&&&my_number; // This is a &&&&&i32
}
```
در کد بالا همه متغییر ها نوع متفاوتی از دیگری دارند، مثل اینکه "دوست یک دوست" با خود دوست فرق داره.

## More about printing

در `Rust` ما تقریبا میتونیم هر چیزی رو به هر روشی که میخوایم پرینت کنیم. در این بخش چیز های بیشتری در مورد پرینت کردن یاد میگیریم.

اضافه کردن `\n`، یک خط جدید ایجاد میکنه و همچنین `\t` یک تب (`tab`) ایچاد میکنه:
```rust
fn main() {
    // Note: this is print!, not println!
    print!("\t Start with a tab\nand move to a new line");
}
```
خروجیش:
```text
         Start with a tab
and move to a new line
```

داخل `""` میتونیم هر چند خط که میخوایم بنویسیم اما خب حواسمون باید به اسپیس ها هم باشه:

```rust
fn main() {
    // Note: After the first line you have to start on the far left.
    // If you write directly under println!, it will add the spaces
    println!("Inside quotes
you can write over
many lines
and it will print just fine.");

    println!("If you forget to write
    on the left side, the spaces
    will be added when you print.");
}
```

چنین چیزی رو پرینت میکنه:

```text
Inside quotes
you can write over
many lines
and it will print just fine.
If you forget to write
    on the left side, the spaces
    will be added when you print.
```

اگه میخواید `Escape Character` ها رو پرینت کنید، باید یه `\` اضافی هم بزارید که بفهمه میخواید خودش رو پرینت کنید و نمیخواید اون کاری که در حالت عادی انجام میده رو انجام بده:

```rust
fn main() {
    println!("Here are two escape characters: \\n and \\t");
}
```

خروجی این هم همچین چیزی میشه:

```text
Here are two escape characters: \n and \t
```

گاهی اوقات، نیاز داریم تعداد زیادی `Escape Character` یا `"` رو پرینت کنیم، و نمیخوایم که مدام از `\` استفاده کنیم که کامپایلر بفهمه منظورمون فقط خود کاراکتر هست و نه کارکردش، برای این کار میتونیم از یک `r#` قبل از `String` و یک `#` بعد `String` بزاریم:

```rust
fn main() {
    println!("He said, \"You can find the file at c:\\files\\my_documents\\file.txt.\" Then I found the file."); // We used \ five times here
    println!(r#"He said, "You can find the file at c:\files\my_documents\file.txt." Then I found the file."#)
}
```

این دو خط کد یک چیز رو پرینت میکنن، اما روش دوم بهتره، چون کد راحت‌تر خونده میشه:
```text
He said, "You can find the file at c:\files\my_documents\file.txt." Then I found the file.
He said, "You can find the file at c:\files\my_documents\file.txt." Then I found the file.
```

هر وقت هم که نیاز داشتیم که `#` رو پرینت کنیم، میتونیم `String` رو با `r##` شروع کنیم و با `##` تموم کنیم. البته اگه هم بیشتر از یکی نیاز داشتیم میتونیم هر چند تا که میخوام `#` به هر دو طرف اضافه کنیم، برای درک بهتر کدهای زیر رو ببینید:

```rust
fn main() {

    let my_string = "'Ice to see you,' he said."; // single quotes
    let quote_string = r#""Ice to see you," he said."#; // double quotes
    let hashtag_string = r##"The hashtag #IceToSeeYou had become very popular."##; // Has one # so we need at least ##
    let many_hashtags = r####""You don't have to type ### to use a hashtag. You can just use #.""####; // Has three ### so we need at least ####

    println!("{}\n{}\n{}\n{}\n", my_string, quote_string, hashtag_string, many_hashtags);

}
```

خروجیش:

```text
'Ice to see you,' he said.
"Ice to see you," he said.
The hashtag #IceToSeeYou had become very popular.
"You don't have to type ### to use a hashtag. You can just use #."
```

همچنین `r#` یه کاربرد دیگه هم داره، اون هم این هست که باهاش میتونیم از `کلمات‌کلیدی` به عنوان اسم متغییر استفاده کنیم، که در حالت عادی نمیتونیم:

```rust
fn main() {
    let r#let = 6; // The variable's name is let
    let mut r#mut = 10; // This variable's name is mut
}
```
البته در شاید شما **`واقعا`‍** لازم دارید از یک کلمه‌کلیدی به عنوان نام استفاده کنید، برای مثال **`باید`** اسم فانکشنی که میخوایید استفاده کنید، `return` باشه:
```rust
fn r#return() -> u8 {
    println!("Here is your number.");
    8
}

fn main() {
    let my_number = r#return();
    println!("{}", my_number);
}
```
خروجیش:
```text
Here is your number.
8
```
احتمالا هیچوقت به چنین قابلیتی نیاز پیدا نمیکنید، اما اگه در جایی واقعا لازم داشتید که از کلمات‌کلیدی به عنوان اسم استفاده کنید، یادتون باشه که میتونید از `r#` استفاده کنید.

اگه هر وقت لازم داشتید که مقدار بایت یک `&str` یا `char` رو پرینت کنید میتونید قیل از `String` یک `b` بزارید. این برای همه کاراکتر های `ASCII` کار میکنه.

این ها همه کاراکتر های `ASCII` هستند:
```text
☺☻♥♦♣♠♫☼►◄↕‼¶§▬↨↑↓→∟↔▲▼123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\]^_`abcdefghijklmnopqrstuvwxyz{|}~
```

پس کد زیر:

```rust
fn main() {
    println!("{:?}", b"This will look like numbers");
}
```

چنین خروجی‌ای میده:

```text
[84, 104, 105, 115, 32, 119, 105, 108, 108, 32, 108, 111, 111, 107, 32, 108, 105, 107, 101, 32, 110, 117, 109, 98, 101, 114, 115]
```

البته برای یک `char` بهش میگن ***`byte`***، و برای `&str` بهش میگن ***`byte string`***.

همچنین میتونیم از `b` و `r` در کنار هم استفاده کنیم:

```rust
fn main() {
    println!("{:?}", br##"I like to write "#"."##);
}
```

همچین خروجی‌ای میده:  `[73, 32, 108, 105, 107, 101, 32, 116, 111, 32, 119, 114, 105, 116, 101, 32, 34, 35, 34, 46]`.

همچنین میتونیم کاراکتر های `Unicode` رو با استفاده از کدشون پرینت کنیم. برای اینکار باید از فرمت `\u{}` استفاده کنیم. عدد هگزادسیمال کاراکتر هم داخل `{}` قرار میگیره:

```rust
fn main() {
    println!("{:X}", '행' as u32); // Cast char as u32 to get the hexadecimal value
    println!("{:X}", 'H' as u32);
    println!("{:X}", '居' as u32);
    println!("{:X}", 'い' as u32);

    println!("\u{D589}, \u{48}, \u{5C45}, \u{3044}"); // Try printing them with unicode escape \u
}
```

ما تا الان میدونیم که با استفاده از `{}` میتونیم متغییر هارو پرینت کنیم که بهش میگیم `Display Printing`، با `{:?}` هم میتونیم پرینت کنیم که بهش میگیم `Debug Printing` و همچنین با `{:#?}` هم میتونیم پرینت کنیم که بهش میگیم `Debug-Pretty Printing`. اما روش های دیگه‌ای هم برای پرینت کردن وجود داره.

برای مثال، با استفاده از `{:p}` میتونیم ‍`Pointer Address` رو پرینت کنیم. این یعنی میتونیم ادرس متغییر در حافظه(`RAM`) رو بدست بیاریم:

```rust
fn main() {
    let number = 9;
    let number_ref = &number;
    println!("{:p}", number_ref);
}
```

الان چنین چیزی رو پرینت کرد: `0xe2bc0ffcfc`

البته هر بار این ادرس متفاوت هست، حافظه ادرس های تصادفی داده ها رو ذخیره میکنه.‌ (`RAM` = `Random Access Memory`)

همچنین میتونیم مقادیر رو به باینری، هگزادسیمال یا اکتال پرینت کنیم:

```rust
fn main() {
    let number = 555;
    println!("Binary: {:b}, hexadecimal: {:x}, octal: {:o}", number, number, number);
}
```

چنین چیزی پرینت میکنه: `Binary: 1000101011, hexadecimal: 22b, octal: 1053`.

همچنین میتونیم با استفاده از اعداد ترتیب متغییر هارو در فرمت مشخص کنیم:

```rust
fn main() {
    let father_name = "Vlad";
    let son_name = "Adrian Fahrenheit";
    let family_name = "Țepeș";
    println!("This is {1} {2}, son of {0} {2}.", father_name, son_name, family_name);
}
```

همچنین میتونیم از اسم برای مشخص کردن متغییر ها در فرمت استفاده کنیم:
```rust
fn main() {
    println!(
        "{city1} is in {country} and {city2} is also in {country},
but {city3} is not in {country}.",
        city1 = "Seoul",
        city2 = "Busan",
        city3 = "Tokyo",
        country = "Korea"
    );
}
```

چنین چیزی رو پرینت میکنه:
```text
Seoul is in Korea and Busan is also in Korea,
but Tokyo is not in Korea.
```

یک روش پرینت کارامدی و پیچیده‌ای هم وجود داره که چنین فرمتی داره: `{variable:padding alignment minimum.maximum}`

برای فهم این فرمت به نکات زیر توجه کنید:
1) میخواید به متغییر اسم بدید؟ اسم رو اول بنویسید (بعدش اگه میخوایم کارای بیشتری انجام بدیم کاراکتر `:` رو میزاریم)
2) ایا به `Padding Character` نیاز داریم؟ اون کاراکتر مدنظر رو میزاریم
3) ایا نیاز به مشخص کردن جایگاه `Padding Character` داریم؟ علامتی که میخوایم رو میزاریم (`^` یعنی وسط، `<` یعنی به سمت سمت، `>` یعنی به سمت راست)
4) ایا به حداقلی تعدادی از `Padding Character` نیاز داریم؟ تعداد رو به عدد مینویسیم
5) به مشخص کردن حداکثر تعدادی از `Padding Character` نیاز داریم؟ اول یک `.` میزاریم و بعد تعداد رو به عدد مینویسیم

برای مثال،‌ اگه میخوایم کاراکتر `a` نوشته بشه با پنچ کاراکتر `ㅎ` قبل و بعدش باید چنین کدی بنویسیم:

```rust
fn main() {
    let letter = "a";
    println!("{:ㅎ^11}", letter);
}
```

چنین چیزی رو پرینت میکنه:  `ㅎㅎㅎㅎㅎaㅎㅎㅎㅎㅎ`.

برای اینکه بفهمیم کامپایلر چظور باهاش رفتار میکنه بهتره به نکات زیر توجه کنیم:
- به اسم نیاز داریم؟ `{:ㅎ^11}`: چیزی قبل از `:` وجود نداره پس خیر
- به `Padding Character` نیاز داریم؟ `{:ㅎ^11}`: بله، چون کاراکتر `ㅎ` بعد از `:` مشخص شده و همچنین با استفاده از کاراکتر `^` جایگاهش وسظ انتخاب شده
- به حداقل تعدادی از `Padding Character` نیاز داریم؟ `{:ㅎ^11}`: بله، عددی وجود داره که `11` هست
- به حداکثر تعدادی از `Padding Character` نیاز داریم؟ `{:ㅎ^11}`: خیر چون عددی وجود نداره که قبلش کاراکتر `.` وجود داشته باشه

این مثالی از استفاده های این نوع پرینت کردن هست:
```rust
fn main() {
    let title = "TODAY'S NEWS";
    println!("{:-^30}", title); // no variable name, pad with -, put in centre, 30 characters long
    let bar = "|";
    println!("{: <15}{: >15}", bar, bar); // no variable name, pad with space, 15 characters each, one to the left, one to the right
    let a = "SEOUL";
    let b = "TOKYO";
    println!("{city1:-<15}{city2:->15}", city1 = a, city2 = b); // variable names city1 and city2, pad with -, one to the left, one to the right
}
```

چنین چیزی رو پرینت میکنه:
```text
---------TODAY'S NEWS---------
|                            |
SEOUL--------------------TOKYO
```

## Strings

زبان `Rust` دو نوع اصلی `String` دارد: `String` و `&str`، خب فرقشون چیه؟
- نوع `&str` نوع ساده‌ای هست، وقتی کد `;let s = "my string"` مینویسیم، یک `&str` درست میشه همچنین `&str` خیلی سربع هست
- نوع `String` یکم پیچیده هست، یکم کند‌تر هست اما کارایی بیشتری داره،‌ `String` یک اشاره‌گر هست پس داده‌ای که بهش اشاره میکنه توی قسمت `Heap` حافظه هست

همچنین به این توجه کنید که `&str` یک `&` قبلش هست به این دلیل که برای استفاده از `str` نیاز به یک `Reference` داریم، این به دلیل است که `Stack` برای ذخیره سازی نیاز به سایز داده داره. همچنین باید این توجه کنید که برای استفاده از `str` به `&` نیاز داریم ، **پس ما مالکش نیستیم** ، اما برعکس ما مالک یک `String` هستیم. (بعدا در مورد مالکیت که مبحث مهمی در `Rust` هست صحبت میکنیم)

هم `&str` و هم `String` از `UTF-8` پشتیبانی میکنند، برای مثال:

```rust
fn main() {
    let name = "서태지"; // This is a Korean name. No problem, because a &str is UTF-8.
    let other_name = String::from("Adrian Fahrenheit Țepeș"); // Ț and ș are no problem in UTF-8.
}
```
میتونید ببینید که در کد `String::from("Adrian Fahrenheit Țepeș")` یک `String` از `&str` ساخته شده، این دو نوع متفاوت هستند اما قابل تبدیل به یکدیگر هستند

همچنین با تشکر از `UTF-8` میتونید ایموجی هم چاپ کنید:
```rust
fn main() {
    let name = "😂";
    println!("My name is actually {}", name);
}
```
رو سیستم شما عبارت `My name is actually 😂` چاپ میشه اما امکان داره `Command Line` شما از `UTF-8` پشتیبانی نکنه و ایموجی پرینت نشه و خب این مشکل `Rust` نیست.

بیاید دوباره دلیل استفاده از `&` برای `str` رو مرور کنیم.

- نوع `str` سایز پویا `Dynamic` هست،‌ یعنی سایزش میتونه متفاوت باشه، برای مثال سایز های `서태지` و `Adrian Fahrenheit Țepeș` متفاوت هست:

```rust
fn main() {

    println!("A String is always {:?} bytes. It is Sized.", std::mem::size_of::<String>()); // std::mem::size_of::<Type>() gives you the size in bytes of a type
    println!("And an i8 is always {:?} bytes. It is Sized.", std::mem::size_of::<i8>());
    println!("And an f64 is always {:?} bytes. It is Sized.", std::mem::size_of::<f64>());
    println!("But a &str? It can be anything. '서태지' is {:?} bytes. It is not Sized.", std::mem::size_of_val("서태지")); // std::mem::size_of_val() gives you the size in bytes of a variable
    println!("And 'Adrian Fahrenheit Țepeș' is {:?} bytes. It is not Sized.", std::mem::size_of_val("Adrian Fahrenheit Țepeș"));
}
```

چنین چیزی رو پرینت میکنه:

```text
A String is always 24 bytes. It is Sized.
And an i8 is always 1 bytes. It is Sized.
And an f64 is always 8 bytes. It is Sized.
But a &str? It can be anything. '서태지' is 9 bytes. It is not Sized.
And 'Adrian Fahrenheit Țepeș' is 25 bytes. It is not Sized.
```

این دلیلی هست که باید از `&` استفاده کنیم، چون `&` یک اشاره گر میسازه و خب `Rust` سایز یک اشاره‌گر رو میدونه، پس اشاره‌گر میره توی `Stack`. اگه بنویسیم `str`، `Rust` نمیدونه که باید چیکار کنه چون سایز رو نمیدونه

چندین راه برای ساختن برای `String` وجود دارد:

- `String::from("This is the string text");`: این یک روش برای ساخت `String` هست
- `"This is the string text".to_string()`: در این روش یک `&str` به یک `String` تبدیل میشه
- همچنین ماکروی `format!` یک `String` میسازه

مثالی از استفاده از `format!`:
```rust
fn main() {
    let my_name = "Billybrobby";
    let my_country = "USA";
    let my_home = "Korea";

    let together = format!(
        "I am {} and I come from {} but I live in {}.",
        my_name, my_country, my_home
    );
}
```

حالا ما یک `String`ساختیم.

یک روش دیگه برای ساخت `String` استفاده از `()into.` هست، اما یکم متفاوت هست به این دلیل که `()into.` فقط برای ساختن `String` نیست. بعضی نوع ها با استفاده از `from` و`()into.`، میتونند به راحتی به نوع دیگه‌ای تبدیل بشند.

استفاده از `from` رایج‌تر هست چون میدونیم که چه نوعی به چه نوعی تبدیل میشه، اما در هنگام استفاده از `()into.` بعضی وقت ها کامپایلر نمیدونه که باید به چه نوعی تبدیل کنه.
برای مثال در کد `;String::from("Some str")`، میدونیم که یک `String` به یک `&str` تبدیل میشه اما برای مثال کد زیر رو در نظر بگیرید که کامپایلر نمیتونه نوع رو تشخیص بده:

```rust
fn main() {
    let my_string = "Try to make this a String".into(); // ⚠️
}
```

در کد بالا کامپایلر نمیتونه بفهمه که به نوعی میخواید تبدیل کنید،‌‌ چون نوع `&str` میتونه به نوع های زیادی تبدیل بشه و ما مشخص نکردیم.

در خطایی هم که میده میگه که `"من میتونیم "&str" رو به نوع های زیادی تبدیل کنم،‌ کدوم رو میخوای؟"` (`"I can make a &str into a lot of things. Which one do you want?"`)

```text
error[E0282]: type annotations needed
 --> src\main.rs:2:9
  |
2 |     let my_string = "Try to make this a String".into();
  |         ^^^^^^^^^ consider giving `my_string` a type
```

و خب ما میتونیم به اینگونه نوع درخواستی رو مطالبه کنیم:

```rust
fn main() {
    let my_string: String = "Try to make this a String".into();
}
```

و حالا ما یک `String` میگیریم.

## consts and statics

<div dir="rtl">

دو روش دیگه برای ایچاد مقدار هم به جز استفاده از `let` داریم.

اون دوتا `const` و `static` هستند، همچنین هنگام اینجاد متغییر با استفاده از این کلمه‌کلیدی‌‌ها `Rust` از استنتاج نوع استفاده نمیکنه، یعنی باید نوع رو مشخص کنیم.

این ها برای ایجاد مقدار هایی هستند که تغییر نمیکنند، تفاوتشون چیه؟
- کلمه‌کلیدی `const` برای ایجاد مقدار هایی هست که تغییر نمیکنند

- کلمه‌کلیدی `static` هم شبیه به `const` هست، اما `static` ادرس حافظه‌اش تغییر نمیکنه، یعنی میتونیم ازش به عنوان متغییر جهانی (`Global Variable`) استفاده کنیم، البته مقدار `static` میتونه تغییر کنه

پس تقریبا شبیه هم هستند. اما ما معمولا از `const` استفاده میکنیم. البته جا هایی هم هست که نیاز هست که از `static` استفاده کنیم.

اسمی که برای مقادیری که با استفاده از کلمه‌کلیدی `const` یا `static` ساخته شدند، باید با حروف بزرگ باشد. همچنین معمولا بیرون از فانکشن `main` تعریف میشند که اینطوری میتونند در طول برنامه استفاده بشند.

برای مثال اینطوری از این کلمه‌کلیدی ها استفاده کنید:
- `const NUMBER_OF_MONTHS: u32 = 12;`
- `static SEASONS: [&str; 4] = ["Spring", "Summer", "Fall", "Winter"];`

</div>

## More on references

مرجع (`Reference`) ها در `Rust` بسیار مهم هستند، `Rust` از `Reference` استفاده میکند که دسترسی امن به حافظه را ایجاد کند.

ما میدونیم که `&` یک `Reference` میسازد:

```rust
fn main() {
    let country = String::from("Austria");
    let ref_one = &country;
    let ref_two = &country;

    println!("{}", ref_one);
}
```

چنین چیزی رو پرینت میکنه: `Austria`

در کد بالا `country` یک `String` است.ما بعدش دو `Reference` به ان ساختیم. اون ها نوع `&String` رو دارند، ما میتونیم `Reference` های بیشماری به `country` بسازیم.

اما این یک مشکل ایجاد میکنه:

```rust
fn return_str() -> &str {
    let country = String::from("Austria");
    let country_ref = &country;
    country_ref // ⚠️
}

fn main() {
    let country = return_str();
}
```
فانکشن `return_str()` یک `String` میسازه و بعدش یک `Reference` به اون رو برمیگردونه، اما `String`‌ای که در `return_str()` درست میشه فقط در همونجا قابل دسترس هست و وقتی که فانکشن تموم بشه از بین میره و هر فضایی که این فانکشن گرفته بود برای استفاده های بعدی ازاد میشه. پس `country_ref` به یک چیزی اشاره میکنه که از بین رفته و وجود نداره و خب این چیز خوبی نیست. پس `Rust` باهوش ما این کد رو کامپایل نمیکنه.

باید به این نکته توجه کنید اگه یک نوعی که مالکیت داشته باشه از بین بره، تمام چیز هایی که بهش اشاره میکردند هم از بین میرند.

## Mutable references

اگه میخواید با استفاده از `Reference` مقدار رو تغییر بدید باید از `Mutable Reference` استفاده کنیم. برای استفاده از `Mutable Reference` باید از `&mut` به جای `&` استفاده کنیم.

```rust
fn main() {
    let mut my_number = 8; // don't forget to write mut here!
    let num_ref = &mut my_number;
}
```
خب نوع های این متغییر ها چی هستند؟ `my_number` یک `i32` هست و `num_ref` یک `mut i32&`. (میگیم که `num_ref` یک `Mutable Reference` به `my_number` است )

خب بیاید مقدار `my_number` رو با استفاده از `num_ref` با مقدار `10` جمع بزنیم. اما نمیتونیم بنویسیم `num_ref += 10`، به این دلیل که `num_ref` یک `i32` نیست، یک `&i32` هست.

برای اینکه به مقداری که `num_ref` بهش اشاره میکنه باید از کاراکتر `*` استفاده کنیم. کاراکتر `*` به این معنی هست که **من `Reference` رو نمیخوام و مقداری که داره بهش اشاره میکنه رو میخوام**. میتونیم اینطوری برداشت کنیم که `*` مخالف `&` هست.

```rust
fn main() {
    let mut my_number = 8;
    let num_ref = &mut my_number;
    *num_ref += 10; // Use * to change the i32 value.
    println!("{}", my_number);

    let second_number = 800;
    let triple_reference = &&&second_number;
    println!("Second_number = triple_reference? {}", second_number == ***triple_reference);
}
```

چنین چیزی پرینت میکنه:

```text
18
Second_number = triple_reference? true
```
به استفاده از `&` میگن `Referencing`، اما به استفاده از `*` میگن `Derefrencing`.

زبان `Rust` از سه قانون برای استفاده از `Mutable/Immutable Reference` داره، اونها خیلی مهم هستند اما با اینجال به منطق جور در میاند:

- **قانون اول**: نمیتونیم همزمان هم `Mutable Reference` داشته باشیم و هم `Immutable Reference`
- **قانون دوم**: اگه فقط `Immutable Reference` داریم، میتونیم هر چند تا که میخوایم داشته باشیم
- **قانون سوم**: اگه حتی یک `Mutable Reference` داشته باشیم، دیگه نمیتونیم یکی دیگه هم داشته باشیم

این قوانین به این دلیل وجود دارند که یک `Mutable Reference` میتونه داده رو تغییر بده. و خب اگه این قوانین وجود نداشتند میتونستیم به مشکل بر بخوریم، برای مثال فکر کنید که یک قسمت برنامه میخواد یک داده رو بخونه اما همزمان یک قسمت دیگه داره اون داده رو تغییر میده...

یک روش خوب برای درک این قضیه فکر کردن به یک `Powerpoint Presentation` هست:

شرایط اول، **فقط یک `Mutable Reference`**:

یک کارمند درحال نوشتن یک `Presentation` هست. اون میخواد که مدیرش کمکش کنه. کارمند اطلاعات `Login` رو به مدیر میده، الان مدیر یک `Mutable Reference` به `Presentation` داره. مدیر میتونه هر تغییری که میخواد رو روی `Presentation` انجام بده. در این شرایظ هیچ مشکلی وجود نداشت.

شرایط دوم، **هر چندتا `Immutable Reference`**:

کارمند `Presentation` رو با هر چند نفر که میخواد به اشتراک میزاره، همه اونها میتونند `Presentation` رو ببینند اما نمیتونند تغییرش بدند. در این شرایط هم مشکلی پیش نمیاد.

شرایط سوم، **شرایط مشکل**:

کارمند اطلاعات `Login` رو به مدیرش میده. الان مدیرش یک `Mutable Reference` داره. بعد کارمند `Presentation` رو با هرچند نفر که میخواد به اشتراک میزاره، و خب الان اون هر چند نفر، نفری یک `Immutable Reference` دارند. و خب این مشکل داره، شاید مدیر وقتی `Login` کرده میخواد وسط ویرایش کردن یک ایمیل هم به مادرش بفرسته ! و خب همه‌ی اون هر چند نقر میتونند ایمیل رو هم ببینند، و **این چیزی نبود که انتظار داشتند**.

این یک مثالی از داشتن `Mutable Reference` و `Immutable Reference` به طور همزمان هست:

```rust
fn main() {
    let mut number = 10;
    let number_ref = &number;
    let number_change = &mut number;
    *number_change += 10;
    println!("{}", number_ref); // ⚠️
}
```

کامپایلر خطای پرینت میکنه که بسیار مفیده:

نکته: به ساختن `Reference`، قرض گرفتن(`"Borrowing"`)هم میگن
```text
error[E0502]: cannot borrow `number` as mutable because it is also borrowed as immutable
 --> src\main.rs:4:25
  |
3 |     let number_ref = &number;
  |                      ------- immutable borrow occurs here
4 |     let number_change = &mut number;
  |                         ^^^^^^^^^^^ mutable borrow occurs here
5 |     *number_change += 10;
6 |     println!("{}", number_ref);
  |                    ---------- immutable borrow later used here
```

با این حال کد زیر کار میکند ! چرا ؟

```rust
fn main() {
    let mut number = 10;
    let number_change = &mut number; // create a mutable reference
    *number_change += 10; // use mutable reference to add 10
    let number_ref = &number; // create an immutable reference
    println!("{}", number_ref); // print the immutable reference
}
```
این کد بدون مشکل `20` رو پرینت میکنه، به این دلیل کار میکنه که کامپایلر به اندازه‌ای باهوش هست که کد مارو متوجه بشه. کامپایلر میدونه که از `number_change` استفاده کردیم که `number` رو تغییر بدیم، اما بعدا ازش استفاده نکردیم، پس مشکلی وجود نداره. یه جورایی ما همزمان از `Mutable Reference` و `Immutable Reference` استفاده نکردیم.

قبلا در `Rust` چنین کد هایی کامپایل نمیشدند و در هنگام کامپایل خطا میدادند، اما الان کامپایلر باهوش‌تر شده.

### Shadowing again

یادتون هست که گفتم، سایه‌زدن(`Shadowing`) متغییر رو از بین نمیبره؟ و بلکه مسدودش میکنه. خب بیاید با `Reference` ها هم این موضوع رو ببینیم:

```rust
fn main() {
    let country = String::from("Austria");
    let country_ref = &country;
    let country = 8;
    println!("{}, {}", country_ref, country);
}
```

<div dir="rtl">

خب کد بالا چی پرینت میکنه؟

- `Austria, 8`
- `8, 8`

خروجی کد بالا میشه:
- `Austria, 8`


بزارید ببینیم ما چیکار کردیم؟

اول یک متغییر `String` تغریف کردیم به نام `country`. بعدش یک `Reference` به `country` به نام `country_ref` درست کردیم. بعدش متغییر `country` رو با مقدار `8` سایه‌زدیم.

خب پس هنوز متغییر `country` از بین نرفته، پس `country_ref` هنوز باید به مقدار `Austria` اشاره کنه و نه مقدار `8`.

در زیر همون کد رو با کامنت میبینید و متوجه نحوه کار میشید:

</div>

```rust
fn main() {
    let country = String::from("Austria"); // Now we have a String called country
    let country_ref = &country; // country_ref is a reference to this data. It's not going to change
    let country = 8; // Now we have a variable called country that is an i8. But it has no relation to the other one, or to country_ref
    println!("{}, {}", country_ref, country); // country_ref still refers to the data of String::from("Austria") that we gave it.
}
```

## Giving references to functions

<div dir="rtl">

در زبان `Rust`، `Reference` ها برای فانکشن ها کاربردی هستند.

در زبان `Rust` یک قانون **مهم** برای مقدار ها وجود داره:
- هر مقدار میتونه فقط یک مالک داشته باشه

کد زیر کامپایل نمیشه:
</div>

```rust
fn print_country(country_name: String) {
    println!("{}", country_name);
}

fn main() {
    let country = String::from("Austria");
    print_country(country); // We print "Austria"
    print_country(country); // ⚠️ That was fun, let's do it again!
}
```
<div dir="rtl">

به این دلیل کامپایل نمیشه که `country` نابود شده.

ببینیم چی شده:
- یک متغییر `String` به نام `country` درست کردیم. `country` مالکش هست
- ما `country` رو به `print_country` دادیم. اگه یادتون باشه در هنگام به اتمام رسیدن یک فانکشن تمام فضایی که اشغال کرده بود هم ازاد میشه. ما `country` رو به `print_country` دادیم و اون در هنگام اتمام `print_country` نابود میشه. و خب البته `print_country` میتونست ورودیش رو به عنوان خروجیش بده بیرون، اما خب نداده
- ما سعی کردیم که `country` که نابود شده رو به `print_country` بدیم، اما خب نابود شده

میتونیم کاری کنیم که `print_country` اون مقدار رو به عنوان خروجی بده و خب اینطوری کد کار میکنه، اما اینطوری کد یکم بیریخت میشه:

</div>

```rust
fn print_country(country_name: String) -> String {
    println!("{}", country_name);
    country_name // return it here
}

fn main() {
    let country = String::from("Austria");
    let country = print_country(country); // we have to use let here now to get the String back
    print_country(country);
}
```

الان چنین چیزی رو پرینت میکنه:

```text
Austria
Austria
```

یک روش بهتر این هست که `Reference` متغییر `country` رو به فانکشن بدیم. میتونیم با اضافه کردن `&` این کار رو انجام بدیم.

```rust
fn print_country(country_name: &String) {
    println!("{}", country_name);
}

fn main() {
    let country = String::from("Austria");
    print_country(&country); // We print "Austria"
    print_country(&country); // That was fun, let's do it again!
}
```

حالا `()print_country` یک فانکشنی هست که یک `Reference` به `String` رو به عنوان ورودی میگیره. همچنین ما یک `Reference` به `country` رو بهش دادیم.

این یعنی که فانکشن میتونه ازش استفاده کنه اما ما مالکش هستیم هنوز...

حالا بیاید همینکار رو با استفاده از `Mutable Reference` انجام بدیم:

```rust
fn add_hungary(country_name: &mut String) { // first we say that the function takes a mutable reference
    country_name.push_str("-Hungary"); // push_str() adds a &str to a String
    println!("Now it says: {}", country_name);
}

fn main() {
    let mut country = String::from("Austria");
    add_hungary(&mut country); // we also need to give it a mutable reference.
}
```

چنین خروجی‌ای میده: `Now it says: Austria-Hungary`.

پس برای نتیجه‌گیری چنین چیزی میشه:

- `fn function_name(variable: String)`: یک `String` میگیره و مالکش میشه و اگه به عنوان خروجی برش نگردونه، اون ورودی نابود میشه
- `fn function_name(variable: &String)`: یک `String` قرض میگیره، و میتونه به مقدارش دسترسی داشته باشه، اما مالکش نیست
- `fn function_name(variable: &mut String)`: یک `String` قرض میگیره، و میتونه به مقدارش دسترسی داشته باشه همچنین میتونه مقدارش رو تغییر بده، اما مالکش نیست

کد زیر شبیه به استفاده از `Mutable Reference` هست،‌ اما نیست و متقاوت هست:

```rust
fn main() {
    let country = String::from("Austria"); // country is not mutable, but we are going to print Austria-Hungary. How?
    adds_hungary(country);
}

fn adds_hungary(mut country: String) { // Here's how: adds_hungary takes the String and declares it mutable!
    country.push_str("-Hungary");
    println!("{}", country);
}
```
کد کامپایل میشه، اما چطور ممکنه؟

به این دلیل هست که `mut country` یک `Reference` نیست. در این حالت `adds_hungary` مالک `country` میشه. (یک `String` میگیره و نه `&String`)

وقتی که `adds_hungary` رو صدا میزنید، اون مالک میشه. و خب میتونه اون رو به یک متغییر تغییرپذیر تغییر بده. و مشکلی هم ایجاد نمیشه.

مثال `Powerpoint Presentation` رو یادتون هست؟ در این شرایط میتونیم بگیم که کارمند کل کامپیوتر رو به مدیرش میده و کارمند دیگه به کامپیوتر دسترسی نداره پس مدیر هم میتونه هر کاری که میخواد با کامپیوتر و `Presentation` بکنه.

## Copy types

<div dir="rtl">

بعضی نوع ها در `Rust` خیلی ساده هستند. بهشون میگیم **نوع ها کپی**. این نوع های ساده توی `Stack` ذخیره میشند، و خب کامپایلر سایزشون رو میدونه. این به معنی این هست که خیلی راحت میتونیم کپی‌شون کنیم، پس کامپایلر همیشه برای فرستادنشون به یک فانکشن اون ها رو کپی میکنه. همیشه کپی میکنه به این دلیل معمولا خیلی کوچیک هستند و دلیلی نداره که اونهارو کپی نکنه. پس نیازی نیست که به مالکیتشون فکر کنیم.

این نوع ها ساده این ها هستند: `Integers`, `Floats`, `Booleans` (`true` و `false`), و `char`.


خب چطور بفهمیم که یک تایپ کپی میشه یا که خیر؟

میتونیم مستندات اون رو بخونیم. برای مثال مستند نوع `char` در لینک زیر هست:

[https://doc.rust-lang.org/std/primitive.char.html](https://doc.rust-lang.org/std/primitive.char.html)


در سمت چپ لینک بالا میتونید قسمت `Trait Implementations` رو ببینید. شما میتونید **Copy**، **Debug** و **Display** رو ببینید، پس میفهمید که:

- وقتی به فانکشنی فرستاده میشه کپی میشه. (**`Copy`**)

-میشه از `{}` برای پرینت کردنش استفاده کرد. (**`Display`**)

-میشه از `{:?}` برای پرینت کردنش استفاده کرد. (**`Debug`**)

</div>

```rust
fn prints_number(number: i32) { // There is no -> so it's not returning anything
                             // If number was not copy type, it would take it
                             // and we couldn't use it again
    println!("{}", number);
}

fn main() {
    let my_number = 8;
    prints_number(my_number); // Prints 8. prints_number gets a copy of my_number
    prints_number(my_number); // Prints 8 again.
                              // No problem, because my_number is copy type!
}
```
اما اگه به مستندات نوع `String` نگاه کنید، میبینید که یک `Copy type` نیست.

[https://doc.rust-lang.org/std/string/struct.String.html](https://doc.rust-lang.org/std/string/struct.String.html)

در سمت چپ لینک بالا میتونید قسمت `Trait Implementations` رو ببینید. شما میتونید چیز های زیادی رو ببینید اما `Copy` رو نمیبینید اما به جاش `Clone`. `Clone` شبیه به `Copy` هست اما به حافظه‌ی بیشتری نیاز داره، همچنین نیاز دارید وقتی لازم دارید ازش استفاده کنید مستقیم از `()clone.` استفاده کنید. (خودش همینطوری کلون نمیشه)

در کد زیر، `()prints_country` یک `String` رو پرینت میکنه، ما میخوایم دوبار پرینتش کنیم اما نمیتونیم (دلیلش مالکیت هست)

```rust
fn prints_country(country_name: String) {
    println!("{}", country_name);
}

fn main() {
    let country = String::from("Kiribati");
    prints_country(country);
    prints_country(country); // ⚠️
}
```

اما الان میتونیم خطای زیر رو بفهمیم:

```text
error[E0382]: use of moved value: `country`
 --> src\main.rs:4:20
  |
2 |     let country = String::from("Kiribati");
  |         ------- move occurs because `country` has type `std::string::String`, which does not implement the `Copy` trait
3 |     prints_country(country);
  |                    ------- value moved here
4 |     prints_country(country);
  |                    ^^^^^^^ value used here after move
```
قسمت مهمش بخش `which does not implement the Copy trait` هست. اما در مستنداتش فهمیدیم که `Clone` رو پیاده‌سازی کرده، یعنی ازش پشتیبانی میکنه. پس میتونیم `()clone.` رو به کدمون اضافه کنیم. این یک دیگه از مقداری که وجود داره میسازه و به فانکشن میده. الان `country` هم در دسترس هست و نابود نشده. پس میتونیم ازش استفاده کنیم.

```rust
fn prints_country(country_name: String) {
    println!("{}", country_name);
}

fn main() {
    let country = String::from("Kiribati");
    prints_country(country.clone()); // make a clone and give it to the function. Only the clone goes in, and country is still alive
    prints_country(country);
}
```
البته، اگه `String` سایز زیادی داشته باشه، `()clone.` مقدار حافظه‌ی بسیار زیادی مصرف میکنه. یک `String` برای مثال میتونه کل کتاب رو به عنوان مقدار در خودش داشته باشه، و در این شرایط هر وقتی که از `()clone.` استفاده کنیم، کل کتاب رو کپی میکنه. پس در این شرایط استفاده از `Reference` بهینه‌تر هست.

برای مثال کد زیر، چندین بار یک `&str` به یک `String` اضافه میکنه و یک کلون هم ازش میگیره میده به یک فانکشن:

```rust
fn get_length(input: String) { // Takes ownership of a String
    println!("It's {} words long.", input.split_whitespace().count()); // splits to count the number of words
}

fn main() {
    let mut my_string = String::new();
    for _ in 0..50 {
        my_string.push_str("Here are some more words "); // push the words on
        get_length(my_string.clone()); // gives it a clone every time
    }
}
```

چنین چیزی رو پرینت میکنه:

```text
It's 5 words long.
It's 10 words long.
...
It's 250 words long.
```

اما خب `50` تا کلون گرفت ازش، این یعنی `50` بار مقدار رو کپی کرده. اما اینبار از `Reference` استفاده میکنیم، که بهتره:

```rust
fn get_length(input: &String) {
    println!("It's {} words long.", input.split_whitespace().count());
}

fn main() {
    let mut my_string = String::new();
    for _ in 0..50 {
        my_string.push_str("Here are some more words ");
        get_length(&my_string);
    }
}
```

به جای `50` تا کپی گرفتن اینبار اصلا کپی نگرفتیم که خب یعنی حافظه‌ی کمتری مصرف کردیم.

### Variables without values

یک متغییر بدون مقدار را `Uninitialized` میگیم. خیلی ساده هستند، فقط باید `let` و اسم متغییر رو بنویسیم:

```rust
fn main() {
    let my_variable; // ⚠️
}
```
اما `Rust` این رو کامپایل نمیکنه. یعنی اگه حتی یک چیزی که مقدار بهش داده نشده باشه، وچود داشته باشه، کد رو کامپایل نمیکنه.

اما بعضی وقت ها کاربردی هستند:

```rust
fn loop_then_return(mut counter: i32) -> i32 {
    loop {
        counter += 1;
        if counter % 50 == 0 {
            break;
        }
    }
    counter
}

fn main() {
    let my_number;

    {
        // Pretend we need to have this code block
        let number = {
            // Pretend there is code here to make a number
            // Lots of code, and finally:
            57
        };

        my_number = loop_then_return(number);
    }

    println!("{}", my_number);
}
```
کد بالا `100` رو پرینت میکنه.
میتونید ببینید که `my_number` در فانکشن `()main` ایچاد شده، پس تا انتهای اون در دسترس هست. اما مقدارش درون حلقه‌ی `loop` مشخص میشه. با این حال

برای اینکه کد ساده‌تر بشه بهتره تصور کنیم که `(number)loop_then_return` همیشه خروچی `100` رو برمیگردونه، پس حذفش میکنیم و `100` رو بجاش مینویسیم. همچنین به متغییر `number` هم احتیاج نداریم پس حذفش میکنیم. الان کد چنین چیزی هست:

```rust
fn main() {
    let my_number;
    {
        my_number = 100;
    }

    println!("{}", my_number);
}
```

همچنین به این نکته توجه کنید که `my_number`، یک `Mutable` نیست. اون اولین مقداری که گرفته `100` هست و هیچ وقت هم تغییر نکرده پس نیازی هم نیست که `mut` رو داشته باشه. در نهایت کدی که کامپایلر تولید میکنه چنین چیزی وجود داره:`;let my_number = 100`.

## Collection types

زبان `Rust` نوع های زیادی برای ساخت مجموعه دارد. مجموعه های برای زمان هایی هستند که نیاز دارید چندین داده را در یک متغییر ذخیره کنیم. برای مثال، میتونیم نام تمام شهر های یک کشور رو داخل یک متغییر داشته باشیم. ما با ارایه ها شروع میکنیم، که سریع‌ترین هستند اما کاربرد کمی دارند، از این لحاظ شبیه به `&str` هستند.

### Arrays

<div dir="rtl">

مشخصات ارایه ها:

- سایزشون نمیتونه بعد از تعریف تغییر کنه
- همه‌ی اعضا باید از یک نوع باشند

اما خب خیلی سریع هستند.

نوع یک ارایه چنین فرمتی هست: `[type; size]`

برای مثال دو متغییر زیر نوع های متفاوتی دارند:
</div>

```rust
fn main() {
    let array1 = ["One", "Two"]; // This one is type [&str; 2]
    let array2 = ["One", "Two", "Five"]; // But this one is type [&str; 3]. Different type!
}
```
نوع `array1`: `[&str; 2]` هست.
نوع `array2`: `[&str; 3]` هست.

یک ترفند جالب برای فهمیدن نوع یک ارایه از طریق کامپایلر وجود داره، و اون هم استفاده از متود هایی هست که وجود ندارند:
```rust
fn main() {
    let seasons = ["Spring", "Summer", "Autumn", "Winter"];
    let seasons2 = ["Spring", "Summer", "Fall", "Autumn", "Winter"];
    seasons.ddd(); // ⚠️
    seasons2.thd(); // ⚠️ as well
}
```
کامپایلر میگه که ‌"چی میگی؟ متود `()ddd.` برای `seasons` وجود نداره و `()thd.` هم برای `seasons2` وجود نداره":

```text
error[E0599]: no method named `ddd` found for array `[&str; 4]` in the current scope
 --> src\main.rs:4:13
  |
4 |     seasons.ddd(); // 
  |             ^^^ method not found in `[&str; 4]`

error[E0599]: no method named `thd` found for array `[&str; 5]` in the current scope
 --> src\main.rs:5:14
  |
5 |     seasons2.thd(); // 
  |              ^^^ method not found in `[&str; 5]`
```

خب کامپایلر میگه که ``method not found in `[&str; 4]` ``، که خب نوع ارایه رو هم داده !

اگه بخوایم ارایه‌ای بسازیم که همه‌ی عناصرش یک مقدار داشته باشند، از فرمتی مثل فرمت زیر استفاده میکنیم:
```rust
fn main() {
    let my_array = ["a"; 10];
    println!("{:?}", my_array);
}
```

چنین چیزی پرینت میکنه: `["a", "a", "a", "a", "a", "a", "a", "a", "a", "a"]`.

این روش به طور مداوم برای ایچاد بافر استفاده میشه، برای مثال: `;let mut buffer = [0; 640]`. که یک ارایه با `640` عنصری که مقدارشون `0` هست میسازه.

با استفاده از `[]` میتونیم عنصر هارو بدست بیاریم. شماره‌ی اولین عنصر `[0]` هست و دومین عنصر هم `[1]` هست و همینطوری تا اخر...

```rust
fn main() {
    let my_numbers = [0, 10, -20];
    println!("{}", my_numbers[1]); // prints 10
}
```

همچنین ما میتونیم یک `slice` (یه تیکه) از یک ارایه بدست بیاریم. اول از همه به `&` نیاز داریم چون کامپایلر سایز رو نمیدونه بعد میتونیم از `..` برای مشخص کردن بازه تیکه‌ای که میخوایم رو مشخص کنیم.

برای مثال:

```rust
fn main() {
    let array_of_ten = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

    let three_to_five = &array_of_ten[2..5];
    let start_at_two = &array_of_ten[1..];
    let end_at_five = &array_of_ten[..5];
    let everything = &array_of_ten[..];

    println!("Three to five: {:?}, start at two: {:?}, end at five: {:?}, everything: {:?}", three_to_five, start_at_two, end_at_five, everything);
}
```

یادمون باشه که:

- شماره های عنصر ها از `0` شروع میشند و نه `1`
- بازه‌ای که انتخاب میکنیم، **تا** اخرین `index`ای که مشخص میکنیم هست، یعنی خود اون رو شامل نمیشه.

پس بازه‌ی `[0..2]` میشه اولین عنصر و دومین عنصر (0 و ‍‍1).

اما خب میتونیم کاری کنیم که اخرین `index`ای که مشخص میکنیم هم جزو بازه باشه، چطوری؟ با استفاده از `..=`. پس اگه میخوایم بازه ای داشته باشیم از اولین عنصر تا سومین عنصر، میتونیم از `[0..=2]` استفاده کنیم.

## Vectors

همونطوری که `&str` و `String` داریم. ما `Array` و `Vector` هم داریم. `Array` ها سریع هستند اما کاربرد کمتری دارند، و `Vector` ها کند‌تر هستند و کاربرد بیشتری دارند.

البته در `Rust` همه چی خیلی سریع هست پس `Vector` ها کند نیستند، اما از `Array` ها کند‌تر هستند. نوع `Vector` ها `Vec` هست، ما هم برای اینکه وقتمون گرفته نشه بهشون `vec` میگیم :
)

دو روش برای تعریف `vec` ها وجود داره، یکیش استفاده از `new` هست:
```rust
fn main() {
    let name1 = String::from("Windy");
    let name2 = String::from("Gomesy");

    let mut my_vec = Vec::new();
    // If we run the program now, the compiler will give an error.
    // It doesn't know the type of vec.

    my_vec.push(name1); // Now it knows: it's Vec<String>
    my_vec.push(name2);
}
```
<div dir="rtl">

ما همیشه باید نوعی که `Vec` درون خودش نگه میداره رو مشخص کنیم،‌ البته اگه مقداری به `Vec` اضافه کنیم، کامپایلر باهوش `Rust` متوجه نوع میشه. اما میتونیم از `<>` برای مشخص کردن اون نوع استفاده کنیم، برای مثال:
- کد `Vec<(i32, i32)>` یک `Vec` ایجاد میکنه که هر ایتمش یک `Tuple` از `(i32, i32)` نگهداری میکنه
- کد `Vec<Vec<String>>` یک `Vec` ایجاد میکنه که هر ایتمش یک `Vec` که `String` در خودش جای میده رو نگهداری میکنه

همچنین میتونیم نوع یک متغییر رو مشخص کنیم که `Rust` مجبور نباشه از مقداری که ما به `()push.` میدیم نوع رو انتخاب کنه:

</div>

```rust
fn main() {
    let mut my_vec: Vec<String> = Vec::new(); // The compiler knows the type
                                              // so there is no error.
}
```

همونطور که متوجه شدید، ایتم های داخل یک `Vec` باید همه از یک نوع باشند.


یک دیگه از روش های ایجاد یک `Vec` استفاده از ماکروی `vec!` است. شبیه به ایجاد یک `Array` هست، البته یک `vec!` اولش داره:

```rust
fn main() {
    let mut my_vec = vec![8, 10, 10];
}
```

نوع متغییر `my_vec` یک `Vec<i32>` هست.


همچنین میتونیم از قابلیت `Slicing` در `Vec` ها هم استفاده کنیم:

```rust
fn main() {
    let vec_of_ten = vec![1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
    // Everything is the same as above except we added vec!.
    let three_to_five = &vec_of_ten[2..5];
    let start_at_two = &vec_of_ten[1..];
    let end_at_five = &vec_of_ten[..5];
    let everything = &vec_of_ten[..];

    println!("Three to five: {:?},
start at two: {:?}
end at five: {:?}
everything: {:?}", three_to_five, start_at_two, end_at_five, everything);
}
```

بخاطر اینکه یک `Vec` کند‌تر از `Array` هست، ما میتونیم یکسری روش هایی رو بکار بگیریم که بهینه‌تر از `Vec` بتونیم استفاده کنیم.

نوع `Vec` چیزی به نام ظرفیت(`Capacity`) داره، و اون به معنای این هست که `Vec` چه تعداد ایتمی رو میتونه در خودش نگه داره. برای مثال فکر کنید که `Capacity` یک `Vec` مقدار `2` هست،‌ خب در این حالت ما میتونیم به راحتی `2` ایتم درش اضافه کنیم، البته بعدش هم میتونیم اضافه کنیم اما `Vec` برای نگهداری تعداد بیشتری از ایتم ها نیاز داره که فضای بیشتری رو از حافظه اشغال کنه و همه ایتم هارو کپی کنه در فضای جدیدی که گرفته شده و `Capacity` **دو برابر**، `Capacity` قبلی هست. خب اینکار هزینه بر هست.

به این کار میگن `Reallocation`.

ما میتونیم از `()capacity.` برای گرفتن `Capacity` یک `Vec` استفاده کنیم.

برای مثال به کد زیر توجه کنید:

```rust
fn main() {
    let mut num_vec = Vec::new();
    println!("{}", num_vec.capacity()); // 0 elements: prints 0
    num_vec.push('a'); // add one character
    println!("{}", num_vec.capacity()); // 1 element: prints 4. Vecs with 1 item always start with capacity 4
    num_vec.push('a'); // add one more
    num_vec.push('a'); // add one more
    num_vec.push('a'); // add one more
    println!("{}", num_vec.capacity()); // 4 elements: still prints 4.
    num_vec.push('a'); // add one more
    println!("{}", num_vec.capacity()); // prints 8. We have 5 elements, but it doubled 4 to 8 to make space
}
```

چنین چیزی پرینت میکنه:

```text
0
4
4
8
```
پس این `Vec` دو بار فضای جدید، که هربار **دوبرابر** مقدار قبلی هست رو اشغال کرده و هر ایتمی که درونش داشته رو در فضای جدید کپی کرده.

پس این `Vec` دو بار `Reallocation` انچام داده: `0` به `4` و `4` به `8`.

ما میتونیم با استفاده از `.with_capacity()` هنگام ساخت یک `Vec` مقدار `Capacity` رو هم بدیم که خب اگه درست `Capacity` بدیم میتونیم از `Vec` بهینه‌تر استفاده کنیم:

```rust
fn main() {
    let mut num_vec = Vec::with_capacity(8); // Give it capacity 8
    num_vec.push('a'); // add one character
    println!("{}", num_vec.capacity()); // prints 8
    num_vec.push('a'); // add one more
    println!("{}", num_vec.capacity()); // prints 8
    num_vec.push('a'); // add one more
    println!("{}", num_vec.capacity()); // prints 8.
    num_vec.push('a'); // add one more
    num_vec.push('a'); // add one more // Now we have 5 elements
    println!("{}", num_vec.capacity()); // Still 8
}
```
خب `Vec`ای که در کد با وجود داره اصلا `Reallocation` انجام نداده که خب بهتر هست. پس اگه میدونیم که قراره چند ایتم در یک `Vec` قرار بدیم بهتر هست که با استفاده از `.with_capacity()` مقدار `Capacity` اون `Vec` رو مشخص کنیم. که اینطوری برنامه سریع‌تر میشه.

یادتون هست که ما با استفاده از `()into.` یک `&str` رو به `String` تبدیل کردیم؟ خب میتونیم با استفاده ازش یک `Array` رو به `Vec` هم تبدیل کنیم. البته باید نوع `Vec` رو هم مشخص کنیم. همچنین با استفاده از `Vec<_>` میتونیم به کامپایلر بگیم که خودت نوع `Vec` رو انتخاب کن.

```rust
fn main() {
    let my_vec: Vec<u8> = [1, 2, 3].into();
    let my_vec2: Vec<_> = [9, 0, 10].into(); // Vec<_> means "choose the Vec type for me"
                                             // Rust will choose Vec<i32>
}
```

## Tuples

با استفاده از `()` میتونیم در `Rust`، `Tuple` درست کنیم. ما خیلی `Tuple` خالی دیدم تا حالا به این دلیل که **هیچی** یعنی یک `Tuple` خالی:

```text
fn do_something() {}
```

کد بالا در واقعیت میانبری برای کد زیر هست:

```text
fn do_something() -> () {}
```
فانکشن بالا هیچی نمیگیره و هیچی هم بر نمیگردونه، یعنی یک `()` میگیره و یک `()` برمیگردونه. پس همینطوریش هم خیلی از `Tuple` ها استفاده کردیم.

```rust
fn just_prints() {
    println!("I am printing"); // Adding ; means we return an empty tuple
}

fn main() {}
```

نوع `Tuple` میتونه چیز های زیادی نگه داره و حتی میتونه چیز هایی با نوع های مختلف رو هم نگه داره. ایتم های درون `Tuple` به این ترتیب قابل دسترسی هستند: 0, 1, 2 و همینطوری تا اخرین ایتم...

برای دسترسی بهشون به جای `[]` از `.` استفاده میکنیم.

بزارید یک `Tuple` با نوع های مختلف درست کنیم و نحوه‌ی  کار با `Tuple` ها رو ببینیم:

```rust
fn main() {
    let random_tuple = ("Here is a name", 8, vec!['a'], 'b', [8, 9, 10], 7.7);
    println!(
        "Inside the tuple is: First item: {:?}
Second item: {:?}
Third item: {:?}
Fourth item: {:?}
Fifth item: {:?}
Sixth item: {:?}",
        random_tuple.0,
        random_tuple.1,
        random_tuple.2,
        random_tuple.3,
        random_tuple.4,
        random_tuple.5,
    )
}
```

خروجیش:

```text
Inside the tuple is: First item: "Here is a name"
Second item: 8
Third item: ['a']
Fourth item: 'b'
Fifth item: [8, 9, 10]
Sixth item: 7.7
```

نوع `Tuple` بالا از درونش نوع های `(&str, i32, Vec<char>, char, [i32; 3], f64)` وچود دارند.


میتونیم از `Tuple` ها برای ایچاد چندین متغییر استفاده کنیم،‌به کد زیر یه نگاهی بندازید:

```rust
fn main() {
    let str_vec = vec!["one", "two", "three"];
}
```
متغییر `str_vec` سه ایتم درونش داره. چطوری باید استخراجشون کنیم؟ میتونیم از `Tuple` ها استفاده کنیم:

```rust
fn main() {
    let str_vec = vec!["one", "two", "three"];

    let (a, b, c) = (str_vec[0], str_vec[1], str_vec[2]); // call them a, b, and c
    println!("{:?}", b);
}
```

کد با خروجی `"two"` رو میده، که چیزی هست که `b` هست. به این میگن `Destructuring`. این به این خاصر هست که متغییر اولی یک ساختار(`Structure`) هست، اما بعدش ما `a`، `b` و `c` رو درست کردیم که داخل یک ساختار نیستند.

اگه میخوایم `Destructure` کنیم اما به همه‌ی مقدار ها احتیاجی نداریم میتونیم از `_` استفاده کنیم.

```rust
fn main() {
    let str_vec = vec!["one", "two", "three"];

    let (_, _, variable) = (str_vec[0], str_vec[1], str_vec[2]);
}
```
الان فقط `variable` رو داریم و با بقیه کاری نداشتیم.

همچنین نوع های مجموعه‌ای زیادی وجود دارند، و روش های زیادی برای استفاده از `Array` ها، `Vec` ها و `Tuple` ها وجود داره که بعدا در موردشون یاد میگیریم. اما حالا بیاید `Control Flow` رو یاد بگیریم.

## Control flow

کنترل جریان یعنی اینکه برنامه در شرایط متفاوت چه کاری باید انجام بده.

اولین کنترل کننده `if` هست:

```rust
fn main() {
    let my_number = 5;
    if my_number == 7 {
        println!("It's seven");
    }
}
```
همچنین به این نکته توجه کنید که `==` برای مقایسه هست و `=` برای دادن مقدار و به این هم دقت کنید که در `Rust` به پرانتز در `if` نیازی نداریم.

و همچنین `else` و `else if` هم وجود دارند که کنترل بیشتری رو هم میدند:

```rust
fn main() {
    let my_number = 5;
    if my_number == 7 {
        println!("It's seven");
    } else if my_number == 6 {
        println!("It's six")
    } else {
        println!("It's a different number")
    }
}
```

خروجی بالا: `It's a different number` است به این دلیل که مقدار برابر `7` یا `6` نیست.

همچنین میتونیم شرط های بیشتری با استفاده از `&&` و `||` ایجاد کنیم:

```rust
fn main() {
    let my_number = 5;
    if my_number % 2 == 1 && my_number > 0 { // % 2 means the number that remains after diving by two
        println!("It's a positive odd number");
    } else if my_number == 6 {
        println!("It's six")
    } else {
        println!("It's a different number")
    }
}
```

خروجی کد بالا: `It's a positive odd number`است، به این دلیل که وقتی `my_number` رو بر `2` تقسیم میکنیم، باقیمانده‌ی اون `1` میشه، و همچین `1` بزرگتر از `0` هست.

میتونیم ببینیم که `if`، `else` و `else if` زیاد، خوندن کد رو سخت میکنه. خب ما میتونیم از `match` به جای اونها استفاده کنیم که به خوانایی کد کمک میکنه.

اما هر وقت که از `match` استفاده میکنیم باید تمام حالات ممکن رو در نظر بگیریم و براشون کد بنویسیم، برای مثال کد زیر کار نمیکنه:

```rust
fn main() {
    let my_number: u8 = 5;
    match my_number {
        0 => println!("it's zero"),
        1 => println!("it's one"),
        2 => println!("it's two"),
        // ⚠️
    }
}
```

خطای کامپایلر:

```text
error[E0004]: non-exhaustive patterns: `3u8..=std::u8::MAX` not covered
 --> src\main.rs:3:11
  |
3 |     match my_number {
  |           ^^^^^^^^^ pattern `3u8..=std::u8::MAX` not covered
```

این به این معنی هست که "تو شرایطی که مقدار `0`، `1` و `2` باشه رو کنترل کردی اما اگه چیزی غیر از این بود چیکار کنم؟ نوع `u8` میتونه `255` حالت مختلف داشته باشه و تو فقط چندتا ازشون رو گفتی، بقیه چی؟".

خب برای حل این مشکل میتونیم از `_` استفاده کنیم، که به "هر چیز دیگه که بود" هست:

```rust
fn main() {
    let my_number: u8 = 5;
    match my_number {
        0 => println!("it's zero"),
        1 => println!("it's one"),
        2 => println!("it's two"),
        _ => println!("It's some other number"),
    }
}
```

خروجیش میشه: `It's some other number`.

در هنگام استفاده از `match` به این نکات توجه کنید:

- شرایط مختلف `match` رو داخل `{}` باید بنویسیم
- وقتی یک **الگو** مینویسیم، بعدش از `=>` استفاده میکنیم که بگیم اگه مقدار با این **الگو** `match` بود چیکار کنه
- هر شرایطی که در `match` کنترل میکنیم، بهش میگیم یک **بازو**(`Arm`). برای مثال در کد بالا هر خط داخل `match` یک `Arm` هست
- بین `Arm` ها `,` میزاریم و نه `;`


همچنین میتونیم با استفاده از `match` یک مقدار تغریف کنیم:

```rust
fn main() {
    let my_number = 5;
    let second_number = match my_number {
        0 => 0,
        5 => 10,
        _ => 2,
    };
}
```
مقدار متغییر `second_number` میشه `10`.

همونطور که متوجه شدید بعد `match` یک `;` هست. این به دلیل این هست که ما با استفاده از `match` یک مقدار یک متغییر رو تغریف کردیم پس کد ما در نهایت میشه ‌`;let second_number = 10`.

میتونیم به عنوان ورودی به `Rust` یک `Tuple` هم بدیم:

```rust
fn main() {
    let sky = "cloudy";
    let temperature = "warm";

    match (sky, temperature) {
        ("cloudy", "cold") => println!("It's dark and unpleasant today"),
        ("clear", "warm") => println!("It's a nice day"),
        ("cloudy", "warm") => println!("It's dark but not bad"),
        _ => println!("Not sure what the weather is."),
    }
}
```

خروجیش میشه: `It's dark but not bad`، به این دلیل که مقدار `sky`، `cloudy` هست و مقدار `temperature`، `warm` هست.

همچنین میتونیم از `if` داخل `match` استفاده کنیم. به این کار میگن `Match guard`:

```rust
fn main() {
    let children = 5;
    let married = true;

    match (children, married) {
        (children, married) if married == false => println!("Not married with {} children", children),
        (children, married) if children == 0 && married == true => println!("Married but no children"),
        _ => println!("Married? {}. Number of children: {}.", married, children),
    }
}
```

خروجیش میشه: `Married? true. Number of children: 5.`

میتونیم هر چند‌تا که میخوایم از `_` در داخل یک `match` استفاده کنیم:

```rust
fn match_colours(rbg: (i32, i32, i32)) {
    match rbg {
        (r, _, _) if r < 10 => println!("Not much red"),
        (_, b, _) if b < 10 => println!("Not much blue"),
        (_, _, g) if g < 10 => println!("Not much green"),
        _ => println!("Each colour has at least 10"),
    }
}

fn main() {
    let first = (200, 0, 0);
    let second = (50, 50, 50);
    let third = (200, 50, 0);

    match_colours(first);
    match_colours(second);
    match_colours(third);

}
```

خروجیش میشه:

```text
Not much blue
Each colour has at least 10
Not much green
```

خب همونطور که متوجه شدیم، `match` اولین الگویی که با مقدار ها هماهنگ باشه رو اجرا میکنه و با باقی شرایط دیگه کاری نداره. این یکی از جاهایی هست که کد کامپایل میشه اما میتونه نتیجه‌ی دلخواه مارو نده.

برای حل این مشکل میتونیم یک `match` بزرگ بنویسیم، اما بهتر هست که از حلقه‌ی `for` استفاده کنیم. (بعدا در مورد حلقه‌ ها صحبت میکنیم)

دستور `match` اگه خروجی‌ای داره باید همه‌ی خروجی هاش از یک نوع باشند، پس کد زیر کامپایل نمیشه:

```rust
fn main() {
    let my_number = 10;
    let some_variable = match my_number {
        10 => 8,
        _ => "Not ten", // ⚠️
    };
}
```

چیزی که کامپایلر میگه:

```text
error[E0308]: `match` arms have incompatible types
  --> src\main.rs:17:14
   |
15 |       let some_variable = match my_number {
   |  _________________________-
16 | |         10 => 8,
   | |               - this is found to be of type `{integer}`
17 | |         _ => "Not ten",
   | |              ^^^^^^^^^ expected integer, found `&str`
18 | |     };
   | |_____- `match` arms have incompatible types
```

این کد هم به همون دلیل کامپایل نمیشه:
```rust
fn main() {
    let some_variable = if my_number == 10 { 8 } else { "something else "}; // ⚠️
}
```

اما این کار میکنه، به این دلیل که `match` نیست و در هر شرایطی هم یک متغییر جدید ایجاد میکنه:

```rust
fn main() {
    let my_number = 10;

    if my_number == 10 {
        let some_variable = 8;
    } else {
        let some_variable = "Something else";
    }
}
```
همجنین میتونیم از `@` برای دادن اسم به مقدار داخل عبارت `match` استفاده کنیم.

```rust
fn match_number(input: i32) {
    match input {
    number @ 4 => println!("{} is an unlucky number in China (sounds close to 死)!", number),
    number @ 13 => println!("{} is unlucky in North America, lucky in Italy! In bocca al lupo!", number),
    _ => println!("Looks like a normal number"),
    }
}

fn main() {
    match_number(50);
    match_number(13);
    match_number(4);
}
```

خروجیش میشه:

```text
Looks like a normal number
13 is unlucky in North America, lucky in Italy! In bocca al lupo!
4 is an unlucky number in China (sounds close to 死)!
```

## Structs

با استفاده از `Struct` ها میتونیم نوع خومون رو بسازیم. در `Rust`، خیلی از `Struct` ها استفاده میکنیم به این دلیل که ساختشون اسون هست و بسیار کاربردی هستند. `Struct` ها با کلمه‌کلیدی `struct` ایجاد میشند. اسم های باید فرمت `UpperCamelCase` باشند، یعنی فاصله‌ای بین کلمات نباید باشه و هر کلمه با حرف بزرگ شروع بشه. اگه اسم یک `Struct` با حروف کوچیک باشه کامپایلر اخطار میده.

سه نوع `Struct` وجود داره. به یکیشون میگیم `Unit Struct`. این نوع چیز خاصی رو در خودش نگه نمیداره:

```rust
struct FileDirectory;
fn main() {}
```

نوع بعدی `Tuple Struct` ها هستند. در نوع `Struct` ها اسمی برای هر مقدار نمینویسیم. `Tuple Struct` ها زمانی کاربردی هستند که فقط میخوایم یه مقداری رو در یک `Struct` ذخیره کنیم و نیازی نداریم که به هر مقداری که ذخیره میشه اسم بدیم:

```rust
struct Colour(u8, u8, u8);

fn main() {
    let my_colour = Colour(50, 0, 50); // Make a colour out of RGB (red, green, blue)
    println!("The second part of the colour is: {}", my_colour.1);
}
```

کد بالا چنین چیزی پرینت میکنه: `The second part of the colour is: 0`

نوع بعدی `Named Struct` ها هستند. این نوع `Struct` ها رایج‌ترین نوع هستند. در این نوع `Struct` ها ما برای هم مقداری که در `Struct` ذخیره میشه اسم میدیم.

به مقداری که با اسم در یک `Struct` ذخیره میشه، `Field` میگیم. `Field` ها درون `{}` تعریف میشند. نحوه‌ی ایجاد هر `Field` هم اینطوری هست که اسم رو میدیم و نوع مقداری که میتونه درش ذخیره بشه رو هم میگیم.

به این نکته توجه کنید که بعد از تعریف هر `Field` از `;` استفاده نمیکنیم و از `,` استفاده میکنیم.

کد زیر رو ببینید همه چی رو متوجه میشید:
```rust
struct Colour(u8, u8, u8); // Declare the same Colour tuple struct

struct SizeAndColour {
    size: u32,
    colour: Colour, // And we put it in our new named struct
}

fn main() {
    let my_colour = Colour(50, 0, 50);

    let size_and_colour = SizeAndColour {
        size: 150,
        colour: my_colour
    };
}
```
با استفاده از `,`، `Field` ها رو از هم جدا میکنیم. برای اخرین `Field` هم میتونیم `,` بزاریم و هم میتونیم نزاریم. این به عهده‌ی ما است که با کدوم حال کنیم :)

برای مثال در کد زیر اخرین `Field`، `SiezeAndColour` یک `,` داره:

```rust
struct Colour(u8, u8, u8); // Declare the same Colour tuple struct

struct SizeAndColour {
    size: u32,
    colour: Colour, // And we put it in our new named struct
}

fn main() {}
```

اما خب بهش احتیاچی نداریم، اما ایده‌ی خوبی هست که همیشه یک `,` بزاریم، به این دلیل که شاید گاهی بخوایم ترتیب `Field` ها رو عوض کنیم:

```rust
struct Colour(u8, u8, u8); // Declare the same Colour tuple struct

struct SizeAndColour {
    size: u32,
    colour: Colour // No comma here
}

fn main() {}
```

اما اگه بخوایم ترتیب رو عوض کنیم کد کامپایل نمیشه، چون اگه `Field` اخری نیست حتما باید `,` داشته باشه:
```rust
struct SizeAndColour {
    colour: Colour // ⚠️ Whoops! Now this doesn't have a comma.
    size: u32,
}

fn main() {}
```

اما خب این مسئله زیاد مهم نیست، و ما میتونیم تصمیم بگیریم که چیکار کنیم.


خب بیاید یک ساختار به اسم `Country` بسازیم. ساختار `Country` فیلد های `population`، `capital` و `leader_name` رو داره:

```rust
struct Country {
    population: u32,
    capital: String,
    leader_name: String
}

fn main() {
    let population = 500_000;
    let capital = String::from("Elista");
    let leader_name = String::from("Batu Khasikov");

    let kalmykia = Country {
        population: population,
        capital: capital,
        leader_name: leader_name,
    };
}
```

متوجه شدید که اسم فیلد هارو رو بار نوشتیم؟ نوشتیم: `population: population`, `capital: capital`, `leader_name: leader_name`.

خب این اضافه کاری هست و بهش نیازی نداریم اگه اسم متغییر هایی که داریم میدیم با اسم `Field` یکی باشه:
```rust
struct Country {
    population: u32,
    capital: String,
    leader_name: String
}

fn main() {
    let population = 500_000;
    let capital = String::from("Elista");
    let leader_name = String::from("Batu Khasikov");

    let kalmykia = Country {
        population,
        capital,
        leader_name,
    };
}
```

## Enums

کلمه‌ی `enum` کوتاه شده‌ی کلمه‌ی `Enumeration` هست. این ها خیلی شبیه به `Struct` ها هستند،‌ اما تفاوتی هم دارند که این ها هستند:
- زمانی از `Struct` ها استفاده میکنیم که نیاز داریم یک مقدار **و** یک مقدار دیگه رو در یک نوع ذخیره کنیم
- زمانی از `Enum` استفاده میکنیم که نیاز داریم یک مقدار **یا** یک مقدار دیگه رو در یک نوع ذخیره کنیم


پس `Struct` ها برای استفاده از **چندین چیز** کنار یکدیگر هستند. اما `Enum` ها برای استفاده از **چندین انتخاب** کنار یکدیگر هستند.

برای ایجاد یک `Enum` از کلمه‌کلیدی `enum` استفاده میکنیم وبعدش اسم رو میدیم و بعدش هم `{}` میزاریم و انتخاب هارو درونش تعریف میکنیم. همچنین مثل `Struct` ها از `,` برای جداسازی انتخاب ها استفاده میکنیم. در کد زیر یک `Enum` با نام `ThingsInTheSky` ایجاد میکنیم:

```rust
enum ThingsInTheSky {
    Sun,
    Stars,
}

fn main() {}
```
استفاده از `Enum` منطقی هست دیگه، چون تو اسمون یا `خورشید` هست و یا `ستاره ها` هستند. و ما باید یکی رو انتخاب کنیم.

```rust
// create the enum with two choices
enum ThingsInTheSky {
    Sun,
    Stars,
}

// With this function we can use an i32 to create ThingsInTheSky.
fn create_skystate(time: i32) -> ThingsInTheSky {
    match time {
        6..=18 => ThingsInTheSky::Sun, // Between 6 and 18 hours we can see the sun
        _ => ThingsInTheSky::Stars, // Otherwise, we can see stars
    }
}

// With this function we can match against the two choices in ThingsInTheSky.
fn check_skystate(state: &ThingsInTheSky) {
    match state {
        ThingsInTheSky::Sun => println!("I can see the sun!"),
        ThingsInTheSky::Stars => println!("I can see the stars!")
    }
}

fn main() {
    let time = 8; // it's 8 o'clock
    let skystate = create_skystate(time); // create_skystate returns a ThingsInTheSky
    check_skystate(&skystate); // Give it a reference so it can read the variable skystate
}
```

چنین چیزی پرینت میکنه: `I can see the sun!`.

همچین هم انتخاب در `Enum` میتونه مقداری رو هم در خودش ذخیره کنه:
```rust
enum ThingsInTheSky {
    Sun(String), // Now each variant has a string
    Stars(String),
}

fn create_skystate(time: i32) -> ThingsInTheSky {
    match time {
        6..=18 => ThingsInTheSky::Sun(String::from("I can see the sun!")), // Write the strings here
        _ => ThingsInTheSky::Stars(String::from("I can see the stars!")),
    }
}

fn check_skystate(state: &ThingsInTheSky) {
    match state {
        ThingsInTheSky::Sun(description) => println!("{}", description), // Give the string the name description so we can use it
        ThingsInTheSky::Stars(n) => println!("{}", n), // Or you can name it n. Or anything else - it doesn't matter
    }
}

fn main() {
    let time = 8; // it's 8 o'clock
    let skystate = create_skystate(time); // create_skystate returns a ThingsInTheSky
    check_skystate(&skystate); // Give it a reference so it can read the variable skystate
}
```

این هم همون خروچی `I can see the sun!` رو میده.

همچین میتونیم انتخاب هایی که یک `Enum` به ما میده رو هم به اصطلاح `Import` کنیم. باری مثال در کد زیر ما هر باز لازم داریم که برای اشاره به یک انتخاب `Modd::` رو بنویسیم:

```rust
enum Mood {
    Happy,
    Sleepy,
    NotBad,
    Angry,
}

fn match_mood(mood: &Mood) -> i32 {
    let happiness_level = match mood {
        Mood::Happy => 10, // Here we type Mood:: every time
        Mood::Sleepy => 6,
        Mood::NotBad => 7,
        Mood::Angry => 2,
    };
    happiness_level
}

fn main() {
    let my_mood = Mood::NotBad;
    let happiness_level = match_mood(&my_mood);
    println!("Out of 1 to 10, my happiness is {}", happiness_level);
}
```

خروجیش چنین چیزی میشه: `Out of 1 to 10, my happiness is 7`

اما میتونیم انتخاب های `Enum` رو `Import` کنیم که این باعث میشه کد کمتری بنویسیم.

برای `Import` کردن انتخاب هایی که `Mood` به ما میده میتونیم از `;use Mood::*` استفاده کنیم.

این `*` که اینجا استفاده کردیم کاملا با `*` که در `Derefrencing` استفاده میکنیم فرق داره.

بزارید در کد ببینیم:
```rust
enum Mood {
    Happy,
    Sleepy,
    NotBad,
    Angry,
}

fn match_mood(mood: &Mood) -> i32 {
    use Mood::*; // We imported everything in Mood. Now we can just write Happy, Sleepy, etc.
    let happiness_level = match mood {
        Happy => 10, // We don't have to write Mood:: anymore
        Sleepy => 6,
        NotBad => 7,
        Angry => 2,
    };
    happiness_level
}

fn main() {
    let my_mood = Mood::Happy;
    let happiness_level = match_mood(&my_mood);
    println!("Out of 1 to 10, my happiness is {}", happiness_level);
}
```
همچنین اگه ما تغیین نکنیم که انتخاب های یک `Enum` چه مقداری میتونند ذخیره کنند، `Rust` به طور پیشفرض یک عدد رو به هر انتخاب با ترتیبی که هستند میده.

عددی که هر انتخاب نگه میداره به ترتیب از `0` شروع میشه. یعنی در کد زیر `Spring` مقدار `0` رو میگیره، `Summer` مقدار `1` رو میگیره و خودت برو تا تهش...

```rust
enum Season {
    Spring, // If this was Spring(String) or something it wouldn't work
    Summer,
    Autumn,
    Winter,
}

fn main() {
    use Season::*;
    let four_seasons = vec![Spring, Summer, Autumn, Winter];
    for season in four_seasons {
        println!("{}", season as u32);
    }
}
```

کد بالا چنین چیزی رو پرینت میکنه:

```text
0
1
2
3
```
البته اگه میخوایم میتونیم مقدار دیگه رو هم بهشون بدیم.
لازم نیست به همشون مقدار بدیم همیشه مقدار انتخاب بعدی یکی بیشتر از مقدار انتخاب قبلی میشه.

```rust
enum Star {
    BrownDwarf = 10,
    RedDwarf = 50,
    YellowStar = 100,
    RedGiant = 1000,
    DeadStar, // Think about this one. What number will it have?
}

fn main() {
    use Star::*;
    let starvec = vec![BrownDwarf, RedDwarf, YellowStar, RedGiant];
    for star in starvec {
        match star as u32 {
            size if size <= 80 => println!("Not the biggest star."), // Remember: size doesn't mean anything. It's just a name we chose so we can print it
            size if size >= 80 => println!("This is a good-sized star."),
            _ => println!("That star is pretty big!"),
        }
    }
    println!("What about DeadStar? It's the number {}.", DeadStar as u32);
}
```

چنین چیزی رو پرینت میکنه:

```text
Not the biggest star.
Not the biggest star.
This is a good-sized star.
This is a good-sized star.
What about DeadStar? It's the number 1001.
```

اگه به هیچ کدوم مقدار نمیدادیم، مقدار `DeadStar` میشد `4`،‌ اما الان مقدارش شده `1001`.

### Enums to use multiple types

میدونیم که در ایتم هایی که میتونیم در `Vec`، `Array` و ... ذخیره کنیم باید از یک نوع باشند(فقط `Tuple` ها از چندین نوع پشتیبانی میکنند). اما میتونیم از `Enum` استفاده کنیم که نوع های متفاوت رو درون این نوع ها قرار بدیم.

تصور کنید که میخوایم که `Vec` داشته باشیم که بتونه از نوع `u32` یا `i32` درون خودش جای بده. البته که میتونیم از `Vec<(u32, i32)>` استفاده کنیم اما ما میخوایم که یک نوعی داشته باشیم که بتونه `u32` یا `i32` رو درون خودش جای بده.

برای حل این مشکل میتونیم از `Enum` استفاده کنیم:

```rust
enum Number {
    U32(u32),
    I32(i32),
}

fn main() {}
```
<div dir="rtl">

خب دو انتخاب داریم:
- `U32` که میتونه یک مقدار از نوع `u32` در خودش جای بده
- `I32` که میتونه یک مقدار از نوع `i32` در خودش جای بده

`U32` و `I32` فقط اسم هستند و میتونستند هرچیزی باشند، برای مثال میتونیم اسمشون رو بزاریم `UThirtyTwo` و `IThirtyTwo` یا هر چیز دیگه ای...

خب الان میتونیم `Number` رو در یک `Vec` قرار بدیم و اون `Vec` میتونه هم `i32` و هم `u32` رو در هر ایتمش نگهداری کنه. کامپایلر هم ناراضی نمیشه چون نوعی ساختیم که میتونه اینکارو انجام بده. برای کامپایلر مهم نیست که چه مقداری رو درون `Vec` قرار میدیم تا زمانی که اون چیزی که قرار میدیم یک **انتخاب** از `Number` باشه.

بخاطر اینکه `Number` یک `Enum` هست باید یکی از انتخاب های موجود رو انتخاب کنیم. پس در هنگام مقداردهی از `()is_positive` استفاده میکنیم و مقدار ورودی رو به شکل یک انتخاب از `Number` به عنوان خروجی میدیم بیرون. اینکار رو درون فانکشن `get_number` انجام دادیم:

</div>

```rust
enum Number {
    U32(u32),
    I32(i32),
}

fn get_number(input: i32) -> Number {
    let number = match input.is_positive() {
        true => Number::U32(input as u32), // change it to u32 if it's positive
        false => Number::I32(input), // otherwise just give the number because it's already i32
    };
    number
}


fn main() {
    let my_vec = vec![get_number(-800), get_number(8)];

    for item in my_vec {
        match item {
            Number::U32(number) => println!("It's a u32 with the value {}", number),
            Number::I32(number) => println!("It's an i32 with the value {}", number),
        }
    }
}
```

خروجی برنامه بالا چنین چیزی میشه:

```text
It's an i32 with the value -800
It's a u32 with the value 8
```

## حلقه ها | Loops

با استفاده از حلقه ها میتونیم به `Rust` بگیم یک کار رو تا زمانی انجام بده که ما میخوایم. کلمه‌کلیدی `loop` یک حلقه ایجاد میکنه که تا زمانی که به کلمه‌کلیدی `break` برخوره متوقف نمیشه:

```rust
fn main() { // This program will never stop
    loop {

    }
}
```

بیاد به کامپایلر بگیم که در شرایط خاصی باید انجام اون کار رو متوقف کنه و حلقه رو `break` کنه:
```rust
fn main() {
    let mut counter = 0; // set a counter to 0
    loop {
        counter +=1; // increase the counter by 1
        println!("The counter is now: {}", counter);
        if counter == 5 { // stop when counter == 5
            break;
        }
    }
}
```

خروجیش میشه:

```text
The counter is now: 1
The counter is now: 2
The counter is now: 3
The counter is now: 4
The counter is now: 5
```
اگه یک حلقه درون یک حلقه‌ی دیگه داشته باشیم، میتونیم بهشون اسم بدیم اینطوری میتونیم بگیم که کدوم حلقه باید `break` بشه. با استفاده از رو کاراکتر `'` و `:` میتونیم به یک حلقه اسم بدیم:

```rust
fn main() {
    let mut counter = 0;
    let mut counter2 = 0;
    println!("Now entering the first loop.");

    'first_loop: loop {
        // Give the first loop a name
        counter += 1;
        println!("The counter is now: {}", counter);
        if counter > 9 {
            // Starts a second loop inside this loop
            println!("Now entering the second loop.");

            'second_loop: loop {
                // now we are inside 'second_loop
                println!("The second counter is now: {}", counter2);
                counter2 += 1;
                if counter2 == 3 {
                    break 'first_loop; // Break out of 'first_loop so we can exit the program
                }
            }
        }
    }
}
```

خروجیش:

```text
Now entering the first loop.
The counter is now: 1
The counter is now: 2
The counter is now: 3
The counter is now: 4
The counter is now: 5
The counter is now: 6
The counter is now: 7
The counter is now: 8
The counter is now: 9
The counter is now: 10
Now entering the second loop.
The second counter is now: 0
The second counter is now: 1
The second counter is now: 2
```

حلقه‌ی بعدی `while` هست که تا زمانی که شرطی که درش تعریف کردیم، پایدار باشه، ادامه پیدا میکنه:

```rust
fn main() {
    let mut counter = 0;

    while counter < 5 {
        counter +=1;
        println!("The counter is now: {}", counter);
    }
}
```

حلقه‌ی بعدی `for` هست که بعد از تعداد معینی بار اجرا شدن متوقف میشه. حلقه‌ی `for` اغلب از `Range` استفاده میکنه. برای ایجاد یک `Range` از `..` یا `..=` استفاده میکنیم.

- `..` یک بازه‌ی عددی بین `0` **تا** `n` ایجاد میکنه(`n` شامل بازه نمیشه): `0..3` چنین بازه‌ای میسازه: `0, 1, 2`.
- `..=` یک بازه‌ی عددی بین `0` و `n` ایجاد میکنه(`n` شامل بازه میشه): `0..=3` چنین بازه‌ای میسازه: `0, 1, 2, 3`.

```rust
fn main() {
    for number in 0..3 {
        println!("The number is: {}", number);
    }

    for number in 0..=3 {
        println!("The next number is: {}", number);
    }
}
```

خروجیش:

```text
The number is: 0
The number is: 1
The number is: 2
The next number is: 0
The next number is: 1
The next number is: 2
The next number is: 3
```

همچنین در هر دور حلقه، مقداری از بازه که الان روش هستیم رو در متغییری که قبل از `in` تعریف شده بهمون میده. میتونیم اسم اون رو هرچیزی بزاریم. و به این نکته توجه داشته باشید که به اون متغییر فقط در درون حلقه دسترسی داریم.

اگه نیازی به مقداری که الان روش هستیم نداریم میتونیم از `_` استفاده کنیم:
```rust
fn main() {
    for _ in 0..3 {
        println!("Printing the same thing three times");
    }
}
```

خروجیش:

```text
Printing the same thing three times
Printing the same thing three times
Printing the same thing three times
```

اگه به اون متغییر خاص درون حلقه اسم بدیم و ازش استفاده نکنیم، کامپایلر بهمون اخطار میده:

```rust
fn main() {
    for number in 0..3 {
        println!("Printing the same thing three times");
    }
}
```

این هم خروجی کد بالا رو میده، اما در هنگام کامپایل اخطاری نمایش داده میشه که اسم متغییر رو دادیم و از `_` استفاده نکردیم و این به معنای این هست که میخوایم ازش استفاده کنیم، اما ازش استفاده نکردیم:
```text
warning: unused variable: `number`
 --> src\main.rs:2:9
  |
2 |     for number in 0..3 {
  |         ^^^^^^ help: if this is intentional, prefix it with an underscore: `_number`
```

کامپایلر پیشنهاد میکنه که برای اینکه این اخطار رو نگیریم باید قبل از اسم اون متغییر از `_` استفاده کنیم. این برای `Rust` به این معنی هست که حالا شاید ازش استفاده کردم، شایدم نکردیم تو در این مورد گیر نده. اما استفاده از `_` خالی، به این معنا هست که اصلا اهمیتی درباره این متغییر نمیدم.

همچنین میتونیم از `break` برای برگردوندن یک مقدار استفاده کنیم. برای اینکار میتونیم اسم متغییر رو بعد از `break` بنویسیم و بعد از `;` استفاده کنیم، برای مثال:

```rust
fn main() {
    let mut counter = 5;
    let my_number = loop {
        counter +=1;
        if counter % 53 == 3 {
            break counter;
        }
    };
    println!("{}", my_number);
}
```
خروجیش میشه : `56`

کد `;break counter` به این معنا هست که حلقه رو تموم کن و همچنین مقدار متغییر `counter` رو هم برگردون.


خب حالا میدونیم که چطوری از حلقه ها استفاده کنیم. کد زیر یک راه‌حل خوب هست برای مشکلی که در بخش ها قبل با `match` داشتیم.

بهتر هست به این دلیل که ما میخوام همه‌ی ایتم هارو با چیزی مقایسه کنیم و `for` این قابلیت رو به ما میده:

```rust
fn match_colours(rbg: (i32, i32, i32)) {
    println!("Comparing a colour with {} red, {} blue, and {} green:", rbg.0, rbg.1, rbg.2);
    let new_vec = vec![(rbg.0, "red"), (rbg.1, "blue"), (rbg.2, "green")]; // Put the colours in a vec. Inside are tuples with the colour names
    let mut all_have_at_least_10 = true; // Start with true. We will set it to false if one colour is less than 10
    for item in new_vec {
        if item.0 < 10 {
            all_have_at_least_10 = false; // Now it's false
            println!("Not much {}.", item.1) // And we print the colour name.
        }
    }
    if all_have_at_least_10 { // Check if it's still true, and print if true
        println!("Each colour has at least 10.")
    }
    println!(); // Add one more line
}

fn main() {
    let first = (200, 0, 0);
    let second = (50, 50, 50);
    let third = (200, 50, 0);

    match_colours(first);
    match_colours(second);
    match_colours(third);
}
```

چنین خروجی رو میده:

```text
Comparing a colour with 200 red, 0 blue, and 0 green:
Not much blue.
Not much green.

Comparing a colour with 50 red, 50 blue, and 50 green:
Each colour has at least 10.

Comparing a colour with 200 red, 50 blue, and 0 green:
Not much green.
```

## Implementing structs and enums

<div dir="rtl">

اینجا اون جایی هست که میتونیم `Struct` ها و `Enum` ها رو کاربردی کنیم. با استفاده از کلمه‌کلیدی `impl` میتونیم برای `Struct` ها و `Enum` ها فانکشن تعریف کینم. به فانکشن هایی که برای `Struct` ها یا `Enum` ها هستند متود(`Method`) میگیم.

دو نوع `Method` وجود دارند:

- `Regular Method`: اینها همیشه به عنوان ورودی `self` یا `&self` یا `&mut self` رو میگیرند. برای استفاده از اینها باید از `.` استفاده کنیم. برای مثال `().clone` یک `Regular Method` هست

- `Associated/Static Method`:اینها `self` نمیگیرند. معمولا هم برای ایجاد یک `Struct` یا `Enum` جدید بکار میرند. برای استفاده از این ها باید از `::` استفاده کنیم.

</div>


برای پرینت کردن یک `Struct` یا `Enum` با استفاده از `{:?}` جدید باید `Debug` رو پیاده‌سازی کرده باشه. ما میتونیم به کامپایلر بگیم که اینکار رو انجام بده. برای این کار از `#[derive(Debug)]` استفاده میکنیم. به چیز هایی که با `#[]` شروع میشند میگن `Attribute`. بعدا در مورد `Attribute` ها یاد میگیریم اما `derive` رایج ترین چیزی هست که استفاده میکنیم.

در مثال پایین ما یک `Animal` میسازیم و بعد اون رو پرینت میکنیم:

```rust
#[derive(Debug)]
struct Animal {
    age: u8,
    animal_type: AnimalType,
}

#[derive(Debug)]
enum AnimalType {
    Cat,
    Dog,
}

impl Animal {
    fn new() -> Self {
        // Self means Animal.
        // You can also write Animal instead of Self

        Self {
            // When we write Animal::new(), we always get a cat that is 10 years old
            age: 10,
            animal_type: AnimalType::Cat,
        }
    }

    fn change_to_dog(&mut self) { // because we are inside Animal, &mut self means &mut Animal
                                  // use .change_to_dog() to change the cat to a dog
                                  // with &mut self we can change it
        println!("Changing animal to dog!");
        self.animal_type = AnimalType::Dog;
    }

    fn change_to_cat(&mut self) {
        // use .change_to_cat() to change the dog to a cat
        // with &mut self we can change it
        println!("Changing animal to cat!");
        self.animal_type = AnimalType::Cat;
    }

    fn check_type(&self) {
        // we want to read self
        match self.animal_type {
            AnimalType::Dog => println!("The animal is a dog"),
            AnimalType::Cat => println!("The animal is a cat"),
        }
    }
}



fn main() {
    let mut new_animal = Animal::new(); // Associated function to create a new animal
                                        // It is a cat, 10 years old
    new_animal.check_type();
    new_animal.change_to_dog();
    new_animal.check_type();
    new_animal.change_to_cat();
    new_animal.check_type();
}
```

خروجیش:

```text
The animal is a cat
Changing animal to dog!
The animal is a dog
Changing animal to cat!
The animal is a cat
```
به این نکته توجه کنید که `Self` و `self` فقط یک اختصار هستند برای اشاره به نوع فعلی، برای مثال در کد بالا همه‌ی `Self` و `self` ها به نوع `Animal` اشاره میکنند.

در زیر یک ما یک `Method` برای یک `Enum` پیاده‌سازی کردیم:
```rust
enum Mood {
    Good,
    Bad,
    Sleepy,
}

impl Mood {
    fn check(&self) {
        match self {
            Mood::Good => println!("Feeling good!"),
            Mood::Bad => println!("Eh, not feeling so good"),
            Mood::Sleepy => println!("Need sleep NOW"),
        }
    }
}

fn main() {
    let my_mood = Mood::Sleepy;
    my_mood.check();
}
```

خروجی کد بالا میشه: `Need sleep NOW`

## Destructuring

بیاید یکم بیشتر در مورد `Destructuring` بدونیم.

در کد زیر یک روش از `Destructuring` رو میبینیم،‌ در حقیقت متغییر `papa_doc` رو در یک `Struct`، `Destructure` کردیم:
```rust
struct Person { // make a simple struct for a person
    name: String,
    real_name: String,
    height: u8,
    happiness: bool
}

fn main() {
    let papa_doc = Person { // create variable papa_doc
        name: "Papa Doc".to_string(),
        real_name: "Clarence".to_string(),
        height: 170,
        happiness: false
    };

    let Person { // destructure papa_doc
        name: a,
        real_name: b,
        height: c,
        happiness: d
    } = papa_doc;

    println!("They call him {} but his real name is {}. He is {} cm tall and is he happy? {}", a, b, c, d);
}
```

چنین چیزی رو پرینت میکنه: `They call him Papa Doc but his real name is Clarence. He is 170 cm tall and is he happy? false`

اول از همه ما با `; let papa_doc = Person { fields }` یک متغییر از نوع `Person` ایجاد کردیم. بعد با استفاده از `let Person { fields } = papa_doc` اون رو `Destructure` کردیم.

ما مجبور نیستیم که `name: a` رو بنویسیم،‌ میتونیم فقط `name` بنویسیم. اما اونطوری نوشتیم چون میخواستیم اسم اون متغییر `a` باشه.


خب حالا یک مثال بزرگتر میزنیم. در این مثال ما یک `Struct` به نام `City` داریم. ما `Method`،‌ `new` رو براش تغریف کردیم. بعد فانکشن `process_city_values` رو داریم که یکسری کار با مقدار های `City`‌ای که بهش میدیم انجام میده. در این فانشکن متغییر ورودی رو `Destructure` کردیم:

```rust
struct City {
    name: String,
    name_before: String,
    population: u32,
    date_founded: u32,
}

impl City {
    fn new(name: String, name_before: String, population: u32, date_founded: u32) -> Self {
        Self {
            name,
            name_before,
            population,
            date_founded,
        }
    }
}

fn process_city_values(city: &City) {
    let City {
        name,
        name_before,
        population,
        date_founded,
    } = city;
        // now we have the values to use separately
    let two_names = vec![name, name_before];
    println!("The city's two names are {:?}", two_names);
}

fn main() {
    let tallinn = City::new("Tallinn".to_string(), "Reval".to_string(), 426_538, 1219);
    process_city_values(&tallinn);
}
```

چنین چیزی پرینت میکنه: `The city's two names are ["Tallinn", "Reval"]`.

## References and the dot operator

تا اینجا فهمیدیم که ما `Reference` ها رو داریم و برای اینکه مقدار یک `Reference` رو بگیریم باید از `*` استفاده کنیم.

میدونیم که `Reference` یک نوع متفاوت از نوع اصلی هست،‌ در حقیفت یک `Reference` از نوع اصلی هست. پس کد زیر کار نمیکنه:

```rust
fn main() {
    let my_number = 9;
    let reference = &my_number;

    println!("{}", my_number == reference); // ⚠️
}
```

خطایی که کامپایلر میده:

```text
error[E0277]: can't compare `{integer}` with `&{integer}`
 --> src\main.rs:5:30
  |
5 |     println!("{}", my_number == reference);
  |                              ^^ no implementation for `{integer} == &{integer}`
```

پس باید بجاش بنویسیم `println!("{}", my_number == *reference);`، اگه اینکار رو کنیم `true` رو پرینت میکنه،‌ دلیلش این هست که الان یک نوع `i32` رو با `i32` مقایسه میکنه و نه یک نوع `i32` رو با `&i32`. به این کار میگن `Derefrencing`.

اما وقتی از `Method` ها استفاده میکنیم `Rust` خودش عملیات `Dereferencing` رو انجام میده. کاراکتر `.` در استفاده از `Method` ها خودش عملیات `Dereferencing` رو انجام میده. بهش میگیم `dot operator`.

بزارید یک `Struct` با یک فیلد `u8` تعریف کنیم. بعدش یک `Reference` ازش میسازیم و سعی میکنیم با مقداری مقایسش کنیم. اما کد زیر کار نمیکنه:

```rust
struct Item {
    number: u8,
}

fn main() {
    let item = Item {
        number: 8,
    };

    let reference_number = &item.number; // reference number type is &u8

    println!("{}", reference_number == 8); // ⚠️ &u8 and u8 cannot be compared
}
```
برای اینکه کار کنه باید متغییر `reference_number` رو `Dereference` کنیم. چطوری؟ اینطوری: `println!("{}", *reference_number == 8);`

اما اگه طوری کد رو بنویسیم که از `dot operator` استفاده کنیم دیگه خودمون لازم نیست `Derefrencing` رو انجام بدیم:
```rust
struct Item {
    number: u8,
}

fn main() {
    let item = Item {
        number: 8,
    };

    let reference_item = &item;

    println!("{}", reference_item.number == 8); // we don't need to write *reference_item.number
}
```
حالا بزارید یک `Method` برای `Item` درست کنیم که مقدار درون `Item` رو با یک مقدار دیگه مقایسه کنه. اینجا هم نیازی به `*` نداریم:

```rust
struct Item {
    number: u8,
}

impl Item {
    fn compare_number(&self, other_number: u8) { // takes a reference to self
        println!("Are {} and {} equal? {}", self.number, other_number, self.number == other_number);
            // We don't need to write *self.number
    }
}

fn main() {
    let item = Item {
        number: 8,
    };

    let reference_item = &item; // This is type &Item
    let reference_item_two = &reference_item; // This is type &&Item

    item.compare_number(8); // the method works
    reference_item.compare_number(8); // it works here too
    reference_item_two.compare_number(8); // and here

}
```
پس یادمون باشه، وقتی از `.` استفاده میکنیم نیازی به `*` نداریم.

## Generics

(اره واقعا ترجمه‌ی درستی نکردم)

در فانکشن ها ما باید نوع متغییر های ورودی رو بنویسیم:
```rust
fn return_number(number: i32) -> i32 {
    println!("Here is your number.");
    number
}

fn main() {
    let number = return_number(5);
}
```

اما اگه بخوایم بتونیم نوع های دیگه‌ای رو هم بگیریم باید چیکار کنیم؟ خب باید از `Generic` استفاده کنیم. وقتی از `Generic` ها استفاده میکنیم لازم نیست نوع رو به طور مشخص تعریف کنیم و همچنین اون قسمتی از برنامه که درش از `Generic` ها استفاده کردیم میتونه با نوع ها متفاوتی هم کار کنه.

برای استفاده از `Generic` ها، باید از کاراکتر `<>` استفاده کنیم و یک اسمی هم به نوع بدیم برای مثال `T` پس میشه: `<T>`.

این به معنای این هست که هر نوعی رو میپذیره.

معمولا اسم `Generic` ها رو با یک حروف بزرگ مشخص میکنیم اما مجبور به این کار نیستیم.

اینطوری میتونیم فانکشنی که قبلا نوشته بودیم رو `Generic` کنیم، یعنی میتونه هر نوعی رو به عنوان ورودی دریافت کنیم:

```rust
fn return_number<T>(number: T) -> T {
    println!("Here is your number.");
    number
}

fn main() {
    let number = return_number(5);
}
```
بخش مهم `<T>` که بعدش از اسم فانکشن نوشتیم هست. بدون `<T>`، `Rust` فکر میکنه که `T` یک `Concrete` هست(`Concrete،` `Generic` نیست). `Concrete` چیزی هست مثل `String` یا `i8`.

برای فهم بهتر بیاید `<T>` رو حذف کنیم ببینیم چی میشه، همچنین `T` رو به `MyType` تغییر میدیم:

```rust
fn return_number(number: MyType) -> MyType { // ⚠️
    println!("Here is your number.");
    number
}
```
همونطور که گفتم الان `Rust` فکر میکنه که `MyType` یک `Concrete` هست، پس باید یک نوعی به نام `MyType` بسازیم که کد کار کنه وگرنه اصلا `MyType` وجود نداره.

اما ما میخوایم هر نوعی بگیریم و از `Generic` ها استفاده کنیم، پس نوع `MyType` رو نمینویسیم و میایم میگیم که فانکشن `return_number` یک `Generic` میگیره به نام `MyType` و نوع متغییر ورودی رو هم میگیم که `MyType` هست. دقت کنید که `MyType` میتونه هر چیزی باشه:

```rust
fn return_number<MyType>(number: MyType) -> MyType {
    println!("Here is your number.");
    number
}

fn main() {
    let number = return_number(5);
}
```

خب مسخره بازی رو کنار میزاریم و از همون اسم `T` استفاده میکنیم چون تنبلیم...

یادتون هست که در `Rust` بعضی نوع ها **`Copy`** رو پیاده‌سازی کرده بودند و بعضی هم **`Clone`** رو پیاده‌سازی کرده بودند.

خب یادتونم هست که برای اینکه بتونیم یک نوع رو با استفاده از `{:?}` پرینت کنیم، اون نوع باید رو **`Debug`** پیاده‌سازی میکرد.

در هنگام استفاده از `Generic` ها به مشکل بر میخوریم چون نمیدونیم که ایا نوعی که به عنوان ورودی میاد فلان چیز پیاده‌سازی کرده یا که نه:
```rust
fn print_number<T>(number: T) {
    println!("Here is your number: {:?}", number); // ⚠️
}

fn main() {
    print_number(5);
}
```
`print_number` میخواد `number` رو پرینت کنه اما نمیدونیم که ایا نوع `number`، **`Debug`** رو پیاده‌سازی کرده یا نه.

در خطایی که کامپایلر هم میده، میتونیم ببینیم که میگه `T`، `Debug` رو پشتیبانی نکرده:
```text
error[E0277]: `T` doesn't implement `std::fmt::Debug`
  --> src\main.rs:29:43
   |
29 |     println!("Here is your number: {:?}", number);
   |                                           ^^^^^^ `T` cannot be formatted using `{:?}` because it doesn't implement `std::fmt::Debug`
```
در پیام خطا اومده که `T`، `Debug` رو پیاده‌سازی نکرده. خب ما چیکار کنیم؟ `Debug` رو برای `T` پیاده‌سازی کنیم؟ خب ما که نوعش رو نمیدونیم!

خب در اینجا میتونیم به فانکشن این اطمینان رو بدیم که نوعی که به عنوان ورودی بهت فرستاده میشه، **`Debug`** رو پیاده‌سازی کرده:

اینطوری میتونیم اینکار رو انجام بدیم:

```rust
use std::fmt::Debug; // Debug is located at std::fmt::Debug. So now we can just write 'Debug'.

fn print_number<T: Debug>(number: T) { // <T: Debug> is the important part
    println!("Here is your number: {:?}", number);
}

fn main() {
    print_number(5);
}
```

الان کامپایلر میدونه که نوع `T`، **`Debug`** رو پیاده‌سازی کرده. پس کد کار میکنه، چرا ؟ به این دلیل که `i32`، **`Debug`** رو پیاده‌سازی کرده.

الان میتونیم یک `Struct` درست کنیم که **`Debug`** رو پیاده‌سازی کرده و بدیم به `print_item` که پرینتش کنه:

```rust
use std::fmt::Debug;

#[derive(Debug)]
struct Animal {
    name: String,
    age: u8,
}

fn print_item<T: Debug>(item: T) {
    println!("Here is your item: {:?}", item);
}

fn main() {
    let charlie = Animal {
        name: "Charlie".to_string(),
        age: 1,
    };

    let number = 55;

    print_item(charlie);
    print_item(number);
}
```

چنین چیزی رو پرینت میکنه:

```text
Here is your item: Animal { name: "Charlie", age: 1 }
Here is your item: 55
```

گاهی هم نیاز داریم که نوع های بیشتری در یک فانکشن `Generic` بگیریم.

در این مثال ما دو `Generic` رو میگیریم، اول `T` که میخوایم با `{}` پرینتش کنیم، پس باید **`Display`** رو پیاده‌سازی کرده باشه.

همچنین یک نوع دیگه به اسم `U` که هم میخوایم با `{}` پرینتش کنیم و هم میخوایم که قابل مقایسه کردن باشه، پس باید `Display` و `PartialOrd` رو پیاده‌سازی کرده باشه.

```rust
use std::fmt::Display;
use std::cmp::PartialOrd;

fn compare_and_display<T: Display, U: Display + PartialOrd>(statement: T, num_1: U, num_2: U) {
    println!("{}! Is {} greater than {}? {}", statement, num_1, num_2, num_1 > num_2);
}

fn main() {
    compare_and_display("Listen up!", 9, 8);
}
```

خروجیش: `Listen up!! Is 9 greater than 8? true`.

پس `fn compare_and_display<T: Display, U: Display + PartialOrd>(statement: T, num_1: U, num_2: U)` میگه که:

- اسم فانکشن `compare_and_display` هست
- نوع `Generic` اولی که میگیره اسمش `T` هست و باید قابل پرینت با `{}` باشه
- نوع `Generic` دومی که میگیره، اسمش `U` هست و باید قابل پرینت با `{}` باشه و همچنین باید قابل مقایسه باشه

همچین برای اینکه `Generic` ها راحت قابل خوندن باشن میتونیم قبل از شروع بلوک کد فانکشن از `where` استفاده کنیم:

```rust
use std::cmp::PartialOrd;
use std::fmt::Display;

fn compare_and_display<T, U>(statement: T, num_1: U, num_2: U)
where
    T: Display,
    U: Display + PartialOrd,
{
    println!("{}! Is {} greater than {}? {}", statement, num_1, num_2, num_1 > num_2);
}

fn main() {
    compare_and_display("Listen up!", 9, 8);
}
```

استفاده از `where` ایده‌ی خوبی هست وقتی با چندین نوع `Generic` سروکار داریم.

همچین به نکات توجه کنید:

- اگه یک نوع `Generic` دارید به نام `T` و یک نوع دیگه هم با نم `T` دارید، اونها باید یکی باشند
- اگه یک نوع `Generic` به نام `T` دارید و یک نوع دیگه با نام `U`، اونها هم میتونند یکی باشند و هم متفاوت از هم، که خب منطقی هست

برای مثال:

```rust
use std::fmt::Display;

fn say_two<T: Display, U: Display>(statement_1: T, statement_2: U) { // Type T needs Display, type U needs Display
    println!("I have two things to say: {} and {}", statement_1, statement_2);
}

fn main() {

    say_two("Hello there!", String::from("I hate sand.")); // Type T is a &str, but type U is a String.
    say_two(String::from("Where is Padme?"), String::from("Is she all right?")); // Both types are String.
}
```

خروجیش:

```text
I have two things to say: Hello there! and I hate sand.
I have two things to say: Where is Padme? and Is she all right?
```

## Option and Result

ما مفهوم `Enum` ها و `Generic` ها رو فهمیدیم، پس الان میتونیم به راحتی `Option` و `Result` رو هم بفهمیم.

با `Option` شروع میکنیم.

### Option

وقتی از `Option` استفاده میکنیم که شاید مقداری وچود داشته باشه، و شاید هم نداشته باشه.

وقتی مقداری وجود داشته باشه این `Enum` مقدارش میشه، `Some(value)` و وقتی مقداری نداشته باشه میشه `None`. در زیر یکسری کد نامناسب میبینیم که میتونم با استفاده از `Option` بهتر بنویسیمش:

```rust
    // ⚠️
fn take_fifth(value: Vec<i32>) -> i32 {
    value[4]
}

fn main() {
    let new_vec = vec![1, 2];
    let index = take_fifth(new_vec);
}
```

وقتی این کد رو اجرا کنیم، `Panic` اتفاق میوفته و متوقف میشه و چنین پیامی میده:
```text
thread 'main' panicked at 'index out of bounds: the len is 2 but the index is 4', src\main.rs:34:5
```

اصطلاح `Panic` به این معنی هست که برنامه متوقف میشه درست قبل از زمانی که مشکل اتفاق بیوفته. در کد بالا `Rust` میبینه که فانکشن چیزی رو میخواد که غیرممکن هست و خب برنامه رو متوقف میکنه.

خب بیاید نوع بازگشتی فانکشن رو از `i32` به `Option<i32>` تغییر بدیم. این به معنای این هست که مقدار بازگشتی یا `Some(i32)` هست و یا `None` هست.

همچنین به این توجه کنید نوع بازگشتی یک `Enum`ای به نام `Option` هست که یک `Generic` هم هست. و طرز کارش اینطوری هست که دو حالت داره یا هیچ چیزی درش نگه نمیداره و مقدارش `None` هست و یا یک مقدار از نوعی که بهش معرفی شده رو درون `Some` در خودش نگه میداره.

```rust
fn take_fifth(value: Vec<i32>) -> Option<i32> {
    if value.len() < 5 { // .len() gives the length of the vec.
                         // It must be at least 5.
        None
    } else {
        Some(value[4])
    }
}

fn main() {
    let new_vec = vec![1, 2];
    let bigger_vec = vec![1, 2, 3, 4, 5];
    println!("{:?}, {:?}", take_fifth(new_vec), take_fifth(bigger_vec));
}
```

خروجی کد بالا `None, Some(5)` هست، الان خوب شد، چون دیگه `Panic` نمیکنه، اما چطوری مقدار `5` رو بگیریم؟

ما میتونیم با استفاده از `()unwrap.` مقدار داخل یک `Option` رو اگه هست بگیریم،‌ اگه مقداری درش نباشه، یا بهتر بگم مقدارش `None` باشه، `Panic` میکنه:
```rust
// ⚠️
fn take_fifth(value: Vec<i32>) -> Option<i32> {
    if value.len() < 5 {
        None
    } else {
        Some(value[4])
    }
}

fn main() {
    let new_vec = vec![1, 2];
    let bigger_vec = vec![1, 2, 3, 4, 5];
    println!("{:?}, {:?}",
        take_fifth(new_vec).unwrap(), // this one is None. .unwrap() will panic!
        take_fifth(bigger_vec).unwrap()
    );
}
```

پیامی که میده:
```text
thread 'main' panicked at 'called `Option::unwrap()` on a `None` value', src\main.rs:14:9
```
اما مجبور نیستیم از `()unwrap.` استفاده کنیم که امکان `Panic` وجود داشته باشه. میتونیم و بهتره که از `match` استفاده کنیم:
```rust
fn take_fifth(value: Vec<i32>) -> Option<i32> {
    if value.len() < 5 {
        None
    } else {
        Some(value[4])
    }
}

fn handle_option(my_option: Vec<Option<i32>>) {
  for item in my_option {
    match item {
      Some(number) => println!("Found a {}!", number),
      None => println!("Found a None!"),
    }
  }
}

fn main() {
    let new_vec = vec![1, 2];
    let bigger_vec = vec![1, 2, 3, 4, 5];
    let mut option_vec = Vec::new(); // Make a new vec to hold our options
                                     // The vec is type: Vec<Option<i32>>. That means a vec of Option<i32>.

    option_vec.push(take_fifth(new_vec)); // This pushes "None" into the vec
    option_vec.push(take_fifth(bigger_vec)); // This pushes "Some(5)" into the vec

    handle_option(option_vec); // handle_option looks at every option in the vec.
                               // It prints the value if it is Some. It doesn't touch it if it is None.
}
```

خروجیش:
```text
Found a None!
Found a 5!
```
بخاطر اینکه ما فهمیدیم که `Generic` ها چی هستند، میتونیم کدی که برای `Option` نوشته شده رو بخونیم. چیزی شبیه به این هست:

```rust
enum Option<T> {
    None,
    Some(T),
}

fn main() {}
```

نکته مهمی برای یاداوری: `Option` یک `Generic` هست و طبق تعریفی که شده هر نوعی رو میپذیره. و دو حالت داره، `None` که عملا هیچی نیست، و `Some` که یک مقدار از نوع `T` که میتونه هر چیزی باشه رو در خودش ذخیره میکنه.

پس نمیتونیم درون `match` چنین چیزی بنویسیم:

```rust
// 🚧
Some(value) => println!("The value is {}", value),
None(value) => println!("The value is {}", value),
```

به این دلیل که `None` هیچی رو در خودش ذخیره نمیکنه. و "هیچ" هست.

البته راه های راحت‌تری هم وجود دارند، در کد زیر ما از `.is_some()` استفاده میکنیم. (و بله، `.is_none()` هم وچود داره)


```rust
fn take_fifth(value: Vec<i32>) -> Option<i32> {
    if value.len() < 5 {
        None
    } else {
        Some(value[4])
    }
}

fn main() {
    let new_vec = vec![1, 2];
    let bigger_vec = vec![1, 2, 3, 4, 5];
    let vec_of_vecs = vec![new_vec, bigger_vec];
    for vec in vec_of_vecs {
        let inside_number = take_fifth(vec);
        if inside_number.is_some() {
            // .is_some() returns true if we get Some, false if we get None
            println!("We got: {}", inside_number.unwrap()); // now it is safe to use .unwrap() because we already checked
        } else {
            println!("We got nothing.");
        }
    }
}
```

چیزی که پرینت میکنه:

```text
We got nothing.
We got: 5
```

### Result

راستش `Result` هم شبیه به `Option` هست اما تفاوت هایی داره:

- `Option` میگه که مقداری هست یا نیست
- `Reuslt` میگه که خطایی وجود داره یا مشکلی وچود نداره

پس وقتی که فکر میکنیم "که شاید مقداری وجود داشته باشه شاید هم نه" باید از `Option` استفاده کنیم و وقتی که فکر میکنیم که "شاید خطایی رخ بده" باید از `Result` استفاده کنیم.


کدشون رو میتونیم اینجا ببینیم:
```rust
enum Option<T> {
    None,
    Some(T),
}

enum Result<T, E> {
    Ok(T),
    Err(E),
}

fn main() {}
```
پس `Result` رو حالت داره، `Ok` و `Err` که هر دوشون مقداری رو در خودشون میتونند نگه دارند، `Ok` مقدار `T` که هر چیزی میتونه باشه رو در خودش نگه میداره و `Err` مقدار `E` که هرچیزی میتونه باشه رو در خودش نگه میداره. ما اینطوری ازش استفاده میکنیم که `T` رو برابر با مقداری که اگه خطایی رخ نده باید بگیریم قرار میدیم و `E` رو برابر با نوع خطایی که امکان داره رخ بده قرار میدیم.

حالت `Err` به این دلیل مقداری رو در خودش ذخیره میکنه که ما به عنوان یک برنامه‌نویس باید خطایی که رخ داده رو شرح بدیم که امکان رفعش وجود داشته باشه.

مقدار `Ok` و `Err` هر چیزی میتونه باشه یعنی کد زیر هم حتی مشکلی نداره:

```rust
fn check_error() -> Result<(), ()> {
    Ok(())
}

fn main() {
    check_error();
}
```

ما در `check_error` فقط حالت `Ok` رو برگردوندیم، به همین دلیل کامپایلر یه اخطاری بهمون میده:

```text
warning: unused `std::result::Result` that must be used
 --> src\main.rs:6:5
  |
6 |     check_error();
  |     ^^^^^^^^^^^^^^
  |
  = note: `#[warn(unused_must_use)]` on by default
  = note: this `Result` may be an `Err` variant, which should be handled
```
خب اخطارش درسته، طبق هیچ شرایطی امکان نداره که `check_error` حالت `Err` رو برگردونه. پس بیاید یک شرایطی رو پیشبینی کنیم که برای مثال با توجه به ورودی امکان خطا وجود داشته باشه (همچنان کار معنی داری داریم انجام نمیدیم و فقط یک مثال هست):

```rust
fn give_result(input: i32) -> Result<(), ()> {
    if input % 2 == 0 {
        return Ok(())
    } else {
        return Err(())
    }
}

fn main() {
    if give_result(5).is_ok() {
        println!("It's okay, guys")
    } else {
        println!("It's an error, guys")
    }
}
```

خروجیش میشه: `It's an error, guys`

پس ما تونستیم یک `Err` رو کنترل کنیم.

یادمون باشه که چهار `Method` برای چک کردن مقدار `Option` و `Result` اینا هستند: `is_some()`, `is_none()`, `is_ok()` و `is_err`.

دوتای اولی برای `Option` هستند و دوتای دومی برای `Result` استفاده میشند.

گاهی فانکشن ها یک `String` رو به عنوان نوع خطا(`Err`) انتخاب میکنند. این بهترین روش نیست اما باز هم از اینکه مقدار `Err` هیچی نباشه بهتره:

```rust
fn check_if_five(number: i32) -> Result<i32, String> {
    match number {
        5 => Ok(number),
        _ => Err("Sorry, the number wasn't five.".to_string()), // This is our error message
    }
}

fn main() {
    let mut result_vec = Vec::new(); // Create a new vec for the results

    for number in 2..7 {
        result_vec.push(check_if_five(number)); // push each result into the vec
    }

    println!("{:?}", result_vec);
}
```

خروجی:

```text
[Err("Sorry, the number wasn\'t five."), Err("Sorry, the number wasn\'t five."), Err("Sorry, the number wasn\'t five."), Ok(5),
Err("Sorry, the number wasn\'t five.")]
```

دقیقا مثل `Option`، `()unwrap.` در `Result` هم اگه مقدار `Err` باشه، `Panic` میکنه:

```rust
    // ⚠️
fn main() {
    let error_value: Result<i32, &str> = Err("There was an error"); // Create a Result that is already an Err
    println!("{}", error_value.unwrap()); // Unwrap it
}
```

برنامه `Panic` میکنه و چنین چیزی رو چاپ میکنه:
```text
thread 'main' panicked at 'called `Result::unwrap()` on an `Err` value: "There was an error"', src\main.rs:30:20
```

اطلاعات این پیام کمک میکنه که کد رو درست بنویسیم. `src\main.rs:30:20` یعنی در دایکتوری `src` و در فایل `main.rs` و در خط `30` و حتی در ستون `20`. پس میتونیم دقیقا بریم بالا سر چیزی که باعث `Panic` شده و اون رو درست کنیم.

ما همچنین میتونیم نوع خطای خودمون رو هم درست کنیم. معمولا هم برای `Err` ما نوع های خودمون رو میسازیم، برای مثال در زیر یک کد از `Standard Library` رو میبینیم:

```rust
// 🚧
pub fn from_utf8(vec: Vec<u8>) -> Result<String, FromUtf8Error>
```
این فانکشن یک `Vec<u8>` میگیره و سعی میکنه که اون رو تبدیل به `String` کنه. در صورت موفقیت یک `String` و در صورت خطا یک `FromUtf8Error` درون `Result` برمیگردونه. ما میتونیم هر اسمی به نوع خطامون بدیم.

استفاده از `match` روی `Option` و `Result` گاهی اوقات نیازمند کد زیادی هست. برای مثال کد زیر از `Method`، `()get.` که برای `Vec` هست رو استفاده کرده. این `Method` یک `Option` برمیگردونه:

```rust
fn main() {
    let my_vec = vec![2, 3, 4];
    let get_one = my_vec.get(0); // 0 to get the first number
    let get_two = my_vec.get(10); // Returns None
    println!("{:?}", get_one);
    println!("{:?}", get_two);
}
```

This prints

```text
Some(2)
None
```
خب ما میتونیم با استفاده از `match` شرایط مختلف رو کنترل کنیم:

```rust
fn main() {
    let my_vec = vec![2, 3, 4];

    for index in 0..10 {
      match my_vec.get(index) {
        Some(number) => println!("The number is: {}", number),
        None => {}
      }
    }
}
```
این خوبه اما ما هیچکاری برای شرایطی که مقدار `None` باشه، نکردیم، به این دلیل که اگه مقدار `None` باشه اصلا ما اهمیتی بهش نمیدیم.

اینجا ما میتونیم از یک کد کوتاه از `match` هم استفاده کنیم، اون هم `if let` هست. `if let` به این معنا هست که: "فلان کار رو انجام بده اگه شرط برقرار بود، اگه نه هیچکاری نکن"

وقتی که لازم نداریم که همه‌ی شرایط رو کنترل کنیم میتونیم از `if let` استفاده کنیم:
```rust
fn main() {
    let my_vec = vec![2, 3, 4];

    for index in 0..10 {
      if let Some(number) = my_vec.get(index) {
        println!("The number is: {}", number);
      }
    }
}
```

**نکته‌ی مهم**: `if let Some(number) = my_vec.get(index)` به این معنی هست که "اگه `Some(number)` رو از `my_vec.get(index)` گرفتی".

همچنین توجه کنید که: از یک `=` استفاده کردیم

عبارت `while let` هم یک حلقه ایجاد میکنه که شبیه به `if let` هست. فکر کنید که داده‌ای شبیه به این داریم:

```text
["Berlin", "cloudy", "5", "-7", "78"]
["Athens", "sunny", "not humid", "20", "10", "50"]
```

ما میخوایم عدد هارو ازش بگیریم، اما کلمه ها رو نمیخوایم. ما میتونیم از `.parse::<i32>` برای تبدیل یک `&str` به `i32` استفاده کنیم. این `Method` یک `Result` به عنوان خروجی برمیگردونه، چون امکان داره ورودی یک عدد نباشه. همچنین از `()pop.` برای گرفتن اخرین ایتم یک `Vec` استفاده میکنیم.

```rust
fn main() {
    let weather_vec = vec![
        vec!["Berlin", "cloudy", "5", "-7", "78"],
        vec!["Athens", "sunny", "not humid", "20", "10", "50"],
    ];
    for mut city in weather_vec {
        println!("For the city of {}:", city[0]); // In our data, every first item is the city name
        while let Some(information) = city.pop() {
            // This means: keep going until you can't pop anymore
            // When the vector reaches 0 items, it will return None
            // and it will stop.
            if let Ok(number) = information.parse::<i32>() {
                // Try to parse the variable we called information
                // This returns a result. If it's Ok(number), it will print it
                println!("The number is: {}", number);
            }  // We don't write anything here because we do nothing if we get an error. Throw them all away
        }
    }
}
```

چنین چیزی رو پرینت میکنه:

```text
For the city of Berlin:
The number is: 78
The number is: -7
The number is: 5
For the city of Athens:
The number is: 50
The number is: 10
The number is: 20
```

## Other collections

زبان `Rust` مجموعه های دیگه‌ای هم داره، میتونیم در [https://doc.rust-lang.org/beta/std/collections/](https://doc.rust-lang.org/beta/std/collections/) ببینیمشون. این ها در `Standard Library` هستند. این صفحه توضیحات خوبی داره که در چه زمانی و برای چی از یک نوع میتونیم استفاده کنیم. این مجموعه ها همه در `std::collections` وجود دارند. برای استفاده ازشون باید از `use` استفاده کنیم.

با مجموعه‌‌ی `HashMap` شروع میکنیم.

### HashMap and BTreeMap

یک `HashMap` یک مجموعه از **کلید** و **مقدار** هست.

ما میتونیم با استفاده از `HashMap::new()` یک `HashMap` ایجاد کنیم.

با استفاده از `.insert(key,value)` میتونیم یک کلید و مقدار به `HashMap` اضافه کنیم.

یک `HashMap` بر اساس ترتیب داده ها رو ذخیره نمیکنه، و یک مقدار فقط با کلیدی که براش تعریف شده قابل دسترسی هست.

کد طریقه‌ی استفاده از `HashMap` هست:

```rust
use std::collections::HashMap; // This is so we can just write HashMap instead of std::collections::HashMap every time

struct City {
    name: String,
    population: HashMap<u32, u32>, // This will have the year and the population for the year
}

fn main() {

    let mut tallinn = City {
        name: "Tallinn".to_string(),
        population: HashMap::new(), // So far the HashMap is empty
    };

    tallinn.population.insert(1372, 3_250); // insert three dates
    tallinn.population.insert(1851, 24_000);
    tallinn.population.insert(2020, 437_619);


    for (year, population) in tallinn.population { // The HashMap is HashMap<u32, u32> so it returns a two items each time
        println!("In the year {} the city of {} had a population of {}.", year, tallinn.name, population);
    }
}
```

خروجیش:

```text
In the year 1372 the city of Tallinn had a population of 3250.
In the year 2020 the city of Tallinn had a population of 437619.
In the year 1851 the city of Tallinn had a population of 24000.
```

یا برای دفعه‌ی دوم این بود:

```text
In the year 1851 the city of Tallinn had a population of 24000.
In the year 2020 the city of Tallinn had a population of 437619.
In the year 1372 the city of Tallinn had a population of 3250.
```

دیدید، ترتیبی رو رعایت نمیکنه.

اگه میخواید از چیزی مثل `HashMap` که ترتیب رو هم رعایت کنه استفاده کنید، چیزی به  اسم `BTreeMap` وجود داره. اینها خیلی شبیه به هم هستند. خب بیاید کد رو تغییر بدیم که از `HashMap` استفاده کنه(کار زیادی نداریم):

```rust
use std::collections::BTreeMap; // Just change HashMap to BTreeMap

struct City {
    name: String,
    population: BTreeMap<u32, u32>, // Just change HashMap to BTreeMap
}

fn main() {

    let mut tallinn = City {
        name: "Tallinn".to_string(),
        population: BTreeMap::new(), // Just change HashMap to BTreeMap
    };

    tallinn.population.insert(1372, 3_250);
    tallinn.population.insert(1851, 24_000);
    tallinn.population.insert(2020, 437_619);

    for (year, population) in tallinn.population {
        println!("In the year {} the city of {} had a population of {}.", year, tallinn.name, population);
    }
}
```

الان همیشه چنین خروجی میده، چون ترتیب مهم هست:
```text
In the year 1372 the city of Tallinn had a population of 3250.
In the year 1851 the city of Tallinn had a population of 24000.
In the year 2020 the city of Tallinn had a population of 437619.
```

خب برگردیم به `HashMap`.

برای گرفتن یک مقدار از `HashMap` باید **کلید** رو درون `[]` قرار بدیم.
برای مثال در کد زیر ما با استفاده از **کلید**، `Bielefeld`، مقدار `Germany` رو گرفتیم. اما باید مراقب بود، اگه کلیدی بدیم که وجود نداشته باشه، برنامه `Crash` میکنه.

اگه هر وقت اطمینان نداشتیم که یک **کلید** وجود خواهد داشت یا نه، میتونیم از `()get.` استفاده کنیم که یک `Option` برمیگردونه. اگه وجود داشته باشه یک `Some(value)` برمیگردونه و اگه وجود نداشته باشه یک `None` برمیگردونه. و خب برنامه دیگه `Crash` نمیکنه. به همین دلیل `()get.` امن تر از گرفتن مقدار به طور مستفیم از `HashMap` هست.

```rust
use std::collections::HashMap;

fn main() {
    let canadian_cities = vec!["Calgary", "Vancouver", "Gimli"];
    let german_cities = vec!["Karlsruhe", "Bad Doberan", "Bielefeld"];

    let mut city_hashmap = HashMap::new();

    for city in canadian_cities {
        city_hashmap.insert(city, "Canada");
    }
    for city in german_cities {
        city_hashmap.insert(city, "Germany");
    }

    println!("{:?}", city_hashmap["Bielefeld"]);
    println!("{:?}", city_hashmap.get("Bielefeld"));
    println!("{:?}", city_hashmap.get("Bielefeldd"));
}
```

خروجیش:

```text
"Germany"
Some("Germany")
None
```
چنین خروجی‌ای میده به این دلیل که کلید `Bielefeld` وجود داره،‌ اما `Bielefeldd` وجود نداره.

اگه یک کلید و مقدار جدید وارد کنیم که کلیدش تکراری باشه، مقدار جدید جای مقدار قدیم رو میگیره:

```rust
use std::collections::HashMap;

fn main() {
    let mut book_hashmap = HashMap::new();

    book_hashmap.insert(1, "L'Allemagne Moderne");
    book_hashmap.insert(1, "Le Petit Prince");
    book_hashmap.insert(1, "섀도우 오브 유어 스마일");
    book_hashmap.insert(1, "Eye of the World");

    println!("{:?}", book_hashmap.get(&1));
}
```

خروجیش میشه: `Some("Eye of the World")`

برای چک کردن وجود داشتن یک کلید هم میتونید از `()get.` استفاده کنیم:

```rust
use std::collections::HashMap;

fn main() {
    let mut book_hashmap = HashMap::new();

    book_hashmap.insert(1, "L'Allemagne Moderne");

    if book_hashmap.get(&1).is_none() { // is_none() returns a bool: true if it's None, false if it's Some
        book_hashmap.insert(1, "Le Petit Prince");
    }

    println!("{:?}", book_hashmap.get(&1));
}
```

خروجیش میشه: `Some("L\'Allemagne Moderne")`

به این دلیل که چون کلید `1` وجود داشت ما مقدار `Le Petit Prince` رو در جای مقدار کلید `1` ننوشتیم.

نوع `HashMap` یک `Method` جالب به نام `().entry` داره که حتما باید دربارش صحبت کرد.

نوع `HashMap` یک `Method` جالب داره به نام `().entry`. ما میتونیم یک کلید بهش بدیم، و این `Method` در خروجی میگه که ایا این کلید در `HashMap` وجود داره یا خیر.
خود این `Method`، عمل خاصی انجام نمیده اما میتونیم روی این `Method` از `Method` های دیگه‌ای استفاده کنیم.

برای مثال میتونیم از `()or_insert.` استفاده کنیم که اگه کلید وجود نداشت مقداری رو که ما بهش میدیم رو وارد کنه. نکته‌ی جالبش اینجاست که این `Method` در خروجی یک `Mutable Reference` هم میده که میتونیم با استفاده از اون مقدار کلید رو تغییر بدیم.


در کد زیر ما در هنگام اضافه کردن یک کلید، مقدار `true` رو هم بهش اضافه میکنیم.
کد زیر به این دلیل ایتم هارو اضافه میکنه که اون کلید در `HashMap` وجود نداره:

```rust
use std::collections::HashMap;

fn main() {
    let book_collection = vec!["L'Allemagne Moderne", "Le Petit Prince", "Eye of the World", "Eye of the World"]; // Eye of the World appears twice

    let mut book_hashmap = HashMap::new();

    for book in book_collection {
        book_hashmap.entry(book).or_insert(true);
    }
    for (book, true_or_false) in book_hashmap {
        println!("Do we have {}? {}", book, true_or_false);
    }
}
```

خروجیش:

```text
Do we have Eye of the World? true
Do we have Le Petit Prince? true
Do we have L'Allemagne Moderne? true
```

اما خب این چیزی نیست که ما میخوایم، بهتره که به عنوان مقدار، تعداد هر کتاب رو  داشته باشیم، اینطوری میتونیم بدونیم که چه کتاب های تکراریی وجود دارند.

اول بزارید ببینیم که `().entry` و `().or_insert` چیکار میکنند.

خب `().entry` یک `Enum` به نام `Entry` برمیگردونه:

```rust
pub fn entry(&mut self, key: K) -> Entry<K, V> // 🚧
```

[این صفحه‌ی `Entry` هست](https://doc.rust-lang.org/std/collections/hash_map/enum.Entry.html). در کد زیر `K` به معنای کلید هست و `V` به معنای مقدار هست:

```rust
// 🚧
use std::collections::hash_map::*;

enum Entry<K, V> {
    Occupied(OccupiedEntry<K, V>),
    Vacant(VacantEntry<K, V>),
}
```

وقتی که `()or_insert.` رو صدا میزنیم، براساس `Entry` تصمیم میگیره که چه کاری باید انجام بده:

```rust
fn or_insert(self, default: V) -> &mut V { // 🚧
    match self {
        Occupied(entry) => entry.into_mut(),
        Vacant(entry) => entry.insert(default),
    }
}
```
همونطور که گفتم نکته‌ی جالبش اینجاست که یک `Mutable Reference` از مقدار رو برمیگردونه. این یعنی اینکه میتونیم مقداری که درون `HashMap` هست رو تغییر بدیم.

پس هروقت که کلید وجود نداشت مقدار `0` رو وارد میکنیم و بعد با استفاده از `Mutable Reference`‌ای که میده، ما اون مقدار رو به علاوه‌ی یک میکنیم.

خب پس کد میشه:
```rust
use std::collections::HashMap;

fn main() {
    let book_collection = vec!["L'Allemagne Moderne", "Le Petit Prince", "Eye of the World", "Eye of the World"];

    let mut book_hashmap = HashMap::new();

    for book in book_collection {
        let return_value = book_hashmap.entry(book).or_insert(0); // return_value is a mutable reference. If nothing is there, it will be 0
        *return_value +=1; // Now return_value is at least 1. And if there was another book, it will go up by 1
    }

    for (book, number) in book_hashmap {
        println!("{}, {}", book, number);
    }
}
```
بخش مهم کد `;let return_value = book_hashmap.entry(book).or_insert(0)` هست.

اگه خروجی `()or_insert.` رو نمیگرفتیم عملا اون چیزی میخواستیم اجرا نمیشد.

اما الان چه چیزی رخ میده؟

خب اگه کلید وجود نداشته باشه ما اول اون رو اضافه میکنیم و بعد هم `0` رو به عنوان مقدار بهش میدیم.
بعد با استفاده از `Mutable Reference`‌ای که به ما میده ما مقدار رو به علاوه‌ی یک میکنیم.

و در نهاست هم وقتی به اخرین کلید که `Eye of the World` هست میرسیم، `()entry.` میبینه که این کلید وجود داره پس چیزی رو به عنوان مقدار بهش نمیده اما یک `Mutable Reference` به مقدارش بهمون میده و ما هم اون رو به علاوه‌ی یک میکنیم. به این دلیل هست که خروجی کد بالا این میشه:

```text
L'Allemagne Moderne, 1
Le Petit Prince, 1
Eye of the World, 2
```

دیگه فهمیدیم که چه کارهایی میتونیم با استفاده از `()or_insert.` بکنیم.اما بزارید یک مثال دیگه هم بزنیم.

فکر کنید که ما یک نظرسنجی از زنان و مردان در مورد سیاستمدار ها کردیم، و میخوایم که ببینیم کدوم سیاستمدار بین زنان و مردان محبوب‌تر هست، کدش یه چیزی شبیه این میشه:

```rust
use std::collections::HashMap;

fn main() {
    let data = vec![ // This is the raw data
        ("male", 9),
        ("female", 5),
        ("male", 0),
        ("female", 6),
        ("female", 5),
        ("male", 10),
    ];

    let mut survey_hash = HashMap::new();

    for item in data { // This gives a tuple of (&str, i32)
        survey_hash.entry(item.0).or_insert(Vec::new()).push(item.1); // This pushes the number into the Vec inside
    }

    for (male_or_female, numbers) in survey_hash {
        println!("{:?}: {:?}", male_or_female, numbers);
    }
}
```

خروجیش:

```text
"female", [5, 6, 5]
"male", [9, 0, 10]
```
بخش مهم کد بالا `;survey_hash.entry(item.0).or_insert(Vec::new()).push(item.1)` هست.

در کد بالا اگه ببینه که برای مثال کلید `female` وجود نداره، یک `Vec` خالی به عنوان مقدار به کلید میده.

و اگه کلید وجود داشته باشه یا نداشته باشه، در هر صورت مقدار داده‌ای که داریم رو به اون `Vec` اضافه میکنه.

اگه هم کلید وجود داشته باشه دیگه یک `Vec` جدید نمیسازه و فقط داده رو اضافه میکنه.

### HashSet and BTreeSet

نوع `HashSet` مثل `HashMap` هست که فقط کلید داره و مقداری رو نگهداری نمیکنه. [صفحه‌ی مستندات `HashSet`](https://doc.rust-lang.org/std/collections/struct.HashSet.html)

در بالای صفحه‌ی مستند `HashSet` توضیح زیر رو نوشته:
`A hash set implemented as a HashMap where the value is ().`

پس نوع `HashSet` یک `HashMap`‌ای هست که مقدار نداره و فقط کلید داره.

معمولا زمانی از `HashSet` استفاده میکنیم که فقط میخوایم بدونیم که یک کلید وجود داره یا نه.

بیاید فکر کنیم که ما صدتا عدد تصادفی داریم که هر عدد بین `1` تا `100` هست. اگه اینکار رو انجام بدیم، امکان داره که بعضی اعداد چندین بار وجود داشته باشند و بعضی اعداد وجود نداشته باشند.
در ضمن `HashSet` مقادیر تکراری رو حدف میکنه.

خب بزارید یکم کد ببینیم:

```rust
use std::collections::HashSet;

fn main() {
    let many_numbers = vec![
        94, 42, 59, 64, 32, 22, 38, 5, 59, 49, 15, 89, 74, 29, 14, 68, 82, 80, 56, 41, 36, 81, 66,
        51, 58, 34, 59, 44, 19, 93, 28, 33, 18, 46, 61, 76, 14, 87, 84, 73, 71, 29, 94, 10, 35, 20,
        35, 80, 8, 43, 79, 25, 60, 26, 11, 37, 94, 32, 90, 51, 11, 28, 76, 16, 63, 95, 13, 60, 59,
        96, 95, 55, 92, 28, 3, 17, 91, 36, 20, 24, 0, 86, 82, 58, 93, 68, 54, 80, 56, 22, 67, 82,
        58, 64, 80, 16, 61, 57, 14, 11];

    let mut number_hashset = HashSet::new();

    for number in many_numbers {
        number_hashset.insert(number);
    }

    let hashset_length = number_hashset.len(); // The length tells us how many numbers are in it
    println!("There are {} unique numbers, so we are missing {}.", hashset_length, 100 - hashset_length);

    // Let's see what numbers we are missing
    let mut missing_vec = vec![];
    for number in 0..100 {
        if number_hashset.get(&number).is_none() { // If .get() returns None,
            missing_vec.push(number);
        }
    }

    print!("It does not contain: ");
    for number in missing_vec {
        print!("{} ", number);
    }
}
```

خروجیش میشه:

```text
There are 66 unique numbers, so we are missing 34.
It does not contain: 1 2 4 6 7 9 12 21 23 27 30 31 39 40 45 47 48 50 52 53 62 65 69 70 72 75 77 78 83 85 88 97 98 99
```
فرق نوع `HashSet` و `BTreeSet` این هست که، نوع `BTreeSet` مقادیر رو با ترتیب نگهداری میکنه ولی `HashMap` ترتیبی رو برای نگهداری مقادیر در نظر نمیگیره.

پس اگه مقادیر رو در `HashSet` نگهداری کنیم، ترتیبشون رو نمیدونیم و هر بار در یک ترتیبی ظاهر میشند:
```rust
for entry in number_hashset { // 🚧
    print!("{} ", entry);
}
```

شاید خروجی کد بالا این باشه: `67 28 42 25 95 59 87 11 5 81 64 34 8 15 13 86 10 89 63 93 49 41 46 57 60 29 17 22 74 43 32 38 36 76 71 18 14 84 61 16 35 90 56 54 91 19 94 44 3 0 68 80 51 92 24 20 82 26 58 33 55 96 37 66 79 73`. 

اما خب اطمینانی وجود نداره که دفعه‌ی بعد هم همین ترتیب رو داشته باشه.


اما اگه از `BTreeSet` استفاده کنیم، این مشکل رو نداریم و مقادیر با ترتیب نگهداری میشند:
```rust
use std::collections::BTreeSet; // Change HashSet to BTreeSet

fn main() {
    let many_numbers = vec![
        94, 42, 59, 64, 32, 22, 38, 5, 59, 49, 15, 89, 74, 29, 14, 68, 82, 80, 56, 41, 36, 81, 66,
        51, 58, 34, 59, 44, 19, 93, 28, 33, 18, 46, 61, 76, 14, 87, 84, 73, 71, 29, 94, 10, 35, 20,
        35, 80, 8, 43, 79, 25, 60, 26, 11, 37, 94, 32, 90, 51, 11, 28, 76, 16, 63, 95, 13, 60, 59,
        96, 95, 55, 92, 28, 3, 17, 91, 36, 20, 24, 0, 86, 82, 58, 93, 68, 54, 80, 56, 22, 67, 82,
        58, 64, 80, 16, 61, 57, 14, 11];

    let mut number_btreeset = BTreeSet::new(); // Change HashSet to BTreeSet

    for number in many_numbers {
        number_btreeset.insert(number);
    }
    for entry in number_btreeset {
        print!("{} ", entry);
    }
}
```

حالا خروجی کد بالا این میشه: `0 3 5 8 10 11 13 14 15 16 17 18 19 20 22 24 25 26 28 29 32 33 34 35 36 37 38 41 42 43 44 46 49 51 54 55 56 57 58 59 60 61 63 64 66 67 68 71 73 74 76 79 80 81 82 84 86 87 89 90 91 92 93 94 95 96`.

### BinaryHeap

نوع مجموعه‌ای `BinaryHeap` نوع جالبی هست، به این دلیل که تقریبا مقادیر رو بدون ترتیب نگهداری میکنه، اما خب به نوعی ترتیب هم داره. خب این یعنی چی؟

در ساده‌ترین شیوه‌ی توضیح میشه گفت که همیشه بزرگترین ایتم رو در عنصر `0` نگهداری میکنه. اما باقی ایتم ها بدون ترتیب نگهداری میشند:
```rust
use std::collections::BinaryHeap;

fn show_remainder(input: &BinaryHeap<i32>) -> Vec<i32> { // This function shows the remainder in the BinaryHeap. Actually an iterator would be
                                                         // faster than a function - we will learn them later.
    let mut remainder_vec = vec![];
    for number in input {
        remainder_vec.push(*number)
    }
    remainder_vec
}

fn main() {
    let many_numbers = vec![0, 5, 10, 15, 20, 25, 30]; // These numbers are in order

    let mut my_heap = BinaryHeap::new();

    for number in many_numbers {
        my_heap.push(number);
    }

    while let Some(number) = my_heap.pop() { // .pop() returns Some(number) if a number is there, None if not. It pops from the front
        println!("Popped off {}. Remaining numbers are: {:?}", number, show_remainder(&my_heap));
    }
}
```

خروجیش:

```text
Popped off 30. Remaining numbers are: [25, 15, 20, 0, 10, 5]
Popped off 25. Remaining numbers are: [20, 15, 5, 0, 10]
Popped off 20. Remaining numbers are: [15, 10, 5, 0]
Popped off 15. Remaining numbers are: [10, 0, 5]
Popped off 10. Remaining numbers are: [5, 0]
Popped off 5. Remaining numbers are: [0]
Popped off 0. Remaining numbers are: []
```

میتونید این رو چندین بار اچرا کنید، همیشه بزرگ‌ترین ایتم در عنصر اول قرار میگیره و باقی ایتم‌ها ترتیب خاصی ندارند.

خب شاید بپرسید چه زمانی از `BinaryHeap` استفاده کنیم؟

برای مثال میتونیم زمانی که نیاز داریم کارهایی رو با اولویت خاصی انجام بدیم، از `BinaryHeap` استفاده کنیم.

در کد زیر ما یک `BinaryHeap<(u8, &str)>` درست میکنیم که `u8` اولویت رو نشون میده و `&str` کاری که باید انجام بشه رو نشون میده:

```rust
use std::collections::BinaryHeap;

fn main() {
    let mut jobs = BinaryHeap::new();

    // Add jobs to do throughout the day
    jobs.push((100, "Write back to email from the CEO"));
    jobs.push((80, "Finish the report today"));
    jobs.push((5, "Watch some YouTube"));
    jobs.push((70, "Tell your team members thanks for always working hard"));
    jobs.push((30, "Plan who to hire next for the team"));

    while let Some(job) = jobs.pop() {
        println!("You need to: {}", job.1);
    }
}
```

خروجیش میشه:
```text
You need to: Write back to email from the CEO
You need to: Finish the report today
You need to: Tell your team members thanks for always working hard
You need to: Plan who to hire next for the team
You need to: Watch some YouTube
```

### VecDeque

نوع `VecDeque` شبیه به `Vec` هست اما برای برداشت ایتم هم از اخر و هم از اول بهینه هست. `Rust` نوع `VecDeque` رو داره به این دلیل که نوع `Vec` برای گرفتن اخرین عنصر بهینه عمل میکنه اما اگه بخوای اولین ایتم رو از `Vec` بگیری، باید همه‌ی عنصر ها به سمت چپ حرکت کنند و این هزینه‌ی زیادی داره.

این رو میتونید در توضیحات `()remove.` ببینیم:
```text
Removes and returns the element at position index within the vector, shifting all elements after it to the left.
```
(عنصری که در `index`‌ای که مشخص شده برداشته و حذف میشه و تمام عناصر بعد اون به سمت چپ جابجا میشند)


پس اگه اینکار رو انجام بدیم:
```rust
fn main() {
    let mut my_vec = vec![9, 8, 7, 6, 5];
    my_vec.remove(0);
}
```
مقدار `9` از `Vec` حذف و برگردونده میشه و تمام عناصر به سمت چپ جابجا میشند، یعنی مقدار `8` در `index`، `0` قرار میگیره و `7` در `1` و...

برای مثال کد زیر فشار بسیار زیادی بر روی `CPU` وارد میکنه. در حقیقت اگه در `Playground` بخوایم اجراش کنیم، احتمالا به دلیل فشار زیادی که وارد میکنه اصلا اجرا نمیشه:

```rust
fn main() {
    let mut my_vec = vec![0; 600_000];
    for i in 0..600000 {
        my_vec.remove(0);
    }
}
```

کد بالا یک `Vec` با `600000` صفر ایجاد میکنه. و `600000` بار، هر بار عنصر `0` رو حذف میکنه و بقیه عناصر به سمت چپ جابجا میشند.

وقتی از `VecDeque` استفاده کنیم دیگه نیازی به نگرانی در مورد این موضوع نداریم. معمولا `VecDeque` یکم از `Vec` کند‌تر هست، اما اگه میخوایم کارهایی بر روی هم اول و هم اخر یک مجموعه‌ای مثال `Vec` انجام بدیم، بهتره از `VecDeque` استفاده کنیم. چون در انجام اینکار سریع هست.

میتونیم با استفاده از `VecDeque::from` یک `VecDeque` با استفاده از `Vec` بسازیم:

```rust
use std::collections::VecDeque;

fn main() {
    let mut my_vec = VecDeque::from(vec![0; 600000]);
    for i in 0..600000 {
        my_vec.pop_front(); // pop_front is like .pop but for the front
    }
}
```

کد بالا هزینه‌ی بسیار کمتری به `CPU` وارد میکنه و سریع و بهینه هم هست.

در کد زیر، ما کار هایی رو برای انجام در یک `Vec` داریم. بعد یک `VecDeque` میسازیم و کار ها رو با استفاده از `()push_front.` درش وارد میکنیم که در اولش وارد میشه.

هر ایتمی که وارد میکنیم یک `(str, bool&)` هست. که `str&`، توضیحات رو نشون میده و `bool` میگه که کار انجام شده یا خیر. ما با استفاده از `()done` یک ایتم رو از اخر برمیداریم (که به طور خودکار از `VecDeque` حذف هم میشه) و مقدار `bool` رو به `true` تغییر میدیم که بفهمیم انجام شده، و چون نمیخوایم که ایتم حذف بشه، دوباره با استفاده از `()push_front.` به `VecDeque` اضافش میکنیم.

پس کدمون چنین چیزی میشه:

```rust
use std::collections::VecDeque;

fn check_remaining(input: &VecDeque<(&str, bool)>) { // Each item is a (&str, bool)
    for item in input {
        if item.1 == false {
            println!("You must: {}", item.0);
        }
    }
}

fn done(input: &mut VecDeque<(&str, bool)>) {
    let mut task_done = input.pop_back().unwrap(); // pop off the back
    task_done.1 = true;                            // now it's done - mark as true
    input.push_front(task_done);                   // put it at the front now
}

fn main() {
    let mut my_vecdeque = VecDeque::new();
    let things_to_do = vec!["send email to customer", "add new product to list", "phone Loki back"];

    for thing in things_to_do {
        my_vecdeque.push_front((thing, false));
    }

    done(&mut my_vecdeque);
    done(&mut my_vecdeque);

    check_remaining(&my_vecdeque);

    for task in my_vecdeque {
        print!("{:?} ", task);
    }
}
```

خروجیش:

```text
You must: phone Loki back
("add new product to list", true) ("send email to customer", true) ("phone Loki back", false)
```

## The ? operator

یک روش کوتاه‌تر برای کار با `Result` و `Option` هم وجود داره، کوتاه‌تر از `match` و حتی کوتاه‌تر از `if let`. بهش میگیم `"Question Mark Operator"`، و کاراکترش `"?"` هست. میتونیم بعد از فانکشنی که `Result` برمیگردونه استفاده کنیم. خب حالا این اپراتور جیکار میکنه؟

- اگه مقدار درون `Result`، `Ok` باشه، اون مقدار رو برمیگردونه

- اگه مقدار درون `Result`، `Err` باشه، اون `Error` رو از فانکشن `return` میکنه

پس تقریبا همه کار برای ما میکنه.

بیاید با `()parse.` امتحانش کنیم. یک فانکشن مینویسیم که تلاش میکنه یک `&str` رو تبدیل به یک `i32` کنه:

```rust
use std::num::ParseIntError;

fn parse_str(input: &str) -> Result<i32, ParseIntError> {
    let parsed_number = input.parse::<i32>()?; // Here is the question mark
    Ok(parsed_number)
}

fn main() {}
```

این فانکشن یک `&str` به عنوان ورودی میگیره. بعد سعی میکنه که اون رو تبدیل به `i32` کنه، نتیجه‌ی این کار یک `Result` هست، ما هم از `?` استفاده کردیم، پس اگه نتیجه‌ی عملیات `Err` باشه، همون لحظه اون `Err` به عنوان خروجی فانکشن در نظر گرفته میشه و فانکشن تموم میشه. اگه هم که تبدیل به درستی انجام بشه، ما نتیجه رو در یک `Ok` به عنوان خروجی فانکشن به بیرون مبفرستیم.

حالا فانکشن رو تست میکنیم:

```rust
fn parse_str(input: &str) -> Result<i32, std::num::ParseIntError> {
    let parsed_number = input.parse::<i32>()?;
    Ok(parsed_number)
}

fn main() {
    let str_vec = vec!["Seven", "8", "9.0", "nice", "6060"];
    for item in str_vec {
        let parsed = parse_str(item);
        println!("{:?}", parsed);
    }
}
```

خروجیش:

```text
Err(ParseIntError { kind: InvalidDigit })
Ok(8)
Err(ParseIntError { kind: InvalidDigit })
Err(ParseIntError { kind: InvalidDigit })
Ok(6060)
```

حالا چطوری فهمیدیم که باید از نوع `ParseIntError` به عنوان نوع `Err` استفاده کنیم؟ خب ما از کامپایلر میتونیم بپرسیم:
How did we find `std::num::ParseIntError`? One easy way is to "ask" the compiler again.

```rust
fn main() {
    let failure = "Not a number".parse::<i32>();
    failure.rbrbrb(); // ⚠️ Compiler: "What is rbrbrb()???"
}
```

کامپایلر این کد رو نمیفهمه و میگه که:

```text
error[E0599]: no method named `rbrbrb` found for enum `std::result::Result<i32, std::num::ParseIntError>` in the current scope
 --> src\main.rs:3:13
  |
3 |     failure.rbrbrb();
  |             ^^^^^^ method not found in `std::result::Result<i32, std::num::ParseIntError>`
```

پس `std::result::Result<i32, std::num::ParseIntError>` چیزی هست که ما ازش فهمیدیم از جه نوع خطایی باید استفاده کنیم.

ما نیاز نداریم `std::result::Result` رو بنویسیم، به این دلیل که `Result` همیشه در کد قابل دسترس هست(در `Scope` هست). `Rust` این کار رو برای نوع هایی که همیشه استفاده میکنیم، انجام میدیم.

نوع هایی مثل: `std::result::Result`, `std::collections::Vec`

ما هنوز با فایل ها کار نکردیم، پس `?` همچین کاربردی بنظر نمیرسه. اما یک مثال میزنم که بفهمیم چقدر میتونه کاربردی باشه.

فکر کنید به جای تبدیل مستقیم `&str` به `i32`، ما نیاز که `&str` رو به `u16`، `u16` رو به `String`، `String` رو به `i32`، تبدیل کنیم. خب اینجا میتونیم به جای کنترل کردن تمام `Result` ها از `?` استفاده کنیم و اون اینکار رو برامون انجام بده:
```rust
use std::num::ParseIntError;

fn parse_str(input: &str) -> Result<i32, ParseIntError> {
    let parsed_number = input.parse::<u16>()?.to_string().parse::<u32>()?.to_string().parse::<i32>()?; // Add a ? each time to check and pass it on
    Ok(parsed_number)
}

fn main() {
    let str_vec = vec!["Seven", "8", "9.0", "nice", "6060"];
    for item in str_vec {
        let parsed = parse_str(item);
        println!("{:?}", parsed);
    }
}
```
این همون چیزی که قبلا پرینت شده بود رو پرینت میکنه. اما ایندفعه ما تعداد زیادی `Result` رو در یک خط با `?` کنترل کردیم. وقتی نیاز داریم با فایل ها کار کنیم زیاد از `?` استفاده میکنیم. به این دلیل که در هنگام کار با فایل ها امکان داره خیلی چیز ها درست پیش نره.

در هنگام کار با فایل باید بتونیم چنین عملیاتی رو انجام بدیم که هر کدوم امکان خطا درشون وجود داره:

باز کردن فایل، نوشتن/خوندن، بستن فایل

خب ما باید شرایطی که امکان خطا درش وجود داره رو کنترل کنیم، خب اون وقت `?` خیلی بدرد بخور میشه.

### When panic and unwrap are good
(اره به زور میخواستم که کلمه به کلمه ترجمه کنم )

زبان `Rust` ماکرویی به نام `panic!` داره که میتونیم برای ساخت `Panic` ازش استفاده کنیم:

```rust
fn main() {
    panic!("Time to panic!");
}
```
پیام `"Time to panic!"` وقتی نمایش داده میشه که برنامه رو اجرا کنیم و به این خط برسیم، پیام کامل چنین چیزی میشه:
```text
`thread 'main' panicked at 'Time to panic!', src\main.rs:2:3`
```

بیاید پیام رو بررسی کنیم، یادتون هست که `src/main.rs` مسیر فایل اصلی برنامه هست. `2:3` هم خط و ستونی هست که درش `Panic` رخ داده. با این اطلاعات میتونیم به راحتی بفهمیم که چه مشکلی کجا رخ داده.

ماکروی `panic!` میتونه زمانی خوب باشه که میخوایم به برنامه‌نویس یاداوری کنیم که یه چیزی داره اشتباه پیش میره.

برای مثال در کد زیر فانکشن `prints_three_things` همیشه `Index` های [0], [1], [2] رو از یک `Vec` پرینت میکنه. این مشکلی نداره چون همیشه ما یک `Vec` با سه عنصر بهش میفرستیم و اون هم پرینت میکنه:

```rust
fn prints_three_things(vector: Vec<i32>) {
    println!("{}, {}, {}", vector[0], vector[1], vector[2]);
}

fn main() {
    let my_vec = vec![8, 9, 10];
    prints_three_things(my_vec);
}
```

خروجیش میشه: `8, 9, 10`

و همه چی ارومه و قصه‌ها خوابیدن...

اما تصور کنید که بعدا ما کد های بیشتری مینویسیم و یادمون میره که `prints_three_things` فقط باید سه عنصر رو پرینت کنه. و ما `my_vex` رو با شش عنصر میدیم به فانکشن:

```rust
fn prints_three_things(vector: Vec<i32>) {
  println!("{}, {}, {}", vector[0], vector[1], vector[2]);
}

fn main() {
  let my_vec = vec![8, 9, 10, 10, 55, 99]; // Now my_vec has six things
  prints_three_things(my_vec);
}
```

هیچ خطایی رخ نمیده به این دلیل که `Vec` حداقل سه عنصر داره. اما فکر کنید که این واقعا مهم باشه که فقط `Vec` ورودی سه عنصر داشته باشه. خب اینطوری که نمیفهمیم مشکلی پیش اومده، پس میتونیم از `Panic` استفاده کنیم که برنامه‌نویس بفهمه که یه مشکلی پیش اومده.

پس باید کد رو به چنین چیزی تغییر بدیم:

```rust
fn prints_three_things(vector: Vec<i32>) {
    if vector.len() != 3 {
        panic!("my_vec must always have three items") // will panic if the length is not 3
    }
    println!("{}, {}, {}", vector[0], vector[1], vector[2]);
}

fn main() {
    let my_vec = vec![8, 9, 10];
    prints_three_things(my_vec);
}
```

کد زیر `Panic` میکنه چون ما کاری کردیم که باید `Panic` کنه، اینطوری میفهمیم که یه مشکلی وجود داره:
```rust
    // ⚠️
fn prints_three_things(vector: Vec<i32>) {
    if vector.len() != 3 {
        panic!("my_vec must always have three items")
    }
    println!("{}, {}, {}", vector[0], vector[1], vector[2]);
}

fn main() {
    let my_vec = vec![8, 9, 10, 10, 55, 99];
    prints_three_things(my_vec);
}
```

پیامی که نشون میده چنین چیزی هست: `thread 'main' panicked at 'my_vec must always have three items', src\main.rs:8:9`.

با تشکر از `panic!`، حالا ما میدونیم که `prints_three_things` حتما باید ورودی بگیره که سه عنصر داشته باشه.

پس `panic!` یک یاداور خوبی هست.

چند ماکروی دیگه هم هست که شبیه به `panic!` هستند، که خیلی در تست ها ازشون استفاده میکنیم، اونها `assert!`, `assert_eq!`, `assert_ne!`.

بزارید ببینیم چیکار میکنند:

- `assert!()`: اگه شرط درون `()` مقدار `true` رو برنگردونه، برنامه `Panic` میکنه
- `assert_eq!()`: ایتم هایی که درون `()` هستند باید برابر باشند
- `assert_ne!()`: ایتم هایی که درون `()` هستند باید برابر نباشند

چند مثال:
```rust
fn main() {
    let my_name = "Loki Laufeyson";

    assert!(my_name == "Loki Laufeyson");
    assert_eq!(my_name, "Loki Laufeyson");
    assert_ne!(my_name, "Mithridates");
}
```
کد بالا `Panic` نمیکنه چون ما شروطی گذاشتیم که نکنه.

ما میتونیم یک پیام برای `Panic` هم تنظیم کنیم:
```rust
fn main() {
    let my_name = "Loki Laufeyson";

    assert!(
        my_name == "Loki Laufeyson",
        "{} should be Loki Laufeyson",
        my_name
    );
    assert_eq!(
        my_name, "Loki Laufeyson",
        "{} and Loki Laufeyson should be equal",
        my_name
    );
    assert_ne!(
        my_name, "Mithridates",
        "You entered {}. Input must not equal Mithridates",
        my_name
    );
}
```

این پیام ها فقط در صورتی که برنامه `Panic` کنه نمایش داده میشند:
```rust
fn main() {
    let my_name = "Mithridates";

    assert_ne!(
        my_name, "Mithridates",
        "You enter {}. Input must not equal Mithridates",
        my_name
    );
}
```

خروجیش:

```text
thread 'main' panicked at 'assertion failed: `(left != right)`
  left: `"Mithridates"`,
 right: `"Mithridates"`: You entered Mithridates. Input must not equal Mithridates', src\main.rs:4:5
```

همچنین استفاده از `unwrap` زمانی خوب هست که میخوایم اگه برنامه به مشکلی خورد، `Crash` کنه. بعدا که کدمون تکمیل شد بهتره که `unwrap` رو به چیزی تغییر بدیم که برنامه کرش نکنه و مشکل رو کنترل کنیم.


همچنین میتونیم از `expect` استفاده کنیم، که شبیه به `unwrap` هست اما کمی بهتر هست چون میتونیم پیامی رو هم همراه با `Panic` بفرستیم. معمولا اموزش های `Rust` پیشنهاد میکنند که بهتره از `()expect.` استفاده کنیم.

کد زیر `Crash` میکنه:
```rust
   // ⚠️
fn get_fourth(input: &Vec<i32>) -> i32 {
    let fourth = input.get(3).unwrap();
    *fourth
}

fn main() {
    let my_vec = vec![9, 0, 10];
    let fourth = get_fourth(&my_vec);
}
```

پیام خطاش چنین چیزی هست: `thread 'main' panicked at 'called Option::unwrap() on a None value', src\main.rs:7:18`.

ما الا با استفاده از `expect` پیام خودمون رو مینویسیم:

```rust
   // ⚠️
fn get_fourth(input: &Vec<i32>) -> i32 {
    let fourth = input.get(3).expect("Input vector needs at least 4 items");
    *fourth
}

fn main() {
    let my_vec = vec![9, 0, 10];
    let fourth = get_fourth(&my_vec);
}
```

همچنان `Crash` میکنه اما پیام خطا بهتر شده: `thread 'main' panicked at 'Input vector needs at least 4 items', src\main.rs:7:18`. `()expect.`

این یکم از `()unwrap.` بهتره چون پیام بهتری میده

کد زیر یک مثالی از نوشتن کد بد هست، چون امکان  `Crash` کردن هست و کنترلی نشده.
```rust
fn try_two_unwraps(input: Vec<Option<i32>>) {
    println!("Index 0 is: {}", input[0].unwrap());
    println!("Index 1 is: {}", input[1].unwrap());
}

fn main() {
    let vector = vec![None, Some(1000)]; // This vector has a None, so it will panic
    try_two_unwraps(vector);
}
```
پیامی که میده: ``thread 'main' panicked at 'called `Option::unwrap()` on a `None` value', src\main.rs:2:32``

خب ما اطمینان نداریم که در اولین `()unwrap.`، `Crash` رخ داده یا دومی. در اولین مرحله که بهتره اول طول `Vec` رو چک کنیم که با `Crash` کردن برنامه مواجه نشیم. اما خب یک میتونیم از `()expect.` هم استفاده کنیم که حداقل بدونیم مشکل در کدوم خط رخ داده:

```rust
fn try_two_unwraps(input: Vec<Option<i32>>) {
    println!("Index 0 is: {}", input[0].expect("The first unwrap had a None!"));
    println!("Index 1 is: {}", input[1].expect("The second unwrap had a None!"));
}

fn main() {
    let vector = vec![None, Some(1000)];
    try_two_unwraps(vector);
}
```

پیام که میده: `thread 'main' panicked at 'The first unwrap had a None!', src\main.rs:2:32`.

الان شماره‌ی خط رو داریم و میتونیم بفهمیم که مشکل کجا رخ داده.

همچنین میتونیم از `unwrap_or` استفاده کنیم، وقتی از `unwrap_or` استفاده میکنیم، اگه مشکلی پیش بیاد دیگه برنامه `Crash` نمیکنه و اگه مشکلی پیش بیاد مقداری که ما مشخص کردیم رو برمیگردونه.

استفاده از `unwrap_or` خوبه چون برنامه دیگه `Panic` نمیکنه.

البته اگه بخوایم برنامه `Panic` کنه استفاده ازش خب خوب نیست.

اما خب معمولا نمیخوایم که برنامه `Panic` کنه و بهتره ز `unwrap_or` استفاده کنیم:
```rust
fn main() {
    let my_vec = vec![8, 9, 10];

    let fourth = my_vec.get(3).unwrap_or(&0); // If .get doesn't work, we will make the value &0.
                                              // .get returns a reference, so we need &0 and not 0
                                              // You can write "let *fourth" with a * if you want fourth to be
                                              // a 0 and not a &0, but here we just print so it doesn't matter

    println!("{}", fourth);
}
```
خروجی کد بالا `0` هست، به این دلیل که `.unwrap_or(&0)` اگه مقدار `Vec`، `None` باشه، مقدار `0` رو میده.

## Traits

ما قبلا `Trait` ها رو دیدیم: `Debug`، `Copy`، `Clone` هر سه `Trait` هستند. برای اینکه به یک نوع یک `Trait` بدیم، باید اون `Trait` رو در اون نوع پیاده‌سازی کنیم. به این دلیل که `Debug` و... خیلی رایج هستند ما `Attribute` هایی داریم که اونهارو به صورت اتوماتیک برای یک نوع بسازیم. این اتفاق وقتی که `#[derive(Debug)]` رو مینویسیم میوفته.

```rust
#[derive(Debug)]
struct MyStruct {
    number: usize,
}

fn main() {}
```

اما `Trait` های دیگه یکم سخت‌تر هستند و ما باید خودمون اونهارو به صورت دستی پیاده‌سازی کنیم. ما میتونیم با استفاده از کلمه‌کلیدی `impl` اینکار رو انجام بدیم. برای مثال `std::ops:Add` یک `Trait` هست که دو چیز که یک نوع دارند رو با هم جمع میزنه اما خب وقتی نوعی رو خودمون میسازیم `Rust` نمیدونه که چه چیز هایی رو باید با هم جمع بزنه، پس باید خودمون پیاده‌سازیش کنیم.

برای مثال:

```rust
struct ThingsToAdd {
    first_thing: u32,
    second_thing: f32,
}

fn main() {}
```
ما میتونیم `first_thing` رو با `second_thing` جمع بزنیم، اما باید اطلاعات بیشتری به `Rust` بدیم، شاید ما میخوایم نتیجه یک `f32` باشه، چیزی شبیه به این:

```rust
// 🚧
let result = self.second_thing + self.first_thing as f32
```

شاید ما `Intger` میخوایم، چیزی شبیه به این:
```rust
// 🚧
let result = self.second_thing as u32 + self.first_thing
```

یا شاید هم میخوایم `first_thing` رو جلوی `second_thing` بنویسیم، و اینطوری بخوایم جمع بزنیم، برای مثال اگه مقادیر `55` و `33.4` هستند، ما میخوایم وقتی جمع میزنیم نتیجش بشه `5533.4` و نه `88.4`.

پس اول بیاید بفهمیم چطوری باید یک `Trait` ساخت. نکته‌ی مهم این هست که `Trait` ها رفتار/ویژگی ها رو مشخص میکنند.

برای ساخت یک `Trait` باید از کلمه‌کلیدی `trait` استفاده کنیم و بعدش اسم رو بدیم و داخل بلوک کد فانکشن هایی که این `Trait` داره رو مشخص کنیم:

```rust
struct Animal { // A simple struct - an Animal only has a name
    name: String,
}

trait Dog { // The dog trait gives some functionality
    fn bark(&self) { // It can bark
        println!("Woof woof!");
    }
    fn run(&self) { // and it can run
        println!("The dog is running!");
    }
}

impl Dog for Animal {} // Now Animal has the trait Dog

fn main() {
    let rover = Animal {
        name: "Rover".to_string(),
    };

    rover.bark(); // Now Animal can use bark()
    rover.run();  // and it can use run()
}
```

این کد مشکلی نداره، اما ما نمیخوایم که `The dog is runnig` رو پرینت کنیم. ما میتونیم `Method` هایی که یک `Trait` به یک نوع میده رو تغییر بدیم البته اگه میخوایم. اما باید امضای اون `Method` رو نگه داریم. این یعنی اینکه باید همون ورودی هارو بگیریم و همون خروجی هارو بدیم و اسم هم باید همون باشه:

```rust
// 🚧
fn run(&self) {
    println!("The dog is running!");
}
```

کد `fn run(&self)` یعنی ``"fn `()run` takes `&self`, and returns nothing"``. پس نمیتونیم اینکار رو انجام بدیم:

```rust
fn run(&self) -> i32 { // ⚠️
    5
}
```

اگه کار بالا رو انجام بدیم، `Rust` چنین گیری به ما میده:
```text
   = note: expected fn pointer `fn(&Animal)`
              found fn pointer `fn(&Animal) -> i32`
```

اما میتونیم چنین کنیم:

```rust
struct Animal { // A simple struct - an Animal only has a name
    name: String,
}

trait Dog { // The dog trait gives some functionality
    fn bark(&self) { // It can bark
        println!("Woof woof!");
    }
    fn run(&self) { // and it can run
        println!("The dog is running!");
    }
}

impl Dog for Animal {
    fn run(&self) {
        println!("{} is running!", self.name);
    }
}

fn main() {
    let rover = Animal {
        name: "Rover".to_string(),
    };

    rover.bark(); // Now Animal can use bark()
    rover.run();  // and it can use run()
}
```

الان چنین چیزی پرینت میکنه: `Rover is running!`.

این مشکلی نداره چون ما داریم `()` رو برمیگردونیم، که همون چیزی هست که `Trait` مشخص کرده.

وقتی در حال ساخت یک `Trait` هستیم، میتونیم فقط امضای فانکشن هارو بدیم. اما اگه اینکار رو انجام بدیم برای هر نوع باید بدنه‌ی فانکشن هارو بنویسیم. یعنی پیاده‌سازی `Method` ها به عهده‌ی نوعی که میخواد این `Trait` رو پیاده‌سازی کنه هست:

```rust
struct Animal {
    name: String,
}

trait Dog {
    fn bark(&self); // bark() says it needs a &self and returns nothing
    fn run(&self); // run() says it needs a &self and returns nothing.
                   // So now we have to write them ourselves.
}

impl Dog for Animal {
    fn bark(&self) {
        println!("{}, stop barking!!", self.name);
    }
    fn run(&self) {
        println!("{} is running!", self.name);
    }
}

fn main() {
    let rover = Animal {
        name: "Rover".to_string(),
    };

    rover.bark();
    rover.run();
}
```
پس وقتی که داریم یک `Trait` میسازیم باید به این نکته توجه کنیم که چه فانکشن هایی رو باید ما پیاده‌سازی کنیم و چه فانکشن هایی رو باید نوع پیاده‌سازی کنه. اگه فکر کنیم که همه‌ی نوع ها باید یک پیاده‌سازی از فانکشن داشته باشند، خب بهتره که ما اون رو پیاده‌سازی کنیم. اما اگه فکر میکنیم که یک فانکشن باید با توجه به هر نوع پیاده‌سازی خاص خودش رو داشته باشه، بهتره که فقط امضا فانکشن رو مشخص کنیم.

بزارید `Trait`، `Display` رو برای `Struct` خودمون پیاده‌سازی کنیم. اول از همه `Struct` رو میسازیم:

```rust
struct Cat {
    name: String,
    age: u8,
}

fn main() {
    let mr_mantle = Cat {
        name: "Reggie Mantle".to_string(),
        age: 4,
    };
}
```
الان میخوایم که `mr_mantle` رو پرینت کنیم. پیاده‌سازی `Debug` اسون هست:

```rust
#[derive(Debug)]
struct Cat {
    name: String,
    age: u8,
}

fn main() {
    let mr_mantle = Cat {
        name: "Reggie Mantle".to_string(),
        age: 4,
    };

    println!("Mr. Mantle is a {:?}", mr_mantle);
}
```

اما `Debug` همچین بیریخت پرینت میکنه که چنین چیزی هست:

```text
Mr. Mantle is a Cat { name: "Reggie Mantle", age: 4 }
```

پس ما باید `fmt::Display` رو برای `Cat` پیاده‌سازی کنیم.

در [https://doc.rust-lang.org/std/fmt/trait.Display.html](https://doc.rust-lang.org/std/fmt/trait.Display.html) ما میتونیم مستندات `Display` رو بخونیم که میگه:

```rust
use std::fmt;

struct Position {
    longitude: f32,
    latitude: f32,
}

impl fmt::Display for Position {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        write!(f, "({}, {})", self.longitude, self.latitude)
    }
}

fn main() {}
```
بعضی از بخش های کد بالا رو ما هنوز متوجه نمیشیم، مثل `<'_>` و `f`. اما ما میتونیم بفهمیم که `Position` چی هست: این یک `Struct` هست که دو فیلد داره که نوع هر دو فیلد `f32` هست.

همچنین ما `self.longitude` و `self.latitude` رو متوجه میشیم. همجنین انگاری که `write!` شباهت زیادی به `println!` داره. پس ما میتونیم چیزی شبیه به این رو برای `Cat` پیاده‌سازی کنیم:

```rust
use std::fmt;

struct Cat {
    name: String,
    age: u8,
}

impl fmt::Display for Cat {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        write!(f, "{} is a cat who is {} years old.", self.name, self.age)
    }
}

fn main() {}
```

بزارید کد فانکشن `()main` رو هم بنویسیم:
```rust
use std::fmt;

struct Cat {
    name: String,
    age: u8,
}

impl fmt::Display for Cat {
  fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
      write!(f, "{} is a cat who is {} years old.", self.name, self.age)
  }
}

fn main() {
    let mr_mantle = Cat {
        name: "Reggie Mantle".to_string(),
        age: 4,
    };

    println!("{}", mr_mantle);
}
```
خروجی کد بالا چنین چیزی میشه:  `Reggie Mantle is a cat who is 4 years old.`

خب موفق شدیم که `Display` رو برای `Cat` پیاده‌سازی کنیم، بهتره یه نگاهی به کدی که نوشتیم بکنید.


در ضمن، اگه `Display` رو پیاده‌سازی کنیم، ما میتونیم از `()to_string.` هم استفاده کنیم:

```rust
use std::fmt;
struct Cat {
    name: String,
    age: u8,
}

impl fmt::Display for Cat {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        write!(f, "{} is a cat who is {} years old.", self.name, self.age)
    }
}

fn print_cats(pet: String) {
    println!("{}", pet);
}

fn main() {
    let mr_mantle = Cat {
        name: "Reggie Mantle".to_string(),
        age: 4,
    };

    print_cats(mr_mantle.to_string()); // Turn him into a String here
    println!("Mr. Mantle's String is {} letters long.", mr_mantle.to_string().chars().count()); // Turn him into chars and count them
}
```

خروجیش:

```text
Reggie Mantle is a cat who is 4 years old.
Mr. Mantle's String is 42 letters long.
```

نکته‌ای که باید به خاطر داشته باشید این هست که `Trait` ها رفتار یک نوع رو تا حدی مشخص میکنند.

یک نوع چه کار هایی رو میتونه انجام بده؟ یک نوع چطوری یک کار رو انجام میده؟ این ها چیز هایی هستند که `Trait` ها میتونند مشخص کنند.

اگه به `Trait` هایی که تا به حال دیدیم فکر کنید میفهمید که همشون در مورد رفتار یک نوع هستند. `Copy`، `Display`، `ToString` و...

بزارید روی یک مثال دیگه کار کنیم، ما یک بازی خیالی رو تصور میکنیم که کاراکتر های ساده‌ای هم دارند. یک کاراکتر `Monster` هست، دومیش `Wizard` هست و سومیش `Ranger` هست. کاراکتر `Monster` فقط `health` داره که ما بتونیم بهش اسیب بزنیم. بقیه فعلا چیزی ندارند. اما ما دو `Trait` میسازیم. یکی به اسم `FightClose` که باهاش میتونیم از نزدیک اسیب بزنیم و دیگری `FightFromDistance` که میتونیم باهاش از فاصله‌ی دور اسیب بزنیم. فقط `Ranger` میتونه از `FightFromDistance` استفاده کنیم. بیاید چیزی که گفتیم رو تبدیل به کد کنیم:

```rust
struct Monster {
    health: i32,
}

struct Wizard {}
struct Ranger {}

trait FightClose {
    fn attack_with_sword(&self, opponent: &mut Monster) {
        opponent.health -= 10;
        println!(
            "You attack with your sword. Your opponent now has {} health left.",
            opponent.health
        );
    }
    fn attack_with_hand(&self, opponent: &mut Monster) {
        opponent.health -= 2;
        println!(
            "You attack with your hand. Your opponent now has {} health left.",
            opponent.health
        );
    }
}
impl FightClose for Wizard {}
impl FightClose for Ranger {}

trait FightFromDistance {
    fn attack_with_bow(&self, opponent: &mut Monster, distance: u32) {
        if distance < 10 {
            opponent.health -= 10;
            println!(
                "You attack with your bow. Your opponent now has {} health left.",
                opponent.health
            );
        }
    }
    fn attack_with_rock(&self, opponent: &mut Monster, distance: u32) {
        if distance < 3 {
            opponent.health -= 4;
        }
        println!(
            "You attack with your rock. Your opponent now has {} health left.",
            opponent.health
        );
    }
}
impl FightFromDistance for Ranger {}

fn main() {
    let radagast = Wizard {};
    let aragorn = Ranger {};

    let mut uruk_hai = Monster { health: 40 };

    radagast.attack_with_sword(&mut uruk_hai);
    aragorn.attack_with_bow(&mut uruk_hai, 8);
}
```

خروجیش:

```text
You attack with your sword. Your opponent now has 30 health left.
You attack with your bow. Your opponent now has 20 health left.
```

ما `self` رو همیشه در `Trait` ها میدیم، اما فعلا نمیتونیم باهاش کاری انجام بدیم چون `Rust` نمیدونه که `self` از چه نوعی هست و به همین خاطر نمیدونه که چه قابلیت هایی داره. برای اینکه بتونیم از قابلیت های `self` استفاده کنیم باید با استفاده از `Trait` ها به `Rust` بگیم که `self` چه چیز هایی رو پیاده‌سازی کرده و اینطوری میتونیم از قابلیت هاش استفاده کنیم. برای مثال اگه میخوایم `self` رو با استفاده از `{:?}` پرینت کنیم، اون باید `Debug` رو پیاده‌سازی کرده باشه. برای اینکه بگیم `self` چه چیز هایی رو باید پیاده‌سازی کرده باشه میتونیم بعد از اسم `Trait` کاراکتر `:` رو بزاریم و اسم `Trait` هایی که باید پیاده‌سازی کرده باشه رو نام ببریم. پس کدمون میشه چیزی شبیه به این:

```rust
struct Monster {
    health: i32,
}

#[derive(Debug)] // Now Wizard has Debug
struct Wizard {
    health: i32, // Now Wizard has health
}
#[derive(Debug)] // So does Ranger
struct Ranger {
    health: i32, // So does Ranger
}

trait FightClose: std::fmt::Debug { // Now a type needs Debug to use FightClose
    fn attack_with_sword(&self, opponent: &mut Monster) {
        opponent.health -= 10;
        println!(
            "You attack with your sword. Your opponent now has {} health left. You are now at: {:?}", // We can now print self with {:?} because we have Debug
            opponent.health, &self
        );
    }
    fn attack_with_hand(&self, opponent: &mut Monster) {
        opponent.health -= 2;
        println!(
            "You attack with your hand. Your opponent now has {} health left.  You are now at: {:?}",
            opponent.health, &self
        );
    }
}
impl FightClose for Wizard {}
impl FightClose for Ranger {}

trait FightFromDistance: std::fmt::Debug { // We could also do trait FightFromDistance: FightClose because FightClose needs Debug
    fn attack_with_bow(&self, opponent: &mut Monster, distance: u32) {
        if distance < 10 {
            opponent.health -= 10;
            println!(
                "You attack with your bow. Your opponent now has {} health left.  You are now at: {:?}",
                opponent.health, self
            );
        }
    }
    fn attack_with_rock(&self, opponent: &mut Monster, distance: u32) {
        if distance < 3 {
            opponent.health -= 4;
        }
        println!(
            "You attack with your rock. Your opponent now has {} health left.  You are now at: {:?}",
            opponent.health, self
        );
    }
}
impl FightFromDistance for Ranger {}

fn main() {
    let radagast = Wizard { health: 60 };
    let aragorn = Ranger { health: 80 };

    let mut uruk_hai = Monster { health: 40 };

    radagast.attack_with_sword(&mut uruk_hai);
    aragorn.attack_with_bow(&mut uruk_hai, 8);
}
```

الان چنین چیزی رو پرینت میکنه:
```text
You attack with your sword. Your opponent now has 30 health left. You are now at: Wizard { health: 60 }
You attack with your bow. Your opponent now has 20 health left.  You are now at: Ranger { health: 80 }
```

در یک بازی واقعی احتمالا باید هر نوع این فانکشن هارو برای خودش پیاده‌سازی بکنه. به این دلیل که `` احتمالا مسخره هست، اما فهمیدیم که چرا `Method` های داخل `Trait` ها ساده هستند، به این دلیل که نوعی که قرار این رو پیاده‌سازی کنه رو نمیدونیم و نمیتونیم از قابلیت هاش استفاده کنیم. برای مثال نمیتونیم کدی مثال `self.0 += 10` رو بنویسیم.

اما این مثال نشون داد که میتونیم از `Trait` ها داخل `Trait` هایی که داریم مینویسیم استفاده کنیم.

میتونیم به نحو دیگه‌ای هم از `Trait` ها استفاده کنیم، که بهش میگیم `Trait Bounds`. با اینکار میتونیم با استفاده از `Trait` ها محدودیت ایجاد کنیم.

بزارید کدی که نوشتیم رو برای این مثال تغییر بدیم، ایندفعه از `Method` ها استفاده نمیکنیم، و از فانکشن های جنریکی استفاده میکنیم که از `Trait` ها استفاده میکنند:

```rust
use std::fmt::Debug;  // So we don't have to write std::fmt::Debug every time now

struct Monster {
    health: i32,
}

#[derive(Debug)]
struct Wizard {
    health: i32,
}
#[derive(Debug)]
struct Ranger {
    health: i32,
}

trait Magic{} // No methods for any of these traits. They are just trait bounds
trait FightClose {}
trait FightFromDistance {}

impl FightClose for Ranger{} // Each type gets FightClose,
impl FightClose for Wizard {}
impl FightFromDistance for Ranger{} // but only Ranger gets FightFromDistance
impl Magic for Wizard{}  // and only Wizard gets Magic

fn attack_with_bow<T: FightFromDistance + Debug>(character: &T, opponent: &mut Monster, distance: u32) {
    if distance < 10 {
        opponent.health -= 10;
        println!(
            "You attack with your bow. Your opponent now has {} health left.  You are now at: {:?}",
            opponent.health, character
        );
    }
}

fn attack_with_sword<T: FightClose + Debug>(character: &T, opponent: &mut Monster) {
    opponent.health -= 10;
    println!(
        "You attack with your sword. Your opponent now has {} health left. You are now at: {:?}",
        opponent.health, character
    );
}

fn fireball<T: Magic + Debug>(character: &T, opponent: &mut Monster, distance: u32) {
    if distance < 15 {
        opponent.health -= 20;
        println!("You raise your hands and cast a fireball! Your opponent now has {} health left. You are now at: {:?}",
    opponent.health, character);
    }
}

fn main() {
    let radagast = Wizard { health: 60 };
    let aragorn = Ranger { health: 80 };

    let mut uruk_hai = Monster { health: 40 };

    attack_with_sword(&radagast, &mut uruk_hai);
    attack_with_bow(&aragorn, &mut uruk_hai, 8);
    fireball(&radagast, &mut uruk_hai, 8);
}
```

خروجیش میشه:
```text
You attack with your sword. Your opponent now has 30 health left. You are now at: Wizard { health: 60 }
You attack with your bow. Your opponent now has 20 health left.  You are now at: Ranger { health: 80 }
You raise your hands and cast a fireball! Your opponent now has 0 health left. You are now at: Wizard { health: 60 }
```

خب دیدیم که راه های زیادی برای استفاده از `Trait` ها وجود داره. که ما براساس چیزی که میخوایم انتخابشون کنیم.
So you can see there are many ways to do the same thing when you use traits. It all depends on what makes the most sense for the program that you are writing.

خب حالا بزارید ببینیم چطور باید از `Trait` های اصلی استفاده کنیم.

### The From trait

استفاده از `From` خیلی اسون هست. تا الان هم خیلی ارش استفاده کردیم.

با استفاده از `From`، میتونیم `str&` رو به `String` تبدیل کنیم. اما همچنین میتونیم خیلی نوع ها رو به نوع های دیگه باهاش تبدیل کنیم.

برای مثال نوع `Vec` با استفاده از `From` میتونه خیلی چیز ها رو به `Vec` تبدیل کنه:

```text
From<&'_ [T]>
From<&'_ mut [T]>
From<&'_ str>
From<&'a Vec<T>>
From<[T; N]>
From<BinaryHeap<T>>
From<Box<[T]>>
From<CString>
From<Cow<'a, [T]>>
From<String>
From<Vec<NonZeroU8>>
From<Vec<T>>
From<VecDeque<T>>
```

خیلی از این هارو هنوز استفاده نکردیم، بزارید امتحان کنیم:

```rust
use std::fmt::Display; // We will make a generic function to print them so we want Display

fn print_vec<T: Display>(input: &Vec<T>) { // Take any Vec<T> if type T has Display
    for item in input {
        print!("{} ", item);
    }
    println!();
}

fn main() {

    let array_vec = Vec::from([8, 9, 10]); // Try from an array
    print_vec(&array_vec);

    let str_vec = Vec::from("What kind of vec will I be?"); // An array from a &str? This will be interesting
    print_vec(&str_vec);

    let string_vec = Vec::from("What kind of vec will a String be?".to_string()); // Also from a String
    print_vec(&string_vec);
}
```

چنین چیزی رو پرینت میکنه:

```text
8 9 10
87 104 97 116 32 107 105 110 100 32 111 102 32 118 101 99 32 119 105 108 108 32 73 32 98 101 63
87 104 97 116 32 107 105 110 100 32 111 102 32 118 101 99 32 119 105 108 108 32 97 32 83 116 114 105 110 103 32 98 101 63
```
اگه به نوع ها نگاه کنیم، میفهمیم که اولین و دومین `Vec` ها `Vec<u8>` هستند. که یعنی بایت های `str&` و `String` هستند.

خب بزارید `From` رو روی نوعی که خودمون میسازیم استفاده کنیم:

ما دو `Struct` میسازیم و بعد `From` رو براشون پیاده‌سازی میکنیم. یکی `City` هست و دیگری `Country` هست.

ما میخوایم که در نهایت بتونیم از چنین چیزی استفاده کنیم: `let country_name = Country::from(vector_of_cities)`

خب کدش چنین چیزی میشه:

```rust
#[derive(Debug)] // So we can print City
struct City {
    name: String,
    population: u32,
}

impl City {
    fn new(name: &str, population: u32) -> Self { // just a new function
        Self {
            name: name.to_string(),
            population,
        }
    }
}
#[derive(Debug)] // Country also needs to be printed
struct Country {
    cities: Vec<City>, // Our cities go in here
}

impl From<Vec<City>> for Country { // Note: we don't have to write From<City>, we can also do
                                   // From<Vec<City>>. So we can also implement on a type that
                                   // we didn't create
    fn from(cities: Vec<City>) -> Self {
        Self { cities }
    }
}

impl Country {
    fn print_cities(&self) { // function to print the cities in Country
        for city in &self.cities {
            // & because Vec<City> isn't Copy
            println!("{:?} has a population of {:?}.", city.name, city.population);
        }
    }
}

fn main() {
    let helsinki = City::new("Helsinki", 631_695);
    let turku = City::new("Turku", 186_756);

    let finland_cities = vec![helsinki, turku]; // This is the Vec<City>
    let finland = Country::from(finland_cities); // So now we can use From

    finland.print_cities();
}
```

چنین چیزی رو پرینت میکنه:

```text
"Helsinki" has a population of 631695.
"Turku" has a population of 186756.
```

خب پس پیاده‌سازی `From` اسون هست.

در مثال زیر ما یک `Vec` میسازیم که دو `Vec` رو در خودش داره. اولین `Vec` اعداد زوج رو نگه میداره و دومی اعداد فرد رو نگه میداره. ما با استفاده از `From` یک `Vec<i32>` میدیم و اون، اعداد زوج رو در اولین `Vec` میریزه و اعداد فرد رو در دومین `Vec` میریزه:

```rust
use std::convert::From;

struct EvenOddVec(Vec<Vec<i32>>);

impl From<Vec<i32>> for EvenOddVec {
    fn from(input: Vec<i32>) -> Self {
        let mut even_odd_vec: Vec<Vec<i32>> = vec![vec![], vec![]]; // A vec with two empty vecs inside
                                                                    // This is the return value but first we must fill it
        for item in input {
            if item % 2 == 0 {
                even_odd_vec[0].push(item);
            } else {
                even_odd_vec[1].push(item);
            }
        }
        Self(even_odd_vec) // Now it is done so we return it as Self (Self = EvenOddVec)
    }
}

fn main() {
    let bunch_of_numbers = vec![8, 7, -1, 3, 222, 9787, -47, 77, 0, 55, 7, 8];
    let new_vec = EvenOddVec::from(bunch_of_numbers);

    println!("Even numbers: {:?}\nOdd numbers: {:?}", new_vec.0[0], new_vec.0[1]);
}
```

چنین چیزی رو پرینت میکنه:

```text
Even numbers: [8, 222, 0, 8]
Odd numbers: [7, -1, 3, 9787, -47, 77, 55, 7]
```
نوعی مثل `EvenOddVec` بهتر بود که جنریک باشه که بتونه با نوع های بیشتری کار کنه. برای تمرین میتونید جنریکش کنید.

### Taking a String and a &str in a function

گاهی اوقات به فانکشنی نیاز داریم که بتونه هم `String` و هم `str&` رو در یک متغییر به عنوان ورودی بگیره.

ما میتونیم با استفاده از `Trait`، `AsRef` اینکار رو انجام بدیم.

با استفاده از `AsRef` میتونیم یک `Reference` به یک نوع رو به یک `Reference` به نوع دیگه‌ای تبدیل کنیم.

اگه به صفحه‌ی مستندات `String` نگاه کنیم میتونیم ببینیم که `AsRef` رو برای نوع های زیادی پیاده‌سازی کرده.

[https://doc.rust-lang.org/std/string/struct.String.html](https://doc.rust-lang.org/std/string/struct.String.html)

در پایین میتونیم یکسری امضای فانکشن در این رابطه رو ببینیم:

`AsRef<str>`:

```rust
// 🚧
impl AsRef<str> for String

fn as_ref(&self) -> &str
```

`AsRef<[u8]>`:

```rust
// 🚧
impl AsRef<[u8]> for String

fn as_ref(&self) -> &[u8]
```

`AsRef<OsStr>`:

```rust
// 🚧
impl AsRef<OsStr> for String

fn as_ref(&self) -> &OsStr
```

میتونیم ببینیم که `self&` رو میگیره و یک `Reference` به نوع دیگه‌ای میده.
این یعنی اینکه اگه ما یک نوع جنریک به نام `T` داشته باشیم. میتونیم بگیم که اون باید `AsRef<str>` رو پیاده‌سازی کرده باشه. اگه این کار رو انجام بدیم، نوعی که میگیریم میتونه هم `str&` باشه و هم `String`.

بزارید یک فانکشن جنریک درست کنیم، این هنوز کار نمیکنه:

```rust
fn print_it<T>(input: T) {
    println!("{}", input) // ⚠️
}

fn main() {
    print_it("Please print me");
}
```

کامپایلر خطای `error[E0277]: T doesn't implement std::fmt::Display` رو میده، پس نوع `T` باید `Display` رو پیاده‌سازی کرده باشه:

```rust
use std::fmt::Display;

fn print_it<T: Display>(input: T) {
    println!("{}", input)
}

fn main() {
    print_it("Please print me");
}
```
الان کار میکنه و `Please print me` رو پرینت میکنه.

خب خوبه، اما همچنان نوع `T` میتونه خیلی چیز ها باشه، یعنی هر چیزی که `Display` رو پیاده‌سازی کرده باشه.

پس `AsRef<str>` رو اضافه میکنیم، الان `T` باید هم `Display` و هم `AsRef<str>` رو پیاده‌سازی کرده باشه:

```rust
use std::fmt::Display;

fn print_it<T: AsRef<str> + Display>(input: T) {
    println!("{}", input)
}

fn main() {
    print_it("Please print me");
    print_it("Also, please print me".to_string());
    // print_it(7); <- This will not print
}
```

الان فانکشن `print_it` نوعی مثل `i8` رو به عنوان ورودی نمیتونه بگیره.

همچنین فراموش نکنیم که میتونیم از `where` هم استفاده کنیم. معمولا زمانی که تعریف فانکشن طولانی میشه ایده‌ی خوبی هست که از `where` استفاده کنیم.

برای مثال اگه ما `Debug` رو هم اضافه کنیم، خط طولانی‌ای میشه و خب اونوقت بهتره که کد رو اینطوری بنویسیم:

```rust
use std::fmt::{Debug, Display}; // add Debug

fn print_it<T>(input: T) // Now this line is easy to read
where
    T: AsRef<str> + Debug + Display, // and these traits are easy to read
{
    println!("{}", input)
}

fn main() {
    print_it("Please print me");
    print_it("Also, please print me".to_string());
}
```

## Chaining methods

زبان `Rust` یک زبان برای برنامه‌نویسی سیستمی مثل `C` و `++C` هست. و کدش میتونه در دستور های جدا نوشته بشه. اما همچنین از سبک زبان های برنامه‌نویسی تابعی پشتیبانی میکنه. هردو سبک خوب هستند، اما معمولا سبک تابعی کوتاه‌تر هست.

در کد زیر سبک دستوری(`Imperative`) رو میبینیم:

```rust
fn main() {
    let mut new_vec = Vec::new();
    let mut counter = 1;

    while counter < 11 {
        new_vec.push(counter);
        counter += 1;
    }

    println!("{:?}", new_vec);
}
```

خروجیش میشه: `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]`

و در زیر سبک `Functional` رو میبینیم:

```rust
fn main() {
    let new_vec = (1..=10).collect::<Vec<i32>>();
    // Or you can write it like this:
    // let new_vec: Vec<i32> = (1..=10).collect();
    println!("{:?}", new_vec);
}
```
متود `()collect.` میتونه از نوع های زیادی، مجموعه بسازه، پس بهش نوع رو میگیم.

با استفاده از سبک تابعی میتونیم متود هارو به هم زنجیر کنیم، یعنی چندین متود رو پشت‌سر هم استفاده کنیم. برای مثال:

```rust
fn main() {
    let my_vec = vec![0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

    let new_vec = my_vec.into_iter().skip(3).take(4).collect::<Vec<i32>>();

    println!("{:?}", new_vec);
}
```
در کد بالا مقدار `[3, 4, 5, 6]` در متغییر `new_vec` قرار میگیره.

این همه کد رو وقتی در یک خط میبینیم، خوندش سخت میشه، پس بهتره هر متود رو در یک خط استفاده کنیم، مثل زیر:

```rust
fn main() {
    let my_vec = vec![0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

    let new_vec = my_vec
        .into_iter() // "iterate" over the items (iterate = work with each item inside it). into_iter() gives us owned values, not references
        .skip(3) // skip over three items: 0, 1, and 2
        .take(4) // take the next four: 3, 4, 5, and 6
        .collect::<Vec<i32>>(); // put them in a new Vec<i32>

    println!("{:?}", new_vec);
}
```

وقتی که `Closure` ها و `Iterator` ها رو فهمیدیم، میفهمیم که چقدر سبک تابعی کاربردی هست.

خب پس بیاید یادشون بگیریم.

## Iterators

یک `Iterator` یک ساختار است که میتواند ایتم های موحود در یک مجموعه یکی یکی به ما بده. در حقیقت ما همین الانش هم خیلی از `Iterator` ها استفاده کردیم.

حلقه‌ی `for` یک `Iterator` میده. چندین نوع `Iterator` وجود داره:
- متود `()iter.` یک `Reference` به ایتم رو میده
- متود `()iter_mut.` یک `Mutable Reference` به یک ایتم رو میده
- متود `()into_iter.` خود مقدار رو میده و برخلاف بقیه `Reference` نمیده


حلقه‌ی `for` در حقیقت یک `Iterator` هست که مقدار رو میده، به همین دلیل هست که میتونیم `Mutable` کنیمش و مقدار رو تغییر بدیم.

میتونیم از `Iterator` ها اینطوری استفاده کنیم:

```rust
fn main() {
    let vector1 = vec![1, 2, 3]; // we will use .iter() and .into_iter() on this one
    let vector1_a = vector1.iter().map(|x| x + 1).collect::<Vec<i32>>();
    let vector1_b = vector1.into_iter().map(|x| x * 10).collect::<Vec<i32>>();

    let mut vector2 = vec![10, 20, 30]; // we will use .iter_mut() on this one
    vector2.iter_mut().for_each(|x| *x +=100);

    println!("{:?}", vector1_a);
    println!("{:?}", vector2);
    println!("{:?}", vector1_b);
}
```

خروجیش:

```text
[2, 3, 4]
[110, 120, 130]
[10, 20, 30]
```

در دوتای اولی ما از متود `()map.` استفاده کردیم که اجازه میده هر بار با یک ایتم یه کاری کنیم و بعدش اون رو به عنوان خروجی میده.

در اخری ما از متود `()for_each.` استفاده کردیم که اجازه میده یه کاری به مقدار انجام بدیم و چیزی هم به عنوان خروجی نمیده.

متود `()iter_mut.` و `for_each` در کنار هم، دقیقا مثل یک حلقه‌ی `for` عمل میکنند.

در هر متود با میتونیم به ایتمی که هر بار بهمون میده یک اسم بدیم، که ما `x` رو انتخاب کردیم.

به این ها `Closure` میگیم که بعدا دربارشون میخونیم.

بزارید دوباره ببینیم که در کد بالا چیکار کردیم.

اول، ما از `()iter.` روی `vector1` استفاده کردیم که هر بار به ما یک `Reference` به ایتم رو میده. و وقتی که `Reference` رو میگیریم اون رو به علاوه‌ی `1` میکنیم و به عنوان خروجی میدیم. برای اینکه مقدار هایی رو که `()map.` به عنوان خروجی میده رو در جایی نگهداری کنیم از `()collect.` استفاده کردیم که به ما اجازه میده یک مجموعه بسازیم. به این دلیل که ما با `Reference` به ایتم ها دسترسی داشتیم و مالکیتشون تغییری نکرده، `vector1` هنوز قابل استفاده هست. و یک `vector1_a` هم درست کردیم که همون مقدار های `vector1` رو داره اما هر ایتم به علاوه‌ی `1` شده.

دوم، ما از `()into_iter.` استفاده کردیم که خود مقدار هر ایتم رو به ما میده، پس مالکیتشون هم به ما میرسه، و این یعنی `vector1` از بین میره. چون این کاری هست که `()into_iter.` انجام میده.

و در اخر ما از `()iter_mut.` روی `vector2` استفاده کردیم که هر بار به ما یک `Mutable Reference` به یک ایتم میده. خب از اونجایی که `Mutable` هست و میتونیم تغییرش بدیم، پس نیازی نداریم که یک `Vec` جدید بسازیم. عوضش ما مقدار هر ایتم رو با استفاده از `Mutable Reference` تغییر میدیم، با این کار مقدار `vector2` هم تغییر میکنه. متود `()for_each.` هم فقط یه کاری روی ایتم انجام میده و چیزی به عنوان خروجی نمیده. پس شد چیزی مثل حلقه‌ی `for` شد. یعنی ما هر بار یک `Mutable Reference` به ایتم داریم و میتونیم ازش استفاده کنیم و چیزی هم به عنوان خروجی نمیدیم.

### How an iterator works

یک `Iterator` با استفاده از متود `()next.` کار میکنه، که این متود به عنوان خروجی یک `Option` میده. وقتی از یک `Iterator` استفاده میکنیم. کامپایلر بار ها `()next.` رو صدا میزنه، اگه در خروجی `Some` بگیره ادامه میده و اگه `None` بگیره، دیگه ادامه نمیده چون دیگه ایتمی وجود نداره. دیدید چقدر سادست...

ماکروی `assert_eq!` رو یادتون هست؟ همیشه توی کد های مستدات این رو میبینیم.

در پایین میبینیم که یک `Iterator` چطوری کار میکنه:

```rust
fn main() {
    let my_vec = vec!['a', 'b', '거', '柳']; // Just a regular Vec

    let mut my_vec_iter = my_vec.iter(); // This is an Iterator type now, but we haven't called it yet

    assert_eq!(my_vec_iter.next(), Some(&'a'));  // Call the first item with .next()
    assert_eq!(my_vec_iter.next(), Some(&'b'));  // Call the next
    assert_eq!(my_vec_iter.next(), Some(&'거')); // Again
    assert_eq!(my_vec_iter.next(), Some(&'柳')); // Again
    assert_eq!(my_vec_iter.next(), None);        // Nothing is left: just None
    assert_eq!(my_vec_iter.next(), None);        // You can keep calling .next() but it will always be None
}
```
پیاده‌سازی `Iterator` برای یک `Struct` یا `Enum` ای که خودمون ساختیم زیاد سخت نیست.

برای مثال بیاید یک کتابخونه بسازیم:

```rust
#[derive(Debug)] // we want to print it with {:?}
struct Library {
    library_type: LibraryType, // this is our enum
    books: Vec<String>, // list of books
}

#[derive(Debug)]
enum LibraryType { // libraries can be city libraries or country libraries
    City,
    Country,
}

impl Library {
    fn add_book(&mut self, book: &str) { // we use add_book to add new books
        self.books.push(book.to_string()); // we take a &str and turn it into a String, then add it to the Vec
    }

    fn new() -> Self { // this creates a new Library
        Self {
            library_type: LibraryType::City, // most are in the city so we'll choose City
                                             // most of the time
            books: Vec::new(),
        }
    }
}

fn main() {
    let mut my_library = Library::new(); // make a new library
    my_library.add_book("The Doom of the Darksword"); // add some books
    my_library.add_book("Demian - die Geschichte einer Jugend");
    my_library.add_book("구운몽");
    my_library.add_book("吾輩は猫である");

    println!("{:?}", my_library.books); // we can print our list of books
}
```
این به خوبی کار میکنه، حالا ما میخوایم که برای `Library` یک `Iterator` بسازیم. اگه یک `Iterator` براش بسازیم بعدش میتونیم توی حلقه‌ی `for` ازش استفاده کنیم.

الان اگه بخوایم ازش در `for` استفاده کنیم، کامپایلر خطا میده:

```rust
for item in my_library {
    println!("{}", item); // ⚠️
}
```

خطایی که میده:

```text
error[E0277]: `Library` is not an iterator
  --> src\main.rs:47:16
   |
47 |    for item in my_library {
   |                ^^^^^^^^^^ `Library` is not an iterator
   |
   = help: the trait `std::iter::Iterator` is not implemented for `Library`
   = note: required by `std::iter::IntoIterator::into_iter`
```

خب ما میتونیم با استفاده از `impl Iterator for Library`، `Trait`، `Iterator` رو برای `Library` پیاده‌سازی کنیم.
But we can make library into an iterator with `impl Iterator for Library`

مستندات `Trait`، `Iterator` رو میتونیم اینجا پیدا کنیم: [https://doc.rust-lang.org/std/iter/trait.Iterator.html](https://doc.rust-lang.org/std/iter/trait.Iterator.html)

در سمت چپ بالا، میتونیم ببینیم که نوشته: `Associated Types: Item` و `Required Methods: next`.

خب `Associated Types: Item` ما میشه، `String`، به این دلیل که ما مجموعه‌ای از `String` ها داریم و خب هر بار باید یک `String` رو بدیم بیرون.

در همون صفحه‌ی مستند یک مثالی زده:
```rust
// an iterator which alternates between Some and None
struct Alternate {
    state: i32,
}

impl Iterator for Alternate {
    type Item = i32;

    fn next(&mut self) -> Option<i32> {
        let val = self.state;
        self.state = self.state + 1;

        // if it's even, Some(i32), else None
        if val % 2 == 0 {
            Some(val)
        } else {
            None
        }
    }
}

fn main() {}
```
ما میتونیم `type Item = 32` رو ببینیم. این همون `Associated Type` هست.

خب `Iterator` ما باید روی لیستی از کتاب ها باشه که یک `Vec<String>` هست. وقتی هم ما `()next.` رو صدا میزنیم باید یک ایتم از این مجموعه رو بدیم که یک `String` میشه. پس ما `type Item = String` رو مینویسیم.

برای پیاده‌سازی `Iterator`، ما باید فانکشن `()next` رو پیاده‌سازی کنیم. اینجا، اونجاست که تعریف میکنیم این `Iterator` چطوری باید کار کنه. برای یک کتابخونه میخوایم که کتاب ها رو از اخر بگیریم. پس از `match` و `()pop.` استفاده میکنیم که اخرین کتاب رو بگیریم. اگه خروجی `Some` بود ما اون مقدار `String` رو با `is found!` جمع میکنیم و میدیم بیرون. اگه مقدار `None` بود ما مقدار `None` رو میدیم بیرون که وقتی کامپایلر `None` رو ببینه دیگه `()next.` رو صدا نمیزنه چون میفهمه که دیگه‌ای وجود نداره.

خب کدمون این میشه:

```rust
#[derive(Debug, Clone)]
struct Library {
    library_type: LibraryType,
    books: Vec<String>,
}

#[derive(Debug, Clone)]
enum LibraryType {
    City,
    Country,
}

impl Library {
    fn add_book(&mut self, book: &str) {
        self.books.push(book.to_string());
    }

    fn new() -> Self {
        Self {
            library_type: LibraryType::City,
            // most of the time
            books: Vec::new(),
        }
    }
}

impl Iterator for Library {
    type Item = String;

    fn next(&mut self) -> Option<String> {
        match self.books.pop() {
            Some(book) => Some(book + " is found!"), // Rust allows String + &str
            None => None,
        }
    }
}

fn main() {
    let mut my_library = Library::new();
    my_library.add_book("The Doom of the Darksword");
    my_library.add_book("Demian - die Geschichte einer Jugend");
    my_library.add_book("구운몽");
    my_library.add_book("吾輩は猫である");

    for item in my_library.clone() { // we can use a for loop now. Give it a clone so Library won't be destroyed
        println!("{}", item);
    }
}
```

چیزی که پرینت میکنه:

```text
吾輩は猫である is found!
구운몽 is found!
Demian - die Geschichte einer Jugend is found!
The Doom of the Darksword is found!
```

## Closures

خب `Closure` ها مثال یک فانکشن هستند که اسم ندارند. گاهی اوقات بهشون `Lambda` هم میگیم. پیدا کردن `Closure` ها خیلی اسون هست به این دلیل که به جای `()`، علامت `||` دارند. `Closure` ها در `Rust` خیلی رایج هستند، وقتی که این ها رو یاد بگیریم بعدش میگیم که چطوری بدون این ها کد میزدیم.

میتونیم یک `Closure` رو به یک متغییر بدیم، و بعد اون متغییر دقیقا مثال یک فانکشن میشه.:

```rust
fn main() {
    let my_closure = || println!("This is a closure");
    my_closure();
}
```

خب `Closure` بالا هیچی نمیگیره و `This is a closure` رو پرینت میکنه.

ما میتونیم ورودی هایی که میخوایم رو درون `||` تعریف کنیم:

```rust
fn main() {
    let my_closure = |x: i32| println!("{}", x);

    my_closure(5);
    my_closure(5+5);
}
```

خروجیش:

```text
5
10
```
وقتی `Closure` ها طولانی و پیچیده میشند میتونیم از بلوک کد استفاده کنیم، اینطوری میتونیم هر چقدر که میخوایم طولانی بشه:
```rust
fn main() {
    let my_closure = || {
        let number = 7;
        let other_number = 10;
        println!("The two numbers are {} and {}.", number, other_number);
          // This closure can be as long as we want, just like a function.
    };

    my_closure();
}
```

اما `Closure` ها خاص هستند، به این دلیل که اونها میتونند به متغییر هایی که بیرون `Closure` هستند هم دسترسی داشته باشند:

```rust
fn main() {
    let number_one = 6;
    let number_two = 10;

    let my_closure = || println!("{}", number_one + number_two);
    my_closure();
}
```

کد بالا `16` رو پرینت میکنه.

در ضمن، اسم "بسته" هم از اینجا میاد، به این دلیل که اونها میتونند متغییر های بیرونی رو داخل خودشون "محصور" کنند. اگه بخوایم دقیق‌تر باشیم:
- یک `||`‌ای که متغییری رو که بیرون از خودش هست، در خودش محصور نمیکنه(استفاده نمیکنه) بهش میگیم `Anonymous Function`، این به معنای این هست که اسمی ندارند، مثل یک فانکشن معمولی هستند.
- یک `||`‌ای که متغییری رو که بیرون از خودش هست استفاده میکنه بهش میگیم `Closure`.


اما اغلب همه وقتی `||` رو میبینند میگند یک `Closure` هست، پس زیاد در مورد اسم نگران نباشید. اما اگه اسم `Anonymous Function` هم شنیدید، وحشت نکنید.

خب چه فایده‌ای داره که تفاوتشون رو بدونیم؟ خب به این دلیل هست که `Anonymous Function` ها دقیقا کد ماشینی مثل یک فانکشن معمولی رو تولید میکنند. اما خب در مورد `Closure` ها اوضاع فرق میکنه.

خب بیاید ببینیم `Closure` ها چه کار هایی میتونند انجام بدند:

```rust
fn main() {
    let number_one = 6;
    let number_two = 10;

    let my_closure = |x: i32| println!("{}", number_one + number_two + x);
    my_closure(5);
}
```

در بالا یک `Closure` میبینیم که `number_one` و `number_two` رو که بیرون از خودش هستند، رو استفاده میکنه و همچنین یک `x` هم به عنوان ورودی میگیره در همه اینها رو با هم جمع میزنه چاپ میکنه.

معمولا ما `Closure` ها رو در `Rust` درون یک `Method` میبینیم. در بخش قبلی ما از `Closure` ها درون `()map.` و `()for_each.` استفاده کردیم.

بزارید یک مثال دیگه ببینیم، میدونیم که میتونیم به `unwrap_or` یک مقدار بدیم که اگه نتونستیم مقدار رو بگیریم، برنامه `Panic` نکنه و مقدار ما رو به عنوان خروجی بده.

ما قبلا از `my_vec.get(3).unwrap_or(&0)` استفاده کردیم، اما یک `unwrap_or_else` هم وجود داره که به مقدار نمیگیره و یک `Closure` داخل خودش میگیره، پس میتونیم همچین کاری کنیم:

```rust
fn main() {
    let my_vec = vec![8, 9, 10];

    let fourth = my_vec.get(3).unwrap_or_else(|| { // try to unwrap. If it doesn't work,
        if my_vec.get(0).is_some() {               // see if my_vec has something at index [0]
            &my_vec[0]                             // Give the number at index 0 if there is something
        } else {
            &0 // otherwise give a &0
        }
    });

    println!("{}", fourth);
}
```

البته `Closure` ها میتونند خیلی ساده هم باشند. ما میتونیم فقط `let fourth = my_vec.get(3).unwrap_or_else(|| &0)` رو بنویسیم.

لازم نیست همیشه از `{}` استفاده کنیم و کد های پیچیده بنویسیم.

رایج ترین متودی درش از `Closure` استفاده میکنیم احتمالا `()map.` هست:

```rust
fn main() {
    let num_vec = vec![2, 4, 6];

    let double_vec = num_vec        // take num_vec
        .iter()                     // iterate over it
        .map(|number| number * 2)   // for each item, multiply by two
        .collect::<Vec<i32>>();     // then make a new Vec from this
    println!("{:?}", double_vec);
}
```

متود `()enumerate.` رو میتونیم روی یک `Iterator` استفاده کنیم. این متود ایتم و `Index`‌ اون ایتم رو در یک `Tuple` میده.

برای مثال اگه از `()enumerate.` روی `[10 ,9, 8]` استفاده کنیم، نتیجش میشه: `(0, 10), (1, 9), (2, 8)`

در کد زیر میتونیم استفاده از `()enumerate.` و `()for_each.` رو ببینیم:
```rust
fn main() {
    let num_vec = vec![10, 9, 8];

    num_vec
        .iter()      // iterate over num_vec
        .enumerate() // get (index, number)
        .for_each(|(index, number)| println!("Index number {} has number {}", index, number)); // do something for each one
}
```

خروجیش:

```text
Index number 0 has number 10
Index number 1 has number 9
Index number 2 has number 8
```

متود `()for_each` برای انجام دادن یک عملیات روی ایتم هست و خروجی نمیده.

متود `()map.` برای انجام یک عملیات روی هر ایتم و دادن اون به عنوان خروجی هست. همچنین `()map.` کاری انجام نمیده تا زمانی که از متودی مثل `()collect.` استفاده کنیم.

در حقیقت این نکته‌ی جالبی هست، اگه از `()map.` بدون متودی مثل `()collect.` استفاده کنیم، کامپایلر یک اخطار بهمون میده که این هیچ کاری رو انجام نمیده، `Panic` نمیکنه اما کامپایلر میگه که این کاری انجام نمیده.

```rust
fn main() {
    let num_vec = vec![10, 9, 8];

    num_vec
        .iter()
        .enumerate()
        .map(|(index, number)| println!("Index number {} has number {}", index, number));

}
```

اخطاری که میده:

```text
warning: unused `std::iter::Map` that must be used
 --> src\main.rs:4:5
  |
4 | /     num_vec
5 | |         .iter()
6 | |         .enumerate()
7 | |         .map(|(index, number)| println!("Index number {} has number {}", index, number));
  | |_________________________________________________________________________________________^
  |
  = note: `#[warn(unused_must_use)]` on by default
  = note: iterators are lazy and do nothing unless consumed
```

در بالا یک اخطار میبینیم و خطا نیست، پس برنامه اجرا میشه. اما چرا `num_vec` اون خط کاری انجام نمیده؟ بزارید ببینیم چیکار کردیم:

- کد `;let num_vec = vec![10, 9, 8]`،‌ یک `Vec<i32>` میده
- کد `()iter.`، یک `Iter<i32>`میده
- کد `()enumerate.`، یک `Enumerate<Iter<i32>>` میده
- کد `()map.`، یک `Map<Enumerate<Iter<i32>>>` میده

تمام کاری که کردیم این هست که ساختار پیچیده و پیچیده‌تر ساختیم. پس ``Map<Enumerate<Iter<i32>>>` یک ساختار هست که اماده‌ی استفاده هست، اما ما باید بگیم که باید با این ساختار چیکار کنیم، اگه نگیم `Rust` بدون دلیل این ساختار رو درست نمیکنه که ما باهاش هیچ کاری نکنیم. `Rust` اینکار رو انجام میده به این دلیل که نیاز داره سریع باشه.

و خب اینکار رو نمیکنه:

- یک `Iterator` رو روی `Vec<i32>` اجرا نمیکه
- روی کل خروجی `Iterator`، متود `()enumerate.` رو اجرا نمیکنه
- روی خروجی های `()enumerate.`، متود `()map.` رو اجرا نمیکنه

اگه تمام این کار ها رو انجام بده، باز هم نتیجه‌ی این کار استفاده نمیکنه. `Rust` فقط میخواد یک محاسبه رو انجام بده، پس این کار ها رو انجام نمیده تا زمانی که ما از چیزی مثل `()collect::<Vec<i32>>.` استفاده کنیم. وقتی از چنین چیزی استفاده میکنیم `Rust` میفهمه که باید چیکار کنه.

به همین دلیل هست که اخطار `iterators are lazy and do nothing unless consumed` رو میده، این یعنی اینکه `Iterator` کاری انجام نمیده تا زمانی که از خروجیش استفاده بشه.

همچنین با استفاده از `()collect.` میتونیم خروجی رو به چیز های دیگه‌ای هم تبدیل کنیم، مثل `HashMap`. پس خیلی قدرتمند هست.

در زیر یک مثالی رو میبینیم که دو `Vec` رو در یک `HashMap` میکنیم.

اول دوتا `Vec` میسازیم، بعدش از `()into_iter.` استفاده میکنیم تا یک `Iterator` بگیریم، بعدش از `()zip.` استفاده میکنیم که دوتا `Iterator` رو به هم میچسبونه. در نهایت از `()collect.` استفاده میکنیم که خروجی رو در یک `HashMap` بریزیم:

```rust
use std::collections::HashMap;

fn main() {
    let some_numbers = vec![0, 1, 2, 3, 4, 5]; // a Vec<i32>
    let some_words = vec!["zero", "one", "two", "three", "four", "five"]; // a Vec<&str>

    let number_word_hashmap = some_numbers
        .into_iter()                 // now it is an iter
        .zip(some_words.into_iter()) // inside .zip() we put in the other iter. Now they are together.
        .collect::<HashMap<_, _>>();

    println!("For key {} we get {}.", 2, number_word_hashmap.get(&2).unwrap());
}
```

خروجیش:

```text
For key 2 we get two.
```

میتونیم ببینیم که کد `<HashMap<_, _>>` نوشته شده. با اینکار `Rust` خودش نوع هارو حدس میزنه، یعنی تهش `HashMap<i32, &str>` میشه.

البته اگه بخوایم میتونیم `;collect::<HashMap<i32, &str>>()` رو بنویسیم یا حتی در نوع رو در تعریف متغییر مشخص کنیم:

```rust
use std::collections::HashMap;

fn main() {
    let some_numbers = vec![0, 1, 2, 3, 4, 5]; // a Vec<i32>
    let some_words = vec!["zero", "one", "two", "three", "four", "five"]; // a Vec<&str>
    let number_word_hashmap: HashMap<_, _> = some_numbers  // Because we tell it the type here...
        .into_iter()
        .zip(some_words.into_iter())
        .collect(); // we don't have to tell it here
}
```

یک متود دیگه هم وجود داره که شبیه به `()enumerate.` هست، البته برای نوع `char` که اون هم `char_indices()` هست.

برای مثال فکر کنید که ما یک `char` داریم که از اعداد تشکیل شده و میخوایم اون اعداد رو سه رقم سه رقم جدا کنیم:

```rust
fn main() {
    let numbers_together = "140399923481800622623218009598281";

    for (index, number) in numbers_together.char_indices() {
        match (index % 3, number) {
            (0..=1, number) => print!("{}", number), // just print the number if there is a remainder
            _ => print!("{}\t", number), // otherwise print the number with a tab space
        }
    }
}
```

خروجیش: `140     399     923     481     800     622     623     218     009     598    281`.

### |_| in a closure

گاهی وقت ها ما `|_|` رو در یک `Closure` میبینیم. این به معنی این هست که این `Closure` به ورودی نیاز داره اما نیمخوایم ازش استفاده کنیم.

در زیر یک کدی رو میبینیم که کامپایل نمیشه:

```rust
fn main() {
    let my_vec = vec![8, 9, 10];

    println!("{:?}", my_vec.iter().for_each(|| println!("We didn't use the variables at all"))); // ⚠️
}
```

کامپایلر میگه:
```text
error[E0593]: closure is expected to take 1 argument, but it takes 0 arguments
  --> src\main.rs:28:36
   |
28 |     println!("{:?}", my_vec.iter().for_each(|| println!("We didn't use the variables at all")));
   |                                    ^^^^^^^^ -- takes 0 arguments
   |                                    |
   |                                    expected closure that takes 1 argument
```

همچنین کامپایلر یه کمکی هم به ما میکنه:
```text
help: consider changing the closure to take and ignore the expected argument
   |
28 |     println!("{:?}", my_vec.iter().for_each(|_| println!("We didn't use the variables at all")));
```

خب کمک خوبی هست، پس ما `||` رو به `|_|` تغییر میدیم. بعدش کد کار میکنه.

### Helpful methods for closures and iterators

زبان `Rust` به یک زبان باحال تبدیل میشه وقتی که بتونیم با `Closure` ها کار کنیم. با استفاده از `Closure` ها میتونیم متود ها رو به هم زنجیر کنیم و کار های جالبی باهاش انجام بدیم. الان میخوایم متود های مفیدی که میتونیم استفاده کنیم رو ببینیم:

متود `()filter.`: این به ما اجازه میده که ایتم ها رو فیلتر کنیم، یک شرط میزاریم و هر ایتمی که با شرط مشکلی نداشت به عنوان خروجی در نظر گرفته میشه و اگه نتونه از شرط بگذره استفاده نمیشه. بزارید ماه های سال رو فیلتر کنیم:

```rust
fn main() {
    let months = vec!["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];

    let filtered_months = months
        .into_iter()                         // make an iter
        .filter(|month| month.len() < 5)     // We don't want months more than 5 bytes in length.
                                             // We know that each letter is one byte so .len() is fine
        .filter(|month| month.contains("u")) // Also we only like months with the letter u
        .collect::<Vec<&str>>();

    println!("{:?}", filtered_months);
}
```

خروجیش: `["June", "July"]`.

متود `.filter_map()`، هم کار `()filter.` و هم `()map.` رو انجام میده. این متود یک `Option` میگیره و یک `Option` برمیگردونه، حالا کدومارو از فیلتر رد میکنه؟ اون `Option` هایی که مقدارشون `Some` هست.

برای مثال اگه این متود رو روی `vec![Some(2), None, Some(3)]` اجرا کنیم خروجی `[2, 3]` رو میده.

ما یک مثال با استفاده از ساختار `Company` درست میکنیم. هر `Company` یک `name` داره که نوعش `String` هست، اما `CEO` شرکت شاید به تازگی شرکت رو ترک کرده باشه، پس فیلد `ceo` باید یک `Option<String>` باشه. ما از `.filter_map()` استفاده میکنیم که فقط اسم `CEO` های شرکت هایی رو بگیریم که مقدار فیلد `ceo` شون برابر `Some` هست.

```rust
struct Company {
    name: String,
    ceo: Option<String>,
}

impl Company {
    fn new(name: &str, ceo: &str) -> Self {
        let ceo = match ceo {
            "" => None,
            ceo => Some(ceo.to_string()),
        }; // ceo is decided, so now we return Self
        Self {
            name: name.to_string(),
            ceo,
        }
    }

    fn get_ceo(&self) -> Option<String> {
        self.ceo.clone() // Just returns a clone of the CEO (struct is not Copy)
    }
}

fn main() {
    let company_vec = vec![
        Company::new("Umbrella Corporation", "Unknown"),
        Company::new("Ovintiv", "Doug Suttles"),
        Company::new("The Red-Headed League", ""),
        Company::new("Stark Enterprises", ""),
    ];

    let all_the_ceos = company_vec
        .into_iter()
        .filter_map(|company| company.get_ceo()) // filter_map needs Option<T>
        .collect::<Vec<String>>();

    println!("{:?}", all_the_ceos);
}
```

خروجیش: `["Unknown", "Doug Suttles"]`.

از اونجایی که `.filter_map()` به یک `Option` نیاز داره، پس ما باید برای `Result` چیکار کنیم؟

خب مشکلی نداریم، چون یک متودی به نام `()ok.` وجود داره که یک `Result` رو به `Option` تبدیل میکنه. اسمش از اینجا میاد که فقط روی مقدار `Ok` کار میکنه. یعنی با مقدار `Err`، نوع `Result` کاری نداره.

یادمون هست که `Option` یک `Option<T>` هست اما `Result` یک `Result<T, E>` هست. پس ما نمیتونیم مقدار `Err` رو در یک `Option` بریزیم و اگه مقدار یک `Reuslt` برابر `Err` باشه ما اون رو به طور کلی به `None` تبدیل میکنیم تا بتونیم نوع `Result` رو به یک `Option` تبدیل کنیم.

استفاده از `()parse.` مثال خوبی برای این مبحث هست، ما در مثال زیر ورودی های کاربر رو شبیه سازی کردیم و میخوایم اون ها رو به `f32` تبدیل کنیم. که خب باید از متود `()parse.` استفاده کنیم که یک `Result` برمیگردونه، اما از اونجایی که ما داریم از `.filter_map()` استفاده میکنیم باید `Result` رو تبدیل به `Option` کنیم. خب ما از متود `()ok.` استفاده میکنیم که هر `Result`ای که مقدارش `Err` باشه رو به یک `Option` که مقدارش `None` هست تبدیل میکنه و هر `Result`ای که مقدارش `Ok` هست رو به یک `Option` که مقدارش `Some` هست تبدیل میکنه:

```rust
fn main() {
    let user_input = vec!["8.9", "Nine point nine five", "8.0", "7.6", "eleventy-twelve"];

    let actual_numbers = user_input
        .into_iter()
        .filter_map(|input| input.parse::<f32>().ok())
        .collect::<Vec<f32>>();

    println!("{:?}", actual_numbers);
}
```

خروجیش: `[8.9, 8.0, 7.6]`.

در سمت مخالف `()ok.`، متود `.ok_or()` و `.ok_or_else()` هست. این متود ها یک `Option` رو به یک `Result` تبدیل میکنند.

به این دلیل اسمش `.ok_or` هست که نوع `Result` مقدارش یا `Ok` هست **یا** `Err` هست. خب اینجا یه مشکلی پیش میاد اونم این هست که مقدار `None` هیچ اطلاعاتی نداره،‌ پس اگه مقدار یک `Option`، `None` بود. باید به یک `Result`‌ای که مقدارش `Err` هست تبدیل بشه اما مقدار و نوع `Err` باید چی باشه؟ خب ما باید مقدار رو درون `.ok_or()` مشخص کنیم.

همچنین متود `ok_or_else()` هم شبیه به `.ok_or()` هست با این تفاوت که به عنوان ورودی به جای یک مقدار باید یک `Closure` بهش بدیم.

برای کنترل کردن `Error` ها در یک برنامه واقعی بهتره نوع `Error` یک `Struct` باشه و ما باید اون رو بسازیم ما برای این مثال ما فقط یک پیام خطا که از نوع `&str` هست میدیم. پس نوع نهایی `.ok_or()` میشه `Result<String, &str>`.

```rust
// Everything before main() is exactly the same
struct Company {
    name: String,
    ceo: Option<String>,
}

impl Company {
    fn new(name: &str, ceo: &str) -> Self {
        let ceo = match ceo {
            "" => None,
            ceo => Some(ceo.to_string()),
        };
        Self {
            name: name.to_string(),
            ceo,
        }
    }

    fn get_ceo(&self) -> Option<String> {
        self.ceo.clone()
    }
}

fn main() {
    let company_vec = vec![
        Company::new("Umbrella Corporation", "Unknown"),
        Company::new("Ovintiv", "Doug Suttles"),
        Company::new("The Red-Headed League", ""),
        Company::new("Stark Enterprises", ""),
    ];

    let mut results_vec = vec![]; // Pretend we need to gather error results too

    company_vec
        .iter()
        .for_each(|company| results_vec.push(company.get_ceo().ok_or("No CEO found")));

    for item in results_vec {
        println!("{:?}", item);
    }
}
```

خطی که تغییر بزرگ رو ایجاد کرد این خط هست:

```rust
// 🚧
.for_each(|company| results_vec.push(company.get_ceo().ok_or("No CEO found")));
```

این خط به این معنا هست که: برای هر ایتم، مقدار `ceo` رو از طریق `.get_ceo()` بگیر، اگه مقدارش `Some` بود اون رو درون یک `Result` که مقدارش `Ok` هست قرار بده و بعد به عنوان خروجی بده بره. اما اگه مقداری که گرفتی `None` بود، بیا مقدار `No CEO found` رو درون `Result` قرار بده که مقدارش `Err` هست و تهش هم اینو به عنوان خروجی بده. و این خروجی هایی که صحبت کردیم درون متغییر `results_vec`، `push` میشند.

پس وقتی متغییر `results_vec` رو پرینت کنیم، این رو میگیریم:

```text
Ok("Unknown")
Ok("Doug Suttles")
Err("No CEO found")
Err("No CEO found")
```
خب حالا بیاید از `.ok_or_else()` استفاده کنیم که پیام های خطای بهتری بدیم بیرون. در برای ساخت پیام خطا از ماکروی `format!` استفاده میکنیم که یک `String` بسازیم و اسم شرکت هم درش قرار میدیم،‌ بعدش اون `String` رو برمیگردونیم:

```rust
// Everything before main() is exactly the same
struct Company {
    name: String,
    ceo: Option<String>,
}

impl Company {
    fn new(name: &str, ceo: &str) -> Self {
        let ceo = match ceo {
            "" => None,
            name => Some(name.to_string()),
        };
        Self {
            name: name.to_string(),
            ceo,
        }
    }

    fn get_ceo(&self) -> Option<String> {
        self.ceo.clone()
    }
}

fn main() {
    let company_vec = vec![
        Company::new("Umbrella Corporation", "Unknown"),
        Company::new("Ovintiv", "Doug Suttles"),
        Company::new("The Red-Headed League", ""),
        Company::new("Stark Enterprises", ""),
    ];

    let mut results_vec = vec![];

    company_vec.iter().for_each(|company| {
        results_vec.push(company.get_ceo().ok_or_else(|| {
            let err_message = format!("No CEO found for {}", company.name);
            err_message
        }))
    });

    for item in results_vec {
        println!("{:?}", item);
    }
}
```

خروجیش:

```text
Ok("Unknown")
Ok("Doug Suttles")
Err("No CEO found for The Red-Headed League")
Err("No CEO found for Stark Enterprises")
```

متود `.and_then()` یک متود مفید هست که یک `Option` میگیره و اجازه یه کاری باهاش انجام بدیم بعدش دوباره یک `Option` به عنوان خروجی میده بیرون.

یک مثال ساده وقتی هست از `()get.` برای گرفتن یک عدد از یک `Vec` استفاده میکنیم، به این دلیل مثال خوبی هست که یک `Option` برمیگردونه که ما میتونیم اون رو بدیم به `.and_then()` که یه کاری باهاش انجام بدیم، البته اگه مقدار `Option`ای که بهش میدیم `Some` باشه. اگه مقدار `None` باشه همون `None` برمیگرده.

```rust
fn main() {
    let new_vec = vec![8, 9, 0]; // just a vec with numbers

    let number_to_add = 5;       // use this in the math later
    let mut empty_vec = vec![];  // results go in here


    for index in 0..5 {
        empty_vec.push(
            new_vec
               .get(index)
                .and_then(|number| Some(number + 1))
                .and_then(|number| Some(number + number_to_add))
        );
    }
    println!("{:?}", empty_vec);
}
```

خروجیش: `[Some(14), Some(15), Some(6), None, None]`
میتونیم ببینیم که مقادیر `None` فیلتر نشدند و توی نتیجه‌ی نهایی هم دیده میشند.

متود `()and.` یک جورایی مثل `&&` برای `Option` هست. ما میتونیم چندین `Option` رو در شرط قرار بدیم اگه همه اونها مقدارشون `Some` باشه، مقدار اخرین `Option` رو میگیریم و اگه حتی یکی از اونها مقدارشون `None` باشه، مقدار `None` رو میگیریم.

اول بزارید برای نوع `bool` اینکار رو انجام بدیم، که مثال رو درست متوجه بشیم:
```rust
fn main() {
    let one = true;
    let two = false;
    let three = true;
    let four = true;

    println!("{}", one && three); // prints true
    println!("{}", one && two && three && four); // prints false
}
```

در پایین همون هم چیزی مشابهی رو میبینیم اما با استفاده از `()and.` و نوع `Option`.

فکر کنید که ما پنچ عملیات رو سه بار انجام دادیم و نتیجشون رو داخل یک `Vec<Option<&str>>` ریختیم:
```rust
fn main() {
    let first_try = vec![Some("success!"), None, Some("success!"), Some("success!"), None];
    let second_try = vec![None, Some("success!"), Some("success!"), Some("success!"), Some("success!")];
    let third_try = vec![Some("success!"), Some("success!"), Some("success!"), Some("success!"), None];

    for i in 0..first_try.len() {
        println!("{:?}", first_try[i].and(second_try[i]).and(third_try[i]));
    }
}
```

خروجیش:

```text
None
None
Some("success!")
Some("success!")
None
```

اولی `None` هست به این دلیل که ما یک مقدار `None` در `second_try[0]` داریم.

دومی `None` هست به این دلیل که ما یک مقدار `None` در `first_try[1]` داریم.

سومی `success!` هست به این دلیل که ما مقدار `None`ای نداریم.

بقیه رو هم میتونید بفهمید که چرا چنین خروجی رو دادند، اگه نفهمیدید دوباره توضیح متود `()and.` رو بخونید.

استفاده از متود های `()any.` و `()all.` خیلی اسون هست. اونا براساس وجودی که بهشون میدن یک مقدار از نوع `bool` میدن. در مثال زیر ما یک `Vec` بزرگ میسازیم، که کاراکتر هایی از `a` تا `働` رو در خودش داره. بعد یک فانکشن میسازیم که چک کنه ایا کاراکتر ورودی در این `Vec` وجود داره یا نه.

بعد یک `Vec` کوچیک‌تر میسازیم و چک میکنیم که ایا همه‌ی ایتم هاش `Alphabetic` هستند یا نه، برای این کار از متود `.is_alphabetic()` استفاده میکنیم که یک کاراکتر میگیره و میگه که ایا این کاراکتر `Alphabetic` هست یا خیر.

بعد چک میکنیم که ایا همه‌ی کاراکتر هایی که در `Vec` کوچیک هستند، از حرف کره‌ای `행`، کوچیک‌تر هستند یا خیر.

همچنین به این نکته توجه کنید که ما وقتی از `()iter.` استفاده میکنیم یک `Reference` به مقدار داریم پس برای مقایسه باید از `&` استفاده کنیم.

بزارید کد رو ببینیم:

```rust
fn in_char_vec(char_vec: &Vec<char>, check: char) {
    println!("Is {} inside? {}", check, char_vec.iter().any(|&char| char == check));
}

fn main() {
    let char_vec = ('a'..'働').collect::<Vec<char>>();
    in_char_vec(&char_vec, 'i');
    in_char_vec(&char_vec, '뷁');
    in_char_vec(&char_vec, '鑿');

    let smaller_vec = ('A'..'z').collect::<Vec<char>>();
    println!("All alphabetic? {}", smaller_vec.iter().all(|&x| x.is_alphabetic()));
    println!("All less than the character 행? {}", smaller_vec.iter().all(|&x| x < '행'));
}
```

خروجیش:

```text
Is i inside? true
Is 뷁 inside? false
Is 鑿 inside? false
All alphabetic? false
All less than the character 행? true
```

در ضمن، متود `()any.` فقط تا زمانی به چک کردن ادامه میده که یک ایتم هماهنگ با شرط پیدا کنه. بعد از اینکه پیدا کرد، دیگه ادامه نمیده. پس لزوما همه رو چک نمیکنه.

اگه از `()any.` روی یک `Vec` استفاده میکنیم،‌ ایده‌ی خوبی هست که ایتم هایی که ممکنه با شرط هماهنگ باشند رو اول `Vec` بزاریم که همه رو چک نکنه تا برسه به اون...

همچنین ما میتونیم با استفاده از `()rev.` یک `Vec` رو برعکس کنیم.

کد زیر رو در نظر بگیرید:

```rust
fn main() {
    let mut big_vec = vec![6; 1000];
    big_vec.push(5);
}
```

پس وکتور `big_vec` `1000` تا عدد `6` رو در خودش داره که تهش یه `5` هم اضافه شده. بزارید تصور کنیم که میخوایم چک کنیم که عدد `5` در `Vec` وجود داره یا خیر. اول بزارید اطمینان پیدا کنیم که `()rev.` کار میکنه. یادمون هست که یک `Iterator` همیشه متود `()next.` رو داره. پس میتونیم با این متود چک کنیم.
حواسمون هست که `Vec` رو با استفاده از `()rev.` برعکس کردیم:

```rust
fn main() {
    let mut big_vec = vec![6; 1000];
    big_vec.push(5);

    let mut iterator = big_vec.iter().rev();
    println!("{:?}", iterator.next());
    println!("{:?}", iterator.next());
}
```
چنین چیزی رو پرینت میکنه:

```text
Some(5)
Some(6)
```
خب همونطور که حدس میزدیم یک `5` ته `Vec` وجود داره و بعدش هزارتا `6` وجود داره.

پس چیزی که میخواستیم رو میتونیم اینطوری بنویسیم:

```rust
fn main() {
    let mut big_vec = vec![6; 1000];
    big_vec.push(5);

    println!("{:?}", big_vec.iter().rev().any(|&number| number == 5));
}
```

و به این دلیل که وکتور رو برعکس کردیم با یکبار صدا زدن `()next.` ما عدد `5` رو میگیریم و چون با شرط هماهنگ هست دیگه به چک کردن ادامه نمیده.

اگه از `()rev.` استفاده نمیکردیم،‌ باید `1001` بار چک میکردیم...

در کد زیر این قضیه ثابت میشه:

```rust
fn main() {
    let mut big_vec = vec![6; 1000];
    big_vec.push(5);

    let mut counter = 0; // Start counting
    let mut big_iter = big_vec.into_iter(); // Make it an Iterator

    loop {
        counter +=1;
        if big_iter.next() == Some(5) { // Keep calling .next() until we get Some(5)
            break;
        }
    }
    println!("Final counter is: {}", counter);
}
```

چنین چیزی رو پرینت میکنه: `Final counter is: 1001`

پس ما میفهمیم که مجبور شده `1001` بار متود `()next.` رو صدا بزنه و ایتمی که میده رو با شرط چک کنه.

متود `()find.` یک شرط میگیره و اگه ایتمی با اون شرط هماهنگ بود،‌ اون ایتم رو در یک `Option` میده بیرون.

متود `()position.` یک شرط میگیره و اگه ایتمی با اون شرط هماهنگ بود،‌ `Index` اون ایتم رو در یک `Option` میده بیرون.

پس:
- متود `()find.`: میگه من سعی میکنم چیزی رو که میخوای پیدا کنم و بیارم برات
- متود `()position.`: میگه من سعی میکنم مکان چیزی رو که میخوای برات پیدا کنم

بیاید با کد کار کنیم:

```rust
fn main() {
    let num_vec = vec![10, 20, 30, 40, 50, 60, 70, 80, 90, 100];

    println!("{:?}", num_vec.iter().find(|&number| number % 3 == 0)); // find takes a reference, so we give it &number
    println!("{:?}", num_vec.iter().find(|&number| number * 2 == 30));

    println!("{:?}", num_vec.iter().position(|&number| number % 3 == 0));
    println!("{:?}", num_vec.iter().position(|&number| number * 2 == 30));

}
```

کد بالا چنین چیزی رو پرینت میکنه:

```text
Some(30) // This is the number itself
None // No number inside times 2 == 30
Some(2) // This is the position
None
```

خب ما میدونیم که وقتی متود `()next.` یک `Iterator` مقدار `None` رو برگردونه، اون `Iterator` متوقف میشه.
متود `()cycle.` این روند رو میشکونه و اگه یک `Iterator` به `None` برسه، کاری میکنه که `Iterator` دوباره از اول شروع کنه. پس یک حلقه‌ی بینهایت روی اون مجموعه میزنه.

کد زیر مثال استفاده از `()cycle.` هست:
```rust
fn main() {
    let even_odd = vec!["even", "odd"];

    let even_odd_vec = (0..6)
        .zip(even_odd.into_iter().cycle())
        .collect::<Vec<(i32, &str)>>();
    println!("{:?}", even_odd_vec);
}
```
چون از `()cycle.` استفاده کردیم اون `Iterator` هیچوقت متوقف نمیشه، اما با این حال اون یکی `Iterator` بعد از شیش بار اجرا شدن متوقف میشه چون به `None` میرسه.
با استفاده از متود `()zip.` هم میتونیم دوتا مجموعه رو با هم ترکیب کنیم، خروجی کد بالا رو ببینید میفهمید که `()zip.` چیکار میکنه.

خروجی کد بالا:
```
[(0, "even"), (1, "odd"), (2, "even"), (3, "odd"), (4, "even"), (5, "odd")]
```

همچنین اگه `0..` رو بنویسیم یک بازه‌ای درست میشه که هیچوقت تموم نمیشه:

```rust
fn main() {
    let ten_chars = ('a'..).take(10).collect::<Vec<char>>();
    let skip_then_ten_chars = ('a'..).skip(1300).take(10).collect::<Vec<char>>();

    println!("{:?}", ten_chars);
    println!("{:?}", skip_then_ten_chars);
}
```

هر دو متغییر ده کاراکتر رو در خودشون نگهداری میکنند اما دومی `1300` کاراکتر رو رد کرده و بعد ده کاراکتر رو گرفته که کاراکتر های ارمنی‌ای هستند.

خروجی کد بالا:

```
['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j']
['յ', 'ն', 'շ', 'ո', 'չ', 'պ', 'ջ', 'ռ', 'ս', 'վ']
```

یک متود محبوب دیگه `()fold.` هست. این متود یک مقدار اولیه میگیره و هر بار اون مقدار و یک ایتم از مجموعه رو به `Closure` میفرسته. به این نکته توجه کنید که بعد از اینکه یک بار اجرا شد، دیگه هر بار خروجی `Closure` رو به عنوان مقدار اولیه میده.

در کد زیر میتونیم یک مثال از نحوه‌ی استفاده از `()fold.` رو ببینیم:
```rust
fn main() {
    let some_numbers = vec![9, 6, 9, 10, 11];

    println!("{}", some_numbers
        .iter()
        .fold(0, |total_so_far, next_number| total_so_far + next_number)
    );
}
```

پس:

- در قدم اول با مقدار اولیه `0` شروع کرد و بعد در `Closure` این مقدار رو با ایتمی که به عنوان ورودی اومده جمع کرد که نتیجش میده `9` و این مقدار به عنوان خروجی بیرون داده میشه
- بعد مقدار اولیه میشه `9` و با ایتم بعدی که `6` هست جمع میشه که نتیجش میشه `15`
- بعد مقدار اولیه میشه `15` و با ایتم بعدی که `9` هست جمع میشه که نتیجش میشه `24`
- بعد مقدار اولیه میشه `24` و با ایتم که `10` هست،‌ جمع زده میشه که نتیجش میشه `34`
- در اخر مقدار اولیه `34` میشه و با ایتم که `11` هست جمع زده میشه که نتیجش میشه `45` که خب چون دیگه ایتم دیگه وجود نداره `Iterator` متوقف میشه و مقدار `45` پرینت میشه

اما کار های دیگه‌ای هم میشه باهاش کرد، برای مثال میشه کاراکتر `-` رو بین هر کاراکتر در یک `String` قرار داد:

```rust
fn main() {
    let a_string = "I don't have any dashes in me.";

    println!(
        "{}",
        a_string
            .chars() // Now it's an iterator
            .fold("-".to_string(), |mut string_so_far, next_char| { // Start with a String "-". Bring it in as mutable each time along with the next char
                string_so_far.push(next_char); // Push the char on, then '-'
                string_so_far.push('-');
                string_so_far} // Don't forget to pass it on to the next loop
            ));
}
```

خروجیش:

```text
-I- -d-o-n-'-t- -h-a-v-e- -a-n-y- -d-a-s-h-e-s- -i-n- -m-e-.-
```

متود های باحال دیگه هم وجود دارند، برای مثال:
- `.take_while()` تا زمانی که شرط برقرار باشه از مجموعه ایتم رو میگیره (برای مثال `take while x > 5`)
- `()cloned.` همه‌‌ی مقادیر یک `Iterator` رو کپی میکنه، برای مثال `&i32` رو میتونه به `i32` تبدیل کنه
- `.by_ref()` که `Reference` یک `Iterator` رو میگیره که باعت میشه اون `Iterator` همچنان قابل استفاده بمونه
- متود هایی که با `_while()` تموم میشند: `.skip_while()`، `map_while()` و...
- `()sum.`: همه‌ی مقادیر رو با هم جمع میزنه

با استفاده از متود های `()chunks.` و `()windows.` میتونیم یک `Vec` رو به قسمت های کوچیک‌تر تقسیم کنیم، باید سایز رو هم به عنوان ورودی بهشون بدیم، برای مثال تصور کنید که ما یک `Vec` با `10` ایتم از `1` تا `10` داریم و از این متود ها استفاده میکنیم، سایز تقسیم رو هم `3` قرار میدیم، که ببینیم چیکار میکنند:

- `()chunks.` به ما چهار `Slice` میده: `[0, 1, 2]` بعدش `[3, 4, 5]` بعدش `[6, 7, 8]` و در اخر `[9]`. پس تلاش میکنه هر بار یک `Slice` با سه ایتم بسازه، اما اگه ایتم ها کافی نباشند، `Panic` نمیکنه و هر چیزی که باقی مونده رو در `Slice` میده.

- `()windows.` اول یک `Slice` با مقادیر `[0, 1, 2]` میده. بعد ایتم اولی رو حدف میکنه و ایتم بعدی رو داخل `Slice` میاره، پس مقادیر بعدی میشن، `[1, 2, 3]`. این کار رو تا زمانی ادامه میده که اخرین ایتم جزو `Slice` باشه، و بعد متوقف میشه.

خب بزارید ازشون روی یک `Vector` ساده استفاده کنیم:

```rust
fn main() {
    let num_vec = vec![1, 2, 3, 4, 5, 6, 7, 8, 9, 0];

    for chunk in num_vec.chunks(3) {
        println!("{:?}", chunk);
    }
    println!();
    for window in num_vec.windows(3) {
        println!("{:?}", window);
    }
}
```

چنین چیزی رو پرینت میکنه:

```text
[1, 2, 3]
[4, 5, 6]
[7, 8, 9]
[0]

[1, 2, 3]
[2, 3, 4]
[3, 4, 5]
[4, 5, 6]
[5, 6, 7]
[6, 7, 8]
[7, 8, 9]
[8, 9, 0]
```

در ضمن، متود `()chunks.`، اگه روی چیزی با طول `0` اجرا بشه `Panic` میکنه. ما میتونیم `.chunks(1000)` رو روی یک `Vec` با یک ایتم اجرا کنیم، اما نمیتونیم `()chunks.` رو روی یک چیزی با طول `0` اجرا کنیم.

اگه کد این فانکشن رو بررسی کنیم متوجه این موضوع میشیم. به این دلیل که در فانکشن کد `;assert!(chunk_size != 0)` وجود داره.

متود `.match_indices` توی یک `String` یا `&str` دنبال ورودی که بهش دادیم میگرده و اگه پیدا کرد،‌ هم خود اون رو برمیگردونه هم `Index` شروعش رو میده. شبیه به `()enumerate.` هست، چون یک `Tuple` میده که هم مقدار هست و هم `Index`.
نحوه‌ی استفاده ازش رو میتونیم در کد زیر ببینیم:

```rust
fn main() {
    let rules = "Rule number 1: No fighting. Rule number 2: Go to bed at 8 pm. Rule number 3: Wake up at 6 am.";
    let rule_locations = rules.match_indices("Rule").collect::<Vec<(_, _)>>(); // This is Vec<usize, &str> but we just tell Rust to do it
    println!("{:?}", rule_locations);
}
```

چنین چیزی رو پرینت میکنه:

```text
[(0, "Rule"), (28, "Rule"), (62, "Rule")]
```

متود `()peekable.`به ما اجازه میده که از یک `Iterator`، `Iterator`‌ای بسازیم که میتونیم تا زمانی که میخوایم روی یک ایتم بمونیم. یعنی میتونیم یک ایتم رو چندین بار با استفاده از `()peek.` بگیریم. بعد اگه خواستیم بریم روی ایتم بعدی میتونیم از `()next.` استفاده کنیم.

در کد زیر مثالی از طرز استفاده از `()peekable.` رو میبینیم:

```rust
fn main() {
    let just_numbers = vec![1, 5, 100];
    let mut number_iter = just_numbers.iter().peekable(); // This actually creates a type of iterator called Peekable

    for _ in 0..3 {
        println!("I love the number {}", number_iter.peek().unwrap());
        println!("I really love the number {}", number_iter.peek().unwrap());
        println!("{} is such a nice number", number_iter.peek().unwrap());
        number_iter.next();
    }
}
```

چنین چیزی رو پرینت میکنه:

```text
I love the number 1
I really love the number 1
1 is such a nice number
I love the number 5
I really love the number 5
5 is such a nice number
I love the number 100
I really love the number 100
100 is such a nice number
```

کد زیر یک مثال دیگه هست:

```rust
fn main() {
    let locations = vec![
        ("Nevis", 25),
        ("Taber", 8428),
        ("Markerville", 45),
        ("Cardston", 3585),
    ];
    let mut location_iter = locations.iter().peekable();
    while location_iter.peek().is_some() {
        match location_iter.peek() {
            Some((name, number)) if *number < 100 => { // .peek() gives us a reference so we need *
                println!("Found a hamlet: {} with {} people", name, number)
            }
            Some((name, number)) => println!("Found a town: {} with {} people", name, number),
            None => break,
        }
        location_iter.next();
    }
}
```

چیزی که پرینت میکنه:

```text
Found a hamlet: Nevis with 25 people
Found a town: Taber with 8428 people
Found a hamlet: Markerville with 45 people
Found a town: Cardston with 3585 people
```

در این مثال ما از `match_indices()` استفاده میکنیم. ما اسم ها رو بر اساس تعداد `Space` درون `Struct` قرار میدیم:

```rust
#[derive(Debug)]
struct Names {
    one_word: Vec<String>,
    two_words: Vec<String>,
    three_words: Vec<String>,
}

fn main() {
    let vec_of_names = vec![
        "Caesar",
        "Frodo Baggins",
        "Bilbo Baggins",
        "Jean-Luc Picard",
        "Data",
        "Rand Al'Thor",
        "Paul Atreides",
        "Barack Hussein Obama",
        "Bill Jefferson Clinton",
    ];

    let mut iter_of_names = vec_of_names.iter().peekable();

    let mut all_names = Names { // start an empty Names struct
        one_word: vec![],
        two_words: vec![],
        three_words: vec![],
    };

    while iter_of_names.peek().is_some() {
        let next_item = iter_of_names.next().unwrap(); // We can use .unwrap() because we know it is Some
        match next_item.match_indices(' ').collect::<Vec<_>>().len() { // Create a quick vec using .match_indices and check the length
            0 => all_names.one_word.push(next_item.to_string()),
            1 => all_names.two_words.push(next_item.to_string()),
            _ => all_names.three_words.push(next_item.to_string()),
        }
    }

    println!("{:?}", all_names);
}
```

چیزی که پرینت میکنه:

```text
Names { one_word: ["Caesar", "Data"], two_words: ["Frodo Baggins", "Bilbo Baggins", "Jean-Luc Picard", "Rand Al\'Thor", "Paul Atreides"], three_words:
["Barack Hussein Obama", "Bill Jefferson Clinton"] }
```

## The dbg! macro and .inspect

ماکروی `dbg!` خیلی کاربردی هست برای پرینت کردن. همچنین یک جایگزین خوب برای `println!` هست، به این دلیل که سریع تایپ میشه و اطلاعات بیشتری رو هم میده:

```rust
fn main() {
    let my_number = 8;
    dbg!(my_number);
}
```

خروجیش: `[src\main.rs:4] my_number = 8`.

اما میتونیم از `dbg!` در موارد زیادی استفاده کنیم، و حتی درونش کد قرار بدیم، برای مثال به این کد توجه کنید:

```rust
fn main() {
    let mut my_number = 9;
    my_number += 10;

    let new_vec = vec![8, 9, 10];

    let double_vec = new_vec.iter().map(|x| x * 2).collect::<Vec<i32>>();
}
```
این کد یک متغییر `Mutable` میسازه و تغییرش میده. بعد یک `Vec` درست میکنه و...

ما میتونیم `dbg!` رو تقریبا هر جای این کد قرار بدیم.

ماکروی `dbg!` یه جورایی از کامپایلر میپرسه که دقیقا در همین لحظه داری چیکار میکنی؟

کد رو ببینیم:

```rust
fn main() {
    let mut my_number = dbg!(9);
    dbg!(my_number += 10);

    let new_vec = dbg!(vec![8, 9, 10]);

    let double_vec = dbg!(new_vec.iter().map(|x| x * 2).collect::<Vec<i32>>());

    dbg!(double_vec);
}
```

خب این چنین چیزی پرینت میکنه:

```text
[src\main.rs:3] 9 = 9
```

و همچنین این:
```text
[src\main.rs:4] my_number += 10 = ()
```

و این:

```text
[src\main.rs:6] vec![8, 9, 10] = [
    8,
    9,
    10,
]
```

و این یکی که مقدار های عبارات رو نشون میده:

```text
[src\main.rs:8] new_vec.iter().map(|x| x * 2).collect::<Vec<i32>>() = [
    16,
    18,
    20,
]
```

و حتی این:

```text
[src\main.rs:10] double_vec = [
    16,
    18,
    20,
]
```

خب `.inspect` هم کمی شبیه به `dbg!` هست اما ازش مثل `map`، داخل یک `Iterator` استفاده میکنیم.

```rust
fn main() {
    let new_vec = vec![8, 9, 10];

    let double_vec = new_vec
        .iter()
        .map(|x| x * 2)
        .collect::<Vec<i32>>();
}
```

نحوه‌ی استفاده از `()inspect.`:
```rust
fn main() {
    let new_vec = vec![8, 9, 10];

    let double_vec = new_vec
        .iter()
        .inspect(|first_item| println!("The item is: {}", first_item))
        .map(|x| x * 2)
        .inspect(|next_item| println!("Then it is: {}", next_item))
        .collect::<Vec<i32>>();
}
```

جیزی که پرینت میکنه:

```text
The item is: 8
Then it is: 16
The item is: 9
Then it is: 18
The item is: 10
Then it is: 20
```
به دلیل اینکه `()inspect.` یک `Closure` به عنوان ورودی میگیره، ما میتونیم هر چقدر که میخوایم کد بنویسیم:

```rust
fn main() {
    let new_vec = vec![8, 9, 10];

    let double_vec = new_vec
        .iter()
        .inspect(|first_item| {
            println!("The item is: {}", first_item);
            match **first_item % 2 { // first item is a &&i32 so we use **
                0 => println!("It is even."),
                _ => println!("It is odd."),
            }
            println!("In binary it is {:b}.", first_item);
        })
        .map(|x| x * 2)
        .collect::<Vec<i32>>();
}
```

خروجیش:

```text
The item is: 8
It is even.
In binary it is 1000.
The item is: 9
It is odd.
In binary it is 1001.
The item is: 10
It is even.
In binary it is 1010.
```

## Types of &str

خب، باید بدونیم که نوع های بیشتری از `&str` وجود داره:

- نوع `String Literal`: این نوع از `str` ها تا اخر برنامه در حافظه وجود دارند چون در فایل باینری هستند، برای مثال زمانی که ما کد `let my_str = "I am a &str"` رو مینویسیم یک `String Literal` ساختیم. نوع این `str` ها `&'static str` هست. `'` برای مشخص کردن طول عمر استفاده میشه و طول عمر این `str`، `static` هست.

- نوع `Borrowed str`: اینها `str` های معمولی هستند، بدون داشتن طول عمر `static`. برای مثال اگه ما یک `String` بسازیم و یک `Reference` بهش رو بگیریم. `Rust` زمانی که لازم باشه اون رو به `&str` تبدیل میکنه.

بزارید در مورد تبدیل `&String` به `&str` یک مثال ببینیم:

```rust
fn prints_str(my_str: &str) { // it can use &String like a &str
    println!("{}", my_str);
}

fn main() {
    let my_string = String::from("I am a string");
    prints_str(&my_string); // we give prints_str a &String
}
```
خب حالا `LifeTime` یا همون طول عمر چیه؟ در بخش بعدی میفهمیم.

## طول عمر | Lifetimes

یک طول عمر مشخص میکنه که یک متغییر چقدر زنده بمونه، یعنی چقدر قابل استفاده باشه.

فقط زمانی که با `Reference` ها کار میکنیم باید حواسمون به `Lifetime` ها باشه. این به دلیل این هست که یک `Reference` نمیتونه بیشتر از چیزی که بهش اشاره میکنه زنده باشه، برای مثال کد زیر کار نمیکنه:

```rust
fn returns_reference() -> &str {
    let my_string = String::from("I am a string");
    &my_string // ⚠️
}

fn main() {}
```

مشکل اینجاست که `my_string` فقط داخل `returns_reference` زنده هست. و ما میخوایم `&my_string` رو بدیم بیرون، اما `&my_string` نمیتونه بدون `my_string` وجود داشته باشه.
پس کامپایلر اجازه‌ی چنین کاری رو نمیده

این کد هم کار نمیکنه:

```rust
fn returns_str() -> &str {
    let my_string = String::from("I am a string");
    "I am a str" // ⚠️
}

fn main() {
    let my_str = returns_str();
    println!("{}", my_str);
}
```

یعنی اگه مشکلش رو برطرف کنیم کار میکنه ولی الان کامپایلر چنین خطایی میده:

```text
error[E0106]: missing lifetime specifier
 --> src\main.rs:6:21
  |
6 | fn returns_str() -> &str {
  |                     ^ expected named lifetime parameter
  |
  = help: this function's return type contains a borrowed value, but there is no value for it to be borrowed from
help: consider using the `'static` lifetime
  |
6 | fn returns_str() -> &'static str {
  |                     ^^^^^^^^
```

خطای `missing lifetime specifier` یعنی ما باید طول عمر رو مشخص کنیم، ما با استفاده از `'` میتونیم طول عمر مشخص کنیم.

بعدش میگه که `contains a borrowed value, but there is no value for it to be borrowed from`، که این یعنی مقدار `I am a str` از هیچ متغییری قرض گرفته نشده.

بعدش هم میگه که `consider using the 'static lifetime`، که ما میتونیم با استفاده از `&'static str` اینکارو انجام بدیم.

کد زیر الان کار میکنه:
```rust
fn returns_str() -> &'static str {
    let my_string = String::from("I am a string");
    "I am a str"
}

fn main() {
    let my_str = returns_str();
    println!("{}", my_str);
}
```
به دلیل کار میکنه که ما یک `&str` با طول عمر `static` رو برگردوندیم.


پس کد `fn returns_str() -> &'static str` به کامپایلر میگه که: نگران نباش، ما فقط `String Literal` برمیگردونیم. که خب `String Literal` ها در طول برنامه وجود دارند و نابود نمیشند.

با استفاده از مشخص کردن `Lifetime` متیونیم طول عمر ورودی ها رو مشخص کنیم.

اما `'static` تنها `Lifetime` نیست. در حقیقت هر متغییری یک `Lifetime` داره، اما ما معمولا خودمون مشخص نمیکنیمش، به این دلیل که کامپایلر به اندازه‌ی کافی هوشمند هست که خودش بتونه مدیریت کنه. ما فقط `Lifetime` رو برای متغییر هایی مشخص میکنیم که کامپایلر نمیتونه براشون تصمیم بگیره.

در زیر یک مثال دیگه از مشخص کردن `Lifetime` میبینیم. فکر کنید که میخوایم یک ساختاری به نام `City` بسازیم که نوع یک فیلدش `&str` هست. احتمالا میخوایم اینکار رو انجام بدیم به این دلیل که این نوع بهینه‌تر از `String` هست. پس ما کد رو اینطوری مینویسیم(البته هنوز کار نمیکنه):

```rust
#[derive(Debug)]
struct City {
    name: &str, // ⚠️
    date_founded: u32,
}

fn main() {
    let my_city = City {
        name: "Ichinomiya",
        date_founded: 1921,
    };
}
```

خطایی که کامپایلر میده:

```text
error[E0106]: missing lifetime specifier
 --> src\main.rs:3:11
  |
3 |     name: &str,
  |           ^ expected named lifetime parameter
  |
help: consider introducing a named lifetime parameter
  |
2 | struct City<'a> {
3 |     name: &'a str,
  |
```

کامپایلر نیاز داره که `Lifetime` نوع `&str` مشخص بشه. به این دلیل که اون یک `Reference` هست. خب چرا نیاز داره؟ خب فکر کنید ما یک `Reference` به یک متغییر رو درش قرار دادیم، و بعد از مدتی اون متغییر از بین رفت. خب حالا اون `Reference` به چیزی اشاره میکنه که دیگه وجود نداره، و خب این امن نیست.

خب بزارید `Lifetime`، `'static` رو به اون فیلد بدیم:
```rust
#[derive(Debug)]
struct City {
    name: &'static str, // change &str to &'static str
    date_founded: u32,
}

fn main() {
    let my_city = City {
        name: "Ichinomiya",
        date_founded: 1921,
    };

    println!("{} was founded in {}", my_city.name, my_city.date_founded);
}
```
خب الان کار میکنه، اما باید حواسمون باشه که نوع فیلد `name` الان یک `String Literal` هست که باید در کل برنامه وجود داشته باشه، پس کد زیر کامپایل نمیشه،‌ به این دلیل که عناصر `city_names` برای کل برنامه وجود ندارند و میتونند از بین برند:

```rust
#[derive(Debug)]
struct City {
    name: &'static str, // must live for the whole program
    date_founded: u32,
}

fn main() {
    let city_names = vec!["Ichinomiya".to_string(), "Kurume".to_string()]; // city_names does not live for the whole program

    let my_city = City {
        name: &city_names[0], // ⚠️ This is a &str, but not a &'static str. It is a reference to a value inside city_names
        date_founded: 1921,
    };

    println!("{} was founded in {}", my_city.name, my_city.date_founded);
}
```

کامپایلر چنین چیزی میگه:

```text
error[E0597]: `city_names` does not live long enough
  --> src\main.rs:12:16
   |
12 |         name: &city_names[0],
   |                ^^^^^^^^^^
   |                |
   |                borrowed value does not live long enough
   |                requires that `city_names` is borrowed for `'static`
...
18 | }
   | - `city_names` dropped here while still borrowed
```

در حقیقت `Reference`ای که ما بهش دادیم به اندازه کافی طول عمر داره، **اما** ما بهش قول دادیم که چیزی بهش میدیم که طول عمرش برابر با کل برنامه باشه، یعنی `&'static str`. و خب این یه مشکلی هست که باید حلش کنیم.

پس ما میایم به چیزی که کامپایلر قبلا گفته بود عمل میکنیم، گفته بود که از `struct City<'a>` و `name: &'a str` استفاده کنیم. و این به معنای این هست که فقط `Reference`ای رو برای `name` میگیره که به اندازه‌ی `City` طول عمر داشته باشه:

```rust
#[derive(Debug)]
struct City<'a> { // City has lifetime 'a
    name: &'a str, // and name also has lifetime 'a.
    date_founded: u32,
}

fn main() {
    let city_names = vec!["Ichinomiya".to_string(), "Kurume".to_string()];

    let my_city = City {
        name: &city_names[0],
        date_founded: 1921,
    };

    println!("{} was founded in {}", my_city.name, my_city.date_founded);
}
```
همچنین ما میتونیم هر اسم دیگه‌ای به جای `'a` بدیم، مثل اسم های نوع های `Generic` هست که ما میتونیم `T` یا هرچیز دیگه بدیم. پس میتونیم حتی چنین چیزی رو هم بنویسیم:

```rust
#[derive(Debug)]
struct City<'city> { // The lifetime is now called 'city
    name: &'city str, // and name has the 'city lifetime
    date_founded: u32,
}

fn main() {}
```

اما خب ما معمولا از `'a` یا `'b`و... استفاده میکنیم. به این دلیل که راحت نوشته میشن. اما اگه کد پیچیده شد میتونیم از اسم هایی که مشخص‌تر هستنند استفاده کنیم که بعدا بتونیم راحت کد رو بخونیم.

بیاید `Lifetime` ها رو با `Generic` ها مقایسه کنیم. برای مثال:

```rust
use std::fmt::Display;

fn prints<T: Display>(input: T) {
    println!("T is {}", input);
}

fn main() {}
```

در کد بالا `T: Display` به این معنی هست که "لطفا `T` رو فقط زمانی بگیر که `Display` رو پیاده‌سازی کرده باشه".

و به این معنا نیست که: "`Display` رو بده به `T`"

در مورد `Lifetime` ها هم اوضاع همین هست، برای مثال وقتی که `'a` رو مینویسیم:

```rust
#[derive(Debug)]
struct City<'a> {
    name: &'a str,
    date_founded: u32,
}

fn main() {}
```

به این معنا هست که: "فقط زمانی ورودی رو قبول کن که طول عمرش حداقل برابر با `City` باشه"

و به این معنا نیست که: "طول عمر ورودی برای `name` رو برابر با طول عمر `City` کن"

خب الان میتونیم در مورد `<'_>` که قبلا دیدیم،‌ یاد بگیریم. به اینا میگن `Anonymous Lifetime`. کامپایلر زمانی که در حال ساخت `Method` ها برای یک `Struct`ای که درش از `Lifetime` استفاده کردیم، استفاده از این رو به ما پیشنهاد میکنه.

برای مثال کد زیر کار نمیکنه:

```rust
    // ⚠️
struct Adventurer<'a> {
    name: &'a str,
    hit_points: u32,
}

impl Adventurer {
    fn take_damage(&mut self) {
        self.hit_points -= 20;
        println!("{} has {} hit points left!", self.name, self.hit_points);
    }
}

fn main() {}
```

در کد بالا ما چیزی که نیاز داشتیم رو نوشتیم: اول گفتیم که نوع `name` یک `&str` هست. و خب وقتی اینکار رو انجام میدیم باید بهش یک `Lifetime` هم بدیم، که برای همین بود که `<'a>` رو نوشتیم.

اما کامپایلر به ما چنین خطایی رو نشون میده:

```text
error[E0726]: implicit elided lifetime not allowed here
 --> src\main.rs:6:6
  |
6 | impl Adventurer {
  |      ^^^^^^^^^^- help: indicate the anonymous lifetime: `<'_>`
```

داره سعی میکنه به ما بگه که لازم داره که ما بهش بگیم که `Adventurer` از `Lifetime` استفاده کرده. خب ما که بهش گفتیم. اره درسته بهش گفتیم اما زمانی که داشتیم این `Struct` رو پیاده‌سازی میکردیم که بهش نگفتیم، پس باید بگیم:

```rust
struct Adventurer<'a> {
    name: &'a str,
    hit_points: u32,
}

impl Adventurer<'_> {
    fn take_damage(&mut self) {
        self.hit_points -= 20;
        println!("{} has {} hit points left!", self.name, self.hit_points);
    }
}

fn main() {}
```
خب `Anonymous Lifetime` ها ساخته شدند که ما هر بار نیایم وقت پیاده‌سازی دوباره `Lifetime` ها رو به طور کامل معرفی کنیم و فقط از `'_` استفاده کنیم به جای نوشتن دوباره‌ی `'a`. چون قبلا مشخص کردیم خودش میفهمه که `'_` یعنی چی.


خب راستش `Lifetime` ها در `Rust` میتونند یادگیری سختی داشته باشند، اما بهتره نکات زیر رو بدونیم که استرس نگیریم:

- ما برای دوری از `Lifetime` ها میتونیم از `Owned Type` ها استفاده کنیم
- اکثر وقت ها که کامپایلر میگه یک `Lifetime` میخوام میتونیم فقط با نوشتن `<'a>` کاری کنیم که راضی بشه. با اینکار یه جورایی به کامپایلر میگیم که نگران نباش چیزی که طول عمرش کافی نیست رو به عنوان ورودی نمیدم
- باید با `Lifetime` ها سر و کله بزنیم و کامپایلر هی بهمون گیر بده تا یاد بگیریم چطوری باید ازشون استفاده کنیم

به این نکته توجه کنید که `Lifetime` ها خیلی قدرتمند هستند و ویژگی مهمی در `Rust` هستند و باید یادشون بگیریم. پس نادیده نگیریمشون بهتر هست.

خب بیاید دوباره مرور کنیم، اما بزارید همه‌ی `Lifetime` ها رو برداریم و همچنین `Display` رو پیاده‌سازی کنیم:

```rust
// ⚠️
struct Adventurer {
    name: &str,
    hit_points: u32,
}

impl Adventurer {
    fn take_damage(&mut self) {
        self.hit_points -= 20;
        println!("{} has {} hit points left!", self.name, self.hit_points);
    }
}

impl std::fmt::Display for Adventurer {
        fn fmt(&self, f: &mut std::fmt::Formatter<'_>) -> std::fmt::Result {
            write!(f, "{} has {} hit points.", self.name, self.hit_points)
        }
}

fn main() {}
```

خب اولین گیری که میده این هست:

```text
error[E0106]: missing lifetime specifier
 --> src\main.rs:2:11
  |
2 |     name: &str,
  |           ^ expected named lifetime parameter
  |
help: consider introducing a named lifetime parameter
  |
1 | struct Adventurer<'a> {
2 |     name: &'a str,
  |
```

پس ما `Lifetime` ها رو مشخص میکنیم:

```rust
// ⚠️
struct Adventurer<'a> {
    name: &'a str,
    hit_points: u32,
}

impl Adventurer {
    fn take_damage(&mut self) {
        self.hit_points -= 20;
        println!("{} has {} hit points left!", self.name, self.hit_points);
    }
}

impl std::fmt::Display for Adventurer {
        fn fmt(&self, f: &mut std::fmt::Formatter<'_>) -> std::fmt::Result {
            write!(f, "{} has {} hit points.", self.name, self.hit_points)
        }
}

fn main() {}
```
گیر بعدی که میده این هست که `Lifetime` رو برای `impl` مشخص نکردیم، خب این هم انجام میدیم:

```text
error[E0726]: implicit elided lifetime not allowed here
 --> src\main.rs:6:6
  |
6 | impl Adventurer {
  |      ^^^^^^^^^^- help: indicate the anonymous lifetime: `<'_>`

error[E0726]: implicit elided lifetime not allowed here
  --> src\main.rs:12:28
   |
12 | impl std::fmt::Display for Adventurer {
   |                            ^^^^^^^^^^- help: indicate the anonymous lifetime: `<'_>`
```

خب الان همه کار میکنه:

```rust
struct Adventurer<'a> {
    name: &'a str,
    hit_points: u32,
}

impl Adventurer<'_> {
    fn take_damage(&mut self) {
        self.hit_points -= 20;
        println!("{} has {} hit points left!", self.name, self.hit_points);
    }
}

impl std::fmt::Display for Adventurer<'_> {

        fn fmt(&self, f: &mut std::fmt::Formatter<'_>) -> std::fmt::Result {
            write!(f, "{} has {} hit points.", self.name, self.hit_points)
        }
}

fn main() {
    let mut billy = Adventurer {
        name: "Billy",
        hit_points: 100_000,
    };
    println!("{}", billy);
    billy.take_damage();
}
```

خروجیش:

```text
Billy has 100000 hit points.
Billy has 99980 hit points left!
```

خب دیدیم که `Lifetime` ها رو مشخص میکنیم که کامپایلر اطمینان پیدا کنه که مشکلی رخ نخواهد داد. همچنین اونقدری باهوش هست که بتونه اکثر `Lifetime` ها رو خودش مشخص کنه اما بعضی ها رو هم نمیتونه که ما باید بهش کمک کنیم.

## Interior mutability

### Cell

اصطلاح `Interior Mutability` به معنای این هست که ما بتونیم بدون اسفتاده از `mut` یکسری متغییر هارو تغییر بدیم. یادمون هست که برای اینکه بتونیم چیزی رو در `Rust` تغییرپذیر کنیم باید از `mut` استفاده کنیم. اما همچنین راه هایی هم وجود داره که بتونیم بدون استفاده از `mut` متغییر های داخل یک `Struct`‌ای که `mut` نیست رو تغییر بدیم.

اول بزارید یکم کد ببینیم:

```rust
struct PhoneModel {
    company_name: String,
    model_name: String,
    screen_size: f32,
    memory: usize,
    date_issued: u32,
    on_sale: bool,
}

fn main() {
    let super_phone_3000 = PhoneModel {
        company_name: "YY Electronics".to_string(),
        model_name: "Super Phone 3000".to_string(),
        screen_size: 7.5,
        memory: 4_000_000,
        date_issued: 2020,
        on_sale: true,
    };

}
```
خب برای اینکه بتونیم مقادیر `super_phone_3000` رو تغییر بدیم باید اون `mut` کنیم. اما خب ما نمیخوایم همه‌ی فیلد هاش رو قابل تغییر کنیم و لازم داریم که `on_sale` رو تغییر بدیم.

پس ما نمیخوایم کد `let mut super_phone_3000` رو بنویسیم از طرفی هم میخوایم فیلد `on_sale`‌اش رو تغییر بدیم.

زبان `Rust` چندین راه برای تغییر دادن یک چیزی که داخل یک چیز غیرقابل تغییر هست داره. یکی از اونها استفاده از `Cell` هست. اول از همه باید از `use std::cell::Cell` استفاده کنیم که هر بار `use std::cell::Cell` رو ننویسیم و به جاش `Cell` رو بنویسیم.

بعد نووع `on_sale` رو به `Cell<bool>` تغییر میدیم.

و خب نوع `Cell` متودی به نام `()set.` داره که باهاش میتونیم مقدار `Cell` رو تغییر بدیم:

```rust
use std::cell::Cell;

struct PhoneModel {
    company_name: String,
    model_name: String,
    screen_size: f32,
    memory: usize,
    date_issued: u32,
    on_sale: Cell<bool>,
}

fn main() {
    let super_phone_3000 = PhoneModel {
        company_name: "YY Electronics".to_string(),
        model_name: "Super Phone 3000".to_string(),
        screen_size: 7.5,
        memory: 4_000_000,
        date_issued: 2020,
        on_sale: Cell::new(true),
    };

    // 10 years later, super_phone_3000 is not on sale anymore
    super_phone_3000.on_sale.set(false);
}
```
نوع `Cell` برای همه‌ی نوع ها کار میکنه اما بهتره فقط ازش برای `Copy Type` ها استفاده کنیم به این دلیل که همیشه مقدار رو میده و یک `Reference` نمیده. برای مثال `Cell` یک متود به نام `()get` داره که فقط روی `Copy Type` ها کار میکنه.

روش دیگه استفاده از `RefCell` هست.

### RefCell

یک روش دیگه برای اینکه یک مقداری رو که درون یک `Struct` هست رو بدون اینکه از `mut` استفاده کنیم، تغییر بدیم، استفاده از `RefCell` هست.

نوع `RefCell` مثل `Cell` هست اما از `Reference` به جای اینکه هی مقدار رو کپی کنه از `Reference` استفاده میکنه.

ما یک ساختار به نام `User` میسازیم و از `RefCell` هم درش استفاده میکنیم:

```rust
use std::cell::RefCell;

#[derive(Debug)]
struct User {
    id: u32,
    year_registered: u32,
    username: String,
    active: RefCell<bool>,
    // Many other fields
}

fn main() {
    let user_1 = User {
        id: 1,
        year_registered: 2020,
        username: "User 1".to_string(),
        active: RefCell::new(true),
    };

    println!("{:?}", user_1.active);
}
```

خروجی کد بالا: `RefCell { value: true }`

نوع `RefCell` متود های زیادی داره. دوتا از اونها `()borrow.` و `borrow_mut()` هستند. با استفاده از اینها میتونیم کاری هایی که با `&` و `&mut` میکردیم رو انجام بدیم.

قوانین استفاده ازشون هم مثال همون ها هست:
- داشتن چندین `()borrow.` مشکلی نداره
- داشتن یک `.borrow_mut()` مشکلی نداره
- اما استفاده همزمان از `()borrow.` و `borrow_mut()` **مشکل** داره و نباید این کار رو انجام بدیم

پس تغییر مقدار `RefCell` اسون هست:
```rust
// 🚧
user_1.active.replace(false);
println!("{:?}", user_1.active);
```
همچنین متود های دیگه‌ای مثل `replace_with` هم وجود داره که میتونیم درشون از `Closure` ها استفاده کنیم:

```rust
// 🚧
let date = 2020;

user_1
    .active
    .replace_with(|_| if date < 2000 { true } else { false });
println!("{:?}", user_1.active);
```

اما در هنگام استفاده از `RefCell` ها باید مراقب این نکته باشیم که قوانین `Borrow` ها در زمان اجرای برنامه چک میشن. پس امکان داره برنامه کامپایل بشه اما در هنگام اجرا `Panic` کنه، البته اگه قوانین رو رعایت نکرده باشیم.

برای مثال کد زیر کامپایل میشه اما اجرا در هنگام اجرا به مشکل بر میخوره:

```rust
use std::cell::RefCell;

#[derive(Debug)]
struct User {
    id: u32,
    year_registered: u32,
    username: String,
    active: RefCell<bool>,
    // Many other fields
}

fn main() {
    let user_1 = User {
        id: 1,
        year_registered: 2020,
        username: "User 1".to_string(),
        active: RefCell::new(true),
    };

    let borrow_one = user_1.active.borrow_mut(); // first mutable borrow - okay
    let borrow_two = user_1.active.borrow_mut(); // second mutable borrow - not okay
}
```

کد بالا چنین `Panic`‌ای میکنه:
```text
thread 'main' panicked at 'already borrowed: BorrowMutError', C:\Users\mithr\.rustup\toolchains\stable-x86_64-pc-windows-msvc\lib/rustlib/src/rust\src\libcore\cell.rs:877:9
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
error: process didn't exit successfully: `target\debug\rust_book.exe` (exit code: 101)
```

بخش مهم پیام `Panic`، `already borrowed: BorrowMutError` هست.

پس در هنگام استفاده از `RefCell` بهتره برنامه رو اجرا کنیم که درست کار کردن برنامه رو چک کنیم.

### Mutex

خب `Mutex` یک راه دیگه دیگه برای برای تغییر مقدار ها بدون `mut` هست. `Mutex` به معنای `Mutual Exclusion` هست. که یعنی در یک زمان فقط یک کار انجام میشه. به همین دلیل استفاده از `Mutex` امن هست. به این دلیل که فقط اجازه میده یک عملیات در یک زمان انجام بشه. برای اینکار از متود `()lock.` استفاده میکنه. `Lock` مثل این هست که یک در رو از داخل قفل میکنه و یه کاری انجام میده و کس دیگه هم اجازه نداره کاری انجام بده به این دلیل که در قفل هست.

بیاید کد ببینیم چون راحت میشه `Mutex` رو با کد درک کرد:

```rust
use std::sync::Mutex;

fn main() {
    let my_mutex = Mutex::new(5); // A new Mutex<i32>. We don't need to say mut
    let mut mutex_changer = my_mutex.lock().unwrap(); // mutex_changer is a MutexGuard
                                                     // It has to be mut because we will change it
                                                     // Now it has access to the Mutex
                                                     // Let's print my_mutex to see:

    println!("{:?}", my_mutex); // This prints "Mutex { data: <locked> }"
                                // So we can't access the data with my_mutex now,
                                // only with mutex_changer

    println!("{:?}", mutex_changer); // This prints 5. Let's change it to 6.

    *mutex_changer = 6; // mutex_changer is a MutexGuard<i32> so we use * to change the i32

    println!("{:?}", mutex_changer); // Now it says 6
}
```

اما `mutex_changer` همچنان قفل هست. خب کی قفلش باز میشه؟ زمانی که از بلوک کدی که درش تعریف شده تموم بشه،‌ برای مثال:

```rust
use std::sync::Mutex;

fn main() {
    let my_mutex = Mutex::new(5);
    {
        let mut mutex_changer = my_mutex.lock().unwrap();
        *mutex_changer = 6;
    } // mutex_changer goes out of scope - now it is gone. It is not locked anymore

    println!("{:?}", my_mutex); // Now it says: Mutex { data: 6 }
}
```
اگه نمیخوایم از بلوک های جدا استفاده کنیم، باید از `std::mem::drop(mutex_changer)` استفاده کنیم. با استفاده از `std::mem::drop` ما یک متغییر رو از بین میبریم.

برای مثال:

```rust
use std::sync::Mutex;

fn main() {
    let my_mutex = Mutex::new(5);
    let mut mutex_changer = my_mutex.lock().unwrap();
    *mutex_changer = 6;
    std::mem::drop(mutex_changer); // drop mutex_changer - it is gone now
                                   // and my_mutex is unlocked

    println!("{:?}", my_mutex); // Now it says: Mutex { data: 6 }
}
```
در هنگام استفاده از `Mutex` باید حواسمون جمع باشه چون اگه یک متغییر دیگه بخواد اون رو `lock` کنه، باید منتظر بمونه تا زمانی که قبلی از `lock` خارج بشه. برای مثال:

```rust
use std::sync::Mutex;

fn main() {
    let my_mutex = Mutex::new(5);
    let mut mutex_changer = my_mutex.lock().unwrap(); // mutex_changer has the lock
    let mut other_mutex_changer = my_mutex.lock().unwrap(); // other_mutex_changer wants the lock
                                                            // the program is waiting
                                                            // and waiting
                                                            // and will wait forever.

    println!("This will never print...");
}
```

یک متود دیگه `try_lock()` هست. این متود یک بار سعی میکنه که `Mutex` رو `lock` کنه، اگه همون یکبار نتونست دیگه صبر نمیکنه. از `try_lock().unwrap()` استفاده نمیکنیم چون اگه نتونه `lock` کنه، `Panic` میگیریم. پس از `if let` یا `match` استفاده میکنیم:

```rust
use std::sync::Mutex;

fn main() {
    let my_mutex = Mutex::new(5);
    let mut mutex_changer = my_mutex.lock().unwrap();
    let mut other_mutex_changer = my_mutex.try_lock(); // try to get the lock

    if let Ok(value) = other_mutex_changer {
        println!("The MutexGuard has: {}", value)
    } else {
        println!("Didn't get the lock")
    }
}
```

همچنین حتما لازم نیست برای تغییر `Mutex` از یک متغییر استفاده کنیم، ما میتونیم اینکار رو کنیم:

```rust
use std::sync::Mutex;

fn main() {
    let my_mutex = Mutex::new(5);

    *my_mutex.lock().unwrap() = 6;

    println!("{:?}", my_mutex);
}
```
کد `*my_mutex.lock().unwrap() = 6` به این معنا هست که، `Mutex` `lock` کن و بعد مقدارش رو برابر با `6` قرار بده. چون متغییری وجود نداره ما لازم نیست از `std::mem::drop` استفاده کنیم،‌ پس میتونیم هر چقدر که میخوایم این کار رو انجام بدیم:

```rust
use std::sync::Mutex;

fn main() {
    let my_mutex = Mutex::new(5);

    for _ in 0..100 {
        *my_mutex.lock().unwrap() += 1; // locks and unlocks 100 times
    }

    println!("{:?}", my_mutex);
}
```

### RwLock

نوع `RwLock` یعنی `Read/Write lock`. هم شبیه به `Mutex` هست و هم شبیه به `RefCell`. برای تغییرش میتونیم از `.write().unwrap()` به جای `.lock().unwrap()` استفاده کنیم.

برای گرفتن مقدار هم میتونیم از `.read().unwrap()` استفاده کنیم. مثل `RefCell` هست به این دلیل که استفاده ازش چنین قوانینی داره:

- چندین `()read.` مشکلی نداره
- یک `()write.` مشکلی نداره
- اما چندین `()write.` یا استفاده از `()read.` و `()write.` با هم مشکل ایجاد میکنه

زمانی که دسترسی `write` نداریم از `()write.` استفاده کنیم برنامه تا ابد ادامه پیدا میکنه و منتظر میمونه که دسترسی بگیریم:

```rust
use std::sync::RwLock;

fn main() {
    let my_rwlock = RwLock::new(5);

    let read1 = my_rwlock.read().unwrap(); // one .read() is fine
    let read2 = my_rwlock.read().unwrap(); // two .read()s is also fine

    println!("{:?}, {:?}", read1, read2);

    let write1 = my_rwlock.write().unwrap(); // uh oh, now the program will wait forever
}
```

پس میتونیم از `std::mem::drop` استفاده کنیم:

```rust
use std::sync::RwLock;
use std::mem::drop; // We will use drop() many times

fn main() {
    let my_rwlock = RwLock::new(5);

    let read1 = my_rwlock.read().unwrap();
    let read2 = my_rwlock.read().unwrap();

    println!("{:?}, {:?}", read1, read2);

    drop(read1);
    drop(read2); // we dropped both, so we can use .write() now

    let mut write1 = my_rwlock.write().unwrap();
    *write1 = 6;
    drop(write1);
    println!("{:?}", my_rwlock);
}
```

همچنین میتونیم از `try_read()` و `try_write()` هم استفاده کنیم:

```rust
use std::sync::RwLock;

fn main() {
    let my_rwlock = RwLock::new(5);

    let read1 = my_rwlock.read().unwrap();
    let read2 = my_rwlock.read().unwrap();

    if let Ok(mut number) = my_rwlock.try_write() {
        *number += 10;
        println!("Now the number is {}", number);
    } else {
        println!("Couldn't get write access, sorry!")
    };
}
```

## Cow

نوع `Cow` یک `Enum` هست و به معنای `Clone On Write` هست. معمولا نوع `Cow` رو به عنوان خروجی فانکشن ها استفاده میکنیم. در این حالت ما برای مثال میتونیم اگه خواستیم یک `&str` در `Cow` برگردونیم یا اگه خواستیم یک `String` در `Cow` برگردونیم. همین کار رو میشه در مورد `Array` ها با `Vec` ها گفت و...


برای فهم بهتر بیاید امضای `Cow` رو ببینیم:

```rust
pub enum Cow<'a, B>
where
    B: 'a + ToOwned + ?Sized,
 {
    Borrowed(&'a B),
    Owned(<B as ToOwned>::Owned),
}

fn main() {}
```

خب ما میدونیم که `'a` به این معنا هست که داریم با `Reference` ها کار میکنیم و برای مشخص کردن `Lifetime` داریم ازش استفاده میکنیم.

خب هر نوعی که بتونه یک `Onwed Type` بشه، `ToOwned` رو پیاده‌سازی کرده. برای مثال نوع `str` که معمولا یک `Reference` هست(`&str`) میتونه به یک `Owned Type` که `String` باشه، تبدیل بشه.

بعدی `?Sized` هست. این به معنای این هست که شاید `Sized` رو پیاده‌سازی کرده بود، شاید هم نکرده بود. تقریبا همه‌ی نوع ها `Sized` هستند. اما بعضی نوع ها مثل `str`، `Sized` نیستند. اینکه میگیم `Sized` نیستند یعنی اینکه `Sized` رو پیاده‌سازی نکردند. به همین دلیل هم هست که ما برای کار با `str` به `&str` نیاز داریم، چون کامپایلر سایز `str` رو نمیدونه اما سایز `Reference` رو همیشه میدونه چون ثابت هست.

خب حالت های `Enum` ما `Borrowed` و `Owned` هستند.

بزارید تصور کنیم که یک فانکشن داریم که یک `Cow<'stati, str>` برمیگردونه. پس اگه در فانکشن کد `"My message".into()` رو برگردونیم. کامپایلر به نوع `My Message` نگاه میکنه و میفهمه که یک `str` هست. این یک نوع `Borrowed` هست. پس حالت `Borrowed(&'a B)` رو انتخاب میکنه. پس خروجی میشه `Cow::Borrowed(&'static str)`.

و اگه ما در فانکشن کد `format!("{}", "My message").into()` رو بنویسیم. کامپایلر این دفعه نوع رو `String` تشخیص میده چون `format!` یک `String` برمیگردونه. چون `String` یک `Owned Type` هست، حالت `Owned` انتخاب میشه.

در کد زیر یک مثال از استفاده از `Cow` رو میبینیم. ما یک عدد به فانکشن `modulo_3` میدیم. اون یک `Cow<'static, str>` برمیگردونه. با توجه به عدد اون یک `&str` یا یک `String` میسازه. بعد با استفاده از `()into.` اون رو به یکی از حالت های `Cow` تبدیل میکنه. وقتی اینکار رو انجام میدیم بین حالت `Cow::Borrowed` یا `Cow::Owned` یکی انتخاب میشه:

```rust
use std::borrow::Cow;

fn modulo_3(input: u8) -> Cow<'static, str> {
    match input % 3 {
        0 => "Remainder is 0".into(),
        1 => "Remainder is 1".into(),
        remainder => format!("Remainder is {}", remainder).into(),
    }
}

fn main() {
    for number in 1..=6 {
        match modulo_3(number) {
            Cow::Borrowed(message) => println!("{} went in. The Cow is borrowed with this message: {}", number, message),
            Cow::Owned(message) => println!("{} went in. The Cow is owned with this message: {}", number, message),
        }
    }
}
```

خروجیش:

```text
1 went in. The Cow is borrowed with this message: Remainder is 1
2 went in. The Cow is owned with this message: Remainder is 2
3 went in. The Cow is borrowed with this message: Remainder is 0
4 went in. The Cow is borrowed with this message: Remainder is 1
5 went in. The Cow is owned with this message: Remainder is 2
6 went in. The Cow is borrowed with this message: Remainder is 0
```

همچنین `Cow` متود های دیگه‌ای مثل `into_owned` یا `into_borrowed` هم داره که میتونیم ازشون استفاده کنیم.

## Type aliases

اصطلاح `Type Alias` به معنای دادن یک نام جدید به یک نوع هست.


برای مثال:
```rust
type CharacterVec = Vec<char>;

fn main() {}
```

در زیر یک نوع رو میبینیم که طولانی هست:
```rust
// this return type is extremely long
fn returns<'a>(input: &'a Vec<char>) -> std::iter::Take<std::iter::Skip<std::slice::Iter<'a, char>>> {
    input.iter().skip(4).take(5)
}

fn main() {}
```

پس میتونیم یک `Alias` براش درست کنیم:
```rust
type SkipFourTakeFive<'a> = std::iter::Take<std::iter::Skip<std::slice::Iter<'a, char>>>;

fn returns<'a>(input: &'a Vec<char>) -> SkipFourTakeFive {
    input.iter().skip(4).take(5)
}

fn main() {}
```

البته میتونیم ماژول های رو هم `Import` کنیم که راحت‌تر بتونیم از نوع ها استفاده کنیم:
```rust
use std::iter::{Take, Skip};
use std::slice::Iter;

fn returns<'a>(input: &'a Vec<char>) -> Take<Skip<Iter<'a, char>>> {
    input.iter().skip(4).take(5)
}

fn main() {}
```

پس میتونیم تصمیم بگیریم که از `Alias` ها استفاده کنیم یا اینکه ماژول رو `Import` کنیم.

به این نکته توجه کنید که با این کار ما یک نوع جدید نمیسازیم و فقط یک اسم به یک نوعی که وجود داره میدیم، پس اگه `type File = String` رو بنویسیم، کامپایلر نوع رو `String` تشخیص میده، در کد زیر `true` رو پرینت میکنه:

```rust
type File = String;

fn main() {
    let my_file = File::from("I am file contents");
    let my_string = String::from("I am file contents");
    println!("{}", my_file == my_string);
}
```

پس اگه یک نوع جدید میخواستیم چیکار کنیم؟
میتونیم یک `Tuple Struct` بسازیم:

```rust
struct File(String); // File is a wrapper around String

fn main() {
    let my_file = File(String::from("I am file contents"));
    let my_string = String::from("I am file contents");
}
```

الان خروحی کد زیر `false` میشه:
```rust
struct File(String); // File is a wrapper around String

fn main() {
    let my_file = File(String::from("I am file contents"));
    let my_string = String::from("I am file contents");
    println!("{}", my_file == my_string);  // ⚠️ cannot compare File with String
}
```

اگه بخوایم دوتا `String` رو مقایسه کنیم باید از `my_file.0` استفاده کنیم:
```rust
struct File(String);

fn main() {
    let my_file = File(String::from("I am file contents"));
    let my_string = String::from("I am file contents");
    println!("{}", my_file.0 == my_string); // my_file.0 is a String, so this prints true
}
```

خب این یک نوع جدید هست دیگه، پس هر کاری که قبلا با نوع ها میکردیم رو میتونیم روی این هم اجرا کنیم، برای مثال پیاده‌سازی `Trait` ها:
```rust
#[derive(Clone, Debug)]
struct File(String);
```

پس الان اگه از `File` استفاده کنیم میتونیم `Clone` کنیمش یا حتی `Debug Print` کنیمش. اما نمیتونیم روش از `Trait` های `String` استفاده کنیم چون این یک نوع دیگه هست.

### Importing and renaming inside a function

معمولا ما `use` رو در اول برنامه مینویسیم:

```rust
use std::cell::{Cell, RefCell};

fn main() {}
```

اما دیدیم که میتونیم هر جایی بنویسیم، برای مثال قبلا در فانکشن هایی که از `Enum` هایی که حالت های مختلف و طولانی داشتند استفاده کردیم.

در کد زیر از `use` در فانکشن استفاده نمیکنیم:

```rust
enum MapDirection {
    North,
    NorthEast,
    East,
    SouthEast,
    South,
    SouthWest,
    West,
    NorthWest,
}

fn main() {}

fn give_direction(direction: &MapDirection) {
    match direction {
        MapDirection::North => println!("You are heading north."),
        MapDirection::NorthEast => println!("You are heading northeast."),
        // So much more left to type...
        // ⚠️ because we didn't write every possible variant
    }
}
```

در کد زیر از `use` استفاده کردیم که راحت‌تر با `Enum` کار کنیم:

```rust
enum MapDirection {
    North,
    NorthEast,
    East,
    SouthEast,
    South,
    SouthWest,
    West,
    NorthWest,
}

fn main() {}

fn give_direction(direction: &MapDirection) {
    use MapDirection::*; // Import everything in MapDirection
    let m = "You are heading";

    match direction {
        North => println!("{} north.", m),
        NorthEast => println!("{} northeast.", m),
        // This is a bit better
        // ⚠️
    }
}
```

عبارت `::*` به این معنا هست که هر چیزی که در چیزی که قبل `::` معرفی کردیم رو `Import` کن. در مثال بالا میشه `North`، `NorthEast` و...

وقتی از کد های بقیه افراد استفاده میکنیم هم میتونیم از این روش استفاده کنیم. اما اگه کد خیلی زیاد باشه امکان داره به مشکل بخوریم، برای مثال اگه نوعی درش باشه که ما هم همون نوع رو داشته باشیم، کامپایلر نمیفهمه باید از کدوم استفاده کنه. پس بهتره که از `::*` استفاده نکنیم، به غیر از زمانی که اطمینان داریم که مشکلی پیش نمیاد.

اکثر وقت ها ما بخشی به نام `prelude` رو درون کد های دیگران میبینیم که کد هایی چیز هایی که احتمالا ما بهشون نیاز خواهیم داشت رو `Import` کردند. پس احتمالا بهتره که از `crate::prelude::*` استفاده کنیم. در این مورد در بخش `modules` و `crates` بیشتر یاد میگیریم.

همچنین میتونیم از کلمه‌کلیدی `as` استفاده کنیم برای تغییر نام یک ایتم. برای مثال امکان داره که در حال استفاده از کد کس دیگه‌ای هستیم و نمیتونیم ایتم های یک `Enum` رو تغییر بدیم:

```rust
enum FileState {
    CannotAccessFile,
    FileOpenedAndReady,
    NoSuchFileExists,
    SimilarFileNameInNextDirectory,
}

fn main() {}
```

در این شرایط ما میتونیم اول `Enum` رو `Import` کنیم و بعد اسم ایتم هارو تغییر بدیم:

```rust
enum FileState {
    CannotAccessFile,
    FileOpenedAndReady,
    NoSuchFileExists,
    SimilarFileNameInNextDirectory,
}

fn give_filestate(input: &FileState) {
    use FileState::{
        CannotAccessFile as NoAccess,
        FileOpenedAndReady as Good,
        NoSuchFileExists as NoFile,
        SimilarFileNameInNextDirectory as OtherDirectory
    };
    match input {
        NoAccess => println!("Can't access file."),
        Good => println!("Here is your file"),
        NoFile => println!("Sorry, there is no file by that name."),
        OtherDirectory => println!("Please check the other directory."),
    }
}

fn main() {}
```

پس الان میتونیم به جای `FileState::SimilarFileNameInNextDirectory`، `OtherDirectory` رو بنویسیم.

## The todo! macro

گاهی اوقات نیاز داریم که یک تصور کلی از پروژه داشته باشیم و نمیخوایم همه‌ی بخش ها رو پیاده‌سازی کنیم، برای مثال یک پروژه‌ای رو تصور کنید که میخوایم یه کاری با کتاب ها انجام بدیم، پس ما چنین چیزی رو مینویسیم:

```rust
struct Book {} // Okay, first I need a book struct.
               // Nothing in there yet - will add later

enum BookType { // A book can be hardcover or softcover, so add an enum
    HardCover,
    SoftCover,
}

fn get_book(book: &Book) -> Option<String> {} // ⚠️ get_book should take a &Book and return an Option<String>

fn delete_book(book: Book) -> Result<(), String> {} // delete_book should take a Book and return a Result...
                                                    // TODO: impl block and make these functions methods...
fn check_book_type(book_type: &BookType) { // Let's make sure the match statement works
    match book_type {
        BookType::HardCover => println!("It's hardcover"),
        BookType::SoftCover => println!("It's softcover"),
    }
}

fn main() {
    let book_type = BookType::HardCover;
    check_book_type(&book_type); // Okay, let's check this function!
}
```

اما انگار `Rust` زیاد با فانکشن های `get_book` و `delete_book` خوشحال نیست:

```text
error[E0308]: mismatched types
  --> src\main.rs:32:29
   |
32 | fn get_book(book: &Book) -> Option<String> {}
   |    --------                 ^^^^^^^^^^^^^^ expected enum `std::option::Option`, found `()`
   |    |
   |    implicitly returns `()` as its body has no tail or `return` expression
   |
   = note:   expected enum `std::option::Option<std::string::String>`
           found unit type `()`

error[E0308]: mismatched types
  --> src\main.rs:34:31
   |
34 | fn delete_book(book: Book) -> Result<(), String> {}
   |    -----------                ^^^^^^^^^^^^^^^^^^ expected enum `std::result::Result`, found `()`
   |    |
   |    implicitly returns `()` as its body has no tail or `return` expression
   |
   = note:   expected enum `std::result::Result<(), std::string::String>`
           found unit type `()`
```

اما در حال حاضر `get_book` و `delete_book` برای ما مهم نیست و نمیخوایم اونها رو پیاده‌سازی کنیم. خب برای اینکار میتونیم از `todo!()` استفاده کنیم. اگه این ماکرو رو به فانکشن ها اضافه کنیم دیگه `Rust` گیر نمیده:

```rust
struct Book {}

fn get_book(book: &Book) -> Option<String> {
    todo!() // todo means "I will do it later, please be quiet"
}

fn delete_book(book: Book) -> Result<(), String> {
    todo!()
}

fn main() {
    let book_type = BookType::HardCover;
    check_book_type(&book_type); // Okay, let's check this function!
}
```

خب الان خب کامپایل میشه و `check_book_type`: `It's hardcover` رو پرینت میکنه.

اما خب باید مراقب بود، چون فقط کامپایل میشه، اگه ما از اون فانکشن ها استفاده کنیم و `todo!()` اجرا بشه، برنامه `Panic` میکنه.


اما خب باید نوع ورودی و خروجی تعریف شده باشه برای مثال کد زیر کامپایل نمیشه، چون `WorldsBestType` وجود نداره:

```rust
struct Book {}

fn get_book(book: &Book) -> WorldsBestType { // ⚠️
    todo!()
}

fn main() {}
```

خطایی که میده:

```text
error[E0412]: cannot find type `WorldsBestType` in this scope
  --> src\main.rs:32:29
   |
32 | fn get_book(book: &Book) -> WorldsBestType {
   |                             ^^^^^^^^^^^^^^ not found in this scope
```

ماکروی `todo!()` مثل ماکروی `unimplemented!()` هست. برنامه‌نویس ها قبلا از `unimplemented!()` استفاده میکردند، اما خب تایپ کردنش زمان میبرد، پس `todo!()` درست شد که راحت‌تر نوشته میشه.

## Rc

نوع `Rc` به معنای `Reference Counter`. این رو میدونیم که در `Rust` هر متغییر یک مالک داره. به همین دلیل هست که کد زیر کار نمیکنه:

```rust
fn takes_a_string(input: String) {
    println!("It is: {}", input)
}

fn also_takes_a_string(input: String) {
    println!("It is: {}", input)
}

fn main() {
    let user_name = String::from("User MacUserson");

    takes_a_string(user_name);
    also_takes_a_string(user_name); // ⚠️
}
```
بعد از اینکه `takes_a_string`، متغییر `user_name` رو میگیره. دیگه نمیتونیم ازش استفاده کنیم. خب میتونیم `user_name.clone()` رو بهش بدیم. اما گاهی وقت ها متغییر بخشی از یک `Struct` هست و نمیخوایم که اون رو کپی کنیم. یا شاید `String` خیلی بزرگ هست و هزینه‌ی زیادی رو باید برای کپی کردنش بدیم. اینها دلایلی برای استفاده از `Rc` هستند. `Rc` اجازه میده که متغییر درونش بیشتر از یک مالک داشته باشه. `Rc` مثل یک کارمند اداره هست که همه‌ی مالک ها رو نگهداری میکنه و زمانی که تعداد مالک ها به `0` رسید اون متغییر میتونه از بین بره.

برای مثال، بزارید فکر کنیم که ما یک `City` داریم و یک `CityData`. `City` اطلاعاتی در مورد یک شهر رو در خودش نگهداری میکنه و `CityData` همه‌ی شهر ها رو در کنار هم نگه میداره:

```rust
#[derive(Debug)]
struct City {
    name: String,
    population: u32,
    city_history: String,
}

#[derive(Debug)]
struct CityData {
    names: Vec<String>,
    histories: Vec<String>,
}

fn main() {
    let calgary = City {
        name: "Calgary".to_string(),
        population: 1_200_000,
           // Pretend that this string is very very long
        city_history: "Calgary began as a fort called Fort Calgary that...".to_string(),
    };

    let canada_cities = CityData {
        names: vec![calgary.name], // This is using calgary.name, which is short
        histories: vec![calgary.city_history], // But this String is very long
    };

    println!("Calgary's history is: {}", calgary.city_history);  // ⚠️
}
```

البته، کد بالا کار نمیکنه، به این دلیل که متغییر `canada_cities` حالا مالک `city_history` هست و دیگه مالکش `calgary` نیست.

خطایی که میده:

```text
error[E0382]: borrow of moved value: `calgary.city_history`
  --> src\main.rs:27:42
   |
24 |         histories: vec![calgary.city_history], // But this String is very long
   |                         -------------------- value moved here
...
27 |     println!("Calgary's history is: {}", calgary.city_history);  // ⚠️
   |                                          ^^^^^^^^^^^^^^^^^^^^ value borrowed here after move
   |
   = note: move occurs because `calgary.city_history` has type `std::string::String`, which does not implement the `Copy` trait
```

ما میتونیم کد `names: vec![calgary.name.clone()]` رو هم بنویسیم. اما خب نمیخوایم که `city_history` رو کپی کنیم به این دلیل که طولانی و بزرگ هست و حافظه‌ی زیادی استفاده میکنه، پس از `Rc` استفاده میکنیم:

```rust
use std::rc::Rc;

fn main() {}
```

Then put `Rc` around `String`.

```rust
use std::rc::Rc;

#[derive(Debug)]
struct City {
    name: String,
    population: u32,
    city_history: Rc<String>,
}

#[derive(Debug)]
struct CityData {
    names: Vec<String>,
    histories: Vec<Rc<String>>,
}

fn main() {}
```
برای اینکه یک `Reference` بسازیم، باید `Rc` رو `clone` کنیم. اما مگه ما نمیخواستیم  `clone` نکنیم؟

واقعیتش نه، ما نمیخواستیم که `String` رو `clone` کنیم. `clone` کردن یک `Rc` به معنای کپی کردن `Pointer` هست. و عملا هزینه‌ی زیادی نداره. مثل این میمونه که یک برچسب روی یک جعبه‌ی کتاب بزنیم که نشون بدیم رو نفر مالک این کتاب ها هستند. با این کار از ساختن دوباره‌ی کتاب ها جلوگیری میکنیم.

ما میتونیم یک `Rc` به نام `item` با `item.clone()` یا `Rc::clone(&item)` کپی(`clone`) کنیم. پس `calgary.city_history` دو مالک داره. ما میتونیم تعداد مالک ها رو با `Rc::strong_count(&item)` بفهمیم. بزارید یک مالک دیگه هم اضافه کنیم:

```rust
use std::rc::Rc;

#[derive(Debug)]
struct City {
    name: String,
    population: u32,
    city_history: Rc<String>, // String inside an Rc
}

#[derive(Debug)]
struct CityData {
    names: Vec<String>,
    histories: Vec<Rc<String>>, // A Vec of Strings inside Rcs
}

fn main() {
    let calgary = City {
        name: "Calgary".to_string(),
        population: 1_200_000,
           // Pretend that this string is very very long
        city_history: Rc::new("Calgary began as a fort called Fort Calgary that...".to_string()), // Rc::new() to make the Rc
    };

    let canada_cities = CityData {
        names: vec![calgary.name],
        histories: vec![calgary.city_history.clone()], // .clone() to increase the count
    };

    println!("Calgary's history is: {}", calgary.city_history);
    println!("{}", Rc::strong_count(&calgary.city_history));
    let new_owner = calgary.city_history.clone();
}
```
دومین `println!` که داریم مقدار `2` رو پرینت میکنه. بعدش `new_owner` هم یک مالک میشه. و اگه بعدش هم یک `println!("{}", Rc::strong_count(&calgary.city_history))` میزاریم مقدار `3` رو میگرفتیم. 

پس اگه `Strong Pointer` وجود داره، ایا `Week Pointer` هم وجود داره؟

اره، `Week Pointer` هم وجود داره. `Week Pointer` ها هم کاربردی هستند، برای مثال اگه دو `Rc` به همدیگه `Point` کنند، هیچکدوم نمیتونند از بین برند. به اینکار میگن `Reference Cycle`.

اما اگه `Rc` فقط یک `Week Reference` داشته باشه میتونه از بین بره. پس برای حل `Reference Cycle` میتونیم از `Week Reference` ها استفاده کنیم.

برای ساخت یک `Week Reference` از `Rc::downgrade(&item)` به جای `Rc::clone(&item)` استفاده میکنیم. همچنین میتونیم از `Rc::week_count(&item)` برای گرفتن تعداد `Week Reference` ها استفاده کنیم.

## Multiple threads

با استفاده از `Thread` ها میتونیم چندین کار رو در یک زمان انجام بدیم. کامپیوتر های مدرن معمولا بیشتر از `1`، `Core` دارند، پس میتونند چندین کار رو در یک زمان انجام بدند. `Rust` از `Thread` هایی استفاده میکنه که بهشون میگیم `OS Thread`. `OS Thread` ها رو سیستم‌عامل روی `Core` های مختلف میسازه و کنترلشون میکنه.

(بعضی زبان ها از `Green Thread` استفاده میکنند که قدرت کمتری دارند)


ما میتونیم با استفاده از `std::thread::spawn` یک `Thread` بسازیم و به عنوان ورودی بهش یک `Closure` بدیم که بهش بگیم باید چه کاری در اون `Thread` انجام بده.

استفاده از `Thread` ها جالب هست به این دلیل که در یک زمان اجرا میشند. برای مثال کد زیر رو ببینید:

```rust
fn main() {
    std::thread::spawn(|| {
        println!("I am printing something");
    });
}
```

اگه کد بالا رو اجرا کنیم، گاهی وقت ها `I am printing something` رو پرینت میکنه و گاهی اوقات هم نمیکنه. این بستگی به سرعت کامپیوتر داره. این به این دلیل هست که گاهی اوقات `()main` زودتر از `Thread` تموم میشه. و خب وقتی هم `()main` تموم بشه کل برنامه تموم میشه، بزارید در یک حلفه برنامه رو اجرا کنیم:

```rust
fn main() {
    for _ in 0..10 { // set up ten threads
        std::thread::spawn(|| {
            println!("I am printing something");
        });
    }   // Now the threads start.
}       // How many can finish before main() ends here?
```

در کد بالا معولا باید چهار `Thread` بتونند قبل از `()main` اجرا بشند، اما خب همیشه چنین نتیجه‌ای نمیگیریم. برای مثال اگه کامپیوتر سریع باشه حتی میتونه چیزی هم پرینت نشه.

گاهی وقت ها هم برنامه `Panic` میکنه:

```text
thread 'thread 'I am printing something
thread '<unnamed><unnamed>thread '' panicked at '<unnamed>I am printing something
' panicked at 'thread '<unnamed>cannot access stdout during shutdown' panicked at '<unnamed>thread 'cannot access stdout during
shutdown
```

این به دلیل این اتفاق میوفته که برنامه درحال تموم شدن بود اما یک `Thread` سعی داشته کاری انجام بده.

ما میتونیم به برنامه رو مشغول کنیم که `Thread` ها هم بتونند اجرا بشند:

```rust
fn main() {
    for _ in 0..10 {
        std::thread::spawn(|| {
            println!("I am printing something");
        });
    }
    for _ in 0..1_000_000 { // make the program declare "let x = 9" one million times
                            // It has to finish this before it can exit the main function
        let _x = 9;
    }
}
```
اما خب این کار احمقانه‌ای هست. روش بهتر این هست که در هنگام ایجاد یک `Thread` خروجی‌ای که `spawn` میده رو در یک متغییر نگهداری کنیم. خروجی یک `JoinHandle` هست. میتونیم در امضای `spawn` این موضوع رو ببینیم:

```text
pub fn spawn<F, T>(f: F) -> JoinHandle<T>
where
    F: FnOnce() -> T,
    F: Send + 'static,
    T: Send + 'static,
```
(متغییر `f` یک `Closure` هست، برای در مورد اینکه چطوری یک `Closure` رو در فانکشن بگیریم یاد میگیریم)

پس ما هر بار `JoinHandle` رو میگیریم:

```rust
fn main() {
    for _ in 0..10 {
        let handle = std::thread::spawn(|| {
            println!("I am printing something");
        });

    }
}
```

الان متغییر `handle` یک `JoinHandle` هست. خب چه کاری باهاش کنیم؟ ما میتونیم از متود `()join.` استفاده کنیم. این متود هر جا که استفاده بشه صبر میکنه تا زمانی که `Thread` کارش تموم بشه، بعد کد های بعدش اجرا میشند. پس ما `handle.join()` رو مینویسیم و صبر میکنیم که هر `Thread` تموم بشه و بعد `Thread` بعدی رو میسازیم:

```rust
fn main() {
    for _ in 0..10 {
        let handle = std::thread::spawn(|| {
            println!("I am printing something");
        });

        handle.join(); // Wait for the threads to finish
    }
}
```

خب حالا بزارید در مورد انوع `Closure` ها یاد بگیریم:

- `FnOnce`: کل مقدارها رو میگیره و مالکش میشه
- `FnMut`: یک `Mutable Reference` به مقدار ها میگیره
- `Fn`: یک `Reference` به مقدارها میگیره

یک `Closure` سعی میکنه که از `Fn` استفاده کنه. اما اگه نیاز داشته باشه مقدار رو تغییر بشه از `FnMut` استفاده میکنه. و اگه بخواد یک بار مالک مقدار بشه از `FnOnce` استفاده میکنه.

نوع `FnOnce` اسم خوبی هم داره، به این دلیل که یک بار مقدار ها رو میگیره و دیگه هم اونها بعدش قابل استفاده نیستند.

برای مثال:

```rust
fn main() {
    let my_string = String::from("I will go into the closure");
    let my_closure = || println!("{}", my_string);
    my_closure();
    my_closure();
}
```

نوع `String` یک `Copy` رو پیاده‌سازی نمیکنه، پس `my_closure()` یک `Fn` هست، پس یعنی فقط `Reference` به مقدار ها رو میگیره:

اگه ما در `Closure` مقدار `my_string` رو تغییر بدیم، نوع اون `Closure`، `FnMut` میشه:

```rust
fn main() {
    let mut my_string = String::from("I will go into the closure");
    let mut my_closure = || {
        my_string.push_str(" now");
        println!("{}", my_string);
    };
    my_closure();
    my_closure();
}
```

خروجیش:

```text
I will go into the closure now
I will go into the closure now now
```

و اگه مالک اون متغییر ها بشیم، نوعش `FnOnce` میشه:

```rust
fn main() {
    let my_vec: Vec<i32> = vec![8, 9, 10];
    let my_closure = || {
        my_vec
            .into_iter() // into_iter takes ownership
            .map(|x| x as u8) // turn it into u8
            .map(|x| x * 2) // multiply by 2
            .collect::<Vec<u8>>() // collect into a Vec
    };
    let new_vec = my_closure();
    println!("{:?}", new_vec);
}
```

در کد بالا ما متغییر ها رو با مقدار گرفتیم و مالکشون شدیم، پس نمیتونیم `my_closure()` رو دوباره اجرا کنیم. دلیل اسم `FnOnce` هم از همین جا میاد.



خب حالا برگردیم به `Thread` ها. بزارید از یک متغییری که بیرون `Closure` هست استفاده کنیم:

```rust
fn main() {
    let mut my_string = String::from("Can I go inside the thread?");

    let handle = std::thread::spawn(|| {
        println!("{}", my_string); // ⚠️
    });

    handle.join();
}
```

کامپایلر چنین خطایی میده:

```text
error[E0373]: closure may outlive the current function, but it borrows `my_string`, which is owned by the current function
  --> src\main.rs:28:37
   |
28 |     let handle = std::thread::spawn(|| {
   |                                     ^^ may outlive borrowed value `my_string`
29 |         println!("{}", my_string);
   |                        --------- `my_string` is borrowed here
   |
note: function requires argument type to outlive `'static`
  --> src\main.rs:28:18
   |
28 |       let handle = std::thread::spawn(|| {
   |  __________________^
29 | |         println!("{}", my_string);
30 | |     });
   | |______^
help: to force the closure to take ownership of `my_string` (and any other referenced variables), use the `move` keyword
   |
28 |     let handle = std::thread::spawn(move || {
   |                                     ^^^^^^^
```

پیام طولانی‌ای هست اما بخش مهمش ``use the `move` keyword`` هست. مشکل اینجاست که ما میتونیم از `my_string` در `Thread` استفاده کنیم، اما `Thread` مالک اون نیست. و این همچین امن نیست.

کد زیر هم کار نمیکنه:
```rust
fn main() {
    let mut my_string = String::from("Can I go inside the thread?");

    let handle = std::thread::spawn(|| {
        println!("{}", my_string); // now my_string is being used as a reference
    });

    std::mem::drop(my_string);  // ⚠️ We try to drop it here. But the thread still needs it.

    handle.join();
}
```

پس ما مجبور هستیم که با استفاده از کلمه‌کلیدی `move` متغییر ها رو به `Thread` بدیم. الان کد امن هست، اینطوری مالک متغییر `Thread` میشه، اما همچنان کد زیر کار نمیکنه:
So you have to take the value with `move`. Now it is safe:

```rust
fn main() {
    let mut my_string = String::from("Can I go inside the thread?");

    let handle = std::thread::spawn(move|| {
        println!("{}", my_string);
    });

    std::mem::drop(my_string);  // ⚠️ we can't drop, because handle has it. So this won't work

    handle.join();
}
```

مالک متغییر `my_string`، `Thread` هست و ما سعی داریم که با `` از بین ببریمش که خب امکانش وجود نداره. پس اون کد رو حذف میکنیم:

```rust
fn main() {
    let my_string = String::from("Can I go inside the thread?");

    let handle = std::thread::spawn(move|| {
        println!("{}", my_string);
    });

    handle.join().unwrap();
}
```

پس باید یادمون باشه که اگه میخوایم از یک متغییر بیرون `Closure` استفاده کنیم باید از `move` استفاده کنیم.

## Closures in functions

خب `Closure` ها عالی هستند، اما چطور ازشون در یک فانکشن استفاده کنیم؟

ما میتونیم فانکشن هایی بسازیم که به عنوان ورودی `Closure` دریافت میکنند، بیرون یک فانکشن بر اساس کاری که `Closure` انجام میده نوعش مشخص میشه، اما در یک فانکشن ما باید مشخص کنیم که چه نوعی از `Closure` میخوایم.

برای فهم بهتر، خوب هست که به چند فانکشن نگاهی کنیم، در زیر امضای متود `()all.` رو میبینیم:

```rust
    fn all<F>(&mut self, f: F) -> bool    // 🚧
    where
        F: FnMut(Self::Item) -> bool,
```

عبارت `fn all<F>` میگه که یک `Generic` وجود داره به نام `F`. یک `Closure` همیشه یک `Generic` هست، به این دلیل که نوعش هر بار میتونه تغییر کنه.

در عبارت `(&mut self, f: F)` بخش `&mut self` میگه که این یک متود هست. `f: F` معمولا چیزی هست که برای `Closure` ها ازش استفاده میکنیم. البته هر اسمی که میخوایم میتونیم بزاریم. اما معمولا در امضا های متود/فانکشن ها ما `f: F` رو میبینیم.

بخش بعدی `F: FnMut(Self::Item) -> bool` هست که در اینحا نوع اون `Generic` که `Closure` ما هست مشخص میشه. در این متود نوع `Closure` باید `FnMut` باشه. پس میتونه مقدار های ایتم ها رو تغییر بده و به عنوان خروجی یک `bool` برمیگردونه.

در زیر یک امضای ساده‌تر از فانکشنی که `Closure` میگیره رو میبینیم:

```rust
fn do_something<F>(f: F)    // 🚧
where
    F: FnOnce(),
{
    f();
}
```

این فقط میگه که فانکشن یک `Closure` میگیره که نوعش `FnOnce` هست، چیزی هم بر نمیگردونه و در نهایت درون فانکشن هم اون `Closure` ورودی رو اجرا میکنه. پس این `Closure` چیزی نمیگیره و چیزی هم برنمیگردونه. ما یک `Vec` میسازیم بعد روش `Iterate` میکنیم و مقدار ایتم که روش هستیم رو هم پرینت میکنیم:

```rust
fn do_something<F>(f: F)
where
    F: FnOnce(),
{
    f();
}

fn main() {
    let some_vec = vec![9, 8, 10];
    do_something(|| {
        some_vec
            .into_iter()
            .for_each(|x| println!("The number is: {}", x));
    })
}
```

برای یک مثال واقعی‌تر ما یک `City` میسازیم. این دفعه `City` یک ساختاری هست که اطلاعات زیادی در مورد سال و جمعیت رو در خودش نگهداری میکنه. یک `Vec<u32>` برای نگهداری سال ها داره و یک `Vec<u32>` برای نگهداری جمعیت:

ساختار `City` دو فانکشن داره، یکی `()new` که یک `City` جدید درست میکنه و `.city_data()` که یک `Closure` میگیره. اون `Closure` دو `Vec<u32>` به عنوان ورودی میگیره و یه کاری با اونها انجام میده و چیزی هم بر نمیگردونه، نوع `Closure` هم `FnMut` هست، پس میتونه مقادیر رو هم تغییر بده:

```rust
#[derive(Debug)]
struct City {
    name: String,
    years: Vec<u32>,
    populations: Vec<u32>,
}

impl City {
    fn new(name: &str, years: Vec<u32>, populations: Vec<u32>) -> Self {

        Self {
            name: name.to_string(),
            years,
            populations,
        }
    }

    fn city_data<F>(&mut self, mut f: F) // We bring in self, but only f is generic F. f is the closure

    where
        F: FnMut(&mut Vec<u32>, &mut Vec<u32>), // The closure takes mutable vectors of u32
                                                // which are the year and population data
    {
        f(&mut self.years, &mut self.populations) // Finally this is the actual function. It says
                                                  // "use a closure on self.years and self.populations"
                                                  // We can do whatever we want with the closure
    }
}

fn main() {
    let years = vec![
        1372, 1834, 1851, 1881, 1897, 1925, 1959, 1989, 2000, 2005, 2010, 2020,
    ];
    let populations = vec![
        3_250, 15_300, 24_000, 45_900, 58_800, 119_800, 283_071, 478_974, 400_378, 401_694,
        406_703, 437_619,
    ];
    // Now we can create our city
    let mut tallinn = City::new("Tallinn", years, populations);

    // Now we have a .city_data() method that has a closure. We can do anything we want.

    // First let's put the data for 5 years together and print it.
    tallinn.city_data(|city_years, city_populations| { // We can call the input anything we want
        let new_vec = city_years
            .into_iter()
            .zip(city_populations.into_iter()) // Zip the two together
            .take(5)                           // but only take the first 5
            .collect::<Vec<(_, _)>>(); // Tell Rust to decide the type inside the tuple
        println!("{:?}", new_vec);
    });

    // Now let's add some data for the year 2030
    tallinn.city_data(|x, y| { // This time we just call the input x and y
        x.push(2030);
        y.push(500_000);
    });

    // We don't want the 1834 data anymore
    tallinn.city_data(|x, y| {
        let position_option = x.iter().position(|x| *x == 1834);
        if let Some(position) = position_option {
            println!(
                "Going to delete {} at position {:?} now.",
                x[position], position
            ); // Confirm that we delete the right item
            x.remove(position);
            y.remove(position);
        }
    });

    println!(
        "Years left are {:?}\nPopulations left are {:?}",
        tallinn.years, tallinn.populations
    );
}
```

کد بالا چنین چیزی رو پرینت میکنه:

```text
[(1372, 3250), (1834, 15300), (1851, 24000), (1881, 45900), (1897, 58800)]
Going to delete 1834 at position 1 now.
Years left are [1372, 1851, 1881, 1897, 1925, 1959, 1989, 2000, 2005, 2010, 2020, 2030]
Populations left are [3250, 24000, 45900, 58800, 119800, 283071, 478974, 400378, 401694, 406703, 437619, 500000]
```

## impl Trait

خب `impl Trait` شبیه به `Generic` ها هست. یادمون هست که در `Generic` ها ما یک اسم مثل `T` میدادیم که نوع اون در زمان کامپایل مشخص میشد.

اول بزارید به `Concrete Type` ها نگاهی بندازیم:

```rust
fn gives_higher_i32(one: i32, two: i32) {
    let higher = if one > two { one } else { two };
    println!("{} is higher.", higher);
}

fn main() {
    gives_higher_i32(8, 10);
}
```

خروجیش میشه: `10 is higher.`

اما این فانکشن فقط میتونه نوع `i32` رو بگیره. خب حالا بیاید این فانکشن رو `Generic` کنیم. ما نیاز داریم که اون نوعی که میاد رو مقایسه کنیم و همچنین پرینتش کنیم. پس نوعی که میگیریم باید `PartialOrd` و `Display` رو پیاده‌سازی کرده باشه:

```rust
use std::fmt::Display;

fn gives_higher_i32<T: PartialOrd + Display>(one: T, two: T) {
    let higher = if one > two { one } else { two };
    println!("{} is higher.", higher);
}

fn main() {
    gives_higher_i32(8, 10);
}
```

خب حالا بزارید به `impl Trait` نگاهی بندازیم که شبیه به `Generic` هست. ما به جای `T` میتونیم از `impl Trait` استفاده کنیم. تقریبا شبیه به `Generic` هست:

```rust
fn prints_it(input: impl Into<String> + std::fmt::Display) { // Takes anything that can turn into a String and has Display
    println!("You can print many things, including {}", input);
}

fn main() {
    let name = "Tuon";
    let string_name = String::from("Tuon");
    prints_it(name);
    prints_it(string_name);
}
```

با این حال، بخش جالبش اینجاست که ما میتونیم یک `impl Trait` رو برگردونیم، که این یعنی میتونیم حتی یک `Closure` برگردونیم، به این دلیل که امضای اونها `Trait` ها هستند. بزارید به امضای فانکشن `()map.` یک نگاهی بندازیم:

```rust
fn map<B, F>(self, f: F) -> Map<Self, F>     // 🚧
    where
        Self: Sized,
        F: FnMut(Self::Item) -> B,
    {
        Map::new(self, f)
    }
```

خب `fn map<B, F>(self, f: F)` یعنی دو تا `Generic` میگیره. `F` یک فانکشن هست که یک ایتم از چیزی `()map.` روش اجرا میشه رو میگیره. `B` نوعی هست که فانکشن برمیگردونه. بعد ما `Trait Bound` داریم. یکیش `Sized` هست و بعدی امضای `Closure` هست. `Closure` باید یک `FnMut` باشه و باید یک `Self::Item` رو بگیره که `Iterator` بهش میده، بعدش هم باید نوع `B` رو برگردونه.

پس ما میتونیم برای برگردوندن یک `Closure` هم همین کار رو انجام بدیم. میتونیم از `impl` استفاده کنیم و بعد امضای `Closure` رو مشخص کنیم. خب چون خروجی `Closure` هست میتونیم ازش مثل یک فانکشن استفاده کنیم. در زیر یک مثالی میبینیم که یک فانکشنی داریم که یک `Closure` رو بر اساس ورودی به ما میده. اگه ورودی `double` یا `triple` رو بدیم،‌ به ما یک `Closure`‌ای میده که میتونه ورودی ها رو با `2` یا `3` ضرب کنه. در غیر این صورت به ما یک `Closure`ای میده که فقط ورودی رو برمیگردونه. به این دلیل که یک `Closure` هست ما میتونیم هر کاری درش انجام بدیم، برای مثال میتونیم درش چیزی رو پرینت کنیم:

```rust
fn returns_a_closure(input: &str) -> impl FnMut(i32) -> i32 {
    match input {
        "double" => |mut number| {
            number *= 2;
            println!("Doubling number. Now it is {}", number);
            number
        },
        "triple" => |mut number| {
            number *= 40;
            println!("Tripling number. Now it is {}", number);
            number
        },
        _ => |number| {
            println!("Sorry, it's the same: {}.", number);
            number
        },
    }
}

fn main() {
    let my_number = 10;

    // Make three closures
    let mut doubles = returns_a_closure("double");
    let mut triples = returns_a_closure("triple");
    let mut quadruples = returns_a_closure("quadruple");

    doubles(my_number);
    triples(my_number);
    quadruples(my_number);
}
```

در زیر یک مثال طولانی‌تر میبینیم. بزارید یک بازی رو تصور کنیم که شخصیت بازی با هیولا هایی مواجه میشه که در شب قدرتشون بیشتر میشه. ما میتونیم یک `Enum` به نام `TimeOfDay` درست کنیم که بتونیم زمان روز رو باهاش مشخص کنیم. اسم شخصیت ما `Simon` هست و یک چیزی داره به نام `character_fear` که یک `f64` هست. اون مقدار در طول شب بشتر میشه و در طول روز کمتر میشه. ما یک فانکشن به نام `change_fear` میسازیم که مقدار `character_fear` رو تغییر میده اما خب کار های دیگه‌ای مثال پرینت کردن پیام هم انجام میده:

```rust
enum TimeOfDay { // just a simple enum
    Dawn,
    Day,
    Sunset,
    Night,
}

fn change_fear(input: TimeOfDay) -> impl FnMut(f64) -> f64 { // The function takes a TimeOfDay. It returns a closure.
                                                             // We use impl FnMut(64) -> f64 to say that it needs to
                                                             // change the value, and also gives the same type back.
    use TimeOfDay::*; // So we only have to write Dawn, Day, Sunset, Night
                      // Instead of TimeOfDay::Dawn, TimeOfDay::Day, etc.
    match input {
        Dawn => |x| { // This is the variable character_fear that we give it later
            println!("The morning sun has vanquished the horrible night. You no longer feel afraid.");
            println!("Your fear is now {}", x * 0.5);
            x * 0.5
        },
        Day => |x| {
            println!("What a nice day. Maybe put your feet up and rest a bit.");
            println!("Your fear is now {}", x * 0.2);
            x * 0.2
        },
        Sunset => |x| {
            println!("The sun is almost down! This is no good.");
            println!("Your fear is now {}", x * 1.4);
            x * 1.4
        },
        Night => |x| {
            println!("What a horrible night to have a curse.");
            println!("Your fear is now {}", x * 5.0);
            x * 5.0
        },
    }
}

fn main() {
    use TimeOfDay::*;
    let mut character_fear = 10.0; // Start Simon with 10

    let mut daytime = change_fear(Day); // Make four closures here to call every time we want to change Simon's fear.
    let mut sunset = change_fear(Sunset);
    let mut night = change_fear(Night);
    let mut morning = change_fear(Dawn);

    character_fear = daytime(character_fear); // Call the closures on Simon's fear. They give a message and change the fear number.
                                              // In real life we would have a Character struct and use it as a method instead,
                                              // like this: character_fear.daytime()
    character_fear = sunset(character_fear);
    character_fear = night(character_fear);
    character_fear = morning(character_fear);
}
```

خروجی کد بالا این میشه:

```text
What a nice day. Maybe put your feet up and rest a bit.
Your fear is now 2
The sun is almost down! This is no good.
Your fear is now 2.8
What a horrible night to have a curse.
Your fear is now 14
The morning sun has vanquished the horrible night. You no longer feel afraid.
Your fear is now 7
```

## Arc

یادمون هست که `Rc` به ما اجازه میداد یک متغییر بیشتر از یک مالک داشته باشه. اگه بخوایم از چنین چیزی در `Thread` ها استفاده کنیم، باید از `Arc` استفاده کنیم. `Arc` به معنای `Atomic Reference Counter` هست. `Atomic` اینجا به معنی این هست که از پردازنده‌ی کامپیوتر استفاده میکنه که داده ها فقط یک در یک زمان بتونند روی حافظه نوشته بشند. یعنی اجازه نمیده که دو `Thread` بخوان با هم در یک زمان یک داده‌ای رو در یک جای کامپیوتر بنویسند. این باعث میشه که `Data Race` رخ نده. این به این دلیل مهم هست که اگه دو `Thread` بخوان همزمان داده‌ای رو در یک جای حافظه بنویسند، احتمال داره که نتیجه‌ی اشتباهی بگیریم. برای مثال فکر کنید که چنین کاری رو در `Rust` انجام بدیم:

```rust
// 🚧
let mut x = 10;

for i in 0..10 { // Thread 1
    x += 1
}
for i in 0..10 { // Thread 2
    x += 1
}
```

اگه `Thread` شماره یک و شماره دو با هم اجرا بشند امکان داره چنین حالتی رخ بده:
- `Thread` شماره یک مقدار `10` رو میبینه، بعد `Thread` شماره دو مقدار `11` رو میبینه و مقدار `12` رو روش مینویسه، که خب تا اینجا مشکلی نیست
- `Thread` یک مقدار `12` رو میبینه، در همین زمان، `Thread` شماره دو مقدار `12` رو میبینه، بعد `Thread` شماره یک مقدار `13` رو مینویسه. حالا ما مقدار `13` رو داریم، اما باید `14` میبود. و این یک مشکل بزرگ هست.
If Thread 1 and Thread 2 just start together, maybe this will happen:


یک `Arc` از پردازنده‌ی کامپیوتر استفاده میکنه که جلوی چنین حالتی رو بگیره. پس وقتی داریم از `Thread` ها استفاده میکنیم باید از این روش استفاده کنیم. البته برای یک `Thread` نیازی به `Arc` نداریم و میتونیم از `Rc` استفاده کنیم که از `Arc` سریع‌تر هست.

البته نمیتونیم فقط با `Arc` مقدار رو تغییر بدیم، پس باید از `Mutex` استفاده کنیم.

پس بزارید یک مثالی رو ببینیم که از `Mutex` درون `Arc` استفاده کردیم که مقدار چیزی رو تغییر بدیم. اول بزارید یک `Thread` بسازیم:

```rust
fn main() {

    let handle = std::thread::spawn(|| {
        println!("The thread is working!") // Just testing the thread
    });

    handle.join().unwrap(); // Make the thread wait here until it is done
    println!("Exiting the program");
}
```

تا اینجا خروجی برنامه چنین چیزی میشه:

```text
The thread is working!
Exiting the program
```

خب حالا بیاید یک حلقه‌ی `for` بسازیم:

```rust
fn main() {

    let handle = std::thread::spawn(|| {
        for _ in 0..5 {
            println!("The thread is working!")
        }
    });

    handle.join().unwrap();
    println!("Exiting the program");
}
```

خروجیش تا الان چنین چیزی میشه:

```text
The thread is working!
The thread is working!
The thread is working!
The thread is working!
The thread is working!
Exiting the program
```

خب حالا بزارید بیشتر از یک `Thread` درست کنیم. هر `Thread` کاری شبیه به اون یکی انجام میده. میتونیم ببینیم که `Thread` ها همزمان اجرا میشند. گاهی‌ اوقات اول `Thread 1 is working!` رو پرینت میکنه و گاهی اوقات `Thread 2 is working!` رو پرینت میکنه. به این میگن `Concurrency` که به معنای اجرای همزمان هست:

```rust
fn main() {

    let thread1 = std::thread::spawn(|| {
        for _ in 0..5 {
            println!("Thread 1 is working!")
        }
    });

    let thread2 = std::thread::spawn(|| {
        for _ in 0..5 {
            println!("Thread 2 is working!")
        }
    });

    thread1.join().unwrap();
    thread2.join().unwrap();
    println!("Exiting the program");
}
```

چیزی که پرینت کرد:

```text
Thread 1 is working!
Thread 1 is working!
Thread 1 is working!
Thread 1 is working!
Thread 1 is working!
Thread 2 is working!
Thread 2 is working!
Thread 2 is working!
Thread 2 is working!
Thread 2 is working!
Exiting the program
```

خب حالا میخوایم مقدار `my_number` رو تغییر بدیم که یک `i32` هست. ما اون رو به `Arc<Mutex<i32>>` تغییر میدیم. الان یک `i32`‌ای هست که توسط `Arc` از `Data Race` مراقبت میشه و چون در یک `Mutex` هست میتونه با امنیت تغییر کنه:

```rust
// 🚧
let my_number = Arc::new(Mutex::new(0));
```

خب حالا که چنین چیزی داریم میتونیم `Clone` کنیمش. هر `Clone` میره توی یک `Thread`. ما دو `Thread` داریم، پس دو `Clone` ازش میسازیم:

```rust
// 🚧
let my_number = Arc::new(Mutex::new(0));

let my_number1 = Arc::clone(&my_number); // This clone goes into Thread 1
let my_number2 = Arc::clone(&my_number); // This clone goes into Thread 2
```

خب حالا ما `Clone` های امنی از `my_number` داریم که میتونیم به خیال راحت با استفاده از `move` به `Thread` رو بدیمش:

```rust
use std::sync::{Arc, Mutex};

fn main() {
    let my_number = Arc::new(Mutex::new(0));

    let my_number1 = Arc::clone(&my_number);
    let my_number2 = Arc::clone(&my_number);

    let thread1 = std::thread::spawn(move || { // Only the clone goes into Thread 1
        for _ in 0..10 {
            *my_number1.lock().unwrap() +=1; // Lock the Mutex, change the value
        }
    });

    let thread2 = std::thread::spawn(move || { // Only the clone goes into Thread 2
        for _ in 0..10 {
            *my_number2.lock().unwrap() += 1;
        }
    });

    thread1.join().unwrap();
    thread2.join().unwrap();
    println!("Value is: {:?}", my_number);
    println!("Exiting the program");
}
```

خروجیش:

```text
Value is: Mutex { data: 20 }
Exiting the program
```

خب پس موفق شدیم.

بعد ما میتونیم دو `Thread` رو در یک `for` به هم `Join` کنیم. که کد یکم کمتر بشه.(این هم یک نوع `Refactoring` هست)

ما باید دو `Handle`‌ای که برای `Thread` ها هستند رو بگیریم که بتونیم از `()join.` بیرون از `loop` استفاده کنیم. اگه در `loop` از `()join.` استفاده کنیم. برنامه همونجا وای میسته تا زمانی که `Thread`ای که ساخته شده تموم بشه و بعد `Thread` بعدی رو میسازه.

```rust
use std::sync::{Arc, Mutex};

fn main() {
    let my_number = Arc::new(Mutex::new(0));
    let mut handle_vec = vec![]; // JoinHandles will go in here

    for _ in 0..2 { // do this twice
        let my_number_clone = Arc::clone(&my_number); // Make the clone before starting the thread
        let handle = std::thread::spawn(move || { // Put the clone in
            for _ in 0..10 {
                *my_number_clone.lock().unwrap() += 1;
            }
        });
        handle_vec.push(handle); // save the handle so we can call join on it outside of the loop
                                 // If we don't push it in the vec, it will just die here
    }

    handle_vec.into_iter().for_each(|handle| handle.join().unwrap()); // call join on all handles
    println!("{:?}", my_number);
}
```

در نهایت چنین چیزی پرینت میشه: `Mutex { data: 20 }`

عبارت `Arc<Mutex<SomeType>>>` به نظر پیچیده میاد، اما خیلی در `Rust` استفاده میشه. همچنین همیشه میتونیم کد رو بهتر بنویسیم، برای مثال میتونیم از `use` استفاده کنیم که کد کمتری بنویسیم. فانکشن هایی که در کد زیر میبینید کار عچیبی جدیدی انجام نمیدند اما خب کد قابل فهم‌تر شده و حتی استفاده ازش هم راحت‌تر شده:

```rust
use std::sync::{Arc, Mutex};
use std::thread::spawn; // Now we just write spawn

fn make_arc(number: i32) -> Arc<Mutex<i32>> { // Just a function to make a Mutex in an Arc
    Arc::new(Mutex::new(number))
}

fn new_clone(input: &Arc<Mutex<i32>>) -> Arc<Mutex<i32>> { // Just a function so we can write new_clone
    Arc::clone(&input)
}

// Now main() is easier to read
fn main() {
    let mut handle_vec = vec![]; // each handle will go in here
    let my_number = make_arc(0);

    for _ in 0..2 {
        let my_number_clone = new_clone(&my_number);
        let handle = spawn(move || {
            for _ in 0..10 {
                let mut value_inside = my_number_clone.lock().unwrap();
                *value_inside += 1;
            }
        });
        handle_vec.push(handle);    // the handle is done, so put it in the vector
    }

    handle_vec.into_iter().for_each(|handle| handle.join().unwrap()); // Make each one wait

    println!("{:?}", my_number);
}
```

## Channels

در `Rust` چیزی به نام `Channel` وجود داره، ما با استفاده از `Channel` ها میتونیم کاری کنیم نتیجه‌ی چندین `Thread` در یک جا نگهداری بشند. `Channel` ها محبوب هستند به این دلیل که خیلی راحت میشه ازشون استفاده کرد.

ما میتونیم با استفاده از `std::sync::mpsc` یک `Channel` بسازیم. `mpsc` به معنای `Multiple producer, Single consumer` هست. برای ایجاد یک `Channel` میتونیم از `()channel` استفاده کنیم، به ما یک `Sender` و یک `Receiver` میده، این ها همیشه در کنار هم هستند، بزارید امضای فانکشن `()channel` رو ببینیم:

```rust
// 🚧
pub fn channel<T>() -> (Sender<T>, Receiver<T>)
```

پس ما برای `Sender` و `Receiver` باید اسم انتخاب کنیم. معمولا اسم های منطقی `sender` و `receiver` رو انتخاب میکنیم. اما اگه کد زیر رو اجرا کنیم کامپایلر خطا میده، به این دلیل که اونها `Generic` هستند و ما باید نوعشون رو مشخص کنیم:

```rust
use std::sync::mpsc::channel;

fn main() {
    let (sender, receiver) = channel(); // ⚠️
}
```

خطایی که کامپایلر میده:

```text
error[E0282]: type annotations needed for `(std::sync::mpsc::Sender<T>, std::sync::mpsc::Receiver<T>)`
  --> src\main.rs:30:30
   |
30 |     let (sender, receiver) = channel();
   |         ------------------   ^^^^^^^ cannot infer type for type parameter `T` declared on the function `channel`
   |         |
   |         consider giving this pattern the explicit type `(std::sync::mpsc::Sender<T>, std::sync::mpsc::Receiver<T>)`, where
the type parameter `T` is specified
```

میبینیم که به ما پیشنهاد میکنه که نوع های `Sender` و `Receiver` رو مشخص کنیم، پس میتونیم چنین کاری رو انجام بدیم:

```rust
use std::sync::mpsc::{channel, Sender, Receiver}; // Added Sender and Receiver here

fn main() {
    let (sender, receiver): (Sender<i32>, Receiver<i32>) = channel();
}
```

اما خب مجبور نیستیم، به محض اینکه از `Sender` و `Receiver` استفاده کنیم، `Rust` خودش میتونه نوع هاشون رو مشخص کنه:

```rust
use std::sync::mpsc::channel;

fn main() {
    let (sender, receiver) = channel();

    sender.send(5);
    receiver.recv(); // recv = receive, not "rec v"
}
```
الان نوع `sender` یک `Result<(), SendError<i32>>` هست و نوع `receiver` یک `Result<(), ‌RecvError<i32>>` هست.

پس میتونیم از `()unwrap.` استفاده کنیم که ببینیم مقدار فرستاده شده یا خیر، یا حتی بهتر این هست که خطا های احتمالی رو کنترل کنیم:

```rust
use std::sync::mpsc::channel;

fn main() {
    let (sender, receiver) = channel();

    sender.send(5).unwrap();
    println!("{}", receiver.recv().unwrap());
}
```

خروجی کد بالا: `5`

یک `Channel` شبیه به `Arc` هست، به این دلیل که میتونیم `Clone` کنیمش و بفرستیمش به `Thread` ها. بزارید دو `Thread` بسازیم و مقدار ها رو به `receiver` بفرستیم. این کد کار میکنه اما چیزی که ما میخوایم رو انجام نمیده:

```rust
use std::sync::mpsc::channel;

fn main() {
    let (sender, receiver) = channel();
    let sender_clone = sender.clone();

    std::thread::spawn(move|| { // move sender in
        sender.send("Send a &str this time").unwrap();
    });

    std::thread::spawn(move|| { // move sender_clone in
        sender_clone.send("And here is another &str").unwrap();
    });

    println!("{}", receiver.recv().unwrap());
}
```
دو `Thread` مقدار ها رو میفرستند و ما بعد مقدار ها رو چاپ میکنیم،‌ شاید `Send a &str this time` پرینت بشه یا شاید هم `And here is another &str` پرینت بشه، در حقیقت بستگی به این داره که کدوم `Thread` زودتر تموم شده، و خب بعدش هم `()main` به اتمام میرسه که این یعنی برنامه تموم میشه. خب ما میتونیم با استفاده از `()join.` منتطر `Thread` ها بمونیم:

```rust
use std::sync::mpsc::channel;

fn main() {
    let (sender, receiver) = channel();
    let sender_clone = sender.clone();
    let mut handle_vec = vec![]; // Put our handles in here

    handle_vec.push(std::thread::spawn(move|| {  // push this into the vec
        sender.send("Send a &str this time").unwrap();
    }));

    handle_vec.push(std::thread::spawn(move|| {  // and push this into the vec
        sender_clone.send("And here is another &str").unwrap();
    }));

    for _ in handle_vec { // now handle_vec has 2 items. Let's print them
        println!("{:?}", receiver.recv().unwrap());
    }
}
```
خروجیش:

```text
"Send a &str this time"
"And here is another &str"
```

خب حالا بیاید به جای اینکه مقادیر رو پرینت کنیم اونها رو درون `results_vec` بریزیم.

```rust
use std::sync::mpsc::channel;

fn main() {
    let (sender, receiver) = channel();
    let sender_clone = sender.clone();
    let mut handle_vec = vec![];
    let mut results_vec = vec![];

    handle_vec.push(std::thread::spawn(move|| {
        sender.send("Send a &str this time").unwrap();
    }));

    handle_vec.push(std::thread::spawn(move|| {
        sender_clone.send("And here is another &str").unwrap();
    }));

    for _ in handle_vec {
        results_vec.push(receiver.recv().unwrap());
    }

    println!("{:?}", results_vec);
}
```

مقادیری که در `results_vec` قرار دارند، اینها هستند: `["Send a &str this time", "And here is another &str"]`

خب بیاید تظاهر کنیم که ما کار های زیادی برای انجام دارم و میخوایم از `Thread` ها استفاده کنیم. ما یک `Vec` داریم که یک میلیون ایتم داره، مقدار همه‌ی ایتم ها هم `0` هستند. ما میخوایم که مقادیر همه‌ی ایتم ها رو به `1` تغییر بدیم. برای اینکار از `Thread` ها استفاده میکنیم. هر `Thread` یک دهم کار را انجام میدهد، در نهایت ما یک `Vec` جدید میسازیم و از `()extend.` استفاده میکنیم که نتایج رو درش بریزیم:

```rust
use std::sync::mpsc::channel;
use std::thread::spawn;

fn main() {
    let (sender, receiver) = channel();
    let hugevec = vec![0; 1_000_000];
    let mut newvec = vec![];
    let mut handle_vec = vec![];

    for i in 0..10 {
        let sender_clone = sender.clone();
        let mut work: Vec<u8> = Vec::with_capacity(hugevec.len() / 10); // new vec to put the work in. 1/10th the size
        work.extend(&hugevec[i*100_000..(i+1)*100_000]); // first part gets 0..100_000, next gets 100_000..200_000, etc.
        let handle =spawn(move || { // make a handle

            for number in work.iter_mut() { // do the actual work
                *number += 1;
            };
            sender_clone.send(work).unwrap(); // use the sender_clone to send the work to the receiver
        });
        handle_vec.push(handle);
    }
    
    for handle in handle_vec { // stop until the threads are done
        handle.join().unwrap();
    }
    
    while let Ok(results) = receiver.try_recv() {
        newvec.push(results); // push the results from receiver.recv() into the vec
    }

    // Now we have a Vec<Vec<u8>>. To put it together we can use .flatten()
    let newvec = newvec.into_iter().flatten().collect::<Vec<u8>>(); // Now it's one vec of 1_000_000 u8 numbers
    
    println!("{:?}, {:?}, total length: {}", // Let's print out some numbers to make sure they are all 1
        &newvec[0..10], &newvec[newvec.len()-10..newvec.len()], newvec.len() // And show that the length is 1_000_000 items
    );
    
    for number in newvec { // And let's tell Rust that it can panic if even one number is not 1
        if number != 1 {
            panic!();
        }
    }
}
```

## Reading Rust documentation

مهم هست که بتونیم مستندات رو بخونیم، اگه بتونیم اینکار رو انجام بدیم راحت میتونیم کد هایی که بقیه‌ی افراد نوشتند رو بخونیم و متوجه بشیم، در این قسمت چیز هایی که زیاد در مستندات استفاده میشند رو میبینیم و در موردشون یاد میگیریم.

### assert_eq

ما `assert_eq!` رو در بخش `Test` دیدیم. ما دوتا متغییر بهش میدیم و اگه مقدار اون دو با هم برابر نباشه، برنامه `Panic` میکنه. برای مثال:

```rust
fn main() {
    prints_number(56);
}

fn prints_number(input: i32) {
    assert_eq!(input % 2, 0); // number must be equal.
                              // If number % 2 is not 0, it panics
    println!("The number is not odd. It is {}", input);
}
```

احتمالا ما از `assert_eq!` در کدمون استفاده نمیکنیم، اما در همه‌جای مستندات ازش استفاده میکنیم.

به این دلیل کاربردی هست که اگه بخوایم به اون از `println!` استفاده کنیم باید `Display` یا `Debug` رو برای هر چیزی که داریم تست میکنیم، پیاده‌سازی کنیم. پس استفاده از `aasert_eq!` و بقیه‌ی دوستاش، منطقی هست.

در این [لینک](https://doc.rust-lang.org/std/vec/struct.Vec.html) ما صفحه‌ی مستندات `Vec` رو میبینیم که به ما نشون میده چطور از `Vec` ها استفاده کنیم:

```rust
fn main() {
    let mut vec = Vec::new();
    vec.push(1);
    vec.push(2);

    assert_eq!(vec.len(), 2);
    assert_eq!(vec[0], 1);

    assert_eq!(vec.pop(), Some(2));
    assert_eq!(vec.len(), 1);

    vec[0] = 7;
    assert_eq!(vec[0], 7);

    vec.extend([1, 2, 3].iter().copied());

    for x in &vec {
        println!("{}", x);
    }
    assert_eq!(vec, [7, 1, 2, 3]);
}
```

در کد بالا میتونیم فکر کنیم که کد `assert_eq!(a, b)` به معنای این هست که "ایا `a` برابر با `b` هست".

در کد زیر با کامنت ها کامل متوجه میشیم که کد ها چه کاری انجام میدند:

```rust
fn main() {
    let mut vec = Vec::new();
    vec.push(1);
    vec.push(2);

    assert_eq!(vec.len(), 2); // "The vec length is 2"
    assert_eq!(vec[0], 1); // "vec[0] is 1"

    assert_eq!(vec.pop(), Some(2)); // "When you use .pop(), you get Some()"
    assert_eq!(vec.len(), 1); // "The vec length is now 1"

    vec[0] = 7;
    assert_eq!(vec[0], 7); // "Vec[0] is 7"

    vec.extend([1, 2, 3].iter().copied());

    for x in &vec {
        println!("{}", x);
    }
    assert_eq!(vec, [7, 1, 2, 3]); // "The vec now has [7, 1, 2, 3]"
}
```

### Searching

در بالای [سایت](https://doc.rust-lang.org/std/index.html) مستدات `Rust`، بخشی وجود داره که میتونیم در اون در مورد هر چیزی که میخوایم جستجو کنیم. اگه به پایین صفحه بریم دیگه اون بخش رو نمیبینیم، اما اگه در همونجا کلید `s` رو فشار بدیم، دوباره میتونیم برگردیم به اون بخش و جستجو کنیم.

### [src] button

معمولا کد های `Method`، `Struct`و... ها کامل نیستند. به این دلیل که لازم نداریم که کل کد رو ببینیم که بدونیم چه کاری انجام میدند. اما اگه بخوایم کد رو ببینیم میتونیم روی `[src]` کلیک کنیم. برای مثال در صفحه‌ی `String` ما میتونیم امضای متود `.with_capacity()` رو ببینیم:

```rust
// 🚧
pub fn with_capacity(capacity: usize) -> String
```
خب پس یا عدد بهش میدیم و اون به ما یک `String` با `Capacity`‌ای برابر با اون عدد بهمون میده. اما اگه کنجکاو باشیم که کد رو ببینیم میتونیم روی `[src]` کلیک کنیم:

```rust
// 🚧
pub fn with_capacity(capacity: usize) -> String {
    String { vec: Vec::with_capacity(capacity) }
}
```

خب جالبه، میتونیم ببینیم که `String` یه جورایی یک `Vec` هست. در حقیقت یک `String` یک `Vec`‌ای هست که مقدار `u8` رو در خودش نگهداری میکنه.

پس اگه در مستندات خوب در مورد کارکرد یک چیز توضیح داده نشده میتونیم روی `[src]` بزنیم و کد اون چیز رو ببینیم.

### Information on traits

بخش مهم مستدات درباره یک `Trait`، بخش `Required Methods` هست که در سمت چپ قرار داره. اگه این بخش رو میبینیم به احتمال زیاد باید خودمون اون متود ها رو برای پیاده‌سازی اون `Trait` پیاده‌سازی کنیم. برای مثال برای `Iterator` ما باید متود `()next.` رو بنویسیم. و برای `From` باید متود `()from.` رو بنویسیم. اما بعضی `Trait` ها هم میتونند با استفاده از `Attribute` ها پیاده‌سازی بشند، برای مثال ما کد `#[derive(Debug)]` رو دیدیم.

خب `Debug` به `()fmt.` نیاز داره، اما معمولا ما از `#[derive(Debug)]` استفاده میکنیم و خودمون متود `()fmt.` رو پیاده‌سازی نمیکنیم. به همین دلیل هست که در مستندات `std::fmt::Debug` چنین چیزی نوشته شده:
```text
Generally speaking, you should just derive a Debug implementation.
```

## Attributes

قبلا کد هایی مثل `#[derive(Debug)]` رو دیدیم، به این نوع کد ها میگن `Attribute`. این ها کد های کوچیکی هستند که به کامپایلر اطلاعاتی میدند، ساختنشون همچین اسون نیست، اما استفاده ازشون اسون هست.  اگه با استفاده از `#` یک `Attribute` بنویسیم روی خط بعدی اثر میزاره. اما اگه با استفاده از `#![derive(Debug)]` یک `Attribute` بنویسیم، روی همه‌ی کد های حوزه‌ی خودش اثر میزاره.

چندتا `Attribute` که خیلی اونهارو میبینیم:

خب `#[allow(dead_code)]` و `#[allow(unused_variables)]``. اگه کدی بنویسیم که استفاده نشه،‌ برنامه کامپایل میشه اما بهمون میگه که این هارو نوشتی اما استفاده نکردی، برای مثال در کد زیر `JustAStruct` استفاده‌ای نشده، پس `Rust` یه اخطاری میده:

```rust
struct JustAStruct {}

fn main() {
    let some_char = 'ん';
}
```
-
اخطاری که در زمان کامپایل میگیریم:

```text
warning: unused variable: `some_char`
 --> src\main.rs:4:9
  |
4 |     let some_char = 'ん';
  |         ^^^^^^^^^ help: if this is intentional, prefix it with an underscore: `_some_char`
  |
  = note: `#[warn(unused_variables)]` on by default

warning: struct is never constructed: `JustAStruct`
 --> src\main.rs:1:8
  |
1 | struct JustAStruct {}
  |        ^^^^^^^^^^^
  |
  = note: `#[warn(dead_code)]` on by default
```

میدونیم که میتونیم از `_` استفاده کنیم که کامپایلر در مورد استفاده نشدن این ها گیر نده:

```rust
struct _JustAStruct {}

fn main() {
    let _some_char = 'ん';
}
```


اما همچنین میتونیم از `Attribute` ها هم استفاده کنیم. برای مثال در کد زیر از `` و `` استفاده کردیم که کامپایل در مورد استفاده نشدن گیری نده:

```rust
#![allow(dead_code)]
#![allow(unused_variables)]

struct Struct1 {} // Create five structs
struct Struct2 {}
struct Struct3 {}
struct Struct4 {}
struct Struct5 {}

fn main() {
    let char1 = 'ん'; // and four variables. We don't use any of them but the compiler is quiet
    let char2 = ';';
    let some_str = "I'm just a regular &str";
    let some_vec = vec!["I", "am", "just", "a", "vec"];
}
```

البته، توجه به متغییر یا هر چیزی که تعریف شده اما استفاده نشده مهم هست. اما گاهی وقت ها میخوایم که کامپایلر در این باره سکوت کنه.


کد `#[derive(TraitName)]` به ما اجازه میده که `Trait` ها رو برای یک `Struct` به طور خودکار پیاده‌سازی کنیم. این برای `Trait` های رایج کار میکنه اما بعضی `Trait` ها رو باید خودمون پیاده‌سازی کنیم، برای مثال `Display` یکی از اونهایی هست که ما باید پیاده‌سازیش کنیم، چون کامپایلر نمیدونه که میخوایم چطوری نمایش بدیم:

```rust
// ⚠️
#[derive(Display)]
struct HoldsAString {
    the_string: String,
}

fn main() {
    let my_string = HoldsAString {
        the_string: "Here I am!".to_string(),
    };
}
```

خطایی که میگیریم:

```text
error: cannot find derive macro `Display` in this scope
 --> src\main.rs:2:10
  |
2 | #[derive(Display)]
  |
```

اما خب در کد زیر میتونیم ببینیم که `HoldsAString` چندین `Trait` رو به صورت خودکار پیاده‌سازی کرده:

```rust
#[derive(Debug, PartialEq, Eq, Ord, PartialOrd, Hash, Clone)]
struct HoldsAString {
    the_string: String,
}

fn main() {
    let my_string = HoldsAString {
        the_string: "Here I am!".to_string(),
    };
    println!("{:?}", my_string);
}
```

همچنین اگه تمام `Field` های یک `Struct` قابل `Copy` باشند، میتونیم از `Copy` هم استفاده کنیم. `HoldsAString` یک `Field` از نوع `String` داشت که خب `Copy` نیست. پس ما نمیتونستیم از `#[derive(Copy)` براش استفاده کنیم، اما برای `Struct` زیر میتونیم:

```rust
#[derive(Clone, Copy)] // You also need Clone to use Copy
struct NumberAndBool {
    number: i32, // i32 is Copy
    true_or_false: bool // bool is also Copy. So no problem
}

fn does_nothing(input: NumberAndBool) {

}

fn main() {
    let number_and_bool = NumberAndBool {
        number: 8,
        true_or_false: true
    };

    does_nothing(number_and_bool);
    does_nothing(number_and_bool); // If it didn't have copy, this would make an error
}
```

کد `#[cfg()]` به طور کلی برای تنظیمات هست، برای مثال میتونه به کامپایلر بگه که یک کد اجرا بشه یا نشه. معمولا اینطوری میبینیمش: `#[cfg(test)]`.

استفاده از `#[cfg(test)]` باعث میشه که وقتی فانکشن های تست مینویسیم، اونها هیچوقت اجرا نشند مگر اینکه بخوایم خودمون تست کنیم.

یک مثال دیگه از `cfg`، کد `#[cfg(target_os = "windows")]` هست. که میتونیم بگیم فقط زمانی کد رو اجرا کن که سیستم عامل `Windows` باشه.

کد `#![no_std]` هم جالب هست. این به کامپایلر میگه که به طور پیشفرض `Standard Library` رو استفاده نکن. این به این معنا هست هست که ما نمیتونیم از `Vec`، `String` یا هر چیز دیگه‌ای که داخل `Standard Library` هست، استفاده کنیم. کاربردش جایی هست که داریم برای دستگاهی برنامه مینویسیم که توان پردازشی یا حافظه‌ی کمی داره.

بقیه‌ی `Attribute` ها رو میتونیم در [اینجا](https://doc.rust-lang.org/reference/attributes.html) ببینیم.

## Box

میتونیم با استفاده از `Box` یک مقدار رو در `Heap` به جای `Stack` قرار بدیم. برای ایجاد یک `Box` از `Box::new()` استفاده میکنیم:

```rust
fn just_takes_a_variable<T>(item: T) {} // Takes anything and drops it.

fn main() {
    let my_number = 1; // This is an i32
    just_takes_a_variable(my_number);
    just_takes_a_variable(my_number); // Using this function twice is no problem, because it's Copy

    let my_box = Box::new(1); // This is a Box<i32>
    just_takes_a_variable(my_box.clone()); // Without .clone() the second function would make an error
    just_takes_a_variable(my_box); // because Box is not Copy
}
```

در اولین مواجهه با این نوع تصورش سخته که کجا باید ازش استفاده کنیم، اما در `Rust` خیلی ما ازش استفاده میکنیم.

خب ما یادمون هست که ما از `&` برای `str` استفاده میکنیم به این دلیل که کامپایلر سایز `str` رو نمیدونه، چون `str` میتونه هر سایزی داشته باشه، اما سایز `&` همیشه ثابت هست، پس کامپایلر ازش استفاده میکنه. `Box` هم شبیه به همین هست، ما میتونیم از `*` روی `Box` استفاده کنیم که مقدار رو بگیریم:

```rust
fn main() {
    let my_box = Box::new(1); // This is a Box<i32>
    let an_integer = *my_box; // This is an i32
    println!("{:?}", my_box);
    println!("{:?}", an_integer);
}
```

به همین دلیل هست که به `Box` میگیم `Smart Pointer`. چون شبیه به `&` هست که `&` خودش یک نوع `Pointer` هست، اما در عین حال `Box` میتونه کار های بیشتری هم انجام بده.

ما همچنین میتونیم از `Box` برای ساختن ساختار هایی که خودشون در خودشون دارند، استفاده کنیم. به این ساختار ها میگیم `Recursive` که یعنی ساختار `A` میتونه یک ساختار `A` در خودش داشته باشه. میتونیم از `Box` برای ساخت `Linked List` استفاده کنیم. با اینکه این ساختارداده در `Rust` همچین محبوب نیست.

پس اگه بخوایم یک `Recursive Struct` بسازیم میتونیم از `Box` استفاده کنیم. اگه از `Box` استفاده نکنیم چنین اتفاقی میوفته:

```rust
struct List {
    item: Option<List>, // ⚠️
}
```
کد بالا یک ساختار ساده هست که یک ایتم داره که میتونه `Some<List>` باشه یا `None` باشه. به این دلیل که میتونه `None` باشه این ساختار تا ابد `Recursive` نیست. اما با این حال کامپایلر همچنان سایز رو نمیدونه:

```text
error[E0072]: recursive type `List` has infinite size
  --> src\main.rs:16:1
   |
16 | struct List {
   | ^^^^^^^^^^^ recursive type has infinite size
17 |     item: Option<List>,
   |     ------------------ recursive without indirection
   |
   = help: insert indirection (e.g., a `Box`, `Rc`, or `&`) at some point to make `List` representable
```

میبینیم که کامپایلر پیشنهاد میکنه که از `Box` استفاده کنیم. پس بزارید از `Box` استفاده کنیم:

```rust
struct List {
    item: Option<Box<List>>,
}
fn main() {}
```

الان کامپایلر مشکلی با کدمون نداره، به این دلیل که همه‌چیز پشت یک `Box` هست. و خب کامپایلر سایز `Box` رو میدونه.

پس لیست ساده میتونه چنین چیزی باشه:

```rust
struct List {
    item: Option<Box<List>>,
}

impl List {
    fn new() -> List {
        List {
            item: Some(Box::new(List { item: None })),
        }
    }
}

fn main() {
    let mut my_list = List::new();
}
```
هرچند بدون داده یکم پیچیده هست. `Rust` هم زیاد از این الگو استفاده نمیکنه. این قضیه به این دلیل هست که `Rust` خیلی روی `Borrowing` و `Ownership` سخت‌گیر هست. اما اگه بخوایم یک `Linked List` بسازیم میتونیم از `Box` کمک بگیریم.

همچنین یک `Box` اجازه میده که از `std::mem::drop` استفاده کنیم. به این دلیل که مقدار در قسمت `Heap` حافظه قرار میگیره.

## Box around traits

نوع `Box` برای برگردوندن `Trait` ها کاربردی هست. میدونیم که میتونم از `Trait` ها در ساختن فانکشن `Generic` استفاده کنیم:

```rust
use std::fmt::Display;

struct DoesntImplementDisplay {}

fn displays_it<T: Display>(input: T) {
    println!("{}", input);
}

fn main() {}
```

در کد بالا فانکشن `displays_it` هر چیزی که `Display` رو پیاده‌سازی کرده باشه رو میتونه به عنوان ورودی بگیره. پس نمیتونه نوع `DoesntImplementDisplay` رو بگیره، چون `Display` رو پیاده‌سازی نکرده. اما میتونه نوع های دیگه‌ای که `Display` رو پیاده‌سازی کردند رو بگیره.

همچنین قبلا دیدیم که میتونیم از `impl Trait` استفاده کنیم که یک `Trait` یا حتی یک `Closure` رو برگردونیم. `Box` هم میتونه برای اینکار استفاده بشه. اگه از `Box` استفاده نکنیم، کامپایلر سایز نوعی که میخوایم برگردونیم رو نمیدونه. در مثال زیر میتونیم ببینیم که چیزی که یک `Trait` رو پیاده‌سازی میکنه میتونه هر سایزی داشته باشه:

```rust
#![allow(dead_code)] // Tell the compiler to be quiet
use std::mem::size_of; // This gives the size of a type

trait JustATrait {} // We will implement this on everything

enum EnumOfNumbers {
    I8(i8),
    AnotherI8(i8),
    OneMoreI8(i8),
}
impl JustATrait for EnumOfNumbers {}

struct StructOfNumbers {
    an_i8: i8,
    another_i8: i8,
    one_more_i8: i8,
}
impl JustATrait for StructOfNumbers {}

enum EnumOfOtherTypes {
    I8(i8),
    AnotherI8(i8),
    Collection(Vec<String>),
}
impl JustATrait for EnumOfOtherTypes {}

struct StructOfOtherTypes {
    an_i8: i8,
    another_i8: i8,
    a_collection: Vec<String>,
}
impl JustATrait for StructOfOtherTypes {}

struct ArrayAndI8 {
    array: [i8; 1000], // This one will be very large
    an_i8: i8,
    in_u8: u8,
}
impl JustATrait for ArrayAndI8 {}

fn main() {
    println!(
        "{}, {}, {}, {}, {}",
        size_of::<EnumOfNumbers>(),
        size_of::<StructOfNumbers>(),
        size_of::<EnumOfOtherTypes>(),
        size_of::<StructOfOtherTypes>(),
        size_of::<ArrayAndI8>(),
    );
}
```
خروجی برنامه میشه: `2, 3, 32, 32, 1002`

پس اگه چنین کاری رو بکنیم خطا میگیریم:

```rust
// ⚠️
fn returns_just_a_trait() -> JustATrait {
    let some_enum = EnumOfNumbers::I8(8);
    some_enum
}
```

خطایی که میده:

```text
error[E0746]: return type cannot have an unboxed trait object
  --> src\main.rs:53:30
   |
53 | fn returns_just_a_trait() -> JustATrait {
   |                              ^^^^^^^^^^ doesn't have a size known at compile-time
```

و خب خطایی که میده منطقی هست، به این دلیل که سایز چیزی که `JustATrait` رو پیاده‌سازی کرده میتونه هر چیزی باشه، برای مثال همونطور که دیدیم میتونه `2`، `3`، `32`، `1002` یا هر چیز دیگه باشه.

پس ما از `Box` استفاده میکنیم، همچنین کلمه‌کلیدی `dyn` رو هم استفاده میکنیم. وقتی از `dyn` استفاده میکنیمبه کامپایلر میگیم که داریم در مورد `Trait` ها صحبت میکنیم و در حال صحبت در مورد یک ساختار یا هر چیز دیگه‌ای نیستیم.

پس فانکشن رو به چنین چیزی تغییر میدیم:

```rust
// 🚧
fn returns_just_a_trait() -> Box<dyn JustATrait> {
    let some_enum = EnumOfNumbers::I8(8);
    Box::new(some_enum)
}
```

و خب کدی که نوشتیم کار میکنه چون در قسمت `Stack` فقط نوع `Box` وجود داره و خب کامپایلر سایز `Box` رو میدونه.


ما معولا کد `Box<dyn Error>` رو زیاد میبینیم، چون گاهی وقت ها احتمال داره بیشتر چند `Error` رخ بده.

ما میتونیم سریع چند نوع `Error` بسازیم که این موضوع رو نشون بدیم. برای اینکه یک نوع رسمی `Error` بسازیم، باید `std::error::Error` رو پیاده‌سازی کنیم. برای اینکار فقط باید کد `impl std::error:Error {}` رو بنویسیم. اما `Error` ها باید `Debug` و `Display` رو هم پیاده‌سازی کنند که بتونند اطلاعاتی رو نشون بدن. `Debug` رو میتونیم با `#[derive(Debug)]` پیاده‌سازی کنیم. اما برای پیاده‌سازی `Display` نیاز داریم که `()fmt.` رو پیاده‌سازی کنیم:

```rust
use std::error::Error;
use std::fmt;

#[derive(Debug)]
struct ErrorOne;

impl Error for ErrorOne {} // Now it is an error type with Debug. Time for Display:

impl fmt::Display for ErrorOne {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        write!(f, "You got the first error!") // All it does is write this message
    }
}


#[derive(Debug)] // Do the same thing with ErrorTwo
struct ErrorTwo;

impl Error for ErrorTwo {}

impl fmt::Display for ErrorTwo {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        write!(f, "You got the second error!")
    }
}

// Make a function that just returns a String or an error
fn returns_errors(input: u8) -> Result<String, Box<dyn Error>> { // With Box<dyn Error> you can return anything that has the Error trait

    match input {
        0 => Err(Box::new(ErrorOne)), // Don't forget to put it in a box
        1 => Err(Box::new(ErrorTwo)),
        _ => Ok("Looks fine to me".to_string()), // This is the success type
    }

}

fn main() {

    let vec_of_u8s = vec![0_u8, 1, 80]; // Three numbers to try out

    for number in vec_of_u8s {
        match returns_errors(number) {
            Ok(input) => println!("{}", input),
            Err(message) => println!("{}", message),
        }
    }
}
```

چیزی که پرینت میکنه:

```text
You got the first error!
You got the second error!
Looks fine to me
```

اگه از `Box<dyn Error>` استفاده نکنیم، به مشکل میخوریم:

```rust
// ⚠️
fn returns_errors(input: u8) -> Result<String, Error> {
    match input {
        0 => Err(ErrorOne),
        1 => Err(ErrorTwo),
        _ => Ok("Looks fine to me".to_string()),
    }
}
```

خطایی که میده:

```text
21  | fn returns_errors(input: u8) -> Result<String, Error> {
    |                                 ^^^^^^^^^^^^^^^^^^^^^ doesn't have a size known at compile-time
```

این موضوع شگفت‌انگیز نیست چون میدونیم که نوع هایی که یک `Trait` رو پیاده‌سازی میکنند میتونند سایز های مختلفی داشته باشند.

## Default and the builder pattern

ما میتونیم با پیاده‌سازی `Default` مقدار های پیشفرضی به `Struct` ها یا `Enum` ها بدیم.

الگوی `Builder` الگویی هست که به کاربر اجازه میده یک نوع رو در هنگام ساخت مقدار دهی کنند.

اول بزارید به `Default` نگاهی بندازیم. در حقیقت اکثر نوع ها در `Rust`، `Default` رو پیاده‌سازی کردند. برای مثال `0` برای `Integer Type` ها، `""` برای `String` ها، `false` برای `bool` ها و...

```rust
fn main() {
    let default_i8: i8 = Default::default();
    let default_str: String = Default::default();
    let default_bool: bool = Default::default();

    println!("'{}', '{}', '{}'", default_i8, default_str, default_bool);
}
```

خروجیش میشه: `'0', '', 'false'`

پس `Default` تقریبا شبیه به `new` هست، با این تفاوت که نیازی ندایم چیزی بهش به عنوان ورودی بدیم. بزارید یک ساختار درست کنیم که `Default` رو پیاده‌سازی نکرده. اما `new` رو پیاده‌سازی کرده. ما یک `Character` به نام `Billy` میسازیم و یکسری `Stat` هم بهش میدیم:

```rust
struct Character {
    name: String,
    age: u8,
    height: u32,
    weight: u32,
    lifestate: LifeState,
}

enum LifeState {
    Alive,
    Dead,
    NeverAlive,
    Uncertain
}

impl Character {
    fn new(name: String, age: u8, height: u32, weight: u32, alive: bool) -> Self {
        Self {
            name,
            age,
            height,
            weight,
            lifestate: if alive { LifeState::Alive } else { LifeState::Dead },
        }
    }
}

fn main() {
    let character_1 = Character::new("Billy".to_string(), 15, 170, 70, true);
}
```

اما تصور کنید که در دنیایی که داریم کد میزنیم اکثر `Character` ها اسمشون `Billy` هست و سنشون `15` و قدشون `170` و وزنشون `70` هست. پس ما میتونیم `Default` رو پیاده‌سازی کنیم که برای ساخت یک `Character` با خصوصیاتی که گفتیم فقط از کد `Character::default()` استفاده کنیم:

```rust
#[derive(Debug)]
struct Character {
    name: String,
    age: u8,
    height: u32,
    weight: u32,
    lifestate: LifeState,
}

#[derive(Debug)]
enum LifeState {
    Alive,
    Dead,
    NeverAlive,
    Uncertain,
}

impl Character {
    fn new(name: String, age: u8, height: u32, weight: u32, alive: bool) -> Self {
        Self {
            name,
            age,
            height,
            weight,
            lifestate: if alive {
                LifeState::Alive
            } else {
                LifeState::Dead
            },
        }
    }
}

impl Default for Character {
    fn default() -> Self {
        Self {
            name: "Billy".to_string(),
            age: 15,
            height: 170,
            weight: 70,
            lifestate: LifeState::Alive,
        }
    }
}

fn main() {
    let character_1 = Character::default();

    println!(
        "The character {:?} is {:?} years old.",
        character_1.name, character_1.age
    );
}
```

چیزی که پرینت میکنه: `The character "Billy" is 15 years old.`


خب برسیم به الگوی `Builder`. ما `Default` رو نگه میداریم. اما بعضی `Character` ها کمی تفاوت دارند، پس ما کاری میکنیم که بشه در هنگام ساخت مقادیر رو تغییر هم داد. الگوی `Builder` به ما اجازه میده که متود ها رو به هم مثل زنجیر وصل کنیم:

```rust
fn height(mut self, height: u32) -> Self {    // 🚧
    self.height = height;
    self
}
```
حتما متوجه شدید که `mut self` میگیره. خب این `&mut self` نیست. در حقیقت `mut self` مالکیت `Self` رو `Mutable` میگیره، حتی اگه قبلا `Mutable` نبوده باشه. این بدلیل این هست که `()height.` مالکیت رو میگیره و چیز دیگه‌ای هم کاری به `Self` نداره، پس مشکلی نیست که `Mutable` باشه. بعد ما `self.height` رو مقداردهی میکنیم و دوباره `Self` رو برمیگردونیم:

```rust
fn height(mut self, height: u32) -> Self {     // 🚧
    self.height = height;
    self
}

fn weight(mut self, weight: u32) -> Self {
    self.weight = weight;
    self
}

fn name(mut self, name: &str) -> Self {
    self.name = name.to_string();
    self
}
```

هر کدوم از این متود ها یک متغییر `Self` میگیرند و برمیگردونند، این چیزی هست که الگوی `Builder` اتفاق میوقته. پس الان میتونیم کدی شبیه به `let character_1 = Character::default().height(180).weight(60).name("Bobby")` بنویسیم.

اگه داریم یک `Library` برای استفاده دیگران میسازیم، ایده‌ی خوبی هست که از الگوی `Builder` استفاده کنیم، به این دلیل که استفاده راحت میشه و کد هم راحت‌تر خونده میشه:

```rust
#[derive(Debug)]
struct Character {
    name: String,
    age: u8,
    height: u32,
    weight: u32,
    lifestate: LifeState,
}

#[derive(Debug)]
enum LifeState {
    Alive,
    Dead,
    NeverAlive,
    Uncertain,
}

impl Character {
    fn new(name: String, age: u8, height: u32, weight: u32, alive: bool) -> Self {
        Self {
            name,
            age,
            height,
            weight,
            lifestate: if alive {
                LifeState::Alive
            } else {
                LifeState::Dead
            },
        }
    }

    fn height(mut self, height: u32) -> Self {
        self.height = height;
        self
    }

    fn weight(mut self, weight: u32) -> Self {
        self.weight = weight;
        self
    }

    fn name(mut self, name: &str) -> Self {
        self.name = name.to_string();
        self
    }
}

impl Default for Character {
    fn default() -> Self {
        Self {
            name: "Billy".to_string(),
            age: 15,
            height: 170,
            weight: 70,
            lifestate: LifeState::Alive,
        }
    }
}

fn main() {
    let character_1 = Character::default().height(180).weight(60).name("Bobby");

    println!("{:?}", character_1);
}
```

معمولا اخرین متودی استفاده میشه `()build.` هست. این متود یک جورایی چک میکنه که همه‌ی مقادیر معتبر باشند. به همین دلیل `()build.` یک `Result` برمیگردونه. اگه مشکلی با مقادیر وجود نداشت `Ok(Self)` رو برمیگردونیم.

اول بزارید `()new.` رو تغییر بدیم. نمیخوایم که کاربر بتونه هر چیزی رو بدون اینکه اعتبار‌سنجی بشه بسازه. پس کد های `()default.` رو در `()new.` مینویسیم و الان `()new.` ورودی هم نمیگیره:

```rust
    fn new() -> Self {    // 🚧
        Self {
            name: "Billy".to_string(),
            age: 15,
            height: 170,
            weight: 70,
            lifestate: LifeState::Alive,
        }
    }
```

خب ما `Defult` رو هم پیاده‌سازی نمیکنیم، به این دلیل که `()new.` مقدار های پیشفرض رو به ما میده.

کدمون چنین چیزی شده:

```rust
#[derive(Debug)]
struct Character {
    name: String,
    age: u8,
    height: u32,
    weight: u32,
    lifestate: LifeState,
}

#[derive(Debug)]
enum LifeState {
    Alive,
    Dead,
    NeverAlive,
    Uncertain,
}

impl Character {
    fn new() -> Self {
        Self {
            name: "Billy".to_string(),
            age: 15,
            height: 170,
            weight: 70,
            lifestate: LifeState::Alive,
        }
    }

    fn height(mut self, height: u32) -> Self {
        self.height = height;
        self
    }

    fn weight(mut self, weight: u32) -> Self {
        self.weight = weight;
        self
    }

    fn name(mut self, name: &str) -> Self {
        self.name = name.to_string();
        self
    }
}

fn main() {
    let character_1 = Character::new().height(180).weight(60).name("Bobby");

    println!("{:?}", character_1);
}
```

چیزی که پرینت میکنه: `Character { name: "Bobby", age: 15, height: 180, weight: 60, lifestate: Alive }`

خب ما تقریبا اماده هستیم که متود `()build.` رو بنویسیم، اما یک مشکل داریم، چطوری کاربر رو مجبور کنیم که حتما از `()build.` استفاده کنه؟ الان کاربر میتونه کد `let x = Character::new().height(76767)` رو بنویسه و `Character` رو بگیره.

خب راه های زیادی برای اینکار هست، اما خب در ساده‌ترین حالت میتونیم یک `can_use: bool` به `Character` اضافه کنیم که این مقدار فقط در `()build.` تغییر میکنه:

```rust
#[derive(Debug)]       // 🚧
struct Character {
    name: String,
    age: u8,
    height: u32,
    weight: u32,
    lifestate: LifeState,
    can_use: bool, // Set whether the user can use the character
}

\\ Cut other code

    fn new() -> Self {
        Self {
            name: "Billy".to_string(),
            age: 15,
            height: 170,
            weight: 70,
            lifestate: LifeState::Alive,
            can_use: true, // .new() always gives a good character, so it's true
        }
    }
```

برای بقیه متود ها مثل `()height.` ما `can_use` رو به `false` تغییر میدیم. پس فقط `()build.` میتونه `can_use` رو `true` کنه. پس ما کاربر رو یک جورایی مجبور کردیم که از `()build.` استفاده کنه. و حالا میتونیم در `()build.` مقدار ها رو اعتبار سنجی کنیم:

کد متود `()build.` چیزی شبیه به این هست:

```rust
fn build(mut self) -> Result<Character, String> {      // 🚧
    if self.height < 200 && self.weight < 300 && !self.name.to_lowercase().contains("smurf") {
        self.can_use = true;
        Ok(self)
    } else {
        Err("Could not create character. Characters must have:
1) Height below 200
2) Weight below 300
3) A name that is not Smurf (that is a bad word)"
            .to_string())
    }
}
```

کد `!self.name.to_lowercase().contains("smurf")` باعث میشه که اطمینان پیدا کنیم کاربر از کلمه‌ی `smurf` در اسم شخصیت استف اده نکرده. متود `()lowecase.` یک `String` رو تبدیل به حروف کوچیک میکنه و بعد ما با `()contais.` چک میکنیم که ایا `String` شامل `smurf` هست یا خیر.

اگه چیزی مشکلی نداشت ما `can_use` رو به تغییر `true` تغییر میدیم و `Character` رو درون `Ok` برمیگردونیم.

خب الان کدمون کار میکنه، برای مثال ما چند `Character` میسازیم که معتبر نیستند و...:

```rust
#[derive(Debug)]
struct Character {
    name: String,
    age: u8,
    height: u32,
    weight: u32,
    lifestate: LifeState,
    can_use: bool, // Here is the new value
}

#[derive(Debug)]
enum LifeState {
    Alive,
    Dead,
    NeverAlive,
    Uncertain,
}

impl Character {
    fn new() -> Self {
        Self {
            name: "Billy".to_string(),
            age: 15,
            height: 170,
            weight: 70,
            lifestate: LifeState::Alive,
            can_use: true,  // .new() makes a fine character, so it is true
        }
    }

    fn height(mut self, height: u32) -> Self {
        self.height = height;
        self.can_use = false; // Now the user can't use the character
        self
    }

    fn weight(mut self, weight: u32) -> Self {
        self.weight = weight;
        self.can_use = false;
        self
    }

    fn name(mut self, name: &str) -> Self {
        self.name = name.to_string();
        self.can_use = false;
        self
    }

    fn build(mut self) -> Result<Character, String> {
        if self.height < 200 && self.weight < 300 && !self.name.to_lowercase().contains("smurf") {
            self.can_use = true;   // Everything is okay, so set to true
            Ok(self)               // and return the character
        } else {
            Err("Could not create character. Characters must have:
1) Height below 200
2) Weight below 300
3) A name that is not Smurf (that is a bad word)"
                .to_string())
        }
    }
}

fn main() {
    let character_with_smurf = Character::new().name("Lol I am Smurf!!").build(); // This one contains "smurf" - not okay
    let character_too_tall = Character::new().height(400).build(); // Too tall - not okay
    let character_too_heavy = Character::new().weight(500).build(); // Too heavy - not okay
    let okay_character = Character::new()
        .name("Billybrobby")
        .height(180)
        .weight(100)
        .build();   // This character is okay. Name is fine, height and weight are fine

    // Now they are not Character, they are Result<Character, String>. So let's put them in a Vec so we can see them:
    let character_vec = vec![character_with_smurf, character_too_tall, character_too_heavy, okay_character];

    for character in character_vec { // Now we will print the character if it's Ok, and print the error if it's Err
        match character {
            Ok(character_info) => println!("{:?}", character_info),
            Err(err_info) => println!("{}", err_info),
        }
        println!(); // Then add one more line
    }
}
```

خروجی کد بالا:

```text
Could not create character. Characters must have:
1) Height below 200
2) Weight below 300
3) A name that is not Smurf (that is a bad word)

Could not create character. Characters must have:
1) Height below 200
2) Weight below 300
3) A name that is not Smurf (that is a bad word)

Could not create character. Characters must have:
1) Height below 200
2) Weight below 300
3) A name that is not Smurf (that is a bad word)

Character { name: "Billybrobby", age: 15, height: 180, weight: 100, lifestate: Alive, can_use: true }
```

## Deref and DerefMut

خب `Deref` یک `Trait` هست که به ما اجازه میده از `*` روی یک نوع استفاده کنیم که `Dereference` کنیمش.

میدونیم که یک `Reference` با نوعی که بهش اشاره میکنه فرق میکنه، پس نمیتونه با اون نوع مقایسه بشه:

```rust
// ⚠️
fn main() {
    let value = 7; // This is an i32
    let reference = &7; // This is a &i32
    println!("{}", value == reference);
}
```
در کد بالا حتی `false` رو نمیبینیم، به این دلیل که کامپایلر اجازه کامپایل شدن برنامه رو نمیده چون نمیتونه نوع `i32` رو با `&i32` مقایسه کنه:

```text
error[E0277]: can't compare `{integer}` with `&{integer}`
 --> src\main.rs:4:26
  |
4 |     println!("{}", value == reference);
  |                          ^^ no implementation for `{integer} == &{integer}`
```

البته خب برای اینکه مقدار یک `Reference` رو بگیریم میتونیم از `*` استفاده کنیم:

```rust
fn main() {
    let value = 7;
    let reference = &7;
    println!("{}", value == *reference);
}
```

حالا بزارید یک ساختار بسازیم که فقط یک عدد رو نگه میداره. چیزی شبیه به `Box` مبشه، و ما میخوایم یکسری قابلیت ها بهش اضافه کنیم.

ما نمیتونیم از `*` روی `HoldsANumber` استفاده کنیم، چون این نوع `Deref` رو پیاده‌سازی نکرده:
```rust
// ⚠️
struct HoldsANumber(u8);

fn main() {
    let my_number = HoldsANumber(20);
    println!("{}", *my_number + 20);
}
```

چنین خطایی رو میده:

```text
error[E0614]: type `HoldsANumber` cannot be dereferenced
  --> src\main.rs:24:22
   |
24 |     println!("{:?}", *my_number + 20);
```

البته ما میتونیم چنین کاری کنیم: `println!("{:?}", my_number.0 + 20)`

اما میخوایم که مستقیم `Derefrence`اش کنیم. دیدیم که خطای ``type `HoldsANumber` cannot be dereferenced`` رو به ما داد، پس ما باید `Deref` رو براش پیاده‌سازی کنیم.

گاهی اوقات به چیزی که `Deref` رو پیاده‌سازی میکنه، میگیم `Smart Pointer`. یک `Smart Pointer` میتونه به یک چیزی اشاره کنه و یکسری اطلاعات هم در مورد اون چیز داره و یکسری قابلیت ها هم به ما میده.

حقیقت جالب: نوع `String` یک `Smart Pointer` به `&str` هست. همچنین `Vec` هم یک `Smart Pointer` به `Array`(یا نوع های دیگه) هست. ما خیلی وقت هست که درحال استفاده از `Smart Pointer` هستیم.

پیاده‌سازی `Deref` زیاد سخت نیست، میتونیم مثال هایی که در [`Standard Library](https://doc.rust-lang.org/std/ops/trait.Deref.html) هست رو ببینیم:

```rust
use std::ops::Deref;

struct DerefExample<T> {
    value: T
}

impl<T> Deref for DerefExample<T> {
    type Target = T;

    fn deref(&self) -> &Self::Target {
        &self.value
    }
}

fn main() {
    let x = DerefExample { value: 'a' };
    assert_eq!('a', *x);
}
```

خب با الهام گرفتن از همون مثال، میایم که `HoldsANumber` رو تبدیل به `Smart Pointer` کنیم:

```rust
// 🚧
impl Deref for HoldsANumber {
    type Target = u8; // Remember, this is the "associated type": the type that goes together.
                      // You have to use the right type Target = (the type you want to return)

    fn deref(&self) -> &Self::Target { // Rust calls .deref() when you use *. We just defined Target as a u8 so this is easy to understand
        &self.0   // We chose &self.0 because it's a tuple struct. In a named struct it would be something like "&self.number"
    }
}
```

خب الان میتونیم از `*` روی `HoldsANumber` استفاده کنیم:

```rust
use std::ops::Deref;
#[derive(Debug)]
struct HoldsANumber(u8);

impl Deref for HoldsANumber {
    type Target = u8;

    fn deref(&self) -> &Self::Target {
        &self.0
    }
}

fn main() {
    let my_number = HoldsANumber(20);
    println!("{:?}", *my_number + 20);
}
```
خب چیزی که کد بالا پرینت میکنه، `` هست. ما دیگه ما لازم نیست `my_number.0` رو بنویسیم.

همچنین این به این معنی هست که ما متود های `u8` رو میتونیم استفاده کنیم، همچنین میتونیم برای `HoldsANumber` هم متود بسازیم.

برای مثال ما متود `checked_sub()` رو میسازیم که یک متودی هست که سعی میکنه تفریق انجام بده و مقدار بازگشتیش هم یک `Option` هست:

```rust
use std::ops::Deref;

struct HoldsANumber(u8);

impl HoldsANumber {
    fn prints_the_number_times_two(&self) {
        println!("{}", self.0 * 2);
    }
}

impl Deref for HoldsANumber {
    type Target = u8;

    fn deref(&self) -> &Self::Target {
        &self.0
    }
}

fn main() {
    let my_number = HoldsANumber(20);
    println!("{:?}", my_number.checked_sub(100)); // This method comes from u8
    my_number.prints_the_number_times_two(); // This is our own method
}
```

خروجیش:

```text
None
40
```

همچنین میتونیم `DerefMut` رو پیاده‌سازی کنیم که بتونیم مقدار رو با استفاده از `*` تغییر هم بدیم. همچنین بهتره یادمون باشه که برای اینکه `DerefMut` رو پیاده‌سازی کنیم باید از قبل `Deref` رو پیاده‌سازی کرده باشیم:

```rust
use std::ops::{Deref, DerefMut};

struct HoldsANumber(u8);

impl HoldsANumber {
    fn prints_the_number_times_two(&self) {
        println!("{}", self.0 * 2);
    }
}

impl Deref for HoldsANumber {
    type Target = u8;

    fn deref(&self) -> &Self::Target {
        &self.0
    }
}

impl DerefMut for HoldsANumber { // You don't need type Target = u8; here because it already knows thanks to Deref
    fn deref_mut(&mut self) -> &mut Self::Target { // Everything else is the same except it says mut everywhere
        &mut self.0
    }
}

fn main() {
    let mut my_number = HoldsANumber(20);
    *my_number = 30; // DerefMut lets us do this
    println!("{:?}", my_number.checked_sub(100));
    my_number.prints_the_number_times_two();
}
```

خب میبینیم که `Deref` قابلیت های جالبی به نوع ما داد.

به همین دلیل هست که در `Standard Library` میبینیم که چنین چیزی گفته شده: 

این به دلیل این هست که ما میتونیم با پیاده‌سازی `Deref` کار های عجیبی هم انجام بدیم که میتونه باعث بالا رفتن پیچیدگی بشه.

برای مثال درک کد زیر خیلی سخت هست، ما یک ساختار به نام `Character` ساختیم. یک `Character` چندین ویژگی داره مثل `intelligence` و `strength`. بزارید کد رو ببینیم:

```rust
struct Character {
    name: String,
    strength: u8,
    dexterity: u8,
    health: u8,
    intelligence: u8,
    wisdom: u8,
    charm: u8,
    hit_points: i8,
    alignment: Alignment,
}

impl Character {
    fn new(
        name: String,
        strength: u8,
        dexterity: u8,
        health: u8,
        intelligence: u8,
        wisdom: u8,
        charm: u8,
        hit_points: i8,
        alignment: Alignment,
    ) -> Self {
        Self {
            name,
            strength,
            dexterity,
            health,
            intelligence,
            wisdom,
            charm,
            hit_points,
            alignment,
        }
    }
}

enum Alignment {
    Good,
    Neutral,
    Evil,
}

fn main() {
    let billy = Character::new("Billy".to_string(), 9, 8, 7, 10, 19, 19, 5, Alignment::Good);
}
```

خب بیاید تصور کنیم که ما میخوایم نقاط ضریه‌ی شخصیت رو در یک `Vec` نگهداری کنیم. شاید داده‌های هیولا بازی رو هم درش نگهداری کردیم. از اونجایی که `hit_points` یک `i8` هست. ما `Deref` رو براش پیاده‌سازی کردیم که بتونیم کار های ریاضی روش انجام بدیم. اما کدمون خیلی عجیب شده:

```rust
use std::ops::Deref;

// All the other code is the same until after the enum Alignment
struct Character {
    name: String,
    strength: u8,
    dexterity: u8,
    health: u8,
    intelligence: u8,
    wisdom: u8,
    charm: u8,
    hit_points: i8,
    alignment: Alignment,
}

impl Character {
    fn new(
        name: String,
        strength: u8,
        dexterity: u8,
        health: u8,
        intelligence: u8,
        wisdom: u8,
        charm: u8,
        hit_points: i8,
        alignment: Alignment,
    ) -> Self {
        Self {
            name,
            strength,
            dexterity,
            health,
            intelligence,
            wisdom,
            charm,
            hit_points,
            alignment,
        }
    }
}

enum Alignment {
    Good,
    Neutral,
    Evil,
}

impl Deref for Character { // impl Deref for Character. Now we can do any integer math we want!
    type Target = i8;

    fn deref(&self) -> &Self::Target {
        &self.hit_points
    }
}



fn main() {
    let billy = Character::new("Billy".to_string(), 9, 8, 7, 10, 19, 19, 5, Alignment::Good); // Create two characters, billy and brandy
    let brandy = Character::new("Brandy".to_string(), 9, 8, 7, 10, 19, 19, 5, Alignment::Good);

    let mut hit_points_vec = vec![]; // Put our hit points data in here
    hit_points_vec.push(*billy);     // Push *billy?
    hit_points_vec.push(*brandy);    // Push *brandy?

    println!("{:?}", hit_points_vec);
}
```
خروجی کد بالا میشه: `[5, 5]`

اما کدمون خیلی سخت توسط فرد دیگه‌ای خونده میشه. ما باید `Deref` بالای `()main` رو بخونیم تا بفهمیم که `*billy` یک `i8` هست. اما با همین روش یک کد های زیادی بنویسیم واقعا خوندنش سخت میشه که باعث میشه نتونیم کد رو بفهمیم.

البته این روش غیرمجاز نیست اما خب کد رو عجیب میکنه، اما خب از اول بهتر بود به جای پیاده‌سازی `Deref` یک متودی مثل `.get_hp()` مینوشتیم.

پیاده‌سازی `Deref` قابلیت های زیادی به ما میده اما باید منطقی ازش استفاده کنیم.

## Crates and modules

هر وقت که در حال نوشتن کدی در `Rust` هستیم، داریم اون رو در یک `crate` مینویسیم.

یک `crate` میتونه یک فایل یا چند فایل باشه.

در یک `crate` میتونیم با استفاده از `mod`، یک `module` بسازیم.

خب `module` جایی هست که میتونیم درش `Function` ها، `Struct` ها و... رو درش قرار بدیم.

استفاده از `modoule` ها چنین قابلیت هایی رو میده:
- میتونیم بهتر به ساختار کلی کد نگاه کنیم، این خیلی مهم هست، بخصوص زمانی که مقدار کد ها زیاد میشه
- میتونیم راحت‌تر کد رو بخونیم، این کمک میکنه که بشه روی کد کار کرد، وقتی کد راحت قابل درک باشه بقیه افراد میتونند به راحتی کد رو توسعه بدند، برای مثال اسم `std::collections::HashMap` به ما میگه که درون `std` در ماژول `collections`، نوع `HashMap` وجود داره، که خب میتونیم بفهمیم احتمالا درون ماژول `collections` نوع های دیگه‌ای هم وجود داره
- حریم خصوصی هم میاره، میتونیم فانکشن ها و... هایی رو که کاربر نیاز داره رو خصوصی(`Private`) کنیم

برای ساخت یک ماژول میتونیم از کلمه‌کلیدی `mod` کمک بگیریم و بعد کد ها رو درون `{}` بنویسیم. برای مثال در کد زیر ما یک ماژول به نام `print_things` درست کردیم که فانکشن هایی که به پرینت کردن مربوط هست رو داره:

```rust
mod print_things {
    use std::fmt::Display;

    fn prints_one_thing<T: Display>(input: T) { // Print anything that implements Display
        println!("{}", input)
    }
}

fn main() {}
```

دیدیم که ما کد `use std::fmt::Display` رو درون `print_things` نوشتیم، به این دلیل که از `main` جدا هست. و اگه `use std::fmt::Display` رو در `main` مینوشتیم نمیتونستیم ازش در `print_things` استفاده کنیم و برعکس. همچنین تا زمانی که از `pub` قبل از `fn` استفاده نکنیم، نمیتونیم از `prints_one_thing` بیرون از این ماژول استفاده کنیم، به این دلیل که خصوصی هست. بزارید بدون `pub` سعی کنیم ازش استفاده کنیم:

```rust
// 🚧
fn main() {
    crate::print_things::prints_one_thing(6);
}
```
کلمه‌کلیدی `crate` در کد بالا، به معنای "همین پروژه" هست ولی در کد بالا به معنای همین فایل هم هست، چون چیز دیگه‌ای به جز این فایل وجود نداره. درون این `crate` ما ماژول `print_things` رو داریم، بعد هم `prints_one_thing` رو داریم. میتونیم هر بار این رو بنویسیم یا با استفاده از `use` این ماژول رو `Import` کنیم، خب میدونیم که `prints_one_thing` خصوصی هست به همین دلیل نمیتونیم ازش استفاده کنیم، اما بزارید خطایی که میده رو هم ببینیم:

```rust
// ⚠️
mod print_things {
    use std::fmt::Display;

    fn prints_one_thing<T: Display>(input: T) {
        println!("{}", input)
    }
}

fn main() {
    use crate::print_things::prints_one_thing;

    prints_one_thing(6);
    prints_one_thing("Trying to print a string...".to_string());
}
```

خطایی که کامپایلر میده:

```text
error[E0603]: function `prints_one_thing` is private
  --> src\main.rs:10:30
   |
10 |     use crate::print_things::prints_one_thing;
   |                              ^^^^^^^^^^^^^^^^ private function
   |
note: the function `prints_one_thing` is defined here
  --> src\main.rs:4:5
   |
4  |     fn prints_one_thing<T: Display>(input: T) {
   |     ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
```

خب راحت میتونیم بفهمیم که `prints_one_thing` خصوصی هست. همچنین میگه که فانکشن در مسیر `src\main.rs:4:5` وجود داره. این ادرس دهی کاربردی هست به این دلیل که ما میتونیم در چند فایل یک ماژول رو بنویسیم.

خب حالا بزارید با استفاده از کلمه‌کلیدی `pub` فانکشن `prints_one_thing` رو عمومی(`Public`) کنیم:

```rust
mod print_things {
    use std::fmt::Display;

    pub fn prints_one_thing<T: Display>(input: T) {
        println!("{}", input)
    }
}

fn main() {
    use crate::print_things::prints_one_thing;

    prints_one_thing(6);
    prints_one_thing("Trying to print a string...".to_string());
}
```

چیزی که پرینت میکنه:

```text
6
Trying to print a string...
```

کلمه‌کلیدی `pub` برای `Struct` ها `Enum` ها `Trait` ها هم میتونه استفاده بشه:
- کلمه‌کلیدی `pub` برای `Struct`: باعث میشه که ساختار `Public` بشه، اما ایتم های ساختار `Public` نمیشند، برای اینکه اونها هم `Public` بشند باید کلمه‌کلیدی `pub` رو برای اونها هم بنویسیم
- کلمه‌کلیدی `pub` برای `Enum` یا `Trait`: همه‌چی `Public` میشه، این منطقی هست به این دلیل که `Trait` ها یک رفتار رو به یک نوع میدند پس باید بتونیم از اون رفتار استفاده کنیم و `Enum` ها هم درباره‌ی انتخاب بین چندین حالت هستند، پس باید بتونیم به حالت ها دسترسی داشته بشیم
- کلمه‌کلیدی `pub` برای یک `Module`: اعضای `Public` اون مازول قابل دسترسی میشند اما اگه یک ماژول درون یک ماژول دیگه باشه، `Public`نمیشه و برای اون هم باید از `pub` استفاده کرد

خب بزارید داخل `print_things` یک ساختار به نام `Billy` بسازیم. این ساختار تقریبا `Public` میشه، اما نه کاملا. برای اینکه خود ساختار رو `Public` کنیم باید قبلش از `pub‍` استفاده کنیم. درون ساختار ما `name` و `times_to_print` رو داریم. فیلد `name`، `Public` نمیشه، به این دلیل که ما میخوایم فقط بشه ساختار رو با اسم `Billy` ساخت که این کار در `new` انجام میشه. اما باید بتونیم که تعداد بار هایی که باید پرینت بشه رو تنظیم کنیم، پس `times_to_print` باید `Public` باشه:

```rust
mod print_things {
    use std::fmt::{Display, Debug};

    #[derive(Debug)]
    pub struct Billy { // Billy is public
        name: String, // but name is private.
        pub times_to_print: u32,
    }

    impl Billy {
        pub fn new(times_to_print: u32) -> Self { // That means the user needs to use new to create a Billy. The user can only change the number of times_to_print
            Self {
                name: "Billy".to_string(), // We choose the name - the user can't
                times_to_print,
            }
        }

        pub fn print_billy(&self) { // This function prints a Billy
            for _ in 0..self.times_to_print {
                println!("{:?}", self.name);
            }
        }
    }

    pub fn prints_one_thing<T: Display>(input: T) {
        println!("{}", input)
    }
}

fn main() {
    use crate::print_things::*; // Now we use *. This imports everything from print_things

    let my_billy = Billy::new(3);
    my_billy.print_billy();
}
```

چیزی که پرینت میکنه:

```text
"Billy"
"Billy"
"Billy"
```

در ضمن، از `*` هم استفاده کردیم که بهش در اینجا بهش میگیم `Glob Operator`. `Glob` به معنای `Global` هست، پس یعنی همه‌چی.

درون یک ماژول ما میتونیم ماژول های دیگه‌ای رو هم بسازیم. به ماژولی که درون یک ماژول دیگه هست میگیم `Child Module`. یک `Child Module` همیشه میتونه از چیز هایی که در ماژول که خودش درش ساخته شده استفاده کنه.

برای مثال در کد زیر ما ماژول `city` رو درون `province` ساختیم که خود `province` در ماژول `country` هست:

```rust
mod country { // The main mod doesn't need pub
    fn print_country(country: &str) { // Note: this function isn't public
        println!("We are in the country of {}", country);
    }
    pub mod province { // Make this mod public

        fn print_province(province: &str) { // Note: this function isn't public
            println!("in the province of {}", province);
        }

        pub mod city { // Make this mod public
            pub fn print_city(country: &str, province: &str, city: &str) {  // This function is public though
                crate::country::print_country(country);
                crate::country::province::print_province(province);
                println!("in the city of {}", city);
            }
        }
    }
}

fn main() {
    crate::country::province::city::print_city("Canada", "New Brunswick", "Moncton");
}
```

بخش جالبش اینجاست که `print_city` میشه به `print_province` و `print_country` دسترسی داشته باشه. این به دلیل این هست که `city` درون ماژول های دیگه هست. به `pub` هم جلوی `print_province` نیازی نداریم که بتونیم ازش استفاده کنیم.

خب احتمالا متوجه شدید که `` خیلی طولانی هست. خب وقتی که درون یک ماژول هستیم میتونیم از `super` برای دسترسی به ماژول بالایی استفاده کنیم.

در مثال، ما فقط یک بار از فانکشن استفاده کردیم اگه نیاز داشتیم چندین بار ازش استفاده کنیم ایده‌ی خوبی بود که اعضای اون ماژول رو `Import` کنیم، چون هم راحت‌تر میتونیم کد بنویسیم و هم کد راحت‌تر خونده میشه، پس ازش استفاده میکنیم چون کد راحت‌تر خونده میشه:

```rust
mod country {
    fn print_country(country: &str) {
        println!("We are in the country of {}", country);
    }
    pub mod province {
        fn print_province(province: &str) {
            println!("in the province of {}", province);
        }

        pub mod city {
            use super::super::*; // use everything in "above above": that means mod country
            use super::*;        // use everything in "above": that means mod province

            pub fn print_city(country: &str, province: &str, city: &str) {
                print_country(country);
                print_province(province);
                println!("in the city of {}", city);
            }
        }
    }
}

fn main() {
    use crate::country::province::city::print_city; // bring in the function

    print_city("Canada", "New Brunswick", "Moncton");
    print_city("Korea", "Gyeonggi-do", "Gwangju"); // Now it's less work to use it again
}
```

## Testing

تست کردن مبحث خوبی هست که در مورد `Module` ها هم یاد بگیریم. تست کردن کد در راست خیلی ساده هست.

راحت ترین روش برای شروع کردن تست اضافه کردن `#[test]` بالای یک فانکشن هست:

```rust
#[test]
fn two_is_two() {
    assert_eq!(2, 2);
}
```

اما اگه بخوایم کد بالا رو در `Playground` اجرا کنیم، خطای: ```error[E0601]: `main` function not found in crate `playground``` رو میگیریم. مشکل اینحاست که `Playground` فکر میکنه یک برنامه اجرایی رو میخوایم اجرا کنیم، و خب `()main` رو درش پیدا نمیکنه. برای اینکه تست ها رو در `Playground` اجرا کنیم، باید روی `...` کلیک کنیم و گزینه‌ی `Test` رو انتخاب کنیم. حالا میتونم این تست رو اجرا کنیم.

اما اگر `Rust` رو نصب داریم، میتونیم به راحتی از `cargo test` برای انجام اینکار استفاده کنیم.

خروجی تست:

```text
running 1 test
test two_is_two ... ok

test result: ok. 1 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out
```

بزارید `assert_eq!(2, 2)` رو به `assert_eq!(2, 3)` تغییر بدیم و ببینیم که چه اتفاقی میوفته:

```text
running 1 test
test two_is_two ... FAILED

failures:

---- two_is_two stdout ----
thread 'two_is_two' panicked at 'assertion failed: `(left == right)`
  left: `2`,
 right: `3`', src/lib.rs:3:5
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace


failures:
    two_is_two

test result: FAILED. 0 passed; 1 failed; 0 ignored; 0 measured; 0 filtered out
```

وقتی که تست ناموفق میشه اطلاعات بیشتری دریافت میکنیم.

ماکروی `assert_eq!` تست میکنه که دو مقداری که بهش میدیم برابر باشند.

استفاده از `` یک روش رایج برای تست دو مقدار هست، اگه مقادیر با هم برابر نباشند، برنامه `Panic` میکنه که این باعث میشه تست ناموفق بشه.

همچنین میبینیم که مقادیر رو هم چاپ کرد که `left = 2` و `right = 3`. پس `left == right` ناموفق بود.

خب توی `Panic`‌ای که گرفتیم در مورد `RUST_BACKTRACE=1` یه صحبتی شده، این چیه؟

خب اگه مقدار متغییر سیستم `RUST_BACKTRACE` برابر `1` بشه ما در هنگام خطا ها اطلاعات بیشتری میگیریم.

در `Playground` برای فعال کردن این قابلیت باید روی `...` کلیک کنیم بعد روی `STABLE` کلیک کنیم و در اخر گزینه‌ی `Backtrace` رو `Enable` کنیم. همونطور که گفتم اگه اینکار رو کنیم اطلاعات بسیار بیشتری میگیریم:

```text
running 1 test
test two_is_two ... FAILED

failures:

---- two_is_two stdout ----
thread 'two_is_two' panicked at 'assertion failed: 2 == 3', src/lib.rs:3:5
stack backtrace:
   0: backtrace::backtrace::libunwind::trace
             at /cargo/registry/src/github.com-1ecc6299db9ec823/backtrace-0.3.46/src/backtrace/libunwind.rs:86
   1: backtrace::backtrace::trace_unsynchronized
             at /cargo/registry/src/github.com-1ecc6299db9ec823/backtrace-0.3.46/src/backtrace/mod.rs:66
   2: std::sys_common::backtrace::_print_fmt
             at src/libstd/sys_common/backtrace.rs:78
   3: <std::sys_common::backtrace::_print::DisplayBacktrace as core::fmt::Display>::fmt
             at src/libstd/sys_common/backtrace.rs:59
   4: core::fmt::write
             at src/libcore/fmt/mod.rs:1076
   5: std::io::Write::write_fmt
             at /rustc/c367798cfd3817ca6ae908ce675d1d99242af148/src/libstd/io/mod.rs:1537
   6: std::io::impls::<impl std::io::Write for alloc::boxed::Box<W>>::write_fmt
             at src/libstd/io/impls.rs:176
   7: std::sys_common::backtrace::_print
             at src/libstd/sys_common/backtrace.rs:62
   8: std::sys_common::backtrace::print
             at src/libstd/sys_common/backtrace.rs:49
   9: std::panicking::default_hook::{{closure}}
             at src/libstd/panicking.rs:198
  10: std::panicking::default_hook
             at src/libstd/panicking.rs:215
  11: std::panicking::rust_panic_with_hook
             at src/libstd/panicking.rs:486
  12: std::panicking::begin_panic
             at /rustc/c367798cfd3817ca6ae908ce675d1d99242af148/src/libstd/panicking.rs:410
  13: playground::two_is_two
             at src/lib.rs:3
  14: playground::two_is_two::{{closure}}
             at src/lib.rs:2
  15: core::ops::function::FnOnce::call_once
             at /rustc/c367798cfd3817ca6ae908ce675d1d99242af148/src/libcore/ops/function.rs:232
  16: <alloc::boxed::Box<F> as core::ops::function::FnOnce<A>>::call_once
             at /rustc/c367798cfd3817ca6ae908ce675d1d99242af148/src/liballoc/boxed.rs:1076
  17: <std::panic::AssertUnwindSafe<F> as core::ops::function::FnOnce<()>>::call_once
             at /rustc/c367798cfd3817ca6ae908ce675d1d99242af148/src/libstd/panic.rs:318
  18: std::panicking::try::do_call
             at /rustc/c367798cfd3817ca6ae908ce675d1d99242af148/src/libstd/panicking.rs:297
  19: std::panicking::try
             at /rustc/c367798cfd3817ca6ae908ce675d1d99242af148/src/libstd/panicking.rs:274
  20: std::panic::catch_unwind
             at /rustc/c367798cfd3817ca6ae908ce675d1d99242af148/src/libstd/panic.rs:394
  21: test::run_test_in_process
             at src/libtest/lib.rs:541
  22: test::run_test::run_test_inner::{{closure}}
             at src/libtest/lib.rs:450
note: Some details are omitted, run with `RUST_BACKTRACE=full` for a verbose backtrace.


failures:
    two_is_two

test result: FAILED. 0 passed; 1 failed; 0 ignored; 0 measured; 0 filtered out
```

معمولا لازم نیست که از `BACKTRACE` استفاده کنیم مگه زمانی که واقعا نتونیم بفهمیم خطایی که کامپایلر داده چی هست. خوشبختابه نیازی نیست که همش رو بخونیم، اگه یه نگاهی بهش بندازیم در نهایت میبینیم که در خط `13` به `Playground` اشاره کرده، که این یعنی تازه داره در مورد کدی که ما نوشتیم صحبت میکنه. بقیه‌اش در مورد کار هایی هست که کامپایلر داشت انجام میداد. اما خط در خط `13` و `14` این خطا میتونیم ببینیم که میگه در فایل `two_is_two.rs` در خط های `2` و `3` یک مشکلی پیش اومده. در زیر اون بخشی که این اطلاعات رو میده رو میبینیم:

```text
  13: playground::two_is_two
             at src/lib.rs:3
  14: playground::two_is_two::{{closure}}
             at src/lib.rs:2
```

البته `Rust` پیام های `Backtrace` رو از اوایل سال `2021` سعی کرده که با معنا‌تر کنه و اطلاعات مفید رو نشون بده. یعنی در حال حاضر چنین چیزی رو میده:

```text
failures:

---- two_is_two stdout ----
thread 'two_is_two' panicked at 'assertion failed: `(left == right)`
  left: `2`,
 right: `3`', src/lib.rs:3:5
stack backtrace:
   0: rust_begin_unwind
             at /rustc/cb75ad5db02783e8b0222fee363c5f63f7e2cf5b/library/std/src/panicking.rs:493:5
   1: core::panicking::panic_fmt
             at /rustc/cb75ad5db02783e8b0222fee363c5f63f7e2cf5b/library/core/src/panicking.rs:92:14
   2: playground::two_is_two
             at ./src/lib.rs:3:5
   3: playground::two_is_two::{{closure}}
             at ./src/lib.rs:2:1
   4: core::ops::function::FnOnce::call_once
             at /rustc/cb75ad5db02783e8b0222fee363c5f63f7e2cf5b/library/core/src/ops/function.rs:227:5
   5: core::ops::function::FnOnce::call_once
             at /rustc/cb75ad5db02783e8b0222fee363c5f63f7e2cf5b/library/core/src/ops/function.rs:227:5
note: Some details are omitted, run with `RUST_BACKTRACE=full` for a verbose backtrace.


failures:
    two_is_two

test result: FAILED. 0 passed; 1 failed; 0 ignored; 0 measured; 0 filtered out; finished in 0.02s
```

خب حالا بیاید `Backtrace` رو غیرفعال کنیم و برگردیم سر تست کردن. ما چند فانکشن میسازیم و بعد تست‌شون میکنیم:

```rust
fn return_two() -> i8 {
    2
}
#[test]
fn it_returns_two() {
    assert_eq!(return_two(), 2);
}

fn return_six() -> i8 {
    4 + return_two()
}
#[test]
fn it_returns_six() {
    assert_eq!(return_six(), 6)
}
```

الان دو فانکشنی که قبلشون `#[test]` دارند رو اجرا میکنه که اونها هم دو فانکشن دیگه رو تست میکنند، خروجی تست:
```text
running 2 tests
test it_returns_two ... ok
test it_returns_six ... ok

test result: ok. 2 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out
```

خب زیاد سخت نبود.

معمولا ما کد های تست رو در یک `Module` جدا قرار میدیم. برای اینکار، از کلمه‌کلیدی `mod` استفاده میکنیم و `#[cfg(test)]` رو هم بالاش میزاریم. همچنین `#[test]` رو هم قبل هر تست میزاریم. این بخاطر این هست که وقتی که `Rust` رو نصب کنیم میتونیم تست های پیچیده‌تری هم انچام بدیم. برای مثال میتونیم یک تست، چند تست یا همه‌ی تست ها رو اجرا کنیم یا حتی اونها رو `Debug` کنیم. همچنین فراموش نمیکنیم که از `super::*;` استفاده کنیم، این باعث میشه که بتونیم به فانکشن ها و... هایی که بیرون ماژول `tests` هستند، دسترسی داشته باشیم.

کد چنین چیزی میشه:

```rust
fn return_two() -> i8 {
    2
}
fn return_six() -> i8 {
    4 + return_two()
}

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn it_returns_six() {
        assert_eq!(return_six(), 6)
    }
    #[test]
    fn it_returns_two() {
        assert_eq!(return_two(), 2);
    }
}
```

### Test-driven development

خب احتمال داره اصطلاح `Test-Driven Development` رو دیده باشید. این یک روش برای نوشتن برنامه هست، که بعضی ها به بقیه‌ی روش ها ترجیحش میدند. در روش `Test-Driven Development` ما اول تست های برنامه رو مینویسیم و بعد کد رو مینویسیم. خب وقتی این کار رو انجام میدیم برای هرکاری که برنامه باید انجام بده تست داریم. خب این هم یعنی احتمال اینکه باگی در نسخه‌ی رسمی پیدا بشه کم میشه، چون برای اگه جایی برنامه طبق خواسته‌ی ما پیش نره، تست `Failed` میشه و میفهمیم که برنامه درست کار نکرده. و خب اگه تستی ناموفق باشه کامپایلر هم کمک میکنه که چطوری درستش کنیم. بزارید یک برنامه با روش `TDD` بنویسیم.

بزارید تصور کنیم که میخوایم یک ماشین‌حساب بنویسیم. این برنامه میتونیم با کاراکتر `+` اعداد رو جمع کنه. با کاراکتر `-` اعداد رو از هم تفریق کنه. اگه کاربر `5 + 6` رو وارد کنه، برنامه باید نتیجه‌ی `11` رو برگردونه. یا اگه `5 + 6 - 7` رو وارد کنه، برنامه باید `4` رو به عنوان نتیجه نشون بده. خب پس ما شروع میکنیم تست رو بنویسیم. معمولا اسم فانکشن های تست طولانی هست، به این دلیل که خب ما باید بفهمیم درست چی رو تست کردیم.

خب ما یک فانکشن به نام `()math` درست میکنیم که قرار هست همه‌ی کار ها رو انجام بده. این فانکشن یک `i32` برمیگردونه. به این دلیل که برای کامپایل شدن برنامه، این فانکشن باید چیزی رو برگردونه ما فعلا فقط `6` رو برمیگردونیم. بعد سه تست فانکشن مینویسیم. البته که الان همشون `Fail` میشند، به این دلیل که ما هنوز `()math` رو کامل نکردیم. اما خب بزارید کد رو ببینیم:

```rust
fn math(input: &str) -> i32 {
    6
}

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn one_plus_one_is_two() {
        assert_eq!(math("1 + 1"), 2);
    }
    #[test]
    fn one_minus_two_is_minus_one() {
        assert_eq!(math("1 - 2"), -1);
    }
    #[test]
    fn one_minus_minus_one_is_two() {
        assert_eq!(math("1 - -1"), 2);
    }
}
```

چنین اطلاعاتی رو میده:

```text
running 3 tests
test tests::one_minus_minus_one_is_two ... FAILED
test tests::one_minus_two_is_minus_one ... FAILED
test tests::one_plus_one_is_two ... FAILED
```
و خب اطلاعاتی در مورد ``thread 'tests::one_plus_one_is_two' panicked at 'assertion failed: `(left == right)` `` هم میده که لازم نیست اینجا بنویسیم.

خب حالا بیاید فانشکن `()math` رو بنویسیم. ما به عنوان ورودی فقط اعداد، نماد های `+` و `-` و اسپیس رو قبول میکنیم. پس بزارید کاراکتر هایی که مورد قبول هستند رو درون یک متغییر `const` قرار بدیم. بعد هم ورودی چک میکنیم که فقط کاراکتر های مورد قبول درش باشند.

بعد یک فانکشن تست مینویسیم که اگه `Panic` کنه، تست `Succeed` میشه. ما با استفاده از `#[should_panic]` این کار رو انجام میدیم.

خب کد رو ببینیم:

```rust
const OKAY_CHARACTERS: &str = "1234567890+- "; // Don't forget the space at the end

fn math(input: &str) -> i32 {
    if !input.chars().all(|character| OKAY_CHARACTERS.contains(character)) {
        panic!("Please only input numbers, +-, or spaces");
    }
    6 // we still return a 6 for now
}

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn one_plus_one_is_two() {
        assert_eq!(math("1 + 1"), 2);
    }
    #[test]
    fn one_minus_two_is_minus_one() {
        assert_eq!(math("1 - 2"), -1);
    }
    #[test]
    fn one_minus_minus_one_is_two() {
        assert_eq!(math("1 - -1"), 2);
    }

    #[test]
    #[should_panic]  // Here is our new test - it should panic
    fn panics_when_characters_not_right() {
        math("7 + seven");
    }
}
```

الان اگه تست ها رو اجرا کنیم چنین خروجی‌ای میگیریم:

```text
running 4 tests
test tests::one_minus_two_is_minus_one ... FAILED
test tests::one_minus_minus_one_is_two ... FAILED
test tests::panics_when_characters_not_right ... ok
test tests::one_plus_one_is_two ... FAILED
```

خب یکی `Succeed` شد که اون هم `panics_when_characters_not_right()` هست. پس فانشکن `()math` فقط کاراکتر هایی که مشخص کردیم رو قبول میکنه.

قدم بعدی نوشتن جدی عملیات ماشین‌حساب هست، ما چنین کاری رو انجام میدیم:

- همه‌ی `Space` ها باید حذف بشند. که خب با `()filter.` اینکار رو انجام میدیم.

- ورودی باید به یک `Vec` تبدیل بشه. نماد های `+` و `-` عملوند(اعداد) ها رو مشخص میکنند و خب اینکه چه عملیاتی باید روی این عملوند ها انجام بشند رو هم مشخص میکنند. برای مثال اگه ورودی `11+1` باشه، چنین چیزی رخ میده: اول `1` رو میبینه و اون رو به یک `String` اضافه میکنه. بعد یک `1` دیگه میبینه و اون رو هم به `String` اضافه میکنه. بعد `+` رو میبینه که میفهمه عملوند تموم شده. پس `String` رو به `Vec` اضافه میکنه و بعد `String` رو خالی میکنه برای ذخیره کردن عملوند بعدی.

- برنامه باید تعداد `-` رو داشته باشه. اگه تعدادشون یک عدد ‍**فرد** باشه، باید عمل تفریق رو انجام بدیم. و اگه تعداد نماد های `-` **زوج** باشه باید عملیات جمع رو انجام بدیم. برای مثال `1--9` باید نتیجش `10` باشه و `8` نباشه.

- برنامه باید هرچیزی که بعد از اخرین عملوند هست رو پاک کنه. برای مثال `5+5+++++----` باید تبدیل به `5+5` بشه. خب ما با استفاده از `.trim_end_matches()` میتونیم این کار رو انجام بدیم.

(در ضمن، `.trim_end_matches()` و `.trim_start_matches()` قبلا اسم هاشون `` و `` بود. اما خب بعضی زبان ها مثل **فارسی** و **عبری** و... راست به چپ هستند. پس `right` و `left` اشتباه بودند. اما امکان داره در بعضی کد ها اون ها رو هم ببینید)




اول ما میخوایم که همه‌ی تست ها رو `Pass` کنیم. بعد از اینکه ما تست ها رو `Pass` کردیم. میتونیم کدمون رو `Refactor` کنیم. اصطلاح `Refactoring` به معنای بهتر کردن کد هست.

خب بزارید ببینیم تست ها `Pass` میشند:

```rust
const OKAY_CHARACTERS: &str = "1234567890+- ";

fn math(input: &str) -> i32 {
    if !input.chars().all(|character| OKAY_CHARACTERS.contains(character)) ||
       !input.chars().take(2).any(|character| character.is_numeric())
    {
        panic!("Please only input numbers, +-, or spaces.");
    }

    let input = input.trim_end_matches(|x| "+- ".contains(x)).chars().filter(|x| *x != ' ').collect::<String>(); // Remove + and - at the end, and all spaces
    let mut result_vec = vec![]; // Results go in here
    let mut push_string = String::new(); // This is the string we push in every time. We will keep reusing it in the loop.
    for character in input.chars() {
        match character {
            '+' => {
                if !push_string.is_empty() { // If the string is empty, we don't want to push "" into result_vec
                    result_vec.push(push_string.clone()); // But if it's not empty, it will be a number. Push it into the vec
                    push_string.clear(); // Then clear the string
                }
            },
            '-' => { // If we get a -,
                if push_string.contains('-') || push_string.is_empty() { // check to see if it's empty or has a -
                    push_string.push(character) // if so, then push it in
                } else { // otherwise, it will contain a number
                result_vec.push(push_string.clone()); // so push the number into result_vec, clear it and then push -
                push_string.clear();
                push_string.push(character);
                }
            },
            number => { // number here means "anything else that matches". We selected the name here
                if push_string.contains('-') { // We might have some - characters to push in first
                    result_vec.push(push_string.clone());
                    push_string.clear();
                    push_string.push(number);
                } else { // But if we don't, that means we can push the number in
                    push_string.push(number);
                }
            },
        }
    }
    result_vec.push(push_string); // Push one last time after the loop is over. Don't need to .clone() because we don't use it anymore

    let mut total = 0; // Now it's time to do math. Start with a total
    let mut adds = true; // true = add, false = subtract
    let mut math_iter = result_vec.into_iter();
    while let Some(entry) = math_iter.next() { // Iter through the items
        if entry.contains('-') { // If it has a - character, check if it's even or odd
            if entry.chars().count() % 2 == 1 {
                adds = match adds {
                    true => false,
                    false => true
                };
                continue; // Go to the next item
            } else {
                continue;
            }
        }
        if adds == true {
            total += entry.parse::<i32>().unwrap(); // If there is no '-', it must be a number. So we are safe to unwrap
        } else {
            total -= entry.parse::<i32>().unwrap();
            adds = true;  // After subtracting, reset adds to true.
        }
    }
    total // Finally, return the total
}
   /// We'll add a few more tests just to make sure

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn one_plus_one_is_two() {
        assert_eq!(math("1 + 1"), 2);
    }
    #[test]
    fn one_minus_two_is_minus_one() {
        assert_eq!(math("1 - 2"), -1);
    }
    #[test]
    fn one_minus_minus_one_is_two() {
        assert_eq!(math("1 - -1"), 2);
    }
    #[test]
    fn nine_plus_nine_minus_nine_minus_nine_is_zero() {
        assert_eq!(math("9+9-9-9"), 0); // This is a new test
    }
    #[test]
    fn eight_minus_nine_plus_nine_is_eight_even_with_characters_on_the_end() {
        assert_eq!(math("8  - 9     +9-----+++++"), 8); // This is a new test
    }
    #[test]
    #[should_panic]
    fn panics_when_characters_not_right() {
        math("7 + seven");
    }
}
```

الان همه‌ی تست ها `Pass` میشند:

```text
running 6 tests
test tests::one_minus_minus_one_is_two ... ok
test tests::nine_plus_nine_minus_nine_minus_nine_is_zero ... ok
test tests::one_minus_two_is_minus_one ... ok
test tests::eight_minus_nine_plus_nine_is_eight_even_with_characters_on_the_end ... ok
test tests::one_plus_one_is_two ... ok
test tests::panics_when_characters_not_right ... ok

test result: ok. 6 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out
```

میبینیم که فرایند `TDD` یک چیزی شبیه این هست:

- اول ما برای هر چیزی که میتونیم فکر کنیم تست مینویسیم

- بعد شروع به نوشتن کد میکنیم

- در حالی که کد مینویسیم ایده برای تست کردن چیز جدید میاد و اون رو هم مینویسیم


این کار باعث میشه احتمال اینکه کد باگ داشته باشه کاهش پیدا کنه.

البته این به معنای این نیست که تست نوشتن یعنی بهترین کد رو قراره بنویسیم. اما تست نوشتن خیلی کارایی داره بخصوص زمانی که کدمون رو تغییر میدیم. در اون زمان میتونیم تست رو اجرا کنیم که بفهمیم کدمون باز هم درست کار میکنه یا اینکه خیر، اگه درست کار نکرد خب باید کد رو درست کنیم.

خب الان میخوایم کد رو `Refactor` کنیم. اینکه از `‌Clippy` استفاده کنیم ایده‌ی خوبی هست. اگه `Rust` رو نصب کردیم میتونیم از دستور `cargo clippy` استفاده کنیم. در `Playground` هم میتونیم از طریق‍ `TOOLS` گزینه‌ی `Clippy` رو انتخاب کنیم.

خب `Clippy` کدمون رو یه نگاهی میندازه و میگه که چطوری میشه بهتر نوشتش.

خب `Clippy` دو نکته بهمون میگه:

```text
warning: this loop could be written as a `for` loop
  --> src/lib.rs:44:5
   |
44 |     while let Some(entry) = math_iter.next() { // Iter through the items
   |     ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ help: try: `for entry in math_iter`
   |
   = note: `#[warn(clippy::while_let_on_iterator)]` on by default
   = help: for further information visit https://rust-lang.github.io/rust-clippy/master/index.html#while_let_on_iterator

warning: equality checks against true are unnecessary
  --> src/lib.rs:53:12
   |
53 |         if adds == true {
   |            ^^^^^^^^^^^^ help: try simplifying it as shown: `adds`
   |
   = note: `#[warn(clippy::bool_comparison)]` on by default
   = help: for further information visit https://rust-lang.github.io/rust-clippy/master/index.html#bool_comparison
```
خب میبینم که داره درست میگه، استفاده از `for entry in math_iter` بهتر از `while let Some(entry) = math_iter.next()` هست، به این دلیل که ساده تر هست.


خب الان میریم به طور جدی کد رو `Refactor` کنیم. ما یک `Calculator` میسازیم. این ساختار همه‌ی متغییر ها  رو در خودش نگهداری میکنه. ما اسم `result_vec` رو هم به `results` تغییر میدیم، و همچنین `push_string` هم میشه `current_input`. و براش فقط یک متود به نام `new` میسازیم:

```rust
// 🚧
#[derive(Clone)]
struct Calculator {
    results: Vec<String>,
    current_input: String,
    total: i32,
    adds: bool,
}

impl Calculator {
    fn new() -> Self {
        Self {
            results: vec![],
            current_input: String::new(),
            total: 0,
            adds: true,
        }
    }
}
```

الان کدمون یکم طولانی شد اما خب راحت‌تر خونده میشه. برای مثال `if add` شده `if calcualtor.adds` که خب راحت‌تر خونده میشه:

```rust
#[derive(Clone)]
struct Calculator {
    results: Vec<String>,
    current_input: String,
    total: i32,
    adds: bool,
}

impl Calculator {
    fn new() -> Self {
        Self {
            results: vec![],
            current_input: String::new(),
            total: 0,
            adds: true,
        }
    }
}

const OKAY_CHARACTERS: &str = "1234567890+- ";

fn math(input: &str) -> i32 {
    if !input.chars().all(|character| OKAY_CHARACTERS.contains(character)) ||
       !input.chars().take(2).any(|character| character.is_numeric()) {
        panic!("Please only input numbers, +-, or spaces");
    }

    let input = input.trim_end_matches(|x| "+- ".contains(x)).chars().filter(|x| *x != ' ').collect::<String>();
    let mut calculator = Calculator::new();

    for character in input.chars() {
        match character {
            '+' => {
                if !calculator.current_input.is_empty() {
                    calculator.results.push(calculator.current_input.clone());
                    calculator.current_input.clear();
                }
            },
            '-' => {
                if calculator.current_input.contains('-') || calculator.current_input.is_empty() {
                    calculator.current_input.push(character)
                } else {
                calculator.results.push(calculator.current_input.clone());
                calculator.current_input.clear();
                calculator.current_input.push(character);
                }
            },
            number => {
                if calculator.current_input.contains('-') {
                    calculator.results.push(calculator.current_input.clone());
                    calculator.current_input.clear();
                    calculator.current_input.push(number);
                } else {
                    calculator.current_input.push(number);
                }
            },
        }
    }
    calculator.results.push(calculator.current_input);

    for entry in calculator.results {
        if entry.contains('-') {
            if entry.chars().count() % 2 == 1 {
                calculator.adds = match calculator.adds {
                    true => false,
                    false => true
                };
                continue;
            } else {
                continue;
            }
        }
        if calculator.adds {
            calculator.total += entry.parse::<i32>().unwrap();
        } else {
            calculator.total -= entry.parse::<i32>().unwrap();
            calculator.adds = true;
        }
    }
    calculator.total
}

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn one_plus_one_is_two() {
        assert_eq!(math("1 + 1"), 2);
    }
    #[test]
    fn one_minus_two_is_minus_one() {
        assert_eq!(math("1 - 2"), -1);
    }
    #[test]
    fn one_minus_minus_one_is_two() {
        assert_eq!(math("1 - -1"), 2);
    }
    #[test]
    fn nine_plus_nine_minus_nine_minus_nine_is_zero() {
        assert_eq!(math("9+9-9-9"), 0);
    }
    #[test]
    fn eight_minus_nine_plus_nine_is_eight_even_with_characters_on_the_end() {
        assert_eq!(math("8  - 9     +9-----+++++"), 8);
    }
    #[test]
    #[should_panic]
    fn panics_when_characters_not_right() {
        math("7 + seven");
    }
}
```

در نهایت ما دو متود جدید هم درست میکنیم. اولی `()clear.` هست که `current_input` رو خالی میکنه. دومی `push_char()` هست که ورودی رو به `current_input` اضافه میکنه.

```rust
#[derive(Clone)]
struct Calculator {
    results: Vec<String>,
    current_input: String,
    total: i32,
    adds: bool,
}

impl Calculator {
    fn new() -> Self {
        Self {
            results: vec![],
            current_input: String::new(),
            total: 0,
            adds: true,
        }
    }

    fn clear(&mut self) {
        self.current_input.clear();
    }

    fn push_char(&mut self, character: char) {
        self.current_input.push(character);
    }
}

const OKAY_CHARACTERS: &str = "1234567890+- ";

fn math(input: &str) -> i32 {
    if !input.chars().all(|character| OKAY_CHARACTERS.contains(character)) ||
       !input.chars().take(2).any(|character| character.is_numeric()) {
        panic!("Please only input numbers, +-, or spaces");
    }

    let input = input.trim_end_matches(|x| "+- ".contains(x)).chars().filter(|x| *x != ' ').collect::<String>();
    let mut calculator = Calculator::new();

    for character in input.chars() {
        match character {
            '+' => {
                if !calculator.current_input.is_empty() {
                    calculator.results.push(calculator.current_input.clone());
                    calculator.clear();
                }
            },
            '-' => {
                if calculator.current_input.contains('-') || calculator.current_input.is_empty() {
                    calculator.push_char(character)
                } else {
                calculator.results.push(calculator.current_input.clone());
                calculator.clear();
                calculator.push_char(character);
                }
            },
            number => {
                if calculator.current_input.contains('-') {
                    calculator.results.push(calculator.current_input.clone());
                    calculator.clear();
                    calculator.push_char(number);
                } else {
                    calculator.push_char(number);
                }
            },
        }
    }
    calculator.results.push(calculator.current_input);

    for entry in calculator.results {
        if entry.contains('-') {
            if entry.chars().count() % 2 == 1 {
                calculator.adds = match calculator.adds {
                    true => false,
                    false => true
                };
                continue;
            } else {
                continue;
            }
        }
        if calculator.adds {
            calculator.total += entry.parse::<i32>().unwrap();
        } else {
            calculator.total -= entry.parse::<i32>().unwrap();
            calculator.adds = true;
        }
    }
    calculator.total
}

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn one_plus_one_is_two() {
        assert_eq!(math("1 + 1"), 2);
    }
    #[test]
    fn one_minus_two_is_minus_one() {
        assert_eq!(math("1 - 2"), -1);
    }
    #[test]
    fn one_minus_minus_one_is_two() {
        assert_eq!(math("1 - -1"), 2);
    }
    #[test]
    fn nine_plus_nine_minus_nine_minus_nine_is_zero() {
        assert_eq!(math("9+9-9-9"), 0);
    }
    #[test]
    fn eight_minus_nine_plus_nine_is_eight_even_with_characters_on_the_end() {
        assert_eq!(math("8  - 9     +9-----+++++"), 8);
    }
    #[test]
    #[should_panic]
    fn panics_when_characters_not_right() {
        math("7 + seven");
    }
}
```

خب این احتمالا به اندازه‌ی کافی خوب هست.

## External crates

اصطلاح `External Crate` به معنای `crate`‌ای هست که کس دیگه نوشته.

برای این بخش تقریبا نیاز داریم که `Rust` رو نصب کنیم. اما همچنان میتونیم از `Playground` هم استفاده کنیم. در این بخش یاد میگیریم که `crate` های مهم چه چیز هایی هستند و چطوری باید ازشون استفاده کنیم، این نکته‌‌ی مهمی در راست هست، به این دلایل:
- استفاده از `crate` ها خیلی راحت هست
- خب `Standard Library`، `Rust` خیلی کوچیک هست

این به این معنا هست که به طور عادی ما از `crate` کار زیادی استفاده میکنیم حتی برای کار های پایه‌ای هم زیاد از `crate` ها استفاده میکنیم.

ایده این هست که بدلیل اینکه استفاده از `crate` ها اسون هست، پس ما میتونیم بهترین رو بین `crate` ها استفاده کنیم. شاید یکی `crate` بهتری نسبت به اینی که فعلا داریم استفاده میکنیم نوشت، پس ما خیلی راحت میتونیم از اون بهتر استفاده کنیم.

ما در این بخش فقط `crate` های مهم رو معرفی میکنیم، `crate` هایی که معمولا همه استفاده میکنند.

از `rand` شروع میکنیم.

### rand

به این نکته توجه کردید که تا حالا از اعداد تصادفی استفاده نکردیم؟ این به این دلیل هست که بدون استفاده از `External crate` نمیتونیم اینکارو انجام بدیم، چون در `Standard Library` چنین قابلیتی وجود نداره. اما `crate` های زیادی هستند که تقریبا جزو `Standard Library` حساب میشند، به این دلیل که همیشه داریم ازشون استفاده میکنیم. خب حالا چطوری میتونیم از `crate` استفاده کنیم؟ اگه `Rust` رو نصب کرده باشیم میتونیم در پوشه‌ی پروژه، فایل `Cargo.toml` رو تغییر بدیم. فایل `Cargo.toml` در ابتدا چیزی شبیه به این هست:

```text
[package]
name = "rust_book"
version = "0.1.0"
authors = ["David MacLeod"]
edition = "2018"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
```
خب الان ما برای اینکه از `crate`، `rand` استفاده کنیم، میریم در سایت `crates.io` دنبالش جستجو میکنیم. که خب به صفحه‌ی `https:://crates.io/crates/rand` میرسیم. در این صفحه میتونیم ببینیم که میگه اگه میخوایم از `rand` استفاده کنیم. باید `rand = 0.7.3` رو به فایل `Cargo.toml` اضافه کنیم. البته زیر `dependencies`، که خب در نهایت باید فایل `Cargo.toml` چنین چیزی بشه:

```text
[package]
name = "rust_book"
version = "0.1.0"
authors = ["David MacLeod"]
edition = "2018"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
rand = "0.7.3"
```

بعد `cargo` خودش بقیه کار ها رو انجام میده. بعد میتونیم با استفاده از `rand` هم کد بنویسیم. برای مثال میتونیم به [صفحه‌ی مستندات](https://docs.rs/rand/0.7.3/rand/) نگاهی بندازیم.

برای رفتن به صفحه‌ی مستندات یک `crate` میتونیم در سایت `crates.io` روی `docs` کلیک کنیم.

خب این در مورد `cargo` بود اما در `Playground` ما `100` تا `crate` محبوب رو میتونیم استفاده کنیم. پس لازم نیست جایی اونها رو معرفی کنیم. میتونیم تصور کنیم که توی `Playground` ما یک لیستی از `100` تا `crate` محبوب رو در `Cargo.toml` وارد کردیم:

```text
[dependencies]
rand = "0.7.3"
some_other_crate = "0.1.0"
another_nice_crate = "1.7"
```

این به این معنا هست که میتونیم از `rand` هم استفاده کنیم:

```rust
use rand; // This means the whole crate rand
          // On your computer you can't just write this;
          // you need to write in the Cargo.toml file first

fn main() {
    for _ in 0..5 {
        let random_u16 = rand::random::<u16>();
        print!("{} ", random_u16);
    }
}
```

برنامه بالا هربار یک `u16` متفاوت رو پرینت میکنه، برای مثال: `42266 52873 56528 46927 6867`

فانکشن های اصلی در `rand`، `random` و `thread_rng` هستند. `rng` به معنای `random number generator` هست. و اگه در حقیقت به `random` نگاهی بندازید میبینید که به سادگی فقط یک `Shortcut` برای `thread_rng().gen()` هست. پس این `thread_rng` هست که تقریبا همه‌ی کار ها رو انجام میده.


در زیر یک کدی رو میبینید که به صورت پنج عدد تصادفی بین `1` تا `10` رو پرینت میکنه. برای اینکار ما از `.gen_range()` استفاده کردیم:

```rust
use rand::{thread_rng, Rng}; // Or just use rand::*; if we are lazy

fn main() {
    let mut number_maker = thread_rng();
    for _ in 0..5 {
        print!("{} ", number_maker.gen_range(1, 11));
    }
}
```

چنین چیزی رو پرینت میکنه: `7 2 4 8 6`

با استفاده از اعداد تصادفی میتونیم کار های جالبی انجام بدیم، برای مثال ساخت شخصیت برای یک بازی. ما از `rand` و چندین چیز دیگر در ساخت این بازی استفاده میکنیم.

در این بازی هر شخصیت شش ویژگی داره، و ما از یک `d6` براشون استفاده میکنیم. یک `d6` یک مکعب هست که به طور تصادفی اعدادی بین `1` تا `6` رو هر باری که پرتابش میکنیم میده(منظورم وقتی هست که ازش استفاده میکنیم).

اما اگه شخصیت شانس نداشته باشه چیزی مثل `3` یا `4` میگیره که خب منصفانه نیست. اگه قدرت شخصیت `3` باشه خب نمیتونه چیزی رو حمل کنه. پس یک متود دیگه هم درست میکنیم که چهار بار `d6` رو پرتاب کنیم و کمترین عددی که داده رو حذف میکنیم. پس اگه ما `3, 3, 1, 6` رو بگیریم. ما از `3, 3, 6` استفاده میکنیم که نتیجش میشه `12`.

در کد زیر یک شخصیت رو میسازیم. ما از `Character` برای نگهداری ویژگی ها استفاده میکنیم. و `Display` رو هم براش پیاده‌سازی میکنیم:

```rust
use rand::{thread_rng, Rng}; // Or just use rand::*; if we are lazy
use std::fmt; // Going to impl Display for our character


struct Character {
    strength: u8,
    dexterity: u8,    // This means "body quickness"
    constitution: u8, // This means "health"
    intelligence: u8,
    wisdom: u8,
    charisma: u8, // This means "popularity with people"
}

fn three_die_six() -> u8 { // A "die" is the thing you throw to get the number
    let mut generator = thread_rng(); // Create our random number generator
    let mut stat = 0; // This is the total
    for _ in 0..3 {
        stat += generator.gen_range(1..=6); // Add each time
    }
    stat // Return the total
}

fn four_die_six() -> u8 {
    let mut generator = thread_rng();
    let mut results = vec![]; // First put the numbers in a vec
    for _ in 0..4 {
        results.push(generator.gen_range(1..=6));
    }
    results.sort(); // Now a result like [4, 3, 2, 6] becomes [2, 3, 4, 6]
    results.remove(0); // Now it would be [3, 4, 6]
    results.iter().sum() // Return this result
}

enum Dice {
    Three,
    Four
}

impl Character {
    fn new(dice: Dice) -> Self { // true for three dice, false for four
        match dice {
            Dice::Three => Self {
                strength: three_die_six(),
                dexterity: three_die_six(),
                constitution: three_die_six(),
                intelligence: three_die_six(),
                wisdom: three_die_six(),
                charisma: three_die_six(),
            },
            Dice::Four => Self {
                strength: four_die_six(),
                dexterity: four_die_six(),
                constitution: four_die_six(),
                intelligence: four_die_six(),
                wisdom: four_die_six(),
                charisma: four_die_six(),
            },
        }
    }
    fn display(&self) { // We can do this because we implemented Display below
        println!("{}", self);
        println!();
    }
}

impl fmt::Display for Character { // Just follow the code for in https://doc.rust-lang.org/std/fmt/trait.Display.html and change it a bit
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        write!(
            f,
            "Your character has these stats:
strength: {}
dexterity: {}
constitution: {}
intelligence: {}
wisdom: {}
charisma: {}",
            self.strength,
            self.dexterity,
            self.constitution,
            self.intelligence,
            self.wisdom,
            self.charisma
        )
    }
}



fn main() {
    let weak_billy = Character::new(Dice::Three);
    let strong_billy = Character::new(Dice::Four);
    weak_billy.display();
    strong_billy.display();
}
```

چنین چیزی رو پرینت میکنه:

```rust
Your character has these stats:
strength: 9
dexterity: 15
constitution: 15
intelligence: 8
wisdom: 11
charisma: 9

Your character has these stats:
strength: 9
dexterity: 13
constitution: 14
intelligence: 16
wisdom: 16
charisma: 10
```

میبینیم که شخصیتی که با چهار بار تاس انداختن ساخته شده کمی بهتر از اون یکی هست.

### rayon

خب `rayon` یکی از `crate` های محبوب هست که اجازه میده کدی بنویسیم که سرعت بالایی داشته باشه. همچنین `Thread` میسازه اما بدون نیاز به نوشتن `thread::spawn`. در معنای دیگه، اون به این دلیل محبوب هست که اجازه میده به راحتی کدی بنویسیم که بهینه و پرسرعت هست.

متود های `()iter.`، `iter_mut()`، `into_iter()` در `rayon` به چنین شکلی نوشته میشند: `par_iter()`، `par_iter_mut()`، `par_into_iter()`.

پس فقط لازم هست که `par_` رو به اول این متود ها اضافه کنیم که سریع‌تر بشند.
در ضمن `par` به معنای `Parallel` هست که اون هم یعنی موازی.

بقیه‌ی متود های هم از همین الگو پیروی میکنند: `()chars` میشه‌ `.par_chars()` و همینطوری بگیر برو تا اخر...

کدی که در زیر میبینید باعث میشه که کامپیوتر کار زیادی انجام بده و فشاری زیادی روش میاد:

```rust
fn main() {
    let mut my_vec = vec![0; 200_000];
    my_vec.iter_mut().enumerate().for_each(|(index, number)| *number+=index+1);
    println!("{:?}", &my_vec[5000..5005]);
}
```
کد بالا یک `Vec` با `200000` ایتم میسازه. مقدار هر ایتم `0` هست. بعد از `()enumerate` استفاده میکنه که `index` رو بگیره و مقدار `0` رو به مقدار `index` تغییر میده.
اگه پرینتش کنیم یک خروجی بلندی میده، پس ما فقط `5000` تا `5004` رو پرینت میکنیم. این همچنان در `Rust` سریع هست. اما با استفاده از `rayon` میتونیم سریع‌ترش هم بکنیم:

```rust
use rayon::prelude::*; // Import rayon

fn main() {
    let mut my_vec = vec![0; 200_000];
    my_vec.par_iter_mut().enumerate().for_each(|(index, number)| *number+=index+1); // add par_ to iter_mut
    println!("{:?}", &my_vec[5000..5005]);
}
```
خب `rayon` متود های دیگه‌ای هم داره اما ساده ترینش `par_` بود که دیدیم.

### serde

خب برسیم به بعدی، `serde` یک `crate` هست که به ما اجازه میده از `Fromat` هایی مثل `JSON`، `YAML` و... استفاده کنیم. بهترین روش استفاده ازش این هست که یک `Struct` بسازیم که فیلد هایی که در اون فرمت هست رو در خودش داشته باشه و همچنین باید `Serialize` و `Deserialize` رو پیاده‌سازی کنیم که خوشبختانه میتونیم به طور خودکار با استفاده از `derive` اون هارو پیاده‌سازی کنیم:

```rust
#[derive(Serialize, Deserialize, Debug)]
struct Point {
    x: i32,
    y: i32,
}
```
میتونیم در این [سایت](https://serde.rs) بیشتر در موردش بخونیم.

### regex

خب [`regex`](https://crates.io/crates/regex) اجازه میده توی یک متن سرچ کنیم و همچنین کار های پیچیده‌ی دیگه‌ای رو هم میتونیم باهاش انجام بدیم. این `crate` به ما اجازه‌ی استفاده از [`Regular Expression`](https://en.wikipedia.org/wiki/Regular_expression) ها رو میده. `Regex` کلا یه مبحث جدا از زبان `Rust` هست که باید یادش گرفت.

در این [لینک](https://github.com/ziishaned/learn-regex) میتونیم `Regex` رو یاد بگیریم.

### chrono

خب [`chrono`](https://crates.io/crates/chrono) اصلی‌ترین `crate` برای کار با `time` هست. در `Standard Library` زبان `Rust` ما میتونیم با زمان کار کنیم اما اگه نیاز به قابلیت های بیشتری داشتیم میتونیم از `chrono` هم استفاده کنیم.

## A tour of the standard library

تا الان ما خیلی از `Rust` رو یاد گرفتیم، پس باید بتونیم اکثر چیز هایی که در `Standard Library` هستند رو بفهمیم. کدی که درش هست همچین ترسناک هم نیست. بزارید یک نگاهی بهش بندازیم. این این بخش به بخش های مهم `STD` یه سری میزنیم.

### Arrays

در گذشته (قبل از نسخه‌ی `1.53`)، نوع `Array`، `Iterator` رو پیاده‌سازی نکرده بود و برای اینکه ازش در یک `loop` استفاده میکردیم باید از `()iter.` استفاده میکردیم. همچنین معمولا از `&` استفاده میکردیم که یک `Slice` در `loop` بگیریم. پس کد زیر در گذشته کار نمیکرد:

```rust
fn main() {
    let my_cities = ["Beirut", "Tel Aviv", "Nicosia"];

    for city in my_cities {
        println!("{}", city);
    }
}
```

کامپایلر قبلا جنین خطایی میداد:

```text
error[E0277]: `[&str; 3]` is not an iterator
 --> src\main.rs:5:17
  |
  |                 ^^^^^^^^^ borrow the array with `&` or call `()iter.` on it to iterate over it
```

خوشبختانه الان چنین مشکلی نداریم پس کد زیر کار خواهد کرد:

```rust
fn main() {
    let my_cities = ["Beirut", "Tel Aviv", "Nicosia"];

    for city in my_cities {
        println!("{}", city);
    }
    for city in &my_cities {
        println!("{}", city);
    }
    for city in my_cities.iter() {
        println!("{}", city);
    }
}
```

خروجیش:

```text
Beirut
Tel Aviv
Nicosia
Beirut
Tel Aviv
Nicosia
Beirut
Tel Aviv
Nicosia
```
اگه میخوایم یک `Array` رو در چند متغییر `Destructure` کنیم باید از الگوی زیر استفاده کنیم:

```rust
fn main() {
    let my_cities = ["Beirut", "Tel Aviv", "Nicosia"];
    let [city1, city2, city3] = my_cities;
    println!("{}", city1);
}
```

خروجیش میشه: `Beirut`

### char

ما میتونیم از `.escape_unicode()` برای گرفتن کد `Unicode` یک کاراکتر(`char`) استفاده کنیم:

```rust
fn main() {
    let korean_word = "청춘예찬";
    for character in korean_word.chars() {
        print!("{} ", character.escape_unicode());
    }
}
```

خروجیش میشه: `\u{ccad} \u{cd98} \u{c608} \u{cc2c}`

ما میتونیم با استفاده از `From` یک `u8` رو به `char` تبدیل کنیم. اما برای `u32` ما باید از `TryFrom` استفاده کنیم، به این دلیل که اعدادی که نوع `u32` میتونه در خودش ذخیره کنه بیشتر از `Unicode` هست، پس امکان داره که معادل `Unicode` یک `u32` وجود نداشته باشه.

برای مثال کد زیر این مسئله رو نشون میده:

```rust
use std::convert::TryFrom; // You need to bring TryFrom in to use it
use rand::prelude::*;      // We will use random numbers too

fn main() {
    let some_character = char::from(99); // This one is easy - no need for TryFrom
    println!("{}", some_character);

    let mut random_generator = rand::thread_rng();
    // This will try 40,000 times to make a char from a u32.
    // The range is 0 (std::u32::MIN) to u32's highest number (std::u32::MAX). If it doesn't work, we will give it '-'.
    for _ in 0..40_000 {
        let bigger_character = char::try_from(random_generator.gen_range(std::u32::MIN..std::u32::MAX)).unwrap_or('-');
        print!("{}", bigger_character)
    }
}
```
خروجی‌ای که میده:

```text
------------------------------------------------------------------------𤒰---------------------
-----------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------
-------------------------------------------------------------춗--------------------------------
-----------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------
------------򇍜----------------------------------------------------
```

پس استفاده از `TryFrom` ایده‌ی خوبی هست.

همچنین از اواخر اگوست `2020` ما میتونیم `char` رو به `String` تبدیل کنیم.

### Integers

برای نوع های `Integer` متود های ریاضی زیادی وجود داره، به علاوه‌ی همه‌ی اونها متود های زیر هم وجود دارند:

خب متود های `.checked_add()`، `.checked_sub()`، `checked_mul()`، `.checked_div()` هم وجود دارند که سعی میکنند عملیات جمع، تفریق، ضرب و تقسیم رو رو انجام بدند، چیزی که برمیگردونند یک `Option` هست. پس میتونیم چک کنیم که ایا عملیاتی که میخواستیم انجام شده یا خیر. اینطوری اگه عملیات انجام نشه برنامه `Panic` نمیکنه:

```rust
fn main() {
    let some_number = 200_u8;
    let other_number = 200_u8;

    println!("{:?}", some_number.checked_add(other_number));
    println!("{:?}", some_number.checked_add(1));
}
```

خروجیش:

```text
None
Some(201)
```
اگه به مستندات این نوع ها رفتید و به اصطلاح `rhs` برخوردید، نترسید. اصطلاح `rhs` به معنای `right hand side` هست، که در حقیقت به معنای راست ترین عملوندی هست که در یک عبارت ریاضی مینویسیم. برای مثال در `5 + 7`، عدد `5` در سمت چپ هست و `7` در سمت راست(`rhs`) هست. اصطلاح `rhs` یک کلمه‌کلیدی نیست اما خب زیاد میبینیمش، و الان ما میدونیم این چی هست.

حالا که تا اینجا اومدیم بزارید در مورد `Trait`، `Add` هم یاد بگیریم. بعد از اینکه `Add` رو برای یک نوع پیاده‌سازی کردیم میتونیم از `+` روی اون نوع استفاده کنیم. ما باید `Add` رو به صورت دستی پیاده‌سازی کنیم، به این دلیل که میتونه کار های زیادی انجام بده، در زیر یک مثال از `STD` میبینیم:

```rust
use std::ops::Add; // first bring in Add

#[derive(Debug, Copy, Clone, PartialEq)] // PartialEq is probably the most important part here. You want to be able to compare numbers
struct Point {
    x: i32,
    y: i32,
}

impl Add for Point {
    type Output = Self; // Remember, this is called an "associated type": a "type that goes together".
                        // In this case it's just another Point

    fn add(self, other: Self) -> Self {
        Self {
            x: self.x + other.x,
            y: self.y + other.y,
        }
    }
}
```

خب الان بزارید `Add` رو برای یک `Struct`‌ای که خودمون ساختیم پیاده‌سازی کنیم:

```rust
use std::fmt;
use std::ops::Add;

#[derive(Clone)]
struct Country {
    name: String,
    population: u32,
    gdp: u32, // This is the size of the economy
}

impl Country {
    fn new(name: &str, population: u32, gdp: u32) -> Self {
        Self {
            name: name.to_string(),
            population,
            gdp,
        }
    }
}

impl Add for Country {
    type Output = Self;

    fn add(self, other: Self) -> Self {
        Self {
            name: format!("{} and {}", self.name, other.name), // We will add the names together,
            population: self.population + other.population, // and the population,
            gdp: self.gdp + other.gdp,   // and the GDP
        }
    }
}

impl fmt::Display for Country {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        write!(
            f,
            "In {} are {} people and a GDP of ${}", // Then we can print them all with just {}
            self.name, self.population, self.gdp
        )
    }
}

fn main() {
    let nauru = Country::new("Nauru", 10_670, 160_000_000);
    let vanuatu = Country::new("Vanuatu", 307_815, 820_000_000);
    let micronesia = Country::new("Micronesia", 104_468, 367_000_000);

    // We could have given Country a &str instead of a String for the name. But we would have to write lifetimes everywhere
    // and that would be too much for a small example. Better to just clone them when we call println!.
    println!("{}", nauru.clone());
    println!("{}", nauru.clone() + vanuatu.clone());
    println!("{}", nauru + vanuatu + micronesia);
}
```

خروجیش:

```text
In Nauru are 10670 people and a GDP of $160000000
In Nauru and Vanuatu are 318485 people and a GDP of $980000000
In Nauru and Vanuatu and Micronesia are 422953 people and a GDP of $1347000000
```

همچنین `Trait` های `Sub`، `Mul` و `Div` هم وجود دارند که به ترتیب برای پیاده‌سازی علمیات تفریق، ضرب و تقسیم هستند.

میتونیم لیست کامل `Trait` هایی که میتونیم ازشون برای پیاده‌سازی اپراتور ها برای نوع های خودمون استفاده کنیم رو در [اینجا](https://doc.rust-lang.org/std/ops/index.html#structs) ببینیم.

### Floats

نوع ها `f32` و `f64` میتونیم اعداد بزرگی رو در خودشون نگهداری کنند و همچنین متود های ریاضی زیادی هم دارند. برای مثال:
- متود `()floor.`: بزرگ‌ترین عدد صحیحی که کوچک‌تر یا مساوی خود `float` هست رو میده. برای مثال `3.5` میشه `3.0`
- متود `()ceil.`: کوچیک‌ترین عدد صحیحی که بزرگ‌تر یا مساوی با خود `float` هست رو میده. برای مثال `3.5` میشه `4.0`
- متود `()round.`: نزدیک‌ترین عدد صحیح به خود `float` رو میده. برای مثال `3.5` میشه `4.0`
- متود `()trunc.`: اعداد بعد از `.` رو حذف میکنه، یعنی عدد صحیح خود `float` رو میده که عدد بعد `.` برابر با `0` هست. برای مثال `3.5` میشه `3.0`

برای مثال در کد زیر میتونیم استفاده از این متود ها رو ببینیم:

```rust
fn four_operations(input: f64) {
    println!(
"For the number {}:
floor: {}
ceiling: {}
rounded: {}
truncated: {}\n",
        input,
        input.floor(),
        input.ceil(),
        input.round(),
        input.trunc()
    );
}

fn main() {
    four_operations(9.1);
    four_operations(100.7);
    four_operations(-1.1);
    four_operations(-19.9);
}
```

چیزی که پرینت میکنه:

```text
For the number 9.1:
floor: 9
ceiling: 10
rounded: 9 // because less than 9.5
truncated: 9

For the number 100.7:
floor: 100
ceiling: 101
rounded: 101 // because more than 100.5
truncated: 100

For the number -1.1:
floor: -2
ceiling: -1
rounded: -1
truncated: -1

For the number -19.9:
floor: -20
ceiling: -19
rounded: -20
truncated: -19
```

نوع های `f32` و `f64` متودی به نام `()max.` و `()min.` دارند که بزرگ‌ترین و کوچیک‌ترین عددی که ما میدیم رو میدند. برای نوع های دیگه میتونیم از `std::cmp::max` و `std::cmp::min` استفاده کنیم. در کد زیر نحوه‌ی استفاده از اونها همراه با `()fold.` رو میبینیم. همچنین میتونیم ببینیم که `()fold.` فقط برای جمع زدن اعداد استفاده نمیشه:

```rust
fn main() {
    let my_vec = vec![8.0_f64, 7.6, 9.4, 10.0, 22.0, 77.345, 10.22, 3.2, -7.77, -10.0];
    let maximum = my_vec.iter().fold(f64::MIN, |current_number, next_number| current_number.max(*next_number)); // Note: start with the lowest possible number for an f64.
    let minimum = my_vec.iter().fold(f64::MAX, |current_number, next_number| current_number.min(*next_number)); // And here start with the highest possible number
    println!("{}, {}", maximum, minimum);
}
```

### bool

در راست اگه بخوایم میتونیم یک `bool` رو به یک `Integer` تبدیل کنیم، به این دلیل که اینکار امن هست. در کد زیر میتونیم ببینیم که `true` به `1` تبدیل میشه و `false` به `0` تبدیل میشه:

```rust
fn main() {
    let true_false = (true, false);
    println!("{} {}", true_false.0 as u8, true_false.1 as i32);
}
```
چنین چیزی رو پرینت میکنه: `1 0`

همچنین میتونیم از `()into.` استفاده کنیم، البته باید نوع ها رو مشخص کنیم:

```rust
fn main() {
    let true_false: (i128, u16) = (true.into(), false.into());
    println!("{} {}", true_false.0, true_false.1);
}
```

این کد هم همون خروجی رو میده.

وقتی نسخه‌‌ی `1.50`، `Rust` اومد، یک متودی به نام `()then` بهش اضافه شد، که یک `bool` رو میتونه به `Option` تبدیل کنه. با استفاده از `()then` ما میتونیم `Closure` هم بنویسیم و زمانی که ایتم `true` بود `Closure` اجرا میشه. همچنین هر چیزی که از `Closure` برگردونده بشه، میره داخل `Option`، بزارید کد ببینیم:

```rust
fn main() {

    let (tru, fals) = (true.then(|| 8), false.then(|| 8));
    println!("{:?}, {:?}", tru, fals);
}
```

خروجیش میشه: `Some(8), None`

حالا یک مثال بزرگ‌تر ببینیم:

```rust
fn main() {
    let bool_vec = vec![true, false, true, false, false];
    
    let option_vec = bool_vec
        .iter()
        .map(|item| {
            item.then(|| { // Put this inside of map so we can pass it on
                println!("Got a {}!", item);
                "It's true, you know" // This goes inside Some if it's true
                                      // Otherwise it just passes on None
            })
        })
        .collect::<Vec<_>>();

    println!("Now we have: {:?}", option_vec);

    // That printed out the Nones too. Let's filter map them out in a new Vec.
    let filtered_vec = option_vec.into_iter().filter_map(|c| c).collect::<Vec<_>>();

    println!("And without the Nones: {:?}", filtered_vec);
}
```

چیزی که پرینت میکنه:

```text
Got a true!
Got a true!
Now we have: [Some("It\'s true, you know"), None, Some("It\'s true, you know"), None, None]
And without the Nones: ["It\'s true, you know", "It\'s true, you know"]
```

### Vec

نوع `Vec` متود های زیادی داره که ما هنوز بهش نگاهی ننداختیم. بزارید با `()sort.` شروع کنیم.

متود `()sort.` یک `&mut self` میگیره و یک `Vec` رو مرتب میکنه:

```rust
fn main() {
    let mut my_vec = vec![100, 90, 80, 0, 0, 0, 0, 0];
    my_vec.sort();
    println!("{:?}", my_vec);
}
```

چیزی که کد بالا پرینت میکنه: `[0, 0, 0, 0, 0, 80, 90, 100]`

اما یک روش دیگه برای مرتب کردن هم هست که اسمش `.sort_unstable()` هست. معمولا سریع‌تر هست، به این دلیل سریع هست که اهمیتی به ترتیب اعداد تکراری نمیده.

متود `()dedup.` به معنای `de-duplicate` هست. این متود ایتم های تکراری رو در یک `Vec` در صورتی که کنار هم باشند حذف میکنه.

برای مثال خروجی کد زیر `"sun", "moon"` نمیشه:

```rust
fn main() {
    let mut my_vec = vec!["sun", "sun", "moon", "moon", "sun", "moon", "moon"];
    my_vec.dedup();
    println!("{:?}", my_vec);
}
```
خروجیش میشه: `["sun", "moon", "sun", "moon"]`

متود `()dedup.` در بالا فقط `"sun"` که بعد `"sun"` هست رو حذف میکنهَِ، همچنین `"moon"`‌ای که بعد `"moon"` هست رو هم حذف میکنه، در نهایت اونیکی `"moon"` که بعد `"moon"` هست رو هم حذف میکنه. که خب خروجیش میشه: `["sun", "moon", "sun", "moon"]`

اگه میخوایم همه‌ی ایتم های تکراری رو حذف کنیم باید اول `()sort.` کنیم:

```rust
fn main() {
    let mut my_vec = vec!["sun", "sun", "moon", "moon", "sun", "moon", "moon"];
    my_vec.sort();
    my_vec.dedup();
    println!("{:?}", my_vec);
}
```

خروجیش:`["moon", "sun"]`.

### String

یادمون هست که یک `String` یک جورایی شبیه به `Vec` هست. پس اکثر متود های نوع `Vec` رو داره. برای مثال میتونیم با `String::with_capacity()` شروع کنیم. در کد زیر میبینیم که یک `String` بار های زیادی `Allocation` انجام میده:

```rust
fn main() {
    let mut push_string = String::new();
    let mut capacity_counter = 0; // capacity starts at 0
    for _ in 0..100_000 { // Do this 100,000 times
        if push_string.capacity() != capacity_counter { // First check if capacity is different now
            println!("{}", push_string.capacity()); // If it is, print it
            capacity_counter = push_string.capacity(); // then update the counter
        }
        push_string.push_str("I'm getting pushed into the string!"); // and push this in every time
    }
}
```

چیزی که پرینت میکنه:

```text
35
70
140
280
560
1120
2240
4480
8960
17920
35840
71680
143360
286720
573440
1146880
2293760
4587520
```

ما `18` بار `Reacllocation` کردیم. اما خب الان ما میدونیم که مقدار `Capacity` نهایی برابر با `4587520` میشه. پس ما میتونیم `String` رو از اول با همین `Capacity` بسازیم:

```rust
fn main() {
    let mut push_string = String::with_capacity(4587520); // We know the exact number. Some different big number could work too
    let mut capacity_counter = 0;
    for _ in 0..100_000 {
        if push_string.capacity() != capacity_counter {
            println!("{}", push_string.capacity());
            capacity_counter = push_string.capacity();
        }
        push_string.push_str("I'm getting pushed into the string!");
    }
}
```

خروجی کد بالا میشه: `4587520`
خب عالی شد دیگه الکی `Allocate` نکردیم.

البته که طول واقعی کمتر از `4587520` هست. این به دلیل این هست که در هر بار `Reallocation` دو برابر فضایی که قبلا اشغال شده بود اشغال میشه. ما میتونیم با استفاده از `.shrink_to_fit()` فضای اضافی‌ای که گرفته شده رو ازاد کنیم. `String`ما خیلی بزرگ هست و ما دیگه نمیخوایم چیزی بهش اضافه کنیم پس بهتره که فضایی که لازم نداره رو ازاد کنیم، اما فقط زمانی که نیاز هست باید این کار رو انجام بدیم، دلیلش رو در زیر میبینیم:

```rust
fn main() {
    let mut push_string = String::with_capacity(4587520);
    let mut capacity_counter = 0;
    for _ in 0..100_000 {
        if push_string.capacity() != capacity_counter {
            println!("{}", push_string.capacity());
            capacity_counter = push_string.capacity();
        }
        push_string.push_str("I'm getting pushed into the string!");
    }
    push_string.shrink_to_fit();
    println!("{}", push_string.capacity());
    push_string.push('a');
    println!("{}", push_string.capacity());
    push_string.shrink_to_fit();
    println!("{}", push_string.capacity());
}
```

چیزی که پرینت میکنه:

```text
4587520
3500000
7000000
3500001
```

خب ما اول `4587520` فضا اشغال کرده بودیم، و خب بهش نیاز نداشتیم، پس فضایی که نیاز نداشتیم رو ازاد کردیم و بعد مقدار فضای اشغال شده برابر با `3500000` شد. اما بعد ما `a` رو بهش اضافه کردیم، که خب فضایی برای این نداشتیم، پس نیاز شد که `Reallocation` انجام بشه و به همین دلیل فضایی که `String` اشغال میکرد حالا شد `7000000` یعنی دقیقا دو برابر قبلی. در نهایت ما از `.shring_to_fit()` استفاده کردیم که دوباره شد `3500001`.

متود `()pop.` دقیقا همینوطوری که برای `Vec` ها کار میکنه برای `String` ها هم کار میکنه:

```rust
fn main() {
    let mut my_string = String::from(".daer ot drah tib elttil a si gnirts sihT");
    loop {
        let pop_result = my_string.pop();
        match pop_result {
            Some(character) => print!("{}", character),
            None => break,
        }
    }
}
```

خروجی کد بالا میشه: `This string is a little bit hard to read.`

به این دلیل که از اخرین کاراکتر شروع کرد

متود `()retain.` در `String` شبیه متود `()filter.` هست در `Iterator`:

```rust
fn main() {
    let mut my_string = String::from("Age: 20 Height: 194 Weight: 80");
    my_string.retain(|character| character.is_alphabetic() || character == ' '); // Keep if a letter or a space
    dbg!(my_string); // Let's use dbg!() for fun this time instead of println!
}
```

خروجیش:

```text
[src\main.rs:4] my_string = "Age  Height  Weight "
```

### OsString and CString

ماژول `std::ffi` یک بخشی از `std` هست که اجازه میده ما در `Rust` زبان های برنامه‌نویسی دیگه یا سیستم‌عامل های مختلف کار کنیم. نوع هایی مثل `OsString` و `CString` داره که میتونیم حدس بزنیم چی هستند. `OsString`، `String`‌ای هست که سیستم‌عامل استفاده میکنه. `CString` هم `String`‌ای هست که زبان `C` ازش استفاده میکنه. هر کدومشون یک نوع `&str` هم دارند، برای مثال `OsStr` و `CStr`.

کلمه‌ی `ffi` به معنای `Foreign Function Interface` هست.

زمانی که با یک سیستم‌عاملی کار میکنیم که از `Unicode` پشتیبانی نمیکنه میتونیم از `OsString` استفاده کنیم. همه‌‌ی `String` ها `Rsut` به فرمت `Unicode` هستند. اما خب همه‌ی سیستم‌عامل ها از `Unicode` پشتیبانی نمیکنند.

در زیر میتونیم به طور ساده متوحه بشیم که `OsString` چی هست:
- یک `String` در `Unix` (`Linux`و...) میتونه بایت هایی کنار هم باشه که `0` ندارند. و گاهی اوقات میتونیم اونها رو به عنوان `UTF-8` بخونیم.
- یک `String` در `Windows` میتونه از مقدار های تصادفی `16` بیتی باشه که `0` بینشون نیست. گاهی اوقات میتونیم اونها رو به عنوان `UTF-8` بخونیم.
- در `Rust` همه‌ی `String` ها یک `UTF-8` معتبر هستند که میتونند `0` هم داشته باشند.


ما میتونیم همه‌ی کار ها رو با `OsString` هم انجام بدیم،‌ برای مثال `OsString::from("Write something here")`. همچنین میتونیم از متود `.into_string()` هم استفاده کنیم که تلاش میکنه مقدار رو به یک `String` معمولی تبدیل کنه. یک `Result` برمیگردونه، اما مقدار `Err` همون `OsString` هست:
```rust
// 🚧
pub fn into_string(self) -> Result<String, OsString>
```
پس اگه تبدیل ناموفق باشه همون مقدار رو میگیریم. ما نباید از `()unwrap.` استفاده کنیم چون در این صورت `Panic` میکنه اما میتونیم از `match` استفاده کنیم که اگه خطایی هم رخ داد بتونیم مقدار `OsString` رو دوباره بگیریم. بزارید با متود هایی که وجود ندارند تستش کنیم:

```rust
use std::ffi::OsString;

fn main() {
    // ⚠️
    let os_string = OsString::from("This string works for your OS too.");
    match os_string.into_string() {
        Ok(valid) => valid.thth(),           // Compiler: "What's .thth()??"
        Err(not_valid) => not_valid.occg(),  // Compiler: "What's .occg()??"
    }
}
```

کامپایلر چیز های خوبی میگه:

```text
error[E0599]: no method named `thth` found for struct `std::string::String` in the current scope
 --> src/main.rs:6:28
  |
6 |         Ok(valid) => valid.thth(),
  |                            ^^^^ method not found in `std::string::String`

error[E0599]: no method named `occg` found for struct `std::ffi::OsString` in the current scope
 --> src/main.rs:7:37
  |
7 |         Err(not_valid) => not_valid.occg(),
  |                                     ^^^^ method not found in `std::ffi::OsString`
```

میتونیم ببینیم که نوع متغییر `valid` یک `String` هست و نوع متغییر `not_valid` یک `OsString` هست.

### mem

ماژول `std::mem` متود های جالبی داره. ما چند تا ازشون رو مثل `.size_of()`، `.size_of_val()` و `()drop.` رو دیدیم:

```rust
use std::mem;

fn main() {
    println!("{}", mem::size_of::<i32>());
    let my_array = [8; 50];
    println!("{}", mem::size_of_val(&my_array));
    let mut some_string = String::from("You can drop a String because it's on the heap");
    mem::drop(some_string);
    // some_string.clear();   If we did this it would panic
}
```

چنین چیزی پرینت میکنه:

```text
4
200
```

همچنین متود های دیگه‌ای هم در ماژول `mem` وجود دارند:

متود `()swap`: با این متود میتونیم مقدار های دو متغییر رو جا‌به‌جا کنیم. باید از هر دو متغییر یک `Mutable Reference` داشته باشیم. این متود میتونه خیلی کاربردی باشه وقتی `Rust` به دلیل قوانین `Borrowing` اجازه‌ی این کار رو به ما نمیده. یا حتی وقتی میخوایم خیلی سریع دو رو تا مقدار رو جا‌به‌جا کنیم هم کاربردی هست:

برای مثال:

```rust
use std::{mem, fmt};

struct Ring { // Create a ring from Lord of the Rings
    owner: String,
    former_owner: String,
    seeker: String, // seeker means "person looking for it"
}

impl Ring {
    fn new(owner: &str, former_owner: &str, seeker: &str) -> Self {
        Self {
            owner: owner.to_string(),
            former_owner: former_owner.to_string(),
            seeker: seeker.to_string(),
        }
    }
}

impl fmt::Display for Ring { // Display to show who has it and who wants it
        fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
            write!(f, "{} has the ring, {} used to have it, and {} wants it", self.owner, self.former_owner, self.seeker)
        }
}

fn main() {
    let mut one_ring = Ring::new("Frodo", "Gollum", "Sauron");
    println!("{}", one_ring);
    mem::swap(&mut one_ring.owner, &mut one_ring.former_owner); // Gollum got the ring back for a second
    println!("{}", one_ring);
}
```

چیزی که پرینت میکنه:

```text
Frodo has the ring, Gollum used to have it, and Sauron wants it
Gollum has the ring, Frodo used to have it, and Sauron wants it
```

متود `()replace`: این متود مثل `()swap` هست و در حقیقت از اون هم استفاده میکنه، بزارید کدش رو ببینیم:

```rust
pub fn replace<T>(dest: &mut T, mut src: T) -> T {
    swap(dest, &mut src);
    src
}
```
این متود مقادیر رو جا‌به‌جا میکنه و مقدار `src` رو هم برمیگردونه، برای مثال:

```rust
use std::mem;

struct City {
    name: String,
}

impl City {
    fn change_name(&mut self, name: &str) {
        let old_name = mem::replace(&mut self.name, name.to_string());
        println!(
            "The city once called {} is now called {}.",
            old_name, self.name
        );
    }
}

fn main() {
    let mut capital_city = City {
        name: "Constantinople".to_string(),
    };
    capital_city.change_name("Istanbul");
}
```

خروجی‌ای که میده: `The city once called Constantinople is now called Istanbul.`

یک فانکشن دیگه هم به نام `()take.` وجود داره که شبیه به `()replace.` هست، یعنی مقدار که وجود داره رو برمیگردونه و به جاش مقدار `Default` اون نوع رو درش قرار میده.

این خود متود هست:

```rust
// 🚧
pub fn take<T>(dest: &mut T) -> T
where
    T: Default,
```

مثالی از این متود:
```rust
use std::mem;

fn main() {
    let mut number_vec = vec![8, 7, 0, 2, 49, 9999];
    let mut new_vec = vec![];

    number_vec.iter_mut().for_each(|number| {
        let taker = mem::take(number);
        new_vec.push(taker);
    });

    println!("{:?}\n{:?}", number_vec, new_vec);
}
```
همونطور که میبینیم همه‌ی مقادیر رو به `0` که مقدار `Default` نوع های `Integer` هست تغییر داد، و هر بار که این کار رو انجام داد، مقدار اصلی که توش بود رو هم برگردوند:

```text
[0, 0, 0, 0, 0, 0]
[8, 7, 0, 2, 49, 9999]
```

البته ما میتونیم برای نوع هایی که خودمون میسازیم هم مقدار `Default` قرار بدیم. برای اینکار باید `Trait`، `Default` رو پیاده‌سازی کنیم.

بزارید به مثالی نگاه کنیم. در این مثال ما `Bank` و `Robber` رو داریم. هر وقت کسی از بانک دزدی میکنه، پول رو از روی میز برمیداره. اما میز همیشه باید `50` تا پول داشته باشه. پس مقدار پیشفرض `DeskMoney` رو `50` میزاریم.

با اینکه در کل کد بی معنی هست اما میتونیم مفهوم `Default` رو ببینیم:

```rust
use std::mem;
use std::ops::{Deref, DerefMut}; // We will use this to get the power of u32

struct Bank {
    money_inside: u32,
    money_at_desk: DeskMoney, // This is our "smart pointer" type. It has its own default, but it will use u32
}

struct DeskMoney(u32);

impl Default for DeskMoney {
    fn default() -> Self {
        Self(50) // default is always 50, not 0
    }
}

impl Deref for DeskMoney { // With this we can access the u32 using *
    type Target = u32;

    fn deref(&self) -> &Self::Target {
        &self.0
    }
}

impl DerefMut for DeskMoney { // And with this we can add, subtract, etc.
    fn deref_mut(&mut self) -> &mut Self::Target {
        &mut self.0
    }
}

impl Bank {
    fn check_money(&self) {
        println!(
            "There is ${} in the back and ${} at the desk.\n",
            self.money_inside, *self.money_at_desk // Use * so we can just print the u32
        );
    }
}

struct Robber {
    money_in_pocket: u32,
}

impl Robber {
    fn check_money(&self) {
        println!("The robber has ${} right now.\n", self.money_in_pocket);
    }

    fn rob_bank(&mut self, bank: &mut Bank) {
        let new_money = mem::take(&mut bank.money_at_desk); // Here it takes the money, and leaves 50 because that is the default
        self.money_in_pocket += *new_money; // Use * because we can only add u32. DeskMoney can't add
        bank.money_inside -= *new_money;    // Same here
        println!("She robbed the bank. She now has ${}!\n", self.money_in_pocket);
    }
}

fn main() {
    let mut bank_of_klezkavania = Bank { // Set up our bank
        money_inside: 5000,
        money_at_desk: DeskMoney(50),
    };
    bank_of_klezkavania.check_money();

    let mut robber = Robber { // Set up our robber
        money_in_pocket: 50,
    };
    robber.check_money();

    robber.rob_bank(&mut bank_of_klezkavania); // Rob, then check money
    robber.check_money();
    bank_of_klezkavania.check_money();

    robber.rob_bank(&mut bank_of_klezkavania); // Do it again
    robber.check_money();
    bank_of_klezkavania.check_money();

}
```

چیزی که پرینت میکنه:

```text
There is $5000 in the back and $50 at the desk.

The robber has $50 right now.

She robbed the bank. She now has $100!

The robber has $100 right now.

There is $4950 in the back and $50 at the desk.

She robbed the bank. She now has $150!

The robber has $150 right now.

There is $4900 in the back and $50 at the desk.
```

You can see that there is always $50 at the desk.

### prelude

در راست، `Standard Library` هم `Prelude` داره، به همین دلیل هست که لازم نیست از `use std::vec::Vec` استفاده کنیم، و براحتی میتونیم از `Vec` استفاده کنیم.

همه‌ی `Prelude` ها رو میتونیم در این [لینک](https://doc.rust-lang.org/std/prelude/index.html#prelude-contents) ببینیم. بعضی هاشون رو تاحالا دیدیم:
- `std::ops::{Drop, Fn, FnMut, FnOnce}`
- `std::mem::drop`
- `std::boxed::Box`
- `std::clone::Clone`
- `std::cmp::{PartialEq, PartialOrd, Eq, Ord}`
- `std::convert::{AsRef, AsMut, Into, From}`
- `std::default::Default`
- `std::option::Option::{self, Some, None}`
- `std::result::Result::{self, Ok, Err}`
- `std::string::{String, ToString}`
- `std::vec::Vec`
- `std::marker::{Copy, Send, Sized, Sync, Unpin}`: ما `Unpin` رو ندیدیم، اکثر نوع ها از `Unpin` استفاده کردند، درست مثل ‌`Sized`. ‍`Pin` به معنای این هست که مقدار نمیتونه در حافظه جا‌به‌جا بشه. اما خب همونطور که گفتم اکثر نوع ها `Unpin` هستند، پس میتونند در حافظه جا‌به‌جا بشند. فانکشن هایی مثل `std::mem::replace` روی نوع های `Unpin` کار میکنند
- `std::borrow::ToOwned`: این رو قبلا در بخش `Cow` دیدیم، این میتونه یک مقدار `Borrowed` رو بگیره و اون `Owned` کنه. برای این کار از `.to_owned()` استفاده میکنه، میتونیم از `.to_owned()` روی یک `&str` هم استفاده کنیم که `String` ازش بگیریم. همینطور روی بقیه مقدار های `Borrowed` هم کار میکنه
- `std::iter::{Iterator, Extend, IntoIterator, DoubleEndedIterator, ExactSizeIterator}`: ما از `()rev.` روی `Iterator` استفاده کردیم، این در حقیقت یک `DoubleEndedIterator` میسازه. نوع `ExcatSizeIterator` هم چیزی شبیه به `0..10` هست، به این دلیل که سایز مشخصی داره. بقیه‌ی `Iterator` ها سایز مشخصی ندارند، یا اگه دارند قابل تغییر هستند

اگه نخوایم از `Prelude` ها استفاده کنیم میتونیم از `#![no_implicit_prelude]` استفاده کنیم:

```rust
// ⚠️
#![no_implicit_prelude]
fn main() {
    let my_vec = vec![8, 9, 10];
    let my_string = String::from("This won't work");
    println!("{:?}, {}", my_vec, my_string);
}
```

کامپایلر میگه داری از چیز هایی استفاده میکنی که نمیشناسمشون:

```text
error: cannot find macro `println` in this scope
 --> src/main.rs:5:5
  |
5 |     println!("{:?}, {}", my_vec, my_string);
  |     ^^^^^^^

error: cannot find macro `vec` in this scope
 --> src/main.rs:3:18
  |
3 |     let my_vec = vec![8, 9, 10];
  |                  ^^^

error[E0433]: failed to resolve: use of undeclared type or module `String`
 --> src/main.rs:4:21
  |
4 |     let my_string = String::from("This won't work");
  |                     ^^^^^^ use of undeclared type or module `String`

error: aborting due to 3 previous errors
```

پس با این مثال فهمیدیم که راست به صورت پیشفرض از `std` استفاده میکنه. بزارید خودمون به طور دستی به راست بفهمونیم که چه چیز هایی میخوایم:

```rust
#![no_implicit_prelude]

extern crate std; // Now you have to tell Rust that you want to use a crate called std
use std::vec; // We need the vec macro
use std::string::String; // and string
use std::convert::From; // and this to convert from a &str to the String
use std::println; // and this to print

fn main() {
    let my_vec = vec![8, 9, 10];
    let my_string = String::from("This won't work");
    println!("{:?}, {}", my_vec, my_string);
}
```
خب الان کار میکنه و خروجی ``[8, 9, 10], This won't work`` رو میده.

اگه به `STD` هم نیاز نداشتیم میتونیم از `#![no_std]` استفاده کنیم که با این کار راست به طور خودکار از `STD` استفاده نمیکنه. اما خب اکثر وقت ها ما به `STD` نیاز داریم.

خب ما چرا تا الان کلمه‌‌کلیدی `extern` رو ندیده بودیم؟ این به دلیل این هست که دیگه بهش نیازی نداریم، قبلا برای اینکه از `External Crate` ها استفاده کنیم باید ازش استفاده میکردیم، یعنی قبلا برای اینکه از `rand` استفاده کنیم باید چنین چیزی مینوشتیم:

```rust
extern crate rand;
```

و بعدش از `use` برای معرفی ماژول هاو... استفاده میکردیم. اما الان دیگه کامپایلر نیازی به مشخص کردن اینها نداره.

ما فقط `use` رو مینویسیم و خودش بقیه کار ها رو انجام میده. پس دیگه تقریبا هیچوقت نیازی نداریم که از `extern crate` استفاده کنیم. اما خب در کد های قدیمی میتونیم هنوز این کلمه‌کلیدی رو ببینیم.

### time

در ماژول `std::time` میتونیم فانکشن هایی برای کار با زمان پیدا کنیم. همچنین اگه به فانکشن های بیشتری نیاز داشتیم میتونیم از `crate` هایی مثل `chrono` استفاده کنیم.

با استفاده از `Instant::now()` میتونیم زمان سیستم رو بگیریم:

```rust
use std::time::Instant;

fn main() {
    let time = Instant::now();
    println!("{:?}", time);
}
```
اگه این برنامه رو اجرا کنیم چیزی شبیه به `` میگیریم.

این به ما ثانیه و میکروثانیه رو میده که خب کاربردی نیست. این زمانی که میخوایم دو زمان رو با هم مقایسه کنیم کاربرد داره.

اگه به صفحه‌ی مستندات این نوع بریم میتونیم در قسمت چپ ببینیم که `Sub<Instant>` رو پیاده‌سازی کرده. یعنی اینکه ما میتونیم از `-` روی این نوع استفاده کنیم، اگه کد رو بخوایم ببینیم، چنین چیزی رو بهمون نشون میده:

```rust
impl Sub<Instant> for Instant {
    type Output = Duration;

    fn sub(self, other: Instant) -> Duration {
        self.duration_since(other)
    }
}
```

پس یک `Instant` میگیره و از `.duration_since()` استفاده میکنه و یک `Duration` به ما میده.

در کد زیر ما اول دو بار از `Instant::now()` استفاده میکنیم که زمان رو بگیریم، بعد برنامه رو مشفول یه کاری میکنیم. در نهایت دوباره زمان رو میگیریم و فواصل بین این زمان ها رو پرینت میکنیم:

```rust
use std::time::Instant;

fn main() {
    let time1 = Instant::now();
    let time2 = Instant::now(); // These two are right next to each other

    let mut new_string = String::new();
    loop {
        new_string.push('წ'); // Make Rust push this Georgian letter onto the String
        if new_string.len() > 100_000 { //  until it is 100,000 bytes long
            break;
        }
    }
    let time3 = Instant::now();
    println!("{:?}", time2 - time1);
    println!("{:?}", time3 - time1);
}
```

خروجیش:

```text
1.025µs
683.378µs
```

خب ما میتونیم `Instant` رو با استفاده از `format!` به `String` تبدیل کنیم:

```rust
use std::time::Instant;

fn main() {
    let time1 = format!("{:?}", Instant::now());
    println!("{}", time1);
}
```
چیزی شبیه به `` پرینت میکنه.

اگه از `()iter.` و `()rev.` و `()skip.` استفاده کنیم میتونیم یک عدد تقریبا تصادفی بدست بیاریم. البته باید یادمون باشه که هیچوقت برای ساخت عدد تصادفی از این روش استفاده نکنیم.

```rust
use std::time::Instant;

fn bad_random_number(digits: usize) {
    if digits > 9 {
        panic!("Random number can only be up to 9 digits");
    }
    let now = Instant::now();
    let output = format!("{:?}", now);

    output
        .chars()
        .rev()
        .skip(2)
        .take(digits)
        .for_each(|character| print!("{}", character));
    println!();
}

fn main() {
    bad_random_number(1);
    bad_random_number(1);
    bad_random_number(3);
    bad_random_number(3);
}
```

چیزی که پرینت میکنه:

```text
6
4
967
180
```

ما اسم فانکشن رو `bad_random_number` گذاشتیم به این دلیل که ساخت عدد تصادفی با این روش مشکلاتی داره. و در عین حال راست `crate` های خوبی برای ساخت عدد تصادفی مثل `rand` و `fastrand` داره.

وقتی داریم با `Thread` ها کار میکنیم میتونیم از `std::thread::sleep` استفاده کنیم که اون `Thread` برای مدتی متوقف بشه.

این رو باید یادمون باشه که برنامه اصلی هم خودش یک `Thread` هست. پس برای تست این فانکشن لازم نیست یک `Thread` درست کنیم.

فانکشن `sleep` به یک `Duration` نیاز داره که بدونه چه مدت زمانی باید `Thread` رو متوقف کنه. میتونیم از `Duration::from_millis()` یا `Duration::from_secs` برای ساخت یک `Duration` استفاده کنیم:

```rust
use std::time::Duration;
use std::thread::sleep;

fn main() {
    let three_seconds = Duration::from_secs(3);
    println!("I must sleep now.");
    sleep(three_seconds);
    println!("Did I miss anything?");
}
```

خروجیش:

```text
I must sleep now.
Did I miss anything?
```

اگه کد بالا رو اجرا کنیم برنامه برای `3` ثانیه متوقف میشه.

### Other macros
بزارید یکم ماکروی باحال ببینیم.


ماکروی `unreachable!()`:

این ماکرو مثل ماکروی `todo!()` هست، با این تفاوت که زمانی ازش استفاده میکنیم که هیچوقت قرار نیست کد رو بنویسیم.


برای مثال: برنامه که هر وقت یه مکان رو انتخاب کردیم یه چیزی رو پرینت کنه، همه‌ی مکان ها خوب هستند به جز `Chernobyl`. برنامه اجازه نمیده که `Chernobyl` انتخاب بشه، به این دلیل که فعلا مکان خوبی برای زندگی نیست. اما `Enum` خیلی قبلا درست شده و اصلا کس دیگه‌ای درستش کرده و نمیتونیم تغییرش بدیم. پس میتونیم در `match` از ماکروی `unreachable!()` استفاده کنیم:

```rust
enum UkrainePlaces {
    Kiev,
    Kharkiv,
    Chernobyl, // Pretend we can't change the enum - Chernobyl will always be here
    Odesa,
    Dnipro,
}

fn choose_city(place: &UkrainePlaces) {
    use UkrainePlaces::*;
    match place {
        Kiev => println!("You will live in Kiev"),
        Kharkiv => println!("You will live in Kharkiv"),
        Chernobyl => unreachable!(),
        Odesa => println!("You will live in Odesa"),
        Dnipro => println!("You will live in Dnipro"),
    }
}

fn main() {
    let user_input = UkrainePlaces::Kiev; // Pretend the user input is made from some other function. The user can't choose Chernobyl, no matter what
    choose_city(&user_input);
}
```

خروجیش: `You will live in Kiev`

البته اگه برنامه به `unreachable!()` برسه، `Panic` میکنه. پس واقعا نباید تحت هیچ شرایطی به اونجای کد برسیم.

همچنین اگه کامپایلر بفهمه که یه کدی هیچوقت اجرا نمیشه یه اخطاری بهمون میده، برای مثال:

```rust
fn main() {
    let true_or_false = true;

    match true_or_false {
        true => println!("It's true"),
        false => println!("It's false"),
        true => println!("It's true"), // Whoops, we wrote true again
    }
}
```

اخطاری که میده:

```text
warning: unreachable pattern
 --> src/main.rs:7:9
  |
7 |         true => println!("It's true"),
  |         ^^^^
  |
```


ماکرو های: `column!`, `line!`, `file!`, `module_path!`:

این ماکرو ها شبیه به `dbg!()` هستند به این دلیل که اطلاعاتی در مورد کد بهمون میدن. اما چیزی به عنوان ورودی نمیگیرن:

- `column!()` شماره‌ی ستونی که نوشتیمش رو میده
- `file!()` اسم فایلی که توش نوشتیمش رو میده
- `line!()` شماره خطی که اون رو توش نوشتیم رو میده
- `module_path!()` ماژولی که درش هست رو میده

کد زیر نحوه‌ی استفاده از همشون رو نشون میده.

```rust
pub mod something {
    pub mod third_mod {
        pub fn print_a_country(input: &mut Vec<&str>) {
            println!(
                "The last country is {} inside the module {}",
                input.pop().unwrap(),
                module_path!()
            );
        }
    }
}

fn main() {
    use something::third_mod::*;
    let mut country_vec = vec!["Portugal", "Czechia", "Finland"];
    
    // do some stuff
    println!("Hello from file {}", file!());

    // do some stuff
    println!(
        "On line {} we got the country {}",
        line!(),
        country_vec.pop().unwrap()
    );

    // do some more stuff

    println!(
        "The next country is {} on line {} and column {}.",
        country_vec.pop().unwrap(),
        line!(),
        column!(),
    );

    // lots more code

    print_a_country(&mut country_vec);
}
```

خروجیش:

```text
Hello from file src/main.rs
On line 23 we got the country Finland
The next country is Czechia on line 32 and column 9.
The last country is Portugal inside the module rust_book::something::third_mod
```

ماکروی `cfg!`:

ما قبلا `Attribute` هایی مثل `#[cfg(test)]` و `#[cfg(windows)]` رو دیدیم. میتونیم ازشون استفاده کنیم که به کامپایلر بگیم در فلان شرایط چه کاری انجام بده.

وقتی که از برنامه رو در حالت تست اجرا کنیم کد هایی که زیر `` هستند اجرا میشند.

وقتی که برنامه در سیستم‌عامل ویندوز اجرا بشه، کد هایی که زیر `` نوشته شدند اجرا میشند.

همچنین این ماکروی به عنوان خروجی یک `bool` میده، پس میتونیم ازش در `if` استفاده کنیم:

```rust
fn main() {
    let helpful_message = if cfg!(target_os = "windows") { "backslash" } else { "slash" };

    println!(
        "...then in your hard drive, type the directory name followed by a {}. Then you...",
        helpful_message
    );
}
```
کد بالا با توجه به سیستم‌عامل میتونه متن های متفاوتی پرینت کنه. چون `Playgroun` در یک سیستم‌عامل `Linux` اجرا میشه، کد بالا چنین خروجی‌ای رو میده:

```text
...then in your hard drive, type the directory name followed by a slash. Then you...
```

ماکروی `cfg!()` یک جورایی برای تنظیم کردن کامپایلر هست، برای مثال کد زیر یک استفاده‌ی دیگه از `cfg!()` رو نشون میده:

```rust
#[cfg(test)] // cfg! will know to look for the word test
mod testing {
    use super::*;
    #[test]
    fn check_if_five() {
        assert_eq!(bring_number(true), 5); // This bring_number() function should return 5
    }
}

fn bring_number(should_run: bool) -> u32 { // This function takes a bool as to whether it should run
    if cfg!(test) && should_run { // if it should run and has the configuration test, return 5
        5
    } else if should_run { // if it's not a test but it should run, print something. When you run a test it ignores println! statements
        println!("Returning 5. This is not a test");
        5
    } else {
        println!("This shouldn't run, returning 0."); // otherwise return 0
        0
    }
}

fn main() {
    bring_number(true);
    bring_number(false);
}
```

کد بالا رو اگه در حالت عادی اجرا کنیم،‌ چنین چیزی رو پرینت میکنه:

```text
Returning 5. This is not a test
This shouldn't run, returning 0.
```

اما اگه در حالت `test` اجراش کنیم، چیز های دیگه‌ای پرینت میکنه:

```text
running 1 test
test testing::check_if_five ... ok

test result: ok. 1 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out
```

## Writing macros

نوشتن ماکرو میتونه پیچیده باشه. احتمالا هیچوقت نیازی نداریم که ماکرو بنویسیم، اما شاید گاهی اوقات بخوایم بنویسیم چون استفاده ازشون خیلی راحت هست. نوشتن ماکرو جالب هست به این دلیل که تقریبا انگار یک زبان دیگه هست.

برای نوشتن یک ماکرو ما باید از ماکروی دیگه به نام `macro_rules!` استفاده کنیم. بعد اسم ماکرو و بعد هم کد های ماکرو رو باید درون `{}` بنویسیم. یکجورایی شبیه به `match` هست.

در زیر یک ماکرویی رو میبینیم که یک `()` به عنوان ورودی میگیره و `6` رو برمیگردونه:

```rust
macro_rules! give_six {
    () => {
        6
    };
}

fn main() {
    let six = give_six!();
    println!("{}", six);
}
```

اما برابر با `match` نیست. به این دلیل که ماکرو ها چیزی رو کامپایل نمیکنند، فقط ورودی میگیرند و خروجی میدند، بعد کامپایلر اونها رو چک میکنه که ببینه با عقل جور در میاد یا نه. به همین دلیل هست که ماکرو ها شبیه کدی که کد مینویسه هستند. یادمون هست که یک `match` باید خروجی‌ای از یک نوع بده، به همین دلیل هست که کد زیر کار نمیکنه:

```rust
fn main() {
// ⚠️
    let my_number = 10;
    match my_number {
        10 => println!("You got a ten"),
        _ => 10,
    }
}
```

کامپایلر گیر میده که یه جایی `()` برمیگرده و یه جایی دیگه `i32` برمیگردونه، اینو درستش کن:

```text
error[E0308]: `match` arms have incompatible types
 --> src\main.rs:5:14
  |
3 | /     match my_number {
4 | |         10 => println!("You got a ten"),
  | |               ------------------------- this is found to be of type `()`
5 | |         _ => 10,
  | |              ^^ expected `()`, found integer
6 | |     }
  | |_____- `match` arms have incompatible types
```

اما در ماکرو این مهم نیست، چون فقط قراره خروجی بده و به نوعش کاری نداره، پس میتونیم چنین کاری کنیم:

```rust
macro_rules! six_or_print {
    (6) => {
        6
    };
    () => {
        println!("You didn't give me 6.");
    };
}

fn main() {
    let my_number = six_or_print!(6);
    six_or_print!();
}
```
کد بالا مشکلی نداره و `You didn't give me 6.` رو پرینت میکنه میتونیم ببینیم که شبیه به `Match Arm` ها هم نیست، چون `_` درش وجود نداره. همچنین ما فقط میتونیم بهش `(6)` یا `()` بدیم، هر چیزی غیر از این باعث خطا میشه. حتی `6`‌ای که بهش میدیم یک `i32` نیست، فقط یک `6` هست.

یک مثال دیگه:
```rust
macro_rules! might_print {
    (THis is strange input 하하はは哈哈 but it still works) => {
        println!("You guessed the secret message!")
    };
    () => {
        println!("You didn't guess it");
    };
}

fn main() {
    might_print!(THis is strange input 하하はは哈哈 but it still works);
    might_print!();
}
```

این یک ماکروی عجیب هست که فقط به ورودی های `()` و `(THis is strange input 하하はは哈哈 but it still works)` جواب میده. خروجی که میده:

```text
You guessed the secret message!
You didn't guess it
```

پس ماکرو از `Syntax` زبان `Rust` استفاده نمیکنه. اما همچنان ماکرو ها میتونند نوع ها رو درک کنند، برای مثال:

```rust
macro_rules! might_print {
    ($input:expr) => {
        println!("You gave me: {}", $input);
    }
}

fn main() {
    might_print!(6);
}
```
کد بالا چنین خروجی‌ای میده: 

بخش `$input:expr` مهم هست، این بخش به معنای این هست که "هر `Expression` رو به یک متغییر به نام `$input` بده".

در ماکرو ها نام متغییر با `$` شروع میشه. برای مثال در ماکروی بالا اگه بهش یک `Expression` بدیم، ماکرو اون `Expression` رو پرینت میکنه:

```rust
macro_rules! might_print {
    ($input:expr) => {
        println!("You gave me: {:?}", $input); // Now we'll use {:?} because we will give it different kinds of expressions
    }
}

fn main() {
    might_print!(()); // give it a ()
    might_print!(6); // give it a 6
    might_print!(vec![8, 9, 7, 10]); // give it a vec
}
```

چیزی که پرینت میکنه:

```text
You gave me: ()
You gave me: 6
You gave me: [8, 9, 7, 10]
```

همچنین باید به این نکته توجه کرد که ما `{:?}` رو نوشتیم، اما در ماکرو اینکه ایا `&input` نوع `Debug` رو پرینت کرده چک نمیشه، فقط کد رو مینویسه و سعی میکنه که کامپایلش کنه، اگه نشد خطا میده.

خب یک ماکرو دیگه جه چیز هایی رو به جز `expr` متوجه میشه؟

خب ماکرو ها عبارت های `block | expr | ident | item | lifetime | literal  | meta | pat | path | stmt | tt | ty | vis` رو متوجه میشند. این بخش کمی پیچیده هست.

میتونیم معنای هر کدوم رو در این [لینک](https://doc.rust-lang.org/beta/reference/macros-by-example.html) ببینیم:
```text
item: یک ایتم
block: یک BlockExpression
stmt: یک Statement‌ که بدون سمیکالن هست(البته به جز اونهایی که به سمیکالن نیاز دارند)
pat: یک الگو
expr: یک Expression
ty: یک نوع
ident: یک IDENTIFIER_OR_KEYWORD
path: یک TypePath به سبک مسیر
tt: یک TokenTree (یک یا چند Token در Delimiter ها)
meta: یک Attr یا محتوای یک Attribute
lifetime: یک LIFETIME_TOKEN
vis: یک نشانگر جای خالی
literal: matches - ?LiteralExpression
```

یک سایت خوبی هم به نام `cheats.rs` وجود داره که در مورد این مبحث همه توضیح داده، میتونیم در این [لینک](https://cheats.rs/#macros-attributes) در موردشون بخونیم، در ضمن برای هر کدوم مثال هم زده.

با این حال، برای اکثر ماکرو ها ما از `expr` و `ident` و `tt` استفاده میکنیم. `ident` به معنای یک مشخص‌کننده هست و به اسم متغییر ها یا اسم فانکشن ها اشاره میکنه. `tt` به معنای یک `Token Tree` هست، همچنین یجورایی به معنای هر نوعی از ورودی هست. بزارید با استفاده از هر دوتای اینها یک ماکروی ساده بسازیم:

```rust
macro_rules! check {
    ($input1:ident, $input2:expr) => {
        println!(
            "Is {:?} equal to {:?}? {:?}",
            $input1,
            $input2,
            $input1 == $input2
        );
    };
}

fn main() {
    let x = 6;
    let my_vec = vec![7, 8, 9];
    check!(x, 6);
    check!(my_vec, vec![7, 8, 9]);
    check!(x, 10);
}
```

ماکروی بالا یک `ident` و یک `Expression` میگیره و میگه که ایا اینها برابر هستند یا خیر، خروجی کد بالا چنین چیزی میشه:

```text
Is 6 equal to 6? true
Is [7, 8, 9] equal to [7, 8, 9]? true
Is 6 equal to 10? false
```

در زیر هم یک ماکرو میبینیم که یک `tt` میگیره و پرینت میکنه. از یک ماکرو به نام `stringfy!` استفاده میکنه که یک `String` درست کنه:

```rust
macro_rules! print_anything {
    ($input:tt) => {
        let output = stringify!($input);
        println!("{}", output);
    };
}

fn main() {
    print_anything!(ththdoetd);
    print_anything!(87575oehq75onth);
}
```

چیزی که پرینت میکنه:

```text
ththdoetd
87575oehq75onth
```

اما اگه چیزی که `Space`، `Comma`و... بهش بدیم چیزی پرینت نمیکنه. چون فکر میکنه که داریم بهش بیشتر از یک ایتم بهش میدیم، پس گیج میشه.

اینجا همون جایی هست که ماکرو ها پیچیده میشند.
برای اینکه به یک ماکرو در یک زمان بیشتر از یک ایتم بدیم، باید از یک `Syntax` متفاوت استفاده کنیم.برای مثال به جای `$input` باید از `$($input1),*` استفاده کنیم. این به معنای این "صفر یا بیشتر" هست که با `,` جدا شدند(تعداد ایتم ها رو `*` مشخص کرده). اگه میخوایم تعداد ایتم هایی که میگیریم "یکی یا بیشتر‌" باشه، باید از `+` به جای `*` استفاده کنیم.

الان ماکرو چنین چیزی شده:

```rust
macro_rules! print_anything {
    ($($input1:tt),*) => {
        let output = stringify!($($input1),*);
        println!("{}", output);
    };
}


fn main() {
    print_anything!(ththdoetd, rcofe);
    print_anything!();
    print_anything!(87575oehq75onth, ntohe, 987987o, 097);
}
```

پس این ماکرو هر `Token Tree` میگیره که با `,` جدا شده باشند و از `stringfy!` استفاده میکنه که `String` بسازه و در نهایت پرینتش میکنه، برای مثال چیزی که پرینت میکنه:

```text
ththdoetd, rcofe

87575oehq75onth, ntohe, 987987o, 097
```

اگه ما به جای `*` از `+` استفاده میکردیم، به ما خطا میداد، به این دلیل که ما یک بار ورودی بهش ندادیم.

خب الان میتونیم قدرت ماکرو ها رو ببینیم. برای مثال در کد زیر ماکرو یک فانکشن به عنوان خروجی میده:

```rust
macro_rules! make_a_function {
    ($name:ident, $($input:tt),*) => { // First you give it one name for the function, then it checks everything else
        fn $name() {
            let output = stringify!($($input),*); // It makes everything else into a string
            println!("{}", output);
        }
    };
}


fn main() {
    make_a_function!(print_it, 5, 5, 6, I); // We want a function called print_it() that prints everything else we give it
    print_it();
    make_a_function!(say_its_nice, this, is, really, nice); // Same here but we change the function name
    say_its_nice();
}
```

خروجیش:

```text
5, 5, 6, I
this, is, really, nice
```

خب الان میتونیم بقیه ماکرو ها رو درک کنیم. میتونیم ببینیم که بعضی از ماکرو هایی که داشتیم استفاده میکردیم خیلی ساده هستند. برای مثال این کد ماکروی `write!` هست:

```rust
macro_rules! write {
    ($dst:expr, $($arg:tt)*) => ($dst.write_fmt($crate::format_args!($($arg)*)))
}
```

خب برای انکه از ماکروی بالا استفاده کنیم باید چنین چیز هایی رو بهش بدیم:
- یک `Expression` (`expr`) که اسم متغییر درش هست
- هر چیزی، اگه `$arg:tt` مینوشتیم فقط یکی میگرفت، اما به این دلیل که ما `$($arg::tt)*` نوشتیم، الان هیچی یا هر چند تا میگیره

بعدش از `write_fmt` استفاده میکنه توی `$dst`، `arg` ها رو بنویسه در اون از یک ماکروی دیگه به نام `format_args!` استفاده میکنه که همه‌ی `arg` ها رو میگیره.

خب بزارید حالا به `todo!` نگاهی بندازیم. این ماکرو زمانی استفاده میشه که کد رو ننوشتیم اما میخوایم برنامه کامپایل بشه:

```rust
macro_rules! todo {
    () => (panic!("not yet implemented"));
    ($($arg:tt)+) => (panic!("not yet implemented: {}", $crate::format_args!($($arg)+)));
}
```

این ماکرو دو حالت داره، ما میتونیم هم `()` بهش بدیم یا اینکه چند `Token Tree`(`tt`) بهش بدیم:
- اگه `()` بهش بدیم، از `panic!` و یک پیام برای استفاده میکنه، پس انگاری ما کد `panic!("not yet implemented)` رو بجاش نوشتیم
- اگه بهش ارگومان بدیم، سعی میکنه که اونها رو هم در `panic!` استفاده کنه. ما فانکشن `format_args!` رو هم داخلش میبینیم. مثل `println!` کار میکنه

پس اگه این کد رو هم بنویسیم همون کار رو انجام میده:

```rust
fn not_done() {
    let time = 8;
    let reason = "lack of time";
    todo!("Not done yet because of {}. Check back in {} hours", reason, time);
}

fn main() {
    not_done();
}
```

چنین چیزی پرینت میکنه:

```text
thread 'main' panicked at 'not yet implemented: Not done yet because of lack of time. Check back in 8 hours', src/main.rs:4:5
```

درون یک ماکرو میتونیم از خود اون ماکرو هم استفاده کنیم:

```rust
macro_rules! my_macro {
    () => {
        println!("Let's print this.");
    };
    ($input:expr) => {
        my_macro!();
    };
    ($($input:expr),*) => {
        my_macro!();
    }
}

fn main() {
    my_macro!(vec![8, 9, 0]);
    my_macro!(toheteh);
    my_macro!(8, 7, 0, 10);
    my_macro!();
}
```

این یا `()` میگیره یا یک `Expression` یا چند `Expression`. اما هر `Expression` که بهش دادیم رو نادیده میگیره و از `my_macro!` استفاده میکنیم و ورودی `()` رو هم بهش میدیم. پس همیشه خروجی `Let's print this.` میشه.

ما میتونیم همچین چیزی رو در `dbg!` هم ببینیم:

```rust
macro_rules! dbg {
    () => {
        $crate::eprintln!("[{}:{}]", $crate::file!(), $crate::line!()); //$crate means the crate that it's in.
    };
    ($val:expr) => {
        // Use of `match` here is intentional because it affects the lifetimes
        // of temporaries - https://stackoverflow.com/a/48732525/1063961
        match $val {
            tmp => {
                $crate::eprintln!("[{}:{}] {} = {:#?}",
                    $crate::file!(), $crate::line!(), $crate::stringify!($val), &tmp);
                tmp
            }
        }
    };
    // Trailing comma with single argument is ignored
    ($val:expr,) => { $crate::dbg!($val) };
    ($($val:expr),+ $(,)?) => {
        ($($crate::dbg!($val)),+,)
    };
}
```

(ماکروی `eprintln!` هم شبیه به `println!` هست، فقط تفاوتش این هست که در `io::stderr` به جای `io::stdout` پرینت میکنه، همچنین `eprint!` هم وجود داره که بعد اینکه نوشت نمیره ته خط)

پس میتونیم خودمون تستش کنیم:

```rust
fn main() {
    dbg!();
}
```

این اولین `Arm` رو اجرا میکنه، پس اسم فایل و خط رو با `file!` و `line!` پرینت میکنه. خروجیش میشه `src/main.rs:2`.

بزارید این رو امتحان کنیم:

```rust
fn main() {
    dbg!(vec![8, 9, 10]);
}
```

این `Arm` بعدی رو اجرا میکنه که در نتیجه کد `$crate::eprintln!("[{}:{}] {} = {:#?}", $crate::file!(), $crate::line!(), $crate::stringify!($val), &tmp)` اجرا میشه. پس با `file!` و `line!` پرینت میکنه و بعد `$val` رو تبدیل به `String` میکنه و بعدش هم `Pretty Print` میکنه، پس برای ورودی ما چین خروجی‌ای میده:

```text
[src/main.rs:2] vec![8, 9, 10] = [
    8,
    9,
    10,
]
```

و برای بقیه‌ی حالت ها هم فقط `dbg!` رو صدا میزنه.

همونطور که دیدیم ماکرو ها میتونند خیلی پیجیده باشند. معمولا ما از ماکرو استفاده میکنیم که یک کار ساده رو به طور خودکار انجام بدیم و در عین حال اون کار رو یک فانکشن معمولی نمیتونه انجام بده. بهترین روش یادگیری ماکرو ها خوندن ماکرو ها با مثال هست. افراد زیادی نیستند که بتونند به راحتی ماکرو بنویسند، بدون اینکه با مشکلی مواجه بشند. پس فکر نکنید که باید همه‌چیز رو درباره‌ی ماکرو ها بدونید که بتونید با زبان `Rust` کد بزنید. همچنین میتونیم برای نوشتن ماکروی خودمون از ماکرو های دیگه کپی کنیم و کمی تغییرشون بدیم، اینطوری در نهایت میتونیم به راحتی ماکرو های خودمون رو بنویسیم.

# Part 2 - Rust on your computer

خب دیدیم که میتونیم اکثر چیز‌ها در `Rust` رو در `Playground` یاد بگیریم، اما بعضی چیز ها رو هم نمیشه. اما خب اگه تا اینجا یاد گرفتین احتمالا `Rust` رو روی کامپیوتر خودتون نصب کردید. یه سری چیز ها هست که نمیشه در `Playground` یادشون گرفت، برای مثال کار با فایل ها یا نوشتن کد در چندین فایل یا گرفتن ورودی(`Flag`) از کاربر. اما وقتی `Rust` رو روی کامپیوتر نصب داشته باشیم، بهترین مزیتش این هست که میتونیم از هر `crate`‌ای که میخوایم استفاده کنیم. اما در `Playground` فقط میتونیم از محبوب‌ترین `crate` ها استفاده کنیم.

## cargo

خب `rustc` به معنای `Rust Compiler` هست و از اسمش هم میشه حدس زد که کامپایلر هست. یک فایلی که کد `Rust` درش نوشته شده با `.rs` تموم میشه. اکثر برنامه‌نویس ها از `rustc main.rs` برای کامپایل کردن کد استفاده نمیکنند، و بلکه از چیزی به نام `cargo` استفاده میکنند. `cargo`، `Package Manager` زبان `Rust` هست.

یک نکته‌ی جالب در مورد اسم `cargo`: بهش میگیم `cargo` چون `crate` ها رو در کنار هم میزاره. و خب اگه ما `crate`(جعبه) ها رو کنار هم بزاریم یک `cargo`(محموله) میگیریم.

ما میتونیم این رو هنگامی که `cargo` یک پروژه رو اجرا میکنه ببینیم. بزارید برنامه‌ای با `crate`، `rand` بنویسیم:

```rust
use rand::seq::SliceRandom; // Use this for .choose over slices

fn main() {

    let my_letters = vec!['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h'];

    let mut rng = rand::thread_rng();
    for _ in 0..6 {
        print!("{} ", my_letters.choose(&mut rng).unwrap());
    }
}
```
خروجیش میشه: `b c g h e a`

اما خروجیش برامون مهم نیست میخواید ببینیم که `cargo` چطوری اجراش میکنه. برای اجرای برنامه با `cargo` از دستور `cargo run` استفاده میکنیم. این دستور برنامه رو `build` میکنه و `run` میکنه.

در هنگام کامپایل چنین چیز هایی رو میبینیم:

```text
   Compiling getrandom v0.1.14
   Compiling cfg-if v0.1.10
   Compiling ppv-lite86 v0.2.8
   Compiling rand_core v0.5.1
   Compiling rand_chacha v0.2.2
   Compiling rand v0.7.3
   Compiling rust_book v0.1.0 (C:\Users\mithr\OneDrive\Documents\Rust\rust_book)
    Finished dev [unoptimized + debuginfo] target(s) in 13.13s
     Running `C:\Users\mithr\OneDrive\Documents\Rust\rust_book\target\debug\rust_book.exe`
g f c f h b
```

خب پس فقط `crate`، `rand` رو نیاورد و چندین `crate` دیگه رو هم برای کامپایل این برنامه استفاده کرد. این به این دلیل هست که ما `rand` رو لازم داریم، اما خود `rand` به چندین `crate` دیگه هم لازم داره. پس `cargo` همه‌ی `crate` هایی که نیاز داریم تا برنامه کامپایل بشه رو پیدا میکنه و میزاره کنار هم. در این برنامه ما فقط به هفت `crate` نیاز داشتیم اما در برنامه های کاربردی واقعی ما به چند صد `crate` نیاز داریم.

زبان `Rust` خیلی سریع اجرا میشه، اما در زمان کامپایل کمی کند هست، برای مثال کد زیر که از `Generic` درش استفاده رو ببینیم:

```rust
use std::fmt::Display;

fn print_and_return_thing<T: Display>(input: T) -> T {
    println!("You gave me {} and now I will give it back.", input);
    input
}

fn main() {
    let my_name = print_and_return_thing("Windy");
    let small_number = print_and_return_thing(9.0);
}
```

این فانکشن هرچیزی که `Display` رو پیاده‌سازی کرده باشه میتونه به عنوان ورودی بگیره، اول ما بهش یک `&str` دادیم و بعد یک `f64` که خب برنامه هم بدون مشکل اجرا میشه.

اما کامپایلر نمیخواد در هنگام اجرا `Runtime` اینارو تبدیل به کد ماشین کنه. و میخواد یک برنامه رو کنار هم بزاره که بتونه خودش بدون نیاز به `Runtime` تا حد ممکن اجرا بشه.

پس وقتی `"Windy"` رو میبینه چیزی شبیه به `fn print_and_return_thing<T: Display>(input: T) -> T` رو نمیبینه، بلکه چیزی شبیه به `fn print_and_return_thing(input: &str) -> &str` رو میبینه.

بعدش که `9.0` رو  میبینه، `fn print_and_return_thing(input: f64) -> f64` رو میبینه. همه‌ی این اتفاق ها و عملیات ها که توضیح خاصی دربارش ندادم و خیلی ساده‌سازی کردمش در زمان کامپایل اتفاق میوفته.

به همین دلیل هست که وقتی از `Generic` ها استفاده میکنیم،‌ زمان کامپایل طولانی میشه، به این دلیل که باید بتونه اون `Generic` ها رو تبدیل به `Concrete` کنه.

یک نکته‌ی دیگه: زبان `Rust` در سال `2020` خیلی روی کامپایلر کار کرد که زمان کامپایل کاهش پیدا کنه. هر نسخه‌ای از `Rust` یکم در کامپایل کردن، سریع‌تر هست.

خب بیاید یکم دستورات `cargo` رو یاد بگیریم:

- `cargo build`: برنامه رو `build` میکنه، یعنی کامپایل میکنه، و خروجیش چیزی هست که میتونه اچرا بشه
- `cargo run`: برنامه رو `build` میکنه و اجراش میکنه
- `cargo check`: کد رو چک میکنه و خطا ها و... رو میگه، زمانی که میگیره بسیار کمتر از `build` یا `run` هست چون فقط چک میکنه.
- `cargo new`: یک پروژه‌ی جدید درست میکنه، بعد `new` باید اسم پروژه رو بدیم. با این کار یک `Directory/Folder` درست میشه و هر فایلی که یک پروژه `Rust` باید داشته باشه هم توش قرار میگیره.
- `cargo clean`: وقتی `crate` به `Cargo.toml` اضاقه میکنیم، کامپایلر برای کامپایل باید اون `crate` رو دانلود کنه و خب فایل هاش روی کامپیوتر ذخیره میشند. اگه به اون فایل ها نیاز نداشتیم میتونیم از `cargo clean` استفاده کنیم که اون فایل ها پاک بشند.

باید به یک نکته‌ی مهم دیگه هم اشاره کنم، اون هم این هست که دستور `cargo build` یک `Flag` مهم که `--release` هست رو داره، اگه ازش استفاده کنیم زمان کامپایل بیشتر مبشه، به این دلیل که کامپایلر سعی میکنه خروجی اجرایی که میده در بهینه‌ترین و سریع‌ترین حالت ممکن باشه.

به `cargo build` میگیم، `Debug Build` و به `cargo build --release` میگیم، `Release Build`.

یک نکته‌ی دیگه در مورد کامپایلر: اولین بار که `cargo bulild` یا `cargo run` رو اجرا میکنیم، زمان کامپایل خیلی طول میکشه اما دفعات بعد سریع‌تر از دفعه‌ی اول کامپایل میشه. اما اگه `cargo clean` استفاده کنیم، بعد اگه از `cargo build` یا `cargo run` استفاده کنیم دوباره چون اولش بارش هست طول میکشه :)

## Taking user input

یک روش ساده برای گرفتن ورودی از کاربر استفاده از `std::io::stdin` هست. `stdin` به معنای `Standard Input` هست، که خب میتونه کیبورد کاربر باشه. با `()stdin` ما میتونیم از کاربر ورودی بگیریم، ورودی‌ای که گرفتیم رو باید داخل یک `&mut String` با اسفتاده از `.read_line()` ذخیره کنیم،‌ کد زیر یک مثالی از گرفتن ورودی از کاربر هست که کار میکنه، اما نه اونطوری که ما میخوایم
One easy way to take input from the user is with `std::io::stdin`. This means "standard in", which is the input from the keyboard. With `()stdin` you can get user input, but then you will want to put it in a `&mut String` with `.read_line()`. Here is a simple example of that, but it both works and doesn't work:

```rust
use std::io;

fn main() {
    println!("Please type something, or x to escape:");
    let mut input_string = String::new();

    while input_string != "x" { // This is the part that doesn't work right
        input_string.clear(); // First clear the String. Otherwise it will keep adding to it
        io::stdin().read_line(&mut input_string).unwrap(); // Get the stdin from the user, and put it in read_string
        println!("You wrote {}", input_string);
    }
    println!("See you later!");
}
```

این خروجیش هست:

```text
Please type something, or x to escape:
something
You wrote something

Something else
You wrote Something else

x
You wrote x

x
You wrote x

x
You wrote x
```
برنامه ورودی هارو میگیره و چاپ میکنه، و قرار بود اگه `x` رو گرفت برنامه رو متوقف کنه، اما خب نمیکنه. ما میتونیم با استفاده از `CTRL + ` برنامه رو متوقف کنیم.

بزارید `{}` رو به `{:?}` تغییر بدیم که اطلاعات بیشتری بگیریم(میتونیم از `dbg!` هم استفاده کنیم)، اگه این کار رو کنیم خروجی برنامه میشه:

```text
Please type something, or x to escape:
something
You wrote "something\r\n"
Something else
You wrote "Something else\r\n"
x
You wrote "x\r\n"
x
You wrote "x\r\n"
```
به این دلیل اینطوری هست که ما در حقیقت فقط `something` رو ننوشتیم، بلکه نوشتیم `something` و بعد یک `Enter` زدیم.

برای حل این مشکل میتونیم از متود `()trim.` که همه‌ی `Whitespace` ها رو حذف میکنه استفاده کنیم، در ضمن `Whitespace` ها این ها هستند: [https://doc.rust-lang.org/reference/whitespace.html](https://doc.rust-lang.org/reference/whitespace.html):

```text
U+0009 (horizontal tab, '\t')
U+000A (line feed, '\n')
U+000B (vertical tab)
U+000C (form feed)
U+000D (carriage return, '\r')
U+0020 (space, ' ')
U+0085 (next line)
U+200E (left-to-right mark)
U+200F (right-to-left mark)
U+2028 (line separator)
U+2029 (paragraph separator)
```

پس ما با استفاده از `()trim.` میتونیم برای مثال `x\r\n` رو به `x` تبدیل کنیم.

حالا برنامه رو تغییر میدیم:
```rust
use std::io;

fn main() {
    println!("Please type something, or x to escape:");
    let mut input_string = String::new();

    while input_string.trim() != "x" {
        input_string.clear();
        io::stdin().read_line(&mut input_string).unwrap();
        println!("You wrote {}", input_string);
    }
    println!("See you later!");
}
```

چیزی که پرینت میکنه:

```text
Please type something, or x to escape:
something
You wrote something

Something
You wrote Something

x
You wrote x

See you later!
```

یک نوع دیگه‌ای از ورودی هایی که کاربر میده هست که بهشون میگیم `Program Argument`، که با استفاده از `std::env::Args` میتونیم ازشون استفاده کنیم. `Args` چیزی هست که کاربر هنگام اجرای برنامه وارد کرده، همیشه حداقل یک `Arg` وجود داره. یک برنامه مینویسیم که با استفاده از `std::end::args()` تمام `Argument` هایی که برنامه فرستاده شده رو چاپ کنه:

```rust
fn main() {
    println!("{:?}", std::env::args());
}
```

اگه با استفاده از `cargo run` برنامه رو اجرا کنیم، چنین خروجی‌ای میگیریم:

```text
Args { inner: ["target\\debug\\rust_book.exe"] }
```

بزارید بهش `Argument` بدیم. برای اینکار `cargo run but with some extra words`  رو مینویسیم. خروجی‌ای که میده:

```text
Args { inner: ["target\\debug\\rust_book.exe", "but", "with", "some", "extra", "words"] }
```

خب جالب بود، وقتی که به [صفحه‌ی مستندات `Args`]() نگاه میکنیم،‌ میتونیم ببینیم که `IntoIterator` رو پیاده‌سازی کرده. این به این معنی هست که میتونیم ازش به عنوان `Iterator` استفاده کنیم:

```rust
use std::env::args;

fn main() {
    let input = args();

    for entry in input {
        println!("You entered: {}", entry);
    }
}
```

خروجیش:

```text
You entered: target\debug\rust_book.exe
You entered: but
You entered: with
You entered: some
You entered: extra
You entered: words
```

میتونیم ببینیم که همیشه اولین `Argument` مسیر هست، پس معمولا اولین `Arg` رو رد میکنیم:

```rust
use std::env::args;

fn main() {
    let input = args();

    input.skip(1).for_each(|item| {
        println!("You wrote {}, which in capital letters is {}", item, item.to_uppercase());
    })
}
```

خروجی:

```text
You wrote but, which in capital letters is BUT
You wrote with, which in capital letters is WITH
You wrote some, which in capital letters is SOME
You wrote extra, which in capital letters is EXTRA
You wrote words, which in capital letters is WORDS
```

یکی از رایج‌ترین استفاده از `Args`، تنظیم تنظیمات برنامه هست.

ما میتونیم کاری کنیم که اگه کاربر `Arg` مدنظر رو نده، برنامه اجرا نشه، در زیر یک برنامه‌ای نوشتیم که حروف رو به `Capital` یا `Lowecase` تبدیل کنه:

```rust
use std::env::args;

enum Letters {
    Capitalize,
    Lowercase,
    Nothing,
}

fn main() {
    let mut changes = Letters::Nothing;
    let input = args().collect::<Vec<_>>();

    if input.len() > 2 {
        match input[1].as_str() {
            "capital" => changes = Letters::Capitalize,
            "lowercase" => changes = Letters::Lowercase,
            _ => {}
        }
    }

    for word in input.iter().skip(2) {
      match changes {
        Letters::Capitalize => println!("{}", word.to_uppercase()),
        Letters::Lowercase => println!("{}", word.to_lowercase()),
        _ => println!("{}", word)
      }
    }
    
}
```

چندین مثال از اجرای برنامه:

ورودی: `cargo run please make capitals`:

```text
make capitals
```

ورودی: `cargo run capital`:

```text
// Nothing here...
```

ورودی: `cargo run capital I think I understand now`:

```text
I
THINK
I
UNDERSTAND
NOW
```

ورودی: `cargo run lowercase Does this work too?`

```text
does
this
work
too?
```

در کنار `Args` که ورودی های کاربر هست. چیزی به نام `Vars` هم وجود داره که متغییر های سیستم هست که میتونیم با استفاده از `std::env::vars()` بهشون دسترسی داشته باشیم. برای مثال:

```rust
fn main() {
    for item in std::env::vars() {
        println!("{:?}", item);
    }
}
```

خروجیش:

```text
("CARGO", "/playground/.rustup/toolchains/stable-x86_64-unknown-linux-gnu/bin/cargo")
("CARGO_HOME", "/playground/.cargo")
("CARGO_MANIFEST_DIR", "/playground")
("CARGO_PKG_AUTHORS", "The Rust Playground")
("CARGO_PKG_DESCRIPTION", "")
("CARGO_PKG_HOMEPAGE", "")
("CARGO_PKG_NAME", "playground")
("CARGO_PKG_REPOSITORY", "")
("CARGO_PKG_VERSION", "0.0.1")
("CARGO_PKG_VERSION_MAJOR", "0")
("CARGO_PKG_VERSION_MINOR", "0")
("CARGO_PKG_VERSION_PATCH", "1")
("CARGO_PKG_VERSION_PRE", "")
("DEBIAN_FRONTEND", "noninteractive")
("HOME", "/playground")
("HOSTNAME", "f94c15b8134b")
("LD_LIBRARY_PATH", "/playground/target/debug/build/backtrace-sys-3ec4c973f371c302/out:/playground/target/debug/build/libsqlite3-sys-fbddfbb9b241dacb/out:/playground/target/debug/build/ring-cadba5e583648abb/out:/playground/target/debug/deps:/playground/target/debug:/playground/.rustup/toolchains/stable-x86_64-unknown-linux-gnu/lib/rustlib/x86_64-unknown-linux-gnu/lib:/playground/.rustup/toolchains/stable-x86_64-unknown-linux-gnu/lib")
("PATH", "/playground/.cargo/bin:/playground/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin")
("PLAYGROUND_EDITION", "2018")
("PLAYGROUND_TIMEOUT", "10")
("PWD", "/playground")
("RUSTUP_HOME", "/playground/.rustup")
("RUSTUP_TOOLCHAIN", "stable-x86_64-unknown-linux-gnu")
("RUST_RECURSION_COUNT", "1")
("SHLVL", "1")
("SSL_CERT_DIR", "/usr/lib/ssl/certs")
("SSL_CERT_FILE", "/usr/lib/ssl/certs/ca-certificates.crt")
("USER", "playground")
("_", "/usr/bin/timeout")
```

پس اگه به متغییر های سیستم نیاز داشتیم از `Vars` استفاده میکنیم.

همچنین با استفاده از ماکروی `env!` میتونیم به یک `Var` دسترسی داشته باشیم. بهش اسم متغییر رو میدیم و مقدارش رو برمیگردونه. زمانی که اطمینان نداریم که متغییر وجود داره یا نه میتونیم از `option_env!` استفاده کنیم که خروجیش یک `Option` هست:

```rust
fn main() {
    println!("{}", env!("USER"));
    println!("{}", option_env!("ROOT").unwrap_or("Can't find ROOT"));
    println!("{}", option_env!("CARGO").unwrap_or("Can't find CARGO"));
}
```

خروجیش:

```text
playground
Can't find ROOT
/playground/.rustup/toolchains/stable-x86_64-unknown-linux-gnu/bin/cargo
```

پس `option_env!` از `env!` امن‌تر هست. `env!` زمانی خوب هست که میخواید اگه متغییر وجود نداشت برنامه `Crash` کنه.

## Using files

خب حالا که `Rust` رو روی کامپیوتر نصب کردیم میتونیم با فایل ها کار کنیم، در بخش قرار هست که مقدار زیادی `Result` ببینیم. این به دلیل این هست که در هنگام کار با فایل ها امکان داره خیلی چیز ها درست پیش نره، برای مثال فایل میتونه وجود نداشته باشه یا ما دسترسی خوندن بهش رو نداشته باشیم و...

خب احتمالا اپراتور `?` رو یادتون هست. اگه جلوی فانکشنی که `Result` میده از `?` استفاده کنیم، کامپایلر به خروجی `Result` نگاه میکنه، اگه مقدار `Ok` بود که مقدار رو برمیگردونه. اگه مقدار `Err` بود اون `Err` رو برمیگردونه.

در ضمن ما باید از `?` در فانکشنی استفاده کنیم که یک `Result` برمیگردونه و نوع `Err` هم باید همون نوعی باشه که فانکشنی که `Result` میده و ما داریم اون رو کنترل میکنیم، استفاده کرده.

اگه اون نوع رو نمیدونیم میتونیم مقدار `Err` رو `()` بزاریم و کامپایلر بعدش بهمون میگه که نوع باید چی باشه:

```rust
// ⚠️
fn give_number(input: &str) -> Result<i32, ()> {
    input.parse::<i32>()
}

fn main() {
    println!("{:?}", give_number("88"));
    println!("{:?}", give_number("5"));
}
```

کمکی که کامپایلر میکنه:

```text
error[E0308]: mismatched types
 --> src\main.rs:4:5
  |
3 | fn give_number(input: &str) -> Result<i32, ()> {
  |                                --------------- expected `std::result::Result<i32, ()>` because of return type
4 |     input.parse::<i32>()
  |     ^^^^^^^^^^^^^^^^^^^^ expected `()`, found struct `std::num::ParseIntError`
  |
  = note: expected enum `std::result::Result<_, ()>`
             found enum `std::result::Result<_, std::num::ParseIntError>`
```
خب عالیه، پس الان همون چیزی که کامپایلر گفت رو به عنوان نوع `Err` در نظر میگیریم:


```rust
use std::num::ParseIntError;

fn give_number(input: &str) -> Result<i32, ParseIntError> {
    input.parse::<i32>()
}

fn main() {
    println!("{:?}", give_number("88"));
    println!("{:?}", give_number("5"));
}
```

الان برنامه کار میکنه:
```text
Ok(88)
Ok(5)
```

خب حالا `()main` که چیزی برنمیگردونه، پس چطوری از `?` در `()main` استفاده کنیم؟
```rust
// ⚠️
use std::num::ParseIntError;

fn give_number(input: &str) -> Result<i32, ParseIntError> {
    input.parse::<i32>()
}

fn main() {
    println!("{:?}", give_number("88")?);
    println!("{:?}", give_number("5")?);
}
```

خطایی که میده:

```text
error[E0277]: the `?` operator can only be used in a function that returns `Result` or `Option` (or another type that implements `std::ops::Try`)
  --> src\main.rs:8:22
   |
7  | / fn main() {
8  | |     println!("{:?}", give_number("88")?);
   | |                      ^^^^^^^^^^^^^^^^^^ cannot use the `?` operator in a function that returns `()`
9  | |     println!("{:?}", give_number("5")?);
10 | | }
   | |_- this function should return `Result` or `Option` to accept `?`
```

خب `()main` هم میتونه یک `Result` برگردونه، دقیقا مثل هر فانکشن دیگه‌ای...



در کد زیر اگه برنامه بدون `Err`‌ای اچرا شد، ما مقدار `()` رو برمیگردونیم، اما اگه به خطایی برخورد برنامه `ParseIntError` رو برمیگردونه:
```rust
use std::num::ParseIntError;

fn give_number(input: &str) -> Result<i32, ParseIntError> {
    input.parse::<i32>()
}

fn main() -> Result<(), ParseIntError> {
    println!("{:?}", give_number("88")?);
    println!("{:?}", give_number("5")?);
    Ok(())
}
```

کد `Ok(())` رو فراموش نکنیم...

خروجیش:

```text
88
5
```

اما خب در مورد `()parse.` همچین نیازی به این کار نبود، اما وقتی که با فایل ها کار میکنیم خیلی بدردبخور میشه.

خب حالا به یک نکته‌ی مهم میرسیم، اپراتور `?` میتونه نوع یک `Err` رو هم عوض کنه.

در [صفحه‌ی اپراتور `?`](https://doc.rust-lang.org/std/macro.try.html) میتونیم ببینیم که چنین چیزی میگه

```text
If you get an `Err`, it will get the inner error. Then `?` does a conversion using `From`. With that it can change specialized errors to more general ones. The error it gets is then returned.
به فارسی
اگه مقدار `Err` بگیریم، این اپراتور مقدار `Err` رو میگیره. بعد `?` با استفاده از `From` سعی میکنه `Err` رو به چیز دیگه‌ای تبدیل کنه. با استفاده از این قابلیت ما میتونیم خطا های خاص رو به خطا های کلی‌تر تبدیل کنیم. در نهایت مقدار نهایی برگردونده میشه.
```

همچنین، `Rust` یک نوع `Result` برای کار با قایل ها داره. که `std::io::Result` هست. و این چیزی هست که معمولا به عنوان خروجی `()main` در هنگام کار با قایل ها ازش استفاده میکنیم.

نوع `std::io::Result` در حقیقت یک `Type Alias` هست:
```text
type Result<T> = Result<T, Error>;
```

پس این نوع در حقیقت `Result<T, Error>` هست اما ما فقط لازم هست که `Result<T>` رو بنویسیم.

خب حالا بیاید با فایل ها کار کنیم

در `std::fs` متود هایی برای کار با فایل ها وجود داره.

دقت کنید که ما قبل از محتویاتی که میخوایم بهش بدیم یک `b` قرار میدیم که تبدیل به `byte` بشند.

با استفاده از `std::io::Write` میتونیم در فایل ها چیز بنویسیم. با استفاده از این میتونیم از `.write_all()` استفاده کنیم که توی فایل چیز بنویسیم:

```rust
use std::fs;
use std::io::Write;

fn main() -> std::io::Result<()> {
    let mut file = fs::File::create("myfilename.txt")?; // Create a file with this name.
                                                        // CAREFUL! If you have a file with this name already,
                                                        // it will delete everything in it.
    file.write_all(b"Let's put this in the file")?;     // Don't forget the b in front of ". That's because files take bytes.
    Ok(())
}
```

اگه کد بالا رو اچرا کنیم یک فایل ایجاد میکنه که توش `Let's put this in the file` نوشته شده.

با تشکر از `?`، میتونیم کد بالا رو حتی توی یک خط هم بنویسیم:
```rust
use std::fs;
use std::io::Write;

fn main() -> std::io::Result<()> {
    fs::File::create("myfilename.txt")?.write_all(b"Let's put this in the file")?;
    Ok(())
}
```

کد بالا رو میتونیم اینطوری تفسیر کنیم: "لطفا سعی کن یک فایل درست کنی، اگه مشکلی پیش نیومد، از `.write_all()` استفاده کن که چیز توش بنویسی و چک کن که مشکلی پیش اومد یا نه. (اگه هر جا مشکلی پیش بیاد برنامه تموم میشه)"

البته یک فانکشن هم هست که این دو کار رو خودش انجام میده، و اون `std::fs::write` هست. به عنوان ورودی بهش اسم فایل و محتوایی که میخوایم درش بنویسیم رو میدیم.

بهتره مراقب باشید چون اگه فایل از قبل وجود داشته باشه، محتویاتی که درش هست پاک میشه و چیزی که ما گفتیم توش نوشته میشه.

همچنین در هنگام استفاده از این فانکشن نیازی نداریم که از `b` استفاده کنیم، دلیلش این هست:

```rust
pub fn write<P: AsRef<Path>, C: AsRef<[u8]>>(path: P, contents: C) -> Result<()>
```

کد `AsRef<[u8]>` دلیلی هست که اجازه میده قابلیت ای رو داشته باشه که به `u8` تبدیل بشه رو بهش بدیم.

مثالی از استفاده از فانکشن `std::fs::write`:
```rust
use std::fs;

fn main() -> std::io::Result<()> {
    fs::write("calvin_with_dad.txt", 
"Calvin: Dad, how come old photographs are always black and white? Didn't they have color film back then?
Dad: Sure they did. In fact, those photographs *are* in color. It's just the *world* was black and white then.
Calvin: Really?
Dad: Yep. The world didn't turn color until sometimes in the 1930s...")?;

    Ok(())
}
```

باز کردن یک فایل به اسونی ساختنش هست، میتونیم به جای `()create` از `()open` استفاده کنیم، بعد اگه فایل پیدا شد، میتونیم از متود هایی مثل `read_to_string()` اسفتاده کنیم.

متود `read_to_string()` به یک `String` نیاز داره که محتویات فایل رو داخلش بریزه:
```rust
use std::fs;
use std::fs::File;
use std::io::Read; // this is to use the function .read_to_string()

fn main() -> std::io::Result<()> {
     fs::write("calvin_with_dad.txt", 
"Calvin: Dad, how come old photographs are always black and white? Didn't they have color film back then?
Dad: Sure they did. In fact, those photographs *are* in color. It's just the *world* was black and white then.
Calvin: Really?
Dad: Yep. The world didn't turn color until sometimes in the 1930s...")?;


    let mut calvin_file = File::open("calvin_with_dad.txt")?; // Open the file we just made
    let mut calvin_string = String::new(); // This String will hold it
    calvin_file.read_to_string(&mut calvin_string)?; // Read the file into it

    calvin_string.split_whitespace().for_each(|word| print!("{} ", word.to_uppercase())); // Do things with the String now

    Ok(())
}
```

خروجیش:

```rust
CALVIN: DAD, HOW COME OLD PHOTOGRAPHS ARE ALWAYS BLACK AND WHITE? DIDN'T THEY HAVE COLOR FILM BACK THEN? DAD: SURE THEY DID. IN 
FACT, THOSE PHOTOGRAPHS *ARE* IN COLOR. IT'S JUST THE *WORLD* WAS BLACK AND WHITE THEN. CALVIN: REALLY? DAD: YEP. THE WORLD DIDN'T TURN COLOR UNTIL SOMETIMES IN THE 1930S...
```
خب اگه بخوایم یک فایل بسازیم ولی اگه از قبل وجود داشت، حذفش نکنیم چی؟

برای انجام اینکار میتونیم از `OpenOptions` استفاده کنیم، در حقیقت تا الان هم داشتیم از اون استفاده میکردیم و نمیدونستیم، برای مثال بیاید به کد `File::open` نگاه کنیم:

```rust
pub fn open<P: AsRef<Path>>(path: P) -> io::Result<File> {
        OpenOptions::new().read(true).open(path.as_ref())
    }
```

خب جالب شد، برای `File::create` هم اوضاع همین هست:

```rust
pub fn create<P: AsRef<Path>>(path: P) -> io::Result<File> {
        OpenOptions::new().write(true).create(true).truncate(true).open(path.as_ref())
    }
```

اگه به [صفحه‌ی مستندات `OpenOptions`]() بریم، میتونیم متود هایی که داره رو ببینیم،‌ اکثر اونها یک `bool` به عنوان ورودی میگیرند:

- `()append`: اگه فایل وجود داشت چیز هایی که ما میخوایم رو به مجتویاتی که قبلا وجود داشته اضافه میکنه
- `()create`: با استفاده از این میتونیم اجازه‌ی ساختن فایل رو بدیم
- `create_new()`: اگه از این استفاده کنیم به شرطی که قبلا فایل وجود نداشته باشه،‌ فایل رو میسازه
- `()read`: اگه میخوایم قابلیت خوندن رو داشته باشیم از این استفاده میکنیم
- `()truncate`: اگه از این استفاده کنیم وقتی که فایل رو باز میکنیم، محتویاتش رو هم حذف میکنیم
- `()write`: این اجازه‌ی نوشتن روی فایل رو میده

و در اخر از `()open.` استفاده میکنیم و خب مسیر فایل رو هم بهش میدیم، این به ما یک `Result` میده، برای مثال:

```rust
// ⚠️
use std::fs;
use std::fs::OpenOptions;

fn main() -> std::io::Result<()> {
     fs::write("calvin_with_dad.txt", 
"Calvin: Dad, how come old photographs are always black and white? Didn't they have color film back then?
Dad: Sure they did. In fact, those photographs *are* in color. It's just the *world* was black and white then.
Calvin: Really?
Dad: Yep. The world didn't turn color until sometimes in the 1930s...")?;

    let calvin_file = OpenOptions::new().write(true).create_new(true).open("calvin_with_dad.txt")?;

    Ok(())
}
```

اول از همه ما یک `OpenOptions` با استفاده از `new` درست کردیم. بعد قابلیت `write` رو بهش دادیم، بعد قابلیت `create_new` رو فعال کردیم و در نهایت سعی کردیم که فایل رو باز کنیم، چون فایل از قبل وجود داره، `Err` میگیریم:

```text
Error: Os { code: 80, kind: AlreadyExists, message: "The file exists." }
```

خب حالا بزارید از `()append.` استفاده کنیم که اجازه میده به انتهای فایل چیز بنویسیم.

متود `.write_all()` سعی میکنه که هر چیزی که بهش میدیم رو داخل فایل بنویسه.

همچنین `write!` هم همین کار رو میکنه. قبلا از `write!` برای نوشتن داخل یک `Buffer` استفاده کردیم(توی پیاده‌سازی `Display`)، اینبار ازش برای نوشتن داخل یک فایل استفاده میکنیم.

```rust
use std::fs;
use std::fs::OpenOptions;
use std::io::Write;

fn main() -> std::io::Result<()> {
    fs::write("calvin_with_dad.txt", 
"Calvin: Dad, how come old photographs are always black and white? Didn't they have color film back then?
Dad: Sure they did. In fact, those photographs *are* in color. It's just the *world* was black and white then.
Calvin: Really?
Dad: Yep. The world didn't turn color until sometimes in the 1930s...")?;

    let mut calvin_file = OpenOptions::new()
        .append(true) // Now we can write without deleting it
        .read(true)
        .open("calvin_with_dad.txt")?;
    calvin_file.write_all(b"And it was a pretty grainy color for a while too.\n")?;
    write!(&mut calvin_file, "That's really weird.\n")?;
    write!(&mut calvin_file, "Well, truth is stranger than fiction.")?;

    println!("{}", fs::read_to_string("calvin_with_dad.txt")?);

    Ok(())
}
```

خروجیش:

```text
Calvin: Dad, how come old photographs are always black and white? Didn't they have color film back then?
Dad: Sure they did. In fact, those photographs *are* in color. It's just the *world* was black and white then.
Calvin: Really?
Dad: Yep. The world didn't turn color until sometimes in the 1930s...And it was a pretty grainy color for a while too.
That's really weird.
Well, truth is stranger than fiction.
```

## cargo doc

حتما متوجه شدید که مستندات `Rust` شبیه به هم هستند. در سمت چپ ما `Struct` ها و `Trait` ها رو میبینیم، مثال های کد ها رو در سمت راست میبینیم و غیره...

این به این دلیل هست که مستندات به طور خودکار تولید میشوند. با استفاده از `cargo doc` میتونیم مستند رو بسازیم.

حتی یک پروژه‌ی خالی هم مستندات خوبی داره!

کد زیر رو در نظر بگیرید:

```rust
struct DoesNothing {}
struct PrintThing {}

impl PrintThing {
    fn prints_something() {
        println!("I am printing something");
    }
}

fn main() {}
```

اگه دستور `cargo doc --open` رو اجرا کنیم، اطلاعات زیادی میتونیم ببینیم، اول چنین چیزی رو نشون میده:

```text
Crate rust_book

Structs
DoesNothing
PrintThing

Functions
main
```
اما اگه روی یکی از `Struct` ها کلیک کنیم، اطلاعات زیادی حتی در مورد `Trait` ها هم میده که ما نمیدونستیم وجود دارند:

```text
Struct rust_book::DoesNothing
[+] Show declaration
Auto Trait Implementations
impl RefUnwindSafe for DoesNothing
impl Send for DoesNothing
impl Sync for DoesNothing
impl Unpin for DoesNothing
impl UnwindSafe for DoesNothing
Blanket Implementations
impl<T> Any for T
where
    T: 'static + ?Sized,
[src]
[+]
impl<T> Borrow<T> for T
where
    T: ?Sized,
[src]
[+]
impl<T> BorrowMut<T> for T
where
    T: ?Sized,
[src]
[+]
impl<T> From<T> for T
[src]
[+]
impl<T, U> Into<U> for T
where
    U: From<T>,
[src]
[+]
impl<T, U> TryFrom<U> for T
where
    U: Into<T>,
[src]
[+]
impl<T, U> TryInto<U> for T
where
    U: TryFrom<T>,
```

این به دلیل این هست که `Rust` یکسری `Trait` ها رو برای `Struct` ها به صورت پیشفرض پیاده‌سازی میکنه.

با استفاده از `Comment` ها میتونیم برای کدمون مستند بنویسیم:

```rust
/// This is a struct that does nothing
struct DoesNothing {}
/// This struct only has one method.
struct PrintThing {}
/// It just prints the same message.
impl PrintThing {
    fn prints_something() {
        println!("I am printing something");
    }
}

fn main() {}
```

خروجیش:

```text
Crate rust_book
Structs
DoesNothing This is a struct that does nothing
PrintThing  This struct only has one method.
Functions
main
```

## The end?

خب این اخر `Easy Rust in Persian` بود، اما من در دسترس هستم، اگه سوالی داشتید میتونید از طریق `pouria.khakpour9909@gmail.com` با من تماس بگیرید.

اگه فکر میکنید که بخشی درست توضیح داده نشده یا فکر میکنید که روش بهتری برای توضیج داره یا هر چیز دیگه‌ای! میتونید یک `issue` باز کنید. یا حتی بهتر یک `PR` بدید.

هدف این پروژه این هست که مباحث `Rust` رو به زبان ساده توضیح بدیم. البته `Rust` خودش میتونه یکم سخت باشه، اما ما سعی میکنیم...

## Credits

این پروژه فقط یک ترجمه‌ی فارسی از پروژه‌ی [`Easy Rust`](https://github.com/Dhghomon/easy_rust) هست.

</div>

