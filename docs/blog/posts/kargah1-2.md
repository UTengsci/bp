---
date: 2025-11-15 
categories:
    - کارگاه عملی
tags:
    - Input and Output
    - Variables
    - Operators
links:
    - content/inputOutput.md
    - content/variablesAndOperators.md 
---

# کارگاه فصل ۱ و ۲

## سوال اول
برنامه‌ای بنویسید که نام و نام خانوادگی خود را در خروجی چاپ کند و در خط بعدی کلمه‌ی Programming Class را چاپ کند.

<!-- more -->

* در مرحله‌ی بعد سن خود را از طریق ورودی به برنامه بدهید و آن را در جلوی اسم خود چاپ کنید. برای این کار یک متغیر int تعریف کرده و با دستور cin، مقدار آن را توسط ورودی دریافت کنید.

??? success "پاسخ"
    ```cpp
    #include <iostream>

    using namespace std;

    int main()
    {
        int Age;
        cin >> Age;
        cout << "Mohammad Hosein Solouki " << Age << endl
             << "Programming Class";
    }
    ```


## سوال دوم

 برنامه‌ای بنوسید که دو عدد صحیح را از ورودی دریافت کند و حاصل جمع آن را در خروجی چاپ کند.

* مرحله دوم: تفریق دو عدد در خروجی چاپ شود
* •	مرحله‌ی ۳: یک متغیر bool تعریف کنید و مقدار آن را از ورودی بگیرید. اگر bool برابر با ۱ (True) باشد، حاصل‌جمع چاپ شود. اگر برابر با ۰ (False) باشد، تفاضل دو عدد چاپ شود.


??? success "پاسخ"
    ```cpp
    #include <iostream>

    using namespace std;

    int main()
    {
        int x, y;
        bool Check;
        cin >> x >> y;
        cin >> Check;
        int Sum, Difference;
        Sum = x + y;
        Difference = x - y;
        if (Check == true)
        {
            cout << Sum;
        }
        else
        {
            cout << Difference;
        }
    }
    ```

## سوال سوم
برنامه‌ای بنویسید که دو عدد صحیح را از ورودی دریافت کند. با توجه به شرایط زیر، اعمال مربوطه انجام شود:

* اگر عدد اول زوج بود: حاصل‌ضرب دو عدد چاپ شود.
* اگر عدد اول فرد بود: حاصل‌جمع دو عدد چاپ شود.
* اگر عدد دوم زوج بود: تفاضل دو عدد چاپ شود.
* اگر عدد دوم فرد بود: حاصل‌تقسیم عدد اول در عدد دوم چاپ شود. در محاسبه‌‌ی تقسیم، اعشار حاصل نیز نمایش داده شود. برای این کار هنگام تقسیم، صورت تقسیم را باید به double تبدیل کنید. به مثال زیر توجه کنید:

    ```cpp
    double(a) / b
    ```


??? success "پاسخ"
    ```cpp
    #include <iostream>

    using namespace std;

    int main()
    {
        int x, y;
        cin >> x >> y;
        if (x % 2 == 0) {
            cout << x * y << endl;
        } else {
            cout << x + y << endl;
        }

        if (y % 2 == 0) {
            cout << x - y << endl;
        } else {
            cout << double(x) / y;
        }
    }
    ```
## سوال چهارم
دو عدد ضحیح از ورودی دریافت کنید که به عنوان اضلاع مثلث هستند. با استفاده از فرمول $\sqrt{a^2 + b^2}$ وتر مثلث را محاسبه
کند.

برای محاسبه‌ی جذر و توان ابتدا کتابخانه‌ی math.h را در برنامه به صورت زیر وارد کنید:
```cpp
#include<math.h>
```

سپس با استفاده از توابع `sqrt` و `pow` مقادر مورد نظر را محاسبه کنید.
```cpp
sqrt(a); // جذر عدد
pow(a, 2); // توان دوم
```


??? success "پاسخ"
    ```cpp 
    #include <iostream>
    #include <math.h>

    using namespace std;

    int main()
    {
        int a, b;
        cin >> a >> b;
        double A, B, C;
        A = pow(a, 2);
        B = pow(b, 2);
        C = sqrt(A + B);
        cout << C;
    }
    ```
