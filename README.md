# 動物節奏挑戰 (Beats Challenge)

一個基於節拍的互動式節奏挑戰遊戲，玩家需要跟著音樂節拍進行挑戰。支援自訂音樂、挑戰內容，並提供電子鼓聲作為背景音樂。
當前可由此網頁進行使用：https://beats-challenge.hi-changyc.workers.dev/

## 🎮 遊戲特色

- **節拍同步系統**：精確的節拍檢測與視覺化提示
- **自訂音樂支援**：可上傳 MP3 音樂檔案或使用預設挑戰音樂
- **電子鼓聲生成**：使用 Web Audio API 即時生成電子鼓聲
- **多關卡挑戰**：共 5 個關卡，難度逐漸提升
- **自訂挑戰內容**：可設定名稱與圖片，支援圖片上傳或連結輸入
- **靈活設定**：可調整 BPM、預備拍數、組間過渡拍數等參數
- **響應式設計**：使用 Tailwind CSS 打造現代化 UI

## 📋 功能說明

### 音樂設定
- **預設挑戰音樂**：使用內建的 BPM 183 挑戰音樂（鎖定相關設定）
- **自訂音樂上傳**：支援上傳 MP3 格式音樂檔案
- **電子鼓聲**：未提供音樂時，系統會自動產生電子鼓聲作為節拍提示

### 遊戲設定
- **開頭預備拍數**：遊戲開始前的倒數拍數（預設：12 拍）
- **組間過渡拍數**：關卡之間的過渡拍數（預設：8 拍）
- **遊戲速度 (BPM)**：節拍速度，範圍 60-240 BPM（預設：183 BPM）

### 挑戰內容設定
- 可設定最多 8 組挑戰內容
- 每組包含：
  - **名稱**：顯示在卡片上的文字
  - **圖片**：可上傳本地圖片或輸入圖片連結
- 支援清除所有填寫內容功能

### 遊戲流程
1. **預備階段**：顯示倒數拍數，幫助玩家準備
2. **挑戰階段**：卡片會根據節拍高亮顯示，玩家需跟著節奏
3. **關卡進度**：共 5 個關卡，每關會隨機選擇挑戰內容
4. **完成挑戰**：完成所有關卡後顯示結算頁面

## 🚀 快速開始

### 本地運行

1. 克隆或下載專案
2. 使用任何靜態文件伺服器開啟 `index.html`

```bash
# 使用 Python
python -m http.server 8000

# 或使用 Node.js http-server
npx http-server

# 或使用 PHP
php -S localhost:8000
```

3. 在瀏覽器中開啟 `http://localhost:8000`

### 部署到 Cloudflare Workers

專案包含 `wrangler.jsonc` 設定檔，可部署到 Cloudflare Workers：

```bash
# 安裝 Wrangler CLI
npm install -g wrangler

# 登入 Cloudflare
wrangler login

# 部署
wrangler deploy
```

## 📁 專案結構

```
BeatsChallenge/
├── index.html              # 主程式檔案（包含 HTML、CSS、JavaScript）
├── BeatsChallenge_bpm183.mp3  # 預設挑戰音樂
├── wrangler.jsonc         # Cloudflare Workers 設定檔
└── README.md              # 本說明文件
```

## 🛠️ 技術棧

- **HTML5**：結構標記
- **CSS3**：自訂動畫與樣式
- **JavaScript (ES6+)**：遊戲邏輯與互動
- **Web Audio API**：音訊處理與電子鼓聲生成
- **Tailwind CSS**：透過 CDN 引入的 CSS 框架

## 🎯 核心功能實現

### 節拍系統
- 使用 `AudioContext` 進行精確的時間調度
- 透過 `scheduler()` 函數實現節拍循環
- 視覺化節拍提示（卡片高亮動畫）

### 電子鼓聲生成
- **大鼓 (Kick Drum)**：使用振盪器產生低頻音效
- **小鼓 (Snare Drum)**：使用白噪音與濾波器模擬

### 圖片預載入
- 自動預載入所有挑戰圖片
- 顯示載入進度百分比
- 使用快取機制避免重複載入

## 🎨 自訂設定

### 修改預設挑戰內容

在 `index.html` 中找到 `defaultItems` 陣列，可修改預設的挑戰內容：

```javascript
const defaultItems = [
    { name: "豬", url: "圖片連結" },
    { name: "狗", url: "圖片連結" },
    // ... 更多項目
];
```

### 調整遊戲參數

- `CARDS_PER_LEVEL`：每關卡片數量（預設：8）
- `startPrepBeats`：開頭預備拍數（預設：12）
- `levelGapBeats`：組間過渡拍數（預設：8）
- `bpm`：遊戲速度（預設：183）

## 🌐 瀏覽器相容性

- Chrome/Edge（推薦）
- Firefox
- Safari
- 需要支援 Web Audio API 的現代瀏覽器

## 📝 使用注意事項

1. **音樂檔案格式**：僅支援 MP3 格式
2. **圖片格式**：支援常見圖片格式（JPG、PNG、GIF 等）
3. **最少挑戰內容**：需要至少設定 4 組挑戰內容才能開始遊戲
4. **瀏覽器權限**：首次使用時，瀏覽器可能會要求音訊播放權限

## 🐛 已知問題

- 某些瀏覽器需要使用者互動後才能播放音訊
- 圖片載入失敗時會顯示文字替代

## 📄 授權

本專案為開源專案，可自由使用與修改。

## 🤝 貢獻

歡迎提交 Issue 或 Pull Request！

---

**注意**：此說明文件由 AI 生成

