# 主題四：KM 建置與應用思維

本主題深入剖析企業知識管理（KM）與檢索增強生成（RAG）系統的建置觀念，以政府補助案作為載體，解構企業級 AI App 的設計 Pattern。

![AI KM 建置流程概念圖](images/ai_km_development_flow.jpg)

---

## 📂 AI KM 建置範例：政府 RAG 智慧檢索與診斷系統 {#ai-km}

為了解決複雜政策與補助法規的查詢痛點，我們開發了「政府 AI 與資安成熟度檢核專案」與「RAG 智慧檢索系統」。在此案例中，我們貫徹了企業級 RAG 系統的 **五大核心架構思維**：

### 1. 務實主義 (Pragmatism)
拒絕盲目追求高複雜度與昂貴的第三方框架（如 LangChain），以最直觀、高效的「純 JavaScript 向量相似度比對（Cosine Similarity）」在瀏覽器端直接運行，快速驗證核心商業價值與 MVP。

### 2. 安全防禦 (Defensive Coding)
針對企業內部可能存在「無網際網路、無外部 DNS、甚至嚴格限制 CORS」的極端內網環境，設計 `no-cors` 探針與自動降級策略（Fallback），在 API 無法連通時自動切換至離線預置數據庫。

### 3. 落地經濟學 (Economics)
深度優化 Token 消耗，前端設計「本地快取機制（LocalStorage Cache）」，避免重複查詢相同問題而產生不必要的 API 花費。同時在 UI 置入即時 Token 消耗與台幣花費監控面板，強化團隊的成本控制意識。

### 4. 結構化交付 (Structured Output)
強制要求大模型（LLM）輸出符合嚴格 JSON Schema 格式的數據，並在代碼端設計「自動修補與校對引擎」，確保輸出的診斷報告能 100% 與 ERP 的資料庫欄位無縫對接。

### 5. 零運維成本 (Serverless/Static)
採用 100% 靜態網頁架構（HTML/CSS/JS），無需部署資料庫或後端伺服器，免去高昂的維護成本與各種潛在的伺服器漏洞安全性威脅，極適合快速部署於內部儲存空間。

---

## ⚖️ AI Coding 實務對照：一般版 (v1) 與高手優化版 (v2) 的演進

在台灣政府 AI 補助工具庫的實戰開發中，開發者常面臨「能用就好」與「企業級落地」兩種截然不同的開發思維。我們透過以下兩張架構與功能對照圖，深入剖析其中的技術分野：

![AI App Studio: 兩種 AI Coding 的差異](images/ai_coding_comparison_v1_v2.png)

![AI App Studio: 同一需求，不同層次的 AI Coding](images/ai_coding_architecture_details.png)

### 1. 一般 AI Coding 普通版 (v1) 的限制
普通版 v1 的核心目標是 **「快速交付 Demo，驗證想法 (PoC)」**。
* **技術特點**：採用純前端 SPA 架構，資料儲存於靜態 JSON 中，使用簡易的 MiniSearch (TF-IDF) 進行關鍵字搜尋。這在開發初期非常高效，能在幾小時到一天內快速實現。

## 🗺️ 企業級 AI App 落地藍圖：全面合規與長期維運

正如上述對照，做得出來只是開始，要讓企業長期安心使用，必須將技術思維上升到產品與工程思維。根據 **「AI App 企業落地藍圖」** 的七大關鍵注意事項，企業級知識管理（KM）與 RAG 系統的落地必須落實以下防護維度：

![AI App 企業落地關鍵注意事項](images/falo_ai_app_enterprise_landing.png)

