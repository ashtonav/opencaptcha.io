---
sidebar_position: 3
---

# Self-Hosting

Before you begin, clone or download the [OpenCaptcha repository](https://github.com/ashtonav/opencaptcha). Afterwards, choose one of the options below to host OpenCaptcha.

---

## Option 1: Using Docker (recommended for self-hosting)

### Requirements
- Docker

### How to Run
1. From the root folder of the project, run the following commands:
   ```bash
   docker build -t opencaptcha -f ./src/Captcha.WebApi/Dockerfile .
   docker run -it -p 5280:8080 opencaptcha
   ```
2. The API can be accessed at [http://localhost:5280](http://localhost:5280).

## Option 2: Using Visual Studio (recommended for development purposes)

### Requirements
- Visual Studio 2022
    - With ASP.NET and web development installed from the Visual Studio Installer
- .NET 9 SDK

### How to Run
1. Open the solution in Visual Studio 2022.
2. Build and launch the Captcha.WebApi project.
3. The API can be accessed at [https://localhost:5280](https://localhost:5280).
---
