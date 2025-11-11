💬 WhatsApp-Style Real-Time Chat Application

A full-stack real-time chat application built with React, Socket.io, Node.js, Express, and MongoDB. Features a beautiful WhatsApp-inspired UI with instant messaging, multiple rooms, user presence, and typing indicators.

https://img.shields.io/badge/React-19.1.1-blue https://img.shields.io/badge/Socket.io-4.8.1-green https://img.shields.io/badge/Node.js-20+-brightgreen https://img.shields.io/badge/MongoDB-8.19.3-green https://img.shields.io/badge/Deployed-Render%20%26%20Vercel-success

🚀 Live Demo

· Frontend: https://your-chat-app.vercel.app
· Backend: https://your-chat-app.onrender.com
· API Health: https://your-chat-app.onrender.com/api/health

✨ Features

💚 WhatsApp-Style UI

· Familiar WhatsApp green color scheme
· Message bubbles with proper styling
· Online/offline status indicators
· Typing indicators with animated dots
· User avatars with initials
· Responsive design for all devices
· Dark theme sidebar

💬 Core Chat Features

· ✅ Real-time messaging with Socket.io
· ✅ User authentication (simple username-based)
· ✅ Multiple chat rooms support
· ✅ Online/offline user status
· ✅ Typing indicators
· ✅ Message timestamps
· ✅ Message persistence with MongoDB
· ✅ User join/leave notifications

🛠 Technical Features

· ✅ RESTful API endpoints
· ✅ WebSocket connections for real-time updates
· ✅ MongoDB integration for data persistence
· ✅ CORS configuration for cross-origin requests
· ✅ Error handling and validation
· ✅ Production-ready deployment

🛠 Tech Stack

Frontend

· React 19.1.1 - UI framework
· Vite - Build tool and dev server
· Tailwind CSS - Utility-first CSS
· Socket.io Client - Real-time communication
· Axios - HTTP client

Backend

· Node.js - Runtime environment
· Express.js - Web framework
· Socket.io - Real-time engine
· MongoDB with Mongoose - Database & ODM
· CORS - Cross-origin resource sharing
· Dotenv - Environment variables

📦 Quick Start (Local Development)

Prerequisites

· Node.js (v18 or higher)
· MongoDB (local or Atlas)
· Git

1. Clone the Repository

bash
git clone https://github.com/your-username/chat-app.git
cd chat-app


2. Backend Setup

bash
# Navigate to server directory
cd server

# Install dependencies
npm install

# Create environment file
cp .env.example .env

# Start development server
npm run dev


3. Frontend Setup

bash
# Navigate to client directory (from root)
cd client

# Install dependencies
npm install

# Start development server
npm run dev


4. Access the Application

· Frontend: http://localhost:5173
· Backend API: http://localhost:5000
· API Health Check: http://localhost:5000/api/health

🗄 Database Setup

Option 1: Local MongoDB

bash
# Install MongoDB locally
# Start MongoDB service
mongod

# Or using Docker
docker run -d -p 27017:27017 --name mongodb mongo:latest


Option 2: MongoDB Atlas (Recommended for Production)

1. Go to MongoDB Atlas
2. Create free account and cluster
3. Get connection string
4. Update MONGODB_URI in server/.env

🌐 Deployment Guide

Backend Deployment to Render

1. Prepare Your Backend Code

server/.env

env
MONGODB_URI=your_mongodb_atlas_connection_string
NODE_ENV=production
PORT=5000


server/package.json (ensure these scripts exist)

json
{
  "scripts": {
    "dev": "nodemon src/server.js",
    "start": "node src/server.js"
  }
}


2. Deploy to Render

1. Push code to GitHub
2. Go to Render.com
   · Sign up with GitHub
   · Click "New +" → "Web Service"
   · Connect your GitHub repository
3. Configure Render deployment:
   · Name: chat-app-server
   · Environment: Node
   · Region: Choose closest to you
   · Branch: main
   · Root Directory: server
   · Build Command: npm install
   · Start Command: npm start
4. Add Environment Variables in Render:
   · MONGODB_URI - Your MongoDB Atlas connection string
   · NODE_ENV - production
5. Click "Create Web Service" - Wait for deployment

Frontend Deployment to Vercel

1. Prepare Your Frontend Code

client/.env.production

env
VITE_SOCKET_SERVER_URL=https://your-render-app.onrender.com


client/vite.config.js

javascript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import tailwindcss from '@tailwindcss/vite'

export default defineConfig({
  plugins: [react(), tailwindcss()],
  server: {
    port: 5173
  },
  build: {
    outDir: 'dist',
    sourcemap: false
  }
})


2. Deploy to Vercel

1. Go to Vercel.com
   · Sign up with GitHub
   · Click "New Project"
   · Import your GitHub repository
2. Configure Vercel:
   · Framework Preset: Vite
   · Root Directory: client
   · Build Command: npm run build
   · Output Directory: dist
   · Install Command: npm install
