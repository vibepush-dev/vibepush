# VibePush

**Stop writing YAML. Start shipping.**

MCP-native deployment platform. Any AI agent can deploy, monitor, and fix your apps on your own servers.

[![License: AGPL-3.0](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Status: Validating](https://img.shields.io/badge/Status-Validating%20Idea-yellow.svg)]()

---

> **We're in early validation stage.**
> Star this repo if you want VibePush to exist. Your star = vote that this is worth building.

---

## What is VibePush?

VibePush turns your VPS into an AI-managed deployment platform. Your server speaks **MCP (Model Context Protocol)** — so Claude, GPT, Gemini, or any MCP-compatible AI can:

- **Deploy** your apps from natural language
- **Monitor** logs and metrics
- **Fix** issues automatically

No YAML. No Kubernetes expertise. Just talk to your AI.

```
you: Deploy ./my-app with PostgreSQL
AI:  Building image... Deployed at my-app.example.com

you: Why is it crashing?
AI:  Found OOM error. Increasing memory to 512Mi... Fixed.
```

---

## The Problem

We talked to developers. Here's what they said:

### Kubernetes is hard
> "Managing YAML is a weird Sisyphean job. It is by far my least favourite language."

**70%** of K8s users say complexity is their top challenge. The learning curve feels like scaling Everest.

### Cloud PaaS = Lock-in + Surprise Bills
Heroku outages every other Friday. Vercel surprise bills ($95k for Cara). You don't own your infrastructure.

### Self-hosted tools still need DevOps skills
Coolify, CapRover, Dokku — they give you control, but when things break, you're alone with Stack Overflow.

### Vibe coding deployment gap
Lovable and Bolt generate code, but where do you deploy? Their hosting = lock-in. Your VPS = complexity.
*Shuttle just raised $6M to solve this exact problem.*

---

## Our Solution

| Problem | VibePush |
|---------|----------|
| YAML complexity | AI generates config for you |
| K8s learning curve | Zero knowledge required |
| Cloud lock-in | Your servers, your rules |
| Self-hosted complexity | AI troubleshooting, not Stack Overflow |
| Vibe coding deployment gap | Export code → deploy with one command |

---

## How It Works

```
┌─────────────────┐      MCP       ┌─────────────────┐
│   Any AI Agent  │◄──────────────►│    VibePush     │
│                 │    Protocol    │   MCP Server    │
│  Claude / GPT   │                │                 │
│ Gemini / LLaMA  │                └────────┬────────┘
│    Cursor       │                         │
└─────────────────┘                         ▼
                                  ┌─────────────────┐
                                  │   Your Server   │
                                  │      (K3s)      │
                                  │                 │
                                  │  ┌───────────┐  │
                                  │  │  Your App │  │
                                  │  │  Postgres │  │
                                  │  │   Redis   │  │
                                  │  └───────────┘  │
                                  └─────────────────┘
```

1. **Install VibePush** on your VPS
2. **Connect your AI** via MCP protocol
3. **Talk to deploy** — AI handles Docker, Helm, K3s

---

## Supported AI Agents

VibePush works with **any MCP-compatible AI**:

| Agent | Support |
|-------|---------|
| Claude (Anthropic) | Primary |
| ChatGPT (OpenAI) | Planned |
| Gemini (Google) | Planned |
| LLaMA (Meta) | Planned |
| Cursor | Planned |
| Your custom agent | Planned |

**One protocol. Any AI. Your infrastructure.**

---

## Features (Planned)

- **MCP Protocol Native** — Works with any MCP-compatible AI agent
- **AI Deployment** — Understands your code, builds images, generates Helm charts
- **AI Troubleshooting** — Reads logs, identifies issues, fixes automatically
- **Any Infrastructure** — Hetzner, Contabo, DigitalOcean, bare metal
- **One-Click Databases** — PostgreSQL, MySQL, Redis, MongoDB
- **Auto SSL & Security** — Let's Encrypt, UFW, fail2ban

---

## Start Small, Scale Big

Start with one server. Add more when you need them. No migration required.

```
    Day 1                    Month 3                   Scale
┌─────────────┐          ┌─────────────┐          ┌─────────────┐
│  1 Server   │          │  Control    │          │  Control    │
│ ─────────── │    →     │ ─────────── │    →     │ ─────────── │
│ All-in-One  │          │  Worker 1   │          │  Worker 1   │
│ (apps+dbs)  │          │             │          │  Worker 2   │
│             │          │             │          │  Worker N   │
└─────────────┘          └─────────────┘          └─────────────┘
```

**Example conversation:**

```
# Running low on RAM...
you: My server is getting slow. I have a new VPS at 95.216.x.x
AI:  Adding as worker node... Done.
     Cluster now has 2 nodes, 8GB RAM total.

# Black Friday is coming...
you: Add 3 more servers for the traffic spike
AI:  Adding workers... Done. 5 nodes ready.
     Scaling my-app to 5 replicas across all nodes.
```

**Mix any providers:**
- Hetzner (Germany) + Contabo (Germany) + DigitalOcean (NYC)
- Bare metal + Cloud VPS
- ARM + x86

---

## Project Status

> **Early Stage — Validating the Idea**

We're building this in public. Before writing code, we want to validate that developers actually need this.

### What We Have
- [x] Landing page: [vibepush.dev](https://vibepush.dev)
- [x] Pain points research
- [x] Architecture design
- [ ] MVP implementation

### How You Can Help

| Action | What it means |
|--------|---------------|
| **Star this repo** | "Yes, I want this to exist" |
| **Open an issue** | Share your pain points |
| **Watch** | Get updates on progress |
| **Contribute** | PRs welcome |

---

## Comparison

| Feature | VibePush | Coolify | Railway | Heroku |
|---------|----------|---------|---------|--------|
| AI Deployment | Any MCP AI | — | — | — |
| AI Troubleshooting | Any MCP AI | — | — | — |
| Self-Hosted | Yes | Yes | No | No |
| Your Infrastructure | Yes | Yes | No | No |
| MCP Protocol | Native | — | — | — |
| Multi-Node Scaling | Yes | Partial | — | — |
| No K8s Knowledge | Yes | Partial | Yes | Yes |

---

## Tech Stack (Planned)

| Component | Technology |
|-----------|------------|
| Runtime | K3s (lightweight Kubernetes) |
| Protocol | MCP (Model Context Protocol) |
| Build | Buildpacks / Docker |
| Ingress | Traefik |
| SSL | Let's Encrypt / cert-manager |
| Agent | Go |
| MCP Server | TypeScript |

---

## FAQ

### Why MCP and not REST API?

MCP (Model Context Protocol) is Anthropic's standard for AI-to-tool communication. It's becoming the lingua franca for AI agents. By building MCP-native, VibePush works with any AI that adopts the protocol — not just Claude.

### Why K3s and not Docker Compose?

K3s gives us Kubernetes power (rolling deploys, auto-healing, scaling) without Kubernetes complexity. The AI handles the complexity — you just deploy.

### How is this different from Coolify?

Coolify is UI-first. VibePush is **AI-first**. When your app crashes at 3am, you ask your AI to fix it — not navigate a dashboard.

### Will this work with ChatGPT / Gemini?

Yes, once they support MCP. We're building for the protocol, not a specific AI.

### Can I start with one server and add more later?

Absolutely. This is the expected path:
1. **Day 1**: Single $5 VPS runs everything (control plane + apps + databases)
2. **When you grow**: Add worker nodes with a simple "Add server X.X.X.X" command
3. **Scale**: Mix providers (Hetzner + Contabo + DO), mix architectures (ARM + x86)

No migration, no downtime, no reconfiguration.

---

## Community

- [Website](https://vibepush.dev)
- [GitHub Issues](https://github.com/vibepush-dev/vebepush/issues) — Feedback & feature requests

---

## License

[AGPL-3.0](LICENSE)

Free to use, modify, and distribute. If you run VibePush as a service, you must open-source your modifications.

---

<p align="center">
  <b>Star this repo if you want VibePush to exist.</b>
  <br><br>
  Your star = validation that we should build this.
  <br><br>
  <a href="https://vibepush.dev">vibepush.dev</a>
</p>
