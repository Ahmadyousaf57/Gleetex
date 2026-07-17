<div align="center">
  <img src="https://img.shields.io/badge/Gleetex-Luxury_Commerce-black?style=for-the-badge&logo=shopify" alt="Gleetex Logo">
  <h1>✨ Gleetex</h1>
  <p><strong>Premium Full-Stack Luxury E-Commerce Platform</strong></p>

  [![React](https://img.shields.io/badge/React-18.x-61DAFB.svg?style=flat-square&logo=react)](https://reactjs.org/)
  [![Node.js](https://img.shields.io/badge/Node.js-18.x-339933.svg?style=flat-square&logo=node.js)](https://nodejs.org/)
  [![Express.js](https://img.shields.io/badge/Express.js-Backend-lightgrey.svg?style=flat-square&logo=express)](https://expressjs.com/)
  [![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose-47A248.svg?style=flat-square&logo=mongodb)](https://www.mongodb.com/)
  [![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.x-38B2AC.svg?style=flat-square&logo=tailwind-css)](https://tailwindcss.com/)
  [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](https://opensource.org/licenses/MIT)
</div>

---

## 📖 Executive Summary

**Gleetex** is a meticulously crafted, full-stack e-commerce web application designed specifically for the luxury goods market. By combining a highly performant, responsive React frontend with a scalable Node.js backend, Gleetex delivers an unparalleled shopping experience.

It features a comprehensive customer-facing storefront and a powerful administrative dashboard, enabling seamless product management, order tracking, and user administration. The project is engineered utilizing modern web development practices including robust state management via Zustand, RESTful API architecture, and secure JWT-based authentication.

---

## ✨ Core Features & Capabilities

### 🛍️ Customer Experience
- **Elegant Product Catalog:** Browse premium luxury items with high-resolution image galleries and detailed descriptions.
- **Dynamic Shopping Cart:** Manage selections smoothly with real-time updates using Zustand state management.
- **Secure Authentication:** Create accounts and log in securely using JWT (JSON Web Tokens) and bcrypt password hashing.
- **Order Tracking & History:** Customers can seamlessly track current orders and review past purchase history directly from their personalized dashboard.
- **Product Reviews:** Authenticated users can leave and read product reviews, fostering a community of trust.

### 🛡️ Administrative Dashboard
- **Comprehensive Analytics:** A dedicated `/admin` portal displaying high-level metrics and store performance dashboards.
- **Inventory Management:** Full CRUD (Create, Read, Update, Delete) capabilities for product listings, pricing, and stock levels.
- **Order Fulfillment:** Admins can view all incoming orders, update shipping statuses, and manage fulfillment workflows.
- **User Management:** Monitor registered users, handle customer inquiries, and adjust role-based access (e.g., promoting users to Admin).

### ⚡ Technical Highlights
- **Role-Based Access Control (RBAC):** Strict middleware protecting administrative API routes from unauthorized access.
- **Responsive UI/UX:** Built with Tailwind CSS, ensuring pixel-perfect layout rendering across mobile, tablet, and desktop devices.
- **Optimized Data Fetching:** Structured REST API interacting with MongoDB via Mongoose schemas.

---

## 🛠️ Technology Stack

### Frontend (Client-Side)
- **Framework:** React.js (via Vite for lightning-fast HMR and building)
- **Styling:** Tailwind CSS (Utility-first framework for custom, premium aesthetics)
- **State Management:** Zustand (Lightweight, unopinionated state manager)
- **HTTP Client:** Axios (For interceptor-based, secure API communication)

### Backend (Server-Side)
- **Environment:** Node.js
- **Framework:** Express.js (REST API architecture)
- **Database:** MongoDB
- **ODM:** Mongoose (Schema validation and relationship mapping)
- **Authentication:** jsonwebtoken (JWT) & bcryptjs

---

## 📁 Project Structure Architecture

```text
Gleetex/
│
├── backend/               # Core Express.js API
│   ├── src/
│   │   ├── config/        # Environment configurations & DB connection logic
│   │   ├── controllers/   # Route handlers and business logic
│   │   ├── middleware/    # Auth, Error handling, and RBAC verification
│   │   ├── models/        # Mongoose Schemas (User, Product, Order)
│   │   └── routes/        # Express API Route definitions
│   ├── package.json       # Backend dependencies
│   └── .env.example       # Example environment variables
│
└── frontend/              # React + Vite Client
    ├── src/
    │   ├── admin/         # Protected Administrative Dashboard components
    │   ├── components/    # Reusable UI elements (Buttons, Navbars, Cards)
    │   ├── pages/         # Public-facing views (Home, Shop, Cart, Profile)
    │   ├── store/         # Zustand global state definitions
    │   └── utils/         # Axios instances and helper functions
    ├── package.json       # Frontend dependencies
    ├── tailwind.config.js # Custom Tailwind theme definitions
    └── vite.config.js     # Vite bundler configurations
```

---

## 🚀 Installation & Setup Guide

### 1. Prerequisites
Ensure you have the following installed:
- **Node.js** (v18.x or higher)
- **MongoDB** (Running locally on port `27017` or a MongoDB Atlas connection string)
- **Git**

### 2. Clone the Repository
```bash
git clone https://github.com/Ahmadyousaf57/Gleetex.git
cd Gleetex
```

### 3. Backend Setup
Navigate to the backend directory, install dependencies, and start the development server.

```bash
cd backend
npm install

# Create your .env file
cp .env.example .env

# Start the server
npm run dev
# The API will run on http://localhost:5000
```

### 4. Frontend Setup
Open a new terminal, navigate to the frontend directory, install dependencies, and start Vite.

```bash
cd frontend
npm install

# Start the React development server
npm run dev
# The App will run on http://localhost:5173
```

### 5. Creating the First Administrator
To access the Admin panel, you must elevate a standard user account.
1. Register a new user via the frontend (`http://localhost:5173/register`).
2. Open your MongoDB shell, MongoDB Compass, or preferred GUI.
3. Execute the following update command:
   ```javascript
   db.users.updateOne(
     { email: "your@email.com" }, 
     { $set: { role: "admin" } }
   )
   ```
4. Log back in and navigate to `/admin` to access the dashboard.

---

## 📡 API Reference Documentation

### Authentication & Users (`/api/auth`)
| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| `POST` | `/register` | Register a new customer account | Public |
| `POST` | `/login` | Authenticate user and return JWT | Public |
| `GET`  | `/me` | Fetch current logged-in user profile | Private |
| `PUT`  | `/profile` | Update user profile information | Private |

### Products (`/api/products`)
| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| `GET`  | `/` | Retrieve all products (Supports pagination/filtering) | Public |
| `GET`  | `/:id` | Retrieve a single product by ID | Public |
| `POST` | `/` | Create a new luxury product listing | **Admin** |
| `PUT`  | `/:id` | Update product details or pricing | **Admin** |
| `DELETE`| `/:id` | Remove a product from the catalog | **Admin** |
| `POST` | `/:id/reviews`| Submit a customer review and rating | Private |

### Orders (`/api/orders`)
| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| `POST` | `/` | Create a new customer order | Private |
| `GET`  | `/my` | Retrieve all orders for the logged-in user | Private |
| `GET`  | `/:id` | Retrieve specific order details | Private |
| `GET`  | `/` | Retrieve ALL system orders | **Admin** |
| `PUT`  | `/:id/status`| Update order status (e.g., Shipped, Delivered) | **Admin** |

### Administration (`/api/admin`)
| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| `GET`  | `/dashboard` | Retrieve high-level sales and user metrics | **Admin** |
| `GET`  | `/users` | Retrieve all registered users | **Admin** |
| `PUT`  | `/users/:id/role` | Update user role (e.g., promote to Admin) | **Admin** |
| `DELETE`| `/users/:id` | Delete a user account from the system | **Admin** |

---

## 🤝 Contribution Guidelines

We welcome contributions to make Gleetex even better! To contribute:

1. **Fork** the repository.
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`).
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`).
4. **Push** to the branch (`git push origin feature/AmazingFeature`).
5. **Open** a Pull Request detailing your changes.

---

## 📄 License & Legal

This project is open-sourced under the **MIT License**. See the `LICENSE` file for full details.

<div align="center">
  <br>
  <i>Built for the modern web.</i>
  <br>
  <b>Redefining Digital Luxury.</b>
</div>
