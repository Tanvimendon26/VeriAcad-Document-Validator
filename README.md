# VeriAcd – AI-Based Academic Document Validation System

VeriAcd is a full-stack educational document validation platform that verifies academic certificates and marksheets using Artificial Intelligence, Optical Character Recognition (OCR), and institutional record verification.

The system detects forged documents through a CNN-based image classification model, extracts document information using OCR, cross-checks the extracted data with trusted institutional records, and generates a comprehensive validation report with a downloadable PDF.

---

## Features

* Secure user authentication using JWT
* Academic certificate and marksheet upload
* CNN-based visual forgery detection
* OCR-based text extraction (Gemini API with fallback parser)
* Institutional database verification
* Automated validation report generation
* Downloadable PDF verification reports
* Interactive dashboard with validation history
* Role-based access control

---

## Tech Stack

| Layer          | Technologies                                                                  |
| -------------- | ----------------------------------------------------------------------------- |
| **Frontend**   | React 19, Vite 7, Tailwind CSS 4, React Router 7, Axios, Recharts             |
| **Backend**    | Flask 3, Flask-SQLAlchemy, Flask-Migrate, Flask-Limiter, PyJWT                |
| **AI Service** | FastAPI, Uvicorn, PyTorch, Torchvision, OpenCV, Pillow, pdf2image, Gemini API |
| **Database**   | PostgreSQL                                                                    |
| **Testing**    | Pytest, pytest-cov                                                            |

---

## System Architecture

The application is divided into three independent services:

### Frontend

* React + Vite
* Port **5173**

Responsible for:

* User Authentication
* Document Upload
* Dashboard
* Validation Results
* PDF Download

---

### Backend API

* Flask
* Port **5000**

Responsible for:

* Authentication
* User Management
* Upload Management
* Validation Requests
* Database Operations
* PDF Report Generation

---

### AI Model Service

* FastAPI
* Port **8001**

Responsible for:

* CNN Forgery Detection
* OCR Processing
* Data Extraction
* AI Validation Pipeline

---

## Project Structure

```text
Document-Validator/
│
├── frontend/                  # React Frontend
│   ├── src/
│   └── package.json
│
├── backend/                   # Flask Backend
│   ├── app.py
│   ├── blueprints/
│   ├── models/
│   ├── services/
│   ├── requirements.txt
│   └── start_backend.ps1
│
├── AI Model/                  # FastAPI AI Service
│   ├── app/
│   ├── src/
│   ├── saved_models/
│   ├── requirements.txt
│   └── start_ai_model.ps1
│
├── Documentation/
│   ├── ieee_architecture_diagram.mmd
│   └── run.txt
│
└── README.md
```

---

## Workflow

1. User logs into the application.
2. The frontend authenticates the user through the Flask backend.
3. The backend validates JWT tokens and user roles.
4. User uploads an academic document.
5. The backend validates and stores the uploaded document.
6. A validation request is sent to the AI pipeline.
7. The AI service performs:

   * CNN-based forgery detection
   * OCR text extraction
   * Field parsing
8. The backend cross-checks extracted information with institutional records.
9. A final validation decision is generated.
10. The backend creates a downloadable PDF verification report.
11. The frontend displays the validation status and report.

---

## Environment Variables

### Backend (.env)

```env
SECRET_KEY=your_secret_key

JWT_SECRET_KEY=your_jwt_secret

DATABASE_URL=postgresql+psycopg://postgres:password@localhost:5432/document_validator

UPLOAD_FOLDER=uploads

MAX_FILE_SIZE_MB=16
```

---

### AI Model (.env)

```env
GEMINI_API_KEY=your_google_gemini_api_key
```

---

## Installation

### Clone the Repository

```bash
git clone https://github.com/your-username/Document-Validator.git

cd Document-Validator
```

---

## Running the Application

### Step 1 — Start AI Service

```bash
cd "AI Model"

.\start_ai_model.ps1
```

Runs on:

```
http://localhost:8001
```

---

### Step 2 — Start Backend

```bash
cd backend

.\start_backend.ps1
```

Runs on:

```
http://localhost:5000
```

---

### Step 3 — Start Frontend

```bash
cd frontend

npm install

npm run dev
```

Runs on:

```
http://localhost:5173
```

---

## API Health Checks

| Service          | URL                              |
| ---------------- | -------------------------------- |
| Frontend         | http://localhost:5173            |
| Backend          | http://localhost:5000/api/health |
| AI Documentation | http://localhost:8001/docs       |

---

## Testing

Run backend tests:

```bash
pytest
```

Generate coverage report:

```bash
pytest --cov
```

---

## Troubleshooting

### Frontend does not start

* Verify Node.js is installed.
* Delete `node_modules`.
* Run:

```bash
npm install
```

---

### AI Service is not responding

* Ensure the FastAPI server is running.
* Verify the `GEMINI_API_KEY` is configured correctly.
* Check that the required Python dependencies are installed.

---

### Database Connection Error

* Verify PostgreSQL is running.
* Confirm the `DATABASE_URL` in `.env` is correct.
* Run database migrations if required.

---

## Future Enhancements

* Multi-institution database integration
* QR code verification
* Blockchain-backed certificate verification
* Batch document validation
* Email notification system
* Admin analytics dashboard
* REST API for institutional integrations

---

## License

This project is licensed under the MIT License.

---


## Contributors

This project was collaboratively developed by:

* Tanvi Mendon
* Tukaram Chate
* Vedika Singh
