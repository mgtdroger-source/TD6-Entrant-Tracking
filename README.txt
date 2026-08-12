TD6 Tracking Field Test v0.11

PURPOSE
Prove the intended STC Recorder tracking behaviour before changing the Recorder.

USER-FACING TEST DISPLAY
- While the event is running: Tracks N
- Normally N should sit at 0, briefly become 1, then return to 0.
- During a communication break N can rise as tracks are retained.
- At Event End: Transferring...
- After confirmed bulk receipt: Transfer complete

TEST DETAILS
The separate Test details card remains visible for development:
- GPS accuracy
- total recorded
- retained count
- live confirmations
- bulk confirmations
- failures
- Google / simulated-offline state

LOCKED TRANSPORT RULE
- EVENT RUNNING: live submit plus ordinary one-by-one retained recovery only.
- NO automatic bulk transfer during the event.
- EVENT END: stop creating tracks and bulk-send everything still retained.
- Local retained records are removed only after Google confirmation.

STATIC TEST
1. Online: Start Tracking. Tracks should normally return to 0 after confirmations.
2. Simulate Offline: Tracks should rise every ~30 sec.
3. Restore Google: retained count should work back toward 0 one-by-one.
4. Simulate Offline again and build a queue.
5. End Event while tracks remain.
6. Restore Google if needed. Display should show Transferring... then Transfer complete after package confirmation.
