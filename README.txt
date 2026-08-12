TD6 Tracking Field Test v0.14 CLEAN

This is a clean rebuild, not a patch of v0.13.

LIVE DELIVERY FOUNDATION
Taken from the proven STC Recorder v2.84 tracking transport:
- one queue worker
- one request at a time
- 5 s submit timeout
- one exact-key confirm
- uncertain report attempted once per pass
- failed/uncertain reports retained for a later pass
- reports added during an active pass are included
- 5 s later retry pass

TEST-ONLY ADDITIONS
- newest/current tracking report can take priority over older retained history
- detailed activity log
- Share Log File creates/shares a .txt file
- Simulate Offline
- detailed counters

EVENT END BOLT-ON
- no bulk transfer while event is running
- End Event stops new 30 s reports
- waits for the live worker to hand over
- packages every track still retained
- clears exact retained records only after package receipt confirmation
- if offline, retains package and resumes when communication returns

RESET
Reset Test clears:
- ALL retained tracking records
- active bulk package
- recorded counter
- session counters
- activity log
The Google endpoint and sender are retained.
The sequence counter is deliberately retained to prevent accidental duplicate identities during repeated same-day tests.

STATIC TEST
1. Reset Test.
2. Ping Google.
3. Start Tracking online for several tracks.
4. Confirm Tracks normally returns to 0.
5. Simulate Offline and accumulate 4-5 tracks.
6. Restore Google and observe current report priority plus STC-style queue recovery.
7. Share the .txt activity log.
8. Repeat offline accumulation, press End Event, then restore communication if needed.
9. Confirm Transferring... becomes Transfer complete only after package confirmation.
