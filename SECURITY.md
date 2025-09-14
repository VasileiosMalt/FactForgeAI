# Security Policy — FactForge AI (Chrome Extension)

Last updated: 2025-09-14

Overview
FactForge AI is a Chrome extension for AI‑assisted fact‑checking. It runs as a Manifest V3 extension with a background service worker, a content script UI overlay, a popup, and an optional Side Panel.

Supported Versions
- No Support provided

Threat Model and Attack Surface
- Primary surfaces:
  - Content script UI injected into web pages (content.js + content.css)
  - Background service worker (background.js) fetching from search/credibility sites and AI APIs
  - Options/popup/side panel pages (options.html, popup.html)
- No remote code execution: the extension does not load or execute code from the network. It only fetches data (search results, page excerpts, AI responses).
- No eval/Function/new Function, no inline event listeners created by extension code.

Permissions and Why They’re Needed
- activeTab, scripting, tabs: Inject overlay and communicate with the active tab on user action.
- contextMenus: “Fact‑Check This” on selected text.
- sidePanel: Show results in Chrome’s Side Panel.
- storage: Save user settings/API keys (sync) and local history/stats (local).
- downloads: Export a .txt report.
- host_permissions: Fetch data from credibility/news sites (e.g., MBFC, Reuters, AP, Snopes, PolitiFact, FactCheck.org), DuckDuckGo, and AI providers (GitHub Models, OpenRouter, OpenAI, Groq, GLHF, Chutes, Hugging Face).

Data Handling and Privacy
- API keys: Stored only in chrome.storage.sync (Google account–scoped). Not transmitted to the developer or any third party except the relevant AI provider you select. Consider enabling a Chrome sync passphrase for E2E encryption.
- User inputs and results: Sent only to the chosen AI provider and DuckDuckGo. History and stats are stored locally via chrome.storage.local.
- No telemetry/analytics. No data sale or transfer.
- Downloads: Reports are generated locally and saved via the Chrome downloads API.

Network Endpoints (non-exhaustive)
- Search/credibility: api.duckduckgo.com, mediabiasfactcheck.com, reuters.com, apnews.com, bbc.com, npr.org, snopes.com, politifact.com, factcheck.org
- AI providers: models.inference.ai.azure.com (GitHub Models), openrouter.ai, api.openai.com, api.groq.com, glhf.chat, llm.chutes.ai, huggingface.co

Secure Development Practices
- Manifest V3 service worker model (no background pages)
- No remote code execution, no dynamic code eval
- Network requests restricted to declared host_permissions
- Least-privilege messaging between popup/options/content/background
- Best‑effort HTML text extraction from pages with tag stripping in background.js to avoid forwarding raw HTML
- Packaged resources only; no CDN runtime scripts

Known Risks and Mitigations
- Untrusted text in UI:
  - Risk: AI responses and extracted snippets are user-/network-sourced. Some UI is assembled with innerHTML in content.js.
  - Mitigations (current): Many fetched page excerpts are stripped to text in background.js (fetchPageContent removes tags).
- Content script scope:
  - Risk: content script is registered on <all_urls> to enable overlay quickly.
  - Improvements (planned): Restrict automatic injection; prefer programmatic injection (chrome.scripting) on user gesture; consider declarativeContent rules to limit matches.
- Host permissions breadth:
  - Risk: Multiple news/credibility/AI domains are permitted.
  - Mitigations (current): Only data requests are performed; no code is executed from these hosts.
- Third‑party service retention:
  - Note: AI providers and DuckDuckGo may retain queries/logs per their policies. Users should review provider terms.

Supply Chain
- No runtime npm dependencies for the extension codebase.
- All executable code is bundled within the extension package.

Hardening Recommendations for Users
- Keep the extension updated.
- Enable a Chrome sync passphrase to protect API keys in chrome.storage.sync.
- Use provider accounts with appropriate rate limits and access controls.
- Review and clear local history in Options when needed.

Reporting a Vulnerability
- Please use GitHub Security Advisories (Security tab → “Report a vulnerability”) for private disclosure.
- Include:
  - Affected version/commit
  - Reproduction steps, PoC, and impact
  - Suggested remediation if available
- We aim to acknowledge within 2 business days and provide a remediation timeline after triage.
- Coordinated Disclosure: We prefer coordinated disclosure and will credit reporters upon request after a fix is released.

Change Log for Security-Relevant Updates
- v2.0: MV3 service worker; expanded provider support; improved tag stripping for fetched page excerpts; no telemetry.
- Planned: Full sanitization/escaping in content UI; narrower content script scope; configurable host permissions.
