# Team Task Manager

A full-stack web application for managing projects, assigning tasks, and tracking team progress with role-based access control.

🔗 **Live Demo:** https://ethara-testing.up.railway.app/
📦 **Backend API:** https://task-manager-production-9cb0.up.railway.app/

---

## Features

- **Authentication** — Secure signup and login with JWT and bcrypt password hashing
- **Role-Based Access Control** — Admin and Member roles with different permissions
- **Project Management** — Create projects, manage team members
- **Task Management** — Create, assign, and track tasks with priority, due dates, and status
- **Dashboard** — Real-time overview of total, completed, in-progress, and overdue tasks

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React, React Router, Axios |
| Backend | Node.js, Express.js |
| Database | MongoDB Atlas (Mongoose) |
| Auth | JWT, bcryptjs |
| Deployment | Railway |

---

## Role-Based Access Control

| Feature | Admin | Member |
|---------|-------|--------|
| Create projects | ✅ | ❌ |
| Delete projects | ✅ | ❌ |
| Add members to project | ✅ | ❌ |
| Create tasks | ✅ | ❌ |
| Assign tasks | ✅ | ❌ |
| Delete tasks | ✅ | ❌ |
| Update task status | ✅ | ✅ (own tasks only) |
| View dashboard | ✅ | ✅ (own tasks only) |

---

## API Endpoints

### Auth
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/signup` | Register a new user |
| POST | `/api/auth/login` | Login and receive JWT token |

### Projects
| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| GET | `/api/projects` | Get all projects | All |
| POST | `/api/projects` | Create a project | Admin |
| PUT | `/api/projects/:id` | Update a project | Admin |
| DELETE | `/api/projects/:id` | Delete a project | Admin |
| GET | `/api/projects/users` | Get all users | Admin |

### Tasks
| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| GET | `/api/tasks` | Get all tasks | All |
| GET | `/api/tasks/dashboard` | Get dashboard stats | All |
| GET | `/api/tasks/project/:id` | Get tasks by project | All |
| POST | `/api/tasks` | Create a task | Admin |
| PUT | `/api/tasks/:id` | Update a task | Admin / Assigned Member |
| DELETE | `/api/tasks/:id` | Delete a task | Admin |

---

## Database Schema

### User
```
name, email, password (hashed), role (Admin/Member)
```

### Project
```
title, description, createdBy (User ref), members (User refs)
```

### Task
```
title, description, project (Project ref), assignedTo (User ref),
status (Todo/In Progress/Completed), priority (Low/Medium/High), dueDate
```

---

## Local Setup

### Prerequisites
- Node.js v16+
- MongoDB Atlas account

### Backend
```bash
cd task-manager/backend
npm install
```

Create a `.env` file:
```
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
PORT=5000
```

```bash
node index.js
```

### Frontend
```bash
cd task-manager/frontend
npm install
npm start
```

The app runs at `http://localhost:3000`

---

## Deployment

Both frontend and backend are deployed on **Railway**.

- Frontend auto-builds with Railpack (Caddy static server)
- Backend connects to MongoDB Atlas
- Environment variables managed via Railway dashboard

---

## Screenshots

**Admin Dashboard**
- Full task overview with stats cards
- Role badge showing Admin privileges

**Project Management**
- Create and edit projects
- Add/remove team members

**Task Management**
- Create tasks with priority, assignment, and due dates
- Edit and delete tasks (Admin only)
- Status updates with color coding

**Member View**
- Restricted to assigned tasks only
- Can only update status of own tasks
- Locked badge on unassigned tasks

---

## Author

Divyansh Yadav  
GitHub: [@Divyansh6661](https://github.com/Divyansh6661)
