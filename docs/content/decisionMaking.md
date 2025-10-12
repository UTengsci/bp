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
