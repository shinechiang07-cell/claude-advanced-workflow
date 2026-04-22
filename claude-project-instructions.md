# Claude Project 說明（貼入 claude.ai 專案設定）

> 把以下「--- 開始 ---」到「--- 結束 ---」之間的文字，
> 貼入 claude.ai → 專案 → 「專案說明」欄位。

---開始---

## 我的身份與工作模式

我是一位國小老師，正在用 Claude 建立班級工具。每次對話請先當作你已了解以下設定。

## 三個家（工作環境）

| 用途 | 位置 |
|------|------|
| 工作桌（程式碼） | `G:\我的雲端硬碟\Claude進階工作流\` |
| GitHub repo | https://github.com/shinechiang07-cell/claude-advanced-workflow |
| Obsidian 工作筆記 | `G:\我的雲端硬碟\secondbrain\Claude進階工作流\工作筆記.md` |
| Firebase 資料庫 | 專案 ID：`teacherstudy-46c01` |

## 工作節奏

- **「我想做一個 XXX 工具」** → 引導我建 `tools/xxx/` 子資料夾，討論功能設計
- **「收工」** → 提醒我去 Claude Code 執行三方同步（chat 無法直接執行指令）
- **「讀工作筆記」** → 請我把工作筆記內容貼過來，幫我摘要並建議下一步
- **「查 Firebase xxx 集合」** → 提供查詢語法或告訴我去 Claude Code 用 Firebase MCP 查

## Firebase 資料結構（已知）

- Firebase 專案：`teacherstudy-46c01`
- 使用 Firestore 資料庫
- 學生資料只存座號 + 班級代號，不存真名

## 工具清單

（之後建好工具時更新這裡）
- 尚無

## 注意事項

- chat 無法執行指令，需要跑程式碼請告訴我去 Claude Code 操作
- commit 前一定要確認 `.claude/` 不在 staging area
- 學生資料去識別化

---結束---
