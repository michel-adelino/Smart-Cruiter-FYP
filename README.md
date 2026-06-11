# Smart Cruiter

An applicant tracking system (ATS) that helps organizations manage their end-to-end hiring workflow—from job posting and candidate screening to interviews, offers, and reporting.

---

## Features

### For recruiters and organizations

- **Job management** — Create, publish, and manage job listings with rich descriptions and filters.
- **Recruitment pipeline** — Track candidates across stages: applied, recommended, interviewing, hired, rejected, and withdrawn.
- **Candidate profiles** — View applicant details, notes, feedback, and status history in one place.
- **Interview scheduling** — Set up online interviews and notify candidates by email.
- **Bulk email actions** — Send acceptance or rejection emails to many candidates at once.
- **Analytics & reporting** — Visualize hiring metrics and recruitment performance on the dashboard.
- **Team & settings** — Onboard organization profiles, manage employees, and update account settings.

### For job seekers (public portal)

- Browse open positions at `/portal/job`.
- View job descriptions and submit applications through a dedicated apply form.

---

## Tech Stack

| Layer      | Technologies |
| ---------- | ------------ |
| Frontend   | React 18, Vite, Redux Toolkit, React Router, Tailwind CSS, DaisyUI, Chakra UI, Chart.js, Recharts |
| Backend    | Node.js, Express |
| Database   | MongoDB (Mongoose) |
| Auth       | JWT, bcrypt |
| Storage    | Cloudinary (file uploads) |
| Email      | Nodemailer |
| Deployment | Vercel (client), Railway (API) |

---

## Project Structure

```
Smart-Cruiter-FYP/
├── Client/                 # React frontend (Vite)
│   └── src/
│       ├── Pages/          # Route-level views (Auth, Dashboard, Recruitment, etc.)
│       ├── Components/     # Reusable UI components
│       └── Features/       # Redux slices and state
└── Server/                 # Express API
    ├── Controllers/        # Request handlers
    ├── Models/             # Mongoose schemas
    ├── Routes/             # API route definitions
    ├── Middleware/         # Auth and validation
    └── Config/             # Database, Cloudinary, Multer
```

---

## Prerequisites

- [Node.js](https://nodejs.org/) (v16 or later recommended)
- [npm](https://www.npmjs.com/)
- A [MongoDB Atlas](https://www.mongodb.com/atlas) cluster (or local MongoDB instance)
- [Cloudinary](https://cloudinary.com/) account (for image uploads)
- SMTP credentials for transactional email (e.g. Gmail app password)

---

## Environment Variables

Create a `.env` file in the `Server/` directory:

```env
# Server
PORT=8080

# Database
MONGOURL=mongodb+srv://<user>:<password>@<cluster>.mongodb.net/<dbname>

# JWT
KEY=your_jwt_secret_key

# Email (Nodemailer)
MAILUSER=your_email@example.com
MAILPASS=your_email_app_password

# Cloudinary
CLOUDNAME=your_cloud_name
APIKEY=your_api_key
APISECRET=your_api_secret
```

> Never commit `.env` files or real credentials to version control.

The frontend currently calls the production API at `https://smart-cruiter-fyp-production.up.railway.app`. For local development, update the API base URL in the relevant `axios` calls under `Client/src/` to point to `http://localhost:8080`.

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/<your-org>/Smart-Cruiter-FYP.git
cd Smart-Cruiter-FYP
```

### 2. Install and run the backend

```bash
cd Server
npm install
npm run start
```

The API runs on `http://localhost:8080` by default.

### 3. Install and run the frontend

In a separate terminal:

```bash
cd Client
npm install
npm run dev
```

The client runs on the Vite dev server (typically `http://localhost:5173`).

### 4. Build for production

```bash
# Frontend
cd Client
npm run build

# Backend — use your preferred process manager or platform (e.g. Railway, Render)
cd Server
npm run start
```

---

## API Overview

| Prefix       | Purpose |
| ------------ | ------- |
| `/`          | Authentication, registration, password reset |
| `/profile`   | Organization profile setup |
| `/job`       | Job CRUD, applications, public job listings |
| `/details`   | Recruitment pipeline (status updates, emails, comments) |
| `/report`    | Dashboard statistics |
| `/settings`  | User and organization settings |

Protected routes require a valid JWT in the `Authorization` header.

---

## Contributing

Contributions are welcome. Please open an issue to discuss significant changes before submitting a pull request.

