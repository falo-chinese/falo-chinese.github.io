# 主題三：ETL 實務案例分享

本主題分享多個高保真（High-Fidelity）的 ETL 與 OCR 整合實戰案例，引導同仁理解如何進行結構化資料轉置與自動化處理。

![FALO 架構圖 (ETL x KM x Agent)](images/falo_etl_km_agent.png)

---

## 🚀 核心實戰案例展示 (Featured Case Studies)

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
* **互動展示**：[🌐 開啟線上互動展示頁 (ticket-demo)](https://falo-taiwan.github.io/ticket-demo/)

<div id="case-swiper"></div>

### 案例三：iPAS 智慧刷題模擬器 (OCR + ETL 實戰)
* **專案精神**：結合大模型視覺 (Gemini Vision API) 與高精度 OCR 技術，將紙本/圖片題庫進行即時結構化轉換、清洗與自動答題之完整 ETL 實踐。
* **技術整合特點**：
  * **1. 影像擷取與 OCR**：通過前端模擬器擷取題目圖片，調用 Vision API 進行精準文字與排版特點提取。
  * **2. 資料清洗 (ETL)**：利用 Regex 與規則引擎對 OCR 斷字、多餘空格進行極致降噪與欄位校對，轉化為標準 JSON 格式。
  * **3. 模擬器交互 (Swiper)**：結合 Swiper.js 打造流暢的滑動刷題體驗，內建即時 Token 消耗與台幣花費 Telemetry 面板，落實企業級 AI 成本控制意識。
* **雙通道體驗入口**：
  * [🌐 開啟 iPAS 智慧刷題模擬器 (線上 falo 網址)](https://falo-taiwan.github.io/class/a01/class4/practice-swiper.html) *(將於新視窗中開啟線上版模擬器)*
  * [📱 開啟本地練習版模擬器 (practice-swiper.html)](practice-swiper.html) *(在原視窗內直接開啟本地端檔案)*

---

## 📂 實戰專案與手冊
本主題提供豐富的實戰手冊，引導您一步步動手實作上述的案例：
* [🔍 痛點與需求驗證手冊](discovery_validation_playbook.html)：學習如何掃描並定位真實業務痛點。
* [🚀 MVP & PoC 規劃指南](mvp_poc_guide.html)：掌握最簡可行產品的架構設計與交付方法。
* [📋 50+ AI App 創意 Backlog](backlog_template.html)：參考天心 ERP 實際梳理出的需求池，加速靈感轉換。
