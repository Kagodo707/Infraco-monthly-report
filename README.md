# Equatorial Power Energy Dashboard — Published Google Sheet Version

This package is the revised GitHub-ready dashboard built for the published Google Sheet workflow.

## What changed in this version

- All core visuals use **bar charts** for consistency.
- **Uptime**, **SAIFI**, and **SAIDI** are each shown as independent charts.
- **Revenue** is now its own independent bar chart.
- **ARPU** and **Consumption per User** are each independent charts.
- **Generation vs Consumption** remains a grouped bar chart, and it uses **Victron consumption** when comparing to generation.
- **Planned Consumption vs Achieved Consumption** uses **Sparkmeter consumption** as the achieved value.
- **Planned Revenue vs Actual Revenue** is independent from the consumption planning chart.
- **PV Generation vs DG Generation** and **Fuel Planned vs Fuel Consumed** are separated into independent Bugarula charts.
- KPI cards always show the **latest month inside the active filter**, not a 3‑month sum.
- Executive insights are generated from the same active filter scope.
- The **Latest Available Site Table** always pins to the latest month available in the active horizon filter.

## Files

- `index.html` — complete static dashboard
- `.nojekyll` — ensures GitHub Pages serves the site without Jekyll assumptions

## Data connection logic

The dashboard reads directly from the published Google Sheet using tab names.

Configured tabs:

- `Bugarula`
- `Bunyakiri`
- `Buyumbu`
- `Kashiraboba`
- `Mugote`
- `Categorical consumption`

The live URLs are built in the browser as:

```text
https://docs.google.com/spreadsheets/d/<SHEET_ID>/gviz/tq?tqx=out:csv&sheet=<TAB_NAME>
```

If you prefer published CSV links by `gid`, you can fill the `gidOverrides` block in `index.html`.

## GitHub Pages deployment

Recommended repository name:

```text
equatorial-power-energy-dashboard
```

Suggested structure:

```text
/
  index.html
  .nojekyll
```

Deployment steps:

1. Create a new repository under the `kagodo` GitHub account.
2. Upload `index.html` and `.nojekyll` to the repository root.
3. Open **Settings → Pages**.
4. Set the publishing source to the **main** branch and the **root** folder.
5. Save.
6. GitHub Pages will publish the dashboard at:
   `https://kagodo.github.io/<repository-name>/`

## Operating notes

- The dashboard is static and requires no backend.
- If the published sheet updates, the dashboard refreshes from Google Sheets when the page is reloaded or when the **Refresh dashboard** button is clicked.
- If a live tab fails to load in the browser, the page falls back to bundled sample data so the interface still renders.
- The site comparison charts always stay in the dashboard even when the display mode is set to **Selected site only**. That is deliberate because those charts are portfolio comparison views for the latest month.

## Recommended next step

Push this package to a dedicated GitHub repository and test the live data load from the published sheet. If every tab resolves cleanly, you can keep the current setup exactly as it is.
