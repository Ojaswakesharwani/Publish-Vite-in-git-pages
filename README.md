# 🚀 Deploy Vite Project to GitHub Pages

This guide explains how to deploy a **Vite** project to **GitHub Pages** step by step.

---

## 1. Push Your Code to GitHub
1. Create a new repository on [GitHub](https://github.com/).
2. Push your Vite project code to this repository.

---

## 2. Configure `vite.config.js`
Add a `base` property with your repository name.  

```js
// vite.config.js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  base: "/<your-repo-name>/", // 👈 replace with your repo name
})

```


---

## 3. Update package.json
Add `homepage`, `predeploy`, and `deploy` scripts

```js

{
  "name": "your-project",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "homepage": "https://<your-username>.github.io/<your-repo-name>/", // 👈 replace with your repo details
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint .",
    "preview": "vite preview",
    "predeploy": "npm run build",      // 👈 build before deploying
    "deploy": "gh-pages -d dist"       // 👈 deploy dist folder to gh-pages branch
  }
}


```

## 4. Install Dependencies
Run the following commands:

```js

npm install gh-pages --save-dev
npm install

```

## 5. Build and Deploy

```js

npm run build
npm run deploy


```
This will create a `gh-pages` branch in your repository with the production-ready build.


## 6. Configure GitHub Pages
1. Go to your repository on GitHub.
2. Navigate to Settings > Pages.
3. Under Source, select Deploy from a branch.
4. Choose the `gh-pages` branch and save.
5. Your site will be available at:

```js
https://<your-username>.github.io/<your-repo-name>/
```
## ✅ Final Notes
1. Always set the correct base in vite.config.js.

2. The homepage field in package.json ensures GitHub Pages resolves the correct path.

3. If you face a white screen issue, double-check your base path.
