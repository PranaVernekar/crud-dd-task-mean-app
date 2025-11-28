# CRUD MEAN App - Full Deployment

## 🚀 Project Overview
This project demonstrates a complete end-to-end deployment of a MEAN stack CRUD application using Docker, Docker Hub, Nginx Reverse Proxy, GitHub Actions CI/CD pipeline, and deployment on an AWS EC2 Ubuntu server.

## 🗂️ Tech Stack
• MongoDB • Express.js • Angular • Node.js  
• Docker • Nginx • GitHub Actions • AWS EC2

## 📦 Features
🔹 Add / Edit / Delete / View Users

🔹 Fully Dockerized frontend + backend + database

🔹 Automated Deployment via GitHub Actions

🔹 Secured Nginx Reverse Proxy routing everything via port 80

## 🔧 Folder Structure
(frontend, backend, docker-compose…)

## Docker Setup
🔹 Build & Push Backend
docker build -t <dockerhub-username>/mean-backend ./backend
docker push <dockerhub-username>/mean-backend

🔹 Build & Push Frontend
docker build -t <dockerhub-username>/mean-frontend ./frontend
docker push <dockerhub-username>/mean-frontend

## Deployment on AWS EC2

Launch a Ubuntu EC2 instance → Install Docker & Docker Compose → Clone repo:

git clone https://github.com/<your-username>/crud-dd-task-mean-app.git
cd crud-dd-task-mean-app
docker compose up -d


## Nginx Reverse Proxy

Location: /etc/nginx/sites-available/default

server {
    listen 80;

    location / {
        proxy_pass http://frontend:80;
    }

    location /api/ {
        proxy_pass http://backend:3000/;
    }
}


Restart:

sudo systemctl restart nginx
sudo systemctl status nginx

## CI/CD – GitHub Actions Workflow

Every push to main triggers:

✔ Build → ✔ Push Docker Images → ✔ SSH Deploy

File: .github/workflows/ci-cd.yml

Secrets Used:

DOCKERHUB_USERNAME	Docker Hub login
DOCKERHUB_TOKEN	Access token
SERVER_IP	EC2 Public IP
SERVER_SSH_KEY	Private SSH Key contents

Pipeline = fully automated deployment.

## 📸 Screenshots
CI/CD configuration and execution.
<img width="981" height="354" alt="Screenshot 2025-11-28 174456" src="https://github.com/user-attachments/assets/43238048-03f3-42de-b3f9-14b75f776b3b" />
<img width="1913" height="967" alt="Screenshot 2025-11-28 173413" src="https://github.com/user-attachments/assets/cd8cb405-ded3-4262-b711-5485a4aabf82" />

Docker image build and push process.
<img width="1919" height="968" alt="Screenshot 2025-11-28 174842" src="https://github.com/user-attachments/assets/83fdfb50-b7da-4189-a110-61c44a3052bf" />
<img width="1916" height="976" alt="Screenshot 2025-11-28 173818" src="https://github.com/user-attachments/assets/99225aac-ec06-4be4-9bf5-097f1f1e8891" />

Application deployment and working UI.
<img width="1917" height="965" alt="Screenshot 2025-11-28 150329" src="https://github.com/user-attachments/assets/c644110a-0845-4d22-aeb9-af0b9a1d03ad" />
<img width="1918" height="972" alt="Screenshot 2025-11-28 150506" src="https://github.com/user-attachments/assets/56a7e4cb-8bf7-4c99-a8a2-de123d13e5d4" />
<img width="1919" height="974" alt="Screenshot 2025-11-28 150516" src="https://github.com/user-attachments/assets/a82feaa2-3189-40df-898d-8b9be2b79945" />
<img width="1913" height="975" alt="Screenshot 2025-11-28 151038" src="https://github.com/user-attachments/assets/1fe907ba-b18b-4056-a52c-07d0438019e6" />

Nginx setup and infrastructure details.
<img width="1917" height="965" alt="Screenshot 2025-11-28 150329" src="https://github.com/user-attachments/assets/3a05e44e-7d92-44f7-919f-d6b7ee9222f6" />
<img width="1917" height="972" alt="Screenshot 2025-11-28 153231" src="https://github.com/user-attachments/assets/9b168f75-2cf0-4656-bfcb-448170911d85" />
<img width="1918" height="968" alt="Screenshot 2025-11-28 153549" src="https://github.com/user-attachments/assets/8ab7a30c-c297-4cab-8af9-c64a79f6fea6" />
<img width="1919" height="750" alt="Screenshot 2025-11-28 174151" src="https://github.com/user-attachments/assets/86e0a9d8-6bc1-4d82-8b20-ce7b199605da" />





