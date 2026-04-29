# SHA-0 Implementation in C

This is a simple implementation of the SHA-0 hashing algorithm in pure C language.

Forked from [halloweeks/sha1](https://github.com/halloweeks/sha1).

## Introduction

The Secure Hash Algorithm 0 (SHA-0) is a cryptographic hash function that produces a 160-bit (20-byte) hash value known as a message digest, typically rendered as a hexadecimal number, 40 digits long. It was designed by the National Security Agency (NSA) and published by the National Institute of Standards and Technology (NIST) as a U.S. Federal Information Processing Standard. It was withdrawn by the NSA shortly after publication and was superseded by the revised version, published in 1995 in FIPS PUB 180-1 and commonly designated SHA-1. SHA-1 differs from SHA-0 only by a single bitwise rotation in the message schedule of its compression function. According to the NSA, this was done to correct a flaw in the original algorithm which reduced its cryptographic security.

## Features

- Implemented in pure C language.
- Supports hashing of data from memory buffers.
- Follows the SHA-0 specification as outlined in FIPS PUB 180.
- Provides both a simple function interface (`SHA0()`) and a `SHA0_CTX` structure for processing multiple chunks of data.

## Usage

### Using the `SHA0()` Function

```c
#include "sha0.h"

int main() {
    unsigned char data[] = "Hello, World!";
    unsigned char hash[SHA0_BLOCK_SIZE];

    SHA0(data, sizeof(data) - 1, hash);

    // Print or use the hash as needed
    return 0;
}
```

### Using the `SHA0_CTX` Structure

```c
#include "sha0.h"

int main() {
    unsigned char data1[] = "Hello, ";
    unsigned char data2[] = "World!";
    unsigned char hash[SHA0_BLOCK_SIZE];
    
    SHA0_CTX ctx;

    SHA0_Init(&ctx);
    SHA0_Update(&ctx, data1, sizeof(data1) - 1);
    SHA0_Update(&ctx, data2, sizeof(data2) - 1);
    SHA0_Final(&ctx, hash);

    // Print or use the hash as needed
    return 0;
}
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
