### 第一步：建立一個 GitHub 儲存庫 (Repository)

- 登入你的 GitHub 帳號。
- 點擊頁面右上角的「+」號，選擇「New repository」。
- Repository name：輸入 my-nodered（或其他你喜歡的名字）。
- Public/Private：強烈建議選 Private（私有），保護你的流程不被外人看見。
- 勾選「Add a README file」（這能讓儲存庫立刻被建立）。
- 點擊「Create repository」。

### 第二步：啟動 Codespace 環境

1. 在你剛剛建立的儲存庫頁面中，點擊綠色的「<> Code」按鈕。
2. 切換到「Codespaces」標籤頁。
3. 點擊「Create codespace on main」。
4. 稍等約 1~2 分鐘，GitHub 會為你開啟一個類似 Visual Studio Code 的網頁編輯器介面。

### 第三步：在終端機安裝並執行 Node-RED

當網頁編輯器載入完成後，你會在下方看到一個「Terminal」（終端機）視窗。請依序輸入以下指令：

1. 安裝 Node-RED：
   ```
   npm install -g --unsafe-perm node-red
   ```
2. 啟動 Node-RED：
   ```
    node-red
   ```

### 第四步：開啟 Node-RED 編輯介面

1. 當 Node-RED 啟動後，終端機會顯示一些文字。GitHub 會自動偵測到 1880 連接埠已開啟。
2. 視窗右下角會彈出一個小視窗提示：「Your application running on port 1880 is available.」。
3. 點擊按鈕「Open in Browser」（在瀏覽器中開啟）。
4. 可以看到熟悉的 Node-RED 流程編輯器了。

### 第五步：重要！如何保存你的資料與節省時數

由於 Codespace 是雲端環境，有幾個關鍵操作你必須知道：

1. 資料持久化：
   - 預設情況下，Node-RED 的資料儲存在 /home/codespace/.node-red。
   - 如果你希望流程永久保存到 GitHub 儲存庫中，建議在 Node-RED 內將 Flow 匯出成 JSON 檔案，然後手動上傳到 GitHub，或是透過終端機進行 git commit。
2. 停止 Codespace（節省額度）：
   - 不要直接關閉網頁視窗！ 這樣時數可能會繼續倒數。
   - 回到 GitHub Codespaces 管理頁面，找到你的 my-nodered 執行個體。
   - 點擊旁邊的三個點「...」，選擇「Stop codespace」。
   - 當你需要再次使用時，回到這裡點擊開啟即可。
3. 連接埠安全性：
   - 在 VS Code 介面下方有個「Ports」標籤。
   - 找到 1880，右鍵點擊 Port Visibility。預設是 Private（只有你能看），這最安全。如果你要讓外部設備（如手機 APP）連進來，才改為 Public。
