# 主題二：Agent 工具應用交流

本主題探討主流 AI Agent 開發工具的橫向對比、使用心法，以及如何將軟體工程思維融入 AI 專案規劃中。

---

## 🧠 主軸 2：AI 專案規劃與實作思維：從痛點走向 AI App Store
本週將進行關鍵思維躍升：從 **AI 工具認識 ➔ AI 工作流 ➔ AI 能力建立**，正式轉向 **AI 專案思維 ➔ AI App 思維 ➔ AI 產品思維**。
我們將透過 **AI App Workshop**，引導同仁將日常工作的「痛點」轉化為「AI App 需求池」，最終匯聚成天心 ERP × FALO AI App Store 的核心資產。

### 產品思維三大支柱
1. **痛點價值定位**：不為 AI 而 AI，必須精準解決高頻、耗時的業務痛點。
2. **零運維與低成本**：設計高性價比的架構（如 Static Web + Serverless），確保企業運行成本最小化。
3. **結構化交付**：將大模型的靈性輸出，轉化為 100% 穩定、符合 ERP 格式要求的 JSON 數據。

---

## 🛠️ 主軸 4：AI 專案所需技能與解析
開發企業級 AI App 不僅僅是寫 Prompt，更需要一套完整的「AI-Native 軟體工程技術棧」：
* **前端與交互**：熟練掌握 HTML5/CSS3 及輕量 Javascript，打造直觀、流暢的用戶界面（如 Swiper 刷題卡片）。
* **API 整合與控制**：精準調用大模型 API（如 Gemini Vision），優化 Prompt 與參數（Temperature, System Instruction）以獲得穩定輸出。
* **規則與清洗引擎 (ETL)**：運用正規表示式（Regex）、狀態機及資料清洗管道，校對並修復大模型輸出的噪聲數據。
* **安全性與防禦**：設計離線快取、CORS 探針、API 金鑰安全控管等防禦性代碼，確保系統在複雜內網環境下穩定運行。

---

## 📊 AI 開發工具對比分析表

| 工具名稱 | 核心定位 | 優勢特色 | 實戰技巧/限制 |
| :--- | :--- | :--- | :--- |
| **Antigravity (AI 程式助理)** | AI Agent 開發與代碼生成 | 專為本機/雲端 Pair Programming 設計，高效率產出高保真代碼 | 善用 Markdown 做為專案記憶與上下文控制，引導 AI 遵循標準 |
| **n8n / GAS** | 企業工作流自動化與 ERP 串接 | 視覺化 Workflow 與 Google 服務無縫串接，適合無程式碼/低程式碼開發 | 可作為 Event-Rule-Action 落地執行的白箱管道，易於快速驗證 |

---

## 🔗 其他參考資源
* [IPAS AIAP 課程網站](https://forceai0001-commits.github.io/ipas-aiap-2026/)：提供歷屆考試資源與 AI 技術學習指引，加深學術與實戰結合。
* [LINE Bot 專業開發專區](https://falo-taiwan.github.io/ai-line-help/)：專家級 LINE 聊天機器人整合實務與 AI 自動對答技巧，提供多元管道輸出示範。
