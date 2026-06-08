# Wegagen PLC — Corporate Website

A complete, production-ready corporate website for **Wegagen PLC**, built with React + Vite + Tailwind CSS.

---

## Tech Stack

| Tool | Version | Purpose |
|------|---------|---------|
| React | 18 | UI framework |
| Vite | 5 | Build tool & dev server |
| Tailwind CSS | 3 | Utility-first styling |
| React Router DOM | 6 | Client-side routing |
| Framer Motion | 11 | Animations |
| React Icons | 5 | Icon library |
| React CountUp | 6 | Animated counters |
| React Intersection Observer | 9 | Scroll triggers |

---

## Project Structure

```
wegagen-plc/
├── public/
│   └── favicon.svg
├── src/
│   ├── assets/               # Static images (if any local)
│   ├── components/
│   │   ├── AnimatedSection.jsx   # Scroll-triggered animation wrapper
│   │   ├── CTASection.jsx        # Reusable call-to-action band
│   │   ├── Footer.jsx            # Site-wide footer
│   │   ├── Navbar.jsx            # Sticky responsive navbar + mobile menu
│   │   ├── NewsCard.jsx          # News / press article card
│   │   ├── PageBanner.jsx        # Inner-page hero banner with breadcrumbs
│   │   ├── ScrollToTop.jsx       # Route-reset + floating back-to-top button
│   │   ├── ServiceCard.jsx       # Service overview card
│   │   ├── StatsCounter.jsx      # Animated statistics counter strip
│   │   ├── TeamCard.jsx          # Leadership team member card
│   │   └── TestimonialCard.jsx   # Client testimonial card
│   ├── data/
│   │   ├── company.js            # Company info, services, leadership, stats…
│   │   └── news.js               # News articles, jobs, financials
│   ├── layouts/
│   │   └── MainLayout.jsx        # Navbar + page transitions + Footer wrapper
│   ├── pages/
│   │   ├── Home.jsx              # Landing page (all sections)
│   │   ├── About.jsx             # Company history, values, team, milestones
│   │   ├── Services.jsx          # Detailed service line pages
│   │   ├── Investors.jsx         # Annual reports, financials, governance
│   │   ├── News.jsx              # Filterable news grid
│   │   ├── Careers.jsx           # Culture, benefits, job listings
│   │   ├── Contact.jsx           # Contact form + map embed
│   │   └── NotFound.jsx          # 404 page
│   ├── styles/                   # (reserved for extra CSS modules)
│   ├── App.jsx                   # Route definitions
│   ├── main.jsx                  # React DOM entry point
│   └── index.css                 # Tailwind directives + global styles
├── index.html
├── package.json
├── tailwind.config.js
├── postcss.config.js
├── vite.config.js
└── README.md
```

---

## Pages Included

| Route | Page |
|-------|------|
| `/` | Home (Hero, Stats, Intro, Services, Why Us, Testimonials, News, Partners, CTA) |
| `/about` | About (Mission/Vision, Values, Milestones timeline, Leadership) |
| `/services` | Services (6 detailed business lines with stats) |
| `/investors` | Investor Relations (Financials, Annual Reports, Governance) |
| `/news` | News & Press Releases (filterable by category) |
| `/careers` | Careers (Culture, Benefits, Job listings) |
| `/contact` | Contact (Form, map embed, contact info) |
| `*` | 404 Not Found |

---

## Getting Started

### Prerequisites

- **Node.js** ≥ 18.0.0
- **npm** ≥ 9.0.0

### Installation

```bash
# 1. Clone or extract the project folder
cd wegagen-plc

# 2. Install dependencies
npm install

# 3. Start the development server
npm run dev
```

The site will be available at **http://localhost:5173**

### Build for Production

```bash
npm run build
```

Output is placed in the `dist/` folder — ready to deploy.

### Preview Production Build Locally

```bash
npm run preview
```

---

## Customisation

### Company Information
All company data lives in **`src/data/company.js`** and **`src/data/news.js`**.  
Edit these files to update:
- Company name, address, phone, email
- Statistics (assets, employees, etc.)
- Leadership team (names, photos, bios)
- Services
- News articles & job listings
- Financial highlights

### Colours
Primary palette is defined in **`tailwind.config.js`**:
```js
navy: { 950: '#060f21', 900: '#0b1d3e', … }
gold: { 500: '#e8b820', 400: '#f5c842', … }
```

### Logo
Replace the `W` lettermark in **`Navbar.jsx`** and **`Footer.jsx`** with an `<img>` tag pointing to your actual logo file placed in `public/`.

### Contact Form
The contact form in **`src/pages/Contact.jsx`** is pre-wired for [Formspree](https://formspree.io).  
Replace the fetch URL:
```js
// In Contact.jsx handleSubmit()
const res = await fetch('https://formspree.io/f/YOUR_FORM_ID', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify(form),
})
```

---

## Deployment

### Vercel (Recommended)

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy from project root
vercel

# For production deployment
vercel --prod
```

Or connect your GitHub repo to [vercel.com](https://vercel.com) and it auto-deploys on every push.

> **Vercel settings**: Framework preset = **Vite**, Build command = `npm run build`, Output directory = `dist`

### Netlify

```bash
# Install Netlify CLI
npm i -g netlify-cli

# Build first
npm run build

# Deploy
netlify deploy --prod --dir=dist
```

Or drag-and-drop the `dist/` folder at [app.netlify.com](https://app.netlify.com).

Create a **`public/_redirects`** file for client-side routing:
```
/*  /index.html  200
```

### GitHub Pages

```bash
npm install --save-dev gh-pages
```

Add to `package.json`:
```json
"homepage": "https://yourusername.github.io/wegagen-plc",
"scripts": {
  "predeploy": "npm run build",
  "deploy": "gh-pages -d dist"
}
```

Update `vite.config.js`:
```js
export default defineConfig({ base: '/wegagen-plc/', plugins: [react()] })
```

Then run:
```bash
npm run deploy
```

---

## Environment Variables

No environment variables are required for the base setup.  
If you integrate Formspree or other services, create a `.env` file:

```env
VITE_FORMSPREE_ID=your_form_id
```

Access in code via `import.meta.env.VITE_FORMSPREE_ID`.

---

## Browser Support

Modern evergreen browsers (Chrome, Firefox, Safari, Edge).  
IE is not supported.

---

## License

© 2025 Wegagen PLC. All rights reserved.  
This codebase is proprietary and confidential.
