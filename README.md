
# SPY Tactical Dashboard – UB-1042

SPY Tactical Dashboard is a real-time AI-powered surveillance and monitoring system designed for live threat analysis using computer vision and audio anomaly detection. The system integrates a FastAPI backend with a modern React (Vite + TypeScript) frontend, enabling real-time communication through WebSockets.

---

## Overview

The platform processes live video and audio inputs, performs AI-driven threat detection, and streams structured results to a responsive dashboard interface. The architecture is modular and designed to support scalable integration of additional detection agents or analytical components.

---

## Core Features

* Real-time video feed monitoring
* AI-based visual threat detection
* Audio anomaly detection
* WebSocket-based live system updates
* Modular backend pipeline architecture
* Structured and maintainable project layout

---

## Technology Stack

**Backend**

* FastAPI
* Uvicorn
* WebSockets
* OpenCV
* NumPy
* YOLO (optional, if enabled)
* PyTorch (if required by model)

**Frontend**

* React
* Vite
* TypeScript

---

## Project Structure

```
UB-1042/
│
├── backend/
│   └── SPY/
│       ├── main.py
│       ├── core_pipeline.py
│       ├── vision_agent.py
│       ├── audio_agent.py
│       ├── schemas.py
│       └── ...
│
├── src/                # Frontend (React + Vite)
├── public/
├── requirements.txt
├── package.json
└── README.md
```

---

## Backend Setup

### 1. Create a Virtual Environment

Using Conda:

```
conda create -n spy python=3.10
conda activate spy
```

Or using venv (Windows):

```
python -m venv venv
venv\Scripts\activate
```

---

### 2. Install Dependencies

```
pip install -r requirements.txt
```

If a requirements file is not present, install core dependencies manually:

```
pip install fastapi uvicorn python-multipart websockets opencv-python numpy
```

Install additional ML dependencies if required:

```
pip install torch ultralytics
```

---

### 3. Run the Backend Server

From the root directory (`UB-1042`):

```
uvicorn backend.SPY.main:app --reload --port 8000
```

Backend will be available at:

```
http://localhost:8000
```

---

## Frontend Setup

### 1. Install Node Dependencies

```
npm install
```

---

### 2. Start Development Server

```
npm run dev
```

Frontend will be available at:

```
http://localhost:8080
```

---

## WebSocket Configuration

Ensure that the WebSocket endpoint defined in the backend matches the frontend connection URL.

Backend example:

```python
@app.websocket("/ws")
```

Frontend example:

```typescript
new WebSocket("ws://localhost:8000/ws")
```

Endpoint paths and protocol must match exactly.

---

## CORS Configuration (Backend)

To enable communication between frontend and backend:

```python
from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
    CORSMiddleware,
    allow_origins=["http://localhost:8080"],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

---

## Production Build (Frontend)

To generate a production build:

```
npm run build
```

If serving the frontend from FastAPI:

```python
from fastapi.staticfiles import StaticFiles

app.mount("/", StaticFiles(directory="dist", html=True), name="static")
```

---

## Environment Variables

If environment variables are required, create a `.env` file in the root directory:

```
ROBOFLOW_API_KEY=your_key_here
MODEL_PATH=path/to/model.pt
```

Load environment variables in Python:

```python
from dotenv import load_dotenv
load_dotenv()
```

---

## Troubleshooting

If the frontend remains stuck on “Connecting to SPY Network”:

* Confirm backend is running on port 8000
* Verify WebSocket endpoint path consistency
* Inspect browser developer tools for CORS or WebSocket errors
* Ensure CORS configuration includes the frontend origin

---

## Authors

Kishan K
Bhuvan J P
Ananya
Rortin Coelho

