# Mazapan's signing keys

What `mazapan-keyring` puts in pacman's keyring, as archlinux-keyring
does: every package in Mazapan's repository is signed by one of these.

- `mazapan.gpg`: the public keys (`pkg/release keys KEYID pkg/keys`
  exports them).
- `mazapan-trusted`: the ones pacman trusts, `FINGERPRINT:4:` a line.
- `mazapan-revoked`: fingerprints no longer trusted, one a line.

A new key goes out in a keyring signed by a key installed systems
already trust (the old one), and the old one stays in mazapan-trusted
until every system has the new one.

The release key: `Mazapan release key <release@mazapan.dev>`,
fingerprint `B999 B535 645B 54C0 B659  ADBE 8E5A 7E23 52C9 2A1B`
(ed25519, signing only, made 2026-11-11). Only its public half is here;
the secret half and its revocation certificate are kept offline, in more
than one place, never committed.

The first key, `7C05 EB75 B1C5 4AD8 F9E1  61C7 1FCE 814E 8077 F475`
(2026-10-05, 0.1.0 to 0.5.0), was lost with the disk it was on, before a
keyring signed by it could bring in its successor: it's in
mazapan-revoked. A system installed before 0.5.1 takes the new key once,
by hand (CHANGELOG, 0.5.1); then it updates as before.

The second, `42FC 5905 D9D6 A8C1 585E  082B DF87 9369 652B 55DB`
(2026-10-23, 0.5.1), was lost the same way, its secret half nowhere it
could be brought back from: it's in mazapan-revoked too, and a system
installed before 0.5.2 takes the current key by hand once more
(CHANGELOG, 0.5.2).
