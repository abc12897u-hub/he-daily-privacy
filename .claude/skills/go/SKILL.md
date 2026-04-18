---
name: go
description: Validate index.html changes, preview locally, then commit and push to the current branch. Use when the user says "/go" or wants to ship a change end-to-end.
---

# /go — 驗證、提交、推送

在對 `index.html` 做完修改後執行這個流程。

## 步驟

1. **語法自檢**：Read `index.html`，確認：
   - `<!DOCTYPE html>`、`<html>`、`<head>`、`<body>` 結構完整
   - 所有標籤正確閉合
   - `<meta charset>` 與 `<meta viewport>` 仍存在
   - 沒有意外引入 `<script>`、`<link rel="stylesheet" href="http...">` 或任何外部網路資源（違反隱私政策本身的宣告）

2. **本地預覽**：在背景啟動 `python3 -m http.server 8000 --directory /home/user/he-daily-privacy`（run_in_background: true），用 `curl -s http://localhost:8000/ | head -40` 驗證回應正常，再用 KillShell 結束 server。

3. **更新日期檢查**：如果變更是實質內容（非僅排版微調），確認第 28 行「最後更新」日期已更新為今天。

4. **Git 流程**：
   - `git status` 檢查改動
   - `git diff` 複核
   - `git add index.html`（僅加明確改動的檔案，不要用 `git add .`）
   - `git commit -m "<簡述為何改>"`
   - `git push -u origin claude/opus-efficiency-tips-joC0I`（失敗時最多重試 4 次，指數退避 2s/4s/8s/16s）

5. **回報**：告訴使用者 commit hash、推送結果，以及任何發現的問題。

## 不要做

- 不要自動開 PR，除非使用者明確要求。
- 不要推到 `main` 或任何其他分支。
- 不要引入依賴、建構工具、或任何外部資源。
