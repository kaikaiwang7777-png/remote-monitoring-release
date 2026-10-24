# B2 VPS 應用更新
版本：v0.1.0-vps.update.20261024.2
只供已正式升級B1且內容識別相符的既有v1更新管理器；不是fresh安裝，不覆寫獨立特權更新器，不修改SQL migration。左側側欄、持久後端自動檢查/安裝政策與Stable/Pre-release分類皆來自固定W6 source。
僅在本B2精確GPT發布批准與RMR匿名校驗後，由Owner從B1 WebUI的VPS系統更新頁手動檢查、下載驗證、明確確認安裝，保存實際job/revision；未知回覆只查詢，不自動重送。B1尚無B2政策勾選框，不能要求先勾選不存在的控制項；B1 v1 manager可發現本Pre-release且B1無背景自動安裝政策。
B2啟動後預設定期檢查開/24小時、自動安裝關、包含測試版關、維護03:00 GMT+8；首次B2驗收不開自動安裝。未勾包含測試版時後續僅Stable候選；Draft永遠拒絕。自動安裝及測試版需各自明確設定與風險確認，不能由手動WUI成功推論排程已驗收。
更新器仍核固定RMR HTTPS/系統CA、來源版本/content_id、大小SHA256、AEAD與完整受管清單。無獨立簽章根，LoadCredential密碼不傳瀏覽器。備份既有DB/admin/設定/影片佇列/TLS/ACME，不重新安裝或清資料。
失敗按真job狀態處理：ROLLED_BACK非成功，RECOVERY_REQUIRED才由Owner另確認有限recover，保留真job.id與最新revision；不刪pending、不改狀態、不以SSH安裝冒充WUI驗收。
完整含PG race有三項既存失敗：enrollment race429、late-received UPDATE_LIFECYCLE_FENCED、legacy schedule OFF/24H wire；B1隔離同類重現，未修復，不能宣稱全庫全綠。真systemd長時排程、自動安裝、VPS/資料保留、真手機Safari及WUI真升級待Owner驗收，Windows原生STOP。
