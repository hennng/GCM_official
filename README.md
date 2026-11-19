# GCM 領唱練習儀表板

## 檔案
- `index.html`：儀表板（上傳到 GitHub 儲存庫根目錄，覆蓋舊檔）
- `firestore.rules`：Firestore 規則（貼到 Firebase 控制台）
- `gcm-firestore-data.json`、`gcm-import-console.js`：現有資料與一次性匯入程式（之前已提供）

## 一次性設定（Firebase 專案 gcmofficial）
1. **Authentication → 登入方式**：啟用 Google。
2. **Authentication → 設定 → 授權網域**：加入 `hennng.github.io`。
3. **Firestore Database → 規則**：全選刪除，貼上 `firestore.rules` 全部內容並「發布」。
   - 管理者信箱在 `isEditor()` 裡，必須全小寫；要新增管理者，在中括號內加逗號與信箱。
4. 更新規則後，在儀表板登出再重新登入。

## 上線
1. GitHub 儲存庫 → `index.html` → 鉛筆圖示 → 貼上新內容 → Commit changes。
2. 等 1～2 分鐘，用 Cmd/Ctrl＋Shift＋R 強制重新整理。
3. 登入成功且是管理者，右上角會顯示「管理者：您的信箱」，並出現「管理」頁籤。

## 匯入既有資料（只需一次）
登入管理者帳號後，按 F12 → Console，輸入 `allow pasting`，貼上 `gcm-import-console.js` 的內容後 Enter。

## 資料結構（Firestore）
events／members／songs／sessions／logs 為一般文件；
attendance 文件 ID 為 `場次ID__團員ID`；scores 文件 ID 為 `團員ID__曲目ID`。

## 備註
- `apiKey` 寫在網頁中是 Firebase 網頁版的正常做法，GitHub 的「Public leak」警告可視為誤報；
  建議在 Google Cloud Console 把金鑰限制為 `https://hennng.github.io/*`。
- 目前資料為「所有人可讀」。若要限制只有團員能看，需改為登入後才可讀取，並維護團員名單。
