# Astralis HLTV → Live iCal on Vercel

Serves a live-updating `.ics` calendar at `/api/astralis.ics` with upcoming **Astralis** matches from HLTV.
- Default team: Astralis (ID `6665`)
- Override with env var: `ASTRALIS_TEAM_ID`
- Timezone set to `Europe/Copenhagen` (clients still see local time automatically)
- Caches responses to reduce HLTV requests

## 5-minute deploy (no experience needed)

### Option A — **Drag & drop** (no Git required)
1) Download and unzip this project.
2) Go to https://vercel.com/new — sign in (free) with GitHub/Google.
3) Drag the **whole folder** into the page to deploy.
4) After deploy finishes, open:
   `https://<your-project>.vercel.app/api/astralis.ics`
5) Subscribe to that URL in Google/Apple/Outlook Calendar.

> If drag & drop isn't visible, use Option B (GitHub import).

### Option B — **GitHub import** (recommended)
1) Create a new GitHub repo (any name).
2) Upload the files from this folder to that repo.
3) In Vercel, click **Add New… → Project → Import Git Repository** and pick your repo.
4) Accept defaults. (Framework: **Other**, Root: `/`)
5) Click **Deploy**. Your feed will be at:
   `https://<your-project>.vercel.app/api/astralis.ics`

### Optional: set a different team
- In Vercel → **Settings → Environment Variables**, add:
  - `ASTRALIS_TEAM_ID = 6665` (or another team id from the HLTV URL).
- Redeploy (or trigger a redeploy), the API will use that ID.

## Subscribe in your calendar
- **Google Calendar:** Settings → Add calendar → From URL → paste the link.
- **Apple Calendar (Mac/iPhone):** File → New Calendar Subscription → paste the link.
- **Outlook:** Add calendar → Subscribe from web → paste the link.

## Notes
- Each match defaults to a 2-hour block (edit in `lib/buildCalendar.js`).
- HLTV times are UTC; calendars display in your local time.
- If the `hltv` package ever breaks due to site changes, just redeploy after updating dependencies.
