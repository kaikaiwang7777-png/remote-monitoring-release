# Remote Monitoring VPS 測試版
版本 v0.1.0-vps.rc.20261023.4；Ubuntu24.04 amd64，以root SSH終端使用經核准交付的一行命令。
可執行命令由封裝完成後的固定交付資料提供；未發布及匿名驗算前不可宣稱可用。本說明不嵌入入口自身的hash/命令，以避免entry→說明→Manifest→entry的自引用。

首次信任為GitHub RMR官方HTTPS與Ubuntu系統CA，沒有獨立帶外驗證或Ed25519。外層命令必須完整下載、HTTP200、精確entry大小及SHA256全部相符後才交sh；短檔、長檔、同大小錯hash、非200或redirect均停止並清理暫存。固定commit/版本root再驗後續Manifest/來源/大小/SHA256，AES256GCM完整認證後才提取並進原精靈。Tag不可移動/覆寫；GitHub/CA及本機root遭控制不在保證內。
Owner已接受此測試密碼曾存在私人Git/聊天的風險，不宣稱高強度秘密隔離或防離線猜測。公開附件不含密碼；隱藏TTY輸入，不接受argv/env。
初始可信UbuntuAPT可能準備curl/CA/Python與臨時runtime（/opt/rm-exec-*，0700且實際檢查exec掛載；/run仍保留kit/明文/狀態且不改noexec）；runtime由原Supervisor確認受管程序退出後清理，無法確認則保留並非零退出。原精靈再確認後才改PostgreSQL16、DB、/opt/rm-test、管理員、HTTPS/WebUI/systemd。錯誤/取消停止後續job並由原Supervisor確認退出再清理；OS前置套件可能保留，不保證rollback、secure erase或SIGKILL零殘留，不自動恢復/刪除舊殘留。
本新版只更新安裝器/TLS管理，後端/WebUI/SQL位元不變；因此重新密封必要的安裝payload，仍沿用既有Argon2id/AES-GCM格式。新增模式3公網IPv4 Let’s Encrypt shortlived；模式2可用既有有效憑證或自動申請。自動模式需官方snap stable Certbot>=5.4與公網80/8443，安裝器不改防火牆。安裝receipt/TLS policy/完成狀態提交後才啟用每小時續期timer；建立或啟用失敗只清理本次inode/內容可確認的unit，不刪既有設定。續期驗證鏈/SAN、實際服務leaf與WebUI健康；失敗保留舊代憑證，切換失敗恢復舊config。管理rm-test tls-status/tls-switch/tls-renew/tls-recover。沒有真CA/Staging/VPS安裝驗收；需操作者確認ACME條款及公網端口。這是未完成全產品驗收的VPS測試版；inert證據不是實機Ubuntu安裝、Windows/media/TG驗收。第三方全文見THIRD_PARTY_NOTICES.txt、對照見LICENSES.json；客戶另取wheel/APT不是本包重散布附件。
