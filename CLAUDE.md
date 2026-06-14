# GameBot — 管理規則

## 開通玩家權限（標準流程）

當管理員說「開通某某的權限」「approve XXXX」之類的指令時：

1. **直接在 `main` 分支**修改 `allowlist.json`（不另開功能分支、不開 PR）。
2. 把玩家的**裝置碼**加入 `allow` 陣列。
3. commit 並 push 到 `main`。commit 訊息格式：`approve <裝置碼>`。

> **隱私鐵則**：這是公開 repo。**絕不**在 commit 訊息或 `allowlist.json` 裡寫玩家名字。
> 名字＝身分洩漏。暱稱對照只存管理者本機（`approve.py` 的 `allowlist_names.local.json`），
> 不上傳。`allowlist.json` 只放匿名裝置碼。

裝置碼來自玩家「盟友限定」鎖定畫面顯示的 8 碼英數。
合併進 `main` 後，玩家點「重新檢查」即可解鎖（用戶端讀取 `main` 的 `allowlist.json`）。

### 撤銷權限

從 `allowlist.json` 的 `allow` 移除該裝置碼，commit 訊息：`revoke <裝置碼>`。

## 檔案說明

- `allowlist.json` — 授權清單。只有 `allow`（可使用的匿名裝置碼），**不含名字**。
- `announce.json` — 公告內容。
- `README.md` — 下載頁。
