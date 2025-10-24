# 🧱 شرح تقسيمة مشروع الـ Back-End (Node.js + Express + PostgreSQL)

## 📁 src/
> دي المجلد الرئيسي اللي بيضم كل الكود الخاص بالمشروع.

---

### 📁 config/
> يحتوي على ملفات الإعدادات (configuration files).  
> مثال: إعداد الاتصال بقاعدة البيانات أو إعداد JWT secret.

**الملفات المحتملة:**
- `db.js` → كود الاتصال بقاعدة بيانات PostgreSQL.  
- `jwtConfig.js` → إعداد المفاتيح الخاصة بالتوكن.  
- `cloudConfig.js` (اختياري) → إعدادات رفع الصور على Cloudinary مثلًا.

---

### 📁 controllers/
> يحتوي على كل الـ **business logic** — يعني الفانكشن اللي بتنّفذ الأوامر بعد الـ request.

**الملفات المحتملة:**
- `userController.js` → تسجيل دخول، تسجيل مستخدم، تحديث بيانات...  
- `transactionController.js` → إضافة / حذف / عرض معاملات.

كل Controller بيتعامل مع الـ Model أو DB مباشرة.

---

### 📁 models/
> يحتوي على تعريفات الـ **database tables** أو ORM models.  
> يعني كل ملف بيمثل جدول في قاعدة البيانات.

**الملفات المحتملة:**
- `userModel.js` → تعريف جدول المستخدمين.  
- `transactionModel.js` → تعريف جدول العمليات.  

لو بتستخدمي ORM زي Prisma أو Sequelize، هنا بيتحط الـ schema أو الـ model definition.

---

### 📁 routes/
> يحتوي على كل الـ **API endpoints**.  
> كل Route بيربط بين الـ URL والفانكشن المناسبة في الـ controller.

**الملفات المحتملة:**
- `userRoutes.js` → /api/users/login - /api/users/register  
- `transactionRoutes.js` → /api/transactions/all

---

### 📁 middleware/
> يحتوي على كل الأكواد اللي بتتوسط بين الـ request والـ response (Middlewares).  
> زي التحقق من التوكن، أو الفاليديشن، أو التعامل مع الأخطاء.

**الملفات المحتملة:**
- `authMiddleware.js` → يتحقق من صلاحية الـ JWT Token.  
- `errorMiddleware.js` → يتعامل مع الأخطاء العامة.  
- 📁 `validation/` → مجلد فرعي خاص بفاليديشن كل Route.  
  - `userValidation.js` → شروط التسجيل وتسجيل الدخول.  
  - `transactionValidation.js` → شروط إضافة عملية جديدة.

---

### 📁 utils/
> يحتوي على أكواد مساعدة ممكن نحتاجها في أكتر من مكان (Utilities).  

**الملفات المحتملة:**
- `generateToken.js` → لتوليد JWT token.  
- `sendEmail.js` → لإرسال إيميل تأكيد أو استرجاع باسورد.  
- `formatDate.js` → لتنسيق التاريخ بشكل موحد.

---

### 📁 uploads/
> لو بتسمحي للمستخدمين يرفعوا صور أو ملفات.  
> المجلد ده بيحتوي على الملفات اللي تم رفعها (زي الصور أو المرفقات).

---

### 📄 app.js
> بيحتوي على كل إعدادات التطبيق (Express app):  
> - الـ middlewares  
> - الـ routes  
> - الـ error handling  
> - الإعدادات العامة  

ويتم تصديره إلى `server.js`.

---

### 📄 server.js
> نقطة التشغيل الأساسية للتطبيق.  
> - بيتصل بقاعدة البيانات.  
> - بيبدأ تشغيل السيرفر على البورت المحدد.  
> - بيستورد `app` من `app.js`.

---

### 📄 .env
> يحتوي على البيانات الحساسة اللي مش المفروض تتنشر أونلاين:
```
PORT=5000
DATABASE_URL=postgresql://username:password@localhost:5432/dbname
JWT_SECRET=mySuperSecretKey
```

---

### 📄 .gitignore
> بيمنع ملفات معينة من الرفع على GitHub  
(زي `node_modules`, `.env`, و `uploads`)

---

### 📄 package.json
> فيه كل تفاصيل المشروع:  
> - اسم المشروع  
> - إصدارات الـ packages  
> - أوامر التشغيل (scripts)

---

### 📄 README.md
> ملف بيشرح باختصار فكرة المشروع، إزاي يتشغّل، والمتطلبات اللي بيحتاجها.
