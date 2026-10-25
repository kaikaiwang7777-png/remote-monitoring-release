# LightGlass VPS 應用更新
版本：v0.1.0-vps.update.20261025.1
只供已升級至B2且content_id相符的既有v1管理器；不是fresh安裝，不覆寫root updater，17份SQL migration不變。V1 published_at_utc僅為目錄有效起點，不是真公開時間；實際發布時間來自固定RMR Release API唯讀投影，缺失不回退目錄時間。新包含亮色玻璃全站、overlay抽屜、CPU/記憶體折線、磁碟與記憶體donut、RX+TX堆疊面積及正式版本分類。真採樣只在服務可見/proc namespace與錄影objects檔案系統，不宣稱整台VPS網卡；缺值不補零或虛構歷史。
PRIVATE_STORE/.server-dashboard為rm_test服務UID私有0700目錄／0600 lock及history-v1.ring；單sampler/lifetime flock、60秒採樣、10080個4096-byte slot（上限41287680bytes）。舊程式不讀此新增目錄，程式rollback保留歷史，不能承諾反向解讀新資料；落盤失敗顯示volatile。root updater不建立或改寫這些持久資料。
需本版本專屬Owner窗口與指定GPT精確發布批准後公開及匿名驗算，之後Owner從B2真WUI保存包含測試版設定並讀回確認→檢查更新→下載驗證一次→明確安裝；auto_install=false，不使用SSH/fresh-only替代，不冒稱B2此前已WUI驗收。未知回覆只查既有job/revision，不重送。
保留DB/admin/Telegram/TLS/ACME/影片/佇列/政策；更新前備份。完整性仍核固定RMR HTTPS/Ubuntu CA、來源版本/content_id、大小SHA256、AES-GCM與完整受管檔。沒有獨立Ed25519信任根。密碼只由既有systemd LoadCredential提供，不傳瀏覽器。
ROLLED_BACK不算成功；RECOVERY_REQUIRED僅由Owner另明確確認有限recover，使用真job.id及最新revision；不改state、刪pending、重新安裝或清資料。
三項既存完整PG race失敗（enrollment429、late-received409、legacy OFF/24H wire）未修復未豁免，不稱全庫全綠。隔離fixture、短host採樣與真VPS/長時採樣不同；手機真機/Safari、systemd/正式更新恢復仍待驗，Windows原生STOP。
