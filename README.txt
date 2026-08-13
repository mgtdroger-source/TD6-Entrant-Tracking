TD6 Tracking Field Test v0.23 — SIMPLE RESET

Requires Rally Tracking Code.gs v0.25.

Purpose:
Prove only the basic live exchange and observe retained-track build-up/clearance.

LIVE TRACK:
1. Store locally.
2. TRACK XX SENT.
3. hidden-form POST mode=liveSubmit.
4. Google writes directly to Tracking.
5. Google creates the normal bulk-style package receipt using the supplied liveReceiptId.
6. Phone waits 1.2 s then calls the EXISTING packageConfirm once.
7. Receipt found -> TRACK XX RECEIVED -> clear locally.
8. No receipt -> retain locally.

RETAINED TRACKS:
- No automatic resend of the Tracking row.
- Every 15 s the phone re-checks ONE oldest retained receipt.
- If the receipt later appears, that track clears.
- This lets the log show natural backlog and clearance without duplicate live writes.

EVENT END:
- Bulk transfer is OFF.
- End Event only stops new track generation.
- Retained tracks remain visible locally for diagnosis.

No liveConfirm.
No Tracking-sheet fallback.
No adaptive retry.
No packageSubmit for live data.
No Replay route for live data.
