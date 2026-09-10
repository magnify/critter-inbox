# Crew log

Newest first. One entry per session.

## 2026-09-10 — Design pass; real shop taken out

Mech rebuilt the stylesheet alone. Vera ran 19 checks at 1200px and 390px, 18 passed; the one miss (the clickable-tile cue Mech had removed) was put back as a quiet chevron and re-rendered.

- Token layer: colour, ink scale, one accent, alert/ok with soft tints, five type sizes plus two display sizes, 4px spacing scale, two radii, two control heights. Every hardcoded value in the file goes through it.
- Facebook blue is gone as the interface accent. The chart keeps its validated green/blue pair on its own token.
- Underline tabs and a segmented nav instead of pill buttons. One button system, three variants, regular and compact. Draft and needs-you boxes share the card language with a colour stripe. Chrome emoji out; small inline SVGs where a button had no words.
- The real shop and its owner are no longer named anywhere in the working tree. Research file deleted, brief and log reworded, sample replies say "vi". They remain in git history three commits back; rewriting that is the owner's call.
- Contrast checked: all text meets 4.5:1 on its surface, accent-on-white button text passes.

Not verified: iOS Safari on a real phone.

Next: unchanged. Wire the first real channel.

## 2026-09-10 — Overview as the landing view; the product becomes the client's

Ops built the overview. Doc researched the shop. Scribe rewrote data and copy in Danish. Mech reviewed layout. Vera ran 14 checks at 1200px and 390px, all passed, no console errors.

- New landing view: Overblik. Tiles for Kræver dig, Klar til at sende, Sendt i dag (AI vs dig), Åbne samtaler by channel. The flagged conversations listed right there. A week of replies per day as a stacked bar (sample numbers until a channel is wired; marked in code).
- Top bar with Overblik / Indbakke and a red count on Indbakke.
- Doc researched the client: a Danish New Caledonian gecko breeder with one owner, on Facebook. No prices, hours or address are published anywhere. The research file was removed from the repo the next session; the real shop is not to be named here.
- Scribe: all ten conversations are now the shop's customers about kronegekkoer, chahoua, leachianus, daggekkoer, bænkebidere and bioaktive setups. Whole interface in Danish, "du". One name per concept. Only one draft quotes a price and the array carries a comment saying prices are invented. One conversation on Instagram to show the multi-channel shape.
- Mech: nav tap targets on phones, arrows on the clickable tiles, red/green number colours as one pair of variables, two dead rules removed.
- Sent-today attribution: an unedited AI draft counts as AI, an edited one or a manual reply counts as you.

Not verified: iOS Safari on a real phone.

Next: wire Messenger. The prototype has nothing left to prove on fake data. Second: the health classifier and a small price/stock table the owner keeps, so drafts only quote what they've written down.

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
