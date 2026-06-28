# 🐟 青魚 PWA 模板

> 脆上搜尋「青魚大師」取得更多資源

一個可以直接套用的 PWA（漸進式網頁應用程式）模板，任何人都能 Fork 後部署到 GitHub Pages，5 分鐘內擁有自己的 App！

---

## ✨ 功能特色

- 📲 支援加入主畫面（iOS / Android / Desktop）
- ⚡ 離線快取，無網路也能開啟
- 🎨 容易自訂，替換內容不需要學 PWA 原理
- 📱 自動偵測 Android / iOS 並顯示對應安裝引導
- 🐟 底部固定版權聲明（請勿移除）

---

## 🚀 快速開始：5 分鐘部署教程

### 第一步：Fork 這個專案

1. 點右上角 **Fork** 按鈕
2. 選擇你的 GitHub 帳號
3. 按 **Create fork**

> 不知道什麼是 Fork？Fork 就是把別人的程式碼複製一份到你的帳號，你可以自由修改。

---

### 第二步：開啟 GitHub Pages

1. 進入你 Fork 後的倉庫
2. 點上方 **Settings**（齒輪圖示）
3. 左側找到 **Pages**
4. 在「Branch」下拉選單選 **main**，資料夾選 **/ (root)**
5. 按 **Save**

等待約 1～2 分鐘，頁面上會出現你的網址：

```
https://你的帳號名稱.github.io/倉庫名稱/
```

用手機開啟這個網址，就能看到你的 PWA 了！

---

### 第三步：自訂你的內容

用 GitHub 網頁直接編輯，不需要安裝任何軟體。

**編輯 `index.html`：**

1. 在你的倉庫點 `index.html`
2. 點右上角的 ✏️ 鉛筆圖示
3. 找到以下區塊，替換你自己的內容：

```html
<!-- ============================================================
  ✏️ 使用者內容區：自由替換以下 HTML
============================================================ -->
```

4. 修改完後，往下滾，按 **Commit changes**

> ⚠️ 注意：不要刪除 `#qy-footer` 區塊，那是版權聲明。

---

### 第四步：修改 App 名稱與主題色

**改 App 名稱（加入主畫面後顯示的名稱）：**

編輯 `manifest.json`，修改以下兩行：

```json
"name": "你的App名稱",
"short_name": "你的App名稱",
```

> `name` 是完整名稱，`short_name` 是主畫面顯示的短名（建議 6 個字以內）

**改主題色：**

在 `index.html` 的 `<style>` 裡找到：

```css
:root {
  --brand: #0066CC;       /* 主色，改成你喜歡的顏色 */
  --brand-dark: #004d99;  /* 深色版，通常比主色深一點 */
  --brand-light: #e6f0ff; /* 淡色版，用於背景 */
}
```

同時修改 `manifest.json` 裡的：

```json
"background_color": "#ffffff",
"theme_color": "#0066CC"
```

---

### 第五步：換上你自己的 App 圖示（選用）

替換 `icons/` 資料夾裡的圖片：

| 檔案 | 尺寸 | 用途 |
|------|------|------|
| `icon-192.png` | 192×192 px | Android 主畫面圖示 |
| `icon-512.png` | 512×512 px | 啟動畫面 / 商店圖示 |

> 建議使用正方形 PNG，背景可透明也可實色。

---

## 📁 檔案結構說明

```
qingyu-pwa/
├── index.html        ✏️ 主頁面，修改這裡來自訂內容
├── manifest.json     ✏️ App 名稱、顏色、圖示設定
├── sw.js             ⚙️ Service Worker（離線快取，勿大改）
├── icons/
│   ├── icon-192.png  🖼️ App 圖示 192px
│   └── icon-512.png  🖼️ App 圖示 512px
└── README.md         📖 本說明文件
```

---
補充
用 Netlify 部署的方法
如果不想用 GitHub Pages，Netlify 也是免費又簡單的選擇，網址會是 你取的名字.netlify.app。

方法一：直接拖曳資料夾（最快，不需要帳號以外的操作）

把 Fork 下來的專案下載到電腦（GitHub 上點 Code → Download ZIP，解壓縮）
前往 netlify.com 並登入（可用 GitHub 帳號登入）
進入 Dashboard 後，把整個資料夾直接拖曳到頁面中間的拖曳區
等幾秒，Netlify 會自動產生一個網址，部署完成


方法二：連結 GitHub 倉庫（推薦，之後改程式碼會自動更新）

前往 netlify.com 並登入
點 Add new site → Import an existing project
選 Deploy with GitHub，授權後選你 Fork 的倉庫
設定保持預設即可，直接點 Deploy site
部署完成後會給你一個網址

之後只要在 GitHub 上修改檔案，Netlify 會自動重新部署，不需要手動操作。

修改 Netlify 網址
預設網址是一串亂碼，可以改成自訂名稱：

進入 Netlify 的 Site settings
點 Change site name
輸入你想要的名稱（如 my-app），網址就會變成 my-app.netlify.app


注意事項

網址必須是 https:// 開頭，PWA 功能才能正常運作，Netlify 預設就是 https，不需要額外設定
免費方案每月有流量限制，個人使用完全夠用

## 🤔 常見問題

**Q：為什麼加入主畫面後打開是空白？**  
A：GitHub Pages 部署需要 1～2 分鐘生效，稍等再試。也確認網址是 `https://` 開頭。

**Q：iOS 上沒有出現「加入主畫面」提示？**  
A：iOS 不支援自動彈出提示，要手動操作：Safari 開啟網址 → 點底部分享按鈕 ⬆ → 選「加入主畫面」。App 內已有說明引導。

**Q：Android 上沒有出現安裝提示？**  
A：確認使用 Chrome 瀏覽器，且網址是 `https://`。有時候需要多訪問幾次才會出現。

**Q：我可以加自己的頁面或功能嗎？**  
A：可以！在 `index.html` 的「使用者內容區」自由新增 HTML、CSS、JavaScript。你也可以新增多個 `.html` 檔案，做成多頁應用。

**Q：底部那個「脆上搜尋青魚大師」可以拿掉嗎？**  
A：不行，這是使用本模板的條件，請保留版權聲明。

---

## 📋 使用條款

- ✅ 可免費用於個人及商業用途
- ✅ 可自由修改頁面內容與外觀
- ❌ 不得移除或隱藏底部版權聲明（`#qy-footer`）
- ❌ 不得聲稱本模板為自己原創

---

## 🐟 關於青魚大師

更多免費模板、教程與資源，脆上搜尋「**青魚大師**」！

---

*Made with 🐟 by 青魚大師*
