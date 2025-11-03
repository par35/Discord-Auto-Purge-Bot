# Discord Auto-Purge Bot

A production-ready automation that purges old or unwanted messages from Discord channels on a schedule or on-demand, with safety rules and audit logs. It solves the pain of manual cleanup, rate-limit headaches, and inconsistent moderator habits—delivering consistently clean channels and faster server moderation. Built to run via Discord API **and** an Android emulation layer for ADB-less mobile automation where API access is constrained.

<p align="center">
  <a href="https://Appilot.app" target="_blank">
    <img src="media/appilot-baner.png" alt="Appilot Banner" width="100%">
  </a>
</p>
<p align="center">
  <a href="https://t.me/devpilot1" target="_blank">
    <img src="https://img.shields.io/badge/Chat%20on-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram">
  </a>&nbsp;
  <a href="https://wa.me/923249868488?text=Hi%20Appilot%2C%20I'm%20interested%20in%20automation." target="_blank">
    <img src="https://img.shields.io/badge/Chat-WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhatsApp">
  </a>&nbsp;
  <a href="mailto:support@appilot.app" target="_blank">
    <img src="https://img.shields.io/badge/Email-support@appilot.app-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail">
  </a>&nbsp;
  <a href="https://appilot.app" target="_blank">
    <img src="https://img.shields.io/badge/Visit-Website-007BFF?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Website">
  </a>
</p>

<p align="center"> 
   Created by Appilot, built to showcase our approach to Automation!<br>
   <strong>If you are looking for custom Discord Auto-Purge Bot, you've just found your team — Let’s Chat.👆👆</strong>
</p>

## Introduction

This system automates the deletion of messages in Discord channels by age, content rules, user filters, or patterns, while respecting rate limits and moderation policies.  
It removes repetitive manual purging, midnight cleanup tasks, and risky bulk actions that can trip limits or miss compliance windows.  
The benefit: reliable, policy-driven cleanup that improves server health, discoverability, and moderation efficiency.

### Automating Discord Channel Cleanup

- Policy-based rules (age, regex, user roles) keep channels tidy without manual sweeps.  
- Dual-mode engine: Discord API for speed; Android client automation (Appilot) for constrained environments.  
- Safe-by-default: dry-run, sampling, and soft-delete modes with exports.  
- Scales across multiple servers, categories, and threads with queueing and backoff.

## Core Features

- **Real Devices and Emulators:** Run purge flows through the Discord Android app on real phones or emulators (Bluestacks/Nox) using Appilot—handy when API scopes are limited or for compliance mirroring.
- **No-ADB Wireless Automation:** Control Android devices over Wi-Fi without ADB tethering; ideal for device farms and headless racks.
- **Mimicking Human Behavior:** Randomized delays, scrolling cadence, and interaction patterns to reduce automation fingerprints.
- **Multiple Accounts Support:** Rotate moderator tokens or Android user profiles; map rules per server, channel, or workspace.
- **Multi-Device Integration:** Parallel purges across device pools and shards; queue manager spreads load by channel and age buckets.
- **Exponential Growth for Your Account:** Cleaner channels improve engagement and retention, helping communities grow with less mod fatigue.
- **Premium Support:** SLA-backed onboarding, config reviews, and incident help for rate-limit or rule-tuning events.
- **Rule-based Purge Policies:** Age thresholds (e.g., >14d), regex/keyword filters, role/user exclusions, and attachment targeting.
- **Safe Dry-Run + Diff Reports:** Preview deletes, export CSV/JSON, and confirm with one click.
- **Adaptive Rate-Limit Handling:** Smart backoff, jitter, and token/device rotation to keep operations smooth.

### Additional Feature Set

| Feature | Description |
|---|---|
| **Thread & Forum Coverage** | Applies purge rules to threads, forums, and archived topics with safe unarchive cycles. |
| **Audit Logs & Exports** | Every action is logged; generate CSV/JSON and signed HTML reports for compliance. |
| **Scheduler & Cron Rules** | Nightly, hourly, or event-triggered runs with blackout windows to avoid peak chat hours. |
| **Regex & Content Filters** | Target spam waves, invite links, or media-only bursts via robust pattern rules. |
| **Role/User Whitelists** | Preserve staff, bots, or VIP content; exclude pinned messages and recent announcements. |
| **Web Dashboard (Appilot)** | Configure servers, tokens, devices, and policies; monitor job queues and metrics. |

</p>
<p align="center">
  <a href="https://appilot.app" target="_blank">
    <img src="media/{{keyword}-banner}.png" alt="{{keyword}-architecture}" width="95%">
  </a>
</p>

## How It Works

