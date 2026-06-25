# 主題三：ETL 實務案例分享

本主題分享多個高保真（High-Fidelity）的 ETL 與 OCR 整合實戰案例，引導同仁理解如何進行結構化資料轉置與自動化處理。

![FORCE 架構圖 (ETL x KM x Agent)](images/falo_etl_km_agent.png)

## 🛠️ FORCE × Agent 核心四大階段深度解析 (Core Phases)

以下針對 FORCE 智慧協作平台之 **E、T、L、Agent** 四大階段進行深度技術解析，引導學員掌握數據從「異質採集」到「自主決策」的完整演進路徑。

---

### 📥 E (Extract) - 取得資料 {#etl-e}

![E (Extract) 取得資料](images/etl_e_extract.svg)

這是數據管線（Data Pipeline）的起點，專注於從多元、異質的源頭中採集原始資訊。在企業級應用中，數據源通常包含：
- **結構化數據**：ERP 資料庫、關聯式資料庫（SQL）交易紀錄、標準 FORCE API 接口。
- **半結構化數據**：Email 通訊、CSV 報表、JSON 數據流。
- **非結構化數據**：紙本憑證掃描件（PDF/圖片）、會議錄音（語音）、教學影片（影格）。

在 AI 時代，E 階段更被賦予了「多模態感知起點」的使命。透過電腦視覺與 OCR Agent，系統能像人類的眼睛一樣，主動辨識實體世界與非結構化文件中的視覺元素，將其轉化為可供處理的原始文本流（Raw Stream），為後續的 FORCE 知識轉置提供源源不絕的素材。

> [!NOTE]
> 🔗 **相關展示與範例網站**：*(後續將在此插入具體範例網站與相關連結)*

---

### ⚡ T (Transform) - 整理 / 轉換 {#etl-t}

![T (Transform) 整理 / 轉換](images/etl_t_transform.svg)

這是整條數據管線的「核心靈魂」，負責將前階段採集到的無序 Raw 數據，進行極致的降噪、清洗、校正與結構化封裝。核心處理邏輯包括：
1. **資料清洗與去重**：排除重複行、去除頁首頁尾、過濾空白字符與多餘雜訊。
2. **OCR 校正與補件**：針對圖片辨識出的斷字、錯字進行語意校正，並補齊遺漏欄位。
3. **AI 萃取與分類**：調用大語言模型（LLM）的推理能力，從段落中精確辨識並分類出實體（如金額、日期、品項、統編）。
4. **建立 Metadata / 標籤**：自動生成檔案的版本、分類標籤、權限屬性，並將資料轉置為標準的結構化 JSON 格式。

經過 T 階段的處理，原本雜亂無章的非結構化數據將轉化為「高價值、高清晰度、機器與 AI 皆可讀」的黃金數據（Clean JSON），並生成對應的向量嵌入（Embedding），為中央 FORCE 知識庫做好準備。

> [!NOTE]
> 🔗 **相關展示與範例網站**：*(後續將在此插入具體範例網站與相關連結)*

---

### 📤 L (Load) - 輸出 / 應用 {#etl-l}

![L (Load) 輸出 / 應用](images/etl_l_load.svg)

這是管線價值落地的「最後一公里」，負責將清洗乾淨且結構化後的黃金數據，精準加載至目標系統中，進而轉化為企業的決策價值。主要的載入目標與應用場景 include：
- **知識沉澱（Vector DB）**：加載至向量資料庫（如 Milvus、Pinecone 或本地向量索引），作為 RAG（檢索增強生成）系統的核心知識源。
- **業務整合（ERP / SQL）**：與 FORCE 平台或現有的 ERP、CRM 或 MIS 系統對接，自動完成單據入帳、主數據更新。
- **運維監控（Dashboard）**：加載至戰情中心，實時呈現數據流狀態、Token 流量花費、以及 API 性能遙測數據（Telemetry）。
- **主動通知（Notifications）**：加載完成後自動觸發下游通知，如 LINE 訊息推播、Email 自動派送或 Webhook 觸發。

L 階段將結構化知識加載到正確的位置，使靜態的數據重新「活」了起來，成為驅動企業運營的即戰力。

> [!NOTE]
> 🔗 **相關展示與範例網站**：*(後續將在此插入具體範例網站與相關連結)*

---

### 🤖 Agent (AI Agent) - 智慧協作 {#etl-agent}

![Agent (AI Agent) 智慧協作](images/etl_agent.svg)

這是整條 ETL 管線的「大腦指揮官」，對應 FORCE 架縱最底層的 **AI Agent 智慧協作平台**。它改變了傳統自動化程式的僵化思維，引入了具備推理與規劃能力的自治 Agent 佇列：
- **Workflow Agent**：主動規劃多步驟工作流，串聯不同的微服務。
- **OCR / ETL Agent**：自主判斷最適合的辨識引擎，並在辨識失敗時進行自我反思與重試。
- **Audit Agent**：全量審查入帳數據，主動識別異常交易、重複報支或合規漏洞。
- **人機協作（HITL, Human-in-the-Loop）**：當系統遇到低置信度數據或高風險操作時，Agent 會主動暫停並將任務派送給人類主管進行審批，兼顧效率與安全。

AI Agent 貫穿了 E-T-L 的全生命週期，讓整個數據管線具備了自我優化、主動防禦與自主決策的智慧能力。

> [!NOTE]
> 🔗 **相關展示與範例網站**：
> * [🌐 iPAS 智慧輔導 AI Agent 模擬器](https://falo-taiwan.github.io/ipas-aiap/practice-swiper.html) - 結合大模型視覺與高精度 OCR 技術，將紙本/圖片題庫進行即時結構化轉換、清洗與自動答題之完整 ETL 實踐，並搭載即時 Token 消耗與台幣花費監控面板。

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
