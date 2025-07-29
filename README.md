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
bash
Copy code
curl -OL https://go.dev/dl/go1.22.4.linux-amd64.tar.gz
sudo tar -C /usr/local -xvf go1.22.4.linux-amd64.tar.gz
export PATH=$PATH:/usr/local/go/bin
go version
3. Clone Allora SDK
bash
Copy code
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
Install Python Requirements
bash
Copy code
pip install -r requirements.txt
🤖 Build Your Smart Agent
1. Define Agent Logic
Create your agent file:

bash
Copy code
nano my_agent.py
Paste this code:

python
Copy code
from allora_sdk.agents import BaseSmartAgent

class MyPriceMonitorAgent(BaseSmartAgent):
    def on_start(self):
        self.log("Agent initialized.")

    async def on_tick(self):
        price = await self.fetch_price("BTC")
        if price > 70000:
            await self.publish_signal("sell", {"price": price})
Save: Ctrl + X, then Y, then Enter

2. Setup Tiingo API
Create an account at: Tiingo API Token

Replace ${TIINGO_API_KEY} in the config file

3. Create Config File
bash
Copy code
nano agent_config.yaml
Paste:

yaml
Copy code
agent_name: "btc-price-monitor"
tick_interval: 60  # seconds
data_sources:
  - type: tiingo
    api_key: ${TIINGO_API_KEY}
▶️ Run & Test the Agent
Run Locally
bash
Copy code
make run-agent
Run Unit Tests
bash
Copy code
pytest tests/
Simulate Agent Logic
bash
Copy code
make simulate
📦 Package & Deploy
Package Your Agent
bash
Copy code
make package-agent
Deploy to Allora Network
bash
Copy code
allora-cli login
allora-cli deploy agent-package.tar.gz

