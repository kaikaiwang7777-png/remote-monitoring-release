# B1 VPS 應用更新
版本：v0.1.0-vps.update.20261024.1
只供 A 一次性修復及更新管理器啟用成功後、內容識別完全相符的 .4。不是 fresh-only 安裝器；不重新安裝 Ubuntu/PostgreSQL、不重設 admin/Telegram/TLS。此版包含 W6 固定整合的 W1–W5、W7 更新介面及 W8 手機／平板 WUI。
僅在精確 GPT 發布批准、RMR 發布及匿名校驗完成後操作。正式 manager 用固定 RMR HTTPS/Ubuntu 系統 CA 取得 root catalog，核版本、from identity、大小/SHA、AEAD與完整檔案清單；沒有獨立簽章。PACKAGE URL 指向獨立固定 package_commit，避免 catalog 與 ciphertext 自引用。既有伺服器 LoadCredential 密碼不傳至瀏覽器。
Owner 先用 /opt/rm-vps-update/runtime/venv/bin/python -I -B /opt/rm-vps-update/cli.py status，再用同一路徑 check。stage 需要 --version 本版與 --request-id 一個新32位十六進位ID；保留ID，不因連線失敗重送。先以 status 確認 STAGED，再以 install --job-id 實際ID --revision 實際revision --confirm。這些欄位來自該真工作，不得手填假成功或套用他人工作。
切換前預下載、驗證、保留舊版，只重啟 rm-test；不停止PostgreSQL、不跑 migration（要求 SQL 完全相同）。失敗時依真狀態決定有限 recover，需實際job/revision與 --confirm；RECOVERY_REQUIRED 不能假稱已回滾。更新前自行備份設定及資料，保存實際狀態與歷史。
B1後登入 HTTPS WUI 查看「VPS 系統更新」；後續 B2 須有真實產品變更及另一份精確 GPT 發布批准，才能由 WUI 發起、追蹤並確認。B1或A的發布／隔離測試不等於 ONLINE_UPDATE_ACCEPTED。真 root/systemd、VPS、上傳佇列跨重啟、真手機/Safari與真更新仍待Owner驗收；Windows原生測試維持STOP。
