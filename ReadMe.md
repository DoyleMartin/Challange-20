# 📦 Full-Stack App CI/CD Deployment

This project demonstrates the setup of a CI/CD pipeline for a full-stack MERN application. The app itself was provided as starter code. My task was to create a GitHub repository, configure automated testing and deployment, and ensure reliable and secure delivery of new features through GitHub Actions and Render.

---

## 🌍 Live App

**🔗 [Live Site on Render](https://challange-20.onrender.com)**  

---

## 🛠 Tech Stack

- **Frontend**: React  
- **Backend**: Node.js, Express  
- **Database**: MongoDB Atlas  
- **CI/CD**: GitHub Actions  
- **Testing**: Cypress  
- **Deployment**: Render  

---

## ✅ Features

- Continuous Integration via GitHub Actions
- Cypress component tests on all Pull Requests to `develop`
- Deployment to Render triggered on pushes to `main`
- Branch protection rules requiring tests to pass before merge
- Secure handling of environment variables with GitHub Secrets and Render

---


---

## 🧪 Cypress Testing Workflow

GitHub Actions runs Cypress tests on every Pull Request targeting `develop`.

### `.github/workflows/test.yml`

```yaml
name: Run Cypress Component Tests

on:
  pull_request:
    branches:
      - develop

jobs:
  cypress-run:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Install dependencies
        run: |
          npm install
          cd client
          npm install

      - name: Run Cypress tests
        run: npx cypress run


