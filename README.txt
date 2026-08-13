TD6 Tracking Field Test v0.17

Base: v0.16.
Backend remains Rally Tracking Code.gs v0.22.

PURPOSE
Test the selected hybrid transport:
- STC Recorder v2.79 patient request strategy
- v0.16 current-track queue strategy
- v0.22 fast Code.gs receipt
- Event End bulk safety net

LIVE REQUEST
- Each track is stored locally before sending.
- One live submit request is allowed to complete naturally for up to 30 seconds.
- There is NO separate trackingConfirm request.
- Positive acknowledgement clears only that exact local track.
- A request that exceeds 30 seconds remains retained.

QUEUE MANAGEMENT
- New/current track keeps priority.
- Older retained tracks do not change identity; the original packet is reused unchanged.
- Successful newer acknowledgement wakes one older retained track immediately.
- Otherwise retained retry timing is conservative:
  recent successful response median x2, bounded to 15–30 seconds.
- One worker / one active request at a time remains.

UNCHANGED
- true Reset to Track 1
- server timing diagnostics
- Event End bulk transfer
- Share Log File
- Code.gs v0.22

FIRST TEST
1. Confirm backend ping is v0.22.
2. Reset Test.
3. Run normal online tracking for 8–10 tracks.
4. Do not simulate offline on the first run.
5. Share the .txt log and the first two Tracking-sheet timestamp columns.
6. We are looking for the natural response distribution: usually a few seconds, with any slower
   5–30 second replies now allowed to finish instead of being aborted at 5 seconds.
