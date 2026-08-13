TD6 Tracking Field Test v0.15

Base: v0.14 CLEAN.
Backend target: Rally Tracking Code.gs v0.22.

Changes
- True Reset now clears:
  - retained tracking queue
  - active bulk package
  - recorded counter
  - session counters
  - activity log
  - track sequence counter
- After Reset, the next generated report is Track 1.
- Google endpoint and Sender ID remain stored.

Server timing diagnostics
When Code.gs v0.22 returns a successful response, the Activity log now records:
- phone elapsed time
- total Code.gs time
- append time
- sheet-open time
- validation time
- receipt-cache time

For exact confirmation responses it records:
- phone elapsed time
- total Code.gs time
- cache time
- sheet-open time
- lookup time
- confirmation source (recent-receipt-cache or sheet-fallback)

Purpose
This version is a measurement update only. It does not change the proven v0.14 queue worker,
retry behaviour, current-track priority or Event End bulk transfer.

First test
1. Confirm Code.gs ping reports v0.22.
2. Reset Test.
3. Confirm display says next Track 1.
4. Run normal online tracking.
5. Share the .txt log.
6. Compare phone elapsed time with Code.gs totalCodeMs.
