# CI/CD Tools and Practices Final Project Template

## Project Name: ci-cd-final-project

<p align="center">
  <a href="https://github.com/Sairaj213/ci-cd-final-project/actions/workflows/workflow.yml">
    <img src="https://github.com/Sairaj213/ci-cd-final-project/actions/workflows/workflow.yml/badge.svg" alt="CI Workflow" />
  </a>
  <img src="https://img.shields.io/badge/Python-3.9-3776AB?logo=python&logoColor=white" alt="Python 3.9" />
  <img src="https://img.shields.io/badge/Flask-2.1.2-000000?logo=flask&logoColor=white" alt="Flask" />
  <img src="https://img.shields.io/badge/Tekton-Pipelines-00599c?logo=kubernetes&logoColor=white" alt="Tekton" />
  <img src="https://img.shields.io/badge/Red%20Hat-OpenShift-EE0000?logo=redhatopenshift&logoColor=white" alt="OpenShift" />
  <img src="https://img.shields.io/badge/Kubernetes-Compatible-326CE5?logo=kubernetes&logoColor=white" alt="Kubernetes" />
  <img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg" alt="License" />
</p>

This repository contains the complete implementation of the **Continuous Integration and Continuous Delivery (CI/CD) Final Project** for the Coursera course **CI/CD Tools and Practices** (IBM Skills Network).

---

## 🎯 Architecture & CI/CD Pipeline

The solution implements a dual-tier automated delivery pipeline:

1. **Continuous Integration (GitHub Actions):** Triggered automatically on push and pull requests to `main`, validating syntax, style standards, and test suites across isolated container environments.
2. **Continuous Deployment (Tekton / Red Hat OpenShift Pipelines):** An automated cloud-native CD pipeline that prepares workspaces, clones code, runs quality gates, builds OCI container images with Buildah, and deploys services to Kubernetes/OpenShift.

```mermaid
flowchart TD
    subgraph GitHub ["1. Continuous Integration (GitHub Actions)"]
        A[Git Push / PR] --> B[Checkout Code]
        B --> C[Install Python Dependencies]
        C --> D[Lint: Flake8 max-complexity=10]
        D --> E[Unit Tests: Nosetests with Coverage]
    end

    subgraph OpenShift ["2. Continuous Deployment (OpenShift Pipelines / Tekton)"]
        F[(PersistentVolumeClaim<br/>pipelinerun-pvc)] -.-> G
        G([1. cleanup<br/>Alpine:3]) --> H([2. git-clone<br/>ClusterTask])
        H --> I([3. flake8<br/>Python 3.9])
        I --> J([4. nose<br/>Python Unit Tests])
        J --> K([5. buildah<br/>OCI Container Build])
        K --> L([6. openshift-client<br/>oc create deployment])
        L --> M[Running Pod<br/>cicd-app]
    end

    E -.->|Passing Status| G

    classDef gh fill:#24292e,stroke:#fff,stroke-width:2px,color:#fff;
    classDef oc fill:#ee0000,stroke:#fff,stroke-width:2px,color:#fff;
    classDef step fill:#1565c0,stroke:#fff,stroke-width:1px,color:#fff;
    classDef storage fill:#2e7d32,stroke:#fff,stroke-width:2px,color:#fff;

    class A,B,C,D,E gh;
    class G,H,I,J,K,L oc;
    class F storage;
```

---

## 🚀 REST API Service Overview

The backend microservice provides a RESTful API for managing numeric counters:

| HTTP Method | Endpoint | Description |
|:---:|:---|:---|
| `GET` | `/` | Service health status and metadata |
| `GET` | `/counters` | List all tracked counters |
| `POST` | `/counters/<name>` | Create a new counter initialized to zero |
| `GET` | `/counters/<name>` | Retrieve current counter value |
| `PUT` | `/counters/<name>` | Increment counter value by 1 |
| `DELETE` | `/counters/<name>` | Remove counter |

---

## 📂 Project Structure & Manifests

```text
ci-cd-final-project/
├── .github/
│   └── workflows/
│       └── workflow.yml        # GitHub Actions CI Workflow
├── .tekton/
│   ├── tasks.yml               # Tekton Custom Tasks (cleanup, nose)
│   ├── pipeline.yaml           # 6-step declarative OpenShift CD Pipeline
│   ├── pvc.yaml                # PersistentVolumeClaim for workspace
│   └── pipelinerun.yaml        # PipelineRun execution trigger
├── service/
│   ├── routes.py               # REST API endpoints
│   └── common/                 # Logging and error handlers
├── tests/
│   └── test_routes.py          # Automated unit test suite
├── Dockerfile                  # Container build recipe
├── requirements.txt            # Python dependencies
├── setup.cfg                   # Test and coverage configuration
└── README.md                   # Project documentation
```

---

## 🧪 Running Locally

1. **Clone repository:**
   ```bash
   git clone https://github.com/Sairaj213/ci-cd-final-project.git
   cd ci-cd-final-project
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run Code Quality Linting:**
   ```bash
   flake8 service --count --max-complexity=10 --max-line-length=127 --statistics
   ```

4. **Execute Unit Tests:**
   ```bash
   nosetests -v --with-spec --spec-color --with-coverage --cover-package=service
   ```

---

## 📜 License & Acknowledgements

- **License:** Apache License 2.0. See [LICENSE](LICENSE) for details.
- **Author:** Skills Network / IBM Developer Skills Network
- **Repository Owner:** [Sairaj213](https://github.com/Sairaj213)
