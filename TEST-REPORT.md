# 測試摘要

測試日期：2026-10-20。測試對象包括本機 HTTP 版本及正式網址 **https://evanwkm.github.io/jpc-digital-police-academy/**；離線備份另以 `file://` 開啟。

Public Repository 已建立；GitHub Pages 從 `main` 根目錄發佈，HTTPS 強制啟用。首次部署工作流程 [39357078783](https://github.com/evanwkm/jpc-digital-police-academy/actions/runs/39357078783) 的 build、report-build-status 及 deploy 均成功。

## 已通過

- JavaScript 語法檢查，首頁、繁體中文標題及學校名稱。
- 正式 HTTPS 網址回應 HTTP 200，傳回 HTML 與本機已測試的 `index.html` 逐字一致。
- 便利店、公園及巴士站三張原有 WebP 插畫均成功解碼和顯示。
- 三個場景各完成 30 秒觀察，然後收起插畫並進入 5 題選擇題。
- 選答、上一題、下一題及選答保留正常。
- 任務一全對 5 分、全錯 0 分。
- 原有 POLICE 對照表與全部原有電文及答案相符。
- 任務二虛擬鍵盤、字格選取、刪除、清除及提交；實體鍵盤輸入、Backspace 和 Enter。
- 任務二全對 5 分、全錯 0 分及部分正確按原比例四捨五入計分。
- 60 秒到時自動提交、結果頁、總分 10 分、再玩一次分數歸零、返回主頁。
- 兩項任務倒數時主畫面節點不被替換；觀察圖片、解碼終端及鍵盤保留原節點，輸入也不重建整頁。
- 桌面 1440×1000、iPad 尺寸 768×1024、手機 390×844 和小手機 320×740；無水平頁面溢出，按鈕未超出視窗。
- 離線 HTML 在網絡停用時仍能開啟首頁、開始遊戲及載入插畫。
- 測試流程沒有 JavaScript pageerror 或 console error；沒有向第三方服務發送資源請求。
- 另以真實時鐘測試兩項任務的數秒倒數；確認開始按鈕後 AudioContext 運行、指定字格輸入正常，以及分頁返回時過期任務會直接結算。
- 原檔資料逐項比較通過：場景資料、WebP 圖片位元組、備用 SVG、題目、選項、答案、全部電文及對照表完全相同；離線備份與入口逐字相同。

## 修復內容

- 動畫掃光層設為 `pointer-events:none`，避免遮擋按鈕。
- 密碼輸入改為局部更新字格及進度，保留原終端和鍵盤。
- 修正空白字格按刪除時沒有刪去上一個字母的問題。
- 加入實體英文字母鍵、Backspace 及 Enter 支援。
- 計時改用實際時間截止點，返回分頁時同步；插畫載入後才開始觀察計時。
- 在支援的瀏覽器恢復暫停音效；不支援音效時遊戲仍可運行。
- 手機版面保留原配色和內容，調整窄螢幕欄位、文字換行和倒數位置。
- 解除禁止放大的 viewport 限制。
- 加入內嵌 SVG 網站圖示，修正公開網站自動索取 favicon 時的 404 Console 錯誤。

原有問題、選項、答案、電文、插畫、計分規則及學校名稱保留。原有分數圓環 CSS 已驗證有效，維持原寫法。

## 限制與未完成

- 使用桌面 Chrome 的自動化測試和視窗尺寸模擬，未在實體 iPad、iPhone 或 Safari 驗證觸控與音效；不等同實機驗收。
- 倒數邊界使用 Playwright 瀏覽器時鐘加速；節點身份檢查可確認不因更新倒數重建畫面，並非對實際顯示器的逐幀閃爍量測。
- 截圖停用動畫以顯示穩定版面；互動測試保留動畫。
- QR Code 為 1176×1176 黑白 PNG，H 級容錯、四模組白邊，已用獨立解碼工具核實內容為正式 HTTPS 網址。未進行實體印刷及手機鏡頭掃描測試。

可重跑測試見 `tests/game.cjs` 及 `tests/realtime.cjs`，機器結果見 `artifacts/test-results.json`、`artifacts/public-test-results.json` 及 `artifacts/realtime-results.json`；QR Code 解碼結果見 `artifacts/qr-verification.json`，版面截圖見 `artifacts/`。原檔比較工具為 `scripts/audit-source.cjs`。
