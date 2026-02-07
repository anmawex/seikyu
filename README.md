<p align="center">
  <img src="public/logo-seikyu.svg" alt="SEIKYU Logo" width="120" />
</p>

<h1 align="center">SEIKYU</h1>

<p align="center">
  <strong>Minimalist Financial Management System for Freelancers & Small Businesses</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Vue-3.4-42b883?style=flat-square&logo=vue.js" alt="Vue 3" />
  <img src="https://img.shields.io/badge/PrimeVue-4.5-0096FF?style=flat-square" alt="PrimeVue" />
  <img src="https://img.shields.io/badge/Supabase-Backend-3ECF8E?style=flat-square&logo=supabase" alt="Supabase" />
  <img src="https://img.shields.io/badge/TailwindCSS-4.1-38BDF8?style=flat-square&logo=tailwindcss" alt="TailwindCSS" />
  <img src="https://img.shields.io/badge/Vite-5.3-646CFF?style=flat-square&logo=vite" alt="Vite" />
  <img src="https://img.shields.io/badge/Status-MVP%20Beta-orange?style=flat-square" alt="Status" />
</p>

<p align="center">
  <a href="#-features">Features</a> •
  <a href="#-quick-start">Quick Start</a> •
  <a href="#-project-structure">Project Structure</a> •
  <a href="#%EF%B8%8F-tech-stack">Tech Stack</a> •
  <a href="#-deployment">Deployment</a>
</p>

<p align="center">
  <strong>🌐 Language / Idioma:</strong><br/>
  <a href="./README.md">🇺🇸 English</a> •
  <a href="./README.es.md">🇪🇸 Español</a>
</p>

---

## 📝 About

**SEIKYU** (請求 - Japanese for "billing/invoice") is a modern, lightweight financial management application designed for freelancers and small businesses. It provides an intuitive interface for managing clients, creating professional invoices, and tracking payments — all powered by a real-time Supabase backend.

Currently in **MVP Beta**, SEIKYU offers a streamlined solution to replace complex spreadsheets and expensive software, helping you focus on what matters: growing your business.

---

## ✨ Features

### 🏠 Landing Page
- Modern, responsive landing page with smooth animations
- Multi-language support (English/Spanish)
- Light/Dark theme toggle
- Interactive pricing section with access request modal
- Privacy Policy & Terms of Service pages

### 🔐 Authentication
- Secure email/password authentication via Supabase Auth
- Session persistence with automatic token refresh
- Protected routes with navigation guards
- Role-based access control (admin routes)

### 👥 Client Management (CRM)
- Full CRUD operations for client management
- Track contact details, company, and status
- Client detail view with financial summary
- View associated invoices and payment history
- Active/Inactive status management

### 📄 Smart Invoicing
- Create professional invoices with multiple line items
- Automatic balance calculations
- Multiple invoice statuses: `Draft`, `Sent`, `Pending`, `Partial Payment`, `Paid`, `Overdue`, `Cancelled`
- Due date tracking with overdue alerts
- Invoice cancellation workflow

### 💰 Payment Tracking
- Record full and partial payments
- Multiple payment methods: Transfer, Cash, Credit Card, Check
- Real-time balance updates
- Complete payment history with transaction details
- Revenue statistics and metrics

### 📊 Dashboard & Analytics
- Real-time business metrics overview
- Total Receivable & Outstanding Balance
- Monthly collection tracking
- Active clients and engagement rate
- Interactive invoice status distribution chart (Chart.js)
- Pending invoices requiring immediate action

### 🌐 Internationalization (i18n)
- Full support for **English** and **Spanish**
- Language switcher in navbar and app configurator
- All UI elements, messages, and legal pages translated

### 🎨 Modern UI/UX
- Built with PrimeVue component library (Aura theme)
- TailwindCSS for custom styling
- Dark mode support
- Responsive design (desktop & mobile)
- Smooth animations and transitions
- Toast notifications and confirmation dialogs

---

## 🚀 Quick Start

### Prerequisites

