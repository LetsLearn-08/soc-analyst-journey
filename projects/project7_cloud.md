# NexusAuth — Full-Stack Secure Authentication

> This project demonstrates a secure full‑stack authentication system built with Node.js, React, and MongoDB.
It extends my SOC Analyst journey into software engineering workflows, focusing on secure login, session management, and cyberpunk‑themed UI design.
The goal is to showcase how authentication systems can be implemented with modern frameworks while maintaining strong security practices.

---

## 📝 Explanation
- Designed a Node.js + Express backend with MongoDB for user management.  
- Implemented JWT sessions for secure authentication and token validation.  
- Integrated bcrypt password hashing for strong credential protection.  
- Built a React frontend with protected routes and cyberpunk styling.  
- Added middleware for token verification and role‑based access control.  
- Documented deployment steps for Render, Heroku, and Netlify to ensure portability.  
- Captured screenshots and proof artifacts to validate functionality and UI.  

---

## 📸 Screenshots

| Auth Page | Dashboard |
|-----------|-----------|
| ![Auth Page](screenshots/auth-page.png) | ![Dashboard](screenshots/dashboard.png) |

---

## 🏗 Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | React 18, React Router v6, Axios |
| **Backend** | Node.js, Express |
| **Database** | MongoDB (Mongoose ODM) |
| **Auth** | JWT (jsonwebtoken), bcryptjs |
| **Styling** | Custom CSS (Orbitron + Share Tech Mono fonts) |

---

## 📁 Project Structure

```
auth-app/
├── backend/
│   ├── models/
│   │   └── User.js          # Mongoose schema with bcrypt hooks
│   ├── middleware/
│   │   └── auth.js          # JWT verification middleware
│   ├── routes/
│   │   ├── auth.js          # /register, /login, /me, /logout
│   │   └── dashboard.js     # Protected /dashboard route
│   ├── server.js            # Express app entry point
│   ├── .env.example
│   └── package.json
├── frontend/
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── context/
│   │   │   └── AuthContext.js   # Auth state + axios defaults
│   │   ├── pages/
│   │   │   ├── AuthPage.js      # Login + Register
│   │   │   ├── AuthPage.css
│   │   │   ├── Dashboard.js     # Protected dashboard
│   │   │   └── Dashboard.css
│   │   ├── App.js               # Router + private/public routes
│   │   ├── App.css              # Global cyberpunk styles
│   │   └── index.js
│   ├── .env.example
│   └── package.json
└── README.md
```

---

## 🚀 Local Development Setup