* **資料與知識管理**：這是 RAG 系統的基石。企業必須進行嚴格的「資料品質控管（確保準確與完整）」，建立「ETL 定期更新與監控機制」以保證知識庫的時效性，並透過「知識分類與標籤標準化」大幅提升向量比對檢索的精振度。
* **資安防護與治理合規**：企業內部知識庫通常包含高度敏感的專利、法規或經營數據。因此，系統必須實施嚴格的「權限控管（限制誰可查閱哪些知識庫）」，防範「Prompt 注入攻擊」，並建立完整的「操作紀錄與稽核日誌 (Audit Log)」，確保每一次的 AI 檢索均有跡可循。
* **落地經濟學與成本效能**：在大規模查詢情境下，Token 成本會迅速攀升。我們必須導入「Context Caching（上下文快取）」以降低長文本的重複處理花費，優化「快取與索引機制」，落實「聰明用資源，才能長久又划算」的落地指標。

---

## 🖥️ 企業級 AI 雙軌戰情中心 (War Room) 與元件解構 {#ai-war-room}

在企業數據管線（Data Pipeline）的 ETL 閉環中，**Load (L) 階段**不僅僅是將清洗好的數據載入向量資料庫，更包含「如何將高價值的結構化數據呈現給決策者（Data Analytics）」以及「如何實時監控系統的健康度、安全防禦與用戶行為日誌（Operations Telemetry）」。

為了讓學員深刻理解下一代 ERP 生態圈的 AI 運維架構，我們將本課程的政府補助案 RAG 專案進行了延伸開發，設計了一套高質感的深色科技風格**「企業級 AI 雙軌戰情中心」**。這套系統分為兩個獨立的主大屏，分別對應資料剖析與用戶行為審計。

---

### 🖥️ 雙軌戰情中心大屏全景藍圖

學員可在宏觀大屏中體驗「密密麻麻」的高密度指揮中心布局。大屏整合了全局指標，有需要時可「點進去細看」下方物理拆解的各個元件。

#### 1. 版本 A：原始資料戰情系統大屏 (Raw Data & Knowledge Analytics)
此系統專注於**靜態原始資料的加載與多維度剖析**。呈現 244 筆政府補助案的整體結構：

![原始資料戰情系統大屏](images/enterprise_ai_war_room_raw_data.svg)

#### 2. 版本 B：使用者行為與運維審計戰情系統大屏 (User Behavior & Operations Audit)
此系統專注於**動態用戶行為、RAG 回答質量、實時 Token 成本與資安防禦監控**：

![使用者行為與運維審計戰情系統大屏](images/enterprise_ai_war_room_user_behavior.svg)

---

### 📂 雙軌戰情系統八大核心元件物理拆解與深度解構

為了讓學員理解在不同商業與工程場景下，如何選擇並設計最適的圖表類型，我們將上述兩大系統拆解為 **八大核心儀表板元件**，逐一進行視覺展示與深度技術解構：

#### 📊 原始資料戰情系統 (版本 A) 元件解構

##### 元件 A1：大盤核心 KPI 指標面板 (Top Cards)
![KPI 指標面板](images/component_kpi_cards.svg)
*   **圖表類型**：**數值指標卡 (Metric Cards)** ＋ **趨勢微線圖 (Sparklines)**。
*   **商業洞察**：即時呈現「方案總數 244 筆」、「活躍廠商 128 家」、「導入預算中位數 NT$ 65,000」等核心大盤數據，並在下方搭配微幅波動的綠色微線圖，表徵數據的穩定載入狀態。這組指標能讓決策者秒級掌握系統負載與數據規模。
*   **技術實現**：在前端異步加載靜態 `unified_ai_tools_db.json` 資料庫（壓縮後僅約 150KB），在內存中通過高效的 JavaScript 數組處理（如 `Set`、`reduce`）動態計算指標，保證 0 延遲加載。

##### 元件 A2：AI 標準化分類佔比圓環圖 (Donut Chart)
![分類佔比圓環圖](images/component_donut_chart.svg)
*   **圖表類型**：**環狀比例圖 (Donut Chart)** ＋ **結構百分比清單 (Legend Grid)**。
*   **商業洞察**：揭示了補助案在四大 SaaS 領域的分佈。「人資與知識管理 (40%)」佔比最高，是目前政府補助的主力方向；其次為「客戶服務與溝通 (25%)」，「行銷與銷售加值 (20%)」及「生產與運營管理 (15%)」。這能引導企業將資源優先投入最易獲得政府補助的領域。
*   **技術實現**：採用 SVG 原生的 `stroke-dasharray` 與 `stroke-dashoffset` 動態圓環比例繪製，結合 CSS `transition` 提供極致流暢的加載動畫，完全避免了第三方圖表庫（如 Chart.js）帶來的打包體積膨脹。

