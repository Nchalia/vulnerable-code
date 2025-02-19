****** **Steps to be fix**:******

1. Update Node.js base image to a current LTS version like 18-alpine or 20-alpine as Node.js 14 is outdated or  maybe even unsupported now

2. Remove --unsafe-perm from npm install in Dockerfile because it runs npm with root privileges, which isn't secure

3. For the above issue add a non-root user in the Dockerfile to avoid running as root.

4. Dockerfile copies package*.json but doesn't include a package-lock.json. Without a lock file, npm install might get newer versions with vulnerabilities.

4. Use npm ci instead of npm install in Dockerfile for production builds to respect the package-lock.json.

5. Generate a package-lock.json by running npm install locally and commit it, then copy it into the Docker image.

6. Run npm audit to check for vulnerabilities in dependencies.If there are issues, update the packages (like Express if needed) and regenerate the lock file.

7. Update the app.listen in index.js to use '0.0.0.0' so the app is accessible in the Docker container.

8. Set up automated security scanning in the repo using GitHub Actions with Dependabot or Snyk to automatically detect and fix future vulnerabilities.

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


