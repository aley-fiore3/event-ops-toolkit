# Event Ops Toolkit

Plug-and-play templates, checklists, and frameworks for running events on Cvent, Award Force, and Asana — built from producing national-scale conferences and competitions.

## Who This Is For

Event managers, conference producers, and operations teams who use Cvent and/or Award Force and are tired of rebuilding everything from scratch each cycle.

## What's Inside

### Cvent
- **[Registration Launch Checklist](cvent/registration-checklists/registration-launch-checklist.md)** — Everything to verify before opening registration, including the gotchas that only bite you in production.
- **[Email Communication Templates](cvent/email-templates/)** — Invitation, confirmation, reminders, waitlist, cancellation, and post-event emails with merge field placeholders.
- **[Troubleshooting Guide](cvent/troubleshooting/common-issues.md)** — Solutions for the most common Cvent configuration problems, with exact navigation paths.

### Award Force
- **[Judging Rubric Framework](award-force/judging-rubrics/rubric-framework.md)** — Scoring criteria templates with calibration guidance to prevent score inflation.
- **[Entry Form Design Guide](award-force/entry-form-guides/form-design-guide.md)** — Field types, validation rules, and the form structure that minimizes entrant errors.
- **[Data Export Playbook](award-force/data-exports/export-playbook.md)** — What to export, when, and how to clean it for migration to other platforms.

### Cross-Platform
- **[Run Sheet Template](run-sheets/run-sheet-template.md)** — Minute-by-minute day-of timeline with staff assignments, contingencies, and buffer warnings.
- **[Planning Timeline](planning/event-planning-timeline.md)** — Reverse-engineered from event day: what to do at 120, 90, 60, 30, 14, 7, and 1 day(s) out.
- **[Platform Data Sync Guide](cross-platform/data-sync-guide.md)** — How to keep Award Force, Cvent, and your spreadsheets consistent when the same event lives in multiple systems.

## Built From Experience

These aren't theoretical templates. They come from producing multi-day, 200+ person events across platforms, including dealing with:
- Award Force judge lists that didn't match Cvent registration
- Hotel event orders with quantity mismatches
- Entrants who registered under the wrong type
- AV confirmations that came in too late
- The special joy of porting emails between platforms that don't talk to each other

Every template includes a "What Can Go Wrong" section because I've already lived through it.

## How to Use

1. Browse to the template you need
2. Copy it into your own system
3. Customize the variables (marked with `{{PLACEHOLDER}}`)
4. Run through the checklist before launch

## Related Work

Part of a set of open-source FDE tools:
- [Event Data Tools](https://github.com/aley-fiore3/event-data-tools) — Python scripts for cleaning, migrating, and reconciling event data
- [Fiore3 Automation Demos](https://github.com/aley-fiore3/fiore3-automation-demos) — Working automation demos for business operations
- [Claude Prompt Library](https://github.com/aley-fiore3/claude-prompt-library) — Prompts and techniques for deploying Claude in client workflows
- [Event Reconciliation Dashboard](https://github.com/aley-fiore3/event-reconciliation-dashboard) — No-code Streamlit dashboard for cleaning and reconciling registration data

## License

MIT — use these however you want. If they save you a 2am panic, that's all the thanks I need.
