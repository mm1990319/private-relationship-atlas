# Private Relationship Atlas — 加密 GitHub Pages 互動報告

這是私人互動關係研究報告。網站解鎖頁與加密資料檔公開存取，但**LINE 對話與分析報告內容使用 AES-256-GCM 加密**。密碼只在使用者瀏覽器內輸入，不在網站程式、儲存庫或外部服務儲存。

## 使用與更換密碼

1. 打開 https://mm1990319.github.io/private-relationship-atlas/ 並輸入現有密碼。
2. 解鎖後，點上方工具列的 **「設定／更換密碼」**。
3. 設定至少 16 字元的新密碼（建議 24 字元以上、使用密碼管理器產生），再輸入一次。
4. 點 **「產生新加密檔案」**，瀏覽器會使用新隨機 salt 與 IV，在本機重新加密完整報告，並下載新 `payload.bin`。密碼不會傳送到 GitHub。
5. 到 [此儲存庫](https://github.com/mm1990319/private-relationship-atlas) → Add file → Upload files，上傳新 `payload.bin`，提交變更。只有更新線上 `payload.bin` 後，新密碼才正式生效。
6. 等 GitHub Pages 部署完成，在新的無痕視窗使用新密碼測試確認。

請保留新密碼到能成功解鎖線上網站為止；不要將密碼交給 AI、放進 GitHub、或公開貼文。新檔會取代網站所使用的舊版，但下載新檔這一步**本身不會修改線上網站**。

## 加密格式

- 舊版 `payload.bin`：原始 AES-GCM 密文，使用初始頁面內固定 salt 和 IV 解密，為相容性保留。
- 新版 `payload.bin`：二進位格式為 `RAT2` 四個 ASCII bytes + 16 bytes salt + 12 bytes IV + AES-256-GCM 密文與 16 bytes 認證標籤。
- KDF：PBKDF2-SHA256，420,000 次迭代。
- AES-GCM AAD：`private-relationship-atlas-v2`。
- 新版報告只需替換 `payload.bin`，`index.html` 不需要跟著修改。

## 部署設定

在 `Settings → Pages` 選擇 `Deploy from a branch`、`main`、`/(root)`。本網站設為 noindex，但 noindex 並不是權限控管。公開網站及加密檔仍可被所有人存取下載。

**請勿提交：** 原始 LINE TXT、未加密 HTML、任何明文備份、密碼。

## 重要資安提醒

- 密碼更換**不能撤銷已公開的舊密文**。GitHub 歷史版本、下載者的備份或快取可能持續保存舊版 `payload.bin`，持有舊密碼者仍可能解密舊版。
- 如果需要撤銷舊密碼對歷史資料的存取，須改用新的、沒有舊版密文歷史的新儲存庫／服務，並了解既有公開檔案已被下載的風險無法完全消除。
- 此方案是用加密保護內容，並**非使用者登入權限控管**。若需要阻止陌生人下載加密資料，須採真正受權限管控的資料儲存及部署方案。
- 本機解鎖後，瀏覽器記憶體內會包含解密內容。使用者仍需保護自己的裝置與帳號。
