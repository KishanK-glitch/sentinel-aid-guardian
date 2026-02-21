
# SPY Tactical Dashboard – UB-1042

A real-time AI-powered surveillance dashboard built with:

* **FastAPI** (Backend API + WebSocket server)
* **Vite + React (TypeScript)** (Frontend UI)
* Computer Vision & Audio modules (YOLO / custom pipelines)
* Real-time WebSocket communication

---

# 🚀 Features

* Real-time video feed monitoring
* AI-based visual threat detection
* Audio anomaly detection
* WebSocket-based live status updates
* Modular backend architecture
* Production-ready folder structure

---

# 🏗️ Project Structure

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

# ⚙️ Backend Setup (FastAPI)

## 1️⃣ Create Environment (Recommended)

```bash
conda create -n spy python=3.10
conda activate spy
```

OR using venv:

```bash
python -m venv venv
venv\Scripts\activate   # Windows
```

---

## 2️⃣ Install Requirements

```bash
pip install -r requirements.txt
```

If requirements.txt doesn’t exist, typical dependencies are:

```bash
pip install fastapi uvicorn python-multipart websockets opencv-python numpy
```

(Add torch / ultralytics if using YOLO)

---

## 3️⃣ Run Backend

From inside `UB-1042` root:

```bash
uvicorn backend.SPY.main:app --reload --port 8000
```

Backend will run at:

```
http://localhost:8000
```

---

# 🌐 Frontend Setup (Vite + React)

## 1️⃣ Install Node Dependencies

```bash
npm install
```

---

## 2️⃣ Start Frontend Dev Server

```bash
npm run dev
```

Frontend will run at:

```
http://localhost:8080
```

---

# 🔌 WebSocket Configuration

Make sure:

* Backend WebSocket endpoint matches frontend
* Example:

Backend:

```python
@app.websocket("/ws")
```

Frontend:

```ts
new WebSocket("ws://localhost:8000/ws")
```

---

# 🛡️ CORS Configuration (Backend)

Ensure CORS allows frontend:

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

# 📦 Production Build (Frontend)

```bash
npm run build
```

If serving static files from FastAPI, ensure:

```python
app.mount("/", StaticFiles(directory="dist", html=True), name="static")
```

---

# 🧪 Debug Checklist

If frontend shows **“Connecting to SPY Network…”**:

* Confirm backend running on 8000
* Check browser DevTools → Network
* Check WebSocket connection
* Check CORS errors
* Confirm endpoint paths match

---

# 🔐 Environment Variables (Optional)

If using `.env`:

```
ROBOFLOW_API_KEY=your_key_here
MODEL_PATH=path/to/model.pt
```

Load using:

```python
from dotenv import load_dotenv
load_dotenv()
```

---

# 🧠 Tech Stack

* FastAPI
* Uvicorn
* React
* Vite
* TypeScript
* OpenCV
* YOLO (optional)
* WebSockets

---

# 👤 Author

Kishan K,Bhuvan J P,Ananya,Rortin coelho
AI/ML Developer

