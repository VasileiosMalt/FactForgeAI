# FactForge AI — Chrome Extension

AI-powered fact-checking with optional real-time web research across multiple AI providers. Delivers a Truth Score, confidence level, evidence synthesis, and annotated sources with credibility signals.

Version: 2.0.0

- Chrome Web Store: 
- Documentation: 

---

## Quick Start

1) Install from the Chrome Web Store.
2) Open the extension and click Settings to add at least one API key (GitHub Models, OpenRouter, OpenAI, Groq, GLHF, or Chutes).
3) Choose Provider, Model, and Analysis Depth.
4) Paste or select text and click Analyze.
5) Optionally right‑click selected text on any page → “FactForge AI: Fact-Check This”.

Keyboard shortcuts:
- Popup: Ctrl/Cmd+Enter to analyze, Esc to clear.
- Options: Ctrl/Cmd+S to save, Ctrl/Cmd+T to test all providers.

---

## Features

- Multi‑provider AI: GitHub Models, OpenRouter, OpenAI, Groq, GLHF, Chutes (Claude).
- Smart research pipeline:
  - Quick knowledge check.
  - Query generation (multi‑lingual normalization and heuristics).
  - DuckDuckGo search with HTML fallback parsing.
  - Best‑effort content excerpts and relevance scoring.
  - Consolidated analysis and consensus estimation.
- Evidence‑driven reporting:
  - Truth Score (0–100) with confidence badge.
  - Supporting vs. contradicting evidence, limitations, risk level, category.
  - Annotated sources with badges (Recent, Fact‑check, Relevance score).
  - Media Bias/Fact Check (MBFC) lookup with bias/factual/credibility indicators.
- In‑page overlay and Side Panel UI.
- History and usage stats (local only).
- Export, copy, and share:
  - Download .txt reports.
  - One‑click copy/share text.
- Model discovery: fetch model lists for your provider (when API allows).

---

## How It Works (High‑Level)

1) Normalize claim text (translate to concise English when needed).
2) Generate compact, targeted search queries (heuristics + AI validation).
3) Perform DuckDuckGo search (JSON API + HTML fallback) and collect results.
4) Best‑effort fetch of short content excerpts where host permissions allow.
5) Score relevance, identify fact‑check and authoritative sources.
6) Ask the selected model to produce an evidence‑weighted assessment JSON.
7) Calibrate Truth Score with source quality, consensus, and knowledge check.
8) Render a rich in‑page modal with results, methodology, sources, and actions.

Providers supported (by API): GitHub Models, OpenRouter, OpenAI, Groq, GLHF, Chutes; optional Hugging Face endpoints for model lists.

---

## Permissions and Rationale

- storage: Save API keys (sync), settings (sync), and local history/stats.
- activeTab, scripting, tabs: Inject or message the content script to show the in‑page UI.
- contextMenus: Right‑click “Fact-Check This”.
- sidePanel: Open the Side Panel UI from the toolbar button.
- downloads: Export .txt reports.
- host_permissions:
  - Fact‑check and news domains (e.g., reuters.com, apnews.com, bbc.com, npr.org, snopes.com, politifact.com, factcheck.org).
  - MBFC (mediabiasfactcheck.com) for credibility lookups.
  - AI provider endpoints (GitHub Models, OpenRouter, OpenAI, Groq, GLHF, Chutes, Hugging Face).
  - Used strictly for model calls, search result enrichment, and MBFC metadata.

Note: Content excerpts are best‑effort and limited by host permissions; when unavailable, titles/snippets are used.

---

## Privacy

- API keys are stored in Chrome’s sync storage and used only to call the chosen AI provider APIs.
- Text you analyze and generated queries are sent to your selected AI provider and DuckDuckGo.
- Local‑only data:
  - Fact‑check history and usage stats in chrome.storage.local.
- No telemetry, tracking, or external proxy is used by the extension.

---

## Usage

- Popup
  - Choose Provider, Model (auto‑fetched when possible), and Depth (Quick/Standard/Detailed).
  - Paste a claim (≤ 2000 chars) and Analyze.
  - View status; result opens both in the page (overlay) and in History.
- In‑Page Overlay
  - Truth Score dial, confidence, statement, summary, supporting/contradicting evidence, sources with badges and MBFC info.
  - Actions: Copy, Share, Save Report, Close (Esc to close).
- History & Stats
  - Recent checks with score and confidence; open detail, copy, download, or show in page.
  - Stats: total checks, average score, high‑confidence rate.
- Settings
  - Add API keys per provider; Test Connection to fetch model lists.

---

## Troubleshooting

- Missing API key: Configure in Settings; ensure the correct provider is selected.
- Model list not loading: Some providers restrict listing; use known model IDs or try again.
- In‑page overlay not appearing: Some pages block content scripts (e.g., chrome://, store pages). Try another tab or use the History modal.
- “Text too long”: Limit is 2000 characters.
- Rate limits (429) or 401/403: Check plan, key validity, and usage.

---

## Limitations

- Not a definitive fact checker; results rely on third‑party models and public web data.
- Content fetch is constrained by host permissions and site access rules.
- Real‑time search quality varies by query; consensus can be “insufficient_data”.
- MBFC metadata is best‑effort; site pages may change.

---

## Changelog (v2.0)

- Multi‑provider pipeline with model auto‑detection.
- Real‑time web research with DDG JSON and HTML fallback.
- Evidence synthesis and calibrated Truth Score/confidence.
- MBFC integration and source credibility badges.
- In‑page modal UX, Side Panel, History, and Stats.
- Export/share flows and refined error guidance.

---

## FAQ

- Does it cost money?
  - The extension is free; provider API usage may incur charges depending on your account/plan.
- Do you store or transmit my keys?
  - Keys remain in Chrome’s sync storage and are only used to call the selected APIs.
- Does it work offline?
  - No. It requires network access to AI providers and search endpoints.
- File URLs?
  - Enable “Allow access to file URLs” in Chrome extension details to analyze local files.

---

## Acknowledgments

- DuckDuckGo for search endpoints and HTML results fallback.
- MediaBias/FactCheck for credibility pages.
- AI providers: GitHub Models, OpenRouter, OpenAI, Groq, GLHF, Chutes, and Hugging Face.

---

## Legal

- For informational purposes only; not legal, medical, or financial advice.
- Verify claims with primary sources. The extension has only assistive character.
- Respect site Terms of Service when following links and using data.

---

## Support

- Issues/feedback: Use the Chrome Web Store support form or your preferred contact channel.
- Documentation updates and screenshots: Maintain on this GitHub Wiki page.
