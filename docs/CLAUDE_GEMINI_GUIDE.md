# 開發者操作指南 (針對 Gemini/Claude CLI)

## 1. 資料結構 (Firestore)
- /users/{uid}: {points, exp, level, is_pro}
- /stickers/{sid}: {geohash, lat, lng, tier, owner_id, image_url}

## 2. 關鍵任務
- 實作 GeoHash 查詢功能以顯示地圖標記。
- 建立 Cloud Functions 處理召喚機率 (確保公平性)。
- 建立 GitHub Actions 進行代碼檢查。

## 3. 部署流程
- `firebase deploy --only functions`
- `flutter build ios --release`
