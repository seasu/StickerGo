# StickerGO 產品需求文件 (Full Version)
**版本:** 1.0.0
**日期:** 2026-04-29

## 1. 產品概述
StickerGO 是一款基於地理位置 (LBG) 的虛實整合社交遊戲，結合 AI 貼圖生成 (Magic Sticker) 與金融理財教育機制。

## 2. 用戶體系與權限
| 屬性 | 一般用戶 (Free) | 專業用戶 (Pro) |
| :--- | :--- | :--- |
| 召喚權限 | 最高至「靈貓」 | 解鎖「幻神」，排除「凡貓」 |
| 機率分布 | 凡貓(85%), 精銳(14%), 靈貓(1%) | 精銳(80%), 靈貓(18%), 幻神(2%) |
| 收益倍率 | 1.0x | 1.2x |
| 保底機制 | 無 | 50抽保底幻神 |

## 3. 等級與經驗值系統
- **升級公式**: NextLevelEXP = 100 * (CurrentLevel^1.5)
- **獎勵**: 升級獲得 Level * 10 點數。
- **生產經驗值**:
    - 凡貓: +10 EXP
    - 精銳: +30 EXP
    - 靈貓: +100 EXP
    - 幻神: +500 EXP

## 4. 地圖與 LBG 機制
- **雷達掃描**: 半徑 500m 內貼圖顯示。
- **領取判定**: 距離貼圖坐標 <= 20m。
- **埋藏規則**: 從背包選擇貼圖並綁定當前 GPS，貼圖進入世界地圖。

## 5. 技術架構
- **開發框架**: Flutter
- **後端服務**: Firebase (Auth, Firestore, Storage, Cloud Functions)
- **地圖服務**: Google Maps Platform / GeoFlutterFire
- **AI 整合**: Magic Sticker API
