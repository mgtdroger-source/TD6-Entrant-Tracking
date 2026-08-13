TD6 Tracking Field Test v0.21

PURPOSE
Use ONLY the proven bulk-transfer receipt mechanism while keeping the normal live
Tracking write path.

REQUIRES
Rally Tracking Code.gs v0.23.

LIVE FLOW
1. Track is created and retained locally.
2. Hidden-form POST sends the normal live report:
      mode=liveSubmit
3. Code.gs writes that report directly to the Tracking sheet.
4. After the successful append, Code.gs saves a receipt marker using the SAME
   Script Properties receipt mechanism used by bulk packages.
5. Phone waits 1.2 s, then uses the SAME proven packageConfirm JSONP handshake,
   with packageId set to the report's exact Report Key.
6. Exact receipt confirmed:
      TRACK XX RECEIVED
   and the phone clears that track.
7. No receipt:
      track remains retained.
8. No automatic live-track resend in this diagnostic version.

IMPORTANT
- Live data does NOT go through packageSubmit.
- Live data does NOT go through Drive package storage, Replay or the one-minute worker.
- The only piece borrowed from bulk transfer is the receipt marker + packageConfirm handshake.
- Event End bulk remains unchanged.

FIRST TEST
Run normally online. Check that each track appears immediately in Tracking while
the phone log shows:
  TRACK XX SENT · normal live write
  TRACK XX POST HANDED TO GOOGLE
  TRACK XX RECEIPT RETURNED
  TRACK XX RECEIVED

Do not test offline/retry yet.
