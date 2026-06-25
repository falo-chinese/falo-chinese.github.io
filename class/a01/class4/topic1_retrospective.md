# 主題一：前三堂課程交流與補充

本主題旨在對前三週的學習重點進行深度沉澱與補充，並針對同仁在實務開發中遇到的盲點進行診斷與解答。

---

## 📌 常見提醒與交付規範 (台灣時間 UTC+8)
> [!IMPORTANT]
> 本課程與專案之所有宣告、作業交付截止日期等時間，皆**統一宣告並以台灣時間 (UTC+8) 為唯一準則**。

* **雙軌標準規範 (md + html)**: 所有提問集、作業及大綱，必須同時提交 **Markdown (.md)** 檔（供 AI/LLM 結構理解）與 **HTML (.html)** 網頁檔（供人類閱讀），落實雙軌並行標準。
* **壓縮包命名習慣 (ZIP 檔案)**: 凡提交程式碼或專案資源壓縮包時，請遵循 **「[時間戳記]_[重要更新事項].zip」** 命名規範（例如：`20260622_class04_project.zip`）。

---

## 🚀 呼叫 AI 的三大運用模式：雲端、地端與瀏覽器原生 (Cloud vs Local vs Edge)

在進行 AI App 的實戰開發前，我們必須先掌握「如何呼叫 AI」的底層技術路徑。根據系統架構、資安防護、成本預算與運算延遲的不同，AI 呼叫主要分為以下三大經典模式。

本章節將針對這三種模式，提供最乾淨、符合企業實戰的前端 JavaScript/Fetch 程式碼範例與技術解構，讓學員可以直接在瀏覽器控制台 (Console) 或靜態網頁中貼上實測。

### 1. 雲端 AI 呼叫：Google Gemini API (Cloud-based LLM)
*   **技術定位**：商業級雲端大模型 API。
*   **優勢**：模型推理解析力最強（如 Gemini 1.5 Pro / Flash），支援高達 200 萬 Token 的超長上下文 (Context Window)，具備強大的多模態（圖片、語音、影片）理解力，且完全免去本地硬體配置負擔。
*   **劣勢**：必須連接網際網路、有 API 調用成本 (按 Token 計費)、敏感數據直接送往雲端需注意隱私合規。
*   **實戰前端 JavaScript 呼叫代碼**：
```javascript
// ☁️ 雲端 AI: Google Gemini API 呼叫範例 (使用 1.5 Flash)
async function callGemini(promptText, apiKey) {
  // 建立 Gemini REST API 端點 URL (包含 API Key)
  const url = `https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent?key=${apiKey}`;
  
  const payload = {
    contents: [{
      parts: [{ text: promptText }]
    }]
  };

  try {
    const response = await fetch(url, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify(payload)
    });
    
    const data = await response.json();
    // 從回傳的結構中精準萃取生成的文字內容
    const generatedText = data.candidates[0].content.parts[0].text;
    console.log("Gemini 輸出：\n", generatedText);
    return generatedText;
  } catch (error) {
    console.error("Gemini 呼叫失敗：", error);
  }
}

// 💡 實實測呼叫：填入您的 API Key 即可在控制台運行
// callGemini("請用繁體中文解釋什麼是 RAG 技術？", "YOUR_GEMINI_API_KEY");
```

---

### 2. 地端 AI 呼叫：Ollama 服務 (Local-based LLM)
*   **技術定位**：地端部署之開源模型伺服器。
*   **優勢**：100% 數據隱私安全（敏感商業資料完全不出企業內網）、零 Token 調用費用、可在無外網連線的物理隔離環境下穩定運作。
*   **劣勢**：極度依賴本地硬體算力（需要足夠的 GPU 顯示卡與視訊記憶體），且本地部署的模型參數規模（如 8B, 14B）其推理能力與雲端超大型模型相比仍有差距。
*   **實戰前端 JavaScript 呼叫代碼**：
```javascript
// 🏠 地端 AI: Ollama 本地 API 呼叫範例 (非串流模式)
async function callOllama(promptText, modelName = 'llama3') {
  // 本地 Ollama 預設的生成端點
  const url = 'http://localhost:11434/api/generate';
  
  const payload = {
    model: modelName,
    prompt: promptText,
    stream: false // 💡 設定為 false 關閉串流，直接返回完整 JSON，便於前端解析
  };

  try {
    const response = await fetch(url, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify(payload)
    });
    
    const data = await response.json();
    const generatedText = data.response;
    console.log("Ollama 輸出：\n", generatedText);
    return generatedText;
  } catch (error) {
    console.error("Ollama 本地連線失敗，請確保本地 Ollama 已啟動且跨來源資源共用 (CORS) 已放行！\n錯誤資訊：", error);
    // 💡 避坑指引：若在前端網頁中直接 fetch 本地 API 遇到 CORS 阻擋
    // macOS/Linux 環境下請在啟動 Ollama 前，於終端機執行：export OLLAMA_ORIGINS="*"
    // Windows 環境下請在系統環境變數中新增 OLLAMA_ORIGINS 變數，值設定為 *，然後重啟 Ollama
  }
}

// 💡 實測呼叫：確保本地已執行 `ollama run llama3`
// callOllama("請用繁體中文自我介紹。");
```

