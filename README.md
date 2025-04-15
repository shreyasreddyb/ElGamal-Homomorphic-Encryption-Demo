# ElGamal Homomorphic Encryption Demo

## Overview

This project provides an interactive, in-browser demonstration of the ElGamal cryptosystem, specifically highlighting its multiplicative homomorphic encryption properties. The demo is implemented entirely in client-side JavaScript, allowing users to explore the concepts of homomorphic encryption through a practical, hands-on interface.

## Features

- **Key Generation**: Generate ElGamal public and private keys with selectable prime bit lengths
- **Encryption**: Encrypt numerical messages using the ElGamal public key
- **Decryption**: Decrypt ciphertexts using the ElGamal private key
- **Homomorphic Multiplication**: Demonstrate multiplication of encrypted values without decryption
- **Educational Content**: Each section includes explanations of the underlying cryptographic principles

## What is Homomorphic Encryption?

Homomorphic encryption is a form of encryption that allows computations to be performed on encrypted data without first decrypting it. The result of the computation, when decrypted, matches the result of the same computation performed on the plaintext.

The ElGamal cryptosystem is specifically **multiplicatively homomorphic**, meaning it supports multiplication operations on encrypted data. Given two encrypted messages, you can compute their product in the encrypted domain, and the decryption of this product will equal the product of the original plaintexts.

## Technical Details

### ElGamal Cryptosystem

The ElGamal cryptosystem is based on the difficulty of the discrete logarithm problem and consists of:

1. **Key Generation**:
   - Choose a large prime number `p` and a generator `g` of the multiplicative group of integers modulo `p`
   - Select a random integer `x` (1 < x < p-1) as the private key
   - Compute `h = g^x mod p` as the public key
   - Public parameters: (p, g, h); Private key: x

2. **Encryption**:
   - To encrypt a message `m` (where m < p):
   - Choose a random ephemeral key `y` (1 < y < p-1)
   - Compute `c1 = g^y mod p`
   - Compute `c2 = m * h^y mod p`
   - The ciphertext is the pair (c1, c2)

3. **Decryption**:
   - To decrypt the ciphertext (c1, c2):
   - Compute `s = c1^x mod p`
   - Compute `m = c2 * s^(-1) mod p` where s^(-1) is the modular inverse of s modulo p

4. **Homomorphic Multiplication**:
   - Given two ciphertexts (c1_1, c2_1) for m1 and (c1_2, c2_2) for m2:
   - Compute `c1_result = c1_1 * c1_2 mod p`
   - Compute `c2_result = c2_1 * c2_2 mod p`
   - When decrypted, (c1_result, c2_result) yields m1 * m2 mod p

### Implementation

The demo is implemented using:
- **HTML/CSS**: For the user interface
- **JavaScript**: For cryptographic operations
- **BigInt**: For handling large integers required in cryptography
- **Miller-Rabin Primality Test**: For generating probable prime numbers
- **Extended Euclidean Algorithm**: For computing modular inverses

## Security Considerations

This demo is intended for educational purposes and uses relatively small prime numbers for faster computation in the browser. In a real-world application:

- Much larger prime numbers would be used (typically 2048-bit or larger)
- Additional padding and security measures would be implemented
- More comprehensive primality testing would be performed
- Proper cryptographically secure random number generation would be employed

## Getting Started

1. Clone this repository or download the files
2. Open `index.html` in a modern web browser
3. Follow the tabs from left to right (Key Generation → Encryption → Decryption → Homomorphic Operation)
4. Experiment with different values to understand how the system works

## Browser Compatibility

The demo requires a modern browser with support for:
- ES6 JavaScript features
- BigInt support (available in all major browsers since 2020)

## License

[MIT License](LICENSE)

## Future Improvements

Potential enhancements for this project include:
- Adding support for more complex homomorphic operations
- Implementing additional homomorphic encryption algorithms (e.g., Paillier)
- Visualizing the mathematical operations
- Adding comprehensive unit tests
- Creating a server-side component for larger primes and more secure operations

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Acknowledgments

This demo was created to help understand the practical aspects of homomorphic encryption and the ElGamal cryptosystem.
