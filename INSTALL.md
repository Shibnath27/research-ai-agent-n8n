# ⚡ Install n8n on Proxmox (with Helper Script)

This guide explains how to install **n8n** inside **Proxmox VE** using the official [Proxmox Helper-Scripts](https://community-scripts.github.io/ProxmoxVE/scripts?id=n8n).  
It uses an **LXC container** with Docker to run n8n.

---

## 📌 1. Requirements
- Proxmox VE (7.x or 8.x)
- Internet access on your Proxmox node
- At least **2 CPU / 2 GB RAM / 10 GB disk**

---

## 📌 2. One-Line Install

Run this command in your **Proxmox Shell** (not inside a VM/LXC):

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/community-scripts/ProxmoxVE/main/ct/n8n.sh)"
