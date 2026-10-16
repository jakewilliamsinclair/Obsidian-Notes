# Stream Cipher
Treats key and plaintext as a stream of bits, performing an operation on the matching bit of each.
RC4 XORs the bits.

# Block Cipher
Groups bits of the plaintext to equal sized blocks of the ciphertext.
A block cipher is good if it **confuses** the relationship between key and ciphertext and **diffuses** the bits across the ciphertext.

## DES
Data encryption standard (old) involves swapping the left and right half of the input (64 bits) and between each swap XORing the new left with the sub-key, a part of the 56 bit key.

## AES
Advanced version of DES, network of linear transformations and substitutions.

# Block Cipher Modes
## ECB - Electronic CodeBook
Each block is ciphered independently.
## CBC - CipherBlock Chaining
Each block is XORed with the previous ciphertext block, chaining the cipher blocks, this requires an iv for the first block.
$c_{j}=E_{k}(m_{j}\oplus c_{j-1})$ 
Error in $c_{j}$ prevents its decryption and $c_{j+1}$ as $c_j$ must be used to decrypt it, it does not propagate further as $c_{j+1}$ is not corrupted and can be used for $c_{j+2}$.
## CTR - CounTeR
Encrypt a counter value and XOR with the plaintext
$c_{j}=E_{k}(iv+j-1)\oplus m_{j}$ 
The same key is used each time but on a different value of $iv+j-1$ so the keySTREAM is different each time.
## CFB - Cipher FeedBack
$c_{j}=E_{k}(c_{j-1})\oplus m_{j}$ where $c_{0}=iv$ 