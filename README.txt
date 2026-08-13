TD6 Tracking Field Test v0.22

Requires Rally Tracking Code.gs v0.24.

Purpose:
Keep the proven normal live Tracking write and test ONE dedicated live receipt
return only.

Flow:
1. Track created and retained locally.
2. hidden-form POST -> mode=liveSubmit.
3. Code.gs appends immediately to Tracking.
4. Code.gs records a dedicated live receipt keyed by exact Report Key.
5. Phone waits 1.2 seconds.
6. Phone makes ONE JSONP call:
      mode=liveConfirm&reportKey=<exact key>
7. Matching receipt:
      TRACK XX RECEIVED
   and that track is cleared.
8. No receipt / timeout:
      track remains retained.
9. No repeated confirmation polling.
10. No automatic resend.

This version deliberately prevents one failed receipt from blocking the sender
for a minute as v0.21 did.
