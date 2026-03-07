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

## CI/CD Flow
![diagram](https://github.com/user-attachments/assets/8230a61d-187a-4db2-8430-ee210bbf01a8)


## Learning Outcomes / Why This is Valuable

- **Understand CI/CD toolchain:** GitHub Actions → Jenkins → Kubernetes  
- **Learn containerization:** Building images for reproducible test environments  
- **Secure automation:** Using service accounts and tokens instead of exposing credentials  
- **End-to-end pipeline:** From code commit → automated tests → logs → feedback  
- **Portfolio advantage:** Demonstrates full-stack QA automation and cloud-native testing  

This structure is exactly how modern QA teams set up test automation pipelines for **large-scale web applications** — a **mini production-grade learning environment**.



