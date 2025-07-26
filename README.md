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

```bash
# 克隆仓库
git clone https://github.com/AlphaAILabs/perps-variational-edgex-quant-bot.git
cd perps-variational-edgex-quant-bot

# 自动安装 Docker 和 Docker Compose
chmod +x init_env.sh
sudo ./init_env.sh
```

### 配置和运行

```bash
# 配置环境变量
cp .env.example .env
vim .env

# 使用 Docker Compose 运行（推荐）
docker-compose up -d

# 或者使用 Docker 直接运行
docker run -d -p 3000:3000 -v $(pwd)/.env:/app/.env ghcr.io/alphaailabs/perps-variational-edgex-quant-bot:v1.0.0
```

### 监控和管理

```bash
# 查看运行状态
docker-compose ps

# 查看日志
docker-compose logs -f your_container -n 100

# 停止服务
docker-compose down
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

#FANWAN NOTIFY [optional]
FANWAN_TOKEN=

# Variational Client Configuration
# VARIATIONAL_TOKEN=
VARIATIONAL_TOKEN=
VARIATIONAL_BASE_URL=

# EdgeX Client Configuration
EDGEX_API_KEY=
EDGEX_PASS_PHRASE=
EDGEX_BASE_URL=
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
- 🐛 **问题反馈**: [GitHub Issues](https://github.com/AlphaAILabs/perps-variational-edgex-quant-bot/issues)

## ⚠️ 风险提示

- 量化交易存在风险，请充分了解相关风险后使用
- 建议先在测试环境中验证策略效果
- 请合理配置仓位和风险参数

## 📄 许可证

本项目采用 [GNU AFFERO GENERAL PUBLIC LICENSE](LICENSE) 许可证。

---

**AlphaAI Labs** - 专注于能量化交易技术