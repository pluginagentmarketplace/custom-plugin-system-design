<div align="center">

<!-- Animated Typing Banner -->
<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=28&duration=3000&pause=1000&color=2E9EF7&center=true&vCenter=true&multiline=true&repeat=true&width=600&height=100&lines=System+Design+Assistant;7+Agents+%7C+7+Skills;Claude+Code+Plugin" alt="System Design Assistant" />

<br/>

<!-- Badge Row 1: Status Badges -->
[![Version](https://img.shields.io/badge/Version-1.0.0-blue?style=for-the-badge)](https://github.com/pluginagentmarketplace/custom-plugin-system-design/releases)
[![License](https://img.shields.io/badge/License-Custom-yellow?style=for-the-badge)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Production-brightgreen?style=for-the-badge)](#)
[![SASMP](https://img.shields.io/badge/SASMP-v1.3.0-blueviolet?style=for-the-badge)](#)

<!-- Badge Row 2: Content Badges -->
[![Agents](https://img.shields.io/badge/Agents-7-orange?style=flat-square&logo=robot)](#-agents)
[![Skills](https://img.shields.io/badge/Skills-7-purple?style=flat-square&logo=lightning)](#-skills)
[![Commands](https://img.shields.io/badge/Commands-4-green?style=flat-square&logo=terminal)](#-commands)

<br/>

<!-- Quick CTA Row -->
[📦 **Install Now**](#-quick-start) · [🤖 **Explore Agents**](#-agents) · [📖 **Documentation**](#-documentation) · [⭐ **Star this repo**](https://github.com/pluginagentmarketplace/custom-plugin-system-design)

---

### What is this?

> **System Design Assistant** is a Claude Code plugin with **7 agents** and **7 skills** for system design development.

</div>

---

## 📑 Table of Contents

<details>
<summary>Click to expand</summary>

- [Quick Start](#-quick-start)
- [Features](#-features)
- [Agents](#-agents)
- [Skills](#-skills)
- [Commands](#-commands)
- [Documentation](#-documentation)
- [Contributing](#-contributing)
- [License](#-license)

</details>

---

## 🚀 Quick Start

### Prerequisites

- Claude Code CLI v2.0.27+
- Active Claude subscription

### Installation (Choose One)

<details open>
<summary><strong>Option 1: From Marketplace (Recommended)</strong></summary>

```bash
# Step 1️⃣ Add the marketplace
/plugin marketplace add pluginagentmarketplace/custom-plugin-system-design

# Step 2️⃣ Install the plugin
/plugin install custom-plugin-system-design@pluginagentmarketplace-system-design

# Step 3️⃣ Restart Claude Code
# Close and reopen your terminal/IDE
```

</details>

<details>
<summary><strong>Option 2: Local Installation</strong></summary>

```bash
# Clone the repository
git clone https://github.com/pluginagentmarketplace/custom-plugin-system-design.git
cd custom-plugin-system-design

# Load locally
/plugin load .

# Restart Claude Code
```

</details>

### ✅ Verify Installation

After restart, you should see these agents:

```
custom-plugin-system-design:01-frontend-web-development
custom-plugin-system-design:05-devops-cloud-infrastructure
custom-plugin-system-design:02-backend-server-development
custom-plugin-system-design:06-database-system-design
custom-plugin-system-design:07-architecture-leadership-security
... and 2 more
```

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🤖 **7 Agents** | Specialized AI agents for system design tasks |
| 🛠️ **7 Skills** | Reusable capabilities with Golden Format |
| ⌨️ **4 Commands** | Quick slash commands |
| 🔄 **SASMP v1.3.0** | Full protocol compliance |

---

## 🤖 Agents

### 7 Specialized Agents

| # | Agent | Purpose |
|---|-------|---------|
| 1 | **01-frontend-web-development** | Expert Frontend & Web Development specialist. Guides learner |
| 2 | **05-devops-cloud-infrastructure** | Expert DevOps & Cloud Infrastructure specialist. Guides thro |
| 3 | **02-backend-server-development** | Expert Backend & Server Development specialist. Guides throu |
| 4 | **06-database-system-design** | Expert Database & System Design specialist. Guides through r |
| 5 | **07-architecture-leadership-security** | Expert Architecture, Leadership & Security specialist. Guide |
| 6 | **03-mobile-development** | Expert Mobile Development specialist. Guides through native  |
| 7 | **04-data-science-ai** | Expert Data Science & AI specialist. Guides through Machine  |

---

## 🛠️ Skills

### Available Skills

| Skill | Description | Invoke |
|-------|-------------|--------|
| `cloud-devops` | Master cloud platforms and DevOps tools including Docker, Ku | `Skill("custom-plugin-system-design:cloud-devops")` |
| `mobile-platforms` | Master mobile development platforms including Android, iOS,  | `Skill("custom-plugin-system-design:mobile-platforms")` |
| `database-technologies` | Master database technologies including SQL, PostgreSQL, Mong | `Skill("custom-plugin-system-design:database-technologies")` |
| `frontend-technologies` | Master modern frontend technologies including React, Vue, An | `Skill("custom-plugin-system-design:frontend-technologies")` |
| `system-design` | Master system design principles for building scalable, relia | `Skill("custom-plugin-system-design:system-design")` |
| `backend-frameworks` | Master backend frameworks and languages including Node.js, P | `Skill("custom-plugin-system-design:backend-frameworks")` |
| `leadership-management` | Master engineering leadership, team management, product stra | `Skill("custom-plugin-system-design:leadership-management")` |
| `ai-ml-tools` | Master AI and machine learning tools including TensorFlow, P | `Skill("custom-plugin-system-design:ai-ml-tools")` |
| `security-compliance` | Master security principles, cryptography, compliance framewo | `Skill("custom-plugin-system-design:security-compliance")` |

---

## ⌨️ Commands

| Command | Description |
|---------|-------------|
| `/skill-assessment` | assessment |
| `/explore-agents` | agents |
| `/learn-roadmap` | roadmap |
| `/roadmap-search` | search |

---

## 📚 Documentation

| Document | Description |
|----------|-------------|
| [CHANGELOG.md](CHANGELOG.md) | Version history |
| [CONTRIBUTING.md](CONTRIBUTING.md) | How to contribute |
| [LICENSE](LICENSE) | License information |

---

## 📁 Project Structure

<details>
<summary>Click to expand</summary>

```
custom-plugin-system-design/
├── 📁 .claude-plugin/
│   ├── plugin.json
│   └── marketplace.json
├── 📁 agents/              # 7 agents
├── 📁 skills/              # 7 skills (Golden Format)
├── 📁 commands/            # 4 commands
├── 📁 hooks/
├── 📄 README.md
├── 📄 CHANGELOG.md
└── 📄 LICENSE
```

</details>

---

## 📅 Metadata

| Field | Value |
|-------|-------|
| **Version** | 1.0.0 |
| **Last Updated** | 2025-12-29 |
| **Status** | Production Ready |
| **SASMP** | v1.3.0 |
| **Agents** | 7 |
| **Skills** | 7 |
| **Commands** | 4 |

---

## 🤝 Contributing

Contributions are welcome! Please read our [Contributing Guide](CONTRIBUTING.md).

1. Fork the repository
2. Create your feature branch
3. Follow the Golden Format for new skills
4. Submit a pull request

---

## ⚠️ Security

> **Important:** This repository contains third-party code and dependencies.
>
> - ✅ Always review code before using in production
> - ✅ Check dependencies for known vulnerabilities
> - ✅ Follow security best practices
> - ✅ Report security issues privately via [Issues](../../issues)

---

## 📝 License

Copyright © 2025 **Dr. Umit Kacar** & **Muhsin Elcicek**

Custom License - See [LICENSE](LICENSE) for details.

---

## 👥 Contributors

<table>
<tr>
<td align="center">
<strong>Dr. Umit Kacar</strong><br/>
Senior AI Researcher & Engineer
</td>
<td align="center">
<strong>Muhsin Elcicek</strong><br/>
Senior Software Architect
</td>
</tr>
</table>

---

<div align="center">

**Made with ❤️ for the Claude Code Community**

[![GitHub](https://img.shields.io/badge/GitHub-pluginagentmarketplace-black?style=for-the-badge&logo=github)](https://github.com/pluginagentmarketplace)

</div>
