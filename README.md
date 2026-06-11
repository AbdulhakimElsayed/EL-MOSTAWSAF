<div align="center">
🏥 El-Mostawsaf — المستوصف
AI-Powered Smart Hospital Ecosystem
![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Flutter](https://img.shields.io/badge/Flutter-3.x-02569B?logo=flutter)
![FastAPI](https://img.shields.io/badge/FastAPI-Python-009688?logo=fastapi)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Supabase-4169E1?logo=postgresql)
![Docker](https://img.shields.io/badge/Docker-Containerized-2496ED?logo=docker)
Flutter · FastAPI · Node.js · PostgreSQL · TensorFlow · Gemini AI · Docker
View Repository · Report Bug · Request Feature
---
> ⚠️ **Official Notice:** This is the **sole and original** El-Mostawsaf project in Egypt (2026).  
> Any repository with a similar name (e.g., `El-Mostawsaf-HomeNursingPlatform`) is **not affiliated** with this project.
</div>
---
📋 Table of Contents
Overview
The Problem We Solve
System Architecture
Core Components
AI & Machine Learning Engine
Tech Stack
Performance Metrics
Getting Started
Project Team
Future Roadmap
License
Official References
---
🌐 Overview
Egypt's healthcare system faces a critical convergence of challenges: fragmented medical records across incompatible hospital databases, a severe specialist shortage with 80% of physicians concentrated in major cities, insufficient continuous monitoring for chronic disease patients, and delayed emergency response caused by inaccessible patient data.
El-Mostawsaf (Arabic: المستوصف — The Dispensary) is our answer — a unified, intelligent healthcare fabric that seamlessly connects patients, physicians, and administrators through a single integrated platform. It is a production-grade, AI-driven ecosystem that unifies Electronic Medical Records, real-time IoT vital monitoring, and multimodal clinical AI into one cohesive solution built specifically for Egypt's healthcare landscape.
---
🚨 The Problem We Solve
Challenge	Impact	Our Solution
Fragmented Medical Records	Duplicate tests, missed diagnoses, medication errors	Centralized cloud-based EMR with full audit trails
Specialist Access Gap	3–6 month wait times; zero rural access	AI-assisted triage + integrated telemedicine
No Continuous Monitoring	Chronic crises go undetected between visits	Real-time IoT vital monitoring with anomaly alerts
Language Barrier in AI	No colloquial Egyptian Arabic medical AI exists	RAG chatbot trained on 136,000 Arabic Q&A pairs
Delayed Emergency Response	Critical patient data unreachable in emergencies	Emergency SOS with live location + instant medical profile
Data Security Risks	Paper records vulnerable to loss and theft	AES-256 encryption, RBAC, and HIPAA-inspired compliance
---
🏗 System Architecture
The system follows a multi-layered architecture with strict separation of concerns across seven distinct layers:
Layer	Responsibility	Technologies
Presentation	Mobile app + web portals	Flutter, HTML5/CSS3, Bootstrap 5, JavaScript ES6+
Backend & API	Business logic, REST endpoints, auth	Node.js/Express, FastAPI, JWT, RESTful APIs
AI & Diagnostic	LLM inference, vision models, NLP	Gemini API, MedGemma-4B, LangChain, FAISS, ChromaDB
IoT & Wearable	BLE telemetry, vital streaming	BLE Protocol, Python anomaly detection
Data Storage	Relational DB, file storage, vectors	PostgreSQL (Supabase), Firebase Storage, ChromaDB
Real-Time Comms	Live updates, chat, monitoring	Socket.io, WebSockets, Server-Sent Events (SSE)
Security & Compliance	Auth, encryption, auditing	JWT, AES-256, RBAC, RLS, HTTPS/TLS
---
🧩 Core Components
📱 1. Patient Mobile Application (Flutter)
Built with Clean Architecture (Presentation / Domain / Data layers) following the MVC pattern.
Key Capabilities:
Secure registration and biometric authentication with encrypted local storage
Personal Electronic Health Record (EHR) — medical history, allergies, prescriptions, and chronic diseases
Upload and OCR-scan lab reports; submit radiology images for AI-powered analysis
Native Arabic AI chatbot for symptom checking and preliminary triage
Real-time vital signs dashboard from the BLE wearable (Heart Rate, SpO₂, Temperature)
Smart booking and referral system — AI suggests the right specialty and books the nearest clinic
Integrated telemedicine for video consultations without leaving the app
Emergency SOS mode — shares live location and a summarized medical profile with the nearest hospital
Full Arabic/English localization with RTL support
---
👨‍⚕️ 2. Doctor Web Dashboard
Key Capabilities:
Personalized dashboard with daily KPIs: Today's Appointments, Upcoming, and Completed
Patient Medical Records modal: Medical History, AI Analysis, Lab Results, New Record, Schedule
Real-time vital feed from patient wearables with color-coded risk indicators (🟢 Green / 🟡 Amber / 🔴 Red)
Full dark mode / light mode theming via CSS custom properties — no page reload required
AI Analysis tab delivering AI-generated clinical insights per patient record
Complete appointment management with advanced filtering, booking, and status control
---
🛡️ 3. Admin Portal
Key Capabilities:
User CRUD across all roles (Doctors, Patients, Admins) with real-time search and role filtering
Appointments overview with filtering by doctor, patient, date, and status
System settings: toggle Telemedicine, toggle Maintenance Mode, view API health status
Security configuration: AES-256 status, RLS confirmation, JWT timeout settings
---
⌚ 4. IoT Wearable Band
Key Capabilities:
Real-time streaming of Heart Rate, SpO₂, body temperature, and physical activity via BLE
Local anomaly detection algorithms that trigger alerts even in offline scenarios
Automatic synchronization with the Flutter mobile app
Simultaneous alerts dispatched to both patient (mobile) and physician (dashboard)
---
🧠 AI & Machine Learning Engine
El-Mostawsaf's AI layer is built on four core technological pillars:
1. Hybrid RAG Engine — Arabic Medical Chatbot
Property	Detail
Architecture	Retrieval-Augmented Generation (RAG)
LLM	Gemini API via LangChain AgentExecutor
Vector Store	ChromaDB + FAISS-CPU (dense retrieval) + BM25 (keyword retrieval)
Knowledge Base	136,000 balanced Arabic medical Q&A pairs (sourced from Altibbi)
Coverage	20 medical specialties · 6,800 records each
Language	Colloquial Egyptian Arabic with full NLP preprocessing pipeline
The chatbot routes queries through a Dynamic Router-Based Multimodal Architecture across four specialized pipelines:
Q&A RAG Pipeline — general medical questions from the curated knowledge base
Lab RAG Pipeline — interprets uploaded lab results against a structured laboratory knowledge base
Vision Pipeline — fine-tuned model for dermatological and burn classification
Web Search Pipeline — Tavily Search API integration for real-time medical information
---
2. Medical Vision System — MedGemma-4B & Burn Classification
Property	Detail
Model	MedGemma-4B (medically pre-trained Vision-Language Model)
Fine-tuning	PEFT / LoRA via TRL 0.10.0
Training Hardware	Google Colab T4 GPU
Visual Dataset	~1,500 captioned medical images localized to Egyptian Arabic
Supported Diagnostic Tasks:
Task	Dataset	Accuracy
Bone Fracture Detection	MURA (Musculoskeletal Radiographs)	> 90%
Burn Severity Classification (3-class)	Augmented dermatology dataset	84.4%
---
3. Cloud Deployment on Modal Labs
Serverless inference deployed on Modal Labs using A10G GPU instances, enabling scalable, low-latency AI model serving compatible with AWS, Azure, and GCP environments.
---
4. RESTful AI Gateway (FastAPI)
A dedicated FastAPI service exposes all AI capabilities — chatbot, vision inference, lab parsing, and IoT anomaly detection — through secure, versioned REST endpoints.
---
🛠 Tech Stack
Layer	Technologies
Mobile Frontend	Flutter (Dart), Provider, Clean Architecture, MVC
Web Frontend	HTML5, CSS3, Bootstrap 5, JavaScript ES6+
Backend API	Node.js / Express.js (EMR & Web), FastAPI Python (AI Gateway)
AI Orchestration	LangChain (AgentExecutor, Tools, Memory)
LLM	Google Gemini API, MedGemma-4B
Vision / ML	TensorFlow, Keras, PyTorch 2.2.2, Transformers 4.46.3, PEFT/LoRA
Vector Database	ChromaDB, FAISS-CPU 1.9.0, BM25 (Rank-BM25 0.2.2)
Database	PostgreSQL via Supabase (RLS), Firebase Firestore & Storage
Real-Time	Socket.io, WebSockets, Server-Sent Events (SSE)
Auth & Security	JWT, bcrypt, AES-256, HTTPS/TLS, RBAC, Row-Level Security
PDF Generation	ReportLab 4.2.5
Arabic NLP	Arabic-Reshaper 3.0 (RTL rendering)
Containerization	Docker
Cloud Deployment	Modal Labs (Serverless, A10G GPU), AWS / Azure / GCP compatible
Notifications	Firebase Cloud Messaging (FCM)
Dev Environment	Python 3.10, Conda, WSL2, Google Colab
---
📊 Performance Metrics
Model / Component	Metric	Result
Bone Fracture Detection (CNN on MURA)	Overall Accuracy	> 90%
Burn Severity Classification (3-class)	Overall Accuracy	84.4%
MedGemma-4B vs. base Gemma-3 4B	Clinical Benchmark	Consistent gains across all domains
Arabic Medical Chatbot (RAG)	NLG Evaluation (BLEU / ROUGE)	Reported in thesis §5.5.11
Arabic Knowledge Base	Total Q&A Pairs	136,000 across 20 specialties
Visual Training Dataset	Captioned Medical Images	~1,500 localized images
---
🚀 Getting Started
Prerequisites
Flutter SDK v3.x+
Python 3.10+ (Conda environment recommended)
Node.js v18+
PostgreSQL instance (or Supabase project)
Firebase project (FCM + Storage)
Gemini API key
Installation
```bash
# 1. Clone the repository
git clone https://github.com/A_235_s/El-Mostawsaf.git
cd El-Mostawsaf

# 2. Backend — Node.js (EMR & Web API)
cd backend_api
npm install
# Configure .env with SUPABASE_URL, JWT_SECRET, etc.
npm start

# 3. Backend — FastAPI (AI Gateway)
cd ../ai_engine
pip install -r requirements.txt
# Configure .env with GEMINI_API_KEY, model paths, etc.
uvicorn main:app --host 0.0.0.0 --port 8000 --reload

# 4. Mobile App (Flutter)
cd ../patient_app
flutter pub get
flutter run

# 5. Docker (Optional — runs all services)
cd ..
docker-compose up --build
```
Project Structure
```
El-Mostawsaf/
├── patient_app/          # Flutter mobile application
│   └── lib/
│       ├── core/         # Config, constants, utilities
│       ├── data/         # Repositories, API clients, models
│       ├── domain/       # Business logic, use cases, entities
│       └── presentation/ # UI screens, widgets, providers
├── backend_api/          # Node.js / Express.js EMR backend
│   ├── routes/           # REST API route definitions
│   ├── middleware/       # JWT auth, RBAC, error handling
│   └── db/               # Supabase/PostgreSQL queries
├── ai_engine/            # FastAPI AI gateway
│   ├── rag/              # RAG pipeline (ChromaDB, FAISS, BM25)
│   ├── vision/           # MedGemma-4B inference
│   ├── lab/              # Lab report NLP parser
│   └── iot/              # Wearable telemetry + anomaly detection
├── web_dashboard/        # Doctor & Admin web portals
│   ├── admin/
│   └── doctor/
└── docs/                 # Project thesis and documentation
    └── images/           # Architecture diagrams and screenshots
```
---
🎓 Project Team
Graduation Project 2025–2026  
Benha University | Faculty of Engineering at Shoubra  
Communication and Computer Engineering Department
Submitted as partial fulfillment of the requirements for the degree of Bachelor of Science in Electrical Engineering (Computer & Communication Systems Engineering)
Supervised by: Dr. Shimaa Ibrahim
Name	ID	Role
Abdelhakim Elsayed Abdelhakim	231903594	Lead Flutter Developer & AI Integration
Mohamed Emad Fawzy	231903548	Backend & API Orchestration
Saif Emad Shaheen	231903756	AI Model Development & Research
Omar Masoud Mohamed	231903652	System Architecture & Database
Abdelrahman Tarek Salah	231903611	Web Frontend & UI/UX
Shady Mohamed Fathy	221902907	IoT & Hardware Engineering
---
🔭 Future Roadmap
Offline AI — TensorFlow Lite on-device models for basic analysis without internet connectivity
HL7/FHIR Integration — Interoperability with national hospital information systems
Expanded Wearable Support — Compatibility with Apple Watch, Garmin, and Fitbit
Medication Reminder System — Intelligent notification engine to improve patient adherence
Family Health Sharing — Caregiver accounts for remote family health monitoring
Prescription Module — Digital prescriptions linked directly to appointment records
Formal HIPAA/GDPR Audit — Compliance certification for international deployment
Insurance & Billing Module — Automated invoice generation for consultations
Improved Vision Models — Extended datasets for dermatology and ophthalmology
---
📄 License
This project is licensed under the MIT License — see the LICENSE file for full details.
---
🔗 Official References
For the authoritative and complete documentation of El-Mostawsaf, refer only to the following sources:
📝 Medium Article — How El-Mostawsaf is redefining healthcare with AI
📄 LinkedIn Article — Top 5 HealthTech Projects in Egypt 2026
🌐 Official Landing Page
📚 Benha University Graduation Projects Registry
> ⚠️ **Disclaimer:** Any GitHub repository with a similar name (e.g., `El-Mostawsaf-HomeNursingPlatform`) is **not affiliated** with this project. This repository is the sole and original source of the El-Mostawsaf ecosystem.
---
<div align="center">
Built with ❤️ for a Healthier Egypt
El-Mostawsaf — Bridging the gap between medical data and actionable insights.
</div>
