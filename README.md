<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react&logoColor=black" />
  <img src="https://img.shields.io/badge/Flask-3.1-000000?style=for-the-badge&logo=flask&logoColor=white" />
  <img src="https://img.shields.io/badge/YOLOv8-Ultralytics-00FFFF?style=for-the-badge&logo=yolo&logoColor=black" />
  <img src="https://img.shields.io/badge/PyTorch-2.8-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" />
</p>

# 🛡️ SteelGuard — Metal Sheet Defect Detector

An AI-powered web application that detects surface defects on metal sheets and steel coils using **YOLOv8** object detection. Upload an image, and the system returns an annotated result with a detailed analysis report — including defect types, confidence scores, bounding-box locations, severity level, and an overall **PASS / CAUTION / REJECT** verdict.

---

## ✨ Key Features

| Feature | Description |
|---|---|
| 🔍 **Real-Time Detection** | Sub-100 ms inference using YOLOv8 deep learning |
| 📊 **Analysis Report** | Verdict badge, severity level, defect table with confidence bars |
| 📦 **Batch Processing** | Upload and process multiple images in one session |
| 🖼️ **Before / After Comparison** | Side-by-side view of original vs annotated image |
| 📜 **Detection History** | Last 10 detections saved locally for quick recall |
| 💾 **Download & Share** | Save annotated images or share results via Web Share API |
| 🌗 **Dark / Light Mode** | Theme toggle with system preference detection |
| 🎯 **Drag & Drop Upload** | Intuitive file upload with progress bar |
| 🔬 **Scanner Animation** | Live AI scanning overlay during detection |

---

## 🏗️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | React 19 · Vite 7 · Axios · React Hook Form |
| **Backend** | Python · Flask · Flask-CORS |
| **AI / ML** | YOLOv8 (Ultralytics) · PyTorch 2.8 · OpenCV |
| **Data** | NumPy · Pandas · Matplotlib |

---

## 📁 Project Structure

```
Metal-Sheet-Defect-Detector/
├── backend/                  # Flask API server
│   ├── app.py                # Main API — /predict endpoint
│   └── my_model.pt           # Trained YOLOv8 weights (not tracked by git)
├── frontend/                 # React + Vite client
│   ├── public/
│   ├── src/
│   │   ├── App.jsx           # Root component with page routing
│   │   ├── LandingPage.jsx   # Hero landing page with feature showcase
│   │   ├── LandingPage.css
│   │   ├── DefectDetector.jsx # Core detection UI & batch processing
│   │   ├── DefectDetector.css
│   │   ├── index.css
│   │   └── main.jsx          # React entry point
│   ├── package.json
│   └── vite.config.js
├── Images_to_test/           # Sample images for testing
├── requirements.txt          # Python dependencies
├── .gitignore
├── LICENSE                   # MIT License
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- **Python** 3.10 or higher
- **Node.js** 18 or higher & npm
- **Git**
- A trained YOLOv8 model file (`my_model.pt`) placed inside `backend/`

### 1 · Clone the Repository

```bash
git clone https://github.com/<your-username>/Metal-Sheet-Defect-Detector.git
cd Metal-Sheet-Defect-Detector
```

### 2 · Set Up the Backend

```bash
# Create and activate a virtual environment
python -m venv venv

# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate

# Install Python dependencies
pip install -r requirements.txt
```

### 3 · Set Up the Frontend

```bash
cd frontend
npm install
```

### 4 · Add Your Model Weights

Place your trained YOLOv8 model file as:

```
backend/my_model.pt
```

> **Note:** Model weights are excluded from version control via `.gitignore`. If you're sharing the project, consider using [Git LFS](https://git-lfs.com/) or hosting the weights externally.

---

## ▶️ Running the Application

Open **two terminals** — one for the backend and one for the frontend:

**Terminal 1 — Backend (Flask API)**
```bash
cd backend
python app.py
```
The API server will start at `http://localhost:5000`.

**Terminal 2 — Frontend (Vite Dev Server)**
```bash
cd frontend
npm run dev
```
The frontend will start at `http://localhost:5173` (default Vite port).

Open your browser and navigate to **http://localhost:5173** to use the app.

---

## 🔄 How It Works

```
┌──────────────┐      POST /predict       ┌──────────────────┐
│   React UI   │  ──────────────────────▶  │   Flask Server   │
│  (Vite Dev)  │                           │                  │
│              │  ◀──────────────────────  │  YOLOv8 Model    │
│  Annotated   │    JSON { image, report } │  (Ultralytics)   │
│  Report View │                           └──────────────────┘
└──────────────┘
```

1. **Upload** — User uploads a metal sheet image via drag-and-drop or file picker.
2. **Detect** — The image is sent to the Flask backend where YOLOv8 runs inference.
3. **Report** — The backend returns a JSON response containing the base64-encoded annotated image and a structured report with defect details.
4. **Visualize** — The frontend renders a rich analysis report with verdict, severity, defect table, and annotated image.

---

## 📋 API Reference

### `POST /predict`

**Request:** `multipart/form-data`

| Field | Type | Description |
|---|---|---|
| `image` | File | Image file (JPG, PNG, WEBP) |

**Response:** `application/json`

```json
{
  "image": "data:image/png;base64,...",
  "report": {
    "verdict": "REJECT",
    "verdict_reason": "Critical defects detected",
    "total_defects": 3,
    "severity": "High",
    "image_dimensions": { "width": 640, "height": 480 },
    "defects": [
      {
        "class": "scratch",
        "confidence": 0.92,
        "bbox": [120, 45, 380, 210]
      }
    ]
  }
}
```

---

## 🎨 Screenshots

### Landing Page
> A premium landing page with animated background, feature showcase, tech stack section, and a call-to-action.

### Defect Detector
> Drag-and-drop upload zone with real-time scanner animation, analysis report with verdict badge, severity metrics, and a detailed defect table.

---

## 🤝 Contributing

Contributions are welcome! Here's how to get started:

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/your-feature`
3. **Commit** your changes: `git commit -m "Add your feature"`
4. **Push** to the branch: `git push origin feature/your-feature`
5. **Open** a Pull Request

---

## 📜 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics) — State-of-the-art object detection
- [PyTorch](https://pytorch.org/) — Deep learning framework
- [React](https://react.dev/) — Frontend UI library
- [Vite](https://vitejs.dev/) — Lightning-fast build tool
- [Flask](https://flask.palletsprojects.com/) — Lightweight Python web framework

---

<p align="center">
  Made with ❤️ for smarter manufacturing
</p>
