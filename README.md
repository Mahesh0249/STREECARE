# StreeCare - Women's Health Platform

A comprehensive full-stack web application for women's health management with role-based access for patients and doctors.

## Features

- **Multi-language Support**: English, Telugu, Hindi
- **Role-based Access**: Patient and Doctor dashboards
- **AI Chatbot**: Saathi - Your health companion
- **Appointment Booking**: Patient-Doctor scheduling system
- **Menstrual Health Tracker**: Period tracking and predictions
- **Community Forum**: Anonymous health discussions
- **Emo Track**: Mood-based music recommendations
- **JWT Authentication**: Secure login system

## Tech Stack

- **Frontend**: React + TailwindCSS
- **Backend**: Node.js + Express
- **Database**: MySQL
- **Authentication**: JWT + bcrypt
- **Internationalization**: i18next

## Project Structure

```
streecare-backend/
├── frontend/          # React frontend application
├── backend/           # Node.js backend server
├── database/          # MySQL schema and seed data
└── README.md          # This file
```

## Prerequisites

- Node.js (v16 or higher)
- MySQL (v8.0 or higher)
- npm or yarn

## Setup Instructions

### 1. Database Setup

1. Create a MySQL database:
```sql
CREATE DATABASE streecare;
```

2. Import the schema:
```bash
mysql -u your_username -p streecare < database/schema.sql
```

3. Import seed data:
```bash
mysql -u your_username -p streecare < database/seed.sql
```

### 2. Backend Setup

1. Navigate to backend directory:
```bash
cd backend
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file:
```env
DB_HOST=localhost
DB_USER=your_username
DB_PASSWORD=your_password
DB_NAME=streecare
JWT_SECRET=your_jwt_secret_key
PORT=5000
```

4. Start the server:
```bash
npm start
```

### 3. Frontend Setup

1. Navigate to frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm start
```

## API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `GET /api/auth/profile` - Get user profile

### Appointments
- `GET /api/appointments` - Get appointments
- `POST /api/appointments` - Create appointment
- `PUT /api/appointments/:id` - Update appointment status

### Forum
- `GET /api/forum/posts` - Get forum posts
- `POST /api/forum/posts` - Create post
- `POST /api/forum/posts/:id/comments` - Add comment

### Menstrual Tracker
- `GET /api/menstrual/logs` - Get menstrual logs
- `POST /api/menstrual/logs` - Add menstrual log

### Music Recommendations
- `GET /api/music?mood=:mood` - Get mood-based music

### Chatbot
- `POST /api/chatbot/message` - Send message to AI chatbot

## Environment Variables

Create a `.env` file in the backend directory with the following variables:

```env
DB_HOST=localhost
DB_USER=your_mysql_username
DB_PASSWORD=your_mysql_password
DB_NAME=streecare
JWT_SECRET=your_secret_key_here
PORT=5000
NODE_ENV=development
```

## Running the Application

1. Start MySQL service
2. Start backend: `cd backend && npm start`
3. Start frontend: `cd frontend && npm start`
4. Open http://localhost:3000 in your browser

## Default Users

After running seed data, you can login with:

**Patient:**
- Email: patient@example.com
- Password: password123

**Doctor:**
- Email: doctor@example.com
- Password: password123

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is licensed under the MIT License.
