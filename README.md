# ArekMalang.co - Portal Berita Malang Raya

Portal berita modern dengan tema navy-putih yang elegan dan profesional.

![ArekMalang.co Preview](https://images.unsplash.com/photo-1504711434969-e33886168f5c?w=1200&h=600&fit=crop)

## 🎨 Design System

### Warna
- **Primary Navy**: `#1e3a8a` - Warna utama brand
- **Secondary Navy**: `#1e40af` - Hover states
- **Accent Blue**: `#3b82f6` - Highlights
- **Background**: `#ffffff` - Clean white
- **Text Primary**: `#0f172a` - Almost black
- **Text Secondary**: `#64748b` - Slate gray

### Typography
- **Font**: Inter (Google Fonts)
- **Headings**: Bold, tight letter-spacing
- **Body**: Regular, comfortable line-height

## 🚀 Quick Start

### 1. Install Dependencies
```bash
cd arekmalang-co
npm install
```

### 2. Run Development Server
```bash
npm run dev
```

Buka [http://localhost:3000](http://localhost:3000)

### 3. Build for Production
```bash
npm run build
```

Output ada di folder `dist/` (static export)

## 📁 Struktur Folder

```
arekmalang-co/
├── app/                 # Next.js App Router
│   ├── globals.css     # Global styles
│   ├── layout.tsx      # Root layout
│   └── page.tsx        # Homepage
├── components/         # React components
│   ├── ui/            # UI primitives (Button, Badge)
│   ├── navigation.tsx # Header & nav
│   ├── hero-section.tsx
│   ├── trending-section.tsx
│   ├── latest-section.tsx
│   └── footer.tsx
├── lib/               # Utilities & data
│   ├── utils.ts       # Helper functions
│   └── data.ts        # Mock articles data
├── types/             # TypeScript types
├── public/            # Static assets
└── dist/             # Build output
```

## 🎯 Fitur Utama

### 1. Navigation
- Sticky header dengan backdrop blur
- Kategori dropdown (desktop)
- Mobile hamburger menu
- Search & notification icons

### 2. Hero Section
- Featured article besar dengan overlay gradient
- Side articles compact
- Newsletter signup card

### 3. Trending Section
- Top 5 berita populer
- Counter ranking (01, 02, 03...)
- View count & read time

### 4. Latest Articles
- Filter by category
- Grid layout responsive
- Hover animations
- Load more button

### 5. Footer
- 4-column layout
- Social links
- Contact information
- Quick links

## 📝 Cara Menambahkan Artikel

Saat ini menggunakan mock data di `lib/data.ts`:

```typescript
export const articles: Article[] = [
  {
    id: '11',
    title: 'Judul Artikel Baru',
    excerpt: 'Ringkasan singkat...',
    slug: 'judul-artikel-baru',
    coverImage: 'https://images.unsplash.com/...',
    category: 'Kategori',
    author: 'Nama Penulis',
    publishedAt: '2024-02-12T10:00:00Z',
    readTime: 5,
    featured: true,  // Tampil di hero
    trending: true,  // Tampil di trending
  },
  // ...
]
```

## 🔄 Integrasi CMS (Next Step)

Untuk dashboard CMS seperti WordPress, rekomendasi:

### Option A: Sanity.io (Recommended)
- Headless CMS fully managed
- Real-time editing
- Free tier generous
- GROQ query language

### Option B: Strapi
- Self-hosted
- Full control
- PostgreSQL database
- REST/GraphQL API

### Option C: MDX Files
- Static generation
- Version control
- No database needed
- Perfect for small team

## 🛠️ Tech Stack

- **Framework**: Next.js 14 (App Router)
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **UI Components**: Custom + Lucide icons
- **Build Output**: Static Export

## 📱 Responsive Breakpoints

- **Mobile**: < 640px (1 column)
- **Tablet**: 640px - 1024px (2 columns)
- **Desktop**: > 1024px (3 columns)
- **Large**: > 1280px (max-width container)

## 🎨 Customization

### Ganti Warna
Edit `tailwind.config.ts`:
```typescript
colors: {
  arek: {
    primary: '#warna-baru',
    secondary: '#warna-hover',
  }
}
```

### Tambah Kategori
Edit `lib/data.ts`:
```typescript
export const categories: Category[] = [
  { id: '9', name: 'Kategori Baru', slug: 'kategori-baru', count: 0 },
  // ...
]
```

## 📄 License

MIT License - Feel free to use for your own news portal!

---

**Dibuat dengan ❤️ untuk Arek Malang**
