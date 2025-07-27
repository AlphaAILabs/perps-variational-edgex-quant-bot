# perps-variational-edgex-quant-bot

🤖 **AlphaAI Labs 开发的量化交易机器人 Docker 镜像**

一个基于 Docker 容器化部署的中低频永续合约量化交易系统，支持策略自动化执行。

## ✨ 特性

- 🔥 **容器化部署** - 基于 Docker 的一键部署方案
- ⚡ **高性能** - 优化的交易执行引擎
- 🛡️ **风险控制** - 内置多层风险管理机制

## 🚀 快速开始

### 环境准备

**系统要求:**
- Ubuntu 22.04 LTS 或更高版本
- x86_64 (AMD64) 架构
- 最低 1GB RAM，推荐 2GB+
- 推荐 25GB+ 存储空间

### 一键安装 Docker 环境
| 下述命令，请逐行执行

```bash
git clone https://github.com/AlphaAILabs/perps-variational-edgex-quant-bot.git  # 克隆仓库
cd perps-variational-edgex-quant-bot  # 进入到工程目录

# 安装 Docker 和 Docker Compose
sudo apt update
arch=`dpkg --print-architecture`
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=$arch] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt update
sudo apt install -y docker-ce
sudo systemctl status docker
sudo groupadd -f docker
sudo usermod -aG docker $USER
newgrp docker
groups
sudo curl -L "https://github.com/docker/compose/releases/download/v2.2.3/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

```

### 配置和运行

```bash
cp .env.example .env # 配置环境变量
vim .env

docker run -d -p 3000:3000 -v $(pwd)/.env:/app/.env --name perps-variational-edgex-bot ghcr.io/alphaailabs/perps-variational-edgex-quant-bot:v1.0.1 # 将在后台服务自动运行服务

# 查看服务运行日志
docker logs -f perps-variational-edgex-bot -n 100
```

### 更新参数
```shell
cd perps-variational-edgex-quant-bot

vim .env # 修改目标的参数配置
docker restart perps-variational-edgex-bot # 重启 Bot 服务
```

### 升级 Bot
```shell
cd perps-variational-edgex-quant-bot
vim .env # 根据最新 .env.example 去修改最新的配置参数

docker stop perps-variational-edgex-bot && docker rm -f perps-variational-edgex-bot

docker run -d -p 3000:3000 -v $(pwd)/.env:/app/.env --name perps-variational-edgex-bot ghcr.io/alphaailabs/perps-variational-edgex-quant-bot:v1.0.1 # 将在后台服务自动运行服务
# v1.0.1 为最新的代码版本
```

## 📦 Docker 镜像

### 支持的架构
- **x86_64 (AMD64)**: Intel/AMD 64位处理器
- **构建平台**: linux/amd64
- **测试环境**: Intel(R) Xeon(R) Platinum 8255C CPU @ 2.50GHz

### 镜像标签

| 标签 | 描述 | 稳定性 |
|------|------|--------|
| `v1.0.0` | 稳定版本 | 🟢 推荐 |
| `latest` | 最新版本 | 🟡 开发 |

## 🔧 配置说明

主要配置项在 `.env` 文件中：

```env
#ACCOUNT On variational or edgeX
ACCOUNT_ADDRESS=

#AlphaLabs Watchtower [optional]
ALPHALABS_KEY=

# Variational Client Configuration
VARIATIONAL_TOKEN=
VARIATIONAL_BASE_URL=http://localhost:3000

# EdgeX Client Configuration
EDGEX_API_KEY=
EDGEX_PASS_PHRASE=
EDGEX_BASE_URL=https://pro.edgex.exchange
EDGEX_SECRET=
EDGEX_L2_PRIVATE_KEY=
EDGEX_ACCOUNT_ID=

# Trading Configuration
# BTC 下单必须是 0.001 的倍数, 且大于 0.001
BTC_QTY_STEP=
# ETH 下单必须是 0.01 的倍数，且大于 0.01
ETH_QTY_STEP=
# 资金使用率
MAX_PORTFOLIO_MM=0.5
MAX_PORTFOLIO_IM=0.8
OPEN_POSITION_MARKET_PRICE_DIFF_BTC=100
OPEN_POSITION_MARKET_PRICE_DIFF_ETH=5
CLOSE_POSITION_ENTRY_PRICE_DIFF_BTC=500
CLOSE_POSITION_ENTRY_PRICE_DIFF_ETH=15
# 杠杆必须和前端界面设置的保持一致
VARIATIONAL_LEVERAGE_BTC=20
VARIATIONAL_LEVERAGE_ETH=10
EDGEX_LEVERAGE_BTC=20
EDGEX_LEVERAGE_ETH=10
```

## 📊 支持的平台

### 云服务器
✅ 腾讯云  
✅ 阿里云  
✅ AWS  
✅ Azure  

### 物理服务器
✅ Intel x86_64 处理器  
✅ AMD x86_64 处理器  


## 📞 技术支持

- 📧 **邮箱**: contact@alphalabs.app
-    **DC**: [Discord] (https://discord.com/invite/hG2M26Gp )
- 🐛 **问题反馈**: [GitHub Issues](https://github.com/AlphaAILabs/perps-variational-edgex-quant-bot/issues)

## ⚠️ 风险提示

- 量化交易存在风险，请充分了解相关风险后使用
- 建议先在测试环境中验证策略效果
- 请合理配置仓位和风险参数

## 📄 许可证

本项目采用 [GNU AFFERO GENERAL PUBLIC LICENSE](LICENSE) 许可证。

---

**AlphaAI Labs** - 专注于能量化交易技术