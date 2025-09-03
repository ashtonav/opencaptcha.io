---
sidebar_position: 2
---

# Uptime & Availability

## Where is OpenCaptcha hosted?
OpenCaptcha (`api.opencaptcha.io`) is hosted in Seattle, Washington (United States) on Microsoft Azure Container Apps using Linux containers.

## Can I expect it to be always available?
We strive to maintain **99.95% availability**, in line with the [Azure Container Apps SLA](https://www.azure.cn/en-us/support/sla/container-apps/v1_0/). However, the API is provided **as-is**, and there is no formal guarantee of uninterrupted service.

## Can I use it for production purposes?
Absolutely! You are free to use `api.opencaptcha.io` in your production environment. There are no rate limits. However, we recommend [Self-Hosting](self-hosting) for mission-critical use cases. This approach ensures you’re not dependent on us, giving you complete control over uptime and the underlying infrastructure.
