# CI/CD & Test Automation Pipeline – Project Overview

This project implements a **full CI/CD pipeline** for automated Playwright test execution using **GitHub, Docker, Jenkins, and Kubernetes**.  

The goal wasn’t just to run tests—it was to **learn how modern DevOps and QA tools work together** and understand their responsibilities in a real-world workflow.

---

## Why This Setup?

We wanted to:

- **Separate concerns**  
  Each tool has a single responsibility, making debugging, scaling, and maintenance easier.

- **Simulate a real-world automation environment**  
  Developers push code → tests run automatically in isolated containers.

- **Learn the CI/CD flow end-to-end**  
  From code commit to test results **without touching the host machine**.

---

## CI/CD Flow Diagram

  [Code Push]
         │
         ▼
  ┌───────────────────┐
  │ GitHub Repository │
  │  - Source code    │
  │  - Jenkinsfile    │
  └───────────────────┘
         │
         ▼
  ┌───────────────────────────┐
  │ GitHub Actions (CI Build) │
  │  - Checkout repo          │
  │  - Build Docker image     │
  │  - Push to Docker Hub     │
  └───────────────────────────┘
         │
         ▼
  ┌───────────────────────────┐
  │ Docker Hub (Registry)     │
  │  - Stores latest image    │
  └───────────────────────────┘
         │
         ▼  (GitHub webhook triggers)
  ┌───────────────────────────┐
  │ Jenkins (Deployment CI/CD)│
  │  - Pull repo              │
  │  - Read Jenkinsfile       │
  │  - Run kubectl commands   │
  │    • delete old job       │
  │    • apply new job        │
  │    • wait for completion  │
  │    • fetch logs           │
  └───────────────────────────┘
         │
         ▼
  ┌───────────────────────────┐
  │ Kubernetes Cluster        │
  │  - Pulls image from Hub   │
  │  - Runs Job (Playwright)  │
  │  - Executes UI tests      │
  └───────────────────────────┘
         │
         ▼
  ┌───────────────────────────┐
  │ Logs Returned to Jenkins  │
  │  - View test output       │
  │  - Success/Failure        │
  └───────────────────────────┘


## Step-by-Step Explanation

### GitHub Repository
- Stores **source code, Playwright tests, and the Jenkinsfile**.  
- Acts as the **central source of truth** for the pipeline.

### GitHub Actions (CI Build)
- Triggered automatically on **push**.  
- Builds a **Docker image** containing the test environment.  
- Pushes the image to **Docker Hub**.  
- Teaches how CI automation removes manual build steps.

### Docker Hub (Registry)
- Stores the latest images for **Kubernetes to pull**.  
- Demonstrates **centralized artifact storage** in CI/CD pipelines.

### Jenkins (Deployment Orchestrator)
- Triggered via **GitHub webhook**.  
- Reads the **Jenkinsfile** and executes deployment stages:  
  - Deletes old job  
  - Applies new Kubernetes job YAML  
  - Waits for completion  
  - Fetches logs  
- Shows how **CD tools manage deployments independently** of builds.

### Kubernetes Cluster
- Pulls the Docker image and runs the **Playwright tests inside a pod**.  
- Demonstrates **container orchestration** and isolated test execution.

### Playwright Tests Execution
- Runs **fully automated UI tests**.  
- Exits on completion; results are fetched by Jenkins.  
- Highlights **scalable test execution with ephemeral containers**.

### Logs Returned to Jenkins
- Jenkins displays **test output** in the pipeline UI.  
- Developers can see results **immediately without logging into the cluster**.

---

## Learning Outcomes / Why This is Valuable

- **Understand CI/CD toolchain:** GitHub Actions → Jenkins → Kubernetes  
- **Learn containerization:** Building images for reproducible test environments  
- **Secure automation:** Using service accounts and tokens instead of exposing credentials  
- **End-to-end pipeline:** From code commit → automated tests → logs → feedback  
- **Portfolio advantage:** Demonstrates full-stack QA automation and cloud-native testing  

This structure is exactly how modern QA teams set up test automation pipelines for **large-scale web applications** — a **mini production-grade learning environment**.



