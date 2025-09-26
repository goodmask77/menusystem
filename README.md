# 菜單管理系統

這是一個提供餐廳管理菜單、桌數與點餐資訊的純前端應用程式。專案使用原生 HTML、CSS 與 JavaScript，支援匯入/匯出菜單、切換前台/後台模式等功能。

## 專案結構

```
├── public/
│   ├── index.html   # 主頁面
│   ├── styles.css   # 版面與元件樣式
│   └── script.js    # 功能邏輯（含菜單資料）
└── vercel.json      # Vercel 部署設定
```

## 本地開發

1. 安裝任何靜態伺服器（如 `serve`、`http-server` 或直接使用 VS Code Live Server）。
2. 在專案根目錄啟動伺服器並指向 `public/`：
   ```bash
   npx serve public
   ```
3. 造訪終端機顯示的網址即可檢視與操作菜單管理系統。

## 部署至 Vercel

1. 將此專案推送至 GitHub 儲存庫。
2. 登入 [Vercel](https://vercel.com) 並選擇 `Add New...` → `Project` → 匯入剛剛的 GitHub 儲存庫。
3. 在 **Framework Preset** 選擇 `Other`，並於 **Root Directory** 選擇專案根目錄（`/`）。
4. 建置命令與輸出目錄皆留空，因為專案為純靜態頁面，Vercel 會直接透過 `vercel.json` 發佈 `public/` 目錄內容。
5. 建置完成後，Vercel 會提供公開網址；每次推送到 `main`（或你設定的分支）時會自動重新部署。

### 關於 `vercel.json`

- `builds` 指示 Vercel 使用 `@vercel/static` 發佈 `public/` 目錄內的所有檔案。
- `routes` 先讓 Vercel 處理所有實際存在的檔案，若無對應檔案則回退至 `public/` 目錄對應路徑，確保 `/styles.css`、`/script.js` 等資源皆能正確載入。

若部署失敗，請檢查：
- GitHub 分支是否與 Vercel 專案綁定的分支一致。
- 最新的 commit 是否已推送至遠端儲存庫。
- Vercel 儀表板上的 Build Logs 是否顯示權限或網路錯誤。

## 已知限制

- 應用程式資料儲存在瀏覽器 `localStorage`，部署後不同使用者各自維護本地資料，無法共享。
- 若需後端或多人共用資料，建議後續整合 API 或資料庫服務。
