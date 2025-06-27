# 🧠 AI Knowledge Hub

A full-stack **note and task management** web app powered by **Node.js**, **MongoDB**, **JWT Authentication**, and future **AI integration** (e.g., GPT-4o). Designed to be fast, secure, and extendable — with AI-assisted summaries and productivity tools.

---

## 📁 Project Structure Till Now

```
ai-knowledge-hub/
├── client/                # React frontend
│   └── .gitkeep           # Until frontend is started
├── server/                # Node.js backend
│   ├──source
│   │   ├── controllers/
│   │   ├── db/
│   │   ├── middlewares/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── utils/
│   │   ├── app.js
│   │   ├── constants.js
│   │   └── server.js
├── config/                # env configs
└── README.md
```

---

## 🚀 Features

- ✅ User registration & login (with JWT)
- ✅ Access & refresh token generation
- ✅ Secure cookie-based auth (`httpOnly`, `secure`)
- ✅ Protected API routes (`verifyJWT` middleware)
- ✅ Notes: create, fetch, update, delete
- ✅ Tasks: create, fetch, update, delete
- ✅ Subtasks: fully integrated with task-based linkage
- 🧠 AI Integration (planned using Mistral: Mistral 7B Instruct )
- 📎 Modular folder structure with clean code practices

---

## 🔐 Auth Flow

- Access Token (short-lived) stored in secure cookies
- Refresh Token (longer-lived) saved in DB and cookie
- `verifyJWT` middleware protects all sensitive routes
- `/me` route to fetch currently logged-in user
- `/refresh-tokens` endpoint to rotate tokens
- `/logout` endpoint clears session

---

## 📌 API Overview

> All routes are prefixed with `/api/v1/`

### 🧑‍💻 Auth (Prefixed with /users)

| Method | Route             | Description         |
| ------ | ----------------- | ------------------- |
| POST   | `/register`       | Register new user   |
| POST   | `/login`          | Login user          |
| GET    | `/me`             | Get current user    |
| POST   | `/logout`         | Logout user         |
| POST   | `/refresh-tokens` | Rotate access token |

---

### 📝 Notes

| Method | Route        | Description                  |
| ------ | ------------ | ---------------------------- |
| POST   | `/notes/`    | Create a new note            |
| GET    | `/notes/`    | Fetch all notes (user-based) |
| GET    | `/notes/:id` | Fetch a specific note        |
| POST   | `/notes/:id` | Update a note                |
| DELETE | `/notes/:id` | Delete a note                |

---

### ✅ Tasks

| Method | Route                  | Description               |
| ------ | ---------------------- | ------------------------- |
| POST   | `/tasks/`              | Create a new task         |
| GET    | `/tasks/`              | Fetch all tasks           |
| GET    | `/tasks/:id`           | Fetch a specific task     |
| POST   | `/tasks/:id`           | Update a task             |
| DELETE | `/tasks/:id`           | Delete a task             |
| GET    | `tasks/tasks-with-subtasks/` | Fetch tasks with subtasks |

---

### 🔁 Subtasks

| Method | Route                           | Description               |
| ------ | ------------------------------- | ------------------------- |
| POST   | `/tasks/:id/subtask`            | Create subtask for task   |
| GET    | `/tasks/:id/subtask`            | Get all subtasks for task |
| POST   | `/tasks/:id/subtask/:subtaskId` | Update specific subtask   |
| DELETE | `/tasks/:id/subtask/:subtaskId` | Delete specific subtask   |

> 🧠 AI endpoints for summarization will be added soon.

---

## ⚙️ Tech Stack

- **Frontend:** React, Redux, Tailwind (planned)
- **Backend:** Node.js, Express.js
- **Database:** MongoDB (Mongoose ODM)
- **Auth:** JWT, Refresh Tokens, HTTP-only Cookies
- **AI Integration:** Mistral: Mistral 7B Instruct (planned)
- **Dev Tools:** Postman, dotenv, ES6 modules

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

### 🔐 ENV Configuration (server/.env)

```ini
PORT=8000
MONGODB_URI=your-mongo-db-uri
CORS_ORIGIN=set-for-your-network
ACCESS_TOKEN_SECRET=your-access-token-secret
ACCESS_TOKEN_EXPIRY=preffered-expiry-for-access-token
REFRESH_TOKEN_SECRET=your-refresh-token-secret
REFRESH_TOKEN_EXPIRY=preffered-expiry-for-refresh-token
```

## 📌 Todo (Next Steps)

⬜ AI Integration with Mistral: Mistral 7B Instruct for summarizing notes/tasks  
✅ Subtask APIs (create, update, delete)  
⬜ React frontend with protected routes and UI  
⬜ Add validation & rate-limiting middleware  
⬜ Dockerize the backend and frontend (optional)
