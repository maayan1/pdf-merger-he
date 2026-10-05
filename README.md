# איחוד קבצי PDF | PDF Merger (Hebrew UI)

כלי קליל וחד-מטרתי לאיחוד כמה קבצי PDF לקובץ אחד — **רץ כולו בדפדפן, בלי שרת, בלי העלאת קבצים לאינטרנט.**

A small, single-purpose tool for merging multiple PDF files into one — **runs entirely in the browser, no server, no upload.**

🔗 **[נסו את הכלי בלייב / Live demo](#)** _(יעודכן לאחר פרסום ל-GitHub Pages)_

![screenshot](docs/screenshot.png)

## למה בניתי את זה | Why

הייתי צריכה לאחד כמה PDF-ים בלי לשלוח מידע רגיש לאתר חיצוני כלשהו. הפתרונות הקיימים דרשו העלאה לשרת — אז בניתי כלי מקומי משלי: נפתח כקובץ HTML בודד, מעבד הכול בזיכרון הדפדפן, ולא יוצר אף קריאת רשת עם תוכן הקבצים.

I needed to merge a few PDFs without sending sensitive documents to a random third-party website. So I built a local tool instead: it opens as a single HTML file, does all the processing in-browser, and never sends file contents over the network.

## יכולות | Features

- בחירת כמה קבצי PDF בבת אחת (drag of files via the file picker)
- סידור מחדש של סדר הקבצים לפני האיחוד (↑ / ↓)
- הסרת קובץ מהרשימה, ניקוי הרשימה
- הודעות סטטוס נגישות (`aria-live`) להצלחה/שגיאה
- טיפול בקבצי PDF פגומים/מוגנים עם הודעת שגיאה מפורשת וברורה
- תמיכה מלאה ב-RTL ועברית
- אפס תלויות התקנה — טוען את [`pdf-lib`](https://github.com/Hopding/pdf-lib) מ-CDN ורץ מיד

## איך זה עובד | How it works

כל הלוגיקה ב-Vanilla JavaScript (ללא framework): `PDFDocument.load` לכל קובץ, `copyPages` לדף היעד המאוחד, ו-`Blob` + `URL.createObjectURL` כדי להפעיל הורדה בצד הלקוח — בלי לגעת בשרת כלל.

All logic is plain JavaScript (no framework): each file is loaded with `PDFDocument.load`, pages are copied into one output document with `copyPages`, and the result is served as a client-side download via `Blob` + `URL.createObjectURL`.

## הרצה | Run it

פשוט לפתוח את `index.html` בדפדפן — אין build step ואין התקנה.

Just open `index.html` in a browser — no build step, no install.

```bash
git clone https://github.com/maayan1/pdf-merger-he.git
cd pdf-merger-he
open index.html   # or just double-click the file
```

## נבנה בעזרת AI | Built with AI-assisted development

הפרויקט פותח בעבודה משולבת עם כלי AI (Claude) — מהגדרת הארכיטקטורה (קובץ-יחיד, ללא שרת, ללא תלויות מותקנות) ועד חידוד חוויית המשתמש וטיפול בשגיאות. זו הדרך שבה אני עובדת היום: שימוש ב-AI כדי להאיץ איטרציות, לשמור על קוד נקי, ולהתמקד בהחלטות העיצוב והארכיטקטורה.

Built in collaboration with an AI coding assistant (Claude) — from the architecture decision (single file, no backend, zero install dependencies) to UX polish and error handling. This reflects how I work day to day: using AI to speed up iteration while staying in control of design and architecture decisions.

## רישיון | License

MIT — ראו [LICENSE](LICENSE).
