# Tailwind CSS Setup Guide (Manual Setup for Windows)

This guide will help you set up Tailwind CSS manually in your project, bypassing issues with `npx init -p` on Windows.

---

## 1. Initialize Project

Open PowerShell and navigate to your project folder:

```powershell
cd "C:\Users\niket\OneDrive\Desktop\goal of 2027\tailwindcss"
```
Initialize npm (if not already done):

```powershell
npm init -y
```
## 2. Install Tailwind Locally
```powershell
npm install -D tailwindcss postcss autoprefixer
```
This creates node_modules and installs Tailwind CSS locally.

## 3. Create Configuration Files Manually
tailwind.config.js
```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./*.html"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```
postcss.config.js
```js
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```
## 4. Create CSS Entry File
Create a file named input.css:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```
## 5. Add Build Script
In package.json, under "scripts", add:

```json
"scripts": {
  "build:css": "tailwindcss -i ./input.css -o ./output.css --minify"
}
```
input.css → source Tailwind CSS

output.css → compiled CSS

## 6. Build Tailwind CSS
Run the build script in PowerShell:

```powershell
npm run build:css
```
This generates output.css which you can link in your HTML:

```html
<link rel="stylesheet" href="output.css">
```
## 7. Optional: Global Tailwind (if npx fails)
```powershell
npm install -g tailwindcss
tailwindcss -i ./input.css -o ./output.css --minify
```
This is a fallback to compile CSS without relying on npx.