# 💰 FinTrack AI — Smart Personal Finance Tracker

<div align="center">

![FinTrack AI](https://img.shields.io/badge/FinTrack-AI-0ea5e9?style=for-the-badge&logo=react)
![React](https://img.shields.io/badge/React-18-61dafb?style=flat-square&logo=react)
![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=flat-square&logo=node.js)
![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?style=flat-square&logo=mongodb)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

**AI-powered full-stack personal finance management platform built with MERN stack**

[Features](#features) • [Tech Stack](#tech-stack) • [Installation](#installation) • [API Docs](#api-endpoints) • [Deployment](#deployment)

</div>

---

## 📸 Screenshots

> _Dashboard, Analytics, Transactions, Budget pages — dark fintech UI_

---

## ✨ Features

### 🔐 Authentication
- JWT-based secure authentication
- bcrypt password hashing
- Protected frontend routes and backend APIs
- Auto token refresh

### 📊 Dashboard
- Real-time financial summary (balance, income, expenses, savings)
- AI-generated financial insights
- Monthly budget progress tracker
- Recent transactions feed

### 💳 Transaction Management
- Add, edit, delete income/expense transactions
- 11 categories with emoji icons
- Search & filter by type, category, date
- Export transaction history as PDF

### 📈 Analytics
- Pie chart: category-wise spending
- Bar chart: 6-month income vs expense
- Line chart: savings trend
- Monthly spending breakdown
- AI spending analysis panel

### 🎯 Budget Management
- Set monthly total budget
- Per-category budget allocation
- Visual progress bars with color-coded warnings
- Budget exceeded alerts

### 👤 Profile
- Update name, currency, budget
- Change password
- Account info panel

---

## 🛠 Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18 + Vite |
| Styling | Tailwind CSS |
| Routing | React Router DOM v6 |
| Charts | Recharts |
| Animations | Framer Motion |
| HTTP Client | Axios |
| Backend | Node.js + Express.js |
| Database | MongoDB Atlas + Mongoose |
| Authentication | JWT + bcryptjs |
| PDF Export | jsPDF + autotable |
| Deployment | Vercel (FE) + Render (BE) |

---

## 📁 Project Structure

```
fintrack-ai/
├── client/                    # React Frontend (Vite)
│   ├── src/
│   │   ├── components/        # Reusable UI components
│   │   ├── pages/             # Route pages
│   │   │   ├── LoginPage.jsx
│   │   │   ├── RegisterPage.jsx
│   │   │   ├── DashboardPage.jsx
│   │   │   ├── TransactionsPage.jsx
│   │   │   ├── AnalyticsPage.jsx
│   │   │   ├── BudgetPage.jsx
│   │   │   └── ProfilePage.jsx
│   │   ├── context/           # React Context (Auth)
│   │   ├── services/          # API service layer
│   │   ├── layouts/           # MainLayout (sidebar)
│   │   └── App.jsx
│   ├── tailwind.config.js
│   └── vite.config.js
│
└── server/                    # Node.js Backend
    ├── controllers/
    │   ├── authController.js
    │   ├── transactionController.js
    │   ├── analyticsController.js
    │   ├── budgetController.js
    │   └── profileController.js
    ├── routes/
    ├── models/
    │   ├── User.js
    │   ├── Transaction.js
    │   └── Budget.js
    ├── middleware/
    │   └── auth.js
    └── server.js
```

---

## 🚀 Installation

### Prerequisites
- Node.js 18+
- npm or yarn
- MongoDB Atlas account (free tier works)

### 1. Clone the repository
```bash
git clone https://github.com/yourusername/fintrack-ai.git
cd fintrack-ai
```

### 2. Backend Setup
```bash
cd server
npm install
cp .env.example .env
# Edit .env with your MongoDB URI and JWT secret
npm run dev
```

### 3. Frontend Setup
```bash
cd client
npm install
cp .env.example .env
# Set VITE_API_URL=http://localhost:5000/api
npm run dev
```

### 4. Open app
- Frontend: http://localhost:5173
- Backend API: http://localhost:5000/api

---

## 🔑 Environment Variables

### Backend (`server/.env`)
```env
PORT=5000
MONGO_URI=mongodb+srv://<user>:<password>@cluster0.mongodb.net/fintrack-ai
JWT_SECRET=your_secret_key_min_32_chars
CLIENT_URL=http://localhost:5173
```

### Frontend (`client/.env`)
```env
VITE_API_URL=http://localhost:5000/api
```

---

## 📡 API Endpoints

### Auth
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | Register new user |
| POST | `/api/auth/login` | Login user |
| GET | `/api/auth/me` | Get current user |

### Transactions
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/transactions` | Get transactions (with filters) |
| POST | `/api/transactions` | Create transaction |
| PUT | `/api/transactions/:id` | Update transaction |
| DELETE | `/api/transactions/:id` | Delete transaction |

### Analytics
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/analytics/summary` | Financial summary |
| GET | `/api/analytics/charts` | Chart data |
| GET | `/api/analytics/insights` | AI insights |

### Budget
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/budget` | Set/update budget |
| GET | `/api/budget` | Get budget with usage |

### Profile
| Method | Endpoint | Description |
|--------|----------|-------------|
| PUT | `/api/profile` | Update profile |
| PUT | `/api/profile/password` | Change password |

---

## 🌐 Deployment

### Backend → Render
1. Push to GitHub
2. Create new Web Service on [render.com](https://render.com)
3. Set `root directory` to `server`
4. Build command: `npm install`
5. Start command: `npm start`
6. Add environment variables in Render dashboard

### Frontend → Vercel
1. Push to GitHub
2. Import project on [vercel.com](https://vercel.com)
3. Set `root directory` to `client`
4. Add env var: `VITE_API_URL=https://your-render-api.onrender.com/api`
5. Deploy!

### Database → MongoDB Atlas
1. Create cluster at [cloud.mongodb.com](https://cloud.mongodb.com)
2. Create database user
3. Whitelist `0.0.0.0/0` (all IPs) for Render
4. Copy connection string to `MONGO_URI`

---

## 🧠 AI Insights Logic

The AI insights engine in `analyticsController.js` analyzes:
- Month-over-month category spending changes (>15% triggers alert)
- Savings trend comparison
- Budget utilization warnings (>70%, >90%)
- Income-to-spending ratio
- Top spending category detection

All insights are generated dynamically from your MongoDB transaction data — no external AI API required.

---

## 🔮 Future Improvements

- [ ] Voice-based expense entry
- [ ] OCR bill/receipt scanner
- [ ] Email/SMS notifications
- [ ] Real-time updates (Socket.io)
- [ ] Recurring expenses automation
- [ ] Savings goals tracker
- [ ] Dark/light mode toggle
- [ ] Multi-currency support
- [ ] Bank statement import (CSV)
- [ ] GPT-powered personalized advice

---

## 👨‍💻 Author

Built by **Manoj Kumar B** | CSE Final Year | Bangalore

---

## 📄 License

MIT License — free to use and modify
