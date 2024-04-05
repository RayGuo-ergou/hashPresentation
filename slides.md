---
# try also 'default' to start simple
theme: the-unnamed
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides, markdown enabled
title: Cryptography - Hash Functions
info: PY presentation on Hash Functions
# apply any unocss classes to the current slide
class: text-center
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true
---

# Cryptography - Hash Functions

Presented by Ray

---
transition: fade-out
layout: image-right
image: https://cover.sli.dev
---

# Content

<v-click>

1. What are Cryptography and Hash Functions?
1. Where are Hash Functions used, and what are the purposes of Hash Functions?
1. What see the hashes? (A little demo)
1. Safety of hash functions.
1. Conclusion

</v-click>

---

# What are Cryptography and Hash Functions?

<v-click>

## Cryptography

Cryptography is the process of hiding or coding information so that only the person a message was intended for can read it. The art of cryptography has been used to code messages for thousands of years and continues to be used in bank cards, computer passwords, and ecommerce.

</v-click>

<v-click>

Cryptography can be achieved using various techniques such as encryption, hashing, and digital signatures. They are used for different purposes and have different properties. In this presentation, I will focus on hash functions.

</v-click>

<v-click>

## Hash Functions

A hash function is a function that takes an input (or 'message') and returns a fixed-size string of bytes. The output is typically a 'digest' that is unique to the input. Hash functions is a one-way function, meaning that it is easy to compute the hash value of an input, but it is computationally infeasible to generate the original input from the hash value.

</v-click>

---

# Where are Hash Functions used?

<v-click>

- **Data Integrity**: Hash functions are used to ensure that data has not been tampered with. For example, when you download a file from the internet, the website may provide a hash value for the file. You can compute the hash value of the downloaded file and compare it with the hash value provided by the website to ensure that the file has not been tampered with.

  ```bash
  # Neovim sha256 checksums
  44ee395d9b5f8a14be8ec00d3b8ead34e18fe6461e40c9c8c50e6956d643b6ca  nvim-linux64.tar.gz
  0c82e5702af7a11fbb916a11b4a82e98928abf8266c74b2030ea740340437bf9  nvim.appimage
  e3f3174d75c038915330db86bf685c704cb9be86863ee592a07e21203d32ced2  nvim.appimage.zsync
  19d2366e0d6da001583bd0b8a3db59f69ce3dda5fa41f3064c6778cef3edd34c  nvim-macos.tar.gz
  de6dc1f0edb45f5f225ee24ce80a4fcbc3a337932037e98ae143975fca2556bf  nvim-win64.zip
  006b8578f0b6717bc5a987f12bc0746c61c20e6ba777fde6d4aa53ee54b937cd  nvim-win64.msi
  ```

</v-click>

<v-click>

- **Password Storage**: Hash functions are used to store passwords securely. When you create an account on a website, the website will hash your password and store the hash value in their database. When you log in, the website will hash the password you provide and compare it with the hash value stored in their database to authenticate you.

</v-click>

---

# Where are Hash Functions used? contd.

<v-click>

- **Data Structures**: Hash functions are used in data structures such as hash tables to store and retrieve data efficiently. The hash value of the data is used as an index to store and retrieve the data.

  ```ts twoslash
  const hashTable = new Map<string, string>()
  hashTable.set('key1', 'value1')
  ```

</v-click>

<v-click>

- **Blockchain**: Hash functions are used in blockchain technology to create a unique identifier for each block in the chain. The hash value of each block is included in the next block, creating a chain of blocks that is tamper-proof.

</v-click>

---
transition: slide-up
---

# What see the hashes?

<!-- ./components/Hash.vue -->
<Hash></Hash>

---

# Hash Functions Safety

<v-click>

## Collision:

A collision occurs when two different inputs produce the same hash value. Hash functions are designed to minimize the probability of collisions, but they are not collision-free.

</v-click>

<v-click>

## Birthday Attack:
A birthday attack occurs when an attacker tries to find two different inputs that produce the same hash value. The birthday paradox states that the probability of two people in a room sharing the same birthday is higher than you might expect.

</v-click>

<v-click>

## Protecting Against Attacks:
Use a secure hash function that is resistant to collision attacks, such as SHA-256 and SHA-512.

</v-click>

---

# Hash Functions Safety contd.
<v-click>

## Consistent Hash:
Hash functions are deterministic, meaning that the same input will always produce the same hash value. This makes them predictable and vulnerable to attacks.

</v-click>

<v-click>

## Rainbow Table Attack:
A rainbow table attack occurs when an attacker uses a precomputed table of hash values to find the original input of a hash value. This can be used to crack passwords stored using hash functions.

</v-click>

<v-click>

## Salt:
A salt is a random value that is added to the input before hashing. This makes the hash value unique even if the input is the same. Salting passwords makes them more secure against rainbow table attacks.

</v-click>

---

# Conclusion

- Hash functions are an essential tool in cryptography and are used in many places.
- Hash functions are designed to be fast and efficient, but they are not collision-free.
- When developing software, use secure hash functions with salt to protect against attacks.

<v-click>

## A little suggestion

**NEVER use same password for multiple accounts. It may cause a Credential stuffing attack.**

</v-click>
---

# References

<ul>
  <div class="flex items-center gap-2">
    -<img src="/linkedin.svg" class="w-4 h-4" />
    <a href="https://www.linkedin.com/learning/conversations-on-cryptography/hashing?u=60318065" target="_blank">Linkedin Learning - Cryptography and Hash Functions</a>
  </div>

  <div class="flex items-center gap-2">
    -<img src="/slidev.svg" class="w-4 h-4" />
    <a href="https://sli.dev/" target="_blank">Slides made with slidev</a>
  </div>

  <div class="flex items-center gap-2">
    -<img src="/github.svg" class="w-4 h-4" />
    Text from my own and a little help by github copilot
  </div>

</ul>

---
class: text-center flex flex-col justify-center items-center
---

# Thank you for listening!

Any questions?
