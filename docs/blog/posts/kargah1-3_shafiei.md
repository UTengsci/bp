---
date: 2025-11-14
categories:
    - کارگاه عملی
tags:
    - Input and Output
    - Variables
    - Operators
links:
    - content/inputOutput.md
    - content/variablesAndOperators.md 
    - content/helloWorld.md 
    - content/decisionMaking.md
---

# کارگاه فصل ۱ تا ۳ (دکتر شفیعی فر)

## سری 0

> Hello World

برنامه این بنویسید که عبارت "Hello World!" را چاپ کند، برنامه را کامپایل و اجرا کنید.

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;
    int main() {
        cout << "Hello World!" << endl;
        return 0;
    }
    ```

## سری 1 (مسائل پایه)

**جمع یک بازه**

برنامه‌ای بنویسید که دو عدد صحیح start و end را از کاربر دریافت کند. سپس مجموع تمام اعداد از start تا end (شامل خود این دو عدد) را محاسبه و چاپ کند.

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;
    int main() {
        int start, end;
        int sum = 0;
        cout << "Enter start and end numbers: ";
        cin >> start >> end;
        // Loop from start to end inclusive
        for (int i = start; i <= end; i++) {
            sum += i;
        }
        cout << "Sum: " << sum << endl;
        return 0;
    }
    ```

**چالش FizzBuzz** 

برنامه‌ای بنویسید که با استفاده از یک حلقه for، اعداد ۱ تا ۱۰۰ را چاپ کند.

* به جای مضارب 3 “Fizz” را چاپ کند.
* به جای مضارب 5 “Buzz” را چاپ کند.
* به جای اعداد ی که هم مضرب ۳ و هم مضرب ۵ هستند، کلمه “FizzBuzz” را چاپ کند.

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;
    int main() {
        for (int i = 1; i <= 100; i++) {
        // Check for both 3 and 5 first (number divisible by 15)
            if (i % 3 == 0 && i % 5 == 0) {
                cout << "FizzBuzz" << endl;
            } else if (i % 3 == 0) {
                cout << "Fizz" << endl;
            } else if (i % 5 == 0) {
                cout << "Buzz" << endl;
            } else {
                cout << i << endl;
            }
        }

        return 0;
    }
    ```

**مجموع اعداد ورودی**

* برنامه‌ای بنویسید که ابتدا از کاربر بخواهد یک عدد مثبت (n) وارد کند، سپس از یک حلقه while استفاده کنید تا به  n تعداد بار دیگر از کاربر ورودی عددی بگیرد و در نهایت مجموع اعداد را در خروجی چاپ کند.

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;
    int main() {
        int n;
        double num, sum = 0;
        cout << "Enter the count of numbers (n): ";
        cin >> n;
        int i = 0;
        while (i < n) {
            cout << "Enter number: ";
            cin >> num;
            sum += num; // Accumulate value
            i++;
        }
        cout << "Total Sum: " << sum << endl;
        return 0;
    }
    ```

**شمارش اعداد منفی و مثبت و صفر**

* برنامه‌ای بنویسید که از کاربر بخواهد ۱۰ عدد را (یکی پس از دیگری) وارد کند. در پایان، تعداد اعداد مثبت، تعداد اعداد منفی، و تعداد صفرهایی که وارد شده‌اند را بشمارد و چاپ کند.


???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;
    int main() {
        int num;
        int pos = 0, neg = 0, zero = 0;
        cout << "Enter 10 numbers:" << endl;
        for (int i = 0; i < 10; i++) {
            cin >> num;
            // Categorize the input
            if (num > 0) {
                pos++;
            } else if (num < 0) {
                neg++;
            } else {
                zero++;
            }
        }
        cout << "Positives: " << pos << endl;
        cout << "Negatives: " << neg << endl;
        cout << "Zeros: " << zero << endl;
        return 0;
    }
    ```

## سری ۲ (مسائل چالشی)

**یافتن حداقل و حداکثر (از N ورودی)**

* برنامه‌ای بنویسید که ابتدا از کاربر بپرسد چند عدد می‌خواهید وارد کند (n)، سپس، در یک حلقه n عدد از او دریافت کند. در حین دریافت اعداد، بزرگترین و کوچکترین عددی که وارد کرده است را پیدا و در پایان چاپ کند.

???success "پاسخ"
    ```cpp
    #include<iostream>

    using namespace std;

    int main() {
        int n;
        cin >> n;

        int x;
        cin >> x;
        int mn = x, mx = x;
        for (int i = 1; i < n; i++) {
            cin >> x;
            mn = min(mn, x);
            mx = max(mx, x);
        }
        cout << "max is: " << mx << endl;
        cout << "min is: " << mn << endl;
        return 0;
    }
    ```

**چاپ معکوس ارقام عدد**

* برنامه‌ای بنویسید که یک عدد صحیح مثبت (مثلاً 12345) از کاربر دریافت کند با استفاده از یک حلقه و عملیات ریاضی (باقیمانده و تقسیم)، ارقام آن را به ترتیب معکوس چاپ کند (مثلاً 54321).

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;
    int main()
    {
        int num;
        cout << "Enter a positive integer: ";
        cin >> num;
        cout << "Reversed: ";
        // Handle the edge case where input is exactly 0
        if (num == 0) {
            cout << 0;
        }

        while (num > 0) {
            cout << num % 10; // Print the last digit
            num /= 10; // Remove the last digit
        }
        cout << endl;
        return 0;
    }
    ```

**تشخیص عدد اول**

* برنامه‌ای بنویسید که یک عدد صحیح مثبت (بزرگتر از 1) از کاربر دریافت کند. برنامه باید تشخیص دهد که آیا این عدد اول است یا خیر (عدد اول عددی است که هیچ مقسوم‌طبیعی جز 1 و خودش ندارد) "No" یا "Yes" چاپ کند.

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;
    int main()
    {
        int num;
        bool isPrime = true; // Assume prime until proven otherwise
        cout << "Enter a number > 1: ";
        cin >> num;
        if (num <= 1) {
            isPrime = false;
        }
        // Check divisibility from 2 up to the square root of num
        for (int i = 2; i * i <= num; i++) {
            if (num % i == 0) {
                isPrime = false; // Found a divisor, so it's not prime
                break; // Exit loop early
            }
        }

        cout << (isPrime ? "YES" : "NO") << endl;
        return 0;
    }
    ```

**چاپ مربع توخالی**

* برنامه‌ای بنویسید که یک عدد (n) از کاربر دریافت کند. با استفاده از حلقه‌های تودرتو، یک مربع توخالی با ابعاد n در n با استفاده از کاراکتر (ستاره) چاپ کند. برای مثال، اگر n=5 باشد، خروجی باید به شکل زیر باشد:

```
*****
*   *
*   *
*   *
*****
```

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;
    int main()
    {
        int n;
        cout << "Enter size n: ";
        cin >> n;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                // Print '*' only if we are on the borders (first/last row OR first/last column)
                if (i == 0 || i == n - 1 || j == 0 || j == n - 1) 
                    cout << "*";
                else
                    cout << " ";
            }
            cout << endl; // Move to next row
        }
        return 0;
    }
    ```
