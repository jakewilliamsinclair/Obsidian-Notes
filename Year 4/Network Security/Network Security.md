$\newcommand{\Z}{\mathbb{Z}}$
# CIA - Information Security

## Confidentiality
Preventing disclosure of information to unauthorised entities

## Integrity
Preventing unauthorised modification of information

## Availability
Data is accessible and usable upon demand by an authorised entity

In cryptography availability becomes
Authenticity: preventing attribution of data to false origin.

## Definition of an Encryption Scheme

Encryption scheme if E: KxM→C, D: KxC→M

Encryption, Decryption, Keys, M plaintexts Ciphertexts


# Types of Cipher
## Caesar
Simple, shift all letters of an alphabet by a certain amount, this amount is the key.
## Polyalphabetic Substitutions (Vigenere)
Vigenere uses different shift amounts for the same plaintext letter, often done by using a keyword to give a pattern of shifts e.g.
   L    A    N   D = shifts of
+11 +0 +13 +3
### Attacks
Assume we know the key length, now we know that every 4th letter is shifted the same amount and you can determine the distribution of the ciphertext letters in each of the four groups to determine the four shift amounts.

If we don't know the key length it can be determined, guess all key lengths (say 1-100) and if the guess is correct the ciphertext character in a group will have been shifted by the same amount and each group will exhibit the same distribution of letters as the alphabet.
## Block Cipher
Vigenere is also an example of a block cipher, where the plaintext is divided into blocks of a fixed size and the algorithm is applied to each block.
## Types of Attack
- Ciphertext only
- Known-Plaintext
## One-Time Pad (Vernam Cipher)
Each letter of the plaintext is shifted by a fresh, randomly chosen number of positions in the alphabet.
Formally defined as
$K=M=C=\{0,1\}^t$ bit strings of length $t$ 
$E_{k}(m)=k\oplus m$ 
$D_{k}(c)=k\oplus c$ 
![[Pasted image 20261010111411.png|374]]
The One-Time Pad is perfectly confidential, given that the key is chosen uniformly randomly from the set of keys K and is not reused.

This makes using the OTP unpractical as the key must be as long as the message, it is difficult to generate truly random strings and the key cannot be reused.

# Symmetric Cryptography
## Stream Ciphers
Use the key $k$ to generate a keystream $k=k_1,k_2,...$ where each $k$ is a bit.
Break the plaintext message $m$ into a sequence of bits $m_1,m_2,\dots,m_n$ 
Each $m_i$ is encrypted with the $i^{th}$ element $k_i$ as
$c=E_{k}(m)=E_{k_{1}}(m_{1})E_{k_{2}}(m_{2})\dots$ 
### Example (RC4)
Generates its keystream from a key from 64 to 2048 bits in size.
To encrypt; keystream is XORed to the plaintext.
## Block Ciphers
Block ciphers map an $n$-bit block of plaintext to an $n$-bit block of ciphertext.
For an $n$-bit block there are $2^{n}$ plaintexts and thus $(2^{n})!$ permutations of the plaintexts to ciphertexts.
Imagining a codebook that contains all permutations
$E_{k}: \{0,1\}^{n} → \{0,1\}^{n}$ 
Is the permutation on page $k$ of volume $n$ of the book, so to use this Alice and Bob agree on a secret page number $k$ 
![[Pasted image 20261010114519.png|536]]
**Note**
An 8 bit block cipher would have $(2^{8})!=10^{82}$ mappings, which is around the number of atoms in the universe.
### Concepts for Good Design
- Confusion: obscuring the relationship between key and ciphertext
- Diffusion: spreading out bits in the plaintext across ciphertext
- Typically modern block ciphers:
	- use **substitution** to add confusion
	- use **transposition** to add diffusion
	- apply rounds of each to improve both
### DES (Data Encryption Standard)
DES is an antiquated block cipher that is no longer considered secure.
It involves swapping and mixing the left and right halves of the input (64 bits)
with the 56 bit key. The same is done in reverse to decrypt.
![[Pasted image 20261010115853.png|449]]
### AES (Advanced Encryption Standard)
Replaced DES, having block sizes of 128 bits and key sizes of 128/192/256 bits.
Built as a network of linear transformations and substitutions, with 10, 12 or 14 rounds, depending on key size.

## Block Cipher Modes
### ECB - Electronic CodeBook
Each block of the plaintext $m_{j}$ is enciphered independently $c_{j}=E_{k}(m_{j})$ 
Not secure against chosen plaintext attacks.
### CBC - CipherBlock Chaining
Each plaintext block $m_j$ is XORed with the previous ciphertext $c_{j-1}$ block before encryption. An initialisation vector (random, not secret) is used for $c_0$.
$c_{j}=E_{k}(m_{j}\oplus c_{j-1})$ 
Error in block $c_i$ affects only $c_i$ and $c_{i+1}$, any plaintext change requires entire ciphertext recompute, encryption cannot be parallelised but decryption can as ciphertext can be used for next block.
### CTR - CounTeR
Block cipher used as a stream cipher. Each element in keystream is computed directly from the initialisation vector, allowing parallelisation.
$c_{j}=E_{k}(iv+j-1)\oplus m_{j}$ 
Error in block $c_i$ only affects that block, plaintext change only requires that block is recomputed, can be parallelised both ways.
### CFB - Cipher-FeedBack
Encryption function of block cipher is used as a stream cipher.
$c_{j}=E_{k}(c_{j-1})\oplus m_{j}$ where $c_{0}=iv$ 
### OFB - Output FeedBack
This mode works like a stream cipher. A sequence of blocks is generated and XORed to the plaintext blocks. Each generated block is fed back to generate the next block. The first block is generated from the $iv$.
$c_j=O_j\oplus m_j$ , where $O_j=E_k(O_{j-1})$ and $O_0=iv$.
## Cryptographic Hash Functions
Maps a string of **arbitrary length** to a string of **fixed length** (hash).
- One-way (aka preimage resistance):
	- Given h(x) it is computationally difficult to find a y such that h(x) = h(y).
