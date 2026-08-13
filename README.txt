TD6 Tracking Field Test v0.26

Use with standalone diagnostic Code.gs v0.29.

NARROW FIX FROM v0.25 ONLY

Observed v0.25 fault:
A retained receipt-recheck timer could fire while the sender was busy with a
current track. scheduleFlush() then returned, the timer opportunity was lost,
and no new retained-recheck timer was guaranteed. This could strand a backlog.

v0.26 changes only retained receipt scheduling:

1. If the 15 s retained-receipt timer fires while the sender is busy,
   the timer re-arms itself instead of disappearing.

2. After every worker completion, if retained tracks still exist and there is
   no current priority track waiting, ensure a retained-receipt timer is armed.

UNCHANGED
- current/new 30-second track priority
- rotating retained receipt checks
- no retained live-row resend
- hidden-form liveSubmit
- packageConfirm receipt mechanism
- 1.2 s initial receipt delay
- 12 s max receipt lookup
- 15 s background receipt cadence
- Event End bulk OFF
