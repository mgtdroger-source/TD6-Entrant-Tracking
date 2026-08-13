TD6 Tracking Field Test v0.20

PURPOSE
Test whether the proven bulk-transfer handshake behaves well when the "package"
contains exactly one live tracking record.

Backend: Rally Tracking Code.gs v0.22 unchanged.

LIVE PATH
1. Track is created and retained locally.
2. The track is wrapped in a package with recordCount=1 and tracks:[report].
3. The package is sent using the proven hidden-form POST:
      mode=packageSubmit
4. After 1.2 seconds the phone begins the proven packageConfirm JSONP receipt check.
5. When that exact packageId is confirmed:
      TRACK XX RECEIVED
   and the track is cleared locally.
6. If no receipt is confirmed, the track remains retained.

IMPORTANT
- There is NO direct fetch POST in v0.20.
- There is NO trackingConfirm lookup in v0.20 live delivery.
- There is NO resend of a failed live track during this test.
- The confirmation handshake may make repeated receipt LOOKUPS, as the original
  proven Package Transfer Test did. Those are not track resends.
- New tracking reports are still generated every 30 seconds.
- Event End bulk code remains present but is not the subject of this test.

HANDSHAKE
This intentionally mirrors the old proven bulk package mechanism:
- hidden-form POST;
- 1.2 second pause;
- packageConfirm via JSONP;
- up to 10 receipt checks, 2 seconds apart;
- 12 second timeout for an individual receipt check.

LOG EXAMPLES
  TRACK 7 SENT · one-track package
  TRACK 7 POST HANDED TO GOOGLE · 930 ms
  TRACK 7 RECEIPT RETURNED · lookup 1850 ms · check 1
  TRACK 7 RECEIVED · 3980 ms total · receipt check 1

We want to measure:
- normal one-track package handshake turnaround;
- how often the first receipt check succeeds;
- slow outliers;
- genuine failures.

Do not use Simulate Offline for the first run.
