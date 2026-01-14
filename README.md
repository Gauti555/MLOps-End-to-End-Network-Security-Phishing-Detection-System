Network Security System — Phishing Detection (End-to-End ML + FastAPI)

An end-to-end machine learning system for detecting phishing and malicious network traffic using a modular MLOps pipeline and a FastAPI-based training and inference service. The project supports automated data ingestion, validation, drift detection, model training, and cloud-ready deployment.

🚀 Overview

This project provides a production-style ML pipeline that:

Ingests phishing datasets from MongoDB Atlas

Performs schema validation and statistical drift detection (KS-test)

Applies feature engineering and preprocessing

Trains and compares multiple ML models

Exposes a FastAPI service for training and batch prediction

Supports Dockerized deployment with CI/CD on AWS (ECR + GitHub Actions)

✨ Key Features

MongoDB-based ingestion

Push datasets to MongoDB and train directly from the database

Modular ML Pipeline

Data Ingestion – Load data and perform train/test split

Data Validation – Schema checks and data drift detection (KS-test)

Data Transformation – Preprocessing and numpy-ready datasets

Model Training – Train and evaluate multiple classifiers with hyperparameter tuning

FastAPI Service

GET /train → Triggers the full training pipeline

POST /predict → Upload CSV and receive predictions (also saved as output file)

Artifact Management

All pipeline outputs (datasets, drift reports, preprocessors, models) stored under Artifacts/

MLOps & Deployment

Experiment tracking with MLflow + DagsHub

Dockerized for reproducibility

CI/CD via GitHub Actions

Cloud deployment prepared using AWS ECR

🧰 Tech Stack
API & Backend

FastAPI

Uvicorn

Jinja2 Templates

Machine Learning

pandas, NumPy

scikit-learn

SciPy (KS-test for drift detection)

Database

MongoDB Atlas (pymongo, pymongo[srv])

certifi (TLS support)

MLOps

MLflow

DagsHub

DevOps & Cloud

Docker

GitHub Actions

AWS ECR

📁 Project Structure (High Level)
.
├── app.py                     # FastAPI app (/train, /predict)
├── main.py                    # Pipeline runner
├── push_data.py               # Push CSV data into MongoDB
├── requirements.txt
├── Dockerfile
├── templates/
│   └── table.html             # Prediction output UI
├── Network_Data/
│   └── phisingData.csv
├── final_model/
│   ├── model.pkl
│   └── preprocessor.pkl
├── Artifacts/                 # Pipeline outputs (per run)
└── networksecurity/
    ├── components/
    ├── pipeline/
    └── utils/

🔐 Environment Variables

Create a .env file in the project root:

MONGO_DB_URL=mongodb+srv://<username>:<password>@<cluster>/<database>?retryWrites=true&w=majority

📥 Load Dataset into MongoDB

To push the phishing dataset into MongoDB:

python push_data.py


This loads Network_Data/phisingData.csv into MongoDB for training.

🏋️ Train the Model

Start the API:

python app.py


Open Swagger UI:

http://localhost:8000/docs


Trigger training:

GET /train

🔮 Predict

Upload a CSV file to:

POST /predict


Predictions are:

Returned as an HTML table

Saved to prediction_output/output.csv

🐳 Docker Setup

Build the Docker image:

docker build -t networksecurity .


Run:

docker run -p 8000:8000 networksecurity

☁️ AWS Deployment (ECR)
GitHub Secrets

Configure these in your GitHub repository:

AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_REGION = us-east-1
AWS_ECR_LOGIN_URI = 788614365622.dkr.ecr.us-east-1.amazonaws.com/networkssecurity
ECR_REPOSITORY_NAME = networkssecurity

🖥️ Docker Setup on AWS EC2

Run these commands on your EC2 instance:

sudo apt-get update -y
sudo apt-get upgrade -y

curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

sudo usermod -aG docker ubuntu
newgrp docker

📊 Experiment Tracking

All experiments, models, and metrics are tracked using:

MLflow

DagsHub

This allows comparison across multiple algorithms and training runs.

📄 License

Add a license before publishing publicly.
