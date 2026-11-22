# Coiffure Mina · booking page

Live: https://asofficialagency-source.github.io/coiffure-mina/ (GitHub Pages, `index.html` + `cmx.html`).
All settings are at the top of the `<script>` in `index.html` (block "CONFIG (edit here)").

## Settings

| Setting | Empty | Filled |
|---|---|---|
| `CALCOM_URL` | fixed slots from `HOURS` (no blocking of taken times) | Mina's Cal.com calendar in step 3, taken times are blocked |
| `DEPOSIT_LINK` | client reads "payment link via WhatsApp" | "Pay €20 deposit" button after booking |
| `HOURS` / `BLOCKED_DATES` | opening hours per weekday (from 10:00) / days off | |

Bookings go to Web3Forms with `form_type=booking` and subject
`Nieuwe boeking - Coiffure Mina - {name} - {date} {time}` (testimonials use the same key, so filter on the subject).
If the client fills in her birthday, the mail has a link "Zet verjaardag in je agenda" (yearly Google Calendar event).

## Cal.com (stops double bookings): what Mina does

1. Log in on https://cal.com (or create a free account) and connect her Google or Apple calendar
   (Settings > Calendars), so busy times in her own agenda are blocked too.
2. Availability: Tuesday to Saturday, from 10:00. Add days off there.
3. Create one event type, e.g. "Appointment", length 5 hours (the longest service, so nothing overlaps),
   minimum notice 1 day, limit 2 bookings per day if she wants.
4. Copy the public link of that event type, e.g. `https://cal.com/coiffuremina/appointment`.
5. Turn on reminders: Workflows > new workflow > "Before event starts", 24 hours, e-mail (and SMS if she wants) to the attendee.
6. Send the link; we paste it in `CALCOM_URL` and push. Test once with a fake booking and cancel it in Cal.com.

How it works for the client: step 3 shows the Cal.com calendar, she confirms her time there (Cal.com blocks it),
then continues to her details and the deposit in our form. Mina gets the Cal.com confirmation plus the Web3Forms mail.

## Where clients come from

The booking mail has "Found me via" (the client's answer) and "Link source". Use a tagged link per channel,
e.g. `.../coiffure-mina/?src=ig` in the Instagram bio and `?src=tiktok` on TikTok; without a tag the referrer site is used.
