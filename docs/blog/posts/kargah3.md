---
date: 2025-11-16
categories:
    - کارگاه عملی
tags:
    - Input and Output
    - Variables
    - Loops
links:
    - content/inputOutput.md
    - content/variablesAndOperators.md 
    - content/loops.md
---

# کارگاه فصل ۳

## سوال اول
برنامه‌ای بنویسید که اعداد زوج بین ۱ تا ۱۰۰۰ را چاپ کند.

<!-- more -->

مرحله ۱: کران بالای بازه را از ورودی بگیرید.
یک متغیر دیگر از نوع int تعریف کنید و مقدار آن را از ورودی بگیرید:

اگر مقدار ۱ بود، اعداد فرد را چاپ کند.
اگر مقدار ۲ بود، اعداد زوج را چاپ کند.
در غیر این صورت، پیام خطا چاپ کند که مقدار ورودی صحیح نیست.

??? success "پاسخ"
    ```cpp
    #include <iostream>

    using namespace std;

    int main() {
        int upperBound;
        int choice;

        cout << "Enter the upper bound: ";
        cin >> upperBound;

        cout << "Choose (1 for odd, 2 for even): ";
        cin >> choice;

        if (choice == 1) {
            for (int i = 1; i <= upperBound; i = i + 2) {
                cout << i << endl;
            }
        } else if (choice == 2) {
            for (int i = 2; i <= upperBound; i = i + 2) {
                cout << i << endl;
            }
        } else {
            cout << "Invalid input." << endl;
        }

        return 0;
    }
    ```

## سوال دوم
برنامه‌ای بنویسید که نمرات ۲۰ دانشجو را دریافت کند و موارد زیر را محاسبه و چاپ نماید:

* کمترین نمره
* بیشترین نمره
* مجموع نمرات
* میانگین نمرات

??? success "پاسخ"
    ```cpp
    #include <iostream>

    using namespace std;

    int main() {
      int minGrade;
      int maxGrade;
      int currentGrade;
      double sum = 0;

      cout << "Enter grade for student 1: ";
      cin >> currentGrade;

      minGrade = currentGrade;
      maxGrade = currentGrade;
      sum = sum + currentGrade;

      for (int i = 2; i <= 20; i = i + 1) {
        cout << "Enter grade for student " << i << ": ";
        cin >> currentGrade;

        sum += currentGrade;

        if (currentGrade < minGrade) {
          minGrade = currentGrade;
        }

        if (currentGrade > maxGrade) {
          maxGrade = currentGrade;
        }
      }

      double average = sum / 20;

      cout << "--- Grade Statistics ---" << endl;
      cout << "Maximum Grade: " << maxGrade << endl;
      cout << "Minimum Grade: " << minGrade << endl;
      cout << "Sum of Grades: " << sum << endl;
      cout << "Average Grade: " << average << endl;

      return 0;
    }
    ```


## سوال سوم
برنامه‌ای بنویسید که یک عدد صحیح از ورودی بگیرد و تعداد ارقام آن را چاپ کند.

???success "پاسخ"
    ```cpp
    #include <iostream>

    using namespace std;

    int main() {
      int number;
      int count = 0;

      cin >> number;

      if (number > 0 && number < 10) count++;

      while (number / 10 > 0) {
        count++;
        number = number / 10;
      }

      cout << "The number of digits is: " << count << endl;

      return 0;
    }
    ```


## سوال چهارم
یک بازی ساده و تعاملی پیاده‌سازی کنید:

* کاربر اول یک عدد صحیح وارد می‌کند (عدد هدف).
* کاربر دوم باید آن عدد را حدس بزند.
* کاربر دوم می‌تواند به تعداد نامحدود حدس بزند.
* پس از هر حدس، برنامه راهنمایی دهد که عدد وارد شده بزرگ‌تر یا کوچک‌تر از عدد هدف است.
* اگر کاربر دوم از بازی منصرف شد، می‌تواند عدد -۱ را وارد کند و از بازی خارج شود.

???success "پاسخ"
    ```cpp
    #include <iostream>

    using namespace std;

    int main() {
      int targetNumber;
      int guess;

      cout << "Player 1: Enter the target number: ";
      cin >> targetNumber;

      cout << "Player 2: Start guessing." << endl;

      while (1) {
        cout << "Your guess: ";
        cin >> guess;

        if (guess == -1) {
          cout << "You quit the game. The target number was " << targetNumber << "." << endl;
          break;
        }

        if (guess == targetNumber) {
          cout << "Congratulations! You guessed correctly." << endl;
          break;
        }

        if (guess > targetNumber) {
          cout << "Your guess is greater than the target. Try again." << endl;
        }

        if (guess < targetNumber) {
          cout << "Your guess is smaller than the target. Try again." << endl;
        }
      }

      return 0;
    }
    ```
