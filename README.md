# 7459 MORU — S4 Dashboard

A secure, real-time logistics dashboard for tracking budget, equipment status, OCIE, and purchase requests across subordinate units. Built on Firebase with role-based access control.

**Live URL:** https://7459moru.github.io/S4Dashboard/

---

## User Roles

There are three access levels. All accounts require admin approval before access is granted.

| Role | Access |
|------|--------|
| **Admin** | Full access — edit, import, manage users, view all units |
| **Battalion Viewer** | Read-only — views all units, no editing |
| **Unit Viewer** | Read-only — views own unit data only, can add/edit own notes and OCIE status |

---

## Getting Started

### Registering an Account

1. Go to the dashboard URL and click **Register**
2. Enter your full name, email, and password
3. Select your **unit** from the dropdown, or choose **Request Battalion Access** to request access to all units
4. Click **Create Account →**
5. Your account will show an **Awaiting Approval** screen until the admin approves it
6. Once approved, your dashboard loads automatically — no refresh needed

### Forgot Password

Click **Forgot password?** on the Sign In screen, enter your email, and a reset link will be sent.

---

## Admin

### Overview
- Full visibility into all units' LIK and SIK budget data
- Charts, summary tables, De-Obligation Report, Active PR Tracker, and 3-Month Forecast
- Unit filter pills to show/hide specific units
- 3-Month Forecast includes navigation controls (‹ › arrows) to view historical months

### User Management (`Users` tab)
- View all registered users with unit, access level, role, and registration date
- **Approve** or **Deny** new account registrations
- **Approve Battalion Access** or **Keep Unit Only** for battalion upgrade requests
- Promote/demote users between Admin and View Only
- Remove users from the dashboard
- Transfer the Super Admin role to another admin
- Red badge on Users nav shows count of pending approvals

### Audit Log (`Audit Log` tab)
- Full history of all actions: sign-ins, PR adds/edits/deletes, imports, note activity, user approvals
- Search by user, action, or details
- Delete individual entries — Sign In and Note Deleted entries delete instantly; all others confirm first
- **Clear Log** button wipes the entire log
- Orange badge on Audit Log nav when a viewer adds a note
- **→ View in Maintenance** button on viewer note entries navigates directly to that equipment record

### Notifications (`Notifications` tab)
- Shows all notes added by other users across all units
- Orange badge on nav for unread notifications (clears on visit)
- **→ View** button navigates to the equipment record in Maintenance

### PR Management
- Add, edit, and delete Purchase Requests from Unit Detail or the Add PR button
- Track status: Open, Pending, Closed — Categories: LIK, SIK, Supplies
- De-Obligation Report — closed PRs with leftover funds, scrollable with search
- Active PR Tracker — open/pending PRs with doc status badge:
  - 📄 **Docs Received** — PR number is not a full 10-digit number
  - ✅ **Submitted** — PR number is a full 10-digit number

### Maintenance Tab
- **Equipment Status** — full unit filter, tech/op status filters, Export CSV, Import
  - **Weapons Readiness Summary** panel at top showing FMC % and NMC % (Op Status) by unit for:
    - Rifle 5.56MM M16A2
    - Carbine 5.56MM M4A1
    - Pistol 9MM Automatic
    - Pistol 9MM Semiauto
  - Battalion totals row included
  - Hide/Show toggle for the summary panel
- **Schedule / Deadlines** — full unit filter, status filter, Export CSV, Import
- **Notes** — stacked notes per equipment record; admin can delete any note; viewers can only delete their own
- Hover any note cell to preview full text via tooltip
- Click note cell to open modal showing all stacked notes with timestamps and authors

### OCIE Tab (`OCIE`)
- Summary cards: Total Soldiers, OCIE Received %, OCIE Issued %, Without OCIE count
- Battalion Breakdown by Unit table with Received %, Issued %, Without OCIE count, and progress bar
- **Soldiers Without OCIE** — collapsed by unit, click to expand and see names
  - Inline Received/Issued toggle buttons per soldier
  - Soldier automatically removed from section when both are set to Yes