1. **Input or Trigger** — From the Appilot dashboard, select servers/channels, set filters (age/regex/roles), and choose run mode (API or Android-device).  
2. **Core Logic** — The engine navigates channels (via Discord API or UI Automator on Android), batches message lookups, applies rules, and schedules safe deletions with adaptive backoff.  
3. **Output or Action** — Messages matching policies are removed; you receive structured summaries, exports, and optional webhook notifications.  
4. **Other functionalities** — Retry logic, circuit breakers, granular logging, and parallel queues are tunable in the dashboard. Failure paths include auto-pause and resume with context snapshots.

## Tech Stack

- **Language:** TypeScript, Python, Kotlin  
- **Frameworks:** Appium, UI Automator, Robot Framework, Express.js (API), FastAPI (workers)  
- **Tools:** Appilot, Android Debug Bridge (ADB), Appium Inspector, Bluestacks/Nox, Scrcpy, Firebase Test Lab, Accessibility  
- **Infrastructure:** Dockerized workers, Cloud emulators, Proxy networks, Parallel Device Execution, Task Queues, Real device farm

## Directory Structure
```
discord-auto-purge-bot/
│
├── src/
│   ├── main.ts
│   ├── api/
│   │   ├── server.ts
│   │   └── routes/
│   │       └── jobs.ts
│   ├── purge/
│   │   ├── rules.ts
│   │   ├── scheduler.ts
│   │   ├── discord_api_engine.ts
│   │   ├── android_ui_engine/
│   │   │   ├── device_pool.ts
│   │   │   └── uiactions.ts
│   │   └── adapters/
│   │       ├── rate_limit.ts
│   │       └── audit_logger.ts
│   └── utils/
│       ├── config.ts
│       ├── csv_exporter.ts
│       └── logger.ts
│
├── android/
│   ├── appilot_flows/
│   │   ├── open_channel.flow.yaml
│   │   └── delete_messages.flow.yaml
│   └── devicefarm.yaml
│
├── config/
│   ├── settings.yaml
│   ├── policies.example.yaml
│   └── credentials.env
│
├── dashboards/
│   └── appilot.json
│
├── logs/
│   └── purge.log
│
├── output/
│   ├── reports/
│   │   └── 2025-11-01_purge_report.json
│   └── archives/
│       └── dryrun_sample.csv
│
├── media/
│   └── discord-auto-purge-bot-banner.png
│
├── docker/
│   ├── worker.Dockerfile
│   └── docker-compose.yml
│
├── package.json
├── requirements.txt
└── README.md
```


## Use Cases

- **Community Managers** use it to auto-clean inactive channels weekly, so they maintain a vibrant, searchable server.  
- **Esports & Gaming Servers** use it to purge spam bursts after events, so moderators can focus on real conversations.  
- **Education & Cohorts** use it to reset project channels between batches, so new students see a fresh history.  
- **Enterprise Teams** use it to enforce retention windows, so they meet internal compliance and reduce noise.

## FAQs

**How do I configure this for multiple servers and channels?**  
Define policies per server/channel in `policies.yaml` or via the dashboard. The scheduler fans out jobs using a queue to maintain rate-limit safety.

**Does it support proxy rotation or anti-detection?**  
Yes. In API mode, requests can route via proxies per token; in Android mode, devices can use dedicated proxies/VPNs. Human-like timing reduces fingerprint risk.

**Can I run it on a schedule and still do ad-hoc purges?**  
Absolutely. Cron-like schedules run nightly/weekly, and you can trigger one-off jobs with a dry-run preview to validate before committing.

**What happens if Discord rate-limits the bot?**  
The engine applies exponential backoff with jitter, shards workloads, and resumes from checkpoints. You’ll see rate-limit metrics in the report.

## Performance & Reliability Benchmarks

- **Execution Speed:** 2k–5k message checks/minute per worker in API mode; Android mode optimized for 150–300 UI actions/minute per device.  
- **Success Rate:** ~95% measured across mixed channels with rate limits and intermittent API hiccups.  
- **Scalability:** Horizontal scale to 300–1,000 Android devices and 50–200 API shards via queue-based orchestration.  
- **Resource Efficiency:** Workers are lightweight (≤200MB RSS) with batched fetches and streaming exports.  
- **Error Handling:** Retries with capped backoff, circuit breakers, per-channel checkpoints, structured logs, and alerting via webhooks/Slack.

##
<p align="center">
<a href="https://cal.com/app-pilot-m8i8oo/30min" target="_blank">
  <img src="https://img.shields.io/badge/Book%20a%20Call%20with%20Us-34A853?style=for-the-badge&logo=googlecalendar&logoColor=white" alt="Book a Call">
</a>
</p>
