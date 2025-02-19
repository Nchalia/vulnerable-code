**Secure Node.js Application**
🌟 Features
Simple web application using Express.js
Docker container packaging
Automated security scanning system
Updated with latest security patches

🔒 **Security Features**
Non-root User: Docker container runs as non-root use
Updated Base Image: Node.js 20 LTS (Alpine Linux)
Automated Scanning:
Package audit with npm audit
Docker image scan with Trivy
Secure dependency installation (npm ci)
Automatic security updates (Dependabot)

🚀 **Installation**
# Clone repository
git clone https://github.com/Nchalia/vulnerable-code.git
cd vulnerable-code
# Install dependencies
npm install

# Build Docker image
docker build -t secure-app .

# Run container
docker run -p 3000:3000 --rm secure-app

🤖 **Automation System**
Dependabot: Daily security update checks
GitHub Actions:
Security scans on every push/PR
npm audit and Trivy scans


