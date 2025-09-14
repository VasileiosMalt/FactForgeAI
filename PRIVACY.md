# Privacy Policy for FactForge AI (Chrome Extension)
Last updated: 2025-09-14

Summary
FactForge AI is an AI‑assisted fact‑checking extension. I do not collect, sell, or share personal data. The extension runs locally in your browser; network requests go directly to the services you choose (AI provider and DuckDuckGo) to perform analysis.

Data We Process
- User input: The text you analyze (typed or selected) is sent only to your chosen AI provider and to DuckDuckGo for search queries.
- Page access: A content script injects UI to display results. It does not transmit page content unless you explicitly submit text for analysis.
- API keys: Stored only in Chrome Sync (scoped to your Google account). Not sent to the developer.
- History & stats: Stored only on your device via Chrome storage (local). You can clear them anytime in the extension.

What We Do Not Do
- No telemetry or analytics.
- No selling or sharing of data with data brokers or advertisers.
- No remote code execution; the extension does not load or execute code from the network (only data is fetched).

Third‑Party Services
When you use the extension, data necessary to perform analysis is sent directly from your browser to:
- Search/credibility: DuckDuckGo (api.duckduckgo.com), Media Bias/Fact Check (mediabiasfactcheck.com), and selected news/fact‑check sites (e.g., reuters.com, apnews.com, bbc.com, npr.org, snopes.com, politifact.com, factcheck.org).
- AI providers you select: GitHub Models (models.inference.ai.azure.com), OpenRouter, OpenAI, Groq, GLHF, Chutes, Hugging Face.
These services have their own privacy policies and may process/store data per their terms. Your queries may be transferred outside your country depending on provider infrastructure.

Permissions (Why They’re Needed)
- activeTab, scripting, tabs: Inject the overlay and communicate with the current tab when you initiate actions.
- contextMenus: “FactForge AI: Fact‑Check This” on selected text.
- sidePanel: Show results in Chrome’s Side Panel.
- storage: Save settings, API keys (sync), local history/stats (local).
- downloads: Export a .txt report on your request.
- host_permissions: Fetch credibility data, search results, and contact AI provider APIs you select.

Storage & Retention
- API keys: Chrome Sync only (optionally end‑to‑end encrypted if you enable a sync passphrase).
- History/stats: Local only. Up to ~500 recent checks (and score history) for convenience. Clear anytime in Options.
- We (the developer) do not receive or store your API keys, texts, or results on our servers.

Children’s Privacy
This extension is not directed to children and should be used by individuals able to review and accept provider terms.

Your Controls
- Clear data: Use the extension’s Options or History clear action to remove local history/stats.
- API keys: Add/remove in Options. Keys are stored only in Chrome Sync.
- Uninstall: Removes local data stored by the extension in your browser profile.

Security
- Manifest V3 service worker; no remote code execution.
- Network requests over HTTPS to declared host domains only.
- Best‑effort sanitization of fetched text before UI rendering; ongoing hardening to minimize injection risks.
- Recommend enabling a Chrome Sync passphrase to further protect API keys.

Changes to This Policy
I may update this policy. Material changes will be reflected by updating the “Last updated” date and changelog in the repository.
