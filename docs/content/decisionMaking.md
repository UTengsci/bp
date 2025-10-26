---
icon: material/arrow-decision
---

## if

برای اینکه یک بلوک از کد تحت یک یا چند شرط اجرا بشه.

```cpp
if (CONDITION) {
    // block of code
}
```

و اگر شرط داخل `if` برابر با `true` بشه، کذ داخل اسکوپ ران میشه و اگر شرط `false` باشه، کد درون اسکوپ نادیده گرفته
میشه.

به عنوان مثال:
```cpp
int x;
cin >> x;
if (x > 10) {
    cout << "hello";
}
```

---

## else

به طور مکمل در کنار `if` استفاده میشه و خودش به تنهایی معنایی نداره.
کد درون `else` در صورت `false` بودن شرط درون `if` اول اجرا میشه.

```cpp
int x;
cin >> x;
if (x > 10) {
    cout << "hello";
} else {
    cout << "goodbye";
}
```

---

## else if
برای مواقعی که شرط اولیه `false` میشه، ما میتونیم شروط دیگری برای حالت های دیگر تعیین کنیم. برای این کار باید از `elseif
(CONDITION)` استفاده کنید.

```cpp
int x;
cin >> x;
if (x > 10) {
    cout << "if called" << endl;
} else if (x >= 5) {
    cout << "else if called" << endl;
} else {
    cout << "else called" << endl;
}
```

در مثال بالا اگر $x \ge 10$ باشه `if` صدا زده میشه و اگر $10 \ge x \ge 5$ باشه `else if` صدا زده میشه و اگر $5 > x$ باشه،
`else` صدازده میشه.

!!! tip
    برای یک `if` از هر چندتا `else if` می توان استفاده کرد.

```cpp
int x;
cin >> x;
if (x % 4 == 0) {
    cout << "Divisible!" << endl;
} else if (x % 4 == 1) {
    cout << "Modulo is 1" << endl;
} else if (x % 4 == 2) {
    cout << "Modulo is 2" << endl;
} else {
    cout << "Modulo is 3" << endl;
}
```

!!! note
    اگر شرط داخل `if` اول `false` بود، برنامه به `else if` اول میره و اگر شرط داخل `else if` اول هم `false` بود به `else
    if` دوم میره و ...
    اگر شرط درون یک `else if` برابر با `true` بشه، کد درون اون `else if` اجرا میشه ولی اما اگر تمام شروط `false` بودن،
    کد درون `else` (در صورت وجود) اجرا میشه.

    <div align="center">
    ```mermaid

    flowchart LR
        A(شرط اول برقراره؟) --آره--> B(عملیات اول)
        A --نه--> C(شرط دوم برقراره؟) --آره--> D(عملیات دوم)
        C --نه--> E(عملیات سوم)
    ```
    </div>

به نتیجه نکته بالا در دو کد زیر توجه کنید.
```cpp title="کد اول"
int x;
cin >> x;
if (x > 10) {
    cout << "First One" << endl; 
} if (x > 5) {
    cout << "Second One" << endl;
}

// input: 12
// output:
// First One
// Second One
```

```cpp title="کد دوم"
int x;
cin >> x;
if (x > 10) {
    cout << "First One" << endl;
} else if (x > 5) {
    cout << "Second One" << endl;
}

// input: 12
// output:
// First One
```

!!! example "`if` تک خطی"
    می توان ترکیب یک `if` و `else` ساده رو به صورت تک خطی نوشت. 

    ```cpp
    (CONDITION ? FIRST_OPERATION : SECOND_OPERATION);
    ```

    در اینجا اگر `CONDITION` برابر با `true` باشد، `FIRST_OPERATION` اجرا می شود و در غیر این صورت `SECOND_OPERATION`
    اجرا می شود.

    به عنوان مثال ۲ کد زیر معادل هم هستند.

    === "تک خطی"

        ```cpp
        int x;
        cin >> x;
        cout << (x / 4 >= 11 ? "yes" : "no") << endl;
        ```

    === "چند خطی"

        ```cpp
        int x;
        cin >> x;
        if (x / 4 >= 11) {
            cout << "yes" << endl;
        } else {
            cout << "no" << endl;
        }
        ```



