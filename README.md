# 🫁 Chest Cancer Classification using MLflow and DVC

![Python](https://img.shields.io/badge/Python-3.10-blue?style=for-the-badge&logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.15-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-2.0-000000?style=for-the-badge&logo=flask&logoColor=white)
![MLflow](https://img.shields.io/badge/MLflow-2.0-0194E2?style=for-the-badge&logo=mlflow&logoColor=white)
![DVC](https://img.shields.io/badge/DVC-3.0-945DD6?style=for-the-badge&logo=dvc&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-20.10-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-EC2%20%7C%20ECR-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white)

A deep learning-based web application for classifying chest CT scan images to detect **Adenocarcinoma Cancer** or **Normal** tissue. Built with a complete MLOps pipeline using MLflow for experiment tracking, DVC for data versioning, and automated CI/CD deployment to AWS.

---

## 🚀 Key Features

### 1. 🔬 Deep Learning Classification

- **Model Architecture:** Transfer learning using **VGG16** pre-trained on ImageNet
- **Binary Classification:** Detects Adenocarcinoma Cancer vs Normal chest tissue
- **Image Preprocessing:** Automatic resizing, normalization, and augmentation

### 2. 📊 MLOps & Experiment Tracking

- **MLflow Integration:** Track experiments, parameters, metrics, and model artifacts
- **DagsHub:** Remote MLflow tracking server for team collaboration
- **DVC Pipeline:** Reproducible ML pipelines with data version control

### 3. 🌐 Web Application

- **Modern UI:** Dark theme, responsive design with Bootstrap
- **Real-time Prediction:** Upload chest CT scan and get instant classification
- **User-friendly:** Simple drag-and-drop image upload interface

### 4. ☁️ CI/CD & Cloud Deployment

- **GitHub Actions:** Automated testing, building, and deployment
- **Docker:** Containerized application for consistent deployment
- **AWS ECR + EC2:** Production deployment on AWS infrastructure

---

## 🛠️ Tech Stack

| Category             | Technologies                 |
| -------------------- | ---------------------------- |
| **Deep Learning**    | TensorFlow, Keras, VGG16     |
| **Web Framework**    | Flask, HTML, CSS, JavaScript |
| **MLOps**            | MLflow, DVC, DagsHub         |
| **Containerization** | Docker                       |
| **Cloud**            | AWS EC2, AWS ECR             |
| **CI/CD**            | GitHub Actions               |

---

## 📁 Project Structure

```
├── .github/workflows/     # CI/CD pipeline configuration
├── artifacts/             # Model artifacts and data
├── config/                # Configuration files
├── research/              # Jupyter notebooks for experimentation
├── src/cnnClassifier/     # Main source code
│   ├── components/        # Data ingestion, model training, evaluation
│   ├── config/            # Configuration manager
│   ├── entity/            # Data classes
│   ├── pipeline/          # Training and prediction pipelines
│   └── utils/             # Utility functions
├── templates/             # HTML templates
├── app.py                 # Flask web application
├── main.py                # Training pipeline entry point
├── params.yaml            # Model hyperparameters
├── dvc.yaml               # DVC pipeline definition
├── Dockerfile             # Docker configuration
└── requirements.txt       # Python dependencies
```

---

## ⚙️ Installation & Setup

### Prerequisites

- Python 3.10+
- Git
- Docker (optional, for containerized deployment)

### 1. Clone the Repository

```bash
git clone https://github.com/darshanbm26/Chest-Cancer-Classification-using-MLflow-and-DVC.git
cd Chest-Cancer-Classification-using-MLflow-and-DVC
```

### 2. Create Virtual Environment

```bash
# Create environment
python -m venv venv

# Activate (Windows)
venv\Scripts\activate

# Activate (Mac/Linux)
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Run Training Pipeline

```bash
python main.py
```

### 5. Launch Web Application

```bash
python app.py
```

Open your browser and navigate to `http://localhost:8080`

---

## 🔄 Workflows

The modular pipeline follows this workflow:

1. Update `config.yaml`
2. Update `secrets.yaml` [optional]
3. Update `params.yaml`
4. Update the entity
5. Update the configuration manager in src config
6. Update the components
7. Update the pipeline
8. Update `main.py`
9. Update `dvc.yaml`

---

## 📈 MLflow Experiment Tracking

### Local MLflow UI

```bash
mlflow ui
```

### DagsHub Integration

Configure MLflow to track experiments on DagsHub:

```bash
export MLFLOW_TRACKING_URI=https://dagshub.com/darshanbm26/Chest-Cancer-Classification-using-MLflow-and-DVC.mlflow

export MLFLOW_TRACKING_USERNAME=darshanbm26

export MLFLOW_TRACKING_PASSWORD=<your-token>
```

📖 **MLflow Documentation:** https://mlflow.org/docs/latest/index.html

---

## 🔁 DVC Pipeline

Initialize and run the DVC pipeline:

```bash
# Initialize DVC
dvc init

# Run pipeline
dvc repro

# Visualize pipeline DAG
dvc dag
```

---

## ☁️ AWS CI/CD Deployment with GitHub Actions

### Step 1: Login to AWS Console

### Step 2: Create IAM User for Deployment

**Required Access:**

- **EC2:** Virtual machine for hosting
- **ECR:** Elastic Container Registry to store Docker images

**IAM Policies:**

- `AmazonEC2ContainerRegistryFullAccess`
- `AmazonEC2FullAccess`

### Step 3: Create ECR Repository

Create an ECR repository and save the URI.

### Step 4: Create EC2 Instance (Ubuntu)

### Step 5: Install Docker on EC2

```bash
# Update packages (optional)
sudo apt-get update -y
sudo apt-get upgrade -y

# Install Docker
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker
```

### Step 6: Configure EC2 as Self-Hosted Runner

1. Go to Repository → **Settings** → **Actions** → **Runners**
2. Click **New self-hosted runner**
3. Choose OS (Linux)
4. Run the provided commands on your EC2 instance

### Step 7: Setup GitHub Secrets

Add the following secrets in your repository settings:

| Secret Name             | Description                    |
| ----------------------- | ------------------------------ |
| `AWS_ACCESS_KEY_ID`     | IAM user access key            |
| `AWS_SECRET_ACCESS_KEY` | IAM user secret key            |
| `AWS_REGION`            | AWS region (e.g., `us-east-1`) |
| `AWS_ECR_LOGIN_URI`     | ECR login URI                  |
| `ECR_REPOSITORY_NAME`   | ECR repository name            |

---

## 🐳 Docker

### Build Image

```bash
docker build -t chest-cancer-classifier .
```

### Run Container

```bash
docker run -d -p 8080:8081 chest-cancer-classifier
```

---

## 📸 Screenshots

<img width="1920" height="898" alt="image" src="https://github.com/user-attachments/assets/aaad8816-8015-449a-be00-c10ea675b60b" />
<img width="1920" height="1080" alt="Screenshot (324)" src="https://github.com/user-attachments/assets/50024b2d-4de4-441f-8303-550549854fbd" />
<img width="1920" height="1080" alt="Screenshot (325)" src="https://github.com/user-attachments/assets/3ef78613-9f58-4a3c-8184-7ef7ee4bc341" />
<img width="1920" height="1080" alt="Screenshot (327)" src="https://github.com/user-attachments/assets/5cdbb0a5-82d2-41df-a7ef-90a1ebfe1894" />
<img width="1920" height="1080" alt="Screenshot (326)" src="https://github.com/user-attachments/assets/a8144165-81a0-40e9-af7a-1c975b16191c" />
<img width="1920" height="1080" alt="Screenshot (329)" src="https://github.com/user-attachments/assets/c214ec7c-5506-45cf-b3c1-003716dd03b2" />
<img width="1128" height="608" alt="image" src="https://github.com/user-attachments/assets/25f37ac9-85e3-4587-a6e3-596a53979e61" />


---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Darshan B M**

[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/darshanbm26)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/darshanbm26/)

---

<p align="center">
  ⭐ Star this repository if you found it helpful!
</p>