---

### 3. 瀏覽器原生 AI 呼叫：Chrome built-in AI (Edge-based LLM)
*   **技術定位**：端側邊緣運算 (Edge AI)，大模型直接內嵌並運行於使用者的瀏覽器沙盒中。
*   **優勢**：真正的零伺服器運維成本、零網絡頻寬依賴（完全在使用者本地設備 CPU/NPU 運行）、極高隱私度，能大幅度減輕企業伺服器的算力負載。
*   **劣勢**：屬於極限輕量化模型（Gemini Nano 約 1.8B–3.2B 參數），僅適合進行簡易的文本摘要、翻譯、改寫、情感分析或意圖分類任務；目前僅限特定版本 Chrome 瀏覽器，且使用者需手動啟用實驗性 Flag。
*   **實戰前端 JavaScript 呼叫代碼**：
```javascript
// 🌐 瀏覽器原生 AI: Chrome built-in AI (Gemini Nano) 呼叫範例
async function callChromeNano(promptText) {
  // 1. 偵測瀏覽器是否支援且已啟用內建 AI API (W3C 草案標準)
  if (!window.ai || !window.ai.languageModel) {
    console.warn("當前瀏覽器不支援 Chrome 內建 AI。\n請確保使用的是 Chrome M127+，且已在 chrome://flags 啟用 'Built-in AI' 與 'Prompt API'。");
    return;
  }

  try {
    // 2. 檢查內建模型是否就緒與可用性
    const capabilities = await window.ai.languageModel.capabilities();
    if (capabilities.available === "no") {
      console.error("內建 Gemini Nano 模型尚未下載或無法在當前系統環境下使用。");
      return;
    }

    // 3. 建立 AI 會話 Session
    console.log("正在初始化 Chrome 內建 Gemini Nano Session...");
    const session = await window.ai.languageModel.create();

    // 4. 發送 Prompt 請求並取得回應 (非串流)
    console.log("發送 Prompt...");
    const response = await session.prompt(promptText);
    console.log("Chrome Nano 輸出：\n", response);
    
    // 5. 💡 避坑指引：使用完畢後務必摧毀 Session 以釋放瀏覽器記憶體
    session.destroy();
    return response;
  } catch (error) {
    console.error("Chrome Nano 執行失敗：", error);
  }
}

// 💡 實測呼叫：在符合條件的 Chrome 控制台直接執行
// callChromeNano("請將這句話翻譯成英文：今天天氣真好。");
```

---

## 💬 主軸 1：前三週重點補充與問題解答
### 1. 人機協作模式 (HITL - Human in the Loop)
在複雜的企業流程（如 ERP 自動入帳、智慧對帳）中，AI 無法達到 100% 的精準度。因此，必須建立合理的人機協作機制：
* **AI 負責 90% 的繁重工作**：包括非結構化憑證的 OCR 辨識、初步分類、欄位清洗與比對。
* **人類負責 10% 的高風險決策**：當 AI 信心指數（Confidence Score）低於閾值（例如 85%），或是稽核引擎觸發異常警示時，系統自動將任務分流至人工審核界面，確保數據品質。

### 2. 雙軌文件策略
在 AI-Native 的開發模式下，文件不只是給人看的，更是給 AI 助理（如 Antigravity）讀取的關鍵上下文：
* **Markdown (.md)**：語意結構清晰，便於 LLM 進行 RAG 檢索、代碼生成與上下文控制。
* **HTML (.html)**：具備豐富的視覺樣式與互動效果，方便團隊成員、管理層以及客戶直觀理解。

---

## 🛠️ 主軸 3：同學專案方向交流與診斷
現場開放式的交流與診斷環節。學員可分享各自的專案構想或工作痛點，由講師現場診斷並給予可行性建議，協助同仁順利完成謝總交代的作業與功課。

### 診斷核心指標
1. **痛點真實性**：該流程是否每日重複、耗費高昂人工工時？
2. **AI 必要性**：是否必須使用 LLM 語意理解，還是傳統的 Rule-based / Regex 就能解決？
3. **資料可得性**：是否有足夠且合規的樣本數據供 AI 學習與測試？
4. **落地經濟性**：Token 消耗與運行成本是否可控？

---

## 🙋 學員課前提問與解答 (FAQ)

#### Q: 如果有想討論的專案構想，需要提前準備什麼嗎？
A: 建議提前整理出：
1. **目前的人工作業流程與痛點**（例如：每週需花費 4 小時手動比對 ERP 報表與電子發票）。
2. **期望達成的自動化效果**（例如：系統能自動收信、下載發票、辨識金額並與 ERP 沖帳，異常時通知會計）。

哪怕只有文字大綱或螢幕截圖，只要提前傳給講師，便能方便講師事先準備相關案例，讓課程診斷更貼近您的需求！ *[標籤: 專案診斷, 課前準備]*
