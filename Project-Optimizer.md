## System & Folder Setup
```
mkdir ai-cicd-optimizer
cd ai-cicd-optimizer
mkdir -p infra jenkins mlflow prometheus grafana fastapi docker data logs
```

## install docker 
https://github.com/PranavKamlaskar/quicknotes/blob/main/Install%20docker

## Install Python + Virtual Environment & Install the ML Stack
https://github.com/PranavKamlaskar/quicknotes/blob/main/Install%20Python%20pip

## Install the ML Stack
```
source venv/bin/activate
pip install torch scikit-learn pandas numpy mlflow fastapi uvicorn[standard] python-multipart
pip install prometheus_client
```
## Setup MLflow- 
Inside ai-cicd-optimizer/mlflow/
```
mkdir mlruns
touch mlflow.db
cd ..
mlflow server \
  --backend-store-uri sqlite:///mlflow.db \
  --default-artifact-root ./mlruns \
  --host 0.0.0.0 --port 5000
```
MLflow will be available at:
http://localhost:5000

## Setup FastAPI Inference Service
https://github.com/PranavKamlaskar/quicknotes/blob/main/Set%20Up%20FastAPI%20Inference%20Server
``` curl http://localhost:8000/health```

## Setup Prometheus
https://github.com/PranavKamlaskar/quicknotes/blob/main/Set%20Up%20Prometheus
Inside /prometheus/prometheus.yml:
Open:http://localhost:9090

## Setup Grafana
https://github.com/PranavKamlaskar/quicknotes/blob/main/Set%20Up%20Grafana

## setup jenkins server 
https://github.com/PranavKamlaskar/quicknotes/blob/main/ssetup%20jenkins

## setup github actions 
https://github.com/PranavKamlaskar/quicknotes/blob/main/Set%20Up%20GitHub%20Actions
