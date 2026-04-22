# Claude進階工作流 — 我的班級工具總專案

## 對話開始時請先讀
進度與最近更動都在 Obsidian：`secondbrain/Claude進階工作流/工作筆記.md`

## 工作模式

### 一般工具開發
- **加新工具**：對 Claude 說「我想做一個 XXX 工具」→ Claude 會建 `tools/<工具名>/` 子資料夾、引導我跟著影片做
- **接續工作**：對 Claude 說「讀工作筆記、告訴我上次做到哪」
- **消化**：對 Claude 說「消化」→ 僅執行收工步驟 3 + 4（不 commit/push）

### 備課駕駛艙
- **觸發語**：「做第 X 課教學駕駛艙」或「把這課做成駕駛艙」
- **教材來源**：`G:\我的雲端硬碟\Claude 工作區\@@@南一五上國語教科書\`
- **執行技能**：`anthropic-skills:teaching-cockpit`（自動讀 PDF → NotebookLM 生成素材 → 產出互動 HTML）
- **部署目標**：GitHub repo `shinechiang07-cell/lesson-cockpit`（獨立備課 repo，GitHub Pages 對外公開）
- **收工時額外記錄**：在工作筆記 + 每日筆記中補上「完成第幾課、Pages 網址」

### 收工（所有工作模式共用）
對 Claude 說「**收工**」→ 依序執行：
1. git commit + push 到對應 GitHub repo
2. 更新 `secondbrain/Claude進階工作流/工作筆記.md`（進度日誌）
3. 將本次工作消化寫入 `secondbrain/每日筆記/YYYY-MM-DD.md`（今天學到什麼、做了什麼、接下來）
4. 更新 Claude Code 記憶（memory 資料夾），儲存值得跨對話保留的 feedback / project 重點
5. Firebase（條件式）：若本次工作有新增或修改 Firestore 資料結構、集合、規則，才需同步；純靜態工具略過

## 工作桌 + 四個家

| 用途 | 位置 |
|------|------|
| 📋 程式工具工作桌 | `G:\我的雲端硬碟\Claude進階工作流\` |
| 📚 備課教材來源 | `G:\我的雲端硬碟\Claude 工作區\@@@南一五上國語教科書\` |
| 🐙 工具 GitHub | `shinechiang07-cell/claude-advanced-workflow` |
| 🎓 備課駕駛艙 GitHub | `shinechiang07-cell/lesson-cockpit`（GitHub Pages） |
| 📘 Obsidian 駕駛艙 | `secondbrain/Claude進階工作流/工作筆記.md` |
| 🔥 Firebase 專案 | `teacherstudy-46c01`（動態資料用） |

## 工具清單
- `tools/disney-guide/` — 東京迪士尼海洋 2026 互動攻略（個人旅遊）
- `lesson-cockpit/`（獨立 repo）— 南一五上國語教學駕駛艙（GitHub Pages）

## 工作注意事項
- 學生資料一律去識別化（只用座號 + 班級代號）
- commit 訊息要寫清楚做了什麼 + 為什麼
- 備課駕駛艙的影片不上傳 GitHub，放 YouTube 不公開再嵌入
- 備課 PDF 不推 GitHub，只讀取不上傳
