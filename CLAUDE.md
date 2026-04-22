# Claude進階工作流 — 我的班級工具總專案

## 對話開始時請先讀
進度與最近更動都在 Obsidian：`secondbrain/Claude進階工作流/工作筆記.md`

## 工作模式
- **加新工具**：對 Claude 說「我想做一個 XXX 工具」→ Claude 會建 `tools/<工具名>/` 子資料夾、引導我跟著影片做
- **結束工作**：對 Claude 說「**收工**」→ 依序執行：
  1. git commit + push 到 GitHub
  2. 更新 `secondbrain/Claude進階工作流/工作筆記.md`（進度日誌）
  3. 將本次工作消化寫入 `secondbrain/每日筆記/YYYY-MM-DD.md`（今天學到什麼、做了什麼、接下來）
  4. 更新 Claude Code 記憶（memory 資料夾），儲存值得跨對話保留的 feedback / project 重點
- **接續工作**：對 Claude 說「讀工作筆記、告訴我上次做到哪」
- **消化**：對 Claude 說「消化」→ 僅執行步驟 3 + 4（不 commit/push）

## 工作桌 + 三個家
- 📋 GDrive 工作桌：`G:\我的雲端硬碟\Claude進階工作流\`（自動跨電腦同步）
- 🐙 GitHub repo：`shinechiang07-cell/claude-advanced-workflow`（公開，網頁的家）
- 📘 Obsidian 駕駛艙：`secondbrain/Claude進階工作流/工作筆記.md`（想法的家）
- 🔥 Firebase 專案：`teacherstudy-46c01`（資料的家）

## 工具清單
（之後加新工具時會自動更新）
- （尚無）

## 工作注意事項
- 學生資料一律去識別化（只用座號 + 班級代號）
- commit 訊息要寫清楚做了什麼 + 為什麼
- 收工前說「收工」讓 Claude 同步三方
