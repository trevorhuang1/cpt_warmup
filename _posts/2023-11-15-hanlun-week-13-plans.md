---
toc: false
comments: false
layout: base
title: Hanlun's Plans - Steganography Project
description: 
courses: {compsci: {week: 1}}
type: plans
---

## Steganography Encoder:
- convert string you want to hide into binary
-  Read image, get info in each pixel
- convert each into binary
- Modify the least significant bit/ least significant bits (last 1 or last 2) bits to the corresponding bit in the binary string that we made
- save new binary as a new image, then return that image to the user (this image has the encrypted text inside of it)
- make a decrypter, read the least significant bits of each pixel, then add them all to a binary string, then convert that binary string back into a text message

<img src="https://media.discordapp.net/attachments/1174540464951676969/1174593785125158952/image.png?ex=656828b5&is=6555b3b5&hm=a7011f9a63a9b4446ba284351661dfa585a85b633f4d4548d6ce0ea363583709&=">