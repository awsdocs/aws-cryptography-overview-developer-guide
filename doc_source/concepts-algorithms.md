# Cryptographic algorithms<a name="concepts-algorithms"></a>

An *encryption algorithm* is a formula or instructions series that converts a plaintext readable message into an unreadable ciphertext\. Algorithms use advanced mathematics and one or more encryption keys to make it relatively easy to encode a message but virtually impossible to decode without knowing the keys\. Algorithms often involve multiple layers of encryption and can require additional random and sequential one\-time values that prevent attacks and duplicate results\. 

AWS cryptography tools and services that encrypt data support secure algorithms that are publicly vetted\. Some tools and services, like AWS Key Management Service \(AWS KMS\) use a particular algorithm\. AWS KMS uses the Advanced Encryption Standard \(AES\) algorithm in Galois/Counter Mode \(GCM\) with 256\-bit secret keys\. Other tools and services offer multiple algorithms and key sizes but recommend a secure default choice\.

This section describes some of the symmetric and asymmetric algorithms that AWS tools and services support\.

**Topics**
+ [Symmetric algorithms](#concepts-algos)
+ [Asymmetric algorithms](#concepts-asymm)

## Symmetric algorithms<a name="concepts-algos"></a>

### <a name="concepts-symm"></a>

AWS cryptographic tools and services commonly support two widely used symmetric algorithms\. Both are known as block ciphers\.
+ **AES** – [Advanced Encryption Standard](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) \(AES\) with 128\-, 192\-, or 256\-bit keys\. AES is often combined with [Galois/Counter Mode](https://en.wikipedia.org/wiki/Galois/Counter_Mode) \(GCM\) and known as AES\-GCM\.
+ **Triple DES** – Triple DES \(3DES\) uses three 56\-bit keys\. The scheme works on a block of data by splitting it in two and iteratively applying arbitrary round functions derived from an initial function\. Triple DES uses 48 rounds to encrypt a block of data\. 

An encryption scheme is called *symmetric* if it uses the same key to both encrypt and decrypt plaintext\. Technically, the encryption key *e* and decryption key *d* don't have to be exactly the same\. All that's required is that it's computationally trivial to determine *d* when you know *e* and *e* when you know *d*\. However, in most practical symmetric encryption schemes, *e* and *d* are the same\. 

**Note**  
Symmetric encryption is also called *shared key*, *shared secret*, and *secret key* encryption\. It is not called *private key* encryption\. Convention reserves the term *private key* for asymmetric cryptography, which centers around the idea of a private key and a corresponding public key\. 

Symmetric key encryption requires that all intended message recipients have access to the shared key\. Therefore, a secure communication channel must be established among the participants so that the key can be transmitted to each along with the ciphertext\. This presents practical problems and limits the use of direct symmetric key exchange\. 

The following illustrations show how encryption and decryption work with symmetric keys and algorithms\. In the first illustration, a symmetric key and algorithm are used to convert a plaintext message into ciphertext\.

![\[Symmetric key encryption diagram\]](http://docs.aws.amazon.com/crypto/latest/userguide/images/Symmetric_Key_Encryption_sm.png)

The following illustration shows the same secret key and symmetric algorithm being used to turn ciphertext back into plaintext\.

![\[Symmetric key decryption diagram\]](http://docs.aws.amazon.com/crypto/latest/userguide/images/Symmetric_Key_Decryption_sm.png)

There are two types of symmetric key ciphers, block ciphers and stream ciphers\. A **block** cipher divides the plaintext messaged into fixed\-length strings called blocks and encrypts one block at a time\. Block ciphers are typically considered to be more powerful and practical primitives than stream ciphers, but they're also slower\. **Stream** ciphers encrypt each unit of plaintext, one unit at a time, with a corresponding unit of a key stream\. The result is a single unit of ciphertext\. 

## Asymmetric algorithms<a name="concepts-asymm"></a>

AWS services typically support RSA and Elliptic Curve Cryptography \(ECC\) asymmetric algorithms\.

An encryption scheme is called *asymmetric* if it uses one key to encrypt and a different, but mathematically related, key to decrypt\. It must be computationally infeasible to determine one key if the only thing one knows is the other key\. Therefore, one key can be distributed publicly while the related key is kept secret and secure\. Together the keys are referred to as a *key pair*\. The key that's publicly distributed is called the *public key* and the key that's kept secret is called the *private key*\. 

Another more common name for asymmetric encryption is *public\-key* cryptography\. Public key cryptography is typically based on mathematical problems that are relatively easy to perform but cannot be easily reversed\. These include factoring a large integer back into its component prime numbers and solving the elliptic curve discrete logarithm function\. The RSA algorithm is based on the practical difficulty of factoring the product of two large prime numbers\. Elliptic curve cryptography is based on the difficulty of finding the discrete logarithm of a random point on an elliptic curve given a publicly known point\. 