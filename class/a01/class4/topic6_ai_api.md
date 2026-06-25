# 主題六：AI API 呼叫三大模式實戰

本主題旨在引導學員掌握當前主流的雲端、地端與瀏覽器原生三大 AI 呼叫技術，並提供最乾淨、符合企業實戰的前端 JavaScript/Fetch 程式碼範例與技術解構，讓學員可以直接在瀏覽器控制台 (Console) 或靜態網頁中貼上實測。

---

## 🚀 呼叫 AI 的三大運用模式：雲端、地端與瀏覽器原生 (Cloud vs Local vs Edge)

在進行 AI App 的實戰開發前，我們必須先掌握「如何呼叫 AI」的底層技術路徑。根據系統架構、資安防護、成本預算與運算延遲的不同， AI 呼叫主要分為以下三大經典模式。

### 1. 雲端 AI 呼叫：Google Gemini API (Cloud-based LLM)
*   **技術定位**：商業級雲端大模型 API。
*   **優勢**：模型推理解析力最強（如 Gemini 2.0 Flash / Flash-Lite），支援高達 200 萬 Token 的超長上下文 (Context Window)，具備強大的多模態（圖片、語音、影片）理解力，且完全免去本地硬體配置負擔。
*   **劣勢**：必須連接網際網路、有 API 調用成本 (按 Token 計費)、敏感數據直接送往雲端需注意隱私合規。

*   **💡 實戰指引：手把手申請與複製 Gemini API Key 步驟**：
    在呼叫 API 之前，學員必須先取得專屬的 API Key。請遵循以下 7 個步驟進行申請與確認：
    
    1. **步驟一：前往 Google AI Studio 官方入口**
       請在瀏覽器搜尋「Google AI Studio API key」，或直接點選訪問 [https://aistudio.google.com/api-keys](https://aistudio.google.com/api-keys)。
       ![步驟一：搜尋並進入 Google AI Studio](images/gemini_api_key_step1.png)
       
    2. **步驟二：點擊創建 API Key**
       進入後台的「API Keys」介面後，點擊右上角紫色的 **「Create API key」** 按鈕。
       ![步驟二：點擊 Create API key 按鈕](images/gemini_api_key_step2.png)
       
    3. **步驟三：輸入 Key 的名稱與專案**
       In 彈出的視窗中，為您的 API Key 命名（例如：`Gemini API Key - 20260625`），並選擇或創建您的 Google Cloud 專案。
       ![步驟三：為 API Key 命名與選擇專案](images/gemini_api_key_step3.png)
       
    4. **步驟四：確認生成金鑰**
       點擊彈出對話框右下角的 **「Create key」** 按鈕。
       ![步驟四：點擊 Create key 確認生成](images/gemini_api_key_step4.png)
       
    5. **步驟五：複製並安全保存金鑰**
       生成成功後，會顯示您的專屬 API Key（`AQ...`），點擊右下角的 **「Copy key」** 按鈕即可複製。請將此 Key 妥善保存，切勿公開洩漏！
       ![步驟五：點擊 Copy key 複製並安全保存](images/gemini_api_key_step5.png)
       
    6. **步驟六：隨時管理與確認付費級別**
       回到金鑰列表中，您可以看見已建立的金鑰。請確認其 **Billing Tier 為「Free tier (免費級別)」**。此處不需綁定信用卡，學員即可安心進行免費額度內的 API 測試。您隨時可以點擊列表中的「Copy key (複製圖示)」重新複製金鑰。
       ![步驟六：於列表中管理金鑰並確認 Free tier 級別](images/gemini_api_key_step6.png)
       
    7. **步驟七：觀測與監控 API 使用量與 Token 消耗**
       在 API Key 列表中，點擊金鑰右側紫色的 **「用量統計按鈕 (圖表圖示)」**。
       ![步驟七：點擊用量統計按鈕](images/gemini_api_usage_step1.png)
       
       這會引導您進入 **「Gemini API Usage (用量統計頁面)」**。在此頁面中，您可以即時觀測 Total API Requests (請求次數)、Total API Errors (錯誤次數)，以及每個模型的 Input/Output Tokens 消耗趨勢。這對於我們實作 AI 專案時進行 **「落地經濟學 (Economics)」** 的 Token 成本控制與用量監控至關重要！
       ![用量統計頁面：即時監控 Token 消耗與請求次數](images/gemini_api_usage_step2.png)

*   **實戰前端 JavaScript 呼叫代碼**：
```javascript
// ☁️ 雲端 AI: Google Gemini API 呼叫範例 (使用最新的 Gemini 2.0 Flash)
async function callGemini(promptText, apiKey) {
  // 建立 Gemini REST API 端點 URL (包含 API Key，指定最新的 gemini-2.0-flash 模型)
  const url = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;
  
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

// 💡 實測呼叫：填入您的 API Key 即可在控制台運行
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
