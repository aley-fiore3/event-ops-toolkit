# Award Force Data Export Playbook

What to export, when to export it, and how to make the data usable in other systems.

## Export Before the Season Closes

Some data is harder (or impossible) to access after a season closes. Export everything you might need while the season is active.

## What to Export

| Data | When to Export | Format | What You Get |
|------|---------------|--------|-------------|
| All Entries | After submissions close | CSV | Entrant names, emails, organizations, categories, submission status, timestamps |
| User List | Before season close | CSV | All users (entrants, judges, admins) with contact info and roles |
| Score Reports | After each judging round | CSV | Scores by criterion, judge, entry — the raw data |
| Score Summary | After final round | CSV | Aggregated scores, rankings, weighted totals |
| Comments/Feedback | After judging | CSV | Judge comments per entry (if enabled) |
| Communication Log | Anytime | CSV | Emails sent, delivery status |

## How to Export

1. Log into Award Force as Admin
2. Navigate to the data section you need
3. Look for the **Export** or **Download** button (usually top-right)
4. Select CSV format (most portable)
5. Save with a descriptive filename: `NECC2026_entries_final_2026-03-01.csv`

## Cleaning the Export

Award Force exports are generally clean but watch for:

### Name Fields
Award Force often stores names as a single field. You'll likely need to split:
- `"Maria Santos"` → First: `Maria`, Last: `Santos`
- Watch for: prefixes (Dr., Prof.), suffixes (Jr., III), compound names

**Python split:**
```python
import pandas as pd
df = pd.read_csv('export.csv')
df[['First Name', 'Last Name']] = df['Name'].str.split(' ', n=1, expand=True)
```

### Organization Normalization
The same org will appear multiple ways:
- "Texas A&M", "TAMU", "Texas A & M University"

**Fix:** Create a mapping dictionary and apply it:
```python
org_map = {
    'TAMU': 'Texas A&M University',
    'Texas A & M': 'Texas A&M University',
    'Texas A&M': 'Texas A&M University',
}
df['Organization'] = df['Organization'].replace(org_map)
```

### Email Cleanup
- Strip whitespace: `df['Email'] = df['Email'].str.strip().str.lower()`
- Flag duplicates: `df[df.duplicated(subset='Email', keep=False)]`
- Flag invalid: look for missing `@`, typos like `.cmo`, `.con`

## Porting to Other Platforms

### Award Force → Cvent

| Award Force Field | Cvent Field | Notes |
|-------------------|-------------|-------|
| Name | First Name + Last Name | Split required |
| Email | Email Address | Direct map |
| Organization | Company | Normalize first |
| Category | Registration Type | Map categories to reg types |
| Role (Judge/Entrant) | Registration Type | Use to determine correct reg type |
| Submission Status | Custom Field | No native equivalent — use custom field |

### Award Force → Google Sheets / Excel
Direct CSV import works. Add columns for:
- Status tracking (contacted, registered, confirmed)
- Notes (anything the export doesn't capture)
- Source (mark as "Award Force Export" for your records)

### Award Force → Email Platform (Constant Contact, Mailchimp, etc.)
Map: Email, First Name, Last Name, Organization. Segment by role (judge vs. entrant) using tags or lists.

## Post-Event Archive

After the event, create a master archive:
1. Export everything listed above
2. Store in a dedicated folder: `Event_Name_Year/data-exports/`
3. Include a README noting what each file contains and the export date
4. This becomes your starting point for next year's setup

## What Can Go Wrong

| Issue | Prevention |
|-------|-----------|
| Season closes before you export | Set a calendar reminder for 48 hours before close |
| Duplicate contacts across entries | Deduplicate on email before importing elsewhere |
| Judge data missing from export | Judges and entrants may be in separate export paths — check both |
| Scores don't include criteria breakdown | Make sure you export the detailed score report, not just the summary |
