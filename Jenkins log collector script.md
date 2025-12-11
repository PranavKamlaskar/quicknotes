Create file: scripts/jenkins_log_fetch.py
```
import requests
import os
import json
from datetime import datetime

JENKINS_URL = "http://localhost:8080"
JOB_NAME = "example-job"
API_TOKEN = "YOUR_TOKEN"
USER = "admin"

RAW_DIR = "data/raw"

def fetch_build_logs():
    os.makedirs(RAW_DIR, exist_ok=True)

    # get builds list
    url = f"{JENKINS_URL}/job/{JOB_NAME}/api/json"
    resp = requests.get(url, auth=(USER, API_TOKEN)).json()

    for build in resp["builds"]:
        build_num = build["number"]
        log_url = f"{JENKINS_URL}/job/{JOB_NAME}/{build_num}/consoleText"

        log_text = requests.get(log_url, auth=(USER, API_TOKEN)).text

        fname = f"{RAW_DIR}/jenkins_{JOB_NAME}_{build_num}.log"
        with open(fname, "w") as f:
            f.write(log_text)

        print(f"Saved: {fname}")

if __name__ == "__main__":
    fetch_build_logs()
```
