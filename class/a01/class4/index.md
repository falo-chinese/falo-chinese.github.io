# Class 04 企業級 AI Agent 自動化實戰：重點補充、專案診斷與工具解析 (index.md)

前三週還有部分內容尚未完整說明，本週將安排重點補充與回顧，並開放 QA 討論。希望能協助大家完成謝總交代的功課，也透過彼此交流與問題討論，加深對 AI 工具、方法與實務應用的理解與印象。課程內容以工作上的應用為主，但加速個人日常運用的也是可以～

---

## 課程資訊
* 📅 **上課時間**：2026/06/28 (日) 09:00-12:00 (暫定)
* 👨‍🏫 **授課教師**：鄭穎臨 老師
* 📍 **上課地點**：台南市安平區育平九街49號 二樓教室
* 🔑 **課程簡報**：課前另行公佈 (🔒 密碼：attn)

---

## 📌 常見提醒與交付規範 (台灣時間 UTC+8)
> [!IMPORTANT]
> 本課程與專案之所有宣告、作業交付截止日期等時間，皆**統一宣告並以台灣時間 (UTC+8) 為唯一準則**。

* 📄 **雙軌標準規範 (md + html)**: 所有提問集、作業及大綱，必須同時提交 **Markdown (.md)** 檔（供 AI/LLM 結構理解）與 **HTML (.html)** 網頁檔（供人類閱讀），落實雙軌並行標準。
* 📦 **壓縮包命名習慣 (ZIP 檔案)**: 凡提交程式碼或專案資源壓縮包時，請遵循 **「[時間戳記]_[重要更新事項].zip」** 命名規範（例如：`20260622_class04_project.zip`）。

---

## 實戰專案與進階手冊
* 🔗 **FALO 企業環境部署評估與網關相容性矩陣 (Deployment Assessment)**：[FALO 企業環境部署評估與網關相容性矩陣 (Deployment Assessment)](deployment-assessment.html) - 專為售前顧問、架構師與項目經理（PM）設計的標準評估工具。支援 100% 離線運行、no-cors 網際網路 TCP 握手探測，可一鍵檢測 50+ 網域連線，並支持 HTML/JSON 報告還原匯入與 Excel 無亂碼 CSV 匯出。
* 🔗 **FALO 企業環境部署評估矩陣：專案建置與技術教學講義 (TEACHING_NOTES)**：[FALO 企業環境部署評估矩陣：專案建置與技術教學講義 (HTML)](TEACHING_NOTES.html) | [Markdown](TEACHING_NOTES.md) - Force 課程教學專用講義與實戰踩坑筆記，拆解 no-cors 網路探針、DNS NXDOMAIN 假性阻擋排查、HTML 數據備份與版權浮水印防護等高級 Vibe Coding 開發觀念。

---

## 教學核心主軸

### 主軸 1：前三週重點補充與問題解答 (重點補充 / 問題解答)
針對前三堂課中尚未完整說明的核心觀念與技術細節進行補充，解答學員在實作中遇到的疑難雜症。

### 主軸 2：AI 專案規劃與實作思維：從痛點走向 AI App Store (專案規劃 / 實作思維)

本週將進行關鍵思維躍升：從 **AI 工具認識 ➔ AI 工作流 ➔ AI 能力建立**，正式轉向 **AI 專案思維 ➔ AI App 思維 ➔ AI 產品思維**。我們將透過 **AI App Workshop**，引導同仁將日常工作的「痛點」轉化為「AI App 藍圖」，最終匯聚成天心 ERP 的核心資產。

#### 🎯 痛點轉化矩陣：把「很煩的事」變成 AI App
不要直接問「你想做什麼 App？」而是問：「工作上有哪些事情讓你覺得很煩、很花時間、很容易出錯？」

| 日常工作痛點 (很煩/花時間/易出錯) | 對應的 AI App 解法 | 技術核心 |
| :--- | :--- | :--- |
| **找資料很久、翻文件像在大海撈針** | **AI 知識庫助手 (RAG)** | Vector DB + LLM 語意檢索 |
| **每天整理/回覆大量 Email 與交辦事項** | **AI Email 助理** | LLM 意圖識別 + 自動草擬 |
| **客戶/內部同仁一直問重覆度極高的問題** | **AI 客服/諮詢助手** | Prompt 角色扮演 + 知識庫 |
| **手動整理多份報表、寫分析結論很痛苦** | **AI 報表分析助手** | Structured Data Analyst (Python) |
| **手工輸入單據到 ERP，耗時且容易打錯字** | **AI OCR 轉單助手** | Layout-free OCR + ETL 欄位清洗 |
| **專案進度卡在跨部門溝通、一直花時間追進度** | **AI PM 助理 (Agent)** | Multi-Agent 協作 + 定時追蹤 |
| **業務在外要查庫存，得打電話或登入複雜系統** | **AI 庫存查詢助手** | Natural Language to SQL (NL2SQL) |
| **主管要看經營數據，但臨時報表拉不出來** | **AI Dashboard 數據分析師** | Auto Chart Generation + 語意摘要 |

