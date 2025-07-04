# 🧠 Synote

A full-stack **note and task management** web app powered by **Node.js**, **MongoDB**, **JWT Authentication**, and **AI integration** (Mistral 7B Instruct). Designed to be fast, secure, and extendable — with AI-assisted summaries and productivity tools.

---

## 📁 Project Structure

```
synote/
├── client/                # React frontend using Vite
│   ├── public/            # Public assets (e.g., avatar SVGs)
│   ├── src/
│   │   ├── assets/         # Static assets
│   │   ├── components/     # Reusable UI components
│   │   ├── lib/            # Utility functions
│   │   ├── pages/          # Route pages
│   │   ├── services/       # API service functions
│   │   ├── store/          # Redux slices
│   │   ├── App.jsx
│   │   ├── index.css
│   │   └── main.jsx
├── server/                # Node.js backend using Express
│   ├── source/
│   │   ├── controllers/    # Route logic
│   │   ├── db/             # DB connection setup
│   │   ├── middlewares/    # Auth & error middlewares
│   │   ├── models/         # Mongoose models
│   │   ├── routes/         # Express routes
│   │   ├── services/       # Token / AI / utility services
│   │   ├── utils/          # Misc helpers
│   │   ├── app.js
│   │   ├── constants.js
│   │   └── server.js
└── README.md
```

---

## 🚀 Features

* ✅ User registration & login (JWT-based)
* ✅ Secure cookies (`httpOnly`, `secure`) for access/refresh tokens
* ✅ Protected API routes with `verifyJWT` middleware
* ✅ Notes: create, fetch, update, delete
* ✅ Tasks: create, fetch, update, delete
* ✅ Subtasks: fully integrated with task structure
* ✅ Avatar picker system (SVG-based avatars)
* ✅ AI-powered summarization (Mistral 7B Instruct via OpenRouter)
* ✅ Redux state management for auth & user
* ✅ Tailwind CSS for styling
* ✅ React Router DOM for SPA routing
* 📎 Modular code with clean practices

---

## 🔐 Auth Flow

* Access Token (short-lived) in secure cookies
* Refresh Token (longer-lived) stored in DB + cookie
* `verifyJWT` middleware protects routes
* `/me` returns current user info
* `/refresh-tokens` rotates tokens
* `/logout` ends session

---

## 📌 API Overview

> All routes are prefixed with `/api/v1/`

### 👨‍💻 Auth (`/users`)

| Method | Route             | Description                  |
| ------ | ----------------- | ---------------------------- |
| POST   | `/register`       | Register new user            |
| POST   | `/login`          | Login user                   |
| GET    | `/me`             | Get current user             |
| POST   | `/logout`         | Logout user                  |
| POST   | `/refresh-tokens` | Rotate access token          |
| PATCH  | `/me`             | Update current user (avatar) |

---

### 📝 Notes

| Method | Route        | Description                  |
| ------ | ------------ | ---------------------------- |
| POST   | `/notes/`    | Create a new note            |
| GET    | `/notes/`    | Fetch all notes (user-based) |
| GET    | `/notes/:id` | Fetch a specific note        |
| PATCH  | `/notes/:id` | Update a note                |
| DELETE | `/notes/:id` | Delete a note                |

---

### ✅ Tasks

| Method | Route                         | Description               |
| ------ | ----------------------------- | ------------------------- |
| POST   | `/tasks/`                     | Create a new task         |
| GET    | `/tasks/`                     | Fetch all tasks           |
| GET    | `/tasks/:id`                  | Fetch a specific task     |
| PATCH  | `/tasks/:id`                  | Update a task             |
| DELETE | `/tasks/:id`                  | Delete a task             |
| GET    | `/tasks/tasks-with-subtasks/` | Fetch tasks with subtasks |

---

### ↻ Subtasks

| Method | Route                           | Description               |
| ------ | ------------------------------- | ------------------------- |
| POST   | `/tasks/:id/subtask`            | Create subtask for task   |
| GET    | `/tasks/:id/subtask`            | Get all subtasks for task |
| PATCH  | `/tasks/:id/subtask/:subtaskId` | Update specific subtask   |
| DELETE | `/tasks/:id/subtask/:subtaskId` | Delete specific subtask   |

---

### 🧠 AI-Powered Summarization

| Method | Route                         | Description               |
| ------ | ----------------------------- | ------------------------- |
| GET    | `/ai/notes/:noteId/summarize` | Summarize a specific note |
| GET    | `/ai/tasks/:id/summarize`     | Summarize a specific task |

---

## ⚙️ Tech Stack

* **Frontend:** React, Redux Toolkit, Tailwind CSS, React Router DOM
* **Backend:** Node.js, Express.js
* **Database:** MongoDB (via Mongoose)
* **Authentication:** JWT + refresh tokens (secure cookies)
* **AI:** Mistral 7B Instruct via [OpenRouter API](https://openrouter.ai)
* **Dev Tools:** Vite, Postman, dotenv, ESLint, Prettier

---

## 🔧 Setup & Running

### 🛠️ Backend

```bash
cd server
npm install
npm run dev
```

### 💻 Frontend

```bash
cd client
npm install
npm run dev
```

### 🔐 ENV Configuration (`server/.env`)

```ini
PORT=8000
MONGODB_URI=your-mongo-db-uri
CORS_ORIGIN=http://localhost:5173
ACCESS_TOKEN_SECRET=your-access-token-secret
ACCESS_TOKEN_EXPIRY=15m
REFRESH_TOKEN_SECRET=your-refresh-token-secret
REFRESH_TOKEN_EXPIRY=7d
OPEN_ROUTER_API_KEY=your-openrouter-api-key
```

### 🌐 ENV Configuration (`client/.env`)

```env
VITE_API_BASE_URL=http://localhost:8000/api/v1
```

---

## 📌 Todo

* ✅ AI Integration using Mistral 7B via OpenRouter
* ✅ Subtask APIs (create, update, delete)
* ✅ Avatar picker UI & backend integration
* ⬜ Protected routes & full UI in React
* ⬜ Add validation & rate-limiting middleware
* ⬜ Dockerize backend and frontend (optional)
