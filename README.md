# Next.js on Azure App Service (Docker)

A containerised **Next.js** application packaged with **Docker** and deployed to **Azure App Service** for Linux containers.

## 🚀 What this project does

Demonstrates the full lifecycle of a Next.js TypeScript app deployed to Azure: local development, Docker packaging, and zero-downtime release on Azure App Service.

## 🧩 Stack

Next.js (React + TypeScript) for the application. Docker for packaging. Azure App Service (Linux containers) for hosting. Azure Container Registry (optional) for image storage.

## 📁 Repository layout

The `nextjs-starter-01-rec-defaults/` folder contains the Next.js application source with default project structure (pages, components, public assets, and configuration).

## ✅ Prerequisites

Node.js 18+ and npm. Docker Desktop. An Azure subscription with permission to create App Service plans and web apps. Azure CLI (`az login`).

## ⚡ Run locally

```bash
cd nextjs-starter-01-rec-defaults
npm install
npm run dev
```

The app will be available at http://localhost:3000.

## 🐳 Build and run with Docker

```bash
docker build -t nextjs-azure-app .
docker run -p 3000:3000 nextjs-azure-app
```

## ☁️ Deploy to Azure App Service

```bash
# 1. Login
az login

# 2. Create resource group
az group create --name nextjs-rg --location eastus

# 3. Create App Service plan (Linux)
az appservice plan create --name nextjs-plan --resource-group nextjs-rg --is-linux --sku B1

# 4. Create web app from container image
az webapp create --resource-group nextjs-rg --plan nextjs-plan --name my-nextjs-app --deployment-container-image-name <registry>/nextjs-azure-app:latest
```

## 📝 Notes

For production, use Azure Container Registry plus continuous deployment from GitHub Actions or Azure DevOps for fully automated releases.

## 📄 License

MIT
