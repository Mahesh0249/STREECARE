# StreeCare Project Structure

## Overview
StreeCare is a comprehensive full-stack women's health platform with role-based access for patients and doctors.

## Project Structure

```
streecare-backend/
├── frontend/                    # React frontend application
│   ├── public/                 # Static files
│   │   └── index.html         # Main HTML file
│   ├── src/                    # Source code
│   │   ├── components/         # React components
│   │   │   ├── auth/          # Authentication components
│   │   │   ├── common/        # Shared components
│   │   │   ├── dashboard/     # Dashboard components
│   │   │   └── chatbot/       # Chatbot components
│   │   ├── contexts/          # React contexts
│   │   │   ├── AuthContext.js # Authentication state
│   │   │   ├── LanguageContext.js # Internationalization
│   │   │   └── ChatContext.js # Chat state
│   │   ├── locales/           # Translation files
│   │   │   ├── en.json        # English translations
│   │   │   ├── te.json        # Telugu translations
│   │   │   └── hi.json        # Hindi translations
│   │   ├── App.js             # Main app component
│   │   ├── index.js           # App entry point
│   │   └── index.css          # Global styles with TailwindCSS
│   ├── package.json           # Frontend dependencies
│   ├── tailwind.config.js     # TailwindCSS configuration
│   └── postcss.config.js      # PostCSS configuration
├── backend/                    # Node.js backend server
│   ├── config/                # Configuration files
│   │   └── database.js        # MySQL database configuration
│   ├── middleware/            # Express middleware
│   │   └── auth.js            # JWT authentication middleware
│   ├── routes/                # API route handlers
│   │   ├── auth.js            # Authentication routes
│   │   ├── appointments.js    # Appointment management
│   │   ├── forum.js           # Community forum
│   │   ├── menstrual.js       # Menstrual tracking
│   │   ├── music.js           # Music recommendations
│   │   └── chatbot.js         # AI chatbot
│   ├── package.json           # Backend dependencies
│   ├── server.js              # Main server file
│   └── env.example            # Environment variables template
├── database/                   # Database files
│   ├── schema.sql             # MySQL database schema
│   └── seed.sql               # Sample data
└── README.md                   # Project documentation
```

## Key Features

### Frontend
- **React 18** with modern hooks and functional components
- **TailwindCSS** for responsive, mobile-first design
- **i18next** for multi-language support (English, Telugu, Hindi)
- **React Router** for navigation
- **Context API** for state management
- **Axios** for API communication

### Backend
- **Node.js** with Express framework
- **MySQL** database with connection pooling
- **JWT** authentication with bcrypt password hashing
- **Express Validator** for input validation
- **CORS** enabled for frontend integration
- **Helmet** for security headers

### Database
- **Users** table with role-based access
- **Appointments** for patient-doctor scheduling
- **Forum** system with posts, comments, and likes
- **Menstrual logs** for health tracking
- **Songs** for mood-based music recommendations
- **Chat messages** for AI chatbot

## Setup Instructions

1. **Database Setup**
   - Create MySQL database: `CREATE DATABASE streecare;`
   - Import schema: `mysql -u username -p streecare < database/schema.sql`
   - Import seed data: `mysql -u username -p streecare < database/seed.sql`

2. **Backend Setup**
   - Copy `backend/env.example` to `backend/.env`
   - Update database credentials and JWT secret
   - Install dependencies: `cd backend && npm install`
   - Start server: `npm start`

3. **Frontend Setup**
   - Install dependencies: `cd frontend && npm install`
   - Start development server: `npm start`

## Default Users
- **Patient**: patient@example.com / password123
- **Doctor**: doctor@example.com / password123

## API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `GET /api/auth/profile` - Get user profile

### Appointments
- `GET /api/appointments` - Get appointments
- `POST /api/appointments` - Book appointment
- `PUT /api/appointments/:id/status` - Update status

### Forum
- `GET /api/forum/posts` - Get forum posts
- `POST /api/forum/posts` - Create post
- `POST /api/forum/posts/:id/comments` - Add comment

### Menstrual Tracker
- `GET /api/menstrual/logs` - Get logs
- `POST /api/menstrual/logs` - Add log
- `GET /api/menstrual/insights` - Get insights

### Music
- `GET /api/music` - Get songs by mood
- `GET /api/music/moods` - Get available moods

### Chatbot
- `POST /api/chatbot/message` - Send message
- `GET /api/chatbot/history` - Get chat history

## Development Notes

- Frontend runs on port 3000
- Backend runs on port 5000
- Database should be MySQL 8.0+
- Node.js version 16+ required
- All API calls require JWT token in Authorization header
- Multi-language support with automatic language detection
- Mobile-first responsive design
- Real-time chat functionality with AI responses
