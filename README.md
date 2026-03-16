<div align="center">
  <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExcW1scWswaHg1bW1mcjFtN2pvcDNsZWV6dmJrMDlkbjVhY2Z0Y2ZsMyZlcD12MV9zdGlja2Vyc19zZWFyY2gmY3Q9cw/HQTYdpx1yhxWpugAi2/giphy.gif" width="120" alt="robot"/>

# 🤖 LinkedIn Automation

**Fully automated LinkedIn content engine — powered by AI, zero manual effort**

[![Make.com](https://img.shields.io/badge/Make.com-6D00CC?style=for-the-badge&logo=make&logoColor=white)](https://eu1.make.com/public/shared-scenario/3ZNx5oIbz1W/linked-in-automation)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/anubhav-kumar-srivastava-abb28b239/)
[![Airforce API](https://img.shields.io/badge/Airforce%20API-000000?style=for-the-badge&logo=fly&logoColor=white)](https://api.airforce)
[![NVIDIA](https://img.shields.io/badge/NVIDIA-76B900?style=for-the-badge&logo=nvidia&logoColor=white)](https://build.nvidia.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

> 🚀 **[View Live Make.com Scenario →](https://eu1.make.com/public/shared-scenario/3ZNx5oIbz1W/linked-in-automation)**

</div>

---

## ✨ What it does

This automation runs **every day at 11:00 AM** and posts AI-generated content to LinkedIn — completely hands-free. Different content type every day of the week.

| Day | Post Type | Pipeline |
|-----|-----------|----------|
| 🟣 **Monday** | AI Text Post | Airforce API → Clean → Post |
| 🟣 **Tuesday** | AI Text Post | Airforce API → Clean → Post |
| 🟢 **Wednesday** | AI Image Post | NVIDIA SD → ImgBB → Post |
| 🟢 **Thursday** | AI Image Post | NVIDIA SD → ImgBB → Post |
| 🔴 **Friday** | AI Poll Post | Airforce API → Parser → Post |
| 🔴 **Saturday** | AI Poll Post | Airforce API → Parser → Post |
| 🎬 **Sunday** | AI Video Post | BGM → Freepik → json2video → Post |

---

## 🏗️ Architecture

![Architecture](architecture/linkedIn_automation_architecture.svg)
## ⚡ Tech Stack

<div align="center">

| Platform | Role | Badge |
|----------|------|-------|
| Make.com | Automation engine | [![Make](https://img.shields.io/badge/Make.com-Scenario-6D00CC?style=flat-square&logo=make)](https://make.com) |
| Airforce API | AI text generation | [![Airforce](https://img.shields.io/badge/Airforce%20API-llama--4--maverick-000000?style=flat-square)](https://api.airforce) |
| NVIDIA | Stable Diffusion image gen | [![NVIDIA](https://img.shields.io/badge/NVIDIA-Stable%20Diffusion-76B900?style=flat-square&logo=nvidia)](https://build.nvidia.com) |
| ImgBB | Image hosting | [![ImgBB](https://img.shields.io/badge/ImgBB-Image%20Host-1A73E8?style=flat-square)](https://imgbb.com) |
| Freepik | Video asset gen | [![Freepik](https://img.shields.io/badge/Freepik-Assets-1273EB?style=flat-square)](https://freepik.com) |
| json2video | Video composition | [![json2video](https://img.shields.io/badge/json2video-Video%20API-FF6B35?style=flat-square)](https://json2video.com) |
| LinkedIn API | Publishing | [![LinkedIn](https://img.shields.io/badge/LinkedIn-API-0A66C2?style=flat-square&logo=linkedin)](https://linkedin.com) |

</div>

---

## 🚀 Quick Start

### 1. Import the scenario
```
https://eu1.make.com/public/shared-scenario/3ZNx5oIbz1W/linked-in-automation
```
Open Make.com → New Scenario → Import Blueprint → paste shared link

### 2. Add API keys

```json
{
  "airforce_api_key":    "Bearer sk-air-xxxx  →  panel.api.airforce/dashboard",
  "nvidia_api_key":      "Bearer nvapi-xxxx   →  build.nvidia.com",
  "imgbb_api_key":       "xxxx                →  api.imgbb.com",
  "freepik_api_key":     "Bearer xxxx         →  freepik.com/api",
  "json2video_api_key":  "xxxx                →  json2video.com"
}
```

### 3. Connect LinkedIn
Open any LinkedIn module → **Add connection** → Authorize with your account

### 4. Set router filters

```
formatDate(now; "e") = 1 or 2   →  Text post   (Mon, Tue)
formatDate(now; "e") = 3 or 4   →  Image post  (Wed, Thu)
formatDate(now; "e") = 5 or 6   →  Poll post   (Fri, Sat)
formatDate(now; "e") = 7        →  Video post  (Sun)
```

### 5. Enable schedule
Set to **Daily at 11:00 AM** — done! 🎉

---

## 📁 Project Structure

```
linkedin-automation/
├── README.md
├── .gitignore
├── docs/
│   └── architecture.svg
├── config/
│   ├── router-filters.json
│   ├── linkedin-config.json
│   ├── text-parser-config.json
│   ├── poll-parser-config.json
│   └── api-keys.template.json
├── http-requests/
│   ├── airforce-text.json
│   ├── nvidia-image.json
│   ├── imgbb-upload.json
│   ├── poll-generate.json
│   ├── freepik-assets.json
│   ├── json2video-create.json
│   └── video-url-fetch.json
└── tools/
    ├── set-variable.json
    ├── bgm-selector.json
    └── sleep-config.json
```

---

## 🙏 Acknowledgements

This project wouldn't exist without these amazing platforms and their teams. Huge gratitude to:

| Platform | Why I'm grateful |
|----------|-----------------|
| 💜 **[Make.com](https://make.com)** | For making no-code automation genuinely powerful and accessible. The visual scenario builder is a work of art. |
| ✈️ **[Airforce API](https://api.airforce)** | For providing a fast, reliable, and affordable AI gateway with an incredible model selection. |
| 🟢 **[NVIDIA](https://build.nvidia.com)** | For democratizing access to Stable Diffusion and world-class AI models through their API platform. |
| 📸 **[ImgBB](https://imgbb.com)** | For the simplest and most reliable free image hosting API out there. |
| 🎨 **[Freepik](https://freepik.com)** | For providing powerful AI creative tools that make video generation possible. |
| 🎬 **[json2video](https://json2video.com)** | For making video creation as simple as writing JSON. Truly impressive technology. |
| 💼 **[LinkedIn](https://linkedin.com)** | For providing a robust API that makes programmatic publishing possible. |

> *"What I cannot create, I do not understand."* — Richard Feynman

---

## 📬 Connect with me

<div align="center">

[![LinkedIn](https://img.shields.io/badge/Anubhav%20Kumar%20Srivastava-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/anubhav-kumar-srivastava-abb28b239/)

**Built with ❤️ by [Anubhav Kumar Srivastava](https://www.linkedin.com/in/anubhav-kumar-srivastava-abb28b239/)**

<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExcW1scWswaHg1bW1mcjFtN2pvcDNsZWV6dmJrMDlkbjVhY2Z0Y2ZsMyZlcD12MV9zdGlja2Vyc19zZWFyY2gmY3Q9cw/stdqoZQtv5JVM1mI1j/giphy.gif" width="120" alt="thank you"/>

*If this project helped you, consider giving it a ⭐ on GitHub!*

</div>

---

<div align="center">
  <sub>MIT License © 2025 Anubhav Kumar Srivastava</sub>
</div>
