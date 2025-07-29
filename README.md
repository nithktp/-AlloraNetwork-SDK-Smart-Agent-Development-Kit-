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

```
sudo apt update && sudo apt upgrade -y
sudo apt install git curl docker.io -y
```


### 2. Install Go

```bash
curl -OL https://go.dev/dl/go1.22.4.linux-amd64.tar.gz
sudo tar -C /usr/local -xvf go1.22.4.linux-amd64.tar.gz
export PATH=$PATH:/usr/local/go/bin
go version
```

💡 To persist Go path:
```bash
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc
source ~/.bashrc
```
### 3: Clone Allora SDK
```bash
git clone https://github.com/allora-network/allora-smart-agent-sdk.git
cd allora-smart-agent-sdk
```
## ⚙️ Environment Setup

### 1: Install Miniconda & Create Python Environment
```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda.sh
bash miniconda.sh -b -p $HOME/miniconda
export PATH="$HOME/miniconda/bin:$PATH"
conda init
source ~/.bashrc
conda create -n smartagent python=3.11 -y
conda activate smartagent
```
🧹 (Optional) Clean up installer:
```bash
rm miniconda.sh
```
### 2: Install Python Dependencies
```bash
pip install -r requirements.txt
```
## 🛠️ Build Your Smart Agent

### 1: Define Agent Behavior
```bash
nano my_agent.py
```
### Paste the following:
```bash
from allora_sdk.agents import BaseSmartAgent

class MyPriceMonitorAgent(BaseSmartAgent):
    def on_start(self):
        self.log("Agent initialized.")

    async def on_tick(self):
        price = await self.fetch_price("BTC")
        if price > 119000:
            await self.publish_signal("buy", {"price": price})
```
 To save: Ctrl + X, then press Y and Enter

 ### 2: Setup Tiingo API Key
 
1. Create a Tiingo account
2. Export your key as an environment variable:
```bash
export TIINGO_API_KEY=your_actual_key_here
```
###  3: Create YAML Config File
```bash
nano agent_config.yaml
```
Paste the following:
```bash
agent_name: "btc-price-monitor"
tick_interval: 60  # seconds
data_sources:
  - type: tiingo
    api_key: ${Enter the TIINGO_API_KEY}
```
### 🚀 Run Agent Locally
```bash
make run-agent
```
## 🧪 Test Agent Logic
### ✅ Unit Tests
```bash
pytest tests/
```
### 🔄 Integration Simulation
```bash
make simulate
```
## 📦 Package & Deploy

###  1: Package Agent
```bash
make package-agent
```
### 2: Deploy to Allora Network
```bash
allora-cli login
allora-cli deploy agent-package.tar.gz
```
---

## ✅ Done!
Your Smart Agent is now deployed and actively collaborating with the Allora decentralized intelligence network.