- **Node.js** 18+ 
- **npm** or **yarn**
- **Supabase** account ([Create one free](https://supabase.com))

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/seikyu.git
   cd seikyu
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**
   
   Copy the example environment file:
   ```bash
   cp .env.example .env
   ```
   
   Edit `.env` and add your Supabase credentials:
   ```env
   VITE_SUPABASE_URL=https://your-project.supabase.co
   VITE_SUPABASE_KEY=your-anon-key
   ```
   
   > 📍 Find these values in your [Supabase Dashboard](https://app.supabase.com) under **Project Settings > API**

4. **Set up Supabase Database**
   
   Create the following tables in your Supabase project:
   - `clients` - Client information (name, email, phone, company, status)
   - `invoices` - Invoice data (client_id, number, date, due_date, status, items)
   - `payments` - Payment records (invoice_id, amount, method, date, note)
   
   > ⚠️ Make sure to configure **Row Level Security (RLS)** policies for authenticated users.

5. **Run the development server**
   ```bash
   npm run dev
   ```

6. **Open your browser**
   
   Navigate to `http://localhost:5173`

---

## 📁 Project Structure

```
seikyu/
├── public/
│   ├── favicon.ico
│   └── logo-seikyu.svg
├── src/
│   ├── app/
│   │   ├── i18n/                 # Internationalization
│   │   │   ├── index.js
│   │   │   └── locales/
│   │   │       ├── en.json       # English translations
│   │   │       └── es.json       # Spanish translations
│   │   ├── layout/               # App layout components
│   │   │   ├── AppLayout.vue
│   │   │   ├── AppSidebar.vue
│   │   │   ├── AppTopbar.vue
│   │   │   └── AppConfigurator.vue
│   │   ├── pages/                # App-level pages
│   │   │   ├── Landing.vue
│   │   │   ├── NotFound.vue
│   │   │   ├── PrivacyPolicy.vue
│   │   │   └── TermsOfService.vue
│   │   └── router/               # Vue Router configuration
│   │       └── index.js
│   ├── features/
│   │   ├── auth/                 # Authentication module
│   │   │   ├── pages/
│   │   │   │   ├── Login.vue
│   │   │   │   ├── Access.vue    # Access Denied page
│   │   │   │   └── Error.vue
│   │   │   └── store/
│   │   │       └── auth.js       # Pinia auth store
│   │   ├── clients/              # Client management
│   │   │   └── views/
│   │   │       ├── ClientsPage.vue
│   │   │       └── ClientDetails.vue
│   │   ├── dashboard/            # Dashboard module
│   │   │   └── pages/
│   │   │       └── Dashboard.vue
│   │   ├── docs/                 # Documentation page
│   │   │   └── pages/
│   │   │       └── Documentation.vue
│   │   ├── home/                 # Landing page components
│   │   │   └── components/
│   │   │       ├── TopbarWidget.vue
│   │   │       ├── HeroWidget.vue
│   │   │       ├── FeaturesWidget.vue
│   │   │       ├── HighlightsWidget.vue
│   │   │       ├── PricingWidget.vue
│   │   │       └── FooterWidget.vue
│   │   ├── invoices/             # Invoice management
│   │   │   └── views/
│   │   │       ├── InvoicesPage.vue
│   │   │       └── InvoiceDetails.vue
│   │   └── payments/             # Payment tracking
│   │       └── views/
│   │           └── PaymentsPage.vue
│   ├── shared/                   # Shared components & utilities
│   ├── assets/
│   │   ├── styles.scss           # Global SCSS styles
│   │   └── tailwind.css          # Tailwind configuration
│   ├── App.vue                   # Root component
│   ├── main.js                   # Application entry point
│   └── supabase.js               # Supabase client configuration
├── .env.example                  # Environment variables template
├── index.html                    # HTML entry point
├── package.json
├── vercel.json                   # Vercel deployment config
└── vite.config.mjs               # Vite configuration
```

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| [Vue 3](https://vuejs.org/) | Progressive JavaScript Framework (Composition API) |
| [Vite](https://vitejs.dev/) | Next-generation frontend build tool |
| [PrimeVue 4](https://primevue.org/) | Premium UI Component Library (Aura Theme) |
| [Pinia](https://pinia.vuejs.org/) | State Management for Vue |
| [Vue Router 4](https://router.vuejs.org/) | Official Router for Vue.js |
| [Vue I18n](https://vue-i18n.intlify.dev/) | Internationalization plugin |
| [Supabase](https://supabase.com/) | Backend-as-a-Service (Auth, Database, RLS) |
| [TailwindCSS 4](https://tailwindcss.com/) | Utility-first CSS framework |
| [Chart.js](https://www.chartjs.org/) | JavaScript charting library |
| [PrimeIcons](https://primevue.org/icons/) | Icon library |

---

## 📜 Available Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server with hot-reload |
| `npm run build` | Build for production |
| `npm run preview` | Preview production build locally |
| `npm run lint` | Run ESLint to check and fix code issues |

---

## 🌐 Deployment

### Vercel (Recommended)

SEIKYU is configured for seamless deployment on **Vercel**:

1. Push your code to GitHub
2. Import the repository in [Vercel](https://vercel.com)
3. Add environment variables:
   - `VITE_SUPABASE_URL`
   - `VITE_SUPABASE_KEY`
4. Deploy!

The `vercel.json` is already configured for SPA routing.

### Other Platforms

For other platforms (Netlify, Railway, etc.), ensure:
- SPA redirect rules are configured (`/* → /index.html`)
- Environment variables are properly set

---

## 🔒 Security Notes

- ⚠️ **Never commit** your `.env` file to version control
- The `.env` file is already listed in `.gitignore`
- Use `.env.example` as a template for collaborators
- Keep your Supabase keys secure
- Configure proper **RLS policies** in Supabase for production

---

## 🗺️ Roadmap

- [ ] Email notifications for overdue invoices
- [ ] PDF invoice generation and export
- [ ] Recurring invoices
- [ ] Client portal for invoice viewing
- [ ] Multi-currency support
- [ ] Advanced reporting and analytics
- [ ] Mobile app (Vue Native / Capacitor)

---

## 👤 Author

Developed with ❤️ by **Angel Mawex**

- 🌐 [Portfolio](https://angelmawex.dev)
- 💼 [LinkedIn](https://linkedin.com/in/angelmawex)
- 🐙 [GitHub](https://github.com/angelmawex)

---

## 📄 License

This project is proprietary software. All rights reserved.

See [Privacy Policy](/privacy) and [Terms of Service](/terms) for more information.

---

<p align="center">
  <strong>SEIKYU</strong> © 2026 — Streamline Your Business
</p>
