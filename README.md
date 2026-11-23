# The Third Master | Tech

דף הנחיתה של **המאסטר השלישי — AI לצוותים טכנולוגיים**.
כתובת יעד: **https://tech.thirdmaster.com**

אתר סטטי נפרד מהאתר הפיננסי (www.thirdmaster.com, ריפו `ThirdMaster`), שומר על סימן המותג המשותף (טבעת + קו + נקודה כתומה) עם זהות טכנולוגית משלו (navy + lime).

## מבנה
| קובץ | תפקיד |
|---|---|
| `index.html` | דף הנחיתה — אותו עיצוב ומבנה כמו www.thirdmaster.com, עם תוכן טכנולוגי. הטופס שולח דרך FormSubmit כמו באתר הראשי |
| `api/contact.js` | פונקציית Vercel לשליחת טופס הפנייה במייל (אותו מנגנון כמו באתר הראשי) |
| `og-image.png` | תמונת שיתוף 1200×630 (נוצרת מ־`tools/og-image.html`) |
| `robots.txt`, `sitemap.xml` | אינדוקס |
| `vercel.json` | הגדרות פריסה |

## פריסה ב־Vercel
1. Vercel → **Add New → Project** → לבחור את הריפו הזה (פרויקט חדש, לא את הפרויקט של האתר הראשי).
2. Framework Preset: **Other**, בלי Build Command.
3. Settings → **Environment Variables** — להעתיק מהפרויקט הראשי אחד מאלה:
   - `GMAIL_USER` + `GMAIL_APP_PASSWORD` (מומלץ), או `RESEND_API_KEY`
   - אופציונלי: `CONTACT_TO` (ברירת מחדל: hadas@thirdmaster.com)
4. Settings → **Domains** → להוסיף `tech.thirdmaster.com`.

## DNS (אצל ספק הדומיין / ה־DNS של thirdmaster.com)
להוסיף רשומה אחת בלבד — לא לגעת ברשומות הקיימות של `@` ו־`www`:

| Type | Name / Host | Value | TTL |
|---|---|---|---|
| CNAME | `tech` | `cname.vercel-dns.com` | Auto / 3600 |

אם ה־DNS של הדומיין מנוהל ב־Vercel עצמו (Nameservers של Vercel) — הוספת הדומיין בשלב 4 יוצרת את הרשומה אוטומטית.
Vercel יציג את הערך המדויק במסך Domains; אם הוא שונה מהטבלה — הערך של Vercel קובע. תעודת SSL מונפקת אוטומטית.

## בדיקה אחרי פרסום
- https://tech.thirdmaster.com נטען עם HTTPS.
- שליחת טופס ניסיון ומייל מתקבל.
- בדיקת כרטיס שיתוף: https://www.opengraph.xyz/url/https%3A%2F%2Ftech.thirdmaster.com
- Google Search Console: להוסיף את הנכס ולהגיש את `sitemap.xml`.
