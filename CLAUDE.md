# he-daily-privacy

靜態的隱私權政策網頁，只有一個檔案：`index.html`。完全離線、無建構流程、無依賴。

## 驗證工作（每次改 `index.html` 都要跑）

1. **語法檢查**：確認 HTML 結構完整，沒有未閉合的標籤。
2. **本地預覽**：`python3 -m http.server 8000`，在瀏覽器開 `http://localhost:8000` 檢查：
   - 桌面 viewport 排版正常
   - 手機 viewport（開 DevTools responsive mode）排版正常
   - 中文字體顯示正確，沒有亂碼
   - `mailto:` 連結可點
3. **更新日期**：若政策內容有實質變更，記得更新第 28 行「最後更新」。

## 禁止事項

- 不要引入任何 JavaScript、外部字體、分析 SDK、追蹤碼 — 政策明確宣告本 App 不發送任何網路請求，頁面本身也要遵守。
- 不要新增建構工具、套件管理檔或依賴。保持單一 HTML 檔。

## Git

開發分支：`claude/opus-efficiency-tips-joC0I`。Commit 訊息用繁體中文或英文皆可，簡述「為什麼改」。