- Full soldier records table with search, unit filter, status filter, and Export CSV
- **Import Soldiers** — CSV or Excel with column mapping
- **Update Alpha Roster** — fixed column layout read from your standard roster format:
  - Col B (row 14+) → Unit
  - Col D → Soldier Name
  - Col G → Rank
  - Col U → Email
  - Col W → Phone
  - Col X → Home Phone
  - Col Y → Work Phone
  - Preserves existing OCIE status on update; adds new soldiers; skips header/metadata rows

### Unit Groupings (OCIE)
| Display Unit | Includes |
|---|---|
| 7459 | 7459, 7381 |
| 7201 | 7201 |
| 7217 | 7217, 7380 |
| 7222 | 7222 |
| 7235 | 7235 |
| 7236 | 7236, 7382 |
| 7409 | 7409 |

### Column Resizing
All major tables (De-Obligation Report, Active PR Tracker, Equipment Status, Schedule/Deadlines) support drag-to-resize columns. Hover the right edge of any column header to see the resize handle.

### Data Import
- Import equipment data via CSV on Equipment Status and Schedule/Deadlines tabs
- Import budget data via Import Data in the sidebar
- Import OCIE soldier data via the OCIE tab

---

## Battalion Viewer

### Overview
- Full view of all units' LIK and SIK data — charts, summary tables, and all widgets
- Cannot edit any PR or budget data

### Maintenance
- Equipment Status and Schedule/Deadlines — unit filter dropdown visible, can search and filter
- Notes — can add notes to any equipment record; can only delete own notes
- Import button is hidden

### OCIE
- Can view all units' soldier records and summary stats
- Cannot toggle Received/Issued status
- Cannot import soldier data

### Notifications (`Notifications` tab)
- Shows notes added by other users across all units
- Orange badge on nav for unread notifications
- **→ View** button navigates to the equipment record

---

## Unit Viewer

### Overview
- Shows **only their unit's** LIK and SIK data — charts, summary, De-Obligation, Active PR Tracker
- Unit filter pill bar is hidden
- 3-Month Forecast shows only their unit's column

### Unit Detail
- Unit dropdown is hidden — automatically loads their unit's data
- View-only charts and PR records

### Maintenance
- Equipment Status and Schedule/Deadlines filtered to their unit only
- Unit filter dropdown hidden
- Notes — can add notes to their unit's equipment; can only delete own notes
- Import button hidden

### OCIE
- Sees only their unit's soldier records and stats
- Can toggle OCIE Received/Issued for their own unit's soldiers
- Cannot import soldier data

### Notifications (`Notifications` tab)
- Shows notes added by other users on their unit's equipment only
- Own notes do not appear
- Orange badge on nav for unread notifications

---

## Features Summary

| Feature | Admin | Battalion Viewer | Unit Viewer |
|---------|-------|-----------------|-------------|
| View all units' data | ✅ | ✅ | ❌ Unit only |
| Edit / Add PRs | ✅ | ❌ | ❌ |
| Import data | ✅ | ❌ | ❌ |
| Add notes | ✅ | ✅ | ✅ Own unit |
| Delete own notes | ✅ | ✅ | ✅ |
| Delete any note | ✅ | ❌ | ❌ |
| Unit filter dropdowns | ✅ | ✅ | ❌ Hidden |
| Weapons readiness summary | ✅ | ✅ | ✅ Own unit |
| OCIE view | ✅ All | ✅ All | ✅ Own unit |
| OCIE toggle Received/Issued | ✅ | ❌ | ✅ Own unit |
| OCIE import | ✅ | ❌ | ❌ |
| Users tab | ✅ | ❌ | ❌ |
| Audit Log tab | ✅ | ❌ | ❌ |
| Notifications tab | ✅ | ✅ | ✅ |
| Approve users | ✅ | ❌ | ❌ |
| Transfer Super Admin | ✅ | ❌ | ❌ |
| Column resizing | ✅ | ✅ | ✅ |
| Historical forecast view | ✅ | ✅ | ✅ |

---

## Technical Notes

- **Database:** Firebase Realtime Database (`pr-dashboard-6cbd7`)
- **Auth:** Firebase Email/Password Authentication
- **Hosting:** GitHub Pages
- **DB Rules:** `.read: true`, `.write: auth != null`
- **Super Admin:** `alex.a.mckee.civ@army.mil` — always approved, always admin, cannot be locked out
- All data syncs in real-time across all active sessions
- Audit log retains up to 500 entries in Firebase
- OCIE data stored separately under `ocie_data/` in Firebase
