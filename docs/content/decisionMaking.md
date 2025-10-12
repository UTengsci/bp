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
برای 


