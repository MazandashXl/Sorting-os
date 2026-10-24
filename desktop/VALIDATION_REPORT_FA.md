# گزارش اعتبارسنجی سورس — SORTING OS

تاریخ بسته: 2026-10-18

## فرمان‌های اجراشده در محیط ساخت بسته

```bash
python -m py_compile desktop/main.py desktop/database.py desktop/accounting_core.py
cd desktop && python -W default -m unittest discover -s tests -v
```

## نتیجه مشاهده‌شده

- Syntax compile: PASS.
- Unit tests: 17/17 PASS (11 تست هسته حسابداری/واحد پول + 6 تست عملیاتی پایه).
- آزمون تبدیل ریال/تومان با ارقام فارسی، decimal تومان و عدم پذیرش کسر ریال: PASS.
- رد سند نامتوازن و مبلغ ریالی غیرصحیح، جلوگیری از source posting تکراری، برگشت با سند معکوس و عدم auto-post شدن فاکتور legacy: PASS.
- تراز آزمایشی، معادله ترازنامه، سود و زیان و تطبیق اولیه جریان نقد در fixtures مصنوعی: PASS.
- اجرای GUI روی دسکتاپ/چاپگر واقعی: NOT RUN.
- ساخت EXE/installer: NOT RUN.
- Windows 7 SP1 x64: NOT VERIFIED.
- تقویم شمسی، گزارش قانونی/مالیاتی، بسته‌شدن سال مالی، اتصال خودکار فاکتور/صافی/بانک/چک به دفترکل: NOT COMPLETE.

## محدوده گزارش

این گزارش نتیجه فرمان‌های اجراشده در محیط ساخت این بسته را نشان می‌دهد، نه تضمین سازگاری روی تمام رایانه‌ها. تست موفق هسته مالی، جایگزین بازبینی حسابدار، UAT و آزمون روی سیستم‌عامل هدف نیست.

## اجرای تکمیلی — 2026-10-25

محیط: Python 3.15.0, Windows 11 (10.0.22000), SQLite 3.53.4, Tk 9.0.

- Compile تمام 5 فایل Python با `py_compile`: PASS.
- `python -W default -m unittest discover -s tests -v` از پوشه `desktop`: 20/20 PASS.
- راه‌اندازی برنامه، ساخت داشبورد و بستن رابط با پایگاه‌داده موقت: PASS.
- اعتبارسنجی مقادیر NaN/Infinity، ویرایش شخص ناموجود و تکرار هویت در یک CSV به regression tests افزوده شد.
- بررسی 158 فایل Markdown و لینک‌های نسبی inline: 0 لینک شکسته.
- این نتایج روی Python 3.15/Windows 11 هستند؛ CI Python 3.8/3.11/3.12، Windows 7، ساخت EXE/installer، چاپ واقعی، UAT و restore همچنان `NOT RUN` یا `NOT VERIFIED`.
- همچنان باز: فرم فاکتور مقدار را در ستون legacy از نوع REAL نگه می‌دارد. تا تصویب سیاست و migration/reconciliation، این مبلغ برای دفترکل معتبر نیست و نباید خودکار به ریال تبدیل یا post شود.
