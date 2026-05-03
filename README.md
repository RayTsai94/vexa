# My Vexa Project

基於 [Vexa Dashboard](https://github.com/Vexa-ai/Vexa-Dashboard) 與 [Vexa Lite](https://github.com/Vexa-ai/vexa-lite-deploy) 的客製化開發專案。

---

## 環境需求

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Node.js 18+](https://nodejs.org/)
- [Git](https://git-scm.com/)

---

## 本機開發啟動步驟

### 1. Clone 專案

```bash
git clone https://github.com/你的帳號/my-vexa-project.git
cd my-vexa-project
```

### 2. 設定環境變數

```bash
cp .env.example .env.local
```

向隊友索取以下值並填入 `.env`：

| 變數 | 說明 |
|------|------|
| `DB_PASSWORD` | PostgreSQL 密碼 |
| `VEXA_ADMIN_API_KEY` | Vexa Admin Token |
| `TRANSCRIPTION_SERVICE_TOKEN` | Vexa 語音轉錄 Token |
| `JWT_SECRET` | JWT 簽章金鑰 |

### 3. 啟動所有後端服務

```bash
docker compose up -d
```

確認服務狀態：

```bash
docker compose ps
```

### 4. 啟動前端

```bash
cd frontend
cp .env.example .env.local   # 填入對應的環境變數
npm install --legacy-peer-deps
npm run dev
```

---

## 服務對應

| 服務 | 網址 |
|------|------|
| Dashboard 前端 | http://localhost:3000 |
| Vexa API | http://localhost:8056 |
| Vexa API Swagger | http://localhost:8056/docs |

---

## 環境變數說明

`.env.example` 內容：

```bash
# Database（需與隊友一致）
DB_USER=user
DB_PASSWORD=請向隊友索取
DB_NAME=vexa

# Vexa（需與隊友一致）
VEXA_ADMIN_API_KEY=請向隊友索取
TRANSCRIPTION_SERVICE_URL=https://transcription.vexa.ai/v1/audio/transcriptions
TRANSCRIPTION_SERVICE_TOKEN=請向隊友索取

# Security（需與隊友一致）
JWT_SECRET=請向隊友索取

# SMTP（選填）
SMTP_HOST=
SMTP_PORT=587
SMTP_SECURE=false
SMTP_USER=
SMTP_PASS=
SMTP_FROM=
```

> 敏感金鑰請透過私訊或密碼管理工具（如 1Password、Bitwarden）傳遞，不要貼在群組聊天室。

---

## 常用指令

```bash
# 啟動所有服務
docker compose up -d

# 停止所有服務
docker compose down

# 查看 log
docker compose logs -f

# 查看特定服務 log
docker compose logs -f vexa

# 重新 build（修改 Dockerfile 後）
docker compose up -d --build
```

---

## 分支策略

```
main              ← 穩定版，只接 Pull Request
  └─ feat/功能名稱  ← 開發新功能
  └─ fix/問題名稱   ← 修復 bug
```

開發流程：

```bash
# 開新功能前先拉最新 main
git checkout main
git pull origin main

# 開新分支
git checkout -b feat/my-feature

# 開發完推上去
git push origin feat/my-feature

# 在 GitHub 開 Pull Request，請隊友 review 後 merge
```

---

## 同步上游 Vexa 官方更新

```bash
git fetch upstream
git merge upstream/main
```

---

## 聯絡

如有環境問題請聯繫專案維護者。
