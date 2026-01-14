

# Phishing Perception: End-to-End MLOps Pipeline for Network Security

[![MLOps](https://img.shields.io/badge/MLOps-MLflow-blue)](https://mlflow.org/)
[![Python](https://img.shields.io/badge/Python-3.9+-green)](https://www.python.org/)
[![Docker](https://img.shields.io/badge/Docker-Ready-blue)](https://www.docker.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

An industrial-grade machine learning framework designed to detect malicious network traffic and phishing attempts. This project demonstrates a complete **MLOps lifecycle**: from automated data ingestion and drift detection to containerized deployment and CI/CD.

---

## 🔬 1. Project Overview & Motivation

In modern network security, data distributions shift rapidly as attackers evolve their tactics. This system addresses two critical challenges in building robust security AI:

1.  **Automated Pipeline Orchestration:** Moving away from static notebooks toward a modular, production-ready pipeline that ensures reproducibility in research.
2.  **Data Integrity & Drift Detection:** Implementing the **Kolmogorov-Smirnov (K-S) test** to statistically identify when incoming live data deviates from the training distribution—a key requirement for reliable autonomous systems.

---

## 🚀 2. Key Capabilities

* **Multistage Pipeline Architecture:** Fully decoupled modules for Data Ingestion, Validation, Transformation, and Model Training.
* **Proactive Drift Detection:** An automated validation layer checks for **feature-level distribution shifts** before training to prevent model performance decay.
* **Asynchronous API Service:** Built with **FastAPI** to support asynchronous training triggers and high-volume batch inference via CSV uploads.
* **Enterprise-Grade Artifact Tracking:** Integrated with **MLflow** and **DagsHub** for full experiment versioning and model lineage.
* **Cloud-Native CI/CD:** Optimized for **AWS (ECR/EC2)** with a GitHub Actions workflow for automated containerization and deployment.

---

## 🛠 3. Tech Stack

| Category | Tools |
| :--- | :--- |
| **Frameworks** | FastAPI, Scikit-learn, Pandas, NumPy |
| **Database** | MongoDB Atlas (Scalable NoSQL storage) |
| **Orchestration** | MLflow, DagsHub (Experiment tracking & Artifact logging) |
| **Infrastructure** | Docker, AWS (ECR/EC2), GitHub Actions |
| **Security** | TLS/SSL integration via Certifi, Python-dotenv |

---

## 📂 4. Project Structure

```text
├── src/
│   ├── components/       # Core ML logic (ingestion, transformation, training)
│   ├── pipeline/         # Orchestration scripts for training and prediction
│   ├── entity/           # Configuration and Artifact data classes
│   ├── constant/         # Global constants (DB names, file paths)
│   └── utils/            # Helper functions for I/O and logging
├── Artifacts/            # Auto-generated (datasets, drift reports, serialized models)
├── templates/            # Web UI for batch prediction uploads
├── Dockerfile            # Containerization configuration
└── main.py               # FastAPI entry point

```

---

## ⚙️ 5. Setup & Installation

### 1. Environment Variables

Create a `.env` file in the root directory and add your credentials (ensure this file is in your `.gitignore`):

```env
MONGO_DB_URL="your_mongodb_atlas_url"
AWS_ACCESS_KEY_ID="your_aws_key"
AWS_SECRET_ACCESS_KEY="your_aws_secret"
AWS_REGION="us-east-1"

```

### 2. Local Installation

```bash
# Clone the repository
git clone [https://github.com/Gauti555/Your-Repo-Name.git](https://github.com/Gauti555/Your-Repo-Name.git)
cd Your-Repo-Name

# Install dependencies
pip install -r requirements.txt

# Start the API service
python main.py

```

---

## 🐳 6. Docker Deployment (AWS EC2)

To deploy the system on an Ubuntu-based EC2 instance using the provided automation:

```bash
# Install and configure Docker
curl -fsSL [https://get.docker.com](https://get.docker.com) -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker $USER && newgrp docker

# Build and run the container
docker build -t networkssecurity .
docker run -d -p 8080:8080 networkssecurity

```

---

## 📊 7. API Endpoints

* **`GET /train`**: Triggers the full end-to-end pipeline (Ingestion → Validation → Training).
* **`POST /predict`**: Accepts a CSV file upload for batch inference; returns predictions and saves the output locally.

---

## ⚖️ 8. License

This project is licensed under the **MIT License**. See the [LICENSE](https://www.google.com/search?q=LICENSE) file for details.

---

