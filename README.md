# 🏔️ Sacred Sikkim — Monasteries of the Himalayas

A full-stack tourism web app to digitize and showcase the monasteries of Sikkim.

## Tech Stack
- **Frontend:** React 18 + Vite, React Router, Tailwind CSS
- **Backend:** Node.js + Express
- **Database:** `node:sqlite` — **built into Node 22+, zero npm install needed**
- **Auth:** JWT + bcrypt

## ✅ Prerequisites
- Node.js **v22 or higher** (you're on v25 — perfect)
- No native addons. No compilation. No `better-sqlite3`.

## Getting Started

### Backend
```bash
cd backend
npm install          # only installs express, cors, bcryptjs, dotenv, jsonwebtoken
npm start            # runs: node --experimental-sqlite server.js
```
Server starts at **http://localhost:5000**

### Frontend
```bash
cd frontend
npm install
npm run dev
```
App opens at **http://localhost:5173**

### Default Admin Login
- Email: `admin@sacredsikkim.com`
- Password: `admin123`

---

## Project Structure
```
sikkim-monasteries/
├── backend/
│   ├── server.js                  ← Express entry point
│   ├── config/config.js           ← Env vars
│   ├── db/database.js             ← node:sqlite init + seed
│   ├── middleware/                ← JWT auth, error handler
│   ├── controllers/               ← auth, monasteries, reviews, favourites
│   └── routes/                    ← auth, monasteries, reviews, favourites
│
└── frontend/
    └── src/
        ├── api/index.js           ← Axios calls
        ├── context/               ← AuthContext, FavouritesContext
        ├── hooks/                 ← useMonasteries, useMonastery
        ├── components/
        │   ├── common/            ← Navbar, Footer, Loader, ProtectedRoute
        │   ├── monastery/         ← MonasteryCard, FilterBar, ReviewSection
        │   ├── auth/              ← AuthForm
        │   └── admin/             ← MonasteryForm
        └── pages/                 ← Home, Explore, Detail, Festivals,
                                      Login, Register, Favourites, Admin
```

## API Endpoints

| Method | Route | Auth | Description |
|--------|-------|------|-------------|
| POST | /api/auth/register | — | Register |
| POST | /api/auth/login | — | Login → JWT |
| GET | /api/auth/me | JWT | Current user |
| GET | /api/monasteries | — | List (filter: district, sect, search) |
| GET | /api/monasteries/:id | — | Detail + reviews |
| POST | /api/monasteries | Admin | Create |
| PUT | /api/monasteries/:id | Admin | Update |
| DELETE | /api/monasteries/:id | Admin | Delete |
| GET | /api/reviews/:monasteryId | — | Reviews list |
| POST | /api/reviews/:monasteryId | JWT | Add review |
| DELETE | /api/reviews/:id | JWT/Admin | Delete review |
| GET | /api/favourites | JWT | My saved list |
| POST | /api/favourites/:id | JWT | Save |
| DELETE | /api/favourites/:id | JWT | Unsave |
