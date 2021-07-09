# PKI-Public-Key-Infrastructure
## Introduction to PKI (Public Key Infrastructure)

Public Key Infrastructure, as its name indicates, is more like a framework rather than a protocol.

PKI or public key infrastructure is about how two entities learn to trust each other in order to exchange messages securely. You may already know that Kerberos and the KDC (Key Distribution Center) work on a shared-secrets principle, where users can go to a central authority and get authorization to communicate and act in a given network. PKI is a more complex system that understands lots of different networks which may or may not share a common trust authority. In PKI, you’re negotiating trust with a root which then tells you all the other entities that you can trust by default. The central idea of public key infrastructure is that some keys you already trust can delegate their trust (and hence yours) to other keys you don’t yet know. Think of it as a very warm introduction by a friend to someone you don’t yet know!

- the primary components and procedures in the PKI.

   - Asymmetric encryption
   - One-way function
   - Digital signature
   - Digital certificate
   - Certificate Authority

[Wikipedia Link] (https://en.wikipedia.org/wiki/Public_key_infrastructure)

![image](https://user-images.githubusercontent.com/61211023/124836354-c17b0080-df7a-11eb-9129-477405d9ae9f.png)

A public key infrastructure (PKI) is a set of roles, policies, and procedures needed to create, manage, distribute, use, store, and revoke digital certificates and manage public-key encryption.

**Asymmetric encryption**

- A pair of keys
In asymmetric encryption, there is a pair of keys for one identity.
   - Private key
   - Public key
The private key must not be shared to others, while the public key can be shared with anyone.

If you have ever generated keys for application of SSH, you can find them in the following locations.
- ssh-keygen is a tool for creating new authentication key pairs for SSH

- www.ssh.com

   - ~/.ssh/id_rsa // private key
   - ~/.ssh/id_rsa.pub // public key

The file name may be id_rsa or id_dsa, which depending on your key generation algorithm.

**Encryption and decryption**

When a message is encrypted by the private key, it can be decrypted by the paired public key.
On the other hand, the message encrypted by the public key, can be decrypted by the paired private key.

![image](https://user-images.githubusercontent.com/61211023/124837871-9c3bc180-df7d-11eb-87ac-48015fcc781a.png)

**Hash function**

Hash function is a one-way function that its result can be considered a small-sized snapshot of the original message. 
- The calculated result is called digest. 
- It is fast to calculate, and hard to revert. Therefore it is called one-way function.
- The digest for different messages is completely different. 
- Theoretically, there are collisions, but it’s nearly impossible to find the collided message for modern hash function. 

Thus, we can assume that the result of hash function is always unique to each message.

![image](https://user-images.githubusercontent.com/61211023/124838153-2b48d980-df7e-11eb-9eea-1b6123dfded7.png)

**Digital signature**

Digital signature is like a real-life signature. It is used to ensure that the message is confirm by the signer, and no further changes are made beyond the knowledge of the signer.
- The signature is generated by two steps.
   - Get the digest of the message
   - Use sender’s private key to encrypt the digest
    
That is, the encrypted message digest is the sender’s digital signature.

You can see the following diagram learning the steps to verify the integrity of the message by digital signature.

![image](https://user-images.githubusercontent.com/61211023/124838312-78c54680-df7e-11eb-81aa-d39b0e6e9faf.png)

**Digital certificate**

Digital certificate is used to verify the identity of the sender, i.e. authenticity of the sender. 

- Digital certificate contains several main components.
   - Subject (owner)
   - Subject’s public key
   
Issuer’s digital signature, to ensure the identity of subject’s identity and its public key. 

We often call it **Certificate Authority (CA).**

**When we verify a message’s signature, we have to use its public key.**

*How can we ensure that the public key (and the authority’s signature) is really from a trustable authority?*

**Simple solution**

A few certificated authorities are pre-configured in users’ OS and browsers. By the time they install the software, a list of CAs is trusted by default.

You trust several CAs, and the CAs will help you to verify all other people in the world.

**Elements of security**
- The three elements of security are

   1. Authenticity — The message is truely sent from the people we are expecting.
   2. Integrity — The message is not altered by unauthorized people.
   3. Confidentiality — The message is encrypted and can only be decrypted by authorized people.

The two major uses for PKI are for email and web traffic. On a very high level, remember that traffic over the Internet is just a series of packets — little chunks of bits and bytes. While we think of email messages and web requests as philosophically distinct, at the heart, they’re just packets with different port addresses. We define the difference between messages and web requests arbitrarily, but the bits and bytes are transmitted in an identical fashion. So, encrypting those packets is conceptually the same in PKI as well.

The other major use for PKI is a web server authenticating and encrypting communications back and forth between a client — an SSL/TLS certificate that’s installed and working when you see “https” instead of “http” at the beginning of a URL. Most of the time, when we’re talking about PKI in a policy sense or in industry, this is what we mean. Certificate authorities such as DigiCert, Comodo, LetsEncrypt, and others will create those paired keys for websites to use to both verify that they are who they say they are, and to encrypt traffic between a client who’s then been assured that they’re talking to the correct web server and not a visually similar fake site created by an attacker.

There are a few other uses for PKI, including encrypting documents in XML and some Internet Of Things applications (but far, far fewer IoT products are using PKI well than should be, if I can mount my saponified standing cube for a brief moment).

**Why do we use PKI and why do information security experts continue to push people and businesses to use encryption everywhere?**

It’s because encryption is the key (pun absolutely intended) to increasing the expense in terms of time for people who have no business watching your traffic to watch your traffic. Simple tools like Wireshark can sniff and read your mail and web traffic in open wireless access points without it.

**Here’s how to conceptualize PKI**

PKI has become an appliance with service providers and a functional oligopoly of certificate authorities that play well with the major browsers. That isn’t necessarily a bad thing; it’s simply how this technology evolved into its current form of staid usefulness and occasional security hiccups. In reality, most people would do better knowing how best to implement PKI, since vulnerabilities are in general about the endpoints of encryption, not in the encryption itself. For instance: don’t leave 777 perms on the directory with your private keys. If your security is compromised, it’s likely not because someone cracked your key encryption — they just snagged the files from a directory they shouldn’t have been allowed in. Most PKI security issues are actually sysadmin issues. A new 384-bit ECDSA key isn’t going to be cracked by the NSA brute forcing it. It’ll be stolen from a thumb drive at a coffee shop. PKI security is the same as all other kinds of security; if you don’t track your assets and keep them updated, you’ve got Schroedinger’s Vulnerability on your hands.

![image](https://user-images.githubusercontent.com/61211023/124841075-51717800-df84-11eb-8f7e-ee8c9a2a4829.png)

![image](https://user-images.githubusercontent.com/61211023/124841100-63ebb180-df84-11eb-85e4-8068abc6619b.png)

![image](https://user-images.githubusercontent.com/61211023/124841337-e4aaad80-df84-11eb-9b79-9ad39c5d310d.png)


**RSA public key : Behind the scene**

![image](https://user-images.githubusercontent.com/61211023/125069082-2f741480-e0ae-11eb-9497-3f690b20cae9.png)

**What is public and private key in RSA Signing?**
   - Private key is used to sign a mail / file by the sender and public key is used to verify the signature of the mail / file by the recipient.
   - Private key contains the prime numbers, modulus, public exponent, private exponent and coefficients.
   - Public key contains modulus and public exponent.
   - Modulus (n) is the product of two prime numbers used to generate the key pair.
   - Public exponent (d) is the exponent used on signed / encoded data to decode the original value.

**Generate RSA private and public key using openssl**

```shell script
# Generate 1024 bit Private key
$ openssl genrsa -out myprivate.pem 1024
# Separate the public part from the Private key file.
$ openssl rsa -in myprivate.pem -pubout > mypublic.pem
# Display the contents of private key
$ cat myprivate.pem
-----BEGIN RSA PRIVATE KEY-----
MIICXQIBAAKBgQDRFNU++93aEvz3cV8LSUP9ib3iUxT7SufdVXcgVFK9M3BYzvro
A1uO/parFOJABTkNhTPPP/6mjrU2CPEZJ1zIkpaSNJrrhpp/rNMO9nyLYPGs9Mfd
BiWUPmHW5mY1oD0ye4my0tEsHOlgHC8AhA8OtiHr6IY0agXmH/y5YmSWbwIDAQAB
AoGAAj/IH3pUI6FqqTrF+/gYzCRsL4AXTLC8l8vwkR93GGPyRHJNjqtik8I3WrXJ
zUiBGZ0iNouIsL/+QQuNlGiw/c5i2X3nTntREDS9xs2M0x+MWD/5qI1sn0Qk0HNP
BbDczlvO8wXNFGIHiTiPVEawoeNwhMqJDyGcbsEOZp2pLokCQQDvlMBU6dOeOP9a
jnENFSlrvzNR0nugFeoGmfq6s4Czz2QtUd9baKqBfEBSdJskwFVHgxbFA1Dc7iFu
rJkoQEeFAkEA32j9ibSVryxLvWUZngKNwo2xE+wcYDAYVBMsYC3OBU3FXhVkFD06
ZVnJsY/4bd2VdQI+bI2KV99aHutMJG2WYwJABMn2ZjweTMVa5VZ/kAFiSJMT1Yjd
i7+kY+lkB6Na6T02BWnjixI2hkwThRJrn3pwufM2201Lqn7gEDRHA3T1eQJBAKZG
1RUNo6558HEo8vUIf4vCu33RaJkqkqDYmFmJHeISrQfGMfNiUrkmJ5iRR9w1ZExu
/Bj9C281XDTQ+Z3PNnMCQQCan+pvj0OZH6o0PAMJGBBwRECPpfZ6mUjwA2YD3g61
MHjtIYmKKGmn64Qs8zQ4mNEDboQqyaov3Ij/I6c0ZQlc
-----END RSA PRIVATE KEY-----





