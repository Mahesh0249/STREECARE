# StreeCare Setup Guide & Issue Resolution

## 🚨 Critical Issues Fixed

### 1. **Port Configuration**
- **Fixed**: Server now uses `process.env.PORT` instead of hardcoded 3001
- **Result**: Consistent with .env configuration (PORT=5000)

### 2. **Database Connection**
- **Fixed**: Added charset and SSL configuration for MySQL
- **Result**: Better compatibility with MySQL 8.0+ and special characters in passwords

### 3. **Duplicate Routes**
- **Fixed**: Renamed conflicting appointment route from `/` to `/test`
- **Result**: All API endpoints now work correctly

### 4. **Enhanced AI Chatbot**
- **Upgraded**: Replaced token-based responses with Google Gemini AI
- **Features**: Personalized responses, multi-language support, health insights

## 🛠️ Setup Instructions

### Prerequisites
1. **Node.js** (v16+)
2. **MySQL** (v8.0+)
3. **Google Gemini API Key**

### Database Setup
```bash
# Create database
mysql -u root -p
CREATE DATABASE streecare;
USE streecare;

# Import schema and seed data
mysql -u root -p streecare < database/schema.sql
mysql -u root -p streecare < database/seed.sql
```

### Backend Setup
```bash
cd backend

# Install dependencies (including new Gemini AI package)
npm install

# Update .env file with your Gemini API key
GEMINI_API_KEY=your_actual_gemini_api_key_here

# Start server
npm start
```

### Frontend Setup
```bash
cd frontend
npm install
npm start
```

## 🔑 Get Gemini API Key

1. Go to [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Create a new API key
3. Copy the key to your `.env` file:
   ```
   GEMINI_API_KEY=your_actual_api_key_here
   ```

## 🤖 New Gemini AI Features

### Enhanced Chatbot Capabilities
- **Personalized Responses**: Uses user's health data for context
- **Multi-language Support**: English, Telugu, Hindi
- **Health Insights**: AI-generated personalized recommendations
- **Context Awareness**: Considers menstrual logs, appointments, age

### New API Endpoints
- `GET /api/chatbot/insights` - Get personalized health insights
- `POST /api/chatbot/message` - Enhanced AI conversations
- `GET /api/chatbot/history` - Chat history with AI responses

### Sample Conversation Flow
```javascript
// User sends message
POST /api/chatbot/message
{
  "message": "I'm having irregular periods",
  "language": "en"
}

// AI responds with personalized advice
{
  "response": "I understand your concern about irregular periods. Based on your profile, this can be normal, but let me provide some guidance..."
}
```

## 🔧 Potential Runtime Issues & Solutions

### Issue 1: MySQL Connection Fails
**Symptoms**: `Database connection failed` error
**Solutions**:
- Verify MySQL service is running
- Check password in `.env` (escape special characters if needed)
- Ensure database `streecare` exists

### Issue 2: Gemini API Errors
**Symptoms**: Chatbot returns fallback responses
**Solutions**:
- Verify `GEMINI_API_KEY` in `.env`
- Check API key permissions in Google AI Studio
- Monitor API usage limits

### Issue 3: Port Already in Use
**Symptoms**: `EADDRINUSE` error
**Solutions**:
```bash
# Kill process on port 5000
npx kill-port 5000

# Or use different port
PORT=3001 npm start
```

### Issue 4: Frontend Proxy Issues
**Symptoms**: API calls fail from frontend
**Solutions**:
- Ensure backend runs on port 5000
- Check `proxy` setting in `frontend/package.json`
- Verify CORS configuration

## 🧪 Testing the Setup

### 1. Health Check
```bash
curl http://localhost:5000/health
# Should return: {"status":"OK","message":"Server is working!"}
```

### 2. Database Test
```bash
curl http://localhost:5000/db-test
# Should return: {"status":"OK","message":"Database connected successfully!"}
```

### 3. Test Gemini Chatbot
```bash
# First login to get token
curl -X POST http://localhost:5000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"patient@example.com","password":"password123"}'

# Then test chatbot (replace YOUR_TOKEN)
curl -X POST http://localhost:5000/api/chatbot/message \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -d '{"message":"Hello Saathi","language":"en"}'
```

## 📱 Default Login Credentials

**Patient Account**:
- Email: `patient@example.com`
- Password: `password123`

**Doctor Account**:
- Email: `doctor@example.com`
- Password: `password123`

## 🚀 Running the Complete Application

```bash
# Terminal 1: Start Backend
cd backend
npm start

# Terminal 2: Start Frontend
cd frontend
npm start

# Access application at: http://localhost:3000
```

## 🔍 Troubleshooting Common Issues

### MySQL Authentication Error
```bash
# If you get authentication plugin error
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your_password';
FLUSH PRIVILEGES;
```

### Node.js Version Issues
```bash
# Check Node version
node --version

# Should be v16+ for compatibility
```

### Package Installation Issues
```bash
# Clear npm cache and reinstall
npm cache clean --force
rm -rf node_modules package-lock.json
npm install
```

## 📊 Application Architecture

```
StreeCare/
├── backend/                 # Node.js + Express API
│   ├── routes/
│   │   ├── chatbot.js          # Enhanced Gemini AI chatbot
│   │   ├── appointments.js     # Fixed duplicate routes
│   │   └── ...
│   ├── config/
│   │   └── database.js      # Enhanced MySQL config
│   └── server.js           # Fixed port configuration
├── frontend/               # React + TailwindCSS
├── database/              # MySQL schema & seed data
└── SETUP_GUIDE.md        # This file
```

The application is now ready to run with enhanced AI capabilities and all critical issues resolved!
