# Crew log

Newest first. One entry per session.

## 2026-09-09 — Sidebar becomes a triage queue

Ops built it, Mech reviewed layout, Scribe reviewed copy, Vera ran all of it in headless Chromium at 1200px and 390px. All 20 checks passed, no console errors.

- Hero count of what needs the owner. Green zero when the queue is clear.
- Groups: Needs you, Ready to send, Done. Sorted most recent first within each.
- Drafted rows show the reply and send it with one tap. "Send all" with a confirm step.
- Every conversation carries a `source` (all Messenger for now). Shown on the row and in the panel.
- Health flag is data on the conversation and survives reopen. Scribe caught that reopen was dropping it.
- Mech: compact button rule was declared twice and silently beat the mobile override. One rule now, 35px tap targets on phones. Unread dot only red on needs-you rows.
- Scribe: "Resolve" and "Done" were one state with two names, "Draft" and "Reply" one thing with two. One name each now.
- Dropped the duplicate `tag` field; `status` is the one source of truth.

Not verified: iOS Safari on a real phone.

Next: the first real channel. Messenger, most likely. The queue has done what it can on fake data.

## 2026-09-09 — Fix the prototype's broken bits

Ops did the fixes (single file, frontend only). Vera verified in headless Chromium at desktop and 390px, no console errors. She caught one miss: an edited draft was still sent as the original after Done Editing. Fixed and re-run.

- Filter tabs ignored clicks on the count number inside them. Click now resolves to the tab.
- Edit Draft needed two clicks to open. Now toggles a class instead of reading inline style. Approve always sends what's in the editor, edited or not.
- Nothing was HTML-escaped. Customer messages, names, drafts and typed replies now go through `esc()`. Typed script no longer runs.
- Reopening a conversation claimed the AI had held it for a health reason. Hold reason is now data (`holdReason`) and the copy only says "health" when it's true.
- Spam couldn't be undone. Spam now has Reopen like resolved does.
- Layout used `100vh`; added `100dvh` so the reply box isn't under Safari's chrome on iOS. Not verified on a real phone.

Next: decide the real data source (Messenger? email? Shopify inbox?). The UI has gone as far as it can on fake data.
