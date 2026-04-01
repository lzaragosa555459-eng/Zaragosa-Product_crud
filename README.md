<img width="1919" height="1199" alt="Screenshot 2026-03-31 123327" src="https://github.com/user-attachments/assets/40174070-ac32-4c61-8351-0f013c9edd23" />


# ⚡ Fixing Vite Manifest Error in Laravel

## 📌 Overview

This guide explains how to fix the following error in Laravel:

```
Illuminate\Foundation\ViteManifestNotFoundException
Vite manifest not found at: public/build/manifest.json
```

This error occurs when Laravel cannot find the compiled frontend assets required by Vite.

---

## 💥 Cause of the Error

Laravel uses **Vite** to handle frontend assets like:

* CSS (e.g., Tailwind)
* JavaScript

In Blade files, this line:

```blade
@vite(['resources/css/app.css', 'resources/js/app.js'])
```

tells Laravel to load compiled assets.

❌ The error happens because:

* Vite has not been run
* `manifest.json` has not been generated

---

## 🧠 What is Vite?

Vite is a frontend build tool that:

* Compiles CSS and JavaScript
* Optimizes assets
* Generates a `manifest.json` file used by Laravel

---

## ✅ Step-by-Step Fix

### 🔹 Step 1: Open your project directory

```bash
cd C:\Users\Liz\product-crud
```

---

### 🔹 Step 2: Install Node dependencies

```bash
npm install
```

✔ This installs required frontend packages

---

### 🔹 Step 3: Run Vite (Development Mode)

```bash
npm run dev
```

✔ Starts Vite server
✔ Generates necessary files
✔ Watches for changes

---

### 🔹 Alternative: Build for Production

```bash
npm run build
```

✔ Creates optimized build files
✔ Generates `public/build/manifest.json`

---

### 🔹 Step 4: Run Laravel Server

```bash
php artisan serve
```

Then open:

```
http://127.0.0.1:8000/products
```

---

## 🔄 Recommended Workflow

During development, run both:

```bash
php artisan serve
npm run dev
```

* Laravel → backend server
* Vite → frontend assets

---

## ⚠️ Common Mistakes

### ❌ Running only:

```bash
php artisan serve
```

👉 This will NOT compile assets

---

### ❌ Missing Node.js

Make sure Node.js is installed:

```bash
node -v
npm -v
```

---

## 📁 Expected Output

After running Vite, this file should exist:

```
public/build/manifest.json
```

✔ This file resolves the error

---

## 🧩 Summary

* `@vite(...)` → loads frontend assets
* Vite must be running to generate assets
* Missing `manifest.json` = Vite not executed

---

## 🚀 Conclusion

The Vite manifest error is a common setup issue in Laravel projects. By installing dependencies and running Vite, you can quickly resolve it and continue development.

---

✨ Tip: Always run `npm run dev` alongside your Laravel server during development.
