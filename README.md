# 7459 MORU — S4 Dashboard

A secure, real-time logistics dashboard for tracking budget, equipment status, and purchase requests across subordinate units. Built on Firebase with role-based access control.

**Live URL:** https://7459moru.github.io/BO-Dashboard/

---

## User Roles

There are three access levels. All accounts require admin approval before access is granted.

| Role | Access |
|------|--------|
| **Admin** | Full access — edit, import, manage users, view all units |
| **Battalion Viewer** | Read-only — views all units, no editing |
| **Unit Viewer** | Read-only — views own unit data only |

---

## Getting Started

### Registering an Account

1. Go to the dashboard URL and click **Register**
2. Enter your full name, email, and password
3. Select your **unit** from the dropdown, or choose **Request Battalion Access** to request access to all units
4. Click **Create Account →**
5. Your account will show an **Awaiting Approval** screen until the admin approves it
6. Once approved, your dashboard will load automatically — no refresh needed

### Forgot Password

Click **Forgot password?** on the Sign In screen, enter your email, and a reset link will be sent to you.

---

## Admin

### Overview
- Full visibility into all units' LIK and SIK budget data
- Charts, summary tables, De-Obligation Report, Active PR Tracker, and 3-Month Forecast
- Unit filter pills to show/hide specific units

### User Management (`Users` tab)
- View all registered users with their unit, access level, and role
- **Approve** or **Deny** new account registrations
- **Approve Battalion Access** or **Keep Unit Only** for battalion upgrade requests
- Promote/demote users between **Admin** and **View Only**
- Remove users from the dashboard
- Transfer the Super Admin role to another admin
- Red badge on the Users nav shows count of pending approvals

### Audit Log (`Audit Log` tab)
- Full history of all actions: sign-ins, PR adds/edits/deletes, imports, note activity, user approvals
- Search by user, action, or details
- **Delete individual entries** — Sign In and Note Deleted entries delete instantly; all others prompt for confirmation
- **Clear Log** button to wipe the entire log
- Orange badge on Audit Log nav when a viewer has added a note (clears on visit)
- **→ View in Maintenance** button on viewer note entries — navigates directly to that equipment record

### Notifications (`Notifications` tab)
- Shows all notes added by other users to equipment across all units
- Orange badge on nav for unread notifications (clears on visit)
- **→ View** button navigates to the equipment record in Maintenance

### PR Management
- Add, edit, and delete Purchase Requests from Unit Detail or the Add PR button
- Track status: Open, Pending, Closed
- Categories: LIK, SIK, Supplies
- De-Obligation Report shows closed PRs with leftover funds
- Active PR Tracker shows open/pending PRs with doc status badge:
  - 📄 **Docs Received** — PR number is not a full 10-digit number
  - ✅ **Submitted** — PR number is a full 10-digit number

### Maintenance
- **Equipment Status** — full unit filter, all tech/op status filters, Export CSV, Import
- **Schedule / Deadlines** — full unit filter, status filter, Export CSV, Import
- **Notes** — add stacked notes to any equipment record, delete any note from any user
- Hover over any note cell to see the full note in a tooltip
- Orange badge on Notifications nav when a viewer adds a note

### Data Import
- Import equipment data via CSV on Equipment Status and Schedule/Deadlines tabs
- Import budget data via Import Data in the sidebar

---

## Battalion Viewer

### Overview
- Full view of all units' LIK and SIK data — charts, summary tables, and all widgets
- Cannot edit any data

### Active PR Tracker
- View all open/pending PRs across all units
- Search by PR # or description

### De-Obligation Report
- View all closed PRs with remaining funds across all units
- Search by PR # or description, filter by date range

### 3-Month Forecast
- View all units' submission forecast

### Unit Detail
- Dropdown to switch between all units and view their budget charts and PR records

### Maintenance
- **Equipment Status** — unit filter dropdown visible, can search and filter
- **Schedule / Deadlines** — unit filter dropdown visible, can search and filter
- **Notes** — can add notes to any equipment record; can only delete own notes; cannot delete admin notes
- Import button is hidden

### Notifications (`Notifications` tab)
- Shows notes added by other users to any equipment
- Orange badge on nav for unread notifications
- **→ View** button navigates to the equipment record

---

## Unit Viewer

### Overview
- Shows **only their unit's** LIK and SIK data
- Unit filter pill bar is hidden
- De-Obligation Report shows only their unit's closed PRs

### Active PR Tracker
- Shows only their unit's open/pending PRs

### 3-Month Forecast
- Shows only their unit's column

### Unit Detail
- Unit dropdown is hidden — automatically loads their unit's data
- View-only: charts and PR records visible, no editing

### Maintenance
- **Equipment Status** — shows only their unit's equipment; unit filter dropdown hidden
- **Schedule / Deadlines** — shows only their unit's schedule; unit filter dropdown hidden
- **Notes** — can add notes to their unit's equipment; can only delete own notes; cannot delete admin notes
- Import button is hidden

### Notifications (`Notifications` tab)
- Shows notes added by other users to their unit's equipment only
- Own notes do not appear in Notifications
- Orange badge on nav for unread notifications
- **→ View** button navigates to the equipment record

---

## Features Summary

| Feature | Admin | Battalion Viewer | Unit Viewer |
|---------|-------|-----------------|-------------|
| View all units' data | ✅ | ✅ | ❌ Unit only |
| Edit / Add PRs | ✅ | ❌ | ❌ |
| Import data | ✅ | ❌ | ❌ |
| Add notes | ✅ | ✅ | ✅ |
| Delete own notes | ✅ | ✅ | ✅ |
| Delete any note | ✅ | ❌ | ❌ |
| Unit filter dropdown | ✅ | ✅ | ❌ Hidden |
| Users tab | ✅ | ❌ | ❌ |
| Audit Log tab | ✅ | ❌ | ❌ |
| Notifications tab | ✅ | ✅ | ✅ |
| Approve users | ✅ | ❌ | ❌ |
| Transfer Super Admin | ✅ | ❌ | ❌ |

---

## Technical Notes

- **Database:** Firebase Realtime Database (`pr-dashboard-6cbd7`)
- **Auth:** Firebase Email/Password Authentication
- **Hosting:** GitHub Pages
- **DB Rules:** `.read: true`, `.write: auth != null`
- **Super Admin:** `alex.a.mckee.civ@army.mil` — always approved, always admin
- All data syncs in real-time across all active sessions
- Audit log retains up to 500 entries in Firebase