### Prerequisites
- **Node.js** v18+ ([download](https://nodejs.org))
- **MongoDB** — local install **or** [MongoDB Atlas](https://www.mongodb.com/atlas) (free tier)
- **npm** or **yarn**

---

### Step 1 — Clone & Install

```bash
git clone https://github.com/your-username/nexusauth.git
cd nexusauth

# Install backend dependencies
cd backend
npm install

# Install frontend dependencies
cd ../frontend
npm install
```

---

### Step 2 — Configure Environment Variables

**Backend** (`backend/.env`):
```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/authapp
JWT_SECRET=your_super_secret_key_at_least_32_chars
JWT_EXPIRES_IN=7d
CLIENT_URL=http://localhost:3000
```

> For MongoDB Atlas, replace `MONGO_URI` with your connection string:
> `mongodb+srv://<user>:<pass>@cluster.mongodb.net/authapp?retryWrites=true`

**Frontend** (`frontend/.env`):
```env
REACT_APP_API_URL=http://localhost:5000/api
```

---

### Step 3 — Run the Application

Open **two terminals**:

```bash
# Terminal 1 — Backend
cd backend
npm run dev          # uses nodemon for hot reload
# ✅ Server running on port 5000

# Terminal 2 — Frontend
cd frontend
npm start
# ✅ React app on http://localhost:3000
```

Visit **http://localhost:3000** in your browser.

---

## 🔌 API Reference

### `POST /api/auth/register`
Register a new user.

**Request body:**
```json
{
  "username": "cyberuser",
  "email": "user@example.com",
  "password": "secure123"
}
```

**Response (201):**
```json
{
  "message": "Account created successfully.",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": { "_id": "...", "username": "cyberuser", "email": "user@example.com" }
}
```

---

### `POST /api/auth/login`
Authenticate an existing user.

**Request body:**
```json
{
  "email": "user@example.com",
  "password": "secure123"
}
```

**Response (200):**
```json
{
  "message": "Login successful.",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": { ... }
}
```

---

### `GET /api/dashboard` *(protected)*
Get dashboard data for authenticated user.

**Headers:**
```
Authorization: Bearer <token>
```

**Response (200):**
```json
{
  "message": "Welcome back, cyberuser!",
  "user": { ... },
  "stats": {
    "accountAge": 5,
    "lastLogin": "2026-04-24T10:30:00.000Z",
    "securityScore": 85
  }
}
```

---

### `GET /api/auth/me` *(protected)*
Verify token and return current user.

### `POST /api/auth/logout` *(protected)*
Acknowledge logout (client removes token).

---

## ☁️ Deployment

### Deploy to Render (Recommended — Free Tier)

#### Backend
1. Push code to GitHub
2. Go to [render.com](https://render.com) → **New Web Service**
3. Connect your repo, select the `backend/` folder as root
4. Set:
   - **Build Command:** `npm install`
   - **Start Command:** `npm start`
5. Add **Environment Variables** (all from `.env` above)
6. Deploy → copy your backend URL (e.g. `https://nexusauth-api.onrender.com`)

#### Frontend
1. Go to Render → **New Static Site**
2. Connect repo, select `frontend/` as root
3. Set:
   - **Build Command:** `npm install && npm run build`
   - **Publish Directory:** `build`
   - **Environment Variable:** `REACT_APP_API_URL=https://nexusauth-api.onrender.com/api`
4. Deploy

---

### Deploy to Heroku

#### Backend
```bash
cd backend
heroku create nexusauth-api
heroku config:set MONGO_URI="your_atlas_uri"
heroku config:set JWT_SECRET="your_secret"
heroku config:set CLIENT_URL="https://your-frontend.netlify.app"
git subtree push --prefix backend heroku main
```

#### Frontend
Deploy to [Netlify](https://netlify.com) (drag & drop the `build/` folder after `npm run build`), then set `REACT_APP_API_URL` in Netlify env vars.

---

## 🔒 Security Features

| Feature | Implementation |
|---|---|
| Password hashing | bcrypt with 12 salt rounds |
| Session management | JWT (7-day expiry, signed with secret) |
| Protected routes | Middleware validates Bearer token on every request |
| Input validation | Mongoose schema-level validation |
| CORS protection | Origin-restricted via `CLIENT_URL` env var |
| Sensitive field removal | `toJSON()` strips password before response |

---

## 💡 Usage Examples

### Register via cURL
```bash
curl -X POST http://localhost:5000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"username":"hacker","email":"hacker@nexus.io","password":"cyber2099"}'
```

### Access protected dashboard
```bash
TOKEN="eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
curl http://localhost:5000/api/dashboard \
  -H "Authorization: Bearer $TOKEN"
```

---

## 🛠 Development Notes

- JWT tokens are stored in `localStorage`. For production, consider `httpOnly` cookies.
- Add **rate limiting** (`express-rate-limit`) before deploying publicly.
- Use **helmet.js** to set security HTTP headers in production.
- Enable **refresh tokens** for better session management.

---

## 📄 License

MIT — free to use, modify, and deploy.

---

---

## 📂 Resources

This project is organized into separate folders for clarity. Each folder contains code, configuration, or documentation relevant to NexusAuth.

| Folder / File | Description | Link |
|---------------|-------------|------|
| `backend/` | Node.js + Express backend with routes, models, middleware, and server entry point | [backend/](backend/) |
| `backend/models/User.js` | Mongoose schema with bcrypt hooks for password hashing | [User.js](backend/models/User.js) |
| `backend/middleware/auth.js` | JWT verification middleware for protected routes | [auth.js](backend/middleware/auth.js) |
| `backend/routes/auth.js` | Authentication routes (`/register`, `/login`, `/me`, `/logout`) | [auth.js](backend/routes/auth.js) |
| `backend/routes/dashboard.js` | Protected dashboard route | [dashboard.js](backend/routes/dashboard.js) |
| `backend/server.js` | Express app entry point | [server.js](backend/server.js) |
| `frontend/` | React frontend with pages, context, and cyberpunk styling | [frontend/](frontend/) |
| `frontend/src/context/AuthContext.js` | Global auth state + axios defaults | [AuthContext.js](frontend/src/context/AuthContext.js) |
| `frontend/src/pages/AuthPage.js` | Login + Register page | [AuthPage.js](frontend/src/pages/AuthPage.js) |
| `frontend/src/pages/Dashboard.js` | Protected dashboard page | [Dashboard.js](frontend/src/pages/Dashboard.js) |
| `frontend/src/App.js` | Router setup with private/public routes | [App.js](frontend/src/App.js) |
| `frontend/src/App.css` | Global cyberpunk styles | [App.css](frontend/src/App.css) |
| `screenshots/` | UI screenshots for proof artifacts | [screenshots/](screenshots/) |
| `README.md` | Project documentation (this file) | [README.md](README.md) |

---

---

## 🔗 Connect With Me

I actively share my SOC journey, projects, and proof artifacts on GitHub and LinkedIn.  
Feel free to explore my work or connect with me professionally:

- **GitHub:** [LetsLearn‑08](https://github.com/LetsLearn-08?tab=repositories)  
- **LinkedIn:** [Tanuja Reddy](https://www.linkedin.com/in/tanuja-reddy-03aa7b38a)


