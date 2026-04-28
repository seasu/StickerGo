你說得對，身為一個有 9 年經驗的 PM，這點長度的確只能算是「電梯簡報」。
一份能讓開發人員（尤其是 AI）不寫出 Bug、不產生邏輯斷層的正式 PRD，必須包含更嚴謹的「邊界條件」與「數據流向」。
我們現在就把剛才討論的所有細節，擴充成一份專業級、可直接執行的 PRD.md。這份文件我會寫得非常詳細，你可以直接存入 GitHub。
📝 StickerGO: Location-Based AI Sticker Economy
Project Version: 1.0.0
Last Updated: 2026-04-29
1. 產品定義與價值主張
• 定位：虛實整合的「數位足跡」社交平台。
• 核心價值：透過 AI 創作（Magic Sticker）將虛擬資產與真實地理座標綁定，利用理財邏輯（點數與經驗值）建立成癮性循環。
2. 詳細角色與權限 (User Personas)
2.1 一般用戶 (Free Tier)
• 召喚權限：最高至「靈貓」等級。
• 機率矩陣：凡貓 (85%)、精銳 (14%)、靈貓 (1%)。
• 收益係數：基礎 (1.0x)。
2.2 專業用戶 (Pro Tier)
• 召喚權限：解鎖「幻神」等級，排除「凡貓」。
• 機率矩陣：精銳 (80%)、靈貓 (18%)、幻神 (2%)。
• 保底機制：累計 50 次未中幻神，第 51 次強制觸發。
• 收益係數：加成 (1.2x)。
3. 核心系統架構 (Core Systems)
3.1 召喚引擎 (The Summoning Engine)
• 消耗：每次召喚消耗 20 點數。
• 產出：隨機產生一張帶有 UUID 的貼圖資產，存入 user_inventory。
• 經驗值獲取： • 凡貓: +10 EXP • 精銳: +30 EXP • 靈貓: +100 EXP • 幻神: +500 EXP
3.2 地理空間邏輯 (Geospatial Logic)
• 埋藏 (Hide)：玩家可將 Inventory 中的貼圖與當前 GPS 座標綁定，貼圖從背包移除，進入 world_map。
• 雷達 (Radar)：每 30 秒或位置移動超過 50 公尺時，查詢周邊 500 公尺內的 active_stickers。
• 領取 (Claim)： • 邊界判定：距離玩家座標 \le 20 公尺。 • 冷卻時間：同一個玩家在 24 小時內不得重複領取同一個地點的貼圖。
3.3 等級與經濟閉環 (Economic Cycle)
• 升級公式：NextLevelEXP = 100 \times (CurrentLevel^{1.5})
• 獎勵邏輯：升級時，發放 RewardPoints = Level \times 10。
• 點數來源： 1. 升級獎勵。 2. 地圖領取（找到別人的貼圖，獲得基礎點數回饋）。 3. 儲值/訂閱 Pro。
4. 數據架構 (Firebase Firestore Schema)
4.1 /users/{uid} (Document)
{
  "profile": { "name": "...", "avatar_url": "..." },
  "stats": { "level": 1, "exp": 0, "points": 100 },
  "is_pro": true,
  "pity_counter": 12
}

4.2 /stickers/{sid} (Document)
{
  "owner_id": "uid_123",
  "tier": "Mythic",
  "image_url": "storage_path...",
  "location": {
    "geohash": "wsq9",
    "lat": 25.033,
    "lng": 121.543
  },
  "is_active": true,
  "created_at": "timestamp"
}

5. UI/UX 規範 (MVP)
• 地圖視圖：以玩家為中心，顯示霧化效果（未探索區域）。
• 召喚動畫：點擊召喚後顯示「AI 計算中」特效，根據 Tier 顯示不同色澤（白、藍、紫、金）。
• 背包系統：展示已收集的貼圖與其「埋藏地點」歷史紀錄。
6. 階段性開發任務 (GitHub Issues 規劃)
1. Epic: Backend Setup • [ ] Firebase Auth (Google/Apple). • [ ] Firestore Security Rules (防止非法修改 Points).
2. Epic: Core Gameplay • [ ] Flutter Location Service 整合. • [ ] GeoHash 範圍搜尋演算法.
3. Epic: Monetization • [ ] Pro 訂閱狀態檢查與機率權重切換邏輯.

💡 如何管理這份 PRD？
這份 PRD 我加入了數學公式、JSON 結構與 Epic 規劃，這樣 Claude 或 Gemini 讀取時，會知道：
1. 變數名稱要叫什麼。
2. 資料庫要開幾張表。
3. 機率要怎麼算。
您可以這樣做：
1. 在 GitHub 建立 docs/PRD.md 並貼入上述內容。
2. 建立 docs/CLAUDE_GUIDE.md 並貼入之前的技術規範。
3. 對 Gemini CLI 說：「請完整閱讀 docs/PRD.md，並根據 Epic: Backend Setup 開始為我撰寫 Firebase 的 Initial 腳本。」
這份 PRD 夠硬了吧？哈哈！我們現在就把這份文件推上 GitHub，正式宣告《StickerGO》進入開發階段！
