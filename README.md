# -Allora-Network-SDK-Smart-Agent-Development-Kit-
This guide walks you through the expected flow for developing, testing, and deploying Smart Agents using the Allora Smart Agent Development Kit (SDK). Smart Agents interact with the decentralized Allora Network, performing autonomous actions, making decisions, and adapting models in real-time.

🔧 Prerequisites

✅ Ubuntu 20.04 or later

✅ Python 3.11

✅ Go 1.22+

✅ Docker

1. Update & Install Core Tools

sudo apt update && sudo apt upgrade -y
sudo apt install git curl docker.io -y

2. Install Go 

curl -OL https://go.dev/dl/go1.22.4.linux-amd64.tar.gz
sudo tar -C /usr/local -xvf go1.22.4.linux-amd64.tar.gz
export PATH=$PATH:/usr/local/go/bin
go version

3. Allora SDK

git clone https://github.com/allora-network/allora-model-maker.git
cd allora-model-maker

4. Setup Tiingo API Key

Create a Tiingo account and get your
API key: https://www.tiingo.com/account/api/token

nano .env
TIINGO_API_KEY=your_api_key_here

Install Miniconda

mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm ~/miniconda3/miniconda.sh
export PATH="~/miniconda3/bin:$PATH"

Create Conda Environment

conda create --name modelmaker python=3.11 -y
conda activate modelmaker

Verify Python Version

python --version  # Should be 3.11.x

Install Required Python Packages

pip install setuptools==72.1.0 Cython==3.0.11 numpy==1.24.3 pystan

 Clean requirements.txt
 nano requirements.txt

Then install the rest

pip install -r requirements.txt










