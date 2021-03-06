# Cryptography

Child topics:

- ECDSA

## Implementations

- GPG <http://en.wikipedia.org/wiki/GNU_Privacy_Guard>. Installed by default on Ubuntu 14.04.
- PGP <http://en.wikipedia.org/wiki/Pretty_Good_Privacy>.
- OpenSSL <http://en.wikipedia.org/wiki/OpenSSL>

### OpenPGP

<http://en.wikipedia.org/wiki/Pretty_Good_Privacy#OpenPGP>

It is a WIP standard extracted from GPG and PGP. Both implement it to a large extent, and should be interoperable. Vs. <http://askubuntu.com/questions/186805/difference-between-pgp-and-gpg>

### OpenSSL Vs. GPG and PGP

<http://crypto.stackexchange.com/questions/15037/difference-rsa-keypair-creation-openssl-and-openpgp>

<http://security.stackexchange.com/questions/39765/public-keys-on-openssl-vs-pgp>

OpenSSL implements the entire bidirectional communication protocol, which requires some public key algorithms also present in PGP and GPG, but much more on top of that. TODO Are implementations are disjoint?

GPG and PGP on the other hand are suitable for unidirectional encryption, e.g. local storage and email.

## Symmetric cryptography

## Secret key cryptography

You use a password to lock the data.

### AES

<http://en.wikipedia.org/wiki/Advanced_Encryption_Standard>.

Used by the British and American governments. Yanks can encrypt top-secret information with it. So it is likely a good choice.

Supersedes the DES family.

It is a type of <http://en.wikipedia.org/wiki/Block_cipher>.

Implemented by OpenSSL.

Intel has extended x86 to add instructions to accelerate AES encryption since 2008.

## Asymmetric cryptography

## Public key cryptography

Public key cryptography is a way to do cryptography so that it is not necessary to exchange secret data before the actual data is transferred: all transactions are public.

PKC provides two main functions:

-   encryption

    Someone who wants to send you a message encrypts it using your public key, so that only you, holder of the private key, can decrypt it.

-   signature.

    Given an input message, you can generate a string that only you, holder of the private key, would be able to generate, in function of that message.

    Furthermore, anyone can verify that only you could have generated that string, by looking only at your public hey.

Some algorithms may only provide some of those functions.

Algorithms are based on mathematical operations which are fast to calculate, but too slow to inverse.

Main algorithms are:

-   Diffie-Hellman.

    Discrete Exponent mod n / Discrete logarithm mod n problem.

    Only provides secrecy.

-   RSA.

    Multiplication / Factorization problem.

    Both secrecy and signature.

-   ECDSA.

### Man in the middle

Public key cryptography solves the major problem of key distribution.

But it leaves one problem open: identity trust.

An evil user might be able to make you believe that your friend's public key is his public key, and vice versa: this evil person is the man in the middle: he can make you believe that you are talking with your friend over a secure channel, when in fact you're not.

Broadly speaking there are two solutions:

- centralized: PKI
- decentralized: web of trust

The trade offs are the same of every centralize vs not dilemma.

Advantages of centralized:

- simpler to implement, and very specialized individuals can focus on implementing it very well
- the authorities have great concentration of power, and are a single weak link for the entire system

#### PKI

Public Key Infrastructures.

Some centralized authorities exist whom everyone trusts.

#### Net of trust

Model popularized by open source left wing projects like PGP.

Everyone makes a list of keys they trust.
