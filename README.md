Deterministic GPG keychain generator (javascript)
=============================

GPG-HD is a deterministic full GPG keychain (CA key + 3 subkeys) generator using as input a BIP-39 phrase.  For those who don't want their digital identity to be tied to physical media in case of theft/loss/or electronic failure.



Requirements
------------

* nodejs
* yarn (or npm)


Installation
------------

```
yarn
```

How to use
----------

`./gpg-hd`    (to echo usage)

`./gpg-hd -k ed25519 -u "foo bar <foo@bar.com" -d "2023-04-20" -s "milk sad wage cup reward umbrella raven visa give list decorate bulb gold raise twenty fly manual stand float super gentle climb fold park"`

Or to import straight into your PGP keychain:

`./gpg-hd -k ed25519 -u "foo bar <foo@bar.com" -d "2023-04-20" -s "milk sad wage cup reward umbrella raven visa give list decorate bulb gold raise twenty fly manual stand float super gentle climb fold park" | gpg --import`


By default GPG-HD uses 1970-01-1 (Unix epoch of 1 second) to signal a deterministic keychain.  Optionally one can over-ride this with `-d "2023-08-22T01:43:41.612Z"`
 while key expirations are defaulted to never expire.


Use Cases
----------

On an airgap machine, use a safe brainwallet such as [PortalWallet](https://github.com/Logicwax/PortalWallet) to generate a BIP-39 phrase:

`SEED = portalwallet("satoshi")`

 `SEED="fetch december jazz hood pact owner cloth apart impact then person actual"`

 `./gpg-hd -k ed25519 -u "foo bar <foo@bar.com" -s "$SEED"`
