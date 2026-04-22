---
name: shutdown
description: 收工同步助手。當使用者說「收工」、「結束了」、「準備換電腦」、「該同步的同步」、「先到這裡」等任何要結束工作並進行三方同步的請求時，請一定要使用此技能。本技能會智能更新 Obsidian 工作筆記、git commit + push GitHub。
---

# 收工同步助手

對話結束前，把今天的工作完整保存到三個家：
- **GDrive**：自動同步（不用管）
- **Obsidian 工作筆記**：智能更新「上次做到哪」+「最近更動紀錄」
- **GitHub**：commit + push 本 repo 變動

## 專案設定

- **GDrive 工作目錄**：`G:\我的雲端硬碟\Claude進階工作流`
- **GitHub repo**：`shinechiang07-cell/claude-advanced-workflow`
- **Obsidian vault**：`G:\我的雲端硬碟\secondbrain`
- **工作筆記路徑**：`G:\我的雲端硬碟\secondbrain\Claude進階工作流\工作筆記.md`
- **Firebase 專案**：`teacherstudy-46c01`

## 收工 SOP（依序執行）

### 步驟 1：盤點今天做了什麼
從對話歷史摘要：完成的檔案、決策、踩到的新坑。

### 步驟 2：更新 Obsidian 工作筆記
路徑：`G:\我的雲端硬碟\secondbrain\Claude進階工作流\工作筆記.md`
- 「⏯️ 上次做到哪」段：最後動作、完成的檔案、對話脈絡
- 「🗓️ 最近更動紀錄」表格最後加一行：今天日期 + 摘要 + ✅✅✅
- 「🕳️ 踩坑筆記」（若有新坑）：依分類加進去

### 步驟 3：Git commit + push
```bash
git -C "G:/我的雲端硬碟/Claude進階工作流" config windows.appendAtomically false
git -C "G:/我的雲端硬碟/Claude進階工作流" add <今天動到的檔案，不要 add .claude/>
git -C "G:/我的雲端硬碟/Claude進階工作流" commit -m "<今天工作摘要的 commit message>"
git -C "G:/我的雲端硬碟/Claude進階工作流" push origin master
```

commit message 寫法：
- 標題行：「動詞 + 對象」
- 正文：3-5 條 bullet 描述變動 + 為什麼

### 步驟 4：報告同步狀態
給使用者一個三勾表格：

| 平台 | 動到的檔案 | 狀態 |
|------|----------|------|
| GDrive | ... | ✅（自動） |
| Obsidian | 工作筆記更新 | ✅ |
| GitHub | commit + push | ✅ |

## 不該做的事
- ❌ 對「沒實質進度」的對話也跑同步（例：使用者只是問問題沒改檔）
- ❌ 把 `.claude/settings.local.json`、`.claude/worktrees/` commit 進去
- ❌ commit message 寫「更新」、「修改」這種沒資訊的字
