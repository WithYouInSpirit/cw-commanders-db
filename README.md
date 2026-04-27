# CW Commanders Database

Live-updating commanders database page for Celestial Networks Clone Wars RP.

## How it works

The IPS forum page fetches `commanders.csv` from this repo on every page load.
Update the CSV here and the forum page reflects it automatically.

## Setup

### 1. Add your CSV
Export your Google Sheet as CSV and save it as `commanders.csv` in the root of this repo.

The page expects these columns (matching your existing sheet layout):
```
Column A: Commander name
Column B: (empty / section label)
Column C: Regiment
Column D: (empty)
Column E: Rank
Column F: (empty)
Column G: (empty)
Column H: Alias
Column I: Last Promotion date
Column J: Eligible (Yes / No)
Column K: Next Meeting date
```

Section headers in Column A trigger grouping:
- `REPUBLIC HIGH COMMAND`
- `PERMANENT REGIMENTS`
- `DONATOR REGIMENTS`
- `SPECIAL OPERATIONS BRIGADE`
- `DISBANDED`

### 2. IPS Setup

**HTML page:**
- AdminCP > Pages > Page Management > Pages > Create New Page
- Page type: HTML
- Paste contents of `commanders-page.html` into the content editor

**CSS:**
- AdminCP > Pages > Page Management > Templates > CSS tab > New
- Name: `cn-commanders`
- Paste contents of `commanders.css`
- Link this CSS file to your page in the page's Details tab

**No JS file needed** — the JavaScript is embedded in the HTML.

### 3. Updating the roster

Whenever your roster changes:
1. Export your Google Sheet tab as CSV (`File > Download > CSV`)
2. In this GitHub repo, click `commanders.csv` > Edit (pencil icon) > paste new content > Commit
3. The forum page will pull the new data on next load

### 4. Auto-sync (optional)

To automate updates from Google Sheets, you can set up a GitHub Action that fetches the published CSV URL and commits it. Ask your developer to set this up using `.github/workflows/sync.yml`.

## File structure

```
commanders.csv          — live roster data (update this to refresh the page)
commanders-page.html    — paste into IPS page editor
commanders.css          — paste into IPS CSS templates
README.md               — this file
```
