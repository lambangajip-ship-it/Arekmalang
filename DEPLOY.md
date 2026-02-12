# 🚀 Deployment Guide - ArekMalang.co

## Option 1: Vercel (Recommended - Easiest)

### Step 1: Install Vercel CLI
```bash
npm i -g vercel
```

### Step 2: Deploy
```bash
cd arekmalang-co
vercel
```

### Step 3: Follow prompts
- Login/create account
- Confirm project settings
- Auto-deploy!

**Hasil**: `https://arekmalang-co.vercel.app`

---

## Option 2: Netlify

### Drag & Drop (Super Simple)
1. Build project:
```bash
cd arekmalang-co
npm install
npm run build
```

2. Buka folder `dist/`

3. Login [netlify.com](https://netlify.com)

4. Drag folder `dist/` ke dashboard Netlify

**Done!** Dapat URL instant.

### Via CLI
```bash
npm install -g netlify-cli
cd arekmalang-co
netlify deploy --prod --dir=dist
```

---

## Option 3: GitHub Pages (Free)

### Setup Repository
1. Buat repo baru: `arekmalang-co`
2. Push code ke GitHub

### Enable GitHub Pages
1. Settings → Pages
2. Source: GitHub Actions
3. Tambah workflow file `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: 18
      - run: npm ci
      - run: npm run build
      - uses: actions/upload-pages-artifact@v2
        with:
          path: ./dist

  deploy:
    needs: build
    permissions:
      pages: write
      id-token: write
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - uses: actions/deploy-pages@v2
```

---

## Option 4: Custom Domain (Cpanel/Shared Hosting)

### Build Locally
```bash
cd arekmalang-co
npm install
npm run build
```

### Upload ke Hosting
1. Compress folder `dist/` jadi ZIP
2. Login Cpanel → File Manager
3. Upload ke `public_html/` atau subdomain folder
4. Extract ZIP
5. Done!

### htaccess (jika perlu)
Buat file `.htaccess` di root:
```apache
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /
  RewriteRule ^index\.html$ - [L]
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule . /index.html [L]
</IfModule>
```

---

## 📝 Checklist Pre-Deploy

- [ ] Ganti mock data dengan konten real
- [ ] Update metadata SEO di `app/layout.tsx`
- [ ] Ganti favicon (buat file `app/favicon.ico`)
- [ ] Test responsive di mobile
- [ ] Cek semua links berfungsi
- [ ] Optimize images (compress)
- [ ] Setup Google Analytics
- [ ] Setup Search Console

---

## 🔧 Environment Variables (untuk CMS)

Jika pakai Sanity/Strapi, buat file `.env.local`:

```env
# Sanity
NEXT_PUBLIC_SANITY_PROJECT_ID=your_project_id
NEXT_PUBLIC_SANITY_DATASET=production
SANITY_API_TOKEN=your_token

# atau Strapi
NEXT_PUBLIC_STRAPI_URL=https://your-strapi-url.com
```

**Jangan commit `.env.local` ke Git!**

---

## 🎯 Performance Tips

1. **Image Optimization**
   - Gunakan format WebP
   - Lazy loading
   - Proper sizing

2. **Code Splitting**
   - Next.js otomatis handle
   - Dynamic imports untuk heavy components

3. **Caching**
   - Vercel/Netlify auto-cache
   - Custom headers untuk static assets

4. **Analytics**
   - Vercel Analytics (built-in)
   - Google Analytics 4
   - Hotjar untuk heatmap

---

## 🆘 Troubleshooting

### Build Error
```bash
# Clear cache
rm -rf .next dist node_modules
npm install
npm run build
```

### Images not loading
- Cek URL image valid
- CORS headers di server image
- Gunakan domain whitelist di `next.config.js`

### Routing 404
- Pastikan `output: 'export'` di `next.config.js`
- Untuk dynamic routes, gunakan `generateStaticParams()`

---

**Selamat! Website ArekMalang.co siap online! 🎉**
