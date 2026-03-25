# 7459 MORU S4 Dashboard

A real-time S4 tracking dashboard for 7459 MORU unit administration. Tracks purchase requests (PRs), budget utilization, forecasts, de-obligation and maintenance reporting across all subordinate units.

---

## Live Site

🔗 [https://7459moru.github.io/BO-Dashboard/](https://7459moru.github.io/BO-Dashboard/](https://7459moru.github.io/S4Dashboard/)

---

## Features

- **Overview** — All-units summary with LIK/SIK requested vs actual, utilization bars, and variance
- **Unit Detail** — Per-unit monthly charts, PR records, add/edit/delete PRs
- **Forecast** — Burn rate projections and quarterly spend outlook
- **Variance** — Month-by-month and unit-by-unit variance analysis
- **De-Obligation Report** — Closed PRs with leftover funds, filterable by date range, exportable to CSV
- **Active PR Tracker** — Open/Pending PRs with PR# search, highlight, and inline edit
- **3-Month Submission Forecast** — Shows which units have/haven't submitted PRs for the next 3 months
- **PR Import** — Paste directly from Excel (Pending PRs sheet) to bulk import all PRs
- **Firebase Sync** — Real-time shared editing across all users on the same network
- **Dark Mode** — Toggle in top-right corner

---

## Units Tracked

| Unit | Unit | Unit |
|------|------|------|
| 7201 | 7222 | 7409 |
| 7207 | 7224 | 7458 |
| 7217 | 7225 | 7459 |
| 7218 | 7226 | SEMARSG |
| 7221 | 7229 | |
| | 7235 | |
| | 7236 | |

---

## How to Use

### Importing PRs from Excel

1. Open your GPC Coverage Master Excel file
2. Click the **Pending PRs F26** sheet
3. Press `Ctrl+A` then `Ctrl+C` to copy all
4. In the dashboard click **Import** → **📋 Import PRs**
5. Paste with `Ctrl+V` into the text area
6. Click **✓ Import PRs**

### Adding a PR Manually

1. Click **+ Add PR** in the top bar or Unit Detail view
2. Fill in PR#, category (LIK/SIK/Supplies), status, date needed, and amount
3. Click **Save PR**

### Editing a PR

- In **Unit Detail** — click the ✎ pencil icon next to any PR row
- In **Active PR Tracker** — search by PR# and click **✎ Edit**

### De-Obligation Report

- Go to **Overview** → scroll to **💰 De-Obligation Report**
- Shows all Closed PRs with money remaining
- Filter by **All PRs**, **This Month**, or a custom **Date Range**
- Click **⬇ Export CSV** to download for supervisor review

---

## Deployment

The dashboard is a single `index.html` file. No build process required.

### To update the live site:

1. Get the new `index.html` from Claude
2. Go to the [GitHub repo](https://github.com/7459Moru/BO-Dashboard)
3. Click `index.html` → edit → upload replacement file
4. Commit changes — GitHub Pages auto-deploys within ~2 minutes
5. Hard refresh the live URL: `Ctrl+Shift+R`

---

## Firebase Configuration

The dashboard uses Firebase Realtime Database for live shared editing. The config is hardcoded in `index.html`.

- **Project:** `pr-dashboard-6cbd7`
- **Database:** `https://pr-dashboard-6cbd7-default-rtdb.firebaseio.com`

> ⚠️ Firebase rules are currently in **test mode** (open read/write). Lock down rules before sharing externally.

### Recommended Firebase Security Rules

```json
{
  "rules": {
    "lik_sik_dashboard": {
      ".read": "auth != null",
      ".write": "auth != null"
    }
  }
}
```

---

## Tech Stack

| Component | Technology |
|-----------|-----------|
| Frontend | Vanilla HTML/CSS/JS (single file) |
| Charts | Chart.js 4.4.1 |
| Database | Firebase Realtime Database v10.7.1 |
| Hosting | GitHub Pages + Netlify |
| Data Import | Excel paste (tab-delimited) |

---

## File Structure

```
BO-Dashboard/
├── index.html      # Entire application (single file)
└── README.md       # This file
```

---

## Maintained By

7459 MORU Unit S4 Administration  
