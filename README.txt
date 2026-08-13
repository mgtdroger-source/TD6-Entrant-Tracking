TD6 Tracking Field Test v0.25

Use with standalone diagnostic Code.gs v0.29.

PURPOSE
Keep the now-proven live send/receipt mechanism, but stop old retained receipts
from blocking current 30-second tracks.

CHANGES FROM v0.24
1. CURRENT TRACK PRIORITY
   A newly queued 30-second track always gets the next send turn.

2. ROTATING RECEIPT CHECKS
   Retained tracks are checked in rotation:
     Track 2 -> Track 4 -> Track 7 -> ...
   instead of repeatedly hammering the oldest retained track.

3. NO RETAINED RESEND
   Retained Tracking rows are NOT resent in this test.
   Only their receipt is rechecked.

4. NON-BLOCKING PRIORITY
   If a new/current track appears while a retained receipt check is in flight,
   that current track gets the next turn immediately after the check finishes.

5. EVENT END BULK
   Still OFF.
   End Event only stops new track generation; retained tracks remain for diagnosis.

UNCHANGED
- hidden-form liveSubmit
- bulk-style packageConfirm receipt mechanism
- 1.2 s wait before first receipt check
- 12 s max per receipt lookup
- 15 s background receipt recheck cadence
- no adaptive retry
- no live row resend
