# 主題一：前三堂課程交流與補充

> [!NOTE] 📂 **前三堂課程簡報 PDF 下載與存取說明**<br>• **Class 1 課程簡報**：<a href="javascript:void(0);" onclick="verifyPdfPassword('https://drive.google.com/file/d/1lcTQQ4ceWf8-I-qxifTIbkTq8gwW0Pp7/view')" style="color: var(--accent); font-weight: bold; text-decoration: underline;">🌐 Google Drive 下載連結</a><br>• **Class 2 課程簡報**：<a href="javascript:void(0);" onclick="verifyPdfPassword('https://drive.google.com/file/d/1FV_SEjwf68vgd_CH28ScJSjz1FiwxxTw/view')" style="color: var(--accent); font-weight: bold; text-decoration: underline;">🌐 Google Drive 下載連結</a><br>• **Class 3 課程簡報**：<a href="javascript:void(0);" onclick="verifyPdfPassword('https://drive.google.com/file/d/1XDK6z2988pxJ0mIHCvgQmjFEHVCc2UeM/view?usp=sharing')" style="color: var(--accent); font-weight: bold; text-decoration: underline;">🌐 Google Drive 下載連結</a><br>• 🔑 **PDF 檔案密碼提示**：公司英文縮寫。

<script>
function verifyPdfPassword(url) {
    var password = prompt("請輸入密碼以開啟下載連結：\n（提示：公司英文縮寫）");
    if (password) {
        if (password.toLowerCase() === "attn") {
            window.open(url, "_blank");
        } else {
            alert("密碼錯誤！提示：公司英文縮寫");
        }
    }
}
</script>

本主題旨在對前三週的學習重點進行深度沉澱與補充，並針對同仁在實務開發中遇到的盲點進行診斷與解答。

![AI App Studio 專案開發四大原則](images/ai_app_studio_four_principles.png)

---

## 📌 常見提醒與交付規範 (台灣時間 UTC+8) {#guidelines}
> [!IMPORTANT]
> 本課程與專案之所有宣告、作業交付截止日期等時間，皆**統一宣告並以台灣時間 (UTC+8) 為唯一準則**。

* **雙軌標準規範 (md + html)**: 所有提問集、作業及大綱，必須同時提交 **Markdown (.md)** 檔（供 AI/LLM 結構理解）與 **HTML (.html)** 網頁檔（供人類閱讀），落實雙軌並行標準。
* **壓縮包命名習慣 (ZIP 檔案)**: 凡提交程式碼或專案資源壓縮包時，請遵循 **「[時間戳記]_[重要更新事項].zip」** 命名規範（例如：`20260622_class04_project.zip`）。

---

## 💬 前三週重點補充與問題解答 {#supplement}
### 1. 人機協作模式 (HITL - Human in the Loop)
在複雜的企業流程（如 ERP 自動入帳、智慧對帳）中，AI 無法達到 100% 的精準度。因此，必須建立合理的人機協作機制：
* **AI 負責 90% 的繁重工作**：包括非結構化憑證的 OCR 辨識、初步分類、欄位清洗與比對。
* **人類負責 10% 的高風險決策**：當 AI 信心指數（Confidence Score）低於閾值（例如 85%），或是稽核引擎觸發異常警示時，系統自動將任務分流至人工審核界面，確保數據品質。

### 2. 雙軌文件策略
在 AI-Native 的開發模式下，文件不只是給人看的，更是給 AI 助理（如 Antigravity）讀取的關鍵上下文：
* **Markdown (.md)**：語意結構清晰，便於 LLM 進行 RAG 檢索、代碼生成與上下文控制。
* **HTML (.html)**：具備豐富的視覺樣式與互動效果，方便團隊成員、管理層以及客戶直觀理解。

#### 💡 個人 AI（能力管理）與 團隊 AI（知識管理）的不同定位
我們在知識管理與流程規範上，應區分「個人 AI」與「團隊 AI」的用途（皆使用 Markdown 作為基礎，但用途與路徑不同）：

![個人 AI 與 團隊 AI 的知識管理方式](images/personal_vs_team_ai_knowledge.png)

* **個人使用 (Personal AI) ➔ 管理的是「能力 (Skill)」**
  透過 `Skill.md` 定義 AI 助理的行為準則與工具調用流程，注入 AI 執行階段 (AI Runtime)，讓 **AI 自己變強**（例如本機下載的 <a href="file:///Users/force/Downloads/superpowers_skill.md">superpowers_skill.md</a> 技能規範）。
