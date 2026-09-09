# Crew log

Newest first. One entry per session.

## 2026-09-09 — Fix the prototype's broken bits

Ops did the fixes (single file, frontend only). Vera verification in headless Chromium: pending.

- Filter tabs ignored clicks on the count number inside them. Click now resolves to the tab.
- Edit Draft needed two clicks to open. Now toggles a class instead of reading inline style.
- Nothing was HTML-escaped. Customer messages, names, drafts and typed replies now go through `esc()`. Typed script no longer runs.
- Reopening a conversation claimed the AI had held it for a health reason. Hold reason is now data (`holdReason`) and the copy only says "health" when it's true.
- Spam couldn't be undone. Spam now has Reopen like resolved does.
- Layout used `100vh`; added `100dvh` so the reply box isn't under Safari's chrome on iOS. Not verified on a real phone.

Next: decide the real data source (Messenger? email? Shopify inbox?). The UI has gone as far as it can on fake data.
