# 少年警訊｜數碼警察學院

香港中文大學校友會聯會陳震夏中學學習展示日互動遊戲。

## 目前狀態

遊戲已部署至 Public Repository，GitHub Pages 建置及部署成功，HTTPS 已啟用。

- **正式遊戲：[按此開始](https://evanwkm.github.io/jpc-digital-police-academy/)**
- **Repository：[evanwkm/jpc-digital-police-academy](https://github.com/evanwkm/jpc-digital-police-academy)**
- **[印刷用 QR Code PNG](game-qr.png)**
- [成功的首次部署紀錄](https://github.com/evanwkm/jpc-digital-police-academy/actions/runs/39357078783)

## 檔案

- `index.html`：GitHub Pages 入口，包含所有 CSS、JavaScript、原有三張插畫及合成音效。
- `offline-backup.html`：與入口完全相同的離線備份。用 Chrome、Edge 或 Safari 開啟即可，不需要連線。
- `.nojekyll`：指示 GitHub 直接發佈靜態檔案。
- `game-qr.png`：1176×1176 黑白 PNG，內容為正式 HTTPS 遊戲網址；已由本機解碼工具驗證，無第三方轉址或追蹤服務。
- `TEST-REPORT.md`：測試摘要及限制。
- `tests/game.cjs`：可重跑的 Playwright 測試。
- `artifacts/`：測試結果及各尺寸畫面截圖，毋須上傳至網站。

## 日後如需在另一帳戶重新部署（目前網站已部署）

1. 登入 [GitHub](https://github.com/)，按右上角 **+ → New repository**。
2. Repository name 填入 **jpc-digital-police-academy**，選擇 **Public**，啟用 **Add README**，按 **Create repository**。
3. 在新 Repository 按 **Add file → Upload files**，將本資料夾的 **index.html** 拖進去，按 **Commit changes**。只上傳這一個檔案也能運行。
4. 打開 **Settings → Pages**。在 **Build and deployment** 選擇 **Deploy from a branch**，選 **main** 及 **/(root)**，按 **Save**。
5. 等待部署完成，Pages 頁會顯示正式網址及 **Visit site**。GitHub 說明發佈更新可能需要最多約 10 分鐘。
6. 用 **Visit site** 開啟遊戲，完成兩項任務，確認結果頁能按 **再玩一次**。

一般網址格式為 `https://你的帳戶名稱.github.io/jpc-digital-police-academy/`；請以 Pages 顯示的實際網址為準，未部署前不能當作正式網址使用。

官方說明：[Creating a GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)。

## 日後更新

先保留目前可用的 HTML 備份，再到 Repository 的 **Add file → Upload files** 上傳新版 `index.html`，同名覆蓋後 **Commit changes**。等待 Pages 再次完成部署，重新載入正式網址測試；網址保持相同。若瀏覽器仍顯示舊版，重新整理或關閉該分頁再開啟。

## 展示日使用

參加者開啟正式網址，按 **開始任務**；觀察隨機場景 30 秒後回答 5 題，再於 60 秒內破解電文。每項任務 5 分，總分 10 分。結果頁按 **再玩一次**即可讓下一位參加者開始，或按 **返回主頁**。虛擬鍵盤及實體英文字母鍵均可輸入密碼，實體 Backspace 刪除，Enter 提交。

不需要安裝軟件、GitHub 帳戶、登入或資料庫。首次開啟公開網址需要網絡；如場地斷網，工作人員可使用預先儲存的 `offline-backup.html`。這是離線備份，網站本身沒有 Service Worker 離線快取。

## QR Code

使用 `game-qr.png`，建議以至少 5×5 公分印刷，保留四周白邊，不要裁去、拉伸或改變黑白對比。已由軟件解碼確認連到正式遊戲網址；展示前請用現場手機掃描一次，以確認場地網絡及印刷品質。換遊戲內容但保持相同網址時，毋須重印 QR Code。

QR Code 只使用本機工具產生，不經第三方 QR Code 網站；遊戲也不需要載入這些製作工具。

## 本機測試

需要 Node.js、Playwright 及 Chrome。執行 `node tests/game.cjs`。如 Playwright 安裝位置不同，設定 `PLAYWRIGHT_MODULE`；Chrome 路徑可設定 `CHROME_PATH`。測試會產生截圖及 `artifacts/test-results.json`。

正式網址已確認 HTTP 200，下載內容與本機修正版一致；完整驗收與實機測試限制見 `TEST-REPORT.md`。
