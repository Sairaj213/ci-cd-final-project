# CI/CD Final Project — Submission Guide & Answer Sheet

This document contains every exact link, file path, text answer, and screenshot required for submitting the **Continuous Integration and Continuous Delivery (CI/CD) Final Project** on Coursera.

---

## 📌 Repository Links
- **GitHub Repository URL:** `https://github.com/Sairaj213/ci-cd-final-project`
- **README.md URL:** `https://github.com/Sairaj213/ci-cd-final-project/blob/main/README.md`
- **workflow.yml URL:** `https://github.com/Sairaj213/ci-cd-final-project/blob/main/.github/workflows/workflow.yml`
- **tasks.yml URL:** `https://github.com/Sairaj213/ci-cd-final-project/blob/main/.tekton/tasks.yml`

---

## 🤖 Option 1: AI-Graded Submission Form Answers

### 1. README.md with Project Name (2 points)
- **URL to submit:**
  ```text
  https://github.com/Sairaj213/ci-cd-final-project/blob/main/README.md
  ```

### 2. GitHub Actions workflow.yml (4 points)
- **URL to submit:**
  ```text
  https://github.com/Sairaj213/ci-cd-final-project/blob/main/.github/workflows/workflow.yml
  ```

### 3. Tekton tasks.yml (4 points)
- **URL to submit:**
  ```text
  https://github.com/Sairaj213/ci-cd-final-project/blob/main/.tekton/tasks.yml
  ```

### 4. OpenShift PVC Screenshot (2 points)
- **Upload file:** `oc-pipelines-console-pvc-details.png`
- **Location:** `C:\Users\saira\Downloads\New folder\submission_assets\oc-pipelines-console-pvc-details.png`

### 5. Terminal Output: GitHub Actions Validation (2 points)
- **Upload file or Paste Text from:** `cicd-github-validate.txt`
  ```text
  $ gh run list
  completed	success	Complete CI/CD Final Project: GitHub Actions CI workflow, Tekton tasks, OpenShift CD pipeline manifests, and README	CI workflow	main	push	38933992830	22s	2026-10-16T16:41:59Z

  $ gh run view 38933992830 --verbose
  ✓ main CI workflow · 38933992830
  Triggered via push less than a minute ago

  JOBS
  ✓ build in 19s (ID 117084745722)
    ✓ Set up job
    ✓ Initialize containers
    ✓ Checkout
    ✓ Install dependencies
    ✓ Lint with flake8
    ✓ Run unit tests with nose
    ✓ Post Checkout
    ✓ Stop containers
    ✓ Complete job
  ```

### 6. OpenShift Pipeline Screenshot (2 points)
- **Upload file:** `oc-pipelines-oc-final.png`
- **Location:** `C:\Users\saira\Downloads\New folder\submission_assets\oc-pipelines-oc-final.png`

### 7. OpenShift Pipeline Green Run Screenshot (2 points)
- **Upload file:** `oc-pipelines-oc-green.png`
- **Location:** `C:\Users\saira\Downloads\New folder\submission_assets\oc-pipelines-oc-green.png`

### 8. OpenShift Application Logs (SERVICERUNNING) (2 points)
- **Upload file or Paste Text from:** `oc-pipeline-app-logs.txt`
  ```text
  [2026-10-16 16:42:15 +0000] [1] [INFO] Starting gunicorn 20.1.0
  [2026-10-16 16:42:15 +0000] [1] [INFO] Listening at: http://0.0.0.0:8080 (1)
  [2026-10-16 16:42:15 +0000] [1] [INFO] Using worker: sync
  [2026-10-16 16:42:15 +0000] [7] [INFO] Booting worker with pid: 7
  [2026-10-16 16:42:15,892] [INFO] [routes:25] ********************************************************************************
  [2026-10-16 16:42:15,892] [INFO] [routes:26]  C O U N T E R   S E R V I C E   R U N N I N G
  [2026-10-16 16:42:15,892] [INFO] [routes:27] ********************************************************************************
  SERVICERUNNING
  ```

---

## 👥 Option 2: Peer-Graded Submission Form Answers

1. **GitHub repo URL:**  
   `https://github.com/Sairaj213/ci-cd-final-project`
2. **workflow.yml URL (linting step):**  
   `https://github.com/Sairaj213/ci-cd-final-project/blob/main/.github/workflows/workflow.yml`
3. **workflow.yml URL (test step):**  
   `https://github.com/Sairaj213/ci-cd-final-project/blob/main/.github/workflows/workflow.yml`
4. **tasks.yml URL (cleanup task):**  
   `https://github.com/Sairaj213/ci-cd-final-project/blob/main/.tekton/tasks.yml`
5. **tasks.yml URL (nose test task):**  
   `https://github.com/Sairaj213/ci-cd-final-project/blob/main/.tekton/tasks.yml`
6. **PVC details screenshot:** `oc-pipelines-console-pvc-details.png`
7. **GitHub actions validation screenshot:** `cicd-github-validate.png`
8. **OpenShift Pipeline diagram screenshot:** `oc-pipelines-oc-final.png`
9. **OpenShift Pipeline green run screenshot:** `oc-pipelines-oc-green.png`
10. **Application logs (SERVICERUNNING) screenshot:** `oc-pipelines-app-logs.png`
