20260104

##### 需確認本機已安裝python，以local為例，

`python -V`
為Python 3.12.0

`where python`

為C:\Users\user\AppData\Local\Programs\Python\Python312\python.exe

##### 新增 yfinance pandas_ta pandas

`pip install yfinance pandas_ta pandas`

##### 安裝節點：

安裝 `node-red-contrib-pythonshell`。

![1767522905557](https://file+.vscode-resource.vscode-cdn.net/d%3A/ytlLab/localTest/YTNodeRed/image/README/1767522905557.png)

##### 強制修改 JSON 代碼 (解決反灰問題)

1. 在 Node-RED 畫布上，按住滑鼠左鍵選取您的 **`計算 KD/RS`** 節點。
2. 按下鍵盤快速鍵  **`Ctrl + E`** （匯出），會彈出一個包含 JSON 程式碼的視窗。
3. 在程式碼中找到這兩行：
   * 將 `"continuous": true,` 修改為 **`"continuous": false,`**
   * 確保 `"stdInData": true,` 保持不變。
4. 點擊右下角的 **[Import] (匯入)** 按鈕。
5. 此時畫布上會出現一個「新」的節點，請用它**取代**原本那個反灰的舊節點，並重新連線。
6. 最後點擊右上角的  **[Deploy]** 。

##### 更新 Python 套件

請開啟您的  **CMD (命令提示字元)** ，執行以下指令更新 `yfinance` 和 `pandas-ta`。新版本修復了無法抓取台股數據的 Bug：

如果您使用的是全域 Python

`pip install -U yfinance pandas-ta pandas`
