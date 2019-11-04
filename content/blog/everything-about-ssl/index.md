---
title: Things I Wish Could Remember About SSL
date: "2019-11-04T19:46:03.284Z"
description: "Some stuff about SSL / OpenSSL"
---

SSL has always been one of those things that I've understood the fundamentals of - Alice and Bob have explained
Diffie-Hellman to me more times than I can keep track of - but I've always found troubleshooting SSL problems to
be a pain. Thoretical knowledge is certainly a good-to-have and understanding how key-excahnge and chains-of-trust
work ti definitely useful, but when you're sitting at a terminal and there's a whole bunch of red lights flashing
on your favourite dashboard because some service's SSL certificate has expired dont go crying to Alice and Bob. They
have forsaken you. You're dommed, all becuase you've never learned how to troubleshoot SSL problems in a practical
fashion.

## Here's some stuff about SSL

### Check commands

* Check a certificate signing request (CSR)

```openssl req -text -noout -verify -in CSR.csr```

* Check a private key

```openssl rsa -in privateKey.key -check```

* Check a certificate

```openssl x509 -in certificate.crt -text -noout```

* Check that a private key / certificate pair match ( Modulus must match )

```openssl x509 -noout -modulus -in CERTIFICATE.crt | openssl md5```

```openssl rsa -noout -modulus -in PRIVATEKEY.key | openssl md5```

* Check SSL Connection

```openssl s_client -connect www.paypal.com:443```
