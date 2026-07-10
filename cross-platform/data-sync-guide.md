# Cross-Platform Data Sync Guide

How to keep data consistent when your event lives in Award Force, Cvent, spreadsheets, and email platforms simultaneously.

## The Problem

You have the same people in multiple systems:
- **Award Force** — entries, judges, scores
- **Cvent** — registration, hotel blocks, sessions
- **Spreadsheets** — master tracking, budget
- **Email platform** — communications, campaigns

Nobody's data matches. A judge is registered in Cvent but not added to Award Force. An entrant changed their email between submission and registration. Three people registered as "Guest" who should be "Student Competitor."

This guide prevents that.

## Step 1: Establish Source of Truth

Decide which system owns which data. Don't let the same data live in two places without a clear master.

| Data Type | Source of Truth | Syncs To |
|-----------|----------------|----------|
| Entrant/submission info | Award Force | Spreadsheet |
| Judge profiles & scores | Award Force | Spreadsheet |
| Registration & payment | Cvent | Spreadsheet |
| Hotel bookings | Cvent | Spreadsheet |
| Session assignments | Cvent | Spreadsheet |
| Communications | Email platform | — |
| Master contact list | **Spreadsheet** | All platforms |

The spreadsheet is your single pane of glass — it's the only place where a person's full picture exists.

## Step 2: Master Contact Spreadsheet Structure

| Column | Source | Notes |
|--------|--------|-------|
| Full Name | Manual | Standardized format |
| First Name | Split from full | For imports |
| Last Name | Split from full | For imports |
| Email | Most recent | Always lowercase, trimmed |
| Organization | Normalized | Use consistent naming |
| Role | Manual | Judge, Entrant, Advisor, Guest, Staff |
| Award Force Status | AF export | Submitted, Reviewed, etc. |
| Award Force User ID | AF export | For re-import |
| Cvent Reg Type | Cvent export | Student, Judge, Guest, etc. |
| Cvent Reg Status | Cvent export | Confirmed, Waitlisted, Cancelled |
| Hotel Booked | Cvent export | Yes/No + dates |
| Sessions Selected | Cvent export | List |
| Email Platform Tag | Manual | For segmented communications |
| Notes | Manual | Catch-all for edge cases |

## Step 3: Sync Workflow

Run this weekly during active periods, daily during the final 2 weeks.

### Export
1. Export entries + users from Award Force → CSV
2. Export registration report from Cvent → CSV
3. Export email list from email platform → CSV

### Match
4. Match records across exports on **email** (primary key)
5. Flag mismatches:
   - In AF but not Cvent (submitted but didn't register)
   - In Cvent but not AF (registered but not in judging system)
   - Email differs between systems (same person, different address)
   - Role mismatch (registered as Guest, should be Judge)

### Reconcile
6. Update master spreadsheet with latest from all sources
7. Push corrections back to each platform:
   - Add missing judges to Award Force
   - Fix reg types in Cvent
   - Update email lists/tags

### Verify
8. Count check: AF users = Cvent registrants = Email list (by role)
9. Spot check 5 random people across all systems

## Step 4: Matching Script

```python
import pandas as pd

# Load exports
af = pd.read_csv('award_force_export.csv')
cvent = pd.read_csv('cvent_export.csv')

# Normalize emails
af['email_clean'] = af['Email'].str.strip().str.lower()
cvent['email_clean'] = cvent['Email Address'].str.strip().str.lower()

# Find mismatches
in_af_not_cvent = af[~af['email_clean'].isin(cvent['email_clean'])]
in_cvent_not_af = cvent[~cvent['email_clean'].isin(af['email_clean'])]

print(f"In Award Force but not Cvent: {len(in_af_not_cvent)}")
print(f"In Cvent but not Award Force: {len(in_cvent_not_af)}")

# Save for review
in_af_not_cvent.to_csv('missing_from_cvent.csv', index=False)
in_cvent_not_af.to_csv('missing_from_af.csv', index=False)
```

## What Can Go Wrong

| Issue | Prevention |
|-------|-----------|
| Same person, different emails in each system | Always match on email AND name as fallback |
| AF season closes before final export | Calendar reminder: export 48 hours before close |
| Someone changes their info after you synced | Run the sync weekly, not once |
| Bulk import breaks Cvent registrations | Always import to a test event first |
| "I'll just track it in my head" | You won't. Use the spreadsheet. |
