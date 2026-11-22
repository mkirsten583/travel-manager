# Travel Manager: working rules

Single-file browser app (`index.html`), hosted on GitHub Pages at https://mkirsten583.github.io/travel-manager/. Microsoft sign-in (MSAL) and OneDrive sync; data in `Browser Tools/Travel Manager` on OneDrive.

## How to work on it
- Edit `index.html` directly and push to `main` (Pages updates in 1-2 minutes). Never delete `index.html`.
- Before pushing: syntax-check the script block, then test headless with Playwright. Stub the network (Leaflet, geocoding, routing, jsPDF, pdf.js, OneDrive) and say plainly what could not be tested live.
- After every change, send Marc the updated `index.html` as `travel-manager-vX.Y.html` (and `CLAUDE.md` if it changed) so he can save them to his NAS as a backup.
- Versioning: the footer VERSION string reads `YYYY-MM-DD · travel manager vX.Y`. Bump it on every change (Y for each change, X for a big new area), and name Marc's backup copy `travel-manager-vX.Y.html` (the repo file itself stays `index.html`). Current: v3.6.
- Ask whether to update the project's rebuild guide (`claude/travel-manager-rebuild-guide.md` in the Software Solutions project): add a change-history line and update the relevant section. Re-read the guide before writing it back.

## Things not to break
- localStorage keys are namespaced `travel-mgr-*`; all of Marc's tools share one origin, so never use un-namespaced keys.
- Keep the Azure client ID, redirect URI and OneDrive folder paths as they are unless Marc asks.
- Re-import must keep user edits, notes, attachments, pins, `via`, `valid` and Placeholder items (only items with `src:'import'` can be flagged missing).
- Text going into the PDF export must stay Latin-1 safe (see `pdfText`).

## Features Marc has asked for (do not remove)
Day / Timeline / Map / Actions / Reports / Notes views; gap highlighting (Day and Timeline); Placeholder (option) items; Alerts view and day alert box (Open-Meteo weather, USGS earthquakes, own alerts, official links, live GDACS / P2P Quake / JMA feeds); transport validated tick; stops on the way; real road/rail routing with diagnostics; Export PDF. Calendar and Agenda views were removed on request.

## New trip checklist (country-aware Alerts and daily check)
- Alerts adapt to the country of the pinned places (`AL_CTRY` registry; unknown countries are looked up via Nominatim). To give a new country its own links, add it to `AL_CTRY`.
- When Marc starts a new itinerary: update `claude/travel-current-trip.md` in the Software Solutions project (country, dates, cities, hotels) and update the daily scheduled check's prompt so it follows the new trip. The check cannot read the app's OneDrive data.
