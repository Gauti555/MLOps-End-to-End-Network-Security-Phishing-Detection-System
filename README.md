
```markdown
# Phishing Perception: End-to-End MLOps Pipeline for Network Security

[![MLOps](https://img.shields.io/badge/MLOps-MLflow-blue)](https://mlflow.org/)
[![Python](https://img.shields.io/badge/Python-3.9+-green)](https://www.python.org/)
[![Docker](https://img.shields.io/badge/Docker-Ready-blue)](https://www.docker.com/)

An industrial-grade machine learning framework designed to detect malicious network traffic and phishing attempts. This project demonstrates a complete **MLOps lifecycle**: from automated data ingestion and drift detection to containerized deployment and CI/CD.

---

## 🔬 Project Overview

In network security, data distributions shift rapidly as attackers evolve. This system addresses two critical challenges in modern ML security:
1. **Automated Pipeline Orchestration:** Transitioning from manual notebooks to a modular, production-ready pipeline.
2. **Data Integrity & Drift:** Implementing statistical tests (Kolmogorov-Smirnov) to detect when incoming network data no longer matches the training distribution.

### 🚀 Key Capabilities
* **Multistage Pipeline:** Decoupled modules for Ingestion, Validation, Transformation, and Training.
* **Proactive Drift Detection:** Automated validation layer checks for **Data Drift** before model training to prevent performance decay.
* **Asynchronous API:** Built with **FastAPI** to support both real-time training triggers and high-volume batch predictions.
* **Cloud-Native Deployment:** Fully dockerized with a CI/CD workflow optimized for **AWS ECR** and EC2.

---

## 🛠 Tech Stack

| Category | Tools |
| :--- | :--- |
| **Frameworks** | FastAPI, Scikit-learn, Pandas, NumPy |
| **Database** | MongoDB Atlas (Scalable NoSQL storage) |
| **Orchestration** | MLflow, DagsHub (Experiment tracking & Artifact logging) |
| **Infrastructure** | Docker, AWS (ECR/EC2), GitHub Actions |
| **Security** | TLS/SSL integration via Certifi, Python-dotenv |

---

## 📂 Project Structure

```text
├── src/
│   ├── components/       # Core ML logic (ingestion, transformation, training)
│   ├── pipeline/         # Trigger scripts for training and prediction
│   ├── entity/           # Configuration and Artifact entity definitions
│   ├── constant/         # Global constants (DB names, file paths)
│   └── utils/            # Helper functions for I/O and logging
├── Artifacts/            # Auto-generated (datasets, drift reports, serialized models)
├── templates/            # Web UI for file upload
├── Dockerfile            # Containerization instructions
└── main.py               # FastAPI entry point

```

---

## ⚙️ Setup & Installation

### 1. Environment Variables

Create a `.env` file in the root directory and add your credentials:

```env
MONGO_DB_URL="your_mongodb_atlas_url"
AWS_ACCESS_KEY_ID="your_aws_key"
AWS_SECRET_ACCESS_KEY="your_aws_secret"

```

### 2. Local Installation

```bash
# Clone the repository
git clone [https://github.com/Gauti555/Your-Repo-Name.git](https://github.com/Gauti555/Your-Repo-Name.git)
cd Your-Repo-Name

# Install dependencies
pip install -r requirements.txt

# Start the API
python main.py

```

---

## 🐳 Docker Deployment (AWS EC2)

To deploy the system on an Ubuntu-based EC2 instance:

```bash
# Update and install Docker
curl -fsSL [https://get.docker.com](https://get.docker.com) -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker $USER && newgrp docker

# Run the container
docker build -t network-security .
docker run -p 8080:8080 network-security

```

---

## 📊 API Endpoints

* `GET /train`: Executes the full ML pipeline (Ingestion → Validation → Training).
* `POST /predict`: Upload a CSV file of network samples to receive batch predictions.

---

