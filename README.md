# crypto-reading
Report from what I learned reading "INTRODUCTION TO MODERN CRYPTOGRAPHY: Second Edition (Jonathan Katz, Yehuda Lindell)"


Cryptographuy : For purposes of simplicity, it's a way for the sender to hide messages so only the intended reciever can get it.
Encryption or the process of encrypting messages broadly classifies itself into two categories: symmetric and assymetric.

Symmetric key encryption:
In symmetric key encryption, two parties already havea key beforehand. This means they can just encrypt and decrypt the message using the private key to converse.
This scheme has three major algorithms:
1. Key generation algorithm (gen) where key is created.
2. Encryption algorithm (enc): takes as input a key k and a message m
and outputs a ciphertext c (dec).
3. Decryption algorithm: takes the ciphertext c and using key k, decrypts it into message m.

DEC(ENC(M)) = M. -- basic rule

Kerkchoff's principle: knowledge of the entire encryption method beforehand should not help the attacker one bit. The chance of them getting the message should be equal to if they didn't know the scheme.
Basically, the key is the one and only secret factor.

Perfect secrecy: perfectly obey's kerkchoff's principle. No amount of computational power will ever crack the message without key.
Only one perfectly secret encryption method is known : One-Time-Pad.

One time pad encryption scheme: bitwise XOR with a key.
1. Key size should be atleast equal to message size, making it impractical for regular use.

Limitations of Perfect Secrecy: 
1. Key-message size problem
2. A particular key can only be used once to retain perfect secrecy.

Since perfect secrecy is infeasible and overkill, private key encryption can be done in other methods that only require that:
1. Security is only guaranteed against efficient adversaries that run for some
feasible amount of time.
2. Adversaries can potentially succeed (i.e., security can potentially fail)
with some very small probability.
3. secrecy be kept in the sense that attackers will solve the message given a million years with a million supercomputers or something like that.

Negligible function: basically a function that outputs a very very small number. denoted by negI
A private key encryption scheme is said to be secure if probability of figuring out the message is 1/2 + negI.

Message Authentication Codes (MACs)
MACs are a very crucial part of encryption. The problem with sending messages is that attackers, even if they cant read the message, could manipulate it. It could also be changed by natural phenomena.
MACs let the recieving party know whether the message was tampered with so they act accordingly.
Three parts : 
1. mac(m) : tag generation algorithm : makes tag t
2. gen : generates a key
3. Vrfy(m,t ): checks whether message is valid or invalid using tag t and key.


Assymetric key encryption or public key encryption:

Basics before getting into the definition:

Let a, b be positive integers. Then there exist integers X, Y such that Xa + Y b = gcd(a, b). Furthermore, gcd(a, b) is the smallest positive integer that can be expressed in this way.
Chinese remainder theorem : works only for co-primes, different remainder cycles will always line up if the numbers share no factors. and they will always occur once every LCM.
Hash function: it's a one way function that converts input into a fixed length string of characters.

public key encryption: 
A method to encrypt messages by using two keys: a public key and a private key. This allows sharing secret messages even without sharing a key beforehand. The message encrypted with a public key canonly be decrypted with a private key that the reciever has.

Slower than private key encryption.
steps: 
1. Gen(1ⁿ) outputs a key pair (pk, sk)
2. Enc(pk, m) encrypts m to produce ciphertext c.
3. Dec(sk, c) deterministically decrypts c using sk (secret key).
   


