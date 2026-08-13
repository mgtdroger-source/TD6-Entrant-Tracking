TD6 Tracking Field Test v0.16

Base: v0.15. Backend remains Code.gs v0.22.

Live delivery update:
- store each track locally first
- send current track once
- no trackingConfirm call after an uncertain live submit
- no acknowledgement = sent/unconfirmed and retained
- new tracks continue with priority
- retry delay learns from recent successful phone acknowledgement times
- retry delay = recent median x2, bounded 7–20 seconds
- a successful newer acknowledgement immediately wakes one older retained track
- every resend uses the original unchanged packet
- one worker / one request at a time remains

Unchanged:
- true Reset to Track 1
- server timing diagnostics
- Event End bulk transfer
- Share Log File

Test against unchanged Code.gs v0.22.
