<p align="center">
  <img src="frontend/src/assets/spendlex-logo.jpeg" alt="Spendlex Logo" width="120" height="120" style="border-radius: 20px;" />
</p>

<h1 align="center">Spendlex</h1>

<p align="center">
  <strong>Smart Financial Intelligence for Everyday Spending</strong>
</p>

<p align="center">
  <a href="https://spendlex.vercel.app/">Live Demo</a> &nbsp;&bull;&nbsp;
  <a href="https://interswitch-hackathon-4w5u.onrender.com/">API Server</a>
</p>

---

## Overview

**Spendlex** is a personal finance management platform that empowers users to take control of their spending habits through real-time transaction tracking, intelligent budgeting, and AI-driven financial insights. Built for the **Interswitch Hackathon**, Spendlex transforms raw financial data into actionable intelligence — helping users spend smarter, save more, and build healthier financial habits.

## Key Features

### Transaction Management
- Record income and expenses with category tagging
- Search, filter, and organize transactions by type and date
- Monthly spending summaries with category-level breakdowns

### Smart Budgeting
- Set spending limits per category (Food, Transport, Shopping, Bills, etc.)
- Real-time budget utilization tracking with visual progress indicators
- Automatic alerts when spending approaches or exceeds limits

### Analytics & Trends
- Month-over-month spending comparison
- 6-month spending trend visualizations
- Category-wise spending distribution with percentage breakdowns

### Financial Health Score
- Composite health score (0–100) based on multiple metrics:
  - **Spending Velocity** — Income-to-expense ratio
  - **Savings Rate** — Percentage of income saved
  - **Budget Adherence** — How well spending aligns with set budgets

### AI-Powered Insights
- Spending anomaly detection (flags >20% category increases)
- Budget overrun warnings at 90%+ utilization
- Savings opportunity identification from recurring purchases
- Natural language Q&A — ask questions about your finances in plain English

### WhatsApp OTP Verification
- Phone number verification via Interswitch's WhatsApp OTP API
- Secure user authentication with JWT-based sessions

## Tech Stack

| Layer        | Technology                                                  |
|--------------|-------------------------------------------------------------|
| **Frontend** | React 18, TypeScript, Vite, Tailwind CSS, Framer Motion     |
| **Backend**  | Node.js, Express.js                                         |
| **Database** | Supabase (PostgreSQL)                                       |
| **Auth**     | JWT, Interswitch WhatsApp OTP                                |
| **Charts**   | Recharts                                                     |
| **UI**       | Radix UI Primitives, Lucide Icons, Sonner Toasts             |
| **State**    | TanStack React Query, React Context                          |
| **Validation** | Zod, React Hook Form                                      |
| **Deployment** | Vercel (Frontend), Render (Backend)                        |

## Project Structure

```
Interswitch-Hackathon/
├── backend/
│   └── src/
│       ├── server.js              # Express entry point
│       ├── config/                # Supabase & Interswitch config
│       ├── middleware/            # JWT auth middleware
│       ├── routes/                # API route handlers
│       │   ├── auth.js            # Signup, login, OTP
│       │   ├── profile.js         # User profile management
│       │   ├── transactions.js    # Transaction CRUD & summaries
│       │   ├── budgets.js         # Budget CRUD & tracking
│       │   ├── analytics.js       # Spending analysis & health score
│       │   └── insights.js        # AI insights & Q&A
│       └── services/              # External API integrations
│
├── frontend/
│   └── src/
│       ├── pages/                 # Application screens
│       ├── components/            # Reusable UI components
│       ├── context/               # Auth state management
│       ├── services/              # Typed API client
│       ├── hooks/                 # Custom React hooks
│       └── lib/                   # Utility functions
```

## API Endpoints

| Method   | Endpoint                  | Description                          |
|----------|---------------------------|--------------------------------------|
| `POST`   | `/api/auth/signup`        | Register a new user                  |
| `POST`   | `/api/auth/login`         | Authenticate and receive JWT         |
| `POST`   | `/api/auth/send-otp`      | Send WhatsApp OTP                    |
| `POST`   | `/api/auth/verify-otp`    | Verify OTP code                      |
| `GET`    | `/api/auth/me`            | Get current user                     |
| `GET`    | `/api/profile`            | Fetch user profile                   |
| `PUT`    | `/api/profile`            | Update user profile                  |
| `GET`    | `/api/transactions`       | List transactions (filter/search)    |
| `POST`   | `/api/transactions`       | Create a transaction                 |
| `DELETE` | `/api/transactions/:id`   | Delete a transaction                 |
| `GET`    | `/api/transactions/summary` | Monthly spending summary           |
| `GET`    | `/api/budgets`            | List budgets with spending data      |
| `POST`   | `/api/budgets`            | Create a budget                      |
| `PUT`    | `/api/budgets/:id`        | Update a budget                      |
| `DELETE` | `/api/budgets/:id`        | Delete a budget                      |
| `GET`    | `/api/analytics/spending` | Monthly spending comparison          |
| `GET`    | `/api/analytics/trends`   | 6-month spending trends              |
| `GET`    | `/api/analytics/financial-health` | Financial health score        |
| `GET`    | `/api/insights`           | Auto-generated financial insights    |
| `POST`   | `/api/insights/ask`       | Natural language financial Q&A       |

## Getting Started

### Prerequisites

- Node.js 16+
- A [Supabase](https://supabase.com) project
- Interswitch API credentials (for WhatsApp OTP)

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/Interswitch-Hackathon.git
cd Interswitch-Hackathon
```

**Backend:**

```bash
cd backend
npm install
cp .env.example .env
# Configure your environment variables (see below)
npm run dev
```

**Frontend:**

```bash
cd frontend
npm install
npm run dev
```

The frontend runs on `http://localhost:8080` and proxies API requests to the backend on port `3001`.

### Environment Variables

Create a `.env` file in the `backend/` directory:

```env
# Supabase
SUPABASE_URL=your_supabase_project_url
SUPABASE_ANON_KEY=your_supabase_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_role_key

# Authentication
JWT_SECRET=your_jwt_secret

# Interswitch
INTERSWITCH_CLIENT_ID=your_client_id
INTERSWITCH_CLIENT_SECRET=your_client_secret
INTERSWITCH_BASE_URL=https://qa.interswitchng.com
INTERSWITCH_TERMINAL_ID=your_terminal_id

# Server
PORT=3001
NODE_ENV=development
FRONTEND_URL=http://localhost:8080
```

## Database Schema

The application uses four core tables in Supabase:

| Table          | Purpose                                    |
|----------------|--------------------------------------------|
| `users`        | User accounts with auth credentials        |
| `transactions` | Income and expense records                 |
| `budgets`      | Category-based spending limits             |
| `otp_codes`    | Temporary OTP storage for verification     |

## Deployment

| Service    | Platform | URL                                                        |
|------------|----------|------------------------------------------------------------|
| Frontend   | Vercel   | [spendlex.vercel.app](https://spendlex.vercel.app/)        |
| Backend    | Render   | [interswitch-hackathon-4w5u.onrender.com](https://interswitch-hackathon-4w5u.onrender.com/) |

## Team

Built with dedication for the **Interswitch Hackathon**.

---

<p align="center">
  <sub>Made with purpose. Spend smarter with <strong>Spendlex</strong>.</sub>
</p>