<h2 id="switch"> switch </h2>
از `switch` برای مقایسه برابری یک متغیر با چند مقدار متفاوت در `case` های متفاوت استفاده میشه.

```cpp
switch(EXPRESSION) {
    case CONSTANT_EXPRESSION  :
        // some code
        break; //optional
    case CONSTANT_EXPRESSION  :
        // some code
        break; //optional
    // you can have any number of case statements.
    default : //Optional
        // some code
}
```

!!! danger "قوانین استفاده از `switch`"
    * `EXPRESSION` استفده شده در `switch` باید یکی از جنس های `int`, `char` و `bool` باشد در نتیجه نمی توان از `double`,
        `float` یا `string` استفاده کرد.
    * از هر تعداد `case` می توان در `switch` استفاده کرد.
    * در هر `case`، `CONSTANT_EXPRESSION` باید از جنس همان `EXPRESSION` اولیه تعریف شده باشد.
    * اگر مقدار `EXPRESSION` با مقدار یکی از `CONSTANT_EXPRESSION` ها برابر بود، کد درون اون `case` و هچنین تمام `case`
        های بعدی تا جایی که به یک `break;` نرسیدیم اجرا میشه. (در مثال ها به طور کامل تر متوجه میشید)
    * هر وقت که به `break;` رسیدیم اجرای `case` های `switch` متوقف میشه.
    * هر `switch` می تواند یک کیس `default` اختیار کند که اگر هیچ کدام از `case` ها اجرا نشد، کد درون `default` اجرا می
        شود.

### چند مثال

```cpp title="استفاده از switch برای روز های هفته"
int x;
cin >> x;
switch (x) {
    case 0:
        cout << "Shanbe" << endl;
        break;
    case 1:
        cout << "Yek Shanbe" << endl;
        break;
    case 2:
        cout << "Do Shanbe" << endl;
        break;
    case 3:
        cout << "Se Shanbe" << endl;
        break;
    case 4:
        cout << "Char Shanbe" << endl;
        break;
    case 5:
        cout << "Panj Shanbe" << endl;
        break;
    default:
        cout << "Jomee" << endl;

}
```

```cpp
char c;
cin >> c;
switch (c) {
    case 'a':
        cout << "First Case" << endl;
        break;
    case 'b':
        cout << "Second Case" << endl;
        break;
    default:
        cout << "Default Case" << endl;
}

// input: a
// output: First Case

// input: b
// output: Second Case

// input: K
// output: Default Case
```

اما اگر به عنوان مثال در کد بالا در `case` اول از `break;` استفاده نکنیم، پس از اجرا شدن `case` اول، کیس دوم نیز اجرا می
شود.

=== "input: a"

    ```cpp linenums="1" hl_lines="4-8"
    char c;
    cin >> c;
    switch (c) {
        case 'a':
            cout << "First Case" << endl;
        case 'b':
            cout << "Second Case" << endl;
            break;
        default:
            cout << "Default Case" << endl;
    }
    ```

    در کد بالا اگر ورودی برابر با 'a' باشد، هر دو کیس هایلایت شده اجرا می شود یعنی خروجی برابر است با:
    ```
    First Case
    Second Case
    ```

=== "input: b"

    ```cpp linenums="1" hl_lines="6-8"
    char c;
    cin >> c;
    switch (c) {
        case 'a':
            cout << "First Case" << endl;
        case 'b':
            cout << "Second Case" << endl;
            break;
        default:
            cout << "Default Case" << endl;
    }
    ```

    و در این حالت خروجی برابر است با:
    ```
    Second Case
    ```

