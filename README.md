# HabitMentor

HabitMentor is a full-stack AI-powered habit tracking web app that helps users build better routines, track daily progress, monitor streaks, and get personalized habit coaching insights.

The app includes a responsive React dashboard, secure authentication, MongoDB-backed habit logs, visual analytics, and Google Gemini-powered AI features such as weekly reports, habit suggestions, recovery plans, and habit-analysis chat.

## Features

- User registration and login with JWT authentication
- Create, edit, archive, delete, and reorder habits
- Daily habit completion tracking with duplicate-log prevention
- Current streak and longest streak calculation
- Weekly progress grid and 90-day heatmap
- Statistics dashboard with charts for trends, categories, and habit performance
- AI weekly habit reports powered by Google Gemini
- Personalized AI habit suggestions
- Streak recovery coaching for broken habits
- Morning motivation and AI habit-analysis chat
- Responsive UI with dark/light theme support
- Confetti feedback when habits are completed

## Tech Stack

**Frontend**

- React.js
- Vite
- Tailwind CSS
- React Router
- Axios
- Recharts
- Lucide React
- Canvas Confetti

**Backend**

- Node.js
- Express.js
- MongoDB
- Mongoose
- JWT
- bcryptjs
- Google Gemini API

## Project Structure

```text
HabitMentor/
|-- backend/
|   |-- config/
|   |-- controllers/
|   |-- middleware/
|   |-- models/
|   |-- routes/
|   |-- scripts/
|   |-- utils/
|   |-- package.json
|   `-- server.js
|-- frontend/
|   `-- ai-habit-tracker/
|       |-- public/
|       |-- src/
|       |   |-- api/
|       |   |-- components/
|       |   |-- context/
|       |   |-- pages/
|       |   `-- utils/
|       |-- package.json
|       `-- vite.config.js
|-- .gitignore
`-- README.md
```

## Getting Started

### Prerequisites

Install these before running the project:

- Node.js
- npm
- MongoDB Atlas account or local MongoDB server
- Google Gemini API key, optional but required for real AI responses

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/HabitMentor.git
cd HabitMentor
```

### 2. Install Backend Dependencies

```bash
cd backend
npm install
```

### 3. Configure Backend Environment

Create a `.env` file inside the `backend` folder:

```env
PORT=8000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
JWT_EXPIRES_IN=30d
CLIENT_URL=http://localhost:5173
GEMINI_API_KEY=your_gemini_api_key
GEMINI_MODEL=gemini-2.5-flash
```

If `GEMINI_API_KEY` is not set, the backend still runs, but AI features return a fallback message.

### 4. Start the Backend

```bash
npm run dev
```

Backend runs at:

```text
http://localhost:8000
```

Health check:

```text
http://localhost:8000/api/health
```

### 5. Install Frontend Dependencies

Open a new terminal:

```bash
cd frontend/ai-habit-tracker
npm install
```

### 6. Configure Frontend Environment

Create a `.env` file inside `frontend/ai-habit-tracker`:

```env
VITE_API_URL=http://localhost:8000/api
```

### 7. Start the Frontend

```bash
npm run dev
```

Frontend runs at:

```text
http://localhost:5173
```

## Available Scripts

### Backend

```bash
npm run dev
```

Runs the backend with Nodemon.

```bash
npm start
```

Runs the backend with Node.

```bash
npm run seed
```

Runs the seed script.

### Frontend

```bash
npm run dev
```

Starts the Vite development server.

```bash
npm run build
```

Builds the frontend for production.

```bash
npm run lint
```

Runs ESLint.

```bash
npm run preview
```

Previews the production build locally.

## API Overview

### Auth Routes

```text
POST /api/auth/register
POST /api/auth/login
GET  /api/auth/me
PUT  /api/auth/profile
```

### Habit Routes

```text
GET    /api/habits
POST   /api/habits
PUT    /api/habits/reorder
PUT    /api/habits/:id
PUT    /api/habits/:id/archive
DELETE /api/habits/:id
```

### Log and Stats Routes

```text
POST   /api/logs
DELETE /api/logs
GET    /api/logs/today
GET    /api/logs/range
GET    /api/logs/heatmap
GET    /api/logs/stats
GET    /api/logs/stats/:habitId
```

## Key Implementation Details

- Passwords are hashed before saving users to MongoDB.
- JWT tokens protect habit, log, profile, and AI-related endpoints.
- Habit logs use a compound unique index to prevent duplicate completion entries for the same user, habit, and date.
- Habit and log queries are scoped by authenticated user ID for user-specific data isolation.
- The dashboard fetches habits, today's logs, weekly logs, and heatmap data in parallel for a faster user experience.
- AI responses are generated with Google Gemini and stored as insight records where applicable.

## Future Improvements

- Add automated tests for backend controllers and frontend components
- Add deployment configuration for Vercel or Render
- Add screenshot assets to the README
- Add email-based password reset
- Add social login support
- Add notification reminders for habits

## Author

Built by Maulik Pandor.
