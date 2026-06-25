# 主題五：AI App 專案腦力激盪

本主題收錄完整的「AI APP Studio 工作坊」實戰框架，引導同仁從痛點出發，共創天心 ERP × FALO AI App Store 的產品藍圖。

---

## 🗺️ AI App 落地評估指標：工作坊專案設計的終極指引

在 **AI App Studio 工作坊** 中，我們不僅要激發同仁的創意，更需要引導大家以「企業級落地」的高度來評估與設計每一個 AI App 專案。當團隊在進行腦力激盪、填寫需求 Backlog 或規劃 MVP 時，必須參考這份完整的 **「AI App 企業落地關鍵注意事項」** 查檢表：

![AI App 企業落地關鍵注意事項](images/falo_ai_app_enterprise_landing.png)

* **使用者體驗與採用**：這是產品成功的起點。一個 AI App 如果沒人使用，就無法創造價值。設計時必須確保「簡單易用好上手」，提供「精準的搜尋與交互體驗」，並在前期就規劃好「教育訓練與推廣計畫」。
* **人機協作與流程整合**：企業級 AI App 絕非完全脫離人工的黑盒子。我們必須設計 **「HITL (Human-in-the-Loop) 人機協作機制」**，讓關鍵決策始終有同仁把關；並逐步完成從「流程整合（串接現有 ERP 系統）」到「AI Agent 自動化執行任務」的演進，使系統越用越聰明。
* **系統架構與穩定維運**：在設計 MVP 與 PoC 時，就必須考慮未來的擴充性。應採用「模組化與可擴充架構」，優化「API 設計與整合能力」，並在前期就建立完善的「監控與日誌 (Logging)」策略，以確保系統架構穩定，服務不中斷。

---

## 🛡️ 企業部署實戰：FALO 閘道相容性與防火牆檢測工具 (Firewall Test)

在進行 AI App 的專案腦力激盪、MVP（最小可行性產品）與 PoC（概念驗證）規劃時，團隊往往會面臨一個極具殺傷力的現實問題：**「這款 AI App 在企業內部高度安全的網絡環境下到底能不能通？」**

企業的網絡拓撲通常極為嚴格，開發或部署 AI App (特別是需要串接外部 LLM API、雲端數據庫或開源模型庫的專案) 時，常因防火牆阻擋、DNS 無法解析或 CORS 限制，導致 API 連線失敗。如果沒有在 PoC 規劃初期就進行評估，好不容易想出來的 AI App 創意將在部署階段面臨停滯。

為了解決這個企業落地的關鍵痛點，我們將 **FALO Assessment Tool (Firewall Test)** 閘道與平台相容性評估工具納入本主題，作為 AI App 專案可行性評估的即戰力武器。

### 1. 工具設計定位與核心價值
這是一個**去中心化、純前端、可離線運行**的環境相容性評估系統，專為售前顧問 (Pre-sales)、產品經理 (PM)、系統架構師 (Architect) 在進行專案 Discovery (探索) 與 MVP 評估時打造。其核心價值在於：
* **一鍵化快速評估**：團隊只需在客戶或目標企業的內網環境中點開網頁，即可在 10 秒內快速檢測 50+ 種主流 AI API、雲端平台、開源模型庫的連通性。
* **可行性決策矩陣 (Compatibility Matrix)**：將受測平台依「推薦等級 (A–D)」與「導入難度 (1–5 星)」進行視覺化分類，直接對應到專案可行性評估中，提供清晰的防火牆放行與替代架構建議。
* **安全指紋診斷 (Diagnostics)**：自動偵測瀏覽器環境的安全防禦狀態、CORS 繞過可能性、以及 DNS 連線特徵，為 AI App 架構設計提供科學的客觀數據。
* **零隱私洩露風險**：工具採用 100% Client-side 前端執行，不透過 any 後端伺服器中轉數據，保障企業內網拓撲與檢測結果的隱私安全。

### 2. 核心技術原理與實作機制
該工具展示了多項在規劃 AI App 時非常實用的「前端防禦性與診斷性編程 (Defensive & Diagnostic Programming)」技術：
* **`no-cors` 連通性探針 (Reachability Probing)**：利用 Fetch API 的 `mode: 'no-cors'` 模式向外部伺服器發送探針（如向 `https://api.openai.com` 請求）。雖然因跨來源限制無法取得回應內容，但瀏覽器仍會觸發 `fetch` 成功或失敗，藉此精準判斷該網域是否已被防火牆攔截，同時避開了 CORS 的跨域阻擋報錯。
* **離線數據狀態匯出與載入 (State Export & Import)**：針對與網際網路完全隔離的極端內網（Air-gapped Env），支援將本地檢測結果序列化為編碼後的加密 HTML Payload。使用者可下載此離線文件，並在任何有網或無網環境中重新回載、分析其環境矩陣，實現極致的去中心化協作。

### 3. 工具實測與說明入口
本專案已將此工具完整整合，提供線上與本地的雙軌實測管道：
* 🌐 **[線上即時檢測工具入口 ➔ FALO Firewall Test](https://falo-taiwan.github.io/firewall-test/)** *(推薦：一鍵為您的當前環境進行相容性與連通性檢測)*
* 📖 **[企業導入部署說明手冊 ➔ Firewall Test Readme](https://falo-taiwan.github.io/firewall-test/readme.html)** *(詳解 50+ 種平台放行規則、評估等級與網絡架構調校)*
* 💻 **本地運行版入口 ➔ [deployment-assessment.html](deployment-assessment.html)** *(學員可直接雙擊專案包內的 HTML 檔，在本地或內網隔離環境中直接執行檢測與評估)*

---

## 學習目標
- 運用「痛點轉化矩陣」與產品思維方法論。
- 進行三階段工作坊，共創 50+ AI App 創意 Backlog。
- 評估與設計 MVP（最小可行性產品）與 PoC（概念驗證）規劃。

## 工作坊全套資源
- [📖 工作坊總覽首頁](ai_app_readme.html)
- [🧠 產品思維方法論](methodology_blueprint.html)
- [🔍 痛點與需求驗證手冊](discovery_validation_playbook.html)
- [📋 50+ AI App 創意 Backlog](backlog_template.html)
- [💡 100+ AI App 創意庫](idea_library.html)
- [📊 100分制評審與決策表](scorecard.html)
- [🚀 MVP & PoC 規劃指南](mvp_poc_guide.html)
- [📝 學員實作工作紙](student_worksheets.html)
- [👨‍🏫 講師引導指南](workshop_facilitator_guide.html)
- [📂 歷程記錄](project_record.html)