- Weak collision resistance (aka second preimage resistance):
	- Given x, it is difficult to find a y ≠ x such that h(x) = h(y).
- (Strong) collision resistance:
	- It is difficult to find x and y ≠ x such that h(x) = h(y).
Since the domain (inputs) is larger than the range (outputs), collision **must** exist.
### Integrity Protection
Hash functions can also be used to protect [[Network Security#Integrity|integrity]] of an input (file, email, etc) by providing the hash of the input and having the recipient hash their received output and checking they are the same.
### MACs - Message Authentication Codes
A keyed hash, or HMAC (Hash-based MAC) denoted as $h_{K}(x)$, where $K$ is the key and $x$ the input. Due to the presence of a key HMACs are symmetric.
Alice sends $x$ and $h_{K}(x)$ to Bob, he receives $x'$ and hash value $h'$. He computes $h_{K}(x')$ and confirms it matches $h'$.
## Authenticated Encryption and AES-GCM
There are several ways to combine encryption and message authentication
schemes, e.g., encrypt-and-mac, encrypt-then-mac, mac-then-encrypt, etc.
It is good to perform encryption and authentication as a single operation (authenticated encryption), with an example being AES-GCM.
### GCM - Galois/Counter Mode
Extends CTR mode by including a keyed hash value, referred to as the authentication tag, included in the ciphertext. The tag has the same size as a block of the cipher.
$h_{i} = (h_{i-1}\oplus b_{i})\times E_{k}(0)$ 
The tag is checked before decryption occurs.
# Asymmetric Cryptography (Public Key)
## Modular Arithmetic
$\Z$ is the set of all integers $\{\dots,-2,-1,0,1,2,\dots\}$ 
$\Z=\{0,\dots,p-1\}$ is the set of all positive integers modulo p
$\Z_{7}^∗=\{1,2,3,4,5,6\}$ 
$\Z_{15}^∗=\{1,2,4,7,8,11,13,14\}$ 
## One-way Functions
Easy to compute but hard to invert (no algorithm exists)
Examples:
- Pre-image resistant hash functions
- Multiplication of two large prime numbers (factoring is hard)
- Discrete Exponentiation
	- e.g. exponentiation modulo a large prime number
### Discrete Exponentiation
Easy to compute in "linear time"
$3^{65537}\ mod\ 10=?$ 
![[Pasted image 20261010125455.png|507]]
Now try to reverse it, discrete logarithms are not as easy.
### Generators
2 is a generator of $\Z_{11}^*$ as 
![[Pasted image 20261010130551.png]]
## Diffie-Hellman Key Exchange
**NOTE**: All operations in $\Z_{p}$ are $mod\ p$ so we will omit it.
g is a generator of $\Z_{p}^{*}$ 
**Alice**:
random $x$ from $\{1,\dots,p-2\}$ 
send $g^{x}$ 
**Bob**:
random y from $\{1,\dots,p-2\}$ 
sends $g^{y}$ 

Alice computes $k_{A}=(g^{y})^{x}=g^{xy}$ 
Bob computes $k_{A}=(g^{x})^{y}=g^{xy}$ 
Eve: knows p, g, $g^x$ and $g^y$, should not be able to compute $g^{xy}$.
Eve cannot calculate as she doesn't have $x$ or $y$, only $g^x$ and $g^y$ and due to the difficulty of getting $x$ or $y$ from these it is secure and $g^{xy}$ cannot be computed.
### Attacks
This algorithm is secure against a passive adversary as they cannot compute and values from the available information but an active adversary can perform a man in the middle attack, pretending to each person to be the other.
![[Pasted image 20261010131931.png]]
Furthermore Diffie-Hellman requires both parties to be "online".
## Public Key Encryption
Anyone can encrypt a message using a public key but only intended parties can use their secret key to decrypt. In terms of Diffie-Hellman, $g^y$ is Bob's public key and $y$ is Bob's secret key.
## ElGamal Encryption Scheme
With $g^a$ as someone's public key and $a$ as someone's private key, we have an encryption scheme.
Alice's ciphertext is now $(c_{1},c_{2})=(g^x,g^{xy}\times m)$ 
Bob can decrypt using his private key $y$:
$(g^x)^y=g^{xy}$ 
$\frac{c_{2}}{g^{xy}}=m$ 
