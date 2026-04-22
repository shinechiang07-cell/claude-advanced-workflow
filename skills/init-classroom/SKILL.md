---
name: init-classroom
description: 班級工具三合一工作模式初始化助手。當使用者說「初始化工作模式」、「幫我建專案」、「換電腦要重設」、「設定三合一工作流」等，請使用此技能。會自動建立 GDrive 工作資料夾、CLAUDE.md、GitHub repo、Obsidian 工作筆記、/收工 skill，完成後即可用 Firebase + GitHub + Obsidian 三合一節奏工作。
---

# 班級工具三合一初始化助手

幫老師在新電腦或新專案建立完整的三合一工作模式：
- 🗂️ **GDrive**：工作桌（跨電腦自動同步）
- 🐙 **GitHub**：公開 repo + Pages（工具上線）
- 📘 **Obsidian**：工作筆記駕駛艙（進度與想法）
- 🔥 **Firebase**：teacherstudy-46c01（學生資料）

---

## 已知的專案設定（本機）

- **GDrive 工作目錄**：`G:\我的雲端硬碟\Claude進階工作流`
- **GitHub repo**：`shinechiang07-cell/claude-advanced-workflow`
- **Obsidian vault**：`G:\我的雲端硬碟\secondbrain`
- **工作筆記**：`G:\我的雲端硬碟\secondbrain\Claude進階工作流\工作筆記.md`
- **Firebase 專案**：`teacherstudy-46c01`
- **GitHub 帳號**：`shinechiang07-cell`

---

## 初始化 SOP（換電腦時重跑）

### 步驟 0：環境檢查
```bash
git --version
gh auth status       # 未登入時執行 gh auth login
node --version
```
確認 G 槽 GDrive 已掛載、secondbrain vault 存在。

### 步驟 1：確認 GDrive 資料夾存在（GDrive 自動同步，通常已在）
```bash
ls "G:/我的雲端硬碟/Claude進階工作流"
```
若不存在才建立：
```bash
mkdir -p "G:/我的雲端硬碟/Claude進階工作流"
```

### 步驟 2：確認 git remote 正確
```bash
git -C "G:/我的雲端硬碟/Claude進階工作流" remote -v
# 若沒有 remote，拉回來：
git -C "G:/我的雲端硬碟/Claude進階工作流" remote add origin https://github.com/shinechiang07-cell/claude-advanced-workflow.git
git -C "G:/我的雲端硬碟/Claude進階工作流" pull origin master
```

### 步驟 3：確認 Obsidian 工作筆記存在
```bash
ls "G:/我的雲端硬碟/secondbrain/Claude進階工作流/工作筆記.md"
```
若不存在（vault 尚未同步到）才建立空檔。

### 步驟 4：安裝 /收工 skill
```bash
mkdir -p ~/.claude-skills/shutdown
mkdir -p ~/.claude-skills/init-classroom
```
然後把 `shutdown/SKILL.md` 與 `init-classroom/SKILL.md` 寫入（內容見下方「Skill 內容備份」段）。

### 步驟 5：重啟 Claude Code
🖐️ 告知使用者：「請完全關閉 Claude Code，再重新開啟，skill 才會載入。」

驗證：說「收工」看是否觸發三方同步 SOP。

---

## Skill 內容備份

> 換電腦初始化時，把以下內容分別寫入對應路徑。

### `~/.claude-skills/shutdown/SKILL.md`

````
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
- 「⏯️ 上次做到哪」：最後動作、完成的檔案
- 「🗓️ 最近更動紀錄」：加一行今天日期 + 摘要 + ✅✅✅
- 「🕳️ 踩坑筆記」：若有新坑就記下來

### 步驟 3：Git commit + push
```bash
git -C "G:/我的雲端硬碟/Claude進階工作流" config windows.appendAtomically false
git -C "G:/我的雲端硬碟/Claude進階工作流" add <今天動到的檔案，不要 add .claude/>
git -C "G:/我的雲端硬碟/Claude進階工作流" commit -m "<今天工作摘要>"
git -C "G:/我的雲端硬碟/Claude進階工作流" push origin master
```

### 步驟 4：報告三勾表格
| 平台 | 動到的檔案 | 狀態 |
|------|----------|------|
| GDrive | ... | ✅（自動） |
| Obsidian | 工作筆記更新 | ✅ |
| GitHub | commit + push | ✅ |

## 不該做的事
- ❌ 對「沒實質進度」的對話跑同步
- ❌ commit `.claude/` 目錄
- ❌ commit message 寫「更新」、「修改」這種沒資訊的字
````

---

## 工作節奏提醒

| 你說的話 | Claude 做的事 |
|---------|--------------|
| 「我想做一個 XXX 工具」 | 建 `tools/xxx/` 子資料夾 |
| 「請查 xxx 集合最高分」 | Firebase MCP 直接查 |
| 「收工」 | 三方同步（GitHub + Obsidian + GDrive） |
| 「讀工作筆記、告訴我上次做到哪」 | 摘要進度、建議下一步 |
