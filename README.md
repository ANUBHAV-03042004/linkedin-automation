# LinkedIn Automation

Fully automated LinkedIn content posting system built on [Make.com](https://make.com). Generates and publishes AI-powered text posts, image posts, polls, and video posts on a daily schedule.

> **View the live scenario:** [Open in Make.com](https://eu1.make.com/public/shared-scenario/3ZNx5oIbz1W/linked-in-automation)

---

## Architecture

```
Scheduler (Airforce API — text generation)
    → Text parser (remove \n)
    → Text parser (remove ")
    → Text parser (remove ')
    → Router
        ├── Mon + Tue  → LinkedIn text post
        ├── Wed + Thu  → NVIDIA Stable Diffusion → ImgBB → LinkedIn image post
        ├── Fri + Sat  → HTTP POST (poll gen) → LinkedIn poll post
        └── Sunday     → Tools (BGM) → Freepik + json2video → Sleep → HTTP GET → LinkedIn video post
```

---

## Weekly Schedule

| Day | Post Type | APIs Used |
|---|---|---|
| Monday | AI text post | Airforce API |
| Tuesday | AI text post | Airforce API |
| Wednesday | AI image post | NVIDIA Stable Diffusion, ImgBB |
| Thursday | AI image post | NVIDIA Stable Diffusion, ImgBB |
| Friday | AI poll post | Airforce API |
| Saturday | AI poll post | Airforce API |
| Sunday | AI video post | Freepik, json2video |

---

## APIs Used

| Service | Purpose | Method |
|---|---|---|
| [Airforce API](https://api.airforce) | Generate LinkedIn post text | POST |
| [NVIDIA Stable Diffusion](https://integrate.api.nvidia.com) | Generate images | POST |
| [ImgBB](https://api.imgbb.com) | Host generated images | POST |
| [Freepik](https://api.freepik.com) | Generate video assets | POST |
| [json2video](https://api.json2video.com) | Compose video | POST |
| [LinkedIn API](https://api.linkedin.com) | Publish posts | POST |

---

## Project Structure

```
linkedin-automation/
├── README.md
├── docs/
│   └── architecture.svg
├── config/
│   ├── router-filters.json
│   ├── linkedin-config.json
│   └── text-parser-config.json
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

## Setup Guide

### 1. Import scenario
1. Go to [make.com](https://make.com)
2. Create a new scenario
3. Click 3 dots → Import blueprint
4. Use the shared link: https://eu1.make.com/public/shared-scenario/3ZNx5oIbz1W/linked-in-automation

### 2. Add API keys

| Module | Header | Source |
|---|---|---|
| HTTP 3 — Airforce | `Authorization: Bearer YOUR_KEY` | [panel.api.airforce](https://panel.api.airforce/dashboard/) |
| HTTP 19 — NVIDIA | `Authorization: Bearer YOUR_KEY` | [build.nvidia.com](https://build.nvidia.com) |
| HTTP 27 — ImgBB | Query param `key` | [api.imgbb.com](https://api.imgbb.com) |
| HTTP 32 — Poll | `Authorization: Bearer YOUR_KEY` | Same as Airforce |
| Freepik | `Authorization: Bearer YOUR_KEY` | [freepik.com/api](https://www.freepik.com/api) |
| json2video | `x-api-key: YOUR_KEY` | [json2video.com](https://json2video.com) |

### 3. Connect LinkedIn
Open any LinkedIn module → Add connection → Authorize.

### 4. Router filter conditions

| Route | Filter | Value |
|---|---|---|
| Text post | `{{formatDate(now; "e")}}` equal to | `1` or `2` |
| Image post | `{{formatDate(now; "e")}}` equal to | `3` or `4` |
| Poll post | `{{formatDate(now; "e")}}` equal to | `5` or `6` |
| Video post | `{{formatDate(now; "e")}}` equal to | `7` |

### 5. Enable schedule
Set to **Daily at 11:00 AM**.

---

## License

MIT
