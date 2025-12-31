Serv00 (目前最強的免信用卡虛擬主機)
這是一家波蘭的免費主機商，提供 SSH 權限、自定義連接埠與 Node.js 支援，最重要的是：資料會永久儲存。</br>
優點：完全免費、免信用卡、資料不丟失、支援 24 小時運作。</br>
申請網址：serv00.com</br>

# 第一階段：Serv00 面板基礎設定
在登入 Serv00 管理面板 後，需先開啟權限：</br>
1. 開啟 Node.js 支援：
  - 點選左側選單的 Additional services -> Permissions。
  - 找到 Node.js，確保狀態為 Enabled。
2. 預留通訊埠 (Port Reservation)：
  - Node-RED 預設的 1880 在共享主機上通常不能用，必須申請一個專屬 Port。
  - 點選 Port reservation -> Add port。
  - 選擇 TCP，系統會隨機分配一個號碼（例如 12345），請記下這個號碼。

# 第二階段：透過 SSH 安裝 Node-RED
使用電腦的終端機（或 PuTTY）登入你的 Serv00：</br>
ssh 你的帳號@你的伺服器地址 (例如 s1.serv00.com)</br>
登入後執行以下指令：</br>
1. 安裝 Node-RED：
   ```
   npm install -g node-red
   ```
2. 初次啟動測試： 使用你剛剛申請到的 Port 啟動（假設是 12345）：
   ```
   node-red --port 12345
   ```

# 第三階段：達成「不間斷運作」 (使用 PM2)
在 Linux/FreeBSD 伺服器上，直接執行指令只要視窗關閉程式就會停止。我們需要 PM2 這個管理工具來讓它在後台跑，並在當掉時自動重啟。</br>
1. 安裝 PM2：
   ```
   npm install -g pm2
   ```
2. 使用 PM2 啟動 Node-RED：
   ```
   pm2 start node-red -- --port 12345
   ```
3. 儲存狀態：
   ```
   pm2 save
   ```
# 第四階段：防止伺服器重啟後失效 (Cron Job)
Serv00 有時會重啟伺服器，我們可以設定一個定時任務，每隔一段時間檢查 Node-RED 是否在跑，或是開機時自動啟動。</br>
1. 在面板點選 Cron jobs -> Add cron job。
2. Command 填入 PM2 的路徑（通常是 /home/你的帳號/.npm-global/bin/pm2 resurrect）。
3. Time 選擇 Reboot。

# Serv00 使用提醒
- 資源限制：Serv00 對記憶體與 CPU 有一定限制，Node-RED 裡面建議不要裝太多肥大的節點。
- 安全性：同樣的，因為是公網 IP，請務必修改 ~/.node-red/settings.js 設定管理員密碼。
- 網址存取：你可以透過 http://你的帳號.serv00.net:你的Port 來存取。