3. Add Environment Variable in Vercel:
   · Go to Project Settings → Environment Variables
   · Add: VITE_SOCKET_SERVER_URL = https://your-render-app.onrender.com
4. Click "Deploy" - Wait for deployment

📡 API Documentation

REST API Endpoints

Method Endpoint Description
GET /api/health Server health check
GET /api/rooms Get all chat rooms
GET /api/users/online Get online users
GET /api/messages/:room Get room messages
GET /api/stats Get application statistics

Socket Events

Client → Server Events

· user_join - User joins the chat
· send_message - Send a new message
· typing - Typing indicator
· join_room - Join a chat room
· private_message - Send private message
· message_read - Mark message as read

Server → Client Events

· message - New message received
· user_status - User online/offline status
· user_typing - Typing indicator
· online_users - List of online users
· message_history - Previous messages
· room_list - Available chat rooms

🏗 Project Structure


chat-app/
├── client/                 
│   ├── src/
│   │   ├── components/     
│   │   │   ├── Login.jsx   
│   │   │   ├── ChatRoom.jsx 
│   │   │   ├── MessageList.jsx 
│   │   │   ├── MessageInput.jsx 
│   │   │   └── OnlineUsers.jsx 
│   │   ├── App.jsx        
│   │   ├── main.jsx       
│   │   └── index.css       
│   ├── package.json
│   └── vite.config.js
├── server/                
│   ├── src/
│   │   └── server.js       
│   ├── package.json
│   └── .env
└── README.md


🔧 Configuration

Environment Variables

Server (.env)

env
MONGODB_URI=mongodb://localhost:27017/chat-app
PORT=5000
NODE_ENV=development


Client (for production)

env
VITE_SOCKET_SERVER_URL=https://your-render-app.onrender.com


🎯 Usage Guide

Getting Started

1. Open the application in your browser
2. Enter a username to join the chat
3. Start sending messages in the general room
4. See other users join and leave in real-time

Features Usage

· Create Rooms: Use the room panel to create new chat rooms
· Private Messages: Click on users in the online list to message them privately
· Typing Indicators: See when others are typing
· Message History: All messages are saved and persist between sessions

🚨 Troubleshooting

Common Deployment Issues

1. CORS Errors
   · Ensure frontend URL is in backend CORS allowed origins
   · Check environment variables are set correctly
2. Socket Connection Failed
   · Verify backend URL is correct in frontend
   · Check if WebSockets are enabled on hosting platform
3. MongoDB Connection Issues
   · Verify MongoDB Atlas connection string
   · Check IP whitelist in MongoDB Atlas
4. Build Failures
   · Ensure all dependencies are in package.json
   · Check Node.js version compatibility

Development Tips

· Use browser developer tools to monitor WebSocket connections
· Check server logs for connection events
· Use MongoDB Compass to inspect database

📊 Database Schema

Messages Collection

javascript
{
  _id: ObjectId,
  content: String,
  username: String,
  room: String,
  type: String, // 'public' or 'private'
  to: String, // for private messages
  read: Boolean,
  timestamp: Date
}


Users Collection

javascript
{
  _id: ObjectId,
  username: String,
  socketId: String,
  online: Boolean,
  lastSeen: Date,
  joinedAt: Date
}


Rooms Collection

javascript
{
  _id: ObjectId,
  name: String,
  description: String,
  createdBy: String,
  createdAt: Date
}


💰 Cost Analysis (Free Tier)

Render (Backend)

· 750 free hours/month - Enough for 24/7 operation
· Automatic sleep after inactivity
· Wakes up on first request (small delay)

Vercel (Frontend)

· Unlimited personal projects
· 100GB bandwidth/month
· Always free for personal use

MongoDB Atlas (Database)

· 512MB storage
· Shared RAM
· Always free cluster

Total Monthly Cost: $0

🔒 Security Features

· Input validation and sanitization
· CORS configuration for controlled access
· Environment variable protection
· MongoDB injection prevention with Mongoose
· Rate limiting considerations

🚀 Performance Optimizations

· Message pagination for large chat histories
· Efficient reconnection handling
· Optimized database queries
· Production build optimizations
· CDN distribution for frontend assets

🤝 Contributing

1. Fork the repository
2. Create a feature branch (git checkout -b feature/amazing-feature)
3. Commit your changes (git commit -m 'Add amazing feature')
4. Push to the branch (git push origin feature/amazing-feature)
5. Open a Pull Request

📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

🙏 Acknowledgments

· WhatsApp for UI/UX inspiration
· Socket.io for real-time communication
· Vite for fast development experience
· Tailwind CSS for utility-first styling
· MongoDB for data persistence
· Render & Vercel for free hosting

📞 Support

If you encounter any issues:

1. Check the troubleshooting section
2. Search existing GitHub Issues
3. Create a new issue with detailed information

🔄 Update Instructions

To update your deployed application:

1. Push changes to GitHub
2. Render and Vercel will automatically redeploy
3. Monitor deployment logs for any issues

---

Built with ❤ using modern web technologies.

Happy Chatting! 💬✨