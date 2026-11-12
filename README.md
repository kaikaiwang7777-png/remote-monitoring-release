# Remote Monitoring VPS（RMR）

VPS 管理介面、Backend 與更新器的固定版本發布入口。以下為 Pre-release（測試版），下載核驗及隔離測試不代表您的主機已驗收。

| 用途 | 固定版本 |
|---|---|
| 已有健康 v0.1.24 的 WUI 更新 | [RMR-v0.1.25-prerelease.20261112.1](https://github.com/kaikaiwang7777-png/remote-monitoring-release/releases/tag/RMR-v0.1.25-prerelease.20261112.1) |
| 乾淨 VPS 完整安裝 | [RMR-v0.1.25-prerelease.20261112.2](https://github.com/kaikaiwang7777-png/remote-monitoring-release/releases/tag/RMR-v0.1.25-prerelease.20261112.2) |
| 配套 Windows 資源 | [RMW-v0.1.3-prerelease.20261109.1](https://github.com/kaikaiwang7777-png/remote-monitoring-windows-release/releases/tag/RMW-v0.1.3-prerelease.20261109.1) |

兩種 RMR 包用途不同：WUI 更新不需要為了安裝互動改善而重裝；Fresh 不能當作 app-only 更新包。其他已安裝版本須依 WUI 顯示的實際相容條件選版，不自行跳過必要橋接。

## 乾淨安裝

需要乾淨 Ubuntu 24.04 x86_64、sudo/root 與互動終端，可信的系統時間、DNS、CA 及 Ubuntu APT。必須可連線到固定 GitHub 資源與憑證服務；公網 HTTPS 使用 8443 和 HTTP-01 所需 TCP80，安裝器不替您更改防火牆或 NAT。既有資料的保存及是否重置由主機管理員決定，請勿在不明目錄殘留上刪檔強裝。

完整複製下列一行至終端。此固定入口為 39,795 bytes，SHA256 `124a158ee485db49fed3c6a4a50a9fefc54ae618effa0a61ba0ba736bb610c54`；命令先檢查 HTTP、大小及 SHA256 才執行，不使用 latest、PAT 或未驗證的 curl 管線。

```sh
sudo /bin/sh -c 'set -eu; umask 077; [ "$(uname -s)" = Linux ] && [ "$(uname -m)" = x86_64 ]; . /etc/os-release; [ "$ID" = ubuntu ] && [ "$VERSION_ID" = 24.04 ]; [ -t 0 ]; command -v curl >/dev/null && test -s /etc/ssl/certs/ca-certificates.crt && command -v python3 >/dev/null || { apt-get update || exit; apt-get -y --no-install-recommends install curl ca-certificates python3 || exit; }; f=$(mktemp); trap '"'"'rm -f "$f"'"'"' 0; h=$(curl -fLsS --proto =https --proto-redir =https --max-redirs 3 --max-time 60 --max-filesize 39795 -w "%{http_code}" -o "$f" https://github.com/kaikaiwang7777-png/remote-monitoring-release/releases/download/RMR-v0.1.25-prerelease.20261112.2/bootstrap-v0.1.25.sh); [ "$h" = 200 ]; [ "$(wc -c < "$f")" -eq 39795 ]; printf "%s  %s\n" 124a158ee485db49fed3c6a4a50a9fefc54ae618effa0a61ba0ba736bb610c54 "$f" | sha256sum -c -; /bin/sh "$f"'
```

依精靈提供安裝包解密密碼、必要 HTTPS 授權、管理員帳號及密碼。此版本預設公網 HTTPS／8443／自動核對 IPv4／admin；密碼單次輸入可按 F2 顯示或隱藏。明確閱讀 HTTPS 條款與最後安裝範圍確認，不要把空白、取消或 EOF 當同意。解密密碼與後續 RMR 更新使用同一安全用途的秘密；WUI 管理員密碼另設，不要放到命令或公開日誌。入口會自動取得並驗證配套 RMR／RMW，不需手工搬運 ZIP。

完成後以正常可信 HTTPS 開啟顯示的 WUI 位址，核對安裝與運行版本、服務健康及管理器就緒；下載成功不等於安裝成功。

## Windows 與更新

Windows 使用者從 WUI「設備註冊」選數量、產生並複製每台獨立指令，詳見 [RMW 使用說明](https://github.com/kaikaiwang7777-png/remote-monitoring-windows-release)。公開 ZIP 本身不授予安裝、註冊或上線權限。

現有健康 v0.1.24：到「系統更新」檢查並選擇 `RMR-v0.1.25-prerelease.20261112.1`，準備驗證完成後明確確認安裝。確認當前與運行版本一致、沒有未釐清的 Job，並自行評估備份及可恢復條件。結果 FAILED／UNKNOWN／RECOVERY_REQUIRED 時只查原工作，不盲目重送。手動回退只選 WUI 提供且已保留、完整、相容的可信候選；不是任意資料庫降版或直接修改 Current 指向。

## 常見問題

- 找不到版本：確認設定已成功讀取及允許測試版；不要把讀取失敗當成沒有更新。
- TLS、來源、大小、SHA、簽章或容量檢查失敗：停止並保存安全錯誤碼，不能略過驗證。
- 指令無法重顯：一次性秘密只在首次成功回覆提供；歷史查詢不會重建。未知結果先查原申請，不清瀏覽器紀錄或重發。
- 安裝紀錄已送達但未上線：安裝、註冊、啟用及 heartbeat 是不同結果，需分別確認。

本次公開讀回已核對 8 個成對附件及固定下載位置，原下載器 RMR/RMW 取得通過；Fresh 測試在執行安裝前攔截，未代表真 Ubuntu 安裝、ACME、Windows 或 Owner 現場驗收。README 的公開更新不改動舊版附件或安全契約。