##### 元件 A3：適用產業熱力矩陣 (Heatmap)
![適用產業熱力矩陣](images/component_heatmap.svg)
*   **圖表類型**：**二維熱力矩陣 (2D Heatmap Matrix)** ＋ **熱度分級標註 (Density Indicators)**。
*   **商業洞察**：以熱力漸層色彩標註不同 AI 分類在「資訊、製造、零售、醫療、金融」五大產業的適用度。例如「製造業」在「人資知識」與「生產工安」中熱度極高，能幫助企業進行精準的 SaaS 定位。
*   **技術實現**：設計成全局過濾器。當使用者在前端點選矩陣中的特定格子時，會觸發雙向聯動，整個戰情中心的數據（包括圓環圖與象限圖）將立即根據該產業過濾並重新渲染。

##### 元件 A4：預算期程性價比象限散佈圖 (Quadrant Scatter Plot)
![預算期程性價比象限圖](images/component_value_matrix.svg)
*   **圖表類型**：**四象限 Bubble 散佈圖 (Quadrant Bubble Plot)** ＋ **黃金分割十字臨界線 (Threshold Crosshair)**。
*   **商業洞察**：以橫軸「期程 (月)」與縱軸「預算金額」劃分出四大決策象限，協助企業進行精準決策：
    *   **I. 客製 PoC 服務**：高預算、短週期，適合前期概念驗證。
    *   **II. 重型專案系統**：高預算、長週期，適用大型核心系統導入。
    *   **III. 輕量嘗鮮區**：低預算、短週期，適合小範圍敏捷試錯。
    *   **IV. 高性價比 SaaS**：低預算、長週期，是企業轉型、低成本高收益的首選（如 Vital KM+）。
*   **技術實現**：利用 SVG 散佈點（Scatter Plot）定位，氣泡大小與方案熱度掛鉤。透過黃金中位數（6個月期程與 6.5 萬元預算）作為十字交叉線，為企業自動篩選出最優轉型路徑。

---

#### 👤 使用者行為與運維審計系統 (版本 B) 元件解構

##### 元件 B1：熱門搜尋詞與知識缺口橫條圖 (Horizontal Bar Chart)
![熱門搜尋與知識缺口](images/component_horizontal_bar.svg)
*   **圖表類型**：**水平長條圖 (Horizontal Bar Chart)** ＋ **排名標籤 (Rank Badges)**。
*   **商業洞察**：列出 Top 5 查詢頻率最高的詞彙（例如「資安成熟度補助」、「自籌經費比例」等）。這代表企業內最迫切的「知識缺口 (Knowledge Gap)」，如果某些高頻問題的查詢好評率很低，則能直接指導企業下一次 ETL 增量清洗與載入的方向，形成「數據閉環」。
*   **技術實現**：在前端記錄用戶每次的 Search Query，非同步寫入運維審計日誌。數據加載模組定期以 MapReduce 方式在前端進行頻次聚合，並利用 SVG 的 `<rect>` 元素渲染出高質感的漸層水平長條。

##### 元件 B2：RAG 回答滿意度與質量圓弧儀表 (Radial Gauge Chart)
![回答滿意度與質量評估](images/component_radial_satisfaction.svg)
*   **圖表類型**：**半放射狀圓弧儀表 (Radial Gauge)** ＋ **好評率 KPI (Feedback KPI)**。
*   **商業洞察**：呈現用戶按讚/按踩的好評率（89.2%），並展示 LLM 未匹配率 (4.5%)，讓運維人員一眼看出 AI 答得好不好。這直接反映了知識庫切片與 Embedding 檢索的精準度。
*   **技術實現**：前端 UI 提供 thumbs-up/down 的一鍵反饋按鈕。統計引擎異步統計好評率，並動態調用 SVG 的 `stroke-dashoffset` 將好評率即時轉化為綠色發光半圓弧進度條。

