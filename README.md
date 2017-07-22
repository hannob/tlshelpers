# tlshelpers
A collection of shell scripts that help handling X.509 certificate and TLS issues

matchcertkey
============

Script to check whether a private key belongs to a certificate.

It will check three things:

* Internal consistency of private key.
* Does SPKI SHA256 hash match?
* Can a test signature be verified?

Many existing tools and guides only check whether the public key part of the private key
matches and don't really check the private key.

fakekey
=======

Creates a private key for an existing certificate that looks like a real key
if not checked properly.

Requires the [der2ascii/ascii2der](https://github.com/google/der-ascii) tools by David Benjamin.

ocspverify
==========

Checks OCSP status of certificates with a single command.

It will automatically extract the issuer certificate and OCSP url via AIA.

examples
========

The [examples](examples/) subdirectory contains an existing certificate (from symantec) and
a corresponding fake private key.