---
date: 2025-11-17
categories:
    - کارگاه عملی
tags:
    - Input and Output
    - Variables
    - Operators
links:
    - content/inputOutput.md
    - content/variablesAndOperators.md 
    - content/decisionMaking.md
    - content/loops.md
---

# کارگاه اول (دکتر مرتضوی)

## بخش ۱ (حلقه `for`)

سؤال ۱: چاپ اعداد زوج بین ۱ تا ۱۰۰

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;

    int main() {
        // حلقه برای پیمایش اعداد از 1 تا 100
        for(int i = 1; i <= 100; i++) { 
            // شرط: اگر عدد زوج بود
            if(i % 2 == 0) { 
                // چاپ عدد
                cout << i << " "; 
            }
        }
        cout << endl;
        return 0; 
    }
    ```

<!-- more -->

سؤال ۲: محاسبه مجموع ۱۰ عدد ورودی

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;

    int main() {
        int num, sum = 0; 
        
        // حلقه برای دریافت و جمع‌آوری 10 عدد
        for(int i = 1; i <= 10; i++) { 
            cout << "Enter number " << i << ": ";
            cin >> num; 
            
            // افزودن عدد ورودی به مجموع
            sum += num; 
        }
        
        cout << "Sum = " << sum << endl; 
        return 0; 
    }
    ```

## بخش ۲ (استفاده از `break;`)

سؤال ۳: پیدا کردن اولین عدد منفی

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;

    int main() {
        int num; 

        // حلقه برای دریافت حداکثر 10 عدد
        for(int i = 1; i <= 10; i++) { 
            cout << "Enter a number: "; 
            cin >> num; 

            // شرط: اگر عدد منفی بود
            if(num < 0) {
                cout << "First negative number: " << num << endl; 
                // توقف حلقه پس از یافتن اولین عدد منفی
                break; 
            }
        }
        return 0; 
    }
    ```

سؤال ۴: جستجوی عدد ۵۰ در ورودی‌ها

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;

    int main() {
        int num; 
        bool found = false; 

        // حلقه برای دریافت حداکثر 10 عدد
        for(int i = 1; i <= 10; i++) { 
            cout << "Enter number " << i << ": ";
            cin >> num; 

            // شرط: اگر عدد 50 پیدا شد
            if(num == 50) { 
                found = true; 
                cout << "50 is found!" << endl; 
                // توقف حلقه
                break; 
            }
        }

        // اگر پس از اتمام حلقه (یا break شدن) عدد پیدا نشده بود
        if(!found) { 
            cout << "There is no 50!" << endl; 
        }
        return 0; 
    }
    ```


## بخش ۳ (حلقه `for` تو در تو)

سؤال ۵: چاپ مربع ستاره‌ای

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;

    int main() {
        int n; 
        cout << "Enter N (size of the square): "; 
        cin >> n; 
        
        // حلقه بیرونی: کنترل سطرها (از 0 تا N-1)
        for(int i = 0; i < n; i++) { 
            // حلقه داخلی: کنترل ستون‌ها (از 0 تا N-1)
            for(int j = 0; j < n; j++) { 
                // چاپ ستاره برای هر خانه
                cout << "*"; 
            }
            // رفتن به سطر بعدی
            cout << endl; 
        }
        return 0; 
    }
    ```

سؤال ۶: چاپ مثلث ستاره‌ای

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;

    int main() {
        int n; 
        cout << "Enter N (number of rows): "; 
        cin >> n; 

        // حلقه بیرونی: کنترل سطرها (i از 1 تا N)
        for(int i = 1; i <= n; i++) { 
            // حلقه داخلی: کنترل ستون‌ها. در سطر i، تعداد i ستاره چاپ می‌شود (j از 1 تا i)
            for(int j = 1; j <= i; j++) { 
                cout << "*"; 
            }
            // رفتن به سطر بعدی
            cout << endl; 
        }
        return 0; 
    }
    ```


## بخش ۴ (ترکیب حلقه ها)

سؤال ۷: چاپ ارقام یک عدد (جدا کردن با while و چاپ با for)

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;

    int main() {
        int n; 
        cout << "Enter a number: "; 
        cin >> n; 

        // آرایه‌ای برای نگهداری ارقام و متغیر شمارنده
        int digits[20], count = 0; 

        // حلقه while: جدا کردن ارقام (از سمت راست) و ذخیره معکوس آن‌ها
        while (n > 0) { 
            digits[count] = n % 10; // گرفتن رقم یکان 
            n /= 10;                // حذف رقم یکان 
            count++;                // افزایش شمارنده ارقام 
        }

        cout << "Digits: "; 

        // حلقه for: چاپ ارقام از آرایه به صورت صحیح (از آخر به اول برای چاپ مستقیم)
        for(int i = count - 1; i >= 0; i--) { 
            cout << digits[i] << " "; 
        }
        cout << endl;

        return 0; 
    }
    ```

سؤال ۸: شمارش تعداد اعداد اول تا N

???success "پاسخ"
    ```cpp
    #include <iostream>
    #include <cmath> // برای استفاده از sqrt که بهینه‌سازی while را ساده می‌کند

    using namespace std;

    int main() {
        int n; 
        cout << "Enter N: "; 
        cin >> n; 

        int primeCount = 0; 

        // حلقه for بیرونی: پیمایش تمام اعداد از 2 تا N
        for(int num = 2; num <= n; num++) { 
            bool isPrime = true; 
            int i = 2; 

            // حلقه while داخلی: بررسی اول بودن عدد num
            // بهینه‌سازی: تا ریشه دوم num پیمایش می‌کند (i*i <= num) 
            while(i * i <= num) { 
                // شرط: اگر num بر i بخش‌پذیر بود، اول نیست
                if(num % i == 0) { 
                    isPrime = false; 
                    break; // توقف حلقه while داخلی 
                }
                i++; 
            }

            // اگر isPrime همچنان true باقی ماند
            if(isPrime) { 
                primeCount++; 
            }
        }

        cout << "The count of prime numbers = " << primeCount << endl; 
        return 0; 
    }
    ```