##### 元件 B3：Token 流量與快取節費折線走勢圖 (Real-time Line Chart)
![Token 消耗實時走勢圖](images/component_cache_trend.svg)
*   **圖表類型**：**雙折線區域圖 (Dual-line Area Chart)** ＋ **漸層填充 (Gradient Fill Area)**。
*   **商業洞察**：一條陡峭上升的橙色虛線（未啟用快取的線性花費）對比一條極度平緩的藍色實線（啟用 Context Caching 後的快取花費），以極具衝擊力的折線圖直觀證明「快取大省 90% 成本」的經濟學威力，向決策同仁展示實實在在的「企業 AI 降本增效」。
*   **技術實現**：前端對話引擎在每次發起 API Request 前，會讀取並記錄本地 API 返還 of `usageMetadata`，並在前端繪製出一條包含 `linearGradient` 漸層填充的雙折線區域圖。

##### 元件 B4：資安 Gatekeeper 與多 Agent 自治佇列 (Security Alarm & Agent Queue)
![安全與協作佇列](images/component_security_agent_queue.svg)
*   **圖表類型**：**告警狀態面板 (Security Alarm Panels)** ＋ **流水線狀態佇列 (Agent Pipeline Queue)**。
*   **商業洞察**：上方以紅色警報燈監控當日 Prompt 注入攻擊攔截次數（8次）與違規敏感詞查詢，保障系統的生命線；下方監控 ETL-Agent、RAG-Agent、Report-Agent 等非同步協作佇列的執行狀態（ACTIVE/IDLE），讓運維人員精準掌握後台微服務的負載。
*   **技術實現**：資安防護模組（Gatekeeper）攔截惡意輸入並即時寫入告警計數器；微服務協調器（Orchestrator）在非同步工作流啟動與休眠時，通過 Webhook 將狀態即時推送到戰情中心佇列面板。

---

## 📓 NotebookLM 整合運用 {#notebooklm}

企業在導入知識管理 (KM) 時，除了自行建置 RAG 系統，亦可深度整合與搭配 Google NotebookLM 作為協作與提煉工具。為了克服 NotebookLM 網頁端手動操作與單兵作戰的限制，我們規劃了以下兩種企業級整合運用模式：

### 1. 結合 Prompt 管理器 (Prompt Manager Integration)
NotebookLM 的強大在於其基於來源資料的理解與互動，但不同部門（如研發、業務、財務）在提煉知識時所需的輸出格式與視角各有不同。透過導入「企業統一 Prompt 管理器」，同仁可快速調用標準化的系統提示詞（System Prompts），在 NotebookLM 內進行一致性的高質量引導：
- **結構化大綱生成**：統一規定 NotebookLM 生成特定格式的專案審查清單或合規風險矩陣。
- **特定視角角色扮演**：例如以「資深 ERP 顧問」或「政府補助稽核員」的視角，對導入的專案文件進行深度詰問與核對。

### 2. 建立企業共用入口與 NotebookLM CLI 整合 (Unified Portal & NotebookLM CLI)
為了解決傳統上需要逐一手動上傳文件至 NotebookLM 的痛點，企業可構建一層「統一知識共用入口」（Web Portal）。此入口底層結合 **NotebookLM CLI (命令列介面工具)** 或自動化腳本，實現以下流程：
- **自動化文件同步**：員工只需將發票、補助計畫書或合約拖入企業 KM 系統，底層腳本便會自動調用 NotebookLM CLI，將文件同步上傳至指定的 Google Drive 資料夾或 Notebook 來源庫中。
- **跨團隊共用導覽**：透過共用入口，團隊能一鍵將自動編排好的 Notebook 分享給專案利害關係人，實現組織級的知識快速對接與共用。
