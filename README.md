# 🏪 KiranaBoost

> **WhatsApp-powered CRM & Marketing Platform for Kirana Stores and Small Indian Retailers**

KiranaBoost helps small shop owners retain customers and increase repeat purchases by sending promotional offers, festival discounts, and reminders via WhatsApp — all managed from a simple, mobile-first dashboard.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Live Demo](#live-demo)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [Database Schema](#database-schema)
- [API Reference](#api-reference)
- [Pages & Routes](#pages--routes)
- [Subscription Plans](#subscription-plans)
- [WhatsApp Integration](#whatsapp-integration)
- [Payment Integration](#payment-integration)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

KiranaBoost is a SaaS platform built specifically for India's 12+ million kirana stores, grocery shops, vegetable vendors, and small retailers. It bridges the gap between traditional retail and digital marketing by leveraging WhatsApp — India's most-used messaging app — as the primary communication channel.

**The problem it solves:** Most kirana store owners have no way to contact their customers after a purchase. They lose repeat business to larger supermarkets and online platforms simply because they cannot send timely offers or stay top-of-mind.

**The solution:** A simple mobile-first platform where shop owners can manage a customer database, create promotional campaigns, and send WhatsApp messages in bulk — all without any technical knowledge.

---

## Live Demo

| Role         | Email              | Password   | Access               |
|--------------|--------------------|------------|----------------------|
| Shop Owner   | any@email.com      | any        | `/dashboard`         |
| Platform Admin | admin@email.com  | any        | `/admin`             |

> Select the appropriate role in the login dropdown before signing in.

---

## Features

### For Shop Owners

| Feature                    | Free | Basic | Pro  |
|----------------------------|------|-------|------|
| Customer Database          | 50   | 500   | ∞    |
| WhatsApp Messages / Month  | 10   | 500   | 2000 |
| Campaign Builder           | ✓    | ✓     | ✓    |
| Festival Templates         | ✓    | ✓     | ✓    |
| Message Scheduling         | ✗    | ✓     | ✓    |
| Customer Segmentation      | ✗    | Basic | Full |
| Offer / Coupon Creator     | ✗    | ✓     | ✓    |
| Analytics Dashboard        | ✗    | Basic | Full |
| CSV Import / Export        | ✗    | ✓     | ✓    |
| Priority Support           | ✗    | ✓     | ✓    |

### For Platform Admins

- View and manage all registered shop owners
- Approve or suspend accounts
- View platform-wide analytics and revenue
- Manage WhatsApp API and Razorpay configuration
- Monitor message usage and delivery rates

---

## Tech Stack

| Layer            | Technology                                     |
|------------------|------------------------------------------------|
| **Frontend**     | React 18, CSS Variables, Vite                  |
| **Backend**      | Node.js 20, Express.js                         |
| **Database**     | Firebase Firestore (NoSQL)                     |
| **Auth**         | Firebase Authentication (email + password)     |
| **Messaging**    | WhatsApp Business Cloud API (Meta)             |
| **Payments**     | Razorpay (UPI, cards, net banking)             |
| **Hosting**      | Firebase Hosting + Cloud Functions             |
| **Storage**      | Firebase Cloud Storage (offer images)          |
| **Analytics**    | Firebase Analytics + custom metrics            |
| **SEO**          | React Helmet Async, JSON-LD schema markup      |

---

## Project Structure

```
kiranaboost/
├── frontend/                        # React SPA
│   ├── public/
│   │   ├── index.html
│   │   ├── favicon.ico
│   │   ├── robots.txt
│   │   └── sitemap.xml
│   ├── src/
│   │   ├── components/
│   │   │   ├── Navbar.jsx
│   │   │   ├── Sidebar.jsx
│   │   │   ├── StatCard.jsx
│   │   │   ├── CustomerTable.jsx
│   │   │   ├── CampaignCard.jsx
│   │   │   ├── OfferCard.jsx
│   │   │   ├── Modal.jsx
│   │   │   └── ProgressBar.jsx
│   │   ├── pages/
│   │   │   ├── Home.jsx
│   │   │   ├── About.jsx
│   │   │   ├── Features.jsx
│   │   │   ├── Pricing.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── Signup.jsx
│   │   │   ├── Dashboard/
│   │   │   │   ├── index.jsx
│   │   │   │   ├── Overview.jsx
│   │   │   │   ├── Customers.jsx
│   │   │   │   ├── Campaigns.jsx
│   │   │   │   ├── Offers.jsx
│   │   │   │   ├── Analytics.jsx
│   │   │   │   ├── Schedule.jsx
│   │   │   │   └── Settings.jsx
│   │   │   ├── Admin/
│   │   │   │   ├── index.jsx
│   │   │   │   ├── Overview.jsx
│   │   │   │   ├── Users.jsx
│   │   │   │   ├── Subscriptions.jsx
│   │   │   │   ├── Analytics.jsx
│   │   │   │   └── System.jsx
│   │   │   ├── Contact.jsx
│   │   │   ├── FAQ.jsx
│   │   │   ├── Privacy.jsx
│   │   │   └── Terms.jsx
│   │   ├── context/
│   │   │   └── AuthContext.jsx
│   │   ├── hooks/
│   │   │   ├── useAuth.js
│   │   │   ├── useCustomers.js
│   │   │   └── useCampaigns.js
│   │   ├── services/
│   │   │   ├── api.js              # Axios instance + interceptors
│   │   │   ├── firebase.js         # Firebase config + helpers
│   │   │   └── whatsapp.js         # WhatsApp API helpers
│   │   ├── utils/
│   │   │   ├── formatters.js       # Date, currency, phone formatters
│   │   │   └── validators.js       # Form validation helpers
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── package.json
│   └── vite.config.js
│
├── backend/                         # Node.js + Express API
│   ├── src/
│   │   ├── controllers/
│   │   │   ├── authController.js
│   │   │   ├── shopController.js
│   │   │   ├── customerController.js
│   │   │   ├── campaignController.js
│   │   │   ├── offerController.js
│   │   │   ├── subscriptionController.js
│   │   │   └── adminController.js
│   │   ├── routes/
│   │   │   ├── auth.js
│   │   │   ├── shops.js
│   │   │   ├── customers.js
│   │   │   ├── campaigns.js
│   │   │   ├── offers.js
│   │   │   ├── subscriptions.js
│   │   │   └── admin.js
│   │   ├── middleware/
│   │   │   ├── authMiddleware.js   # Firebase token verification
│   │   │   ├── adminMiddleware.js  # Admin role guard
│   │   │   ├── rateLimiter.js      # express-rate-limit config
│   │   │   └── errorHandler.js
│   │   ├── services/
│   │   │   ├── whatsappService.js  # Meta Cloud API integration
│   │   │   ├── razorpayService.js  # Razorpay subscription mgmt
│   │   │   ├── schedulerService.js # node-cron campaign scheduler
│   │   │   └── notificationService.js
│   │   ├── models/                 # Firestore collection helpers
│   │   │   ├── User.js
│   │   │   ├── Customer.js
│   │   │   ├── Campaign.js
│   │   │   ├── Offer.js
│   │   │   └── Subscription.js
│   │   ├── config/
│   │   │   ├── firebase.js
│   │   │   └── constants.js
│   │   └── app.js
│   ├── functions/                  # Firebase Cloud Functions
│   │   ├── scheduledCampaigns.js
│   │   └── webhooks.js
│   └── package.json
│
├── .env.example
├── firebase.json
├── .firebaserc
└── README.md
```

---

## Getting Started

### Prerequisites

- Node.js 20+
- npm or yarn
- Firebase project (Firestore + Authentication enabled)
- Meta Developer account (WhatsApp Business API)
- Razorpay account (for payments)

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/kiranaboost.git
cd kiranaboost
```

### 2. Install Dependencies

```bash
# Frontend
cd frontend
npm install

# Backend
cd ../backend
npm install
```

### 3. Configure Environment Variables

```bash
cp .env.example .env
# Edit .env with your credentials (see Environment Variables section below)
```

### 4. Set Up Firebase

```bash
npm install -g firebase-tools
firebase login
firebase init        # Select Firestore, Hosting, Functions
firebase deploy --only firestore:rules
```

### 5. Run Locally

```bash
# Terminal 1 — Backend
cd backend
npm run dev          # Starts on http://localhost:5000

# Terminal 2 — Frontend
cd frontend
npm run dev          # Starts on http://localhost:5173
```

---

## Environment Variables

### Frontend (`frontend/.env`)

```env
VITE_API_BASE_URL=http://localhost:5000/api/v1
VITE_FIREBASE_API_KEY=your_firebase_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
VITE_FIREBASE_MESSAGING_SENDER_ID=123456789
VITE_FIREBASE_APP_ID=1:123456789:web:abcdef
VITE_RAZORPAY_KEY_ID=rzp_live_xxxxxxxxxxxx
```

### Backend (`backend/.env`)

```env
PORT=5000
NODE_ENV=production

# Firebase Admin SDK
FIREBASE_PROJECT_ID=your_project_id
FIREBASE_CLIENT_EMAIL=firebase-adminsdk@your_project.iam.gserviceaccount.com
FIREBASE_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\n...\n-----END PRIVATE KEY-----\n"

# WhatsApp Business Cloud API
WHATSAPP_API_TOKEN=your_meta_access_token
WHATSAPP_PHONE_NUMBER_ID=123456789012345
WHATSAPP_BUSINESS_ACCOUNT_ID=987654321098765
WHATSAPP_WEBHOOK_VERIFY_TOKEN=your_webhook_secret

# Razorpay
RAZORPAY_KEY_ID=rzp_live_xxxxxxxxxxxx
RAZORPAY_KEY_SECRET=your_razorpay_secret
RAZORPAY_WEBHOOK_SECRET=your_webhook_secret

# App
JWT_SECRET=your_super_secret_jwt_key_min_32_chars
FRONTEND_URL=https://kiranaboost.in
```

---

## Database Schema

### `users` Collection

```
users/{userId}
├── uid              : string         — Firebase Auth UID
├── name             : string         — Owner's full name
├── email            : string         — Login email
├── phone            : string         — E.164 format (+919876543210)
├── shopName         : string         — Display name of the shop
├── shopCategory     : string         — grocery | vegetable | medical | bakery | other
├── city             : string         — City / town
├── whatsappConnected: boolean        — WhatsApp API connected status
├── whatsappPhone    : string         — Business WhatsApp number
├── plan             : string         — free | basic | pro
├── planExpiry       : timestamp      — Subscription expiry date
├── status           : string         — active | suspended | pending
├── createdAt        : timestamp
└── updatedAt        : timestamp
```

### `customers` Collection

```
customers/{customerId}
├── shopId           : string         — Reference to users/{userId}
├── name             : string         — Customer name
├── phone            : string         — E.164 format (+919876543210)
├── segment          : string         — vip | regular | new | inactive
├── tags             : string[]       — Custom labels
├── totalPurchases   : number         — Lifetime visit / purchase count
├── lastVisitDate    : timestamp
├── joinDate         : timestamp      — When added to KiranaBoost
├── notes            : string         — Shop owner notes
├── optedIn          : boolean        — WhatsApp messaging consent
└── createdAt        : timestamp
```

### `campaigns` Collection

```
campaigns/{campaignId}
├── shopId           : string         — Reference to users/{userId}
├── name             : string         — Campaign display name
├── type             : string         — promotional | festival | reminder | reengagement
├── message          : string         — WhatsApp message body (max 1024 chars)
├── mediaUrl         : string         — Optional image URL (Firebase Storage)
├── targetSegment    : string         — all | vip | regular | new | inactive
├── targetCount      : number         — Number of recipients
├── status           : string         — draft | scheduled | sending | sent | failed
├── scheduledAt      : timestamp      — When to send (null = immediate)
├── sentAt           : timestamp      — Actual send time
├── stats
│   ├── sent         : number
│   ├── delivered    : number
│   ├── read         : number
│   └── failed       : number
└── createdAt        : timestamp
```

### `offers` Collection

```
offers/{offerId}
├── shopId           : string
├── title            : string         — e.g., "Diwali Dhamaka Sale"
├── description      : string
├── discountType     : string         — percentage | fixed | bogo
├── discountValue    : string         — e.g., "20" (%) or "50" (₹)
├── minOrderValue    : number         — Minimum cart value (0 = none)
├── type             : string         — promotional | festival | weekly | clearance
├── validFrom        : timestamp
├── validUntil       : timestamp
├── status           : string         — active | draft | expired
├── couponCode       : string         — e.g., "DIWALI24"
└── createdAt        : timestamp
```

### `subscriptions` Collection

```
subscriptions/{subscriptionId}
├── shopId           : string
├── plan             : string         — free | basic | pro
├── billingCycle     : string         — monthly | yearly
├── amount           : number         — Amount in paise (₹199 = 19900)
├── currency         : string         — INR
├── razorpaySubId    : string         — Razorpay subscription ID
├── razorpayPaymentId: string         — Latest payment ID
├── status           : string         — active | cancelled | failed | expired
├── startDate        : timestamp
├── endDate          : timestamp
└── createdAt        : timestamp
```

---

## API Reference

**Base URL:** `https://api.kiranaboost.in/v1`

All protected routes require `Authorization: Bearer <firebase_id_token>` header.

### Authentication

| Method | Endpoint               | Description                     | Auth |
|--------|------------------------|---------------------------------|------|
| POST   | `/auth/register`       | Register new shop owner         | No   |
| POST   | `/auth/login`          | Login (returns Firebase token)  | No   |
| POST   | `/auth/logout`         | Invalidate session              | Yes  |
| POST   | `/auth/forgot-password`| Send password reset email       | No   |

### Shop Profile

| Method | Endpoint               | Description                     | Auth |
|--------|------------------------|---------------------------------|------|
| GET    | `/shop/profile`        | Get shop profile                | Yes  |
| PUT    | `/shop/profile`        | Update shop profile             | Yes  |
| POST   | `/shop/connect-whatsapp` | Connect WhatsApp Business API  | Yes  |
| GET    | `/shop/stats`          | Dashboard stats summary         | Yes  |

### Customers

| Method | Endpoint                   | Description                     | Auth |
|--------|----------------------------|---------------------------------|------|
| GET    | `/customers`               | List all customers (paginated)  | Yes  |
| POST   | `/customers`               | Add a single customer           | Yes  |
| POST   | `/customers/import`        | Bulk import via CSV             | Yes  |
| GET    | `/customers/export`        | Export customers as CSV         | Yes  |
| GET    | `/customers/:id`           | Get customer details            | Yes  |
| PUT    | `/customers/:id`           | Update customer                 | Yes  |
| DELETE | `/customers/:id`           | Delete customer                 | Yes  |
| PUT    | `/customers/:id/segment`   | Update customer segment         | Yes  |
| GET    | `/customers/segments/counts` | Get counts per segment        | Yes  |

### Campaigns

| Method | Endpoint                    | Description                    | Auth |
|--------|-----------------------------|--------------------------------|------|
| GET    | `/campaigns`                | List all campaigns             | Yes  |
| POST   | `/campaigns`                | Create new campaign            | Yes  |
| GET    | `/campaigns/:id`            | Get campaign + stats           | Yes  |
| PUT    | `/campaigns/:id`            | Update campaign                | Yes  |
| DELETE | `/campaigns/:id`            | Delete campaign                | Yes  |
| POST   | `/campaigns/:id/send`       | Send immediately               | Yes  |
| POST   | `/campaigns/:id/schedule`   | Schedule for later             | Yes  |
| GET    | `/campaigns/templates`      | Get message templates          | Yes  |

### Offers

| Method | Endpoint              | Description                     | Auth |
|--------|-----------------------|---------------------------------|------|
| GET    | `/offers`             | List all offers                 | Yes  |
| POST   | `/offers`             | Create new offer                | Yes  |
| PUT    | `/offers/:id`         | Update offer                    | Yes  |
| DELETE | `/offers/:id`         | Delete offer                    | Yes  |
| POST   | `/offers/:id/share`   | Share offer via WhatsApp        | Yes  |

### Subscriptions

| Method | Endpoint                      | Description                   | Auth |
|--------|-------------------------------|-------------------------------|------|
| GET    | `/subscription`               | Get current subscription      | Yes  |
| POST   | `/subscription/create`        | Create Razorpay subscription  | Yes  |
| POST   | `/subscription/verify`        | Verify payment webhook        | No*  |
| POST   | `/subscription/cancel`        | Cancel subscription           | Yes  |
| GET    | `/subscription/invoices`      | List billing history          | Yes  |

> *Razorpay webhook — verified via webhook secret, not Firebase token

### Admin (requires admin role)

| Method | Endpoint                      | Description                   |
|--------|-------------------------------|-------------------------------|
| GET    | `/admin/users`                | List all shop owners          |
| GET    | `/admin/users/:id`            | Get user details              |
| PUT    | `/admin/users/:id/status`     | Approve / suspend user        |
| GET    | `/admin/analytics`            | Platform-wide analytics       |
| GET    | `/admin/revenue`              | Revenue and MRR dashboard     |
| GET    | `/admin/messages/usage`       | WhatsApp usage stats          |
| PUT    | `/admin/settings`             | Update platform settings      |

---

## Pages & Routes

| Route            | Component           | Auth Required | Description                     |
|------------------|---------------------|---------------|---------------------------------|
| `/`              | `Home`              | No            | Landing page                    |
| `/about`         | `About`             | No            | Company info                    |
| `/features`      | `Features`          | No            | Feature breakdown               |
| `/pricing`       | `Pricing`           | No            | Plans and pricing               |
| `/login`         | `Login`             | No            | Shop owner / admin login        |
| `/signup`        | `Signup`            | No            | Multi-step registration         |
| `/dashboard`     | `Dashboard`         | Yes (owner)   | Main shop owner dashboard       |
| `/dashboard/customers` | `Customers`   | Yes (owner)   | Customer database management    |
| `/dashboard/campaigns` | `Campaigns`   | Yes (owner)   | WhatsApp campaign management    |
| `/dashboard/offers`    | `Offers`      | Yes (owner)   | Offer and coupon creator        |
| `/dashboard/analytics` | `Analytics`   | Yes (owner)   | Performance analytics           |
| `/dashboard/schedule`  | `Schedule`    | Yes (owner)   | Campaign scheduling             |
| `/dashboard/settings`  | `Settings`    | Yes (owner)   | Profile and integrations        |
| `/admin`         | `AdminDashboard`    | Yes (admin)   | Platform admin panel            |
| `/contact`       | `Contact`           | No            | Contact form                    |
| `/faq`           | `FAQ`               | No            | Frequently asked questions      |
| `/privacy`       | `Privacy`           | No            | Privacy policy                  |
| `/terms`         | `Terms`             | No            | Terms and con
