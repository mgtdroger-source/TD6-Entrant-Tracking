TD6 Tracking Field Test v0.13

Changes from v0.12
- Backlog recovery now uses the STC Recorder-style philosophy:
  one short confirmation attempt, then retain-and-move-on if Google is slow.
- Retained reports rotate through the queue instead of allowing one slow item
  to monopolise recovery.
- Current/new track priority remains in place.
- Diagnostic status wording is clearer:
  Google: sending current track XX
  Google: recovering retained track XX
  Google: track XX retained for retry
- Share Log now shares/saves an actual .txt file rather than sending the whole
  log as message text.
- Reset Test also resets the recovery cursor.
- No change to Event End bulk-transfer design.

Expected behaviour
- Normal running: Tracks 0, briefly 1, then back to 0.
- After a communication break: newest/current report gets priority first.
- Older retained reports are retried in turn without blocking the lane.
- Event End: all remaining retained records are bulk packaged and cleared only
  after confirmed package receipt.
