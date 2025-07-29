# 🤖 Allora Network SDK – Smart Agent Development Kit

This guide walks you through developing, testing, and deploying **Smart Agents** using the Allora Smart Agent SDK. Smart Agents autonomously interact with the decentralized **Allora Network**, making real-time decisions, adapting models, and publishing signals.

---

## 🔧 Prerequisites

- ✅ Ubuntu 20.04 or later
- ✅ Python 3.11
- ✅ Go 1.22+
- ✅ Docker

---

## ⚙️ Installation & Setup

### 1. Install Core Tools

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install git curl docker.io -y

2. Install Go

curl -OL https://go.dev/dl/go1.22.4.linux-amd64.tar.gz
sudo tar -C /usr/local -xvf go1.22.4.linux-amd64.tar.gz
export PATH=$PATH:/usr/local/go/bin
go version

3. Clone Allora SDK

git clone https://github.com/allora-network/allora-smart-agent-sdk.git
cd allora-smart-agent-sdk

🧪 Environment Setup
Install Miniconda & Create Environment
bash
Copy code
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda.sh
bash miniconda.sh -b -p $HOME/miniconda
export PATH="$HOME/miniconda/bin:$PATH"
conda init
source ~/.bashrc
conda create -n smartagent python=3.11 -y
conda activate smartagent
