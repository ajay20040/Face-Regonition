# Face Recognition Platform with Real-Time AI Q&A

A browser-based platform that enables users to register their faces and recognize them in real-time using laptop camera streams, enhanced with an AI-powered chat interface using RAG (Retrieval-Augmented Generation).

## 🎯 Project Overview

This application combines facial recognition technology with conversational AI to create an interactive platform where users can:
- Register faces through webcam capture
- Perform real-time face recognition with live camera feed
- Query registration data using natural language through an AI chat interface

## 🚀 Demo

📹 **[Watch Live Demo Video](YOUR_LOOM_VIDEO_LINK_HERE)**

*Replace with your actual Loom video link demonstrating the working application*

## 🏗️ Architecture

![Architecture Diagram](./docs/architecture-diagram.png)

*Add your architecture diagram showing the flow between React → Node.js → Python components*

### System Components
- **Frontend**: React.js with camera integration and WebSocket communication
- **Backend API**: Node.js with Express and WebSocket server
- **Face Recognition**: Python service using OpenCV/face_recognition library
- **RAG Engine**: Python service with LangChain + FAISS + OpenAI GPT
- **Database**: [Your chosen database] for storing face encodings and metadata

## 🛠️ Tech Stack

| Component | Technology |
|-----------|------------|
| Frontend | React.js |
| Backend API | Node.js, Express.js |
| WebSocket Server | Socket.io |
| Face Recognition | Python, OpenCV, face_recognition |
| RAG Implementation | Python, LangChain, FAISS |
| LLM | OpenAI ChatGPT API |
| Database | [Your Database Choice] |
| Styling | [CSS Framework/Library] |

## ✨ Features

### 📝 Registration Tab
- **Live Camera Feed**: Access webcam for real-time video streaming
- **Face Detection**: Automatic face detection with bounding box overlay
- **Face Capture**: Capture and preview detected faces
- **User Registration**: Assign names to captured faces
- **Registration History**: View all registered users with timestamps

### 👁️ Live Recognition Tab
- **Real-time Recognition**: Continuous face recognition from camera stream
- **Multi-face Detection**: Simultaneous recognition of multiple faces
- **Visual Feedback**: Bounding boxes and name labels for recognized faces
- **Performance Optimization**: Processes 1-2 frames per second for smooth performance

### 💬 AI Chat Interface
- **Natural Language Queries**: Ask questions about registered users
- **Real-time Responses**: WebSocket-powered instant messaging
- **Smart Context**: RAG-powered responses using registration data
- **Query Examples**:
  - "Who was the last person registered?"
  - "At what time was John registered?"
  - "How many people are currently registered?"

## 🔧 Installation & Setup

### Prerequisites
- **Node.js** (v16 or higher)
- **Python** (v3.8 or higher)
- **Webcam** (built-in or external)
- **OpenAI API Key**

### 1. Clone Repository
```bash
git clone https://github.com/yourusername/face-recognition-platform.git
cd face-recognition-platform
```

### 2. Frontend Setup
```bash
cd frontend
npm install
npm start
```
The frontend will run on `http://localhost:3000`

### 3. Backend Setup
```bash
cd backend
npm install
npm run dev
```
The backend API will run on `http://localhost:5000`

### 4. Python Services Setup

#### Face Recognition Service
```bash
cd python-services/face-recognition
pip install -r requirements.txt
python app.py
```
Face recognition service runs on `http://localhost:8000`

#### RAG Service
```bash
cd python-services/rag-engine
pip install -r requirements.txt
python rag_app.py
```
RAG service runs on `http://localhost:8001`

### 5. Environment Variables

Create `.env` files in respective directories:

**Backend (.env)**
```env
PORT=5000
DATABASE_URL=your_database_connection_string
PYTHON_FACE_SERVICE_URL=http://localhost:8000
PYTHON_RAG_SERVICE_URL=http://localhost:8001
```

**Python RAG Service (.env)**
```env
OPENAI_API_KEY=your_openai_api_key_here
DATABASE_URL=your_database_connection_string
```

### 6. Database Setup
```bash
# Run database migrations/setup
cd backend
npm run db:setup
```

## 🚦 Usage

1. **Start All Services**:
   ```bash
   # Terminal 1 - Frontend
   cd frontend && npm start
   
   # Terminal 2 - Backend
   cd backend && npm run dev
   
   # Terminal 3 - Face Recognition
   cd python-services/face-recognition && python app.py
   
   # Terminal 4 - RAG Engine
   cd python-services/rag-engine && python rag_app.py
   ```

2. **Access Application**: Navigate to `http://localhost:3000`

