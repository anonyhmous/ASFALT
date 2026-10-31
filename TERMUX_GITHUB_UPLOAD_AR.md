# رفع مشروع ASPHALT V5 إلى GitHub من Termux

> لا تضع التوكن داخل الأمر أو رابط Git. إذا طلب Git كلمة المرور، أدخل Personal Access Token الجديد في خانة كلمة المرور فقط. لا ترسله في المحادثة ولا تحفظه في ملف عام.

```bash
pkg update -y
pkg install git unzip -y
termux-setup-storage
cd ~/storage/downloads
mkdir -p ASPHALT_V5
unzip -o ASPHALT_V5_Source.zip -d ASPHALT_V5
cd ASPHALT_V5

git init
git branch -M main
git add .
git commit -m "ASPHALT V5 source"
git remote add origin https://github.com/anonyhmous/ASFALT.git
git push -u origin main
```

عند ظهور طلب بيانات الدخول:
- Username: اسم حساب GitHub الصحيح.
- Password: الصق التوكن الجديد الذي أنشأته بنفسك على GitHub (وليس كلمة مرور الحساب).

بعد نجاح الرفع:
1. افتح المستودع `ASFALT` على GitHub.
2. افتح تبويب **Actions**.
3. افتح مهمة **Build ASPHALT V5 APK**.
4. انتظر أن تكون النتيجة خضراء.
5. افتح تشغيل المهمة ثم **Artifacts** ونزّل `asphalt-v5-debug-apk`.

إذا كان المستودع يحتوي ملفات قديمة وتريد استبدالها بالكامل، لا تستخدم `git push --force` تلقائيًا. راجع الملفات أولًا أو أنشئ مستودعًا فارغًا لتجنب حذف عمل سابق.
