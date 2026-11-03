# Private Relationship Atlas — 加密 GitHub Pages 報告

這是 Jacky × 瑋瑋的私人互動關係研究報告。網站解鎖畫面可公開查看，但**完整報告和原始 LINE 對話以 AES-256-GCM 加密**，解鎖密碼未放入儲存庫。密碼透過 PBKDF2-SHA256（420,000 iterations）衍生金鑰，解密只在使用者瀏覽器內進行。

## 部署檔案

- \`index.html\`：解鎖頁面與本機瀏覽器解密程式。
- \`payload.bin\`：加密報告資料。**仍需由報告持有人單獨上傳**。
- \`.nojekyll\`：可選空檔，讓 GitHub Pages 略過 Jekyll。
- \`README.md\`：使用及安全說明。

**嚴禁上傳：** 未加密的 HTML、原始 LINE TXT、解鎖密碼、任何明文備份。公開 Repo 的訪客可下載加密資料，故密碼應只在受信任的私下管道保存。

## GitHub Pages 設定

上傳加密 \`payload.bin\` 後，在儲存庫 \`Settings → Pages\` 選擇 \`Deploy from a branch\`，\`main\`，\`/(root)\`，儲存。

部署 URL： https://mm1990319.github.io/private-relationship-atlas/

## 隱私及限制

- 網站的 \`noindex\` 只通知搜尋引擎不要索引，**不是權限驗證**。真正的保護來自獨立密碼和加密。
- 使用 HTTPS GitHub Pages；若直接開啟本機 \`index.html\`，瀏覽器可能無法透過 fetch 載入 \`payload.bin\`。
- 解鎖時，明文內容僅出現在當前瀏覽器記憶體中；被授權閱讀者仍可複製內容，請謹慎分享密碼。
- 更換報告內容時，必須先重新產生加密 payload，並妥善管理新密碼。
