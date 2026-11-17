# 🌦️ ForecastGPT — AI-Powered Multilingual Weather Companion

**ForecastGPT** is a voice-first, multilingual weather companion designed to make weather information accessible through natural conversations. Users can ask weather-related questions using text or voice and receive contextual responses in their preferred language.

The project combines real-time weather data, Generative AI, multilingual voice processing, and a conversational interface.

> **Project status:** MVP development and integration. Some services require API credentials and additional configuration before all features can be used.

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Key Features](#-key-features)
- [Technology Stack](#-technology-stack)
- [System Architecture](#-system-architecture)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Installation and Setup](#-installation-and-setup)
- [Firebase Configuration](#-firebase-configuration)
- [Backend Setup](#-backend-setup)
- [Frontend Setup](#-frontend-setup)
- [Running the Project](#-running-the-project)
- [API Endpoints](#-api-endpoints)
- [Environment Variables](#-environment-variables)
- [Troubleshooting](#-troubleshooting)
- [Security](#-security)
- [Future Enhancements](#-future-enhancements)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🌍 Project Overview

Traditional weather applications mainly provide numerical forecasts and static weather information. ForecastGPT aims to make weather information more interactive through conversational AI.

Users can:

1. Select a city or location.
2. Ask weather-related questions.
3. Receive weather information based on live weather-provider data.
4. Interact through text or voice.
5. Receive responses in supported languages.
6. Access weather-safety information through a retrieval-based knowledge system.

The system is designed with a modular architecture so that additional weather providers, AI models, and mobile clients can be integrated later.

---

## ✨ Key Features

| Feature | Description |
|---|---|
| Conversational AI | Natural-language weather assistance |
| Real-time Weather | Weather information through Open-Meteo |
| Weather Forecast | Current conditions and seven-day forecast |
| Multilingual Support | English, Hindi, Telugu, Tamil, Malayalam, Kannada, Marathi and Bengali |
| User Authentication | Firebase email/password authentication |
| Phone Authentication | Firebase phone OTP integration |
| Speech-to-Text | Sarvam AI integration |
| Text-to-Speech | Sarvam AI voice generation |
| RAG Knowledge Base | Retrieval-based weather safety information |
| Chat History | SQLite-based conversation storage |
| Responsive Interface | React-based web interface |
| API Backend | FastAPI REST API |

*Feature availability depends on configuration and valid API credentials.*

---

## 🛠️ Technology Stack

### Frontend
- React
- TypeScript
- Vite
- CSS
- Firebase Authentication
- Lucide React

### Backend
- Python
- FastAPI
- Uvicorn
- SQLite
- Pydantic

### AI and Voice
- Google Gemini API
- Sarvam AI
- Scikit-learn
- TF-IDF Retrieval

### Weather Data
- Open-Meteo Weather API
- Open-Meteo Geocoding API

### Authentication and Security
- Firebase Authentication
- Firebase Admin SDK
- Firebase ID Token Verification
- Environment Variables

### Development Tools
- Visual Studio Code
- Git
- GitHub
- Node.js
- Python
- Windows CMD / PowerShell

---

## 🏗️ System Architecture

```text
                   USER
                    |
                    v
          React + TypeScript UI
                    |
          +---------+---------+
          |                   |
          v                   v
   Firebase Auth         Voice Interface
          |                   |
          |              Sarvam AI
          |              STT / TTS
          |                   |
          +---------+---------+
                    |
                    v
              FastAPI Backend
                    |
       +------------+-------------+
       |            |             |
       v            v             v
  Weather API    Gemini AI     RAG Engine
  Open-Meteo     Responses     TF-IDF Search
       |            |             |
       +------------+-------------+
                    |
                    v
              SQLite Database
                    |
                    v
             Response to User
```

### Request Flow

1. The user selects a location and enters a weather question.
2. Firebase authenticates the user.
3. The frontend sends the request and authentication token to FastAPI.
4. The backend retrieves weather information.
5. The AI component generates a response grounded in the available weather data.
6. The RAG component retrieves relevant weather-safety knowledge when applicable.
7. The response is returned to the frontend.
8. Voice output can be generated through the configured speech service.

---

## 📁 Project Structure

```text
ForecastGPT/
│
├── frontend/
│   ├── src/
│   │   ├── App.tsx
│   │   ├── firebase.ts
│   │   ├── main.tsx
│   │   ├── style.css
│   │   └── vite-env.d.ts
│   │
│   ├── public/
│   ├── index.html
│   ├── package.json
│   ├── package-lock.json
│   ├── tsconfig.json
│   ├── vite.config.ts
│   └── .env.example
│
├── backend/
│   ├── app/
│   │   ├── __init__.py
│   │   ├── main.py
│   │   ├── auth.py
│   │   ├── config.py
│   │   ├── database.py
│   │   ├── weather.py
│   │   ├── ai.py
│   │   ├── rag.py
│   │   └── voice.py
│   │
│   ├── knowledge/
│   │   └── weather_safety.md
│   │
│   ├── requirements.txt
│   └── .env.example
│
├── .gitignore
└── README.md
```

---

## 💻 Prerequisites

Install the following before running the project.

| Software | Recommended version |
|---|---|
| Python | 3.11 |
| Node.js | 22 LTS or a compatible supported release |
| npm | Installed with Node.js |
| Git | Latest stable |
| VS Code | Latest stable |

Check your installed versions:

```cmd
python --version
node --version
npm --version
git --version
```

If Python 3.11 is installed, verify it using:

```cmd
py -3.11 --version
```

---

## 🚀 Installation and Setup

### Step 1: Clone the Repository

```cmd
git clone https://github.com/YOUR_USERNAME/ForecastGPT.git
```

Move into the project:

```cmd
cd ForecastGPT
```

Open the project in VS Code:

```cmd
code .
```

If you already downloaded the project ZIP, extract it and open its root folder in VS Code instead.

### Step 2: Create a Python Virtual Environment

From the project root:

```cmd
cd backend
```

Create the virtual environment:

```cmd
py -3.11 -m venv .venv
```

Activate it:

```cmd
.venv\Scripts\activate.bat
```

Upgrade pip:

```cmd
python -m pip install --upgrade pip
```

Install backend dependencies:

```cmd
pip install -r requirements.txt
```

Return to the root directory:

```cmd
cd ..
```

---

## 🔥 Firebase Configuration

ForecastGPT uses Firebase Authentication for user registration and login.

### Step 1: Create a Firebase Project

Open:

https://console.firebase.google.com/

Create a project or open your existing Firebase project.

### Step 2: Register a Web Application

1. Open Project Settings.
2. Scroll to Your Apps.
3. Select the Web icon (`</>`).
4. Register your application.
5. Open the Firebase SDK configuration.

### Step 3: Configure Authentication

Navigate to:

Firebase Console → Authentication → Sign-in method

Enable:

- Email/Password
- Phone (for OTP authentication)

Save the configuration.

### Step 4: Configure Authorized Domains

Navigate to Authentication → Settings → Authorized domains.

Add your local development domain if it is not already present:

```text
localhost
127.0.0.1
```

### Step 5: Configure the Frontend Environment

Create a file named `.env` inside the `frontend` directory.

```text
frontend/.env
```

Add your Firebase configuration:

```env
VITE_API_URL=http://127.0.0.1:8000

VITE_FIREBASE_API_KEY=YOUR_FIREBASE_API_KEY
VITE_FIREBASE_AUTH_DOMAIN=YOUR_FIREBASE_AUTH_DOMAIN
VITE_FIREBASE_PROJECT_ID=YOUR_FIREBASE_PROJECT_ID
VITE_FIREBASE_APP_ID=YOUR_FIREBASE_APP_ID
VITE_FIREBASE_MESSAGING_SENDER_ID=YOUR_FIREBASE_MESSAGING_SENDER_ID
```

Replace the placeholders with the values from Firebase Project Settings.

**Important:** Never commit your `.env` file to GitHub.

---

## ⚙️ Backend Configuration

### Step 1: Create Backend Environment File

Navigate to:

```cmd
cd backend
```

Copy the example configuration:

```cmd
copy .env.example .env
```

Open `backend/.env` and configure the values required by your backend.

Example configuration:

```env
GEMINI_API_KEY=YOUR_GEMINI_API_KEY
SARVAM_API_KEY=YOUR_SARVAM_API_KEY

FIREBASE_SERVICE_ACCOUNT=firebase-service-account.json
```

Keep any other variables already present in your `.env.example` file.

### Step 2: Configure Firebase Admin SDK

For server-side authentication verification:

1. Open Firebase Console.
2. Go to Project Settings.
3. Open Service Accounts.
4. Generate a private key.
5. Download the JSON file.
6. Place it in the backend directory.

Expected location:

```text
backend/firebase-service-account.json
```

Do not upload this file to GitHub.

### Step 3: Start the Backend

From the `backend` directory, activate the environment if necessary:

```cmd
.venv\Scripts\activate.bat
```

Start FastAPI:

```cmd
uvicorn app.main:app --reload --host 127.0.0.1 --port 8000
```

Backend address:

```text
http://127.0.0.1:8000
```

Interactive API documentation:

```text
http://127.0.0.1:8000/docs
```

Alternative API documentation:

```text
http://127.0.0.1:8000/redoc
```

---

## 🎨 Frontend Configuration

Open a **second VS Code terminal**.

Navigate to the frontend:

```cmd
cd /d C:\ForecastGPT\Project\ForecastGPT\frontend
```

Install frontend dependencies:

```cmd
npm install
```

Start the development server:

```cmd
npm run dev -- --host 127.0.0.1 --port 5173 --strictPort
```

Open:

```text
http://127.0.0.1:5173/
```

Keep the frontend and backend terminals running while using the application.

---

## ▶️ Running the Project

### Terminal 1 — Backend

```cmd
cd /d C:\ForecastGPT\Project\ForecastGPT\backend

.venv\Scripts\activate.bat

uvicorn app.main:app --reload --host 127.0.0.1 --port 8000
```

### Terminal 2 — Frontend

```cmd
cd /d C:\ForecastGPT\Project\ForecastGPT\frontend

npm run dev -- --host 127.0.0.1 --port 5173 --strictPort
```

### Application URLs

| Component | URL |
|---|---|
| ForecastGPT Web App | http://127.0.0.1:5173 |
| FastAPI Backend | http://127.0.0.1:8000 |
| Swagger API Docs | http://127.0.0.1:8000/docs |
| ReDoc | http://127.0.0.1:8000/redoc |

---

## 🔌 API Endpoints

The backend exposes API routes for weather conversations and voice interactions.

| Endpoint | Method | Purpose |
|---|---|---|
| `/docs` | GET | Interactive API documentation |
| `/redoc` | GET | Alternative API documentation |
| `/api/chat` | POST | Conversational weather requests |
| `/api/voice/chat` | POST | Voice-based chat requests |

Authentication-protected endpoints require a valid Firebase ID token.

For exact request parameters, response formats, and authentication requirements, inspect the running Swagger documentation at:

http://127.0.0.1:8000/docs

---

## 🔐 Environment Variables

### Frontend

| Variable | Purpose |
|---|---|
| `VITE_API_URL` | FastAPI backend URL |
| `VITE_FIREBASE_API_KEY` | Firebase Web API key |
| `VITE_FIREBASE_AUTH_DOMAIN` | Firebase authentication domain |
| `VITE_FIREBASE_PROJECT_ID` | Firebase project ID |
| `VITE_FIREBASE_APP_ID` | Firebase application ID |
| `VITE_FIREBASE_MESSAGING_SENDER_ID` | Firebase messaging sender ID |

### Backend

| Variable | Purpose |
|---|---|
| `GEMINI_API_KEY` | Gemini AI integration |
| `SARVAM_API_KEY` | Sarvam speech services |
| `FIREBASE_SERVICE_ACCOUNT` | Firebase Admin service account file |

Refer to the `.env.example` files for the complete configuration expected by each component.

---

## 🧰 Troubleshooting

### 1. Port 5173 is already in use

Check which process is using the port:

```cmd
netstat -ano | findstr :5173
```

Stop the old process using its PID:

```cmd
taskkill /PID YOUR_PID /F
```

Restart Vite:

```cmd
npm run dev -- --host 127.0.0.1 --port 5173 --strictPort
```

### 2. Firebase: auth/invalid-api-key

Check:

- The frontend `.env` file exists.
- It is located inside `frontend`.
- The API key is correct.
- Variable names start with `VITE_FIREBASE_`.
- You restarted Vite after editing `.env`.

### 3. Firebase: auth/operation-not-allowed

Open Firebase Console → Authentication → Sign-in method.

Enable the relevant provider:

- Email/Password for email authentication.
- Phone for mobile OTP.

### 4. Firebase Phone OTP is not working

Check:

- Phone provider is enabled.
- The authorized domains are configured.
- The SMS region policy permits your destination.
- reCAPTCHA is loading successfully.
- Your Firebase phone authentication configuration is correct.

### 5. Backend Firebase Admin error

Check that the Firebase service-account JSON exists at the path configured in `backend/.env`.

### 6. Python dependency errors

Activate the correct virtual environment:

```cmd
.venv\Scripts\activate.bat
```

Reinstall dependencies:

```cmd
python -m pip install -r requirements.txt
```

### 7. Frontend TypeScript errors

Run:

```cmd
npm run build
```

This checks TypeScript and generates the production frontend build.

### 8. Blank white page

Open browser Developer Tools:

```text
F12 → Console
```

Inspect the red errors and resolve the underlying issue.

---

## 🔒 Security

Security practices followed or required for this project:

- Firebase Authentication for user identity.
- Firebase Admin verification for protected backend routes.
- Environment variables for API credentials.
- `.gitignore` for sensitive files.
- No Firebase Admin private keys in frontend code.
- No hardcoded AI or speech API secrets.
- Validate user input on the backend.
- Configure appropriate Firebase security rules.
- Apply rate limiting and request validation before production deployment.

Never commit:

```text
.env
firebase-service-account.json
*.db
.venv/
node_modules/
dist/
```

---

## 🚧 Future Enhancements

Planned improvements include:

- React Native mobile application using Expo.
- Continuous voice conversation.
- Improved multilingual speech recognition.
- More advanced RAG retrieval.
- Official IMD weather-data integration, subject to API access and documentation.
- Weather alerts and notifications.
- Location-based weather personalization with user consent.
- PostgreSQL migration.
- Docker containerization.
- Kubernetes deployment.
- Terraform infrastructure automation.
- CI/CD using GitHub Actions.
- Prometheus and Grafana monitoring.
- Cloud deployment on AWS or Azure.

---

## 🤝 Contributing

Contributions and suggestions are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Implement your changes.
4. Test your changes locally.
5. Commit and push your changes.
6. Open a Pull Request.

Example:

```cmd
git checkout -b feature/new-weather-feature

git add .

git commit -m "Add new weather feature"

git push origin feature/new-weather-feature
```

---

## 📄 License

This project is intended for educational and academic development.

Add a `LICENSE` file to the repository before publishing it under a specific open-source license.

---

## 👨‍💻 Project Information

**Project:** ForecastGPT — AI-Powered Multilingual Weather Companion

**Category:** Artificial Intelligence | Cloud Computing | Full-Stack Development

**Development Focus:** Conversational AI, Weather APIs, Multilingual Voice Processing, Cloud-Ready Architecture

**Frontend:** React + TypeScript + Vite

**Backend:** Python + FastAPI

**Authentication:** Firebase

**Weather Provider:** Open-Meteo

---

⭐ If you find this project interesting, consider starring the repository and following its development.

**ForecastGPT — Making Weather Conversations Smarter, Simpler, and More Accessible.**
