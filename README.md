# PKI-Public-Key-Infrastructure
## Introduction to PKI (Public Key Infrastructure)

Public Key Infrastructure, as its name indicates, is more like a framework rather than a protocol.

- the primary components and procedures in the PKI.

- Asymmetric encryption
- One-way function
- Digital signature
- Digital certificate
- Certificate Authority

[Wikipedia Link] (https://en.wikipedia.org/wiki/Public_key_infrastructure)

[Digital signatures & PKI] ![image](https://user-images.githubusercontent.com/61211023/124836354-c17b0080-df7a-11eb-9129-477405d9ae9f.png)

A public key infrastructure (PKI) is a set of roles, policies, and procedures needed to create, manage, distribute, use, store, and revoke digital certificates and manage public-key encryption.

**Asymmetric encryption**

- A pair of keys
In asymmetric encryption, there is a pair of keys for one identity.
   - Private key
   - Public key
The private key must not be shared to others, while the public key can be shared with anyone.

If you have ever generated keys for application of SSH, you can find them in the following locations.
- ssh-keygen is a tool for creating new authentication key pairs for SSH

— www.ssh.com

- ~/.ssh/id_rsa // private key
- ~/.ssh/id_rsa.pub // public key

The file name may be id_rsa or id_dsa, which depending on your key generation algorithm.

**Encryption and decryption**

When a message is encrypted by the private key, it can be decrypted by the paired public key.
On the other hand, the message encrypted by the public key, can be decrypted by the paired private key.