* **團隊使用 (Team AI) ➔ 管理的是「知識 (Markdown + HTML)」**
  建立專案共享文件目錄（如 `README`、`PROJECT_RULE`、`WORKFLOW`），落實雙軌並行，讓 **大家使用同一份知識與規範**。

---

### 🚀 案例研究：Superpowers 的 HTML 本地化與雙軌優勢 {#superpowers-case}
為了讓大家更直觀地理解雙軌文件在實務上的威力，我們以知名的 AI Coding Agent 方法論專案 [Superpowers](https://github.com/falo-taiwan/superpowers) 為例。該專案原本是一套基於 Markdown 定義的個人 AI 技能庫（如 <a href="file:///Users/force/Downloads/superpowers_skill.md">superpowers_skill.md</a>），但當轉化為團隊協作與教材時，將其**本地化編譯為單頁 HTML 互動說明網頁**（[Superpowers 說明網頁](https://falo-taiwan.github.io/superpowers/)）帶來了諸多顯著好處：

1. **動態「雙視角切換」解決資訊不對稱**
   HTML 網頁可內建互動按鈕，讓讀者在「**新手/一般使用者**」與「**專家/系統架構師**」視角間一鍵切換。
   * **新手視角**：專注於易懂的比喻與直觀 timeline，引導理解「AI 不要亂衝，照著 SOP 做」的世界。
   * **專家視角**：直接展示 `session-start hook`、`behavior-shaping layer`、`hard gates` 等工程硬約束與底層架構。
   在 Markdown 中無法實現這種動態展示，而 HTML 可以透過簡單的 CSS 與 JS 讓同一份文件兼顧商務端與技術端。

2. **流程視覺化（Workflow Visualization）**
   原本在 Markdown 中只是平鋪直述的階層清單，在 HTML 中可以轉化為具備編號、自訂圖示、步進導引的「互動時間軸 (Timeline)」，大幅降低人類工程師的閱讀心智負擔。

3. **重點紅線與規則警示（Iron Laws）**
   透過 HTML 樣式（如 CSS 磨砂玻璃、自訂顏色與醒目的卡片邊框），可以將關鍵的「硬性閘門（Hard Gates）」與「鐵律（Iron Laws）」（例如：*未獲設計核可前禁止任何實作*、*沒有測試不准寫 Code*）進行高視覺強度的突顯，避免重要規則被淹沒在大量文字中。

4. **結構化互動儀表板（Interactive Dashboard）**
   將 14 個 Markdown 技能定義與觸發規則（Triggers）以精美、可滾動的響應式表格展示，方便團隊成員快速檢索與定位。

5. **百分之百離線可用與快速分享**
   HTML 本地化網頁不需要啟動任何本機伺服器（如 Node/Express），直接雙擊就能在瀏覽器開啟，完美融入 FALO 無網路狀態下的離線教材備用機制，同時也非常便於在組織內部快速傳閱與交接。

---

## 🛠️ 同學專案方向交流與診斷 {#diagnostic}
現場開放式的交流與診斷環節。學員可分享各自的專案構想或工作痛點，由講師現場診斷並給予可行性建議，協助同仁順利完成謝總交代的作業與功課。

### 診斷核心指標
1. **痛點真實性**：該流程是否每日重複、耗費高昂人工工時？
2. **AI 必要性**：是否必須使用 LLM 語意理解，還是傳統的 Rule-based / Regex 就能解決？
3. **資料可得性**：是否有足夠且合規的樣本數據供 AI 學習與測試？
4. **落地經濟性**：Token 消耗與運行成本是否可控？

---

## 🙋 學員課前提問與解答 (FAQ) {#faq}

#### Q: 如果有想討論的專案構想，需要提前準備什麼嗎？
A: 建議提前整理出：
1. **目前的人工作業流程與痛點**（例如：每週需花費 4 小時手動比對 ERP 報表與電子發票）。
2. **期望達成的自動化效果**（例如：系統能自動收信、下載發票、辨識金額並與 ERP 沖帳，異常時通知會計）。

哪怕只有文字大綱或螢幕截圖，只要提前傳給講師，便能方便講師事先準備相關案例，讓課程診斷更貼近您的需求！ *[標籤: 專案診斷, 課前準備]*
