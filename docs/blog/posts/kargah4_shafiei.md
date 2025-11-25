---
date: 2025-11-22
categories:
    - کارگاه عملی
links:
    - content/function.md
---

# کارگاه فصل ۴ (دکتر شفیعی فر)

## سوال اول

**محاسبه جمله nام دنباله فیبوناچی.**

تابعی بنویسید که $n$ را از ورودی دریافت کند و جمله $n$ام دنباله فیبوناچی را محاسبه کند.

دنباله فیبوناچی: $0, 1, 1, 2, 3, 5, 8, \dots$

$a_1=0$; $a_2=1$ 

$a_n=a_{n-1}+a_{n-2}$ برای $n=3, 4, 5, \dots$

???success "پاسخ"
    ```cpp
    #include<iostream>
    using namespace std;

    int fibonacci(int n) {
        if (n <= 0) return -1;
        if (n == 1) return 0;
        if (n == 2) return 1;

        int a = 0;
        int b = 1;
        int c = 0;

        for (int i = 3; i <= n; i++) {
            c = a + b;
            a = b;
            b = c;
        }
        return c;
    }
    
    int main() {
        int n;
        cout << "Enter n for Fibonacci: ";
        cin >> n;
        cout << "Fibonacci result: " << fibonacci(n) << endl;
        return 0;
    }
    ```

<!-- more -->

## سوال دوم

**چاپ ارقام تشکیل‌دهنده یک عدد**

تابعی بنویسید که یک عدد از ورودی دریافت کند و ارقام تشکیل‌دهنده آن را در خروجی جدا از هم چاپ کند.

مثال:
```
input: 542
output: 5 4 2
```

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;
    void printDigits(int n) {
        cout << "Digits: ";
        // Loop to get each digit from the end
        while (n > 0) {
            cout << (n % 10) << " ";
            n /= 10;
        }
        cout << endl;
    }
    int main() {
        int num;
        cout << "Enter a number: ";
        cin >> num;
        printDigits(num);   
        return 0;
    }
    ```

## سوال سوم

با توجه به الگوریتمی که در سوال شماره ۲ استفاده کردید، توابعی بنویسید که:

* (الف) مجموع ارقام تشکیل‌دهنده عدد ورودی را برگرداند

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;

    int sumOfDigits(int n)
    {
        int sum = 0;
        while (n > 0)
        {
            sum += (n % 10); // Add the last digit to sum
            n /= 10; // Remove the last digit
        }
        return sum;
    }

    // int main() ... (کامل در قسمت ج، د، ه)
    ```

* (ب) بزرگترین رقم تشکیل‌دهنده عدد را برگرداند.

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;

    int maxDigit(int n)
    {
        int maxVal = 0;
        while (n > 0)
        {
            int digit = n % 10;
            if (digit > maxVal)
            {
                maxVal = digit;
            }
            n /= 10;
        }
        return maxVal;
    }

    int main()
    {
        int num;
        cout << "Enter a number: ";
        cin >> num;
        cout << "Sum of digits: " << sumOfDigits(num) << endl;
        cout << "Max digit: " << maxDigit(num) << endl;
        return 0;
    }
    ```

* (ج) بررسی کند آیا عدد دریافت شده عدد قوی هست یا خیر و نتیجه را برگرداند. (عددی قوی است که مجموع فاکتوریل ارقام آن
    برابر با خود آن عدد شود مثلا ۱۴۵)

* (د) بررسی کند آیا عدد مورد نظر آرمسترانگ است یا خیر و نتیجه را برگرداند. (عددی آرمسترانگ است که مجموع مکعبات ارقام آن
    برابر با خود عدد شود)
* (ه) بررسی کند عدد کامل است یا خیر و نتیجه را برگرداند. (عددی کامل است که مجموع شمارنده های کوچک تر از خودش برابر با
    خودش شود)

???success "پاسخ"
    ```cpp
    #include <iostream>
    using namespace std;

    // Helper function for Strong Number
    int factorial(int n)
    {
        int fact = 1;
        for (int i = 1; i <= n; i++)
        {
            fact *= i;
        }
        return fact;
    }

    // (ج) بررسی عدد قوی (Strong Number)
    // مجموع فاکتوریل ارقام تشکیل دهنده آن برابر با خودش است (مثلاً 145)[cite: 112, 113, 114].
    bool isStrong(int n)
    {
        int original = n;
        int sum = 0;
        while (n > 0)
        {
            int digit = n % 10;
            sum += factorial(digit);
            n /= 10;
        }
        if (sum == original) return true;
        else return false;
    }

    // (د) بررسی عدد آرمسترانگ (Armstrong Number)
    // مجموع مکعب ارقام آن برابر با خودش است[cite: 115, 116].
    bool isArmstrong(int n)
    {
        int original = n;
        int sum = 0;
        while (n > 0)
        {
            int digit = n % 10;
            // Add cube of digit
            sum += (digit * digit * digit);
            n /= 10;
        }
        if (sum == original) return true;
        else return false;
    }

    // (ه) بررسی عدد کامل (Perfect Number)
    // مجموع شمارنده های کوچکتر از خودش برابر با خودش است[cite: 117, 118].
    bool isPerfect(int n)
    {
        int sum = 0;
        // Find divisors
        for (int i = 1; i < n; i++)
        {
            if (n % i == 0)
            {
                sum += i;
            }
        }
        if (sum == n) return true;
        else return false;
    }

    int main()
    {
        int num;
        cout << "Enter a number to check: ";
        cin >> num;
        if (isStrong(num)) cout << "Strong Number: Yes" << endl;
        else cout << "Strong Number: No" << endl;
        if (isArmstrong(num)) cout << "Armstrong Number: Yes" << endl;
        else cout << "Armstrong Number: No" << endl;
        if (isPerfect(num)) cout << "Perfect Number: Yes" << endl;
        else cout << "Perfect Number: No" << endl;
        return 0;
    }
    ```

* (و) بزرگترین عدد اول بعد از عدد دریافتی از ورودی را برگرداند.
???success "پاسخ"

    ```cpp
    #include <iostream>
    using namespace std;

    // Helper function to check if a number is prime
    bool checkPrime(int n)
    {
        if (n <= 1) return false;
        // Check divisibility up to sqrt(n)
        for (int i = 2; i * i <= n; i++)
        {
            if (n % i == 0) return false;
        }
        return true;
    }

    int nextPrime(int n)
    {
        int num = n + 1;
        while (true)
        {
            if (checkPrime(num))
            {
                return num;
            }
            num++;
        }
    }

    int main()
    {
        int num;
        cout << "Enter a number: ";
        cin >> num;
        cout << "Next Prime: " << nextPrime(num) << endl;
        return 0;
    }
    ```

نکته: مقادیر بازگشتی توابعی که خودشان عملیات چاپ را انجام نمی‌دهند را با استفاده از تابع main در خروجی چاپ کنید. همچنین برای توابعی که مقادیر بازگشتیشان (بله/خیر) می‌باشد، از نوع داده boolean استفاده کنید.
