<p align="center">
  <img src="public/logo-seikyu.svg" alt="SEIKYU Logo" width="120" />
</p>

<h1 align="center">SEIKYU</h1>

<p align="center">
  <strong>Sistema de Gestión Financiera Minimalista para Freelancers y Pequeños Negocios</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Vue-3.4-42b883?style=flat-square&logo=vue.js" alt="Vue 3" />
  <img src="https://img.shields.io/badge/PrimeVue-4.5-0096FF?style=flat-square" alt="PrimeVue" />
  <img src="https://img.shields.io/badge/Supabase-Backend-3ECF8E?style=flat-square&logo=supabase" alt="Supabase" />
  <img src="https://img.shields.io/badge/TailwindCSS-4.1-38BDF8?style=flat-square&logo=tailwindcss" alt="TailwindCSS" />
  <img src="https://img.shields.io/badge/Vite-5.3-646CFF?style=flat-square&logo=vite" alt="Vite" />
  <img src="https://img.shields.io/badge/Estado-MVP%20Beta-orange?style=flat-square" alt="Estado" />
</p>

<p align="center">
  <a href="#-características">Características</a> •
  <a href="#-inicio-rápido">Inicio Rápido</a> •
  <a href="#-estructura-del-proyecto">Estructura</a> •
  <a href="#%EF%B8%8F-stack-tecnológico">Tech Stack</a> •
  <a href="#-despliegue">Despliegue</a>
</p>

<p align="center">
  <strong>🌐 Language / Idioma:</strong><br/>
  <a href="./README.md">🇺🇸 English</a> •
  <a href="./README.es.md">🇪🇸 Español</a>
</p>

---

## 📝 Acerca de

**SEIKYU** (請求 - Japonés para "facturación") es una aplicación moderna y ligera de gestión financiera diseñada para freelancers y pequeños negocios. Proporciona una interfaz intuitiva para gestionar clientes, crear facturas profesionales y rastrear pagos — todo impulsado por un backend en tiempo real con Supabase.

Actualmente en **MVP Beta**, SEIKYU ofrece una solución simplificada para reemplazar hojas de cálculo complejas y software costoso, ayudándote a enfocarte en lo que importa: hacer crecer tu negocio.

---

## ✨ Características

### 🏠 Página de Inicio
- Landing page moderna y responsiva con animaciones suaves
- Soporte multi-idioma (Inglés/Español)
- Alternador de tema claro/oscuro
- Sección de precios interactiva con modal de solicitud de acceso
- Páginas de Política de Privacidad y Términos de Servicio

### 🔐 Autenticación
- Autenticación segura por email/contraseña vía Supabase Auth
- Persistencia de sesión con actualización automática de tokens
- Rutas protegidas con guardias de navegación
- Control de acceso basado en roles (rutas de administrador)

### 👥 Gestión de Clientes (CRM)
- Operaciones CRUD completas para gestión de clientes
- Seguimiento de datos de contacto, empresa y estado
- Vista detallada del cliente con resumen financiero
- Ver facturas asociadas e historial de pagos
- Gestión de estado Activo/Inactivo

### 📄 Facturación Inteligente
- Crear facturas profesionales con múltiples líneas de artículos
- Cálculos automáticos de saldo
- Múltiples estados de factura: `Borrador`, `Enviada`, `Pendiente`, `Pago Parcial`, `Pagada`, `Vencida`, `Cancelada`
- Seguimiento de fecha de vencimiento con alertas de atraso
- Flujo de cancelación de facturas

### 💰 Seguimiento de Pagos
- Registrar pagos completos y parciales
- Múltiples métodos de pago: Transferencia, Efectivo, Tarjeta de Crédito, Cheque
- Actualizaciones de saldo en tiempo real
- Historial completo de pagos con detalles de transacciones
- Estadísticas e indicadores de ingresos

### 📊 Dashboard y Analíticas
- Vista general de métricas del negocio en tiempo real
- Total por Cobrar y Saldo Pendiente
- Seguimiento de cobranzas mensuales
- Clientes activos y tasa de engagement
- Gráfico interactivo de distribución de estados de facturas (Chart.js)
- Facturas pendientes que requieren acción inmediata

