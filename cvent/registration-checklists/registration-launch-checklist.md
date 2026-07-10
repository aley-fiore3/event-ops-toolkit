# Cvent Registration Launch Checklist

Use this checklist before opening registration for any Cvent event. Work through it top to bottom — order matters because later items depend on earlier ones.

## Event Setup (Do First)

- [ ] Event name, dates, location, and timezone are correct
- [ ] Event website is built and previewed on mobile
- [ ] Custom domain or vanity URL is configured (if applicable)
- [ ] Event status is set to **Testing** (not Active — don't go live yet)

## Registration Types

- [ ] All registration types created and named correctly
  - *Rename reg types at Admin > Data Lists > Contact Types if needed*
- [ ] Admission items assigned to correct reg types
- [ ] Pricing set correctly per reg type (including $0 for free types)
- [ ] Registration caps set (if limiting by type)
- [ ] Waitlist enabled for types that need it
  - *Waitlists work for Registration AND Sessions*

## Sessions

- [ ] All sessions created with correct dates, times, and rooms
- [ ] Session visibility restricted by reg type (if needed)
- [ ] Session capacity limits set
- [ ] Session waitlists enabled where appropriate
- [ ] Session Groups configured (limits selection to one per group)
- [ ] Session Bundles configured (one-click enrollment for session packages)
- [ ] Advanced Rules set correctly:
  - Optional Session rules
  - Quantity Item rules
  - Hotel Request rules

## Payment & Discounts

- [ ] Payment gateway connected and tested
- [ ] Currency is correct — **CRITICAL: Currency locks after launch and cannot be changed**
- [ ] Discount/promo codes created and tested
- [ ] BOGO configured correctly (if applicable): Threshold 0, Interval 2
- [ ] Service fees configured (if applicable)
- [ ] Payment Credits set to auto-award to Registrants at event end (if applicable)
- [ ] Refund/cancellation policy entered

## Hotel Blocks

- [ ] Hotel blocks created with correct room types and rates
- [ ] Block dates match event dates (plus shoulder nights)
- [ ] Cut-off date set
- [ ] Hotels sync between Admin and events — verify sync is working

## Emails & Communications

- [ ] Registration confirmation email created and assigned
- [ ] Waitlist notification email created and assigned
- [ ] Cancellation confirmation email created and assigned
- [ ] Reminder emails scheduled (2 weeks, 48 hours)
- [ ] All emails tested — check merge fields, formatting, links
- [ ] Sender name and reply-to address are correct

## Website & Branding

- [ ] Header/footer content is complete
- [ ] Language Selector configured in Header/Footer (if multilingual)
- [ ] Registration form previewed and tested end-to-end
- [ ] All custom questions display correctly
- [ ] Terms and conditions / waivers display correctly

## Speaker Setup

- [ ] Speakers added via Admin Speaker Library
- [ ] **Remember: Speakers sync FROM Admin but NOT to individual events** — verify they appear on the event site
- [ ] Speaker bios and headshots display correctly

## Testing (Do Last, Before Launch)

- [ ] Complete a test registration for EVERY registration type
  - *100 test registrations allowed per event*
  - *Test Profile lives in User Profile*
- [ ] Walk through each reg type path: select sessions, add hotel, apply discount, complete payment
- [ ] Verify confirmation emails received for each test
- [ ] Test on mobile device
- [ ] Test waitlist flow (fill a session, try to register, verify waitlist email)
- [ ] Check default timezone in User Profile > Preferences
- [ ] Review at Admin > Reporting > Recent Imports/Exports for any data issues

## Go Live

- [ ] Switch event status from Testing to **Active**
- [ ] Delete test registrations
- [ ] Send invitation email or share registration link
- [ ] Monitor first 10 real registrations for any issues
- [ ] Celebrate (briefly — there's always something)

---

## What Can Go Wrong

| Issue | How to Prevent |
|-------|---------------|
| Currency is wrong after launch | Triple-check before going live — it's permanently locked |
| Wrong sessions visible to a reg type | Test every reg type path, not just one |
| Discount code doesn't work | Test the exact code (case-sensitive) with a real test registration |
| Speakers missing from event site | Speakers only sync FROM Admin — manually verify they appear |
| Hotel block not showing | Verify hotel sync is enabled and dates overlap with event |
| Waitlist emails not sending | Confirm the waitlist email template is assigned, not just created |
