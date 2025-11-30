Air Quality Sentinel is a full-stack AI application designed to monitor, analyze, and predict air quality levels (PM2.5) in major Pakistani cities. It combines real-time data ingestion, Machine Learning for forecasting, and a RAG (Retrieval-Augmented Generation) chatbot to provide actionable health advice.

🚀 Key Features
🌍 Real-Time Monitoring: Live tracking of AQI, PM2.5, PM10, and weather conditions using OpenWeatherMap API.

🔮 48-Hour Forecasting: Machine Learning pipeline (Random Forest) to predict smog risk hours 48 hours in advance.

🤖 AI Health Assistant: A RAG-powered chatbot (using Weaviate & Groq LLaMA 3) that answers user queries based on a scientific knowledge base.

📊 Interactive Dashboard: A responsive React frontend with data visualization (Recharts) and dynamic smog alerts.

Predictive Analytics: Custom ML model to predict PM2.5 levels based on user-inputted meteorological data.

🐳 Fully Dockerized: Seamless deployment using Docker and Docker Compose.

🛠️ Tech Stack
Frontend
React.js (Hooks, Context API)

Tailwind CSS (Responsive UI)

Recharts (Data Visualization)

Lucide React (Icons)

Backend
FastAPI (High-performance Python API)

Uvicorn (ASGI Server)

Scikit-Learn (ML Pipeline: Random Forest, Gradient Boosting)

Pandas & NumPy (Data Processing)

AI & Vector Search
Weaviate (Vector Database for RAG)

Sentence Transformers (Embeddings)

Groq API (LLM Inference)

DevOps
Docker & Docker Compose (Containerization)

Nginx (Reverse Proxy / Serving Frontend)

📂 Project Structure
Bash

air-quality-project/
├── docker-compose.yml       # Orchestration for Backend, Frontend, and Weaviate
├── backend/                 # FastAPI Application
│   ├── backend.py           # Main API endpoints and RAG logic
│   ├── ml_pipeline.py       # ML Training and Prediction logic
│   ├── requirements.txt     # Python dependencies
│   └── Dockerfile           # Backend container config
└── frontend/                # React Application
    ├── public/
    ├── src/
    │   ├── SmogSentinelTabs.js # Main Dashboard Component
    │   └── ...
    └── Dockerfile           # Frontend container config
⚡ Quick Start (Run Locally)
Prerequisites: Docker and Docker Compose installed.

Clone the repository

Bash

git clone https://github.com/Ashir-Ali-Shah/aqi-quality-project.git
cd aqi-quality-project
Configure API Keys

Open docker-compose.yml or backend/backend.py.

Update GROQ_API_KEY and OPENWEATHER_API_KEY with your valid keys.

Build and Run

Bash

docker-compose up --build
Access the Application

🖥️ Frontend Dashboard: http://localhost:3000

📄 Backend API Docs: http://localhost:8000/docs

🧠 Weaviate Console: http://localhost:8080

🧠 Machine Learning & RAG Details
Forecasting Model
We use a Random Forest Regressor trained on historical weather and pollution data to estimate future PM2.5 concentrations based on:

Temperature, Humidity, Wind Speed, Pressure.

Current pollutant concentrations (NO2, SO2, CO, O3).

RAG System (Chatbot)
Ingestion: Scientific documents about smog and health are chunked and embedded using sentence-transformers.

Storage: Embeddings are stored in Weaviate.

Retrieval: User queries are vector-searched to find relevant context.

Generation: The context + query are sent to Groq (LLaMA 3) to generate an accurate, scientifically grounded answer.
