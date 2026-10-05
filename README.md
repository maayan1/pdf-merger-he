# איחוד קבצי PDF | PDF Merger (Hebrew UI)

כלי קליל וחד-מטרתי לאיחוד כמה קבצי PDF לקובץ אחד — **רץ כולו בדפדפן, בלי שרת, בלי העלאת קבצים לאינטרנט.**

A small, single-purpose tool for merging multiple PDF files into one — **runs entirely in the browser, no server, no upload.**

## למה בניתי את זה | Why

הייתי צריכה לאחד כמה PDF-ים אישיים בלי להעלות אותם לאתר חיצוני כלשהו — גם לא ל-CDN. הפתרונות הקיימים דרשו העלאה לשרת, אז בניתי כלי משלי עם דרישה ברורה: **אפס קריאות רשת, גם לא לטעינת ספריות**. בדקתי את זה בפועל — ניתוק מלא של האינטרנט ועדיין איחוד מוצלח של קבצים.

I needed to merge personal PDFs without uploading them anywhere — not even to a CDN. Existing tools required a server upload, so I built my own with one hard requirement: **zero network requests, including for loading libraries**. I verified this empirically by disconnecting the internet entirely and confirming the merge still works.

## יכולות | Features

- בחירת כמה קבצי PDF בבת אחת
- סידור מחדש של סדר הקבצים לפני האיחוד (↑ / ↓)
- הסרת קובץ מהרשימה, ניקוי הרשימה
- הודעות סטטוס נגישות (`aria-live`) להצלחה/שגיאה
- טיפול בקבצי PDF פגומים/מוגנים עם הודעת שגיאה מפורשת וברורה (כולל הנחיה מעשית: הדפסה ל-"Microsoft Print to PDF" ליצירת עותק תקין)
- תמיכה מלאה ב-RTL ועברית
- **ספריית [`pdf-lib`](https://github.com/Hopding/pdf-lib) מוטמעת מקומית בריפו (`lib/pdf-lib.min.js`) ולא נטענת מ-CDN** — כדי שהכלי יעבוד גם במחשב מנותק לחלוטין מהאינטרנט, ללא שום תלות ברשת, אפילו לא בהרצה הראשונה

## איך זה עובד | How it works

כל הלוגיקה ב-Vanilla JavaScript (ללא framework): `PDFDocument.load` לכל קובץ, `copyPages` לדף היעד המאוחד, ו-`Blob` + `URL.createObjectURL` כדי להפעיל הורדה בצד הלקוח. אין `fetch`, אין קריאת API, ואין תלות ברשת — גם לא לספריית ה-PDF עצמה, שמוטמעת מקומית בקובץ `lib/pdf-lib.min.js`.

All logic is plain JavaScript (no framework): each file is loaded with `PDFDocument.load`, pages are copied into one output document with `copyPages`, and the result is served as a client-side download via `Blob` + `URL.createObjectURL`. There is no `fetch`, no API call, and no network dependency at all — not even for the PDF library itself, which is vendored locally in `lib/pdf-lib.min.js` rather than pulled from a CDN.

## הרצה | Run it

פשוט לפתוח את `index.html` בדפדפן — אין build step ואין התקנה.

Just open `index.html` in a browser — no build step, no install.

```bash
git clone https://github.com/maayan1/pdf-merger-he.git
cd pdf-merger-he
open index.html   # or just double-click the file
```

## נבנה בעזרת AI | Built with AI-assisted development

הפרויקט פותח בעבודה משולבת עם עוזר AI (ChatGPT), תוך שאני מכתיבה את הדרישות הקשות: קובץ עצמאי, אפס תלות ברשת, ובדיקה אמפירית בפועל (ניתוק אינטרנט) לפני אישור. זו הדרך שבה אני עובדת: משתמשת ב-AI כדי להאיץ מימוש, אבל שומרת על בקרה מלאה על הדרישות, הארכיטקטורה, ואימות שהתוצאה עומדת בהן.

Built in collaboration with an AI assistant (ChatGPT), while I drove the hard requirements myself: a self-contained file, zero network dependency, and empirical verification (disconnecting the internet) before accepting the result. This reflects how I actually work: using AI to speed up implementation, while staying in control of the requirements, the architecture, and verifying the result actually meets them.

## רישיון | License

MIT — ראו [LICENSE](LICENSE).
