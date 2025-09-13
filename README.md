# FactForge AI — Chrome Extension

<p align="center">
  <img src="https://github.com/VasileiosMalt/FactForgeAI/blob/main/FFlogo.png?raw=true" alt="FactForge AI Logo" width="240"/>
</p>

**AI-powered fact-checking** with real-time web research across multiple AI providers.  
Get a **Truth Score**, confidence level, synthesized evidence, and sources with credibility signals — right in your browser! 🚀  

**Version:** 2.0.0  
- 🌐 Chrome Web Store:  
- 📚 Documentation:  

---

## ⚡ Quick Start

1️⃣ **Install** from the Chrome Web Store  
2️⃣ Open the extension and click **Settings** to add at least one API key (GitHub Models, OpenRouter, OpenAI, Groq, GLHF, or Chutes)  
3️⃣ Choose **Provider**, **Model**, and **Analysis Depth**  
4️⃣ Paste or select text and click **Analyze**  
5️⃣ Optionally, right‑click selected text and choose **“FactForge AI: Fact-Check This”**  

⌨️ **Keyboard shortcuts:**  
- Popup: `Ctrl/Cmd+Enter` to analyze, `Esc` to clear  
- Options: `Ctrl/Cmd+S` to save, `Ctrl/Cmd+T` to test all providers  

---

## ✨ Features

- 🤖 **Multi‑provider AI:** GitHub Models, OpenRouter, OpenAI, Groq, GLHF, Chutes (Claude)
- 🧩 **Smart research pipeline:**  
  - Quick knowledge check  
  - Query generation (multi‑lingual normalization & heuristics)  
  - DuckDuckGo search with HTML fallback  
  - Best‑effort content excerpts, relevance scoring  
  - Consolidated analysis & consensus estimation  
- 📊 **Evidence‑driven reporting:**  
  - Truth Score (0–100) with confidence badge  
  - Supporting vs contradicting evidence, limitations, risk level, category  
  - Annotated sources with badges (Recent, Fact‑Check, Relevance Score)  
  - Media Bias/Fact Check (MBFC) lookup  
- 🖥️ **UI:** In‑page overlay & Side Panel  
- 📈 **History & Stats:** Local only  
- 🔗 **Export, Copy, Share:**  
  - Download .txt reports  
  - One‑click copy/share text  
- 🧭 **Model Discovery:** Fetch model lists for your provider (when possible)  

---

## 🔍 How It Works

1️⃣ Normalize claim text (translate if needed)  
2️⃣ Generate compact, targeted search queries (heuristics + AI)  
3️⃣ Search DuckDuckGo (JSON API + HTML fallback), collect results  
4️⃣ Fetch excerpts (best‑effort, subject to permissions)  
5️⃣ Score relevance, flag fact‑check & authoritative sources  
6️⃣ Request evidence‑weighted assessment JSON from chosen AI model  
7️⃣ Calibrate Truth Score (source quality, consensus, knowledge check)  
8️⃣ Render results in‑page modal ✨  

**Supported providers:** GitHub Models, OpenRouter, OpenAI, Groq, GLHF, Chutes; optional Hugging Face endpoints.  

---

## 🔑 Permissions and Rationale

- **storage:** API keys (sync), settings (sync), local history/stats  
- **activeTab, scripting, tabs:** Inject/show in‑page UI  
- **contextMenus:** Right‑click “Fact-Check This”  
- **sidePanel:** Open main UI  
- **downloads:** Export reports  
- **host_permissions:**  
  - Fact‑check/news domains (e.g., reuters.com, apnews.com, bbc.com, npr.org, snopes.com, politifact.com, factcheck.org)  
  - MBFC for credibility lookups  
  - AI provider endpoints  
- ☑️ Used strictly for model calls, search enrichment, MBFC checks  

*Note:* Excerpts are best‑effort & limited by permissions; when unavailable, titles/snippets only.  

---

## 🛡️ Privacy

- API keys stored in Chrome sync; used only for chosen provider  
- Analyzed text & queries sent solely to your provider and DuckDuckGo  
- 🏠 **Local-only data:**  
  - Fact‑check history & usage stats in chrome.storage.local  
- No telemetry, tracking, or proxies 🚫  

---

## 🧑‍💻 Usage

### Popup
- Choose **Provider**, **Model** (auto‑fetched if available), and **Depth** (Quick/Standard/Detailed)
- Paste a claim (≤2000 chars) and click **Analyze**
- See results in overlay & History

### In-Page Overlay
- Truth Score dial, confidence, statement, summary
- Supporting/contradicting evidence, source badges & MBFC info
- Actions: Copy, Share, Save Report, Close

### History & Stats
- Recent checks: score & confidence; view details, copy/download, reopen in page
- Stats: total checks, avg score, high‑confidence %

### Settings
- Add provider API keys; Test Connection to fetch model lists  

---

## 🛠 Troubleshooting

- **Missing API key:** Go to Settings and add the necessary key  
- **Model list not loading:** Some providers restrict lists; use known IDs or retry  
- **Overlay not appearing:** Content scripts blocked on some pages (e.g., chrome://), use History modal  
- **Text too long:** Limit is 2000 chars  
- **Rate limits/errors (429/401/403):** Check key validity and usage/plan  

---

## 🚫 Limitations

- Not a definitive fact checker  
- Results rely on public web data and third‑party models  
- Extraction and search subject to host permissions  
- Consensus may be “insufficient_data” for some queries  
- MBFC parsing is best‑effort; site changes may affect results  

---

## 📝 Changelog (v2.0)

- Multi‑provider pipeline with auto model detection  
- Real‑time web research integration  
- Evidence synthesis & calibrated Truth Score  
- MBFC integration; credibility badges  
- In‑page & Side Panel UX  
- Export/share flows; clearer error messages  

---

## ❓ FAQ

- **Does it cost money?**  
  The extension is free; API usage may incur charges based on your provider plan  

- **Are my API keys stored or sent out?**  
  Keys remain in Chrome sync, used only for API calls  

- **Does it work offline?**  
  No; needs network access to providers and DuckDuckGo  

- **File URLs?**  
  Enable “Allow access to file URLs” to analyze local files in Chrome extension details  

---

## 🙏 Acknowledgments

- DuckDuckGo (search + HTML fallback)  
- MediaBias/FactCheck (credibility pages)  
- AI providers: GitHub Models, OpenRouter, OpenAI, Groq, GLHF, Chutes, Hugging Face  

---

## 🧾 Legal

- FactForge AI is provided **for informational purposes only** and is **not legal, medical, or financial advice**.
- **No warranties or guarantees**: Results are assisted by AI and public web data. Outputs may be incomplete, incorrect, out of date, or misleading.
- **You are solely responsible** for verifying all outputs and for any decisions, actions, or consequences arising from your use of the extension.
- The developer and contributors **disclaim all liability** for errors, omissions, or any losses or damages resulting from the use of this extension or reliance on its results.
- **Respect all applicable laws** and third-party terms when following links, using APIs, and sharing results.
- **By using FactForge AI, you acknowledge and accept that responsibility for verification and outcomes rests entirely with you.**

---

## 💬 Support

- Report issues/feedback via Chrome Web Store support or your preferred contact  
- Keep docs and screenshots updated on this Wiki
