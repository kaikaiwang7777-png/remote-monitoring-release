# 一次性 .4 修復與 VPS 更新管理器啟用
版本：v0.1.0-vps.repair-enable.20261023.1
僅供已完成安裝且符合固定 .4 身分、原 25 檔及三份合法聲明的 Ubuntu24.04 amd64。不是首次安裝、不是日常更新包；INCOMPLETE／無 receipt／未知檔案均停止。不可刪標記或自行編造 receipt。
使用已精確外審並發布後提供的固定入口命令，以 root SSH TTY 操作。現階段私人候選不可宣稱已發布或可從 RMR 執行。首先自行備份 PostgreSQL、管理資料、媒體、產品設定、TLS／ACME；備份保密且在產品目錄以外。工具只備份其精確修復目標，不能代替資料備份。
入口預設 inspect；apply 要再次輸入 REPAIR-AND-ENABLE-VPS-UPDATER。先執行不變的 W1 精確修復，再複驗、啟用不變的 W7；每個子程式另有確認。既有二十碼密碼只能在隱藏 TTY 輸入，不進 argv/env/日誌。W7 會另外確認後將此密碼保存為 root-only systemd LoadCredential，僅伺服器使用；瀏覽器不取得秘密。
私人 W1／W7 原始碼只在 AES-GCM 認證成功後於受控暫存解出，退出後由既有 Supervisor 確認受管程序已退出才清理。必要原生 runtime 在 /opt 的私有 exec 工作區；狀態與明文仍可留 /run，不修改掛載、防火牆或 ACME 權限。初始 Python3.12/venv/CA/curl 必須已存在，入口不安裝 APT 套件。W7 本身會按固定 lock 準備持久更新 runtime。
部分失敗不能盲目重跑 apply。W1 pending 依 W1 固定 Recovery；W7 ENABLE_PENDING 只能用本入口 recover，由 W7 有限恢復 routing，保留證據、runtime、密碼與 pending。不得在 W7 已啟動後自動 W1 rollback。recover 不宣稱完全復原，未知狀態停止人工核對。
啟用後由 Owner 檢查 rm-test status、health、tls-status、續期服務的真實結果；再核對 rm-vps-update socket/service 與正式 cli.py status/check。CLI 路徑為 /opt/rm-vps-update/cli.py，使用 /opt/rm-vps-update/runtime/venv/bin/python -I -B 執行（以固定 W7 實際安裝路徑為準）。空候選只是沒有已發布更新，不是更新成功。
本次不停止 PostgreSQL，不重新建立帳號／TLS／Telegram。WebUI routing 切換可能短暫重連。rm_test 本機後端受信任可經 socket 呼叫有限協定，不代表 daemon 自身驗 browser session。尚未驗真 root:rm_test、systemd/socket/LoadCredential、CA/ACME、noexec 掛載、Owner VPS 或真更新；不得宣稱 ONLINE_UPDATE_ACCEPTED。
信任根沿用 GitHub RMR HTTPS／Ubuntu 系統 CA，沒有帶外簽章。附件保留既有 LICENSES、第三方全文與測試條款；公開入口是必要驗證／解密膠合碼，不公開完整私人產品原始碼。密碼曾在私人 Git／聊天中存在，不保證防離線猜測。
