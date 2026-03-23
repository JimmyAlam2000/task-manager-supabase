# 📝 Task Manager

A full-stack Task Manager application built with **React**, **TypeScript**, **Vite**, and **Supabase**. Designed with a secure, scalable backend and a clean, responsive frontend.

🌐 **Website:** [https://task-manager-supabase-ashen.vercel.app](https://task-manager-supabase-ashen.vercel.app)

---

## ✨ Features

- 🔐 **User Authentication** — Secure sign up and sign in with email & password
- ✅ **Create Tasks** — Add tasks with a title, description and optional image
- 📋 **View Tasks** — See all your tasks loaded in real time
- ✏️ **Edit Tasks** — Update task descriptions instantly
- 🗑️ **Delete Tasks** — Remove tasks with one click
- 🖼️ **Image Uploads** — Attach images to tasks stored in Supabase Storage
- 🔒 **Data Privacy** — Each user can only see and manage their own tasks

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| React 18 | Frontend UI |
| TypeScript | Type-safe codebase |
| Vite | Lightning-fast build tool |
| Supabase | Backend as a Service |
| Vercel | Frontend deployment |

---

## 🗄️ Backend Architecture (Supabase)

### Authentication
Supabase Auth handles user registration and login using email/password. Sessions are managed automatically with JWT tokens.

### Database (PostgreSQL)
Tasks are stored in a PostgreSQL database hosted on Supabase with the following structure:

| Column | Type | Description |
|--------|------|-------------|
| id | int8 | Auto-incremented primary key |
| title | text | Task title |
| description | text | Task description |
| image_url | text | URL of uploaded image |
| email | text | Owner's email for RLS |
| created_at | timestamptz | Auto-generated timestamp |

### Row Level Security (RLS)
RLS policies are enforced at the database level to ensure users can only access and modify their own data:
- **SELECT** — Public read access per user
- **INSERT** — Authenticated users only
- **UPDATE** — Restricted to the task owner via email
- **DELETE** — Restricted to the task owner via email

### Storage
Images are uploaded to a dedicated **Supabase Storage** bucket (`tasks-images`) with public URL access, keeping media separate from the database.

### Real-time
Supabase Realtime is used to listen for new task insertions and update the UI instantly without a page refresh.

---

## 🙋‍♂️ Author

**Farhan** — [@JimmyAlam2000](https://github.com/JimmyAlam2000)
