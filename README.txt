TD6 Tracking Field Test v0.19

Base: v0.18.
Backend remains Rally Tracking Code.gs v0.22.

PURPOSE
Measure the simplest possible live exchange before designing retry:
  Track XX SENT
  Track XX RECEIVED
or
  Track XX NO RESPONSE

LIVE TRANSPORT
- POST only.
- Same tracking packet and Report Key as previous tests.
- Direct fetch POST to the Apps Script endpoint.
- The phone reads only the response to that POST.
- There is NO secondary GET / JSONP trackingConfirm.
- Response observation window: 30 seconds.

DIAGNOSTIC RULE
- Each newly created track is attempted once.
- A matching POST response removes that exact track from the phone queue.
- A missing/invalid response leaves the track retained.
- There is NO automatic retry of failed tracks in v0.19.
- New 30-second tracks continue to be attempted normally.
- Event End bulk code is left in place but is not part of this live-response test.

LOG
Successful example:
  TRACK 27 SENT
  TRACK 27 RECEIVED · 2140 ms · Code.gs 530 ms

Failure example:
  TRACK 27 SENT
  TRACK 27 NO RESPONSE · 30000 ms · Timed out after 30000 ms

TEST
1. Confirm Code.gs is still v0.22.
2. Reset Test.
3. Run normally online.
4. Aim for at least 20-30 tracks if behaviour permits.
5. Do not use Simulate Offline for the first test.
6. Share the log.

We are measuring:
- how many direct POST exchanges return correctly;
- normal POST response time;
- slow outliers;
- genuine no-response cases.

Only after this measurement should a retry interval/mechanism be chosen.