### 🌐 Internacionalización (i18n)
- Soporte completo para **Inglés** y **Español**
- Selector de idioma en la barra de navegación y configurador de la app
- Todos los elementos de UI, mensajes y páginas legales traducidos

### 🎨 UI/UX Moderno
- Construido con la librería de componentes PrimeVue (tema Aura)
- TailwindCSS para estilos personalizados
- Soporte para modo oscuro
- Diseño responsivo (escritorio y móvil)
- Animaciones y transiciones suaves
- Notificaciones toast y diálogos de confirmación

---

## 🚀 Inicio Rápido

### Prerrequisitos

- **Node.js** 18+ 
- **npm** o **yarn**
- Cuenta de **Supabase** ([Crear una gratis](https://supabase.com))

### Instalación

1. **Clonar el repositorio**
   ```bash
   git clone https://github.com/yourusername/seikyu.git
   cd seikyu
   ```

2. **Instalar dependencias**
   ```bash
   npm install
   ```

3. **Configurar variables de entorno**
   
   Copiar el archivo de ejemplo:
   ```bash
   cp .env.example .env
   ```
   
   Editar `.env` y agregar tus credenciales de Supabase:
   ```env
   VITE_SUPABASE_URL=https://tu-proyecto.supabase.co
   VITE_SUPABASE_KEY=tu-anon-key
   ```
   
   > 📍 Encuentra estos valores en tu [Panel de Supabase](https://app.supabase.com) en **Project Settings > API**

4. **Configurar Base de Datos de Supabase**
   
   Crear las siguientes tablas en tu proyecto de Supabase:
   - `clients` - Información de clientes (nombre, email, teléfono, empresa, estado)
   - `invoices` - Datos de facturas (client_id, número, fecha, fecha_vencimiento, estado, items)
   - `payments` - Registros de pagos (invoice_id, monto, método, fecha, nota)
   
   > ⚠️ Asegúrate de configurar las políticas de **Row Level Security (RLS)** para usuarios autenticados.

5. **Ejecutar el servidor de desarrollo**
   ```bash
   npm run dev
   ```

6. **Abrir tu navegador**
   
   Navega a `http://localhost:5173`

---

## 📁 Estructura del Proyecto

```
seikyu/
├── public/
│   ├── favicon.ico
│   └── logo-seikyu.svg
├── src/
│   ├── app/
│   │   ├── i18n/                 # Internacionalización
│   │   │   ├── index.js
│   │   │   └── locales/
│   │   │       ├── en.json       # Traducciones en inglés
│   │   │       └── es.json       # Traducciones en español
│   │   ├── layout/               # Componentes de layout
│   │   │   ├── AppLayout.vue
│   │   │   ├── AppSidebar.vue
│   │   │   ├── AppTopbar.vue
│   │   │   └── AppConfigurator.vue
│   │   ├── pages/                # Páginas de nivel app
│   │   │   ├── Landing.vue
│   │   │   ├── NotFound.vue
│   │   │   ├── PrivacyPolicy.vue
│   │   │   └── TermsOfService.vue
│   │   └── router/               # Configuración de Vue Router
│   │       └── index.js
│   ├── features/
│   │   ├── auth/                 # Módulo de autenticación
│   │   │   ├── pages/
│   │   │   │   ├── Login.vue
│   │   │   │   ├── Access.vue    # Página de acceso denegado
│   │   │   │   └── Error.vue
│   │   │   └── store/
│   │   │       └── auth.js       # Store de Pinia para auth
│   │   ├── clients/              # Gestión de clientes
│   │   │   └── views/
│   │   │       ├── ClientsPage.vue
│   │   │       └── ClientDetails.vue
│   │   ├── dashboard/            # Módulo de dashboard
│   │   │   └── pages/
│   │   │       └── Dashboard.vue
│   │   ├── docs/                 # Página de documentación
│   │   │   └── pages/
│   │   │       └── Documentation.vue
│   │   ├── home/                 # Componentes de la landing
│   │   │   └── components/
│   │   │       ├── TopbarWidget.vue
│   │   │       ├── HeroWidget.vue
│   │   │       ├── FeaturesWidget.vue
│   │   │       ├── HighlightsWidget.vue
│   │   │       ├── PricingWidget.vue
│   │   │       └── FooterWidget.vue
│   │   ├── invoices/             # Gestión de facturas
│   │   │   └── views/
│   │   │       ├── InvoicesPage.vue
│   │   │       └── InvoiceDetails.vue
│   │   └── payments/             # Seguimiento de pagos
│   │       └── views/
│   │           └── PaymentsPage.vue
│   ├── shared/                   # Componentes y utilidades compartidas
│   ├── assets/
│   │   ├── styles.scss           # Estilos globales SCSS
│   │   └── tailwind.css          # Configuración de Tailwind
│   ├── App.vue                   # Componente raíz
│   ├── main.js                   # Punto de entrada
│   └── supabase.js               # Configuración del cliente Supabase
├── .env.example                  # Plantilla de variables de entorno
├── index.html                    # Punto de entrada HTML
├── package.json
├── vercel.json                   # Configuración de despliegue en Vercel
└── vite.config.mjs               # Configuración de Vite
```

---

## 🛠️ Stack Tecnológico

| Tecnología | Propósito |
|------------|-----------|
| [Vue 3](https://vuejs.org/) | Framework JavaScript Progresivo (Composition API) |
| [Vite](https://vitejs.dev/) | Herramienta de build de próxima generación |
| [PrimeVue 4](https://primevue.org/) | Librería de Componentes UI Premium (Tema Aura) |
| [Pinia](https://pinia.vuejs.org/) | Gestión de Estado para Vue |
| [Vue Router 4](https://router.vuejs.org/) | Router Oficial para Vue.js |
| [Vue I18n](https://vue-i18n.intlify.dev/) | Plugin de internacionalización |
| [Supabase](https://supabase.com/) | Backend-as-a-Service (Auth, Database, RLS) |
| [TailwindCSS 4](https://tailwindcss.com/) | Framework CSS utility-first |
| [Chart.js](https://www.chartjs.org/) | Librería de gráficos JavaScript |
| [PrimeIcons](https://primevue.org/icons/) | Librería de iconos |

---

## 📜 Scripts Disponibles

| Comando | Descripción |
|---------|-------------|
| `npm run dev` | Iniciar servidor de desarrollo con hot-reload |
| `npm run build` | Compilar para producción |
| `npm run preview` | Previsualizar build de producción localmente |
| `npm run lint` | Ejecutar ESLint para verificar y corregir código |

---

## 🌐 Despliegue

### Vercel (Recomendado)

SEIKYU está configurado para despliegue sin problemas en **Vercel**:

1. Sube tu código a GitHub
2. Importa el repositorio en [Vercel](https://vercel.com)
3. Agrega las variables de entorno:
   - `VITE_SUPABASE_URL`
   - `VITE_SUPABASE_KEY`
4. ¡Despliega!

El `vercel.json` ya está configurado para enrutamiento SPA.

### Otras Plataformas

Para otras plataformas (Netlify, Railway, etc.), asegúrate de:
- Configurar reglas de redirección SPA (`/* → /index.html`)
- Establecer correctamente las variables de entorno

---

## 🔒 Notas de Seguridad

- ⚠️ **Nunca hagas commit** de tu archivo `.env` al control de versiones
- El archivo `.env` ya está listado en `.gitignore`
- Usa `.env.example` como plantilla para colaboradores
- Mantén seguras tus claves de Supabase
- Configura políticas **RLS** apropiadas en Supabase para producción

---

## 🗺️ Hoja de Ruta

- [ ] Notificaciones por email para facturas vencidas
- [ ] Generación y exportación de facturas en PDF
- [ ] Facturas recurrentes
- [ ] Portal de cliente para ver facturas
- [ ] Soporte multi-moneda
- [ ] Reportes y analíticas avanzadas
- [ ] Aplicación móvil (Vue Native / Capacitor)

---

## 👤 Autor

Desarrollado con ❤️ por **Angel Mawex**

- 🌐 [Portafolio](https://angelmawex.dev)
- 💼 [LinkedIn](https://linkedin.com/in/angelmawex)
- 🐙 [GitHub](https://github.com/angelmawex)

---

## 📄 Licencia

Este proyecto es software propietario. Todos los derechos reservados.

Consulta [Política de Privacidad](/privacy) y [Términos de Servicio](/terms) para más información.

---

<p align="center">
  <strong>SEIKYU</strong> © 2026 — Optimiza Tu Negocio
</p>
