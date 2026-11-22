# Travel Manager: working rules

Single-file browser app (`index.html`), hosted on GitHub Pages at https://mkirsten583.github.io/travel-manager/. Microsoft sign-in (MSAL) and OneDrive sync; data in `Browser Tools/Travel Manager` on OneDrive.

## How to work on it
- Edit `index.html` directly and push to `main` (Pages updates in 1-2 minutes). Never delete `index.html`.
- Before pushing: syntax-check the script block, then test headless with Playwright. Stub the network (Leaflet, geocoding, routing, jsPDF, pdf.js, OneDrive) and say plainly what could not be tested live.
- After every change, send Marc the updated `index.html` (and `CLAUDE.md` if it changed) so he can save them to his NAS as a backup.
- Update the footer VERSION string when a release is meant to be recognisable.
- Ask whether to update the project's rebuild guide (`claude/travel-manager-rebuild-guide.md` in the Software Solutions project): add a change-history line and update the relevant section. Re-read the guide before writing it back.

## Things not to break
- localStorage keys are namespaced `travel-mgr-*`; all of Marc's tools share one origin, so never use un-namespaced keys.
- Keep the Azure client ID, redirect URI and OneDrive folder paths as they are unless Marc asks.
- Re-import must keep user edits, notes, attachments, pins, `via`, `valid` and Placeholder items (only items with `src:'import'` can be flagged missing).
- Text going into the PDF export must stay Latin-1 safe (see `pdfText`).

## Features Marc has asked for (do not remove)
Day / Timeline / Map / Reports / Notes views; gap highlighting (Day and Timeline); Placeholder (option) items; transport validated tick; stops on the way; real road/rail routing with diagnostics; Export PDF. Calendar and Agenda views were removed on request.
