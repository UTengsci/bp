---
icon: material/vector-line
---

وکتور ها مانند یک آرایه با سایز متغیر عمل می کنن! هدف جفت اون ها ذخیره سازی تعدادی از متغیرهای از جنس یکسانه اما با این
تفاوت که سایز وکتور ها برخلاف آرایه ها متغیره و میشه یک المنت به اونها زیاد یا کم کرد.

برای استفاده از وکتور ها باید از کتابخانه زیر استفاده کنید(هر چند `bits/stdc++.h` این کتابخانه رو هم شامل میشه).

```cpp
#include<vector>
```

---

## ساختن یک وکتور

ساختن یک وکتور با متغیر های دیگه متفاوته چون از یک خانواده جدا میاد. برای ساختن یک وکتور باید از کلیدواژه `vector`
استفاده کنید. بعد از اون تایپ متغیر مورد نظرتون رو داخل `<>` می نویسید و بعد از اون اسم وکتور رو  قرار میدید.

```cpp
vector<DATA_TYPE> NAME;
```

به عنوان مثال:

```cpp
vector<string> studentNames;
```

اگر قصد دارید به وکتورتون مقدار اولیه بدید مثل آرایه ها مقادیر رو داخل `{}` میذارید اما این سری نیازی نیست که تعداد
اونها رو از قبل مشخص کنید.

```cpp
vector<string> studentNames = {"iliya", "soroush", "reza", "ali"};
```

می تونیم در ابتدای ساخت یک وکتور به اون سایز مشخصی بدیم (دقیقا مثل یک آرایه) و علاوه بر اون حتی میتونیم مقادیر اولیه
ذخیره شده رو تعیین کنیم..

```cpp
vector<DATA_TYPE> NAME(SIZE, VALUE_OF_EACH);
```

مثلا:

```cpp
vector<int> vec1(5, -4); // {-4, -4, -4, -4, -4}
vector<bool> vec2(3, true); // {true, true, true} 
vector<string> vec3(2, "salam"); // {"salam", "salam", "salam"}
```

و طبیعتا میشه آرایه‌ای از وکتور ها یا وکتوری از وکتور ها تعریف کرد.
```cpp
vector<int> vec[100]; // array of vectors
vector<vector<int>> vec2; // vector of vectors
```

---

## دسترسی به اعضا

برای دسترسی به اعضای یک وکتور مانند آرایه عمل می کنیم. یعنی با عملگر `[]` میتونیم به المنت مورد نظر دسترسی داشته باشیم.
همچنین یادتون باشه که وکتور ها هم مانند آرایه ها 0-base هستن. یعنی المنت اول در `[0]` و المنت دوم در `[1]` و ... قرار
دارند.

```cpp
vector<string> studentNames = {"iliya", "soroush", "reza", "ali"};

cout << studentNames[0];

// output: iliya
```

همچنین برای چک کردن این که یک وکتور خالی هست یا نه باید از دستور `()empty.` استفاده کنید که به شما یک `true` یا `false`
بر میگردونه.

 برای دسترسی به اعضای اول یا آخر میشه از `()front.` و `()back.` استفاده کرد.

```cpp
cout << studentNames.back(); //(1)!

// output: ali
```

1. !!!danger 
    حواستون باشه که اگر وکتور خالی باشه با ران تایم ارور مواجه میشید.

 برای به دست آوردن تعداد اعضای موجود در وکتور باید از `()size.` استفاده کنید.

```cpp
cout << studentNames.size();

// output: 4
```

همچنین تعویض مقدار یک عضو مانند آرایه هاست.

```cpp
studentNames[2] = "amir";

for (int i = 0; i < studentNames.size(); i++) {
    cout << studentNames[i] << " ";
}

// output: iliya soroush amir ali
```

---

## حذف و اضافه

مهم ترین قدرت وکتور ها در حذف و اضافه المنت هاشون مشخص میشه.

برای اضافه کردن یک المنت به آخر وکتور از `()push_back.` و حذف کرن یک المنت از آخر وکتور از `()pop_back.` استفاده می
کنیم.

```cpp

studentNames.push_back("parham");
studentNames.push_back("sara");

// elements = {iliya, soroush, amir, ali, parham, sara}

studentNames.pop_back();

// elements = {iliya, soroush, amir, ali, parham}
```

!!!warning
    حواستون باشه که به طور پیش فرض ما فقط میتونیم به آخر وکتور یک المنت رو اضافه یا کم کنیم و در حالت عادی قابلیت اضافه
    یا کم کردن از وسط وکتور رو نداریم.


از طرفی میتونیم تمام اعضای یک وکتور رو یک جا با تابع `()clear.` حذف کنیم.

```cpp
vector<int> vec(4, 11);

cout << vec.size() << endl;
// output: 4

vec.clear();
cout << vec.size() << endl;
// output: 0

cout << vec.empty() << endl;
// output: 1        (true)

```

---

## حلقه روی وکتور

برای گردش روی یک وکتور و دسترسی به اعضای اون به کمک حلقه ها میتونید از دو روش عمل کنید.

### به کمک ایندکس

```cpp
for (int i = 0; i < studentNames.size(); i++) {
    cout << studentNames[i] << " ";
}

// output: iliya soroush reza ali
```

### دسترسی مستقیم

این نوع حلقه که در ورژن `11 ++C` اضافه شده به ما این امکان رو میده که با سینتکس کمتری به اعضای هر وکتور دسترسی پیدا
کنیم.
```cpp
for (string name : studentNames) {
    cout << name << " ";
}

// output: iliya soroush reza ali
```
