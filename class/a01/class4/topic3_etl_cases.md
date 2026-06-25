# 主題三：ETL 實務案例分享

本主題分享多個高保真（High-Fidelity）的 ETL 與 OCR 整合實戰案例，引導同仁理解如何進行結構化資料轉置與自動化處理。

![FORCE 架構圖 (ETL x KM x Agent)](images/falo_etl_km_agent.png)


## 🛠️ FORCE × ETL 核心階段深度解析 (Core Phases)

以下針對 FORCE 智慧協作平台之 **E、T、L** 三大核心階段進行深度技術解析，引導學員掌握數據從「異質採集」到「加載應用」的完整演進路徑。

---

### 📥 E (Extract) - 取得資料 {#etl-e}

這是數據管線（Data Pipeline）的起點，專注於從多元、異質的源頭中採集原始資訊。在企業級應用中，數據源通常包含結構化資料（ERP、資料庫）、半結構化資料（Email、CSV、JSON）與非結構化資料（紙本憑證、會議錄音、教學影片等）。

---

### ⚡ T (Transform) - 整理 / 轉換 {#etl-t}

這是整條數據管線的「核心靈魂」，負責將前階段採集到的無序原始數據，進行降噪、清洗、校正、AI 語意萃取與結構化封裝（例如轉換為標準的 Clean JSON 格式），為後續的知識庫檢索與決策應用做好準備。

---

### 📤 L (Load) - 輸出 / 應用 {#etl-l}

這是管線價值落地的「最後一公里」，負責將清洗乾淨且結構化後的黃金數據，精準加載至目標系統中（如向量資料庫、ERP 系統、戰情監控面板或自動通知 Webhook），進而轉化為企業的實質決策與業務價值。

---

## 🚀 核心實戰案例展示 (Featured Case Studies) {#featured-cases}

以下為 Class 04 重點示範專案，著重於將電腦視覺、OCR 辨識與企業工作流/智慧稽核整合運作的實際落地設計。

### 案例一：Video to PPT 智慧簡報影格萃取與知識庫
* **專案精神**：捕捉專家經驗 ➔ 建立企業知識管理 (KM) 資料庫，且執行時完全不耗費任何 AI API Token（零運行成本）。
* **技術整合特點**：
  * **圖像變化偵測**：OpenCV 平均絕對誤差 (MAE) 進行快速變動判定。
  * **雜湊去重與過濾**：64位元差值雜湊 (dHash) 漢明距離去重，輔以 Laplacian 邊緣變異數進行模糊與黑底畫面過濾。
  * **OCR 與智慧搜尋 (RAG)**：擷取圖片後，串接 OCR (PaddleOCR/EasyOCR) 提取文字並進行向量嵌入 (Embedding)，讓簡報投影片內容可直接透過 LLM 進行語意問答與查詢。
* **示範影片**：課堂播放最強完整版功能展示影片 `demo.mp4`。
* **學員基礎代碼**：[📥 下載學生基礎版代碼 (video_to_ppt_basic.zip)](video_to_ppt_basic.zip) *(內含 Python 偵測腳本與 README 說明，供課堂練習使用)*。

### 案例二：AAA-Evidence Hub 企業電子憑證自動化處理平台
* **專案精神**：針對中小企業與一人資訊部門 (OPC) 設計的 PoC，完整打通「憑證收集 ➔ 辨識 ➔ 轉換 ➔ 簽核 ➔ 模擬 ERP 入帳 ➔ 自動稽核」之閉環。
* **技術整合流程**：
  * **1. 辨識層 (OCR)**：整合 Layout-free LLM Vision API / Google OCR / PaddleOCR 提取非結構化憑證欄位。
  * **2. 轉換層 (ETL)**：將憑證資料清洗並標準化為 Expense Record 格式。
  * **3. 工作流 (Workflow)**：以狀態機驅動自動送審、會計覆核與模擬過帳流程。
  * **4. 智慧稽核 (AI Audit)**：比對歷史資料進行重複核銷防弊、設定金額上限警示、以及透過語意理解驗證「週末公務乘車事由」之合規性。
* **互動展示**：[🌐 開啟線上互動展示頁 (ticket-demo)](https://force-taiwan.github.io/ticket-demo/)

<div id="case-swiper"></div>

### 案例三：iPAS 智慧刷題模擬器 (OCR + ETL 實戰)
* **專案精神**：結合大模型視覺 (Gemini Vision API) 與高精度 OCR 技術，將紙本/圖片題庫進行即時結構化轉換、清洗與自動答題之完整 ETL 實踐。
* **技術整合特點**：
  * **1. 影像擷取與 OCR**：通過前端模擬器擷取題目圖片，調用 Vision API 進行精準文字與排版特點提取。
  * **2. 資料清洗 (ETL)**：利用 Regex 與規則引擎對 OCR 斷字、多餘空格進行極致降噪與欄位校對，轉化為標準 JSON 格式。
  * **3. 模擬器交互 (Swiper)**：結合 Swiper.js 打造流暢的滑動刷題體驗，內建即時 Token 消耗與台幣花費 Telemetry 面板，落實企業級 AI 成本控制意識。
* **雙通道體驗入口**：
  * [🌐 開啟 iPAS 智慧刷題模擬器 (線上 force 網址)](https://force-taiwan.github.io/class/a01/class4/practice-swiper.html) *(將於新視窗中開啟線上版模擬器)*
