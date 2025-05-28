# 🧪 Project Spec – Simulate a Production-Grade ML System with Docker Compose

You are part of an **AI Platform Engineering team** at a tech company that builds internal tools for machine learning, data science, and AI product teams.

Your mission?

> ⚙️ **Assemble a complete, working ML application stack** using Docker Compose to simulate what a real production-grade system looks like — in a local or test environment.

This will be used by:

* **ML Engineers** to validate model APIs

* **AI Engineers** to experiment with pipelines and workflows

* **Data Scientists** to test models end-to-end

* **QA and DevOps teams** to run pre-production validation

🎯 Project Goal - Why build this Docker Compose Stack ? 

"At RealOps Labs, we believe that every ML engineer, data scientist, and AI platform builder should be able to spin up a complete ML system — not in weeks, not in days, but in minutes.

This is where Docker Compose comes in.

Your mission? Build a local-first, fully containerized development stack that mirrors what you'd eventually run in production. You’ll integrate model training, model serving, experiment tracking, and a frontend — all running together, all reproducible, all testable — using a single docker-compose up command.

In the real world, this isn’t just a dev exercise — it’s how high-performing teams test workflows, share prototypes, run integration checks, and debug multi-service ML apps before pushing to staging or Kubernetes.

So forget copy-pasting notebooks or chasing ‘it works on my machine’ bugs. With Docker Compose, you’re laying the groundwork for repeatable, reliable ML systems — the kind that real AI platforms are built on."

---

## 🧱 The Use Case

You’re building a **House Price Prediction App** for internal use. The model predicts real estate prices based on features like size, location, and number of rooms. It needs to be:

* Trained reproducibly

* Served through an API

* Visualized through a web UI

* Logged and tracked for every experiment

---

## 🛠️ What You’ll Work With

The Dockerfiles are already written. Your job is to **tie everything together** using Docker Compose to create a **reproducible, containerized development environment** that mimics a production system.

|  Component |  Purpose |  Technology |  Container? |
|---|---|---|---|
|  Training Pipeline |  Generate model artifacts |  Python Script |  No |
|  Experiment Tracker |  Log metrics, parameters, models |  MLflow |  ✅ (public image) |
|  Model API |  Serve predictions via REST |  FastAPI |  ✅ (Dockerfile provided) |
|  Frontend UI |  Collect input, display predictions |  Streamlit |  ✅ (Dockerfile provided) |
|  Orchestration |  Tie everything together |  Docker Compose |  ✅ |
---

## 🎯 Your Mission

1. **Run the training pipeline** to generate the model and preprocessor

2. **Use Docker Compose** to define and launch a local ML app stack

3. **Validate service-to-service communication**

4. **Simulate what an integrated ML system looks like before deploying to Kubernetes**

⠀
---

## 📂 Project Structure

```
house-price-predictor/
├── run_pipeline.sh                # Generates model artifacts
├── Dockerfile                     # FastAPI Dockerfile
├── streamlit_app/
│   ├── Dockerfile                 # Streamlit Dockerfile
│   └── app.py
└── docker-compose.yml             # You will create this
```

---

## 📌 What You’ll Build

Create a `docker-compose.yml` with the following services:

|  Service |  Build Context/Image |  Port |  Depends On |
|---|---|---|---|
|  `mlflow` |  `ghcr.io/mlflow/mlflow:latest` |  5555 |  - |  
|  `fastapi` |  `.` using root `Dockerfile` |  8000 |  mlflow |  
|  `streamlit` |  `./streamlit_app` Dockerfile |  8501 |  fastapi |  
Use DNS-based service discovery: `streamlit` will call `fastapi` via `http://fastapi:8000`.

---

## ✅ Final Validation Checklist

|  Milestone |  Status |
|---|---|
|  Model training pipeline runs and saves artifacts |  [ ] |
|  MLflow UI accessible at [http://localhost:5555](http://localhost:5555/) |  [ ] |  
|  FastAPI available at [http://localhost:8000/docs](http://localhost:8000/docs) |  [ ] |  
|  Streamlit available at [http://localhost:8501](http://localhost:8501/) |  [ ] |  
|  Streamlit fetches predictions from FastAPI successfully |  [ ] |
|  All services run together with `docker-compose up` |  [ ] |  
---

## 🚀 What You'll Learn (Real-World MLOps Skills)

* How to simulate production ML systems using containerized services

* How to tie together training, serving, tracking, and UI in one reproducible dev stack

* How different roles (ML, AI, Data, DevOps, QA) work on the same ML system using Compose

---

