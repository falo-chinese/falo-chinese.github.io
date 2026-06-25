# 政府 AI 與資安成熟度檢核專案 (gov-audit.md)

本項目專為企業對接政府 AI 導入與資安強化補助案所設計。協助企業客戶與售前顧問依據數位發展部（MODA）及經濟部產業發展署之 AI 應用與資安成熟度規範，對企業現行之網路防火牆、網關相容性、AI 代理（Agent）就緒度及資安防護能力進行全方位評估點檢。

---

## 📅 專案政策背景與政府補助案大意

為加速產業 AI 化並確保資訊安全，政府近年推出多項**「企業 AI 導入與資安強化輔導案」**與資金補助。企業在向政府申請 AI 專案補助時，必須提交客觀的「AI 技術就緒度與網路資安相容性評估報告」做為申請及結案之必要附件。
* **評估要點**：企業環境是否具備與雲端 AI 模型 APIs 安全通訊的能力、內網資料防洩（DLP）機制是否完善，以及是否符合政府對 AI 演算法安全與隱私之治理規範。
* **一魚多吃商業價值**：本點檢專案不僅做為企業內部 IT 審查工具，更能產出符合政府審查標準的雙軌報告，協助企業順利通過補助核定。

---

## 📋 企業資安自評與點檢流程 (SOP)

企業在導入 AI 系統（如 AI Agent, Workflow, 大模型治理）前，建議依據以下標準步驟進行點檢：

1. **基礎架構掃描 (Infrastructure Scan)**
   - 確認地端與雲端伺服器之連線狀態，釐清是否需要特定代理（Proxy）或例外排除規則。
2. **網絡與網關相容性檢測 (Network & Gateway Test)**
   - 探測各大 AI API 端點（如 OpenAI, Gemini, Anthropic）及 Webhook 接收點（如 GAS, LINE Bot）之連線通暢度。
3. **資料防洩與資安審計 (DLP & Safety Audit)**
   - 盤點 AI 工作流所存取的資料表，確認是否已建立人機協作（HITL）審核機制，避免敏感機密外洩。
4. **生成與匯出評估報告 (Report Export)**
   - 匯出高階 HTML/CSV 報告，提交給 IT 資安部門與政府窗口進行審查備查。

---

## 🛠️ 實戰檢測工具箱

為實施上述點檢流程，本專案提供多項輕量級自評與探測工具。其中核心網路探測工具如下：

### FALO 企業環境部署評估與網關相容性矩陣 (Deployment Assessment)
* **工具定位**：100% Client-Side 離線網路檢測與相容性分析矩陣。
* **核心特色**：
  - **no-cors 網域探測**：免伺服器直接於現場 Wi-Fi 內網一鍵檢測 50+ 核心網域通暢度。
  - **資訊漸進式揭露**：可展開查看 7 大部署技術相容度（Static, Dynamic API, Webhook, OAuth, Reverse Proxy, Custom Domain, Fixed IP）與導入難度分值。
  - **資料安全閉環**：所有問卷答案與連線結果均保存在瀏覽器本地，支持 HTML 報告上載還原，防止任何敏感企業數據外洩。
* **工具入口**：
  - [本機檢測入口 (HTML)](falo-taiwan/class/a01/class4/deployment-assessment.html)
  - *註：本機點開後，即可進行一鍵網域 TCP 握手探測，並匯出符合資安審核之評估報告。*

---

## 📚 相關參考資源

* **Class 04 課程首頁**：[Class 04 企業級 AI Agent 自動化實戰](falo-taiwan/class/a01/class4/index.html)（含教學實作與 Vibe Coding 觀念引導）
* **FALO 部署評估教學講義**：[FALO 企業環境部署評估講義 (HTML)](falo-taiwan/class/a01/class4/TEACHING_NOTES.html) | [Markdown](falo-taiwan/class/a01/class4/TEACHING_NOTES.md)
* **歷史課程彙整**：[銀河 ERP 內訓歷史課程首頁](history.html)（Class 01 - Class 03 彙整）
* **IPAS AIAP 課程平台**：[IPAS AIAP 官方課程指引](https://forceai0001-commits.github.io/ipas-aiap-2026/)
* **LINE Bot 專業開發專區**：[LINE Bot 專業開發與 AI 自動對答技巧](https://falo-taiwan.github.io/ai-line-help/)
