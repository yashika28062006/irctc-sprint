# IRCTC Problem Discovery — Part A

## Summary

* Total problems documented: 6
* Platform explored: irctc.co.in
* Devices used:

  * Desktop Chrome
  * Mobile Chrome

---

# Problem 1 — Tatkal Booking Crashes at 10:00 AM [Given]

## What is broken

The IRCTC server becomes unresponsive during Tatkal opening hours at exactly 10:00 AM. Users experience loading freezes, session drops, payment uncertainty, and booking failures.

## Affected users

Users attempting Tatkal bookings, especially commuters and travelers from Tier 2 and Tier 3 cities.

Estimated 20–40 lakh users during the Tatkal window.

## Frequency

Occurs daily during Tatkal booking opening hours.

## Current flow — step by step

1. User opens IRCTC at 9:50 AM
2. User logs into account
3. User searches for train
4. User selects Tatkal quota
5. User fills passenger details
6. User clicks Book Now at 10:00 AM
7. Loading spinner freezes
8. Session timeout or HTTP 502 occurs
9. User refreshes and loses booking

## Where exactly it breaks

The flow breaks between steps 6–8 due to sudden concurrent traffic spikes and lack of queue management.

---

# Problem 2 — Search Filters Do Not Work Reliably [Given]

## What is broken

Train filters for class, availability, and quota reset unexpectedly or show inconsistent results.

## Affected users

Users searching trains with specific class or availability preferences.

## Frequency

Occurs intermittently during normal and peak usage.

## Current flow — step by step

1. User searches trains
2. Train list appears
3. User selects Sleeper + Available filters
4. Results reload
5. Waitlisted trains still appear
6. User opens train details
7. User returns to search page
8. Filters reset automatically

## Where exactly it breaks

The issue occurs between steps 4–8 because filter state is not preserved after reload.

---

# Problem 3 — Seat Selection Resets Randomly [Given]

## What is broken

Selected seats or berth preferences reset automatically during booking flow.

## Affected users

Families, senior citizens, and users requiring lower berths.

## Frequency

Observed more frequently on mobile devices.

## Current flow — step by step

1. User selects train
2. Seat map opens
3. User selects lower berth
4. Seat highlights as selected
5. User clicks Proceed
6. Passenger page loads
7. Seat preference changes to Auto
8. Original seat becomes unavailable

## Where exactly it breaks

The issue occurs between steps 4–7 due to booking state not syncing correctly.

---

# Problem 4 — UPI Payment Has No Real-Time Status Feedback [Self-Discovered]

## How I found it

Observed during payment flow testing on mobile browser.

## What is broken

UPI payment screen shows only a loading spinner without payment confirmation progress.

## Affected users

Users paying through UPI apps like Google Pay, PhonePe, and Paytm.

## Frequency

Occurs intermittently during high traffic.

## Current flow — step by step

1. User selects train
2. Passenger details are entered
3. User selects UPI payment
4. User enters UPI ID
5. User clicks Pay
6. Loading spinner appears
7. No confirmation or failure message appears
8. User refreshes tab in confusion

## Where exactly it breaks

The issue occurs between steps 5–8 because payment callback status is not surfaced clearly.

---

# Problem 5 — Mobile Website Layout Breaks During Booking [Self-Discovered]

## How I found it

Observed on Chrome mobile browser during booking process.

## What is broken

Booking forms overflow outside the screen and buttons overlap with the keyboard.

## Affected users

Users booking through mobile browsers on smaller devices.

## Frequency

Occurs consistently on mobile devices.

## Current flow — step by step

1. User opens IRCTC mobile website
2. User searches train
3. Passenger details page opens
4. User fills form
5. Keyboard overlaps buttons
6. Some fields extend outside viewport
7. User scrolls repeatedly
8. Session times out during correction

## Where exactly it breaks

The issue occurs between steps 4–7 due to inconsistent responsive layout handling.

---

# Problem 6 — Refund Information Is Difficult to Understand [Self-Discovered]

## How I found it

Observed while checking cancellation and refund pages.

## What is broken

Refund timelines and cancellation status are fragmented across multiple pages.

## Affected users

Users cancelling waitlisted or Tatkal tickets.

## Frequency

Occurs during every cancellation flow.

## Current flow — step by step

1. User opens Booked Ticket History
2. User selects Cancel Ticket
3. Ticket cancellation succeeds
4. Refund information is unclear
5. User checks bank account repeatedly
6. User revisits support pages
7. Refund status is delayed
8. User raises support complaint

## Where exactly it breaks

The issue occurs between steps 4–7 because refund tracking lacks centralized visibility.
