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

- **Gitleaks** - Is a binary that detects secrets in your repo
    - You can Run an action against your repo in pull request to scan your repo for secrets
    - **.gitleaks.toml - here you can define custom rules**
 
- [[rules]]
id = "aws-test-key"
description = "Test AWS API Key"
regex = '''AKIA[0-9A-Z]{16}'''
secretGroup = 0
