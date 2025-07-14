# Rule Alpha Core Platform

Rule Alpha 核心平台，包含前端界面、後端API和規則引擎服務。

## 🏗️ 系統架構

```
Rule Alpha Core Platform
├── rule_alpha_backend/     # PHP後端API服務
├── rule_alpha_frontend/    # Vue.js前端界面
├── rule_alpha_server/      # Python規則引擎
├── rule_alpha_shared/      # 共享組件庫
├── docker-compose.yml      # 服務編排配置
└── .env.example           # 環境變數範例
```

## 🚀 快速部署

### 前置需求
- Docker & Docker Compose
- 運行中的cocaen基礎設施 (nginx-proxy, MariaDB, MQTT)

### 部署步驟

1. **克隆專案**
```bash
git clone https://github.com/yourusername/rule-alpha-core.git
cd rule-alpha-core
```

2. **配置環境變數**
```bash
cp .env.example .env
# 編輯 .env 檔案設定域名和憑證
```

3. **生產環境部署**
```bash
docker-compose --profile production up -d
```

4. **開發環境部署**
```bash
docker-compose --profile development up -d
```

## 🌐 服務端點

### 生產環境
- **前端**: https://rule-alpha.{DOMAIN_SUFFIX}
- **後端API**: https://rule-alpha-api.{DOMAIN_SUFFIX}
- **規則引擎**: https://rule-alpha-engine.{DOMAIN_SUFFIX}

### 開發環境
- **前端**: http://localhost:3000
- **後端API**: http://localhost:8000
- **規則引擎**: http://localhost:8001

## 📋 服務說明

### rule_alpha_backend
- **技術**: PHP 8.1 + Apache
- **功能**: RESTful API, JWT認證, 數據庫存取
- **依賴**: MariaDB

### rule_alpha_frontend
- **技術**: Vue.js 3 + Vite + Tailwind CSS
- **功能**: 響應式界面, 多語言支援, 主題切換
- **API**: 連接後端API服務

### rule_alpha_server
- **技術**: Python 3.9 + FastAPI
- **功能**: 規則引擎, MQTT通信, 專案管理
- **依賴**: MariaDB, MQTT Broker

### rule_alpha_shared
- **功能**: 共享監控組件, 工具函數
- **使用**: 各服務共用的基礎組件

## 🔧 開發指南

### 本地開發

1. **後端開發**
```bash
cd rule_alpha_backend
composer install
php -S localhost:8000
```

2. **前端開發**
```bash
cd rule_alpha_frontend
npm install
npm run dev
```

3. **規則引擎開發**
```bash
cd rule_alpha_server
pip install -r requirements.txt
python main.py
```

### 環境變數說明

| 變數 | 說明 | 範例 |
|------|------|------|
| `DOMAIN_SUFFIX` | 主域名 | `example.com` |
| `LETSENCRYPT_EMAIL` | SSL憑證申請郵箱 | `admin@example.com` |
| `RULE_ALPHA_DB_*` | 數據庫連接配置 | - |
| `JWT_SECRET` | JWT簽名密鑰 | `your_secret_key` |

## 🔐 安全配置

- SSL/TLS自動憑證管理
- JWT token認證
- 數據庫連接加密
- CORS跨域保護
- 輸入驗證和過濾

## 📊 監控和日誌

```bash
# 查看服務狀態
docker-compose ps

# 查看服務日誌
docker-compose logs -f [service_name]

# 健康檢查
curl https://rule-alpha-api.{DOMAIN_SUFFIX}/api/health
```

## 🐛 故障排除

### 常見問題

1. **服務無法啟動**
   - 檢查 `.env` 配置
   - 確認cocaen基礎設施運行中
   - 查看服務日誌

2. **無法連接數據庫**
   - 檢查數據庫憑證
   - 確認MariaDB服務運行
   - 檢查網路連接

3. **SSL憑證問題**
   - 確認域名DNS設定
   - 檢查Let's Encrypt服務
   - 查看nginx-proxy日誌

## 📞 技術支持

- **維護者**: arch.twn1@gmail.com
- **問題報告**: GitHub Issues
- **文檔**: [Rule Alpha Docs](https://docs.rule-alpha.com)

## 📄 授權協議

MIT License