TD6 Tracking Field Test v0.10

Purpose
- Prove the Tracking Code.gs v0.20 front end before changing STC Recorder.
- Uses real phone GPS, recording one track every 30 seconds.
- Stores every track locally before any Google transfer.
- Normal/current tracks use liveSubmit + exact trackingConfirm.
- A queue of 5+ uses packageSubmit/packageConfirm for the older backlog while leaving the newest track for the live path.
- Maximum package size 300 tracks.
- Package identity and included report keys persist across retries/reloads.
- Local rows are deleted only after exact live confirmation or package receipt confirmation.
- Simulate Offline pauses Google delivery without stopping GPS/queue accumulation.

Backend
- Use the corrected Rally Tracking Code.gs v0.20 included separately in this response.
- The correction restores the JSONP callback required by browser confirmation lookups.
- Run trackingSetup once and deploy/update the Apps Script web app before testing.

Suggested proof
1. Start online. Confirm 30-second tracks clear individually into Tracking.
2. Tap Simulate Offline and leave tracking running long enough to build at least 5 queued tracks.
3. Tap Restore Google. Older queued tracks should be packaged; the newest remains available for the live path.
4. Confirm the Drive package reaches Processed after replay, Replay is populated then ages out, and Tracking is ordered by GPS time.
5. Repeat with actual mobile-data loss as a field test.

This test app deliberately does not include STC timing/submission logic.
