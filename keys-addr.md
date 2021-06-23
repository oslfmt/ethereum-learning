# Cryptography
Encryption - secret writing
Digital signature - prove that you know a secret without revealing secret.
Hashes - prove the authenticity of data

Ethereum does not use encryption. This is because the data must be open and
available for everyone to view so that all transactions can be verified and
consensus can be reached. Zero knowledge proofs and homomorphic encryption
may allow encrypted calculations to be recorded on the blockchain while still
enabling consensus.

## Keys and Addresses
Ethereum uses public key cryptography (PKC) to control ownership of funds using
private keys and addresses.

In PKC systems, keys come in pairs: public and private keys. Public keys are
the identifiers of an account, while private keys are the key that gives actual
control over the account.

There is one other fundamental ingredient, the digital signature. A digital
signature can only be produced by the corresponding private key; thus, a
digital signature proves true ownership of a private key, without revealing
that private key. Therefore, a digital signature can be used to access and
control funds. In Ethereum, digital signatures are required to validate a
transaction.

## PKC & Cryptocurrency
PKC uses unique keys to secure information. These keys are based on mathematical
functions that are easy to calculate, but hard to calculate their inverse; for
example, prime factorization.

Trapdoor functions: given a piece of secret info, it turns a very difficult
problem into a trivial one. Ex., given one prime in a prime product, it is now
very easy to find the other one.

transaction details + private key = digital signature (of that tx)

All transactions in Ethereum must be signed with a digital signature in order
to verify that the private key owner actually owns the private key, and thus
should be granted to access and control funds in the account of question.

Key point: private keys are used to create digital signatures, which are
necessary for transaction authentication.

The "magic" of PKC is that to verify if a digital signature is valid, all that
is needed is the transaction details and Ethereum address. No use of the private
key is necessary. Thus, the private key can be kept private.

## Private Keys
A private key is simply a number between: 1 < n < 2^256. That is, it is 256
binary digits. This means the entire private key space is 2^256, which is 
roughly equivalent to 10^77, which in turn is roughly the number of atoms in
the visible universe. However, one critical point is that the number must be
chosen randomly.

Usually, we feed a large string of random bits into a 256-bit hash function, 
which produces a 256-bit number. This number, if within the valid range,
becomes the private key.

## Public Keys
An Ethereum public key is a *point* on an elliptic curve. More specifically,
it is a set of (x, y) coordinates that lies on the curve.

These two numbers are joined together, and the numbers are produced from the
private key by a one-way calculation. Thus, it is trivial to calculate the
public key from the private key, but virtually impossible to find the private
from the public.

What is this one-way calculation? It is "elliptic curve multiplication", which
is practically irreversible. This is the *discrete logarithm problem*.
Elliptic curve multiplication is:

K = k * G

where k is the private key, G is a generator point, and K is the resulting
public key. However, * is elliptic curve multiplication, not regular integer
multiplication. What this means is that there is no inverse function, ie,
division, such that you can easily find the private key k given the public
key K, ie, K/G = k. This is known as "finding the discrete logarithm" and is
as difficult as just brute force searching for all possible values of k.
This one-way mathematical function provides the basis of security for digital
signatures. You can publish your public key (address) anywhere, and be
confident that no one will know your private key. Similarly, when you sign
a message with your private key, the digital signature provides strong
cryptographic proof that you actually know the private key.

Ethereum uses secp256k1, a specific elliptic curve. What an elliptic curve is
at a conceptual level is essentially a scattering of dots over an extremely
large grid.

Elliptic curve addition is: given two points P1 and P2 on an elliptic curve,
there is a third point P3 = P1 + P2, also on the curve. Geometrically, we can
draw a line connecting P1 and P2, which intersects the curve at *exactly* one
other place--this point can be called P3' = (x, y). Then we reflect across
the x-axis to get P3 = (x, -y).

Multiplication simply extends addition. For a given point P on the curve, if
k is a whole number, then k * P = P + P + P + ... + P (k times).

Thus, in Ethereum, we start with our private key k, and multiply it by a
predetermined generator point G. Thus, we are adding G + G + G + ... + G, k
times. Thus, to generate the public key K, we add the generator point G to 
itself k times. G is always the same. This means that a private key and a
public key have a fixed relationship, however, the one-way property of elliptic
curve arithmetic means that you can't find k from K.

The final point, K, is actually two numbers (a coordinate pair). Ethereum uses
a serialization format that concatenates these two numbers (plus a prefix)
based on a cryptographic standard.

# Cryptographic Hash Functions
A hash function is: a function that maps data of arbitrary size to data of
fixed size.

Hash functions are used to derive the Ethereum address from the public key.
More specifically, the public key is hashed using keccak256. We then take the
last 20 bytes of the hash. These bytes are our Ethereum address.

Ethereum address - the last 20 bytes of the keccak256 hash of the public key

Ethereum addresses are raw hexidecimal without any checksum.

ICAP encoding - 34 alphanumeric characters consisting of a country code (XE for
Ethereum), 2-character checksum, and an account identifier.

EIP-55: Hex Encoding with Checksum in Capitalization
- Ethereum addresses are case insensitive
- We can take the hash of an address, which is a unique fingerprint. This hash
can serve as the checksum.

Now, we line up the hash and address, and we capitalize a character in the
address if iff the corresponding hash character is greater than 0x8. Thus,
we only capitalize certain letters *based on* the hash.

How does this detect errors in mistypes? Well, say we mistype an F for E. Then,
if the wallet is EIP-55 compliant, it notices the mixed capitalization.
The wallet converts the address to lowercase, and then takes the hash of this.
Now, the hash is lined up with the mixed capitalized address, as before.
However, the hash is now completely different, and it is highly unlikely that
the capitalization is all correct. The wallet notices this incorrect
capitalization, which means an error was introduced in the address.
