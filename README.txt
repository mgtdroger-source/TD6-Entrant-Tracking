TD6 Tracking Field Test v0.12

Changes from v0.11
- Current/new track priority after reconnection or whenever a fresh track appears during backlog recovery.
- Older retained tracks then continue one-by-one.
- Detailed Google handshake logging:
  live POST start/sent,
  confirm request/response/error,
  delivery selection,
  queue before/after,
  online/offline/recovery wake,
  bulk pre-check/POST/confirmation.
- Share Log button.
- Reset Test button.
  Clears local retained queue, active package, counters and Activity log.
  Keeps Google endpoint, Sender ID and sequence number.
- Event End status corrected:
  Transferring... changes to Transfer complete only after confirmed package receipt.
- Event End while simulated offline leaves Restore Google available.
- Transport rule unchanged:
  During event = live + one-by-one retained recovery.
  Event End = bulk transfer of all remaining retained tracks.

Clean test:
1. Stop Tracking.
2. Reset Test.
3. Start online and prove Tracks 0 -> 1 -> 0.
4. Go offline and accumulate 4-5 tracks.
5. Restore communications.
6. Newest/current track should go first, then older retained tracks drain.
7. Share Log if anything remains unclear.
8. Repeat offline, then End Event to prove bulk completion.
