# 🧪 血清免疫題庫系統

完整的血清免疫學題庫，支援自訂練習題數和類別選擇。

## ✨ 特色功能

- ✅ **完整題庫** - 160題完整血清免疫題目
- 🎯 **自訂練習** - 可選擇題數（10/20/30/50/全部）
- 📂 **類別篩選** - 依照主題分類選擇練習範圍
- 🎲 **隨機排列** - 題目順序和選項位置隨機
- 📚 **完整詳解** - 每題都有詳細解析
- 🖼️ **圖片支援** - 包含螢光染色等圖片題
- 💾 **離線使用** - 使用SQLite資料庫，可完全離線

## 📁 專案結構

```
serology-quiz/
├── index.html              # 主頁面（設定練習）
├── quiz.html              # 答題頁面
├── data/
│   └── questions.db       # SQLite 資料庫
└── README.md              # 說明文件
```

## 🚀 使用方式

### 方法1：GitHub Pages（推薦）

1. Fork 此專案到您的 GitHub 帳號
2. 到 Settings → Pages
3. 選擇 Source: `main` branch
4. 儲存後即可透過 `https://您的帳號.github.io/專案名稱` 存取

### 方法2：本地使用

1. 下載整個專案
2. 使用本地伺服器運行：
   ```bash
   # Python 3
   python3 -m http.server 8000
   
   # Node.js
   npx http-server
   ```
3. 瀏覽器開啟 `http://localhost:8000`

**注意：** 因為使用 `fetch` API，需要透過 HTTP 伺服器運行，直接打開 HTML 檔案會有 CORS 錯誤。

## 📊 資料庫結構

### questions 表格

| 欄位 | 類型 | 說明 |
|------|------|------|
| id | INTEGER | 主鍵 |
| question_number | INTEGER | 題號 |
| category | TEXT | 類別 |
| question_id | TEXT | 題目ID |
| question_text | TEXT | 題目內容 |
| option_a | TEXT | 選項A |
| option_b | TEXT | 選項B |
| option_c | TEXT | 選項C |
| option_d | TEXT | 選項D |
| correct_answer | TEXT | 正確答案（A/B/C/D） |
| explanation | TEXT | 詳細解析 |
| image_base64 | TEXT | Base64圖片（選填） |

### 題目類別

- 基礎免疫機制
- T細胞免疫
- B細胞與抗體
- 先天免疫與補體
- 自體免疫疾病
- 過敏反應
- 感染免疫
- 實驗技術
- 器官移植
- 腫瘤免疫

## 🛠️ 技術架構

- **前端框架**: 純 HTML + CSS + JavaScript
- **資料庫**: SQLite (透過 SQL.js 在瀏覽器中運行)
- **資料儲存**: LocalStorage (儲存用戶設定)
- **CDN**: SQL.js from cdnjs.cloudflare.com

## 💡 功能說明

### 首頁 (index.html)
- 選擇練習題數
- 選擇題目類別
- 顯示題庫統計資訊

### 答題頁 (quiz.html)
- 隨機顯示選定的題目
- 隨機排列選項順序
- 顯示/隱藏答案功能
- 查看詳細解析
- 上一題/下一題導覽
- 鍵盤快捷鍵支援（← →）

## 🔧 開發與修改

### 新增題目

1. 開啟 `data/questions.db`
2. 使用 SQLite 工具（DB Browser for SQLite 等）
3. 在 `questions` 表格新增資料
4. 或使用 Python 腳本批次匯入

範例 Python 腳本：

```python
import sqlite3

conn = sqlite3.connect('data/questions.db')
cursor = conn.cursor()

cursor.execute('''
    INSERT INTO questions 
    (question_number, category, question_text, 
     option_a, option_b, option_c, option_d, 
     correct_answer, explanation)
    VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?)
''', (
    161,  # 題號
    "類別名稱",
    "題目內容",
    "選項A",
    "選項B",
    "選項C",
    "選項D",
    "D",  # 正確答案
    "詳細解析"
))

conn.commit()
conn.close()
```

### 修改樣式

編輯 `index.html` 和 `quiz.html` 中的 `<style>` 區塊。

### 自訂功能

主要 JavaScript 函數位於：
- `index.html` - 設定頁面邏輯
- `quiz.html` - 答題頁面邏輯

## 📝 授權

本專案僅供教育學習使用。題目內容版權歸原作者所有。

## 🤝 貢獻

歡迎提交 Issue 和 Pull Request！

### 貢獻指南

1. Fork 專案
2. 建立功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交變更 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 開啟 Pull Request

## 📮 聯絡方式

如有問題或建議，請開啟 Issue 或聯絡維護者。

## 🔄 更新日誌

### v1.0.0 (2025-10-25)
- ✨ 初始版本發布
- 🎯 支援自訂題數和類別選擇
- 📊 完整160題題庫
- 🖼️ 圖片題目支援

---

Made with ❤️ for medical students
