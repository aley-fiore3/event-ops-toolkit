# Cvent Common Issues & Troubleshooting

Quick reference for the problems that come up most often in Cvent event management. Each entry includes the symptom, likely cause, and exact fix.

---

## Registration Issues

### All sessions visible to all reg types
**Cause:** Session visibility not restricted by registration type.
**Fix:** Event > Sessions > [Session Name] > Visibility > Set to specific reg types.

### Discount code not working
**Cause:** Code is case-sensitive, expired, or not assigned to the right reg type/admission item.
**Fix:** Event > Registration > Discount Codes > Verify: exact code text, valid date range, applicable reg types, and usage limit not reached.

### Registration cap hit but people can still register
**Cause:** Waitlist is enabled, so registrants are going to waitlist instead of being blocked.
**Fix:** If you want a hard cap, disable waitlist on that reg type. If waitlist is intentional, verify the waitlist notification email is assigned.

### Can't change currency after launch
**This is a known Cvent limitation.** Currency is permanently locked once the event goes active. The only fix is to create a new event with the correct currency and migrate registrations.

---

## Session Issues

### Attendee can select multiple sessions in a group
**Cause:** Session Group not configured, or sessions aren't assigned to the group.
**Fix:** Event > Sessions > Session Groups > Create group > Add sessions > Set "limit one selection."

### Session bundles not enrolling in all sessions
**Cause:** Individual sessions within the bundle are at capacity or have conflicting restrictions.
**Fix:** Check capacity on each session in the bundle. Session Bundles enroll in all included sessions with one click — if any session is full, the bundle fails.

---

## Email Issues

### Confirmation email not sending
**Cause:** Email template created but not assigned to the registration trigger.
**Fix:** Event > Emails > [Template] > Triggers > Assign to "Registration Confirmation."

### Merge fields showing as blank
**Cause:** The merge field references data the registrant didn't provide, or the field name doesn't match.
**Fix:** Test with a full test registration. Check that custom question field names match the merge field exactly.

---

## Speaker Issues

### Speakers not appearing on event website
**Cause:** Speakers sync FROM Admin Speaker Library but NOT to individual events automatically.
**Fix:** Event > Speakers > Manually add or sync from Admin library. Verify speaker profiles are complete (name, bio, headshot).

---

## Hotel Issues

### Hotel block not visible to registrants
**Cause:** Hotel sync not enabled, or block dates don't overlap with event dates.
**Fix:** Admin > Hotels > Verify sync is enabled. Check that hotel block dates include the event dates plus shoulder nights. Hotels DO sync between Admin and events.

---

## Admin & Data Issues

### Can't find recent import
**Fix:** Admin > Reporting > Recent Imports/Exports.

### Need to rename registration types
**Fix:** Admin > Data Lists > Contact Types > Edit names. This changes the display name globally.

### Timezone is wrong on event
**Fix:** User Profile > Preferences > Default timezone. Also check event-level timezone settings.

### Need to find test registration profile
**Fix:** User Profile > Test Profile. Up to 100 test registrations allowed per event.

---

## Advanced Rules Quick Reference

| Rule Type | What It Controls |
|-----------|-----------------|
| Optional Session | Sessions that appear conditionally based on reg type or other criteria |
| Quantity Item | Items where registrants select a quantity (meal tickets, parking passes) |
| Hotel Request | Hotel booking rules tied to registration |

---

## When to Call Cvent Support

Call support (don't just email) when:
- Registration data appears corrupted or missing
- Payment processing errors on live registrations
- Sync issues between Admin and event that don't resolve with the fixes above
- You need a feature that might require a backend configuration change

Before calling, document: what you expected, what happened, steps to reproduce, and screenshots.
