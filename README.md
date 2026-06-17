<div align="center">
  <img src="https://img.shields.io/badge/NeoPay-Pro-blue?style=for-the-badge&logo=appveyor" alt="NeoPay Pro Logo">
  <h1>🚀 NeoPay Pro - Next-Generation FinTech Wallet</h1>
  <p><strong>A Premium Digital Wallet & Payment Gateway Platform</strong></p>

  [![Node.js](https://img.shields.io/badge/Node.js-18.x-green.svg?style=flat-square&logo=node.js)](https://nodejs.org/)
  [![Express.js](https://img.shields.io/badge/Express.js-5.2.1-lightgrey.svg?style=flat-square&logo=express)](https://expressjs.com/)
  [![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15.x-blue.svg?style=flat-square&logo=postgresql)](https://www.postgresql.org/)
  [![Vanilla JS](https://img.shields.io/badge/Vanilla_JS-ES6-yellow.svg?style=flat-square&logo=javascript)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
  [![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=flat-square)](https://opensource.org/licenses/MIT)
</div>

---

## 📖 Executive Summary

**NeoPay Pro** is a cutting-edge, ultra-premium FinTech web application designed to redefine the digital banking experience. By merging state-of-the-art UI/UX principles with a robust, highly secure backend, NeoPay Pro delivers a native app-like experience directly within the browser. 

Whether you're performing peer-to-peer (P2P) transfers, analyzing financial growth through interactive charts, or seeking help from our integrated AI Support Agent, NeoPay Pro handles it all seamlessly with unparalleled speed and aesthetic precision.

---

## ✨ Core Features & Capabilities

### 🛡️ Enterprise-Grade Security
- **Multi-Factor Authentication (MFA):** Mandatory OTP email verification powered by Resend API during registration to prevent bot accounts.
- **Biometric Authentication:** Modern WebAuthn-inspired fingerprint login mechanism for frictionless, passwordless entry.
- **Stateless Sessions:** Secure, time-limited JSON Web Tokens (JWT) ensuring all API requests are strictly authenticated and authorized.
- **Cryptographic Hashing:** Utilization of `bcryptjs` for irreversible password hashing and salting.

### 💳 Ultimate UI/UX & Design Architecture
- **Stunning Glassmorphism:** Crafted with advanced CSS properties (`backdrop-filter`, ambient radial gradients, dynamic shadows) to create a translucent, frosted-glass effect.
- **Interactive 3D Virtual Card:** A masterclass in CSS 3D Transforms (`perspective`, `rotateY`), allowing users to click and flip their card to securely view CVV details.
- **Fluid Micro-Interactions:** Custom bezier-curve transitions, scalable hover effects, and tactile feedback simulation across all touchpoints (e.g., custom transfer numpad).
- **Adaptive Theming:** Native-feeling Dark and Light mode toggle that recalculates CSS variables on the fly for optimal viewing in any environment.

### 💸 Frictionless Financial Operations
- **Real-Time P2P Transfers:** Send money instantly. Features a dynamic contact search filtering users by Name, Phone Number, or Unique PSID.
- **Customized Transfer Numpad:** A bespoke, large-format numeric keypad designed for fast, error-free amount entries.
- **Actionable Transaction History:** Detailed, categorized transaction ledgers (Income, Subscriptions, Food & Drink) with visually distinct icons and receipts.
- **Advanced Card Management:** Instant toggles for freezing the card, disabling online payments, or blocking ATM withdrawals.

### 📊 Intelligent Analytics
- **Dynamic Charting:** Custom-built CSS/JS vertical bar charts visualizing daily expenditures vs. income without relying on heavy third-party libraries.
- **Expense Summaries:** Quick-glance metrics for total monthly income and total expenses.

### 🤖 Integrated AI Support Bot
- **Context-Aware Assistance:** A built-in AI Customer Service ChatBot capable of answering queries regarding security, money transfers, account management, and generalized support.

---

## 🛠️ Technical Stack & Architecture

### The Frontend (The "Vanilla" Advantage)
Instead of relying on heavy frameworks like React or Vue, NeoPay Pro is meticulously engineered using **Vanilla HTML5, CSS3, and ES6+ JavaScript**. This ensures:
- **Zero Bundle Bloat:** Lightning-fast initial load times.
- **Direct DOM Manipulation:** Highly optimized and performant animations.
- **Iconography:** [Phosphor Icons](https://phosphoricons.com/) for lightweight, consistent, and premium scalable vector graphics.
- **Typography:** Custom `Work Sans` font integration for a clean, geometric, and modern look.

### The Backend Engine (Node.js & Express)
The backend is a robust REST API designed for scale and security:
- **Framework:** `Express.js` (v5.2.1) providing fast, unopinionated routing and middleware integration.
- **Database:** `PostgreSQL` interacting via the `pg` pool module. Capable of handling complex relational queries, indexing for fast search, and maintaining transaction integrity.
- **Mailing Service:** `Resend SDK` replacing legacy SMTP systems for ultra-fast, reliable transactional emails (OTP delivery).
- **Environment Management:** `dotenv` for strict environment variable parsing, ensuring no secrets are hardcoded.

---

## 📁 Comprehensive Project Structure

```text
NEOPAYWeb/
│
├── backend/
│   ├── server.js         # Entry point: Express app, middleware, routes, & static serving
│   ├── db.js             # Database configuration: PostgreSQL Pool & automatic table initialization
│   ├── seed.js           # Development utility: Seeds database with mock users and transactions
│   ├── package.json      # Backend dependencies and runtime scripts
│   └── .env              # Secrets and configurations (Must be created by the user)
│
├── wallet.html           # The monolithic Frontend: Contains HTML layout, scoped CSS, and JS logic
├── package.json          # Root package.json (Dependency tracking)
├── vercel.json           # Deployment config: Maps backend serverless functions for Vercel
├── google6a9399bee8f201ee.html # Verification file for Google Search Console
└── README.md             # Project Documentation (You are here)
```

---

## 🚀 Installation & Setup Guide

### 1. Prerequisites
Ensure you have the following installed:
- **Node.js** (v18.x or higher)
- **PostgreSQL** (v14.x or higher, running locally or on a cloud provider like Neon/Supabase)
- **Git**

### 2. Clone the Repository
```bash
git clone https://github.com/your-username/neopay-pro.git
cd neopay-pro
```

### 3. Install Dependencies
```bash
# Install root/backend dependencies
npm install
```

### 4. Environment Variables
Create a `.env` file in the `backend/` directory (or root, depending on execution) and configure the following:

```env
# Server Config
PORT=5000
NODE_ENV=development
FRONTEND_URL=http://localhost:5000

# PostgreSQL Database Config
PG_HOST=localhost
PG_DATABASE=neopay
PG_USER=postgres
PG_PASSWORD=your_secure_password
PG_PORT=5432

# Security
JWT_SECRET=generate_a_strong_random_secret_string

# Email Service (Resend)
RESEND_API_KEY=re_your_resend_api_key
```

### 5. Database Initialization
You do not need to manually create tables. When the server starts, `db.js` automatically connects to PostgreSQL and creates the `users` and `transactions` tables if they do not exist.

### 6. Run the Application
```bash
# Start the server (runs node backend/server.js)
npm start
```

Visit `http://localhost:5000` in your browser. The Express server acts as both the API provider and the static file host for `wallet.html`.

---

## 📡 API Reference Documentation

### Authentication & Onboarding
| Method | Endpoint | Payload / Params | Description |
|--------|----------|------------------|-------------|
| `POST` | `/api/auth/signup` | `{ username, email, password, biometricKey }` | Hashes password, saves user as unverified, triggers OTP email. |
| `POST` | `/api/auth/verify-otp`| `{ email, otp }` | Validates OTP. If valid, marks user as verified. |
| `POST` | `/api/auth/login` | `{ username, password, biometricKey }` | Authenticates via password OR biometric key. Returns JWT token. |

### Users & Social
| Method | Endpoint | Payload / Params | Description |
|--------|----------|------------------|-------------|
| `GET`  | `/api/users/search?q=` | Query param: `q` | Performs an `ILIKE` search on usernames, phone numbers, and PSIDs. Limits to 10 results. |

### Transactions
| Method | Endpoint | Payload / Params | Description |
|--------|----------|------------------|-------------|
| `POST` | `/api/transactions` | `{ sender, receiverName, transferMethod, accountNumber, amount }` | Validates input and logs a new transaction ledger entry. |

### Utility
| Method | Endpoint | Payload / Params | Description |
|--------|----------|------------------|-------------|
| `POST` | `/api/chat` | `{ message }` | Parses user message and returns a context-aware AI chatbot response. |
| `GET`  | `/api/health` | None | Returns a 200 OK status along with boolean checks for required environment variables. |

---

## 🔮 Future Roadmap

- [ ] **Stripe / Plaid Integration:** Real-world fiat on-ramping and bank account linking.
- [ ] **WebSockets Integration:** Real-time transaction notifications without manual refresh.
- [ ] **PWA Support:** Full Progressive Web App manifestation for offline capabilities and native mobile installation.
- [ ] **Multi-Currency & Crypto:** Support for USD, EUR, and top cryptocurrencies (BTC, ETH, SOL) with real-time exchange rates.

---

## 🤝 Contribution Guidelines

We welcome contributions from the community! To contribute:

1. **Fork** the repository.
2. **Create** a feature branch (`git checkout -b feature/NewFeature`).
3. **Commit** your changes (`git commit -m 'Add some NewFeature'`).
4. **Push** to the branch (`git push origin feature/NewFeature`).
5. **Open** a Pull Request detailing your changes.

Ensure your code adheres to the existing styling and includes comments for complex logic.

---

## 📄 License & Legal

This project is licensed under the **MIT License**. See the `LICENSE` file for full details. 

*Disclaimer: NeoPay Pro is a demonstration of FinTech engineering and design capabilities. It is not currently licensed to handle real financial assets in production.*

<div align="center">
  <br>
  <i>Engineered with 💡 and ❤️ for the modern web.</i>
  <br>
  <b>Experience the Future of Digital Payments.</b>
</div>
