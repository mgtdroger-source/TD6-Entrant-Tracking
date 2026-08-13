TD6 Tracking Field Test v0.24

Requires Rally Tracking Code.gs v0.25.

This is a narrow correction to app v0.23 only.

Fix:
- restores the missing scheduleFlush() dispatcher so a newly queued track
  actually proceeds into the existing simple send/receipt worker.

Everything else remains as v0.23:
- normal live Tracking write;
- existing bulk-style packageConfirm receipt mechanism;
- no live row resend;
- retained receipt re-check every 15 seconds;
- Event End bulk OFF;
- no liveConfirm;
- no Tracking-sheet fallback;
- no adaptive retry.

Code.gs v0.25 is unchanged.
