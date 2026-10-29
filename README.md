# תקציב חיה ויואל

## העלאה ל-GitHub והפעלה כאתר
1. ב-github.com: New repository, שם למשל `budget`, Public, Create.
2. Add file ← Upload files. גררו את **כל הקבצים מהתיקייה** (index.html, config.js, sw.js, manifest.webmanifest וארבעת קבצי ה-png, לא את התיקייה עצמה). Commit changes.
3. Settings ← Pages ← Source: Deploy from a branch ← Branch: main, תיקייה / (root) ← Save.
4. אחרי דקה-שתיים הכתובת תהיה `https://שם-המשתמש.github.io/budget/`.

## התקנה בטלפון
- אייפון (Safari): שיתוף ← הוספה למסך הבית.
- אנדרואיד (Chrome): ⋮ ← התקנת אפליקציה / הוספה למסך הבית.

## סנכרון בין יואל וחיה (Firebase, חינמי)
בלי השלבים האלה כל טלפון שומר נתונים רק אצלו.
1. console.firebase.google.com ← Add project.
2. Build ← Authentication ← Get started ← Sign-in method ← Anonymous ← Enable.
3. Build ← Firestore Database ← Create database (Production mode, בחרו מיקום אירופה).
4. ב-Rules הדביקו ולחצו Publish:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /families/{code}/{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```
5. Project settings ← Your apps ← אייקון Web (</>) ← Register app. העתיקו את הערכים apiKey, authDomain, projectId, appId אל `config.js` ב-GitHub (עריכה ← Commit).
6. בשני הטלפונים תתבקשו להזין **אותו קוד סנכרון** (המצאו קוד ארוך). הוא מגן על הנתונים, ולכן לא שומרים אותו ב-GitHub.