#### 🏫 AI App Workshop 三階段設計
1.  **第一階段：痛點盤點**
    每位同仁盤點自身工作流程，具體列出：
    *   **3 個最痛苦** 的工作（心理負擔重）
    *   **3 個最浪費時間** 的工作（重複機械勞動）
    *   **3 個最常出錯** 的工作（需高度專注防錯）
2.  **第二階段：AI 能力分類**
    評估痛點是否適合用 AI 解決，並將解法歸類：
    *   **查詢類 / 分析類**：語意檢索與數據摘要
    *   **預測類 / 預警類**：趨勢預估與異常交易攔截
    *   **辨識類 / 自動化類**：非結構化文件辨識與跨系統串接
3.  **第三階段：規劃 AI App 地圖**
    將解法分流並歸納入 **AI App Store 產品藍圖**：
    *   **查詢/分析類**：庫存、客戶、銷售、採購、財務
    *   **辨識/預警類**：OCR 轉單、合約審查、異常交易預警
    *   **Agent 類**：Email Agent、LINE Agent、ERP Agent

> [!TIP]
> **💡 終極目標：建立「天心 ERP AI App Backlog (需求池)」**
> 透過本次 Workshop，我們收穫的將不僅僅是一堂課的知識，而是一份真實且具商業價值的**天心 ERP AI App Backlog (需求池)**。
> 這份清單將清晰呈現：**市場的真實渴望、同仁遇到的高頻痛點、哪些模組最常重複被需要。** 
> 這將直接轉化為 **「天心 ERP × FALO AI App Store」** 的產品藍圖，引領產品走向下一代 AI 原生升級！

#### 🎯 AI APP Studio：從創意到 AI 產品實作套件
我們為您整理了從**痛點掃描、需求解剖、優先級決策到 MVP 驗證**的完整方法論與實作工具包（同時提供 Markdown 與 HTML 雙軌版）：

* 📖 **工作坊總覽首頁**：[HTML (ai_app_readme.html)](ai_app_readme.html) | [Markdown (ai_app_readme.md)](ai_app_readme.md)
* 🧠 **產品思維方法論**：[HTML (methodology_blueprint.html)](methodology_blueprint.html) | [Markdown (methodology_blueprint.md)](methodology_blueprint.md)
* 🔍 **痛點與需求驗證手冊**：[HTML (discovery_validation_playbook.html)](discovery_validation_playbook.html) | [Markdown (discovery_validation_playbook.md)](discovery_validation_playbook.md)
* 📋 **50+ AI App 創意 Backlog**：[HTML (backlog_template.html)](backlog_template.html) | [Markdown (backlog_template.md)](backlog_template.md)
* 💡 **100+ AI App 創意庫**：[HTML (idea_library.html)](idea_library.html) | [Markdown (idea_library.md)](idea_library.md)
* 📊 **100分制評審與決策表**：[HTML (scorecard.html)](scorecard.html) | [Markdown (scorecard.md)](scorecard.md)
* 🚀 **MVP & PoC 規劃指南**：[HTML (mvp_poc_guide.html)](mvp_poc_guide.html) | [Markdown (mvp_poc_guide.md)](mvp_poc_guide.md)
* 📝 **學員實作工作紙**：[HTML (student_worksheets.html)](student_worksheets.html) | [Markdown (student_worksheets.md)](student_worksheets.md)
* 👨‍🏫 **講師引導指南**：[HTML (workshop_facilitator_guide.html)](workshop_facilitator_guide.html) | [Markdown (workshop_facilitator_guide.md)](workshop_facilitator_guide.md)
* 📂 **歷程記錄**：[HTML (project_record.html)](project_record.html) | [Markdown (project_record.md)](project_record.md)

### 主軸 3：同學專案方向交流與診斷 (專案診斷 / 交流討論)
開放式交流環節，學員分享各自的專案構想或工作痛點，由講師與同仁進行現場診斷與可行性評估，協助大家順利完成謝總交代的課程作業與功課。

### 主軸 4：AI 專案所需技能與工具解析 (技能工具 / 深度解析)
盤點並深度解析執行企業級 AI 專案所需的技術堆疊、核心提示工程技巧以及協作工具應用之關聯。

---

## 🚀 核心實戰案例展示 (Featured Case Studies)

以下為 Class 04 重點示範專案，著重於將電腦視覺、OCR 辨識與企業工作流/智慧稽核整合運作的實際落地設計。

