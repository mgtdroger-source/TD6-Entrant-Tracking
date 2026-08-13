TD6 Tracking Field Test v0.18

Base: v0.17 slow benchmark.
Backend remains Rally Tracking Code.gs v0.22.

NEW: LIVE TRANSPORT SWITCH
Google connection now offers:
1. GET benchmark · v0.17
2. POST receipt · test

GET BENCHMARK
- Exactly the v0.17 live transport.
- Same track packet is encoded into the GET URL.
- Phone waits up to 30 seconds for the full Apps Script response.

POST RECEIPT
- Same logical track packet and same Report Key.
- Track payload is sent in a hidden-form POST body to mode=trackingSubmit.
- Browser does not need to read the POST response.
- After the POST handoff, the phone makes a tiny trackingConfirm JSONP lookup asking only whether
  the exact Report Key was received.
- On a later retry, POST mode PRE-CHECKS the Report Key before resending, avoiding a duplicate
  where the earlier POST arrived but its confirmation was slow/lost.
- Confirmation timeout is 8 seconds.
- All queue/current-priority/adaptive retry behaviour remains v0.17.
- Event End bulk path is unchanged.

TEST
A. Reset Test.
B. Select GET benchmark and run a short normal test if a fresh benchmark is wanted.
C. Reset Test.
D. Select POST receipt and run the same normal online test.
E. Share the log and the first two Tracking-sheet timestamp columns.

POST log markers:
POST SEND START
POST HANDED TO GOOGLE
POST RECEIPT CONFIRMED / NOT FOUND / NO ACK
POST ACKNOWLEDGED
POST PRE-CHECK START / POST ALREADY RECEIVED on retry

Important:
This version changes only the live transport selection. It does not change Code.gs v0.22,
the tracking packet identity, queue ordering, current-track priority, or Event End bulk transfer.
