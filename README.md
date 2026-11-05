# AccessGov AI

### Accessible AI-Assisted Government Service Discovery & Application Preparation

AccessGov AI is a full-stack platform designed to simplify the process of **discovering government services, understanding eligibility, preparing required documents, and tracking application readiness** through an accessibility-focused interface.

It combines **AI-assisted conversation, document intelligence, eligibility logic, accessibility tools, and analytics** into a unified web application.

> **Prototype:** AccessGov AI assists with application preparation and decision support. It does not replace official government portals, government officers, or official document verification.

---

## ✦ What It Does

| Capability | Description |
|---|---|
| **Service Discovery** | Explore government services and their requirements |
| **Eligibility** | Check eligibility using service-specific rules |
| **Document Vault** | Store and reuse application documents |
| **Document Intelligence** | OCR, classification, extraction, validation & readiness analysis |
| **AI Assistant** | Gemini-powered conversational guidance |
| **Accessibility** | Voice interaction, page reading, text scaling & high contrast |
| **Application Preparation** | Track required documents and preparation progress |
| **Analytics** | Accessibility, document, conversation & district insights |

---

## ⚙️ Architecture

```text
                    ┌─────────────────────┐
                    │    React + TS UI    │
                    │ Citizen / Admin     │
                    └──────────┬──────────┘
                               │
                         REST / Axios
                               │
                               ▼
                    ┌─────────────────────┐
                    │    FastAPI API      │
                    │                     │
                    │ Auth • Services     │
                    │ Eligibility         │
                    │ Documents • Agents  │
                    │ Analytics           │
                    └──────────┬──────────┘
                               │
                 ┌─────────────┴─────────────┐
                 ▼                           ▼
        ┌─────────────────┐        ┌─────────────────┐
        │   PostgreSQL    │        │ Document Storage│
        │ Users • Services│        │ PDFs / Images   │
        │ Documents • Logs│        └─────────────────┘
        └─────────────────┘
```

---

## 🧠 Document Intelligence

Documents go through a multi-stage inspection pipeline:

```text
Upload
  ↓
Text Extraction / OCR
  ↓
Classification
  ↓
Field Extraction
  ↓
Validation
  ↓
Quality Analysis
  ↓
Readiness Assessment
```

The system supports both searchable and scanned PDFs using **PyPDF, pdf2image and PaddleOCR**.

It produces indicators such as:

- OCR confidence
- Readability
- Image sharpness
- Extracted fields
- Validation issues
- Readiness score

These results help users identify documents that may need attention before application preparation.

---

## ♿ Accessibility

Accessibility is built into the platform through:

- 🎙️ Voice interaction
- 🔊 Page reading
- 🔠 Adjustable text size
- ◐ High-contrast mode
- 🌐 Multilingual-ready interface
- 🧭 Simplified service guidance

Browser-based voice capabilities use the **Web Speech API**, with React managing accessibility and voice state.

---

## 🤖 AI & Intelligence

The project combines multiple forms of intelligence rather than treating every component as an LLM agent.

### Conversation Intelligence
**Gemini** provides conversational understanding and guidance.

### Document Intelligence
**PaddleOCR + extraction + validation + readiness engines** process uploaded documents.

### Service Intelligence
Structured service data and eligibility rules provide deterministic application guidance.

### Analytics
Backend data processing provides accessibility, document, conversation and district-level insights.

---

## 🛠️ Tech Stack

**Frontend**

`React` · `TypeScript` · `Vite` · `Tailwind CSS` · `React Router` · `Axios`

**Backend**

`Python` · `FastAPI` · `Uvicorn` · `SQLAlchemy` · `Pydantic`

**Database**

`PostgreSQL` · `Alembic`

**AI / Document Processing**

`Gemini` · `PaddleOCR` · `PyPDF` · `pdf2image`

**Authentication**

`JWT` · `Role-Based Access Control`

**Deployment / Development**

`Docker Compose` · `Git`

---

## 📁 Project Structure

```text
AccessGovAI/
├── backend/
│   ├── agents/
│   ├── api/
│   ├── auth/
│   ├── document_intelligence/
│   ├── models/
│   ├── rag/
│   ├── schemas/
│   ├── services/
│   ├── tests/
│   └── alembic/
│
├── datasets/
│   ├── government_services.json
│   ├── scholarship_rules.json
│   ├── pension_rules.json
│   └── income_certificate_rules.json
│
├── frontend/
│   └── src/
│       ├── components/
│       ├── context/
│       ├── pages/
│       └── services/
│
├── docker-compose.yml
└── README.md
```

---

## 🚀 Run Locally

### Backend

```bash
cd backend

python -m venv .venv
.venv\Scripts\activate

pip install -r requirements.txt
python -m alembic upgrade head

python -m uvicorn main:app --reload --port 8000
```

### Frontend

```bash
cd frontend

npm install
npm run dev
```

FastAPI:

```text
http://127.0.0.1:8000
```

API documentation:

```text
http://127.0.0.1:8000/docs
```

---

## 🔐 Security & Privacy

The platform uses **JWT authentication, role-based access control, environment-based secrets, and user-scoped document access**.

Uploaded documents are intentionally excluded from version control.

For production deployment, additional security measures such as encrypted storage, HTTPS, secure secret management, audit logging, and stronger PII protection would be required.

---

## 📌 Scope

AccessGov AI is an **academic prototype and decision-support system**.

It helps users prepare for government-service applications but does not:

- submit applications directly to government departments;
- perform official document verification;
- guarantee eligibility or approval;
- replace official government portals or authorities.

Users should verify final requirements through the relevant official government channel.

---

## 👩‍💻 Author

**Akanksha Mandala**  
B.Tech — Artificial Intelligence & Machine Learning  
Kalasalingam Academy of Research and Education

---

### Repository

**AccessGov AI**  
`github.com/akanksha-mandala/AccessgovAI`