3. **Register Faces**:
   - Go to "Registration" tab
   - Allow camera permissions
   - Position face in camera view
   - Click "Capture" when face is detected
   - Enter name and click "Register"

4. **Live Recognition**:
   - Go to "Live Recognition" tab
   - Camera will automatically start
   - Registered faces will be recognized and labeled

5. **Ask Questions**:
   - Open chat widget
   - Type natural language questions about registered users
   - Get instant AI-powered responses

## 📁 Project Structure

```
face-recognition-platform/
├── frontend/                    # React.js application
│   ├── src/
│   │   ├── components/         # Reusable components
│   │   ├── pages/             # Tab components
│   │   ├── hooks/             # Custom hooks
│   │   ├── services/          # API calls and WebSocket
│   │   └── utils/             # Utility functions
│   ├── public/
│   └── package.json
├── backend/                     # Node.js API server
│   ├── src/
│   │   ├── routes/            # API routes
│   │   ├── controllers/       # Route controllers
│   │   ├── middleware/        # Express middleware
│   │   ├── models/            # Database models
│   │   └── websocket/         # WebSocket handlers
│   └── package.json
├── python-services/            # Python microservices
│   ├── face-recognition/      # Face detection & recognition
│   │   ├── app.py
│   │   ├── face_utils.py
│   │   └── requirements.txt
│   └── rag-engine/            # RAG implementation
│       ├── rag_app.py
│       ├── vector_store.py
│       ├── llm_service.py
│       └── requirements.txt
├── docs/                       # Documentation
│   ├── architecture-diagram.png
│   └── Frontend_BRD.md
├── logs/                      # Application logs
└── README.md
```

## 🐛 Troubleshooting

### Common Issues

**Camera Not Working**
- Ensure camera permissions are granted
- Check if another application is using the camera
- Try refreshing the browser

**WebSocket Connection Failed**
- Verify all services are running
- Check firewall settings
- Ensure ports are not blocked

**Face Recognition Not Working**
- Ensure Python service is running on port 8000
- Check camera lighting conditions
- Verify face is clearly visible and well-lit

**Chat Responses Slow/Not Working**
- Verify OpenAI API key is set correctly
- Check internet connection
- Ensure RAG service is running on port 8001

## 📊 Logging

The application implements comprehensive logging for event tracking:

- **Frontend**: Browser console logs and user interactions
- **Backend**: API requests, WebSocket events, database operations
- **Python Services**: Face recognition events, RAG processing, errors

Log files are stored in the `logs/` directory with rotation based on date.

## 🔒 Security Considerations

- Face images are processed in real-time and not stored locally in browser
- Facial encodings are stored securely in the database
- WebSocket communications use secure protocols
- API endpoints implement proper validation and error handling

## 🧪 Testing

```bash
# Frontend tests
cd frontend && npm test

# Backend tests
cd backend && npm test

# Python service tests
cd python-services/face-recognition && python -m pytest
cd python-services/rag-engine && python -m pytest
```

## 📈 Performance Optimization

- **Face Recognition**: Processes 1-2 frames per second to balance accuracy and performance
- **Frontend**: Optimized React components with proper memoization
- **WebSocket**: Efficient real-time communication with connection pooling
- **Database**: Indexed queries for fast face encoding retrieval

## 🚀 Deployment

### Local Development
Follow the installation steps above for local development setup.

### Production Deployment
1. **Frontend**: Build and deploy to static hosting (Netlify, Vercel)
2. **Backend**: Deploy to cloud service (Heroku, AWS, DigitalOcean)
3. **Python Services**: Containerize and deploy using Docker
4. **Database**: Use cloud database service (MongoDB Atlas, PostgreSQL on AWS)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 Assumptions Made

- Users have modern browsers with WebRTC support
- Webcam access is available and permissions are granted
- Stable internet connection for real-time features
- OpenAI API has sufficient quota for chat functionality
- Users operate in well-lit environments for optimal face recognition

## 🏆 Hackathon Notes

This project was developed for the Katomaran AI Hackathon, focusing on:
- **AI Integration**: Advanced face recognition and RAG-powered chat
- **Full-Stack Development**: Complete end-to-end implementation
- **Real-time Processing**: WebSocket-based live interactions
- **User Experience**: Intuitive and visually appealing interface

### AI Tools Used
- **ChatGPT**: For code generation, debugging, and documentation
- **GitHub Copilot**: For auto-completion and code suggestions
- **Cursor**: For AI-assisted development workflow

*Prompting strategies and interactions with AI tools are documented and available for review during the interview process.*


## Acknowledgments

- OpenAI for ChatGPT API
- Face Recognition library contributors
- LangChain and FAISS communities
- React.js and Node.js ecosystems

---

**This project is a part of a hackathon run by https://katomaran.com**

---