### 案例一：Video to PPT 智慧簡報影格萃取與知識庫
*   **專案精神**：捕捉專家經驗 ➔ 建立企業知識管理 (KM) 資料庫，且執行時完全不耗費任何 AI API Token（零運行成本）。
*   **技術整合特點**：
    *   **圖像變化偵測**：OpenCV 平均絕對誤差 (MAE) 進行快速變動判定。
    *   **雜湊去重與過濾**：64位元差值雜湊 (dHash) 漢明距離去重，輔以 Laplacian 邊緣變異數進行模糊與黑底畫面過濾。
    *   **OCR 與智慧搜尋 (RAG)**：擷取圖片後，串接 OCR (PaddleOCR/EasyOCR) 提取文字並進行向量嵌入 (Embedding)，讓簡報投影片內容可直接透過 LLM 進行語意問答與查詢。
*   **示範影片**：課堂播放最強完整版功能展示影片 `demo.mp4`。
*   **學員基礎代碼**：[📥 下載學生基礎版代碼 (video_to_ppt_basic.zip)](video_to_ppt_basic.zip) (內含 Python 偵測腳本與 README 說明，供課堂練習使用)。

### 案例二：AAA-Evidence Hub 企業電子憑證自動化處理平台
*   **專案精神**：針對中小企業與一人資訊部門 (OPC) 設計 of PoC，完整打通「憑證收集 ➔ 辨識 ➔ 轉換 ➔ 簽核 ➔ 模擬 ERP 入帳 ➔ 自動稽核」之閉環。
*   **技術整合流程**：
    *   **1. 辨識層 (OCR)**：整合 Layout-free LLM Vision API / Google OCR / PaddleOCR 提取非結構化憑證欄位。
    *   **2. 轉換層 (ETL)**：將憑證資料清洗並標準化為 Expense Record 格式。
    *   **3. 工作流 (Workflow)**：以狀態機驅動自動送審、會計覆核與模擬過帳流程。
    *   **4. 智慧稽核 (AI Audit)**：比對歷史資料進行重複核銷防弊、設定金額上限警示、以及透過語意理解驗證「週末公務乘車事由」之合規性。
*   **互動展示**：[🌐 開啟線上互動展示頁 (ticket-demo)](https://falo-taiwan.github.io/ticket-demo/)

### 案例三：iPAS 智慧刷題模擬器 (OCR + ETL 實戰)
*   **專案精神**：結合大模型視覺 (Gemini Vision API) 與高精度 OCR 技術，將紙本/圖片題庫進行即時結構化轉換、清洗與自動答題之完整 ETL 實踐。
*   **技術整合特點**：
    *   **1. 影像擷取與 OCR**：通過前端模擬器擷取題目圖片，調用 Vision API 進行精準文字與排版特點提取。
    *   **2. 資料清洗 (ETL)**：利用 Regex 與規則引擎對 OCR 斷字、多餘空格進行極致降噪與欄位校對，轉化為標準 JSON 格式。
    *   **3. 模擬器交互 (Swiper)**：結合 Swiper.js 打造流暢的滑動刷題體驗，內建即時 Token 消耗與台幣花費 Telemetry 面板，落實企業級 AI 成本控制意識。
*   **本機體驗**：[📱 開啟本機模擬器體驗 (practice-swiper.html)](practice-swiper.html) (100% 本地自包含單頁應用，自動載入 questions.csv)

---

## AI 開發工具對比分析表

| 工具名稱 | 核心定位 | 優勢特色 | 實戰技巧/限制 |
| :--- | :--- | :--- | :--- |
| **Antigravity (AI 程式助理)** | AI Agent 開發與代碼生成 | 專為本機/雲端 Pair Programming 設計，高效率產出 | 善用 Markdown 做為專案記憶與上下文控制 |
| **n8n / GAS** | 企業工作流自動化與 ERP 串接 | 視覺化 Workflow 與 Google 服務無縫串接 | 可作為 Event-Rule-Action 落地執行的白箱管道 |

---

## 學員課前提問與解答 (FAQ)

#### Q: 如果有想討論的專案構想，需要提前準備什麼嗎？
A: 建議提前整理出：(1) 目前的人工作業流程與痛點、(2) 期望達成的自動化效果。哪怕只有文字大綱或螢幕截圖，只要提前傳給講師，便能方便講師事先準備相關案例，讓課程診斷更貼近您的需求！ [標籤: 專案診斷, 課前準備]

---

## 其他參考資源
* [IPAS AIAP 課程網站](https://forceai0001-commits.github.io/ipas-aiap-2026/)：提供歷屆考試資源與 AI 技術學習指引
* [LINE Bot 專業開發專區](https://falo-taiwan.github.io/ai-line-help/)：專家級 LINE 聊天機器人整合實務與 AI 自動對答技巧
* [政府 AI 與資安成熟度檢核專案](../../../../gov-audit.html)：協助企業對接政府補助案與資安自評 SOP

