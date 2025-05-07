Full DevSecOps Project:

<img width="861" alt="Screenshot 2025-05-07 at 12 24 54 PM" src="https://github.com/user-attachments/assets/aa00e52e-153e-4fdd-b180-1d7a029ae696" />

This project includes all security best practices in the SDLC. Security tools that we are going to use in this project are:
Gitleaks (SAST, Credential scanning)
Sonarqube (SAST)
Owasp Zap (DAST)
Owasp Dependancy (Scan dependancies)
Trivy (Scan Docker Images)

CI/CD - Github actions
CSP - AWS
Containerization - Docker, k8s
Notification - Email, slack

This application is vulneralble by intent, to make sure our scanning is working properly. 

Lets get started. First make sure you have git repo. In the repo create a file called .github/workflows/gitleaks.yml:

name: Gitleaks Full Repo Scan

on:
  pull_request:
    branches: [main]

jobs:
 gitleaks-scan:
    
    
    name: Gitleaks Full Commit History Scan
    runs-on: ubuntu-latest

    steps:
      - name: Checkout full history
        uses: actions/checkout@v3
        with:
          fetch-depth: 0  # Fetch full commit history

      - name: Run Gitleaks
        uses: gitleaks/gitleaks-action@v2
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          GITLEAKS_RUN_ARGS: detect --source=. --verbose --report-format sarif --exit-code 1

