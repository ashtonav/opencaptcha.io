---
sidebar_position: 6
---

# Architecture

Below are diagrams illustrating how **OpenCaptcha** processes incoming requests and how it can be deployed via a CI/CD pipeline to Azure Container Instances.

---

## Request Flow Diagram

```
┌────────────────────┐
│   Client Request   │
│  (via HTTPS)       │
└─────────┬──────────┘
          │
          v
┌─────────────────────────┐
│  Captcha.WebApi         │
│  (Controllers, routing) │
└─────────┬───────────────┘
          │
          v
┌─────────────────────────┐
│  Captcha.Core           │
│  (Image generation)     │
└─────────┬───────────────┘
          │
          v
┌──────────────────────────┐
│  Generated Image (JPEG)  │
└──────────────────────────┘
```

1. **Client** sends an HTTPS request to the OpenCaptcha endpoint (`api.opencaptcha.io`).
2. **Captcha.WebApi** receives and processes the request (`POST /captcha`).
3. **Captcha.Core** generates the CAPTCHA image based on the requested parameters (text, dimensions, difficulty).
4. A **JPEG** image is returned to the client.

---

## Deployment Diagram

```
     +---------------------+
     |  GitHub Repository  |
     +----------+----------+
                |
                | (Push code to main branch)
                v
     +--------------------------------------+
     |    CI/CD Pipeline (GitHub Actions)   |
     |  - .NET build & tests                |
     |  - Docker build                      |
     +-------------+------------------------+
                   | (Push image)
                   v
     +----------------------------------+
     |  Azure Container Registry (ACR)  |
     +----------------------------------+
                   | (Pull image)
                   v
+-----------------------------------------+
|  Azure Container Apps                   |
+-----------------------------------------+
                   |
                   v
        +---------------------------------------+
        |  Publicly Accessible                  |
        |  via api.opencaptcha.io               |
        +---------------------------------------+
```

1. **Developers** push code changes or open pull requests on GitHub.
2. **GitHub Actions** (CI/CD service) automatically runs tests and builds a Docker image.
3. The image is **pushed** to **Azure Container Registry (ACR)**.
4. **Azure Container Apps** **pulls** the Docker image from ACR.
5. The container is **deployed** and made publicly available at `api.opencaptcha.io`.

---
