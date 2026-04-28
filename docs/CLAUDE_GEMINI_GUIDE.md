# StickerGO 開發者指南 (Firebase + GitHub)

## 1. 環境配置
- Flutter SDK (最新版)
- Firebase CLI (flutterfire configure)
- GitHub CLI (gh)

## 2. 資料結構 (Firestore)
- `/users/{uid}`: 存儲積分、等級、EXP、Pro 狀態。
- `/stickers/{sid}`: 存儲 Geohash、坐標、等級、圖片 URL、所有者。

## 3. GitHub 工作流建議
- **分支策略**: `main` (穩定版), `dev` (開發版)。
- **文檔同步**: 每次重大邏輯變更需同步更新 `docs/PRD.md`。
- **自動化**: 配置 GitHub Actions 進行代碼檢查與 Firebase Functions 部署。

## 4. Gemini CLI 開工指令範例
> "Gemini, read docs/PRD.md and implement the `StickerSummonEngine` in Cloud Functions with the defined probabilities for Free and Pro users."
