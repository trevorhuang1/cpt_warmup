---
toc: false
comments: true
layout: base
title: Binary Color Generator
description: Random color generator chooses random numbers between 0 and 255 for each of red, green, and blue. The decimal is converted into 8-bit binary and displays the color combination in (R, G, B) and their binary representaations.
courses: {compsci: {week: 1}}
type: tangibles
---

# Stego
Key Commits:
- [stego encoder + decoder implementation](https://github.com/trevorhuang1/cpt_warmup/commit/19b5222fb5bb63762c1bba148aca17f166b11b13)

Key Points:
- Figuring out how to do stego (u gotta take the least signficant bits of each pixel on the image in order to encrypt message)
- figuring out how to take input from images
- processing image data
- outputting images

Improvements: 
- could make image download process more streamlined, maybe click of a button auto downloads image
- find ways to make encoding more efficient
<img src="https://media.discordapp.net/attachments/887546581459554335/1180027619459223602/image.png?ex=657bed5c&is=6569785c&hm=1221fe6bd4904ff61e557c02aaac936ab3cc8857abeedc3ed2fe6157b2a63aa9&=&format=webp&quality=lossless&width=561&height=621">

<img src="https://media.discordapp.net/attachments/887546581459554335/1180027885948522596/image.png?ex=657bed9b&is=6569789b&hm=cfeaf1e17202583ec3fe940a957c074f22e7b6946d880c86f20a061ab38936e0&=&format=webp&quality=lossless&width=559&height=621">
# Ascii Art
Key Points:

* Binary representation of bits in the image
* *Astrix* and _ for every bit creating the ascii art
* User can apply specific image into program

Possible Improvements:

* Work on sizing of the image to fit perfectly
* Implement black background to make ascii image look better
* Incorporating more elements into feature

Commits:

[Work on Program](https://github.com/trevorhuang1/cpt_warmup/commit/8d2ce0585463927361336e4c41df17ed84b469e7)

[Update on Canvas](https://github.com/trevorhuang1/cpt_warmup/commit/4d3509a5712ab6adcf702b442bc1e325e379a30a)

# Binary Project - Random Color Generator

- Validate RGB Values
- Convert RGB Decimal to Binary
- Have sample RGB value input (decimal)
- Display color in RGB format
- Displaying converted RGB values in binary

<img src = "https://media.discordapp.net/attachments/1174540464951676969/1174591418451369994/image.png?ex=65682681&is=6555b181&hm=10da97d668d2ce6c0e1dea11fd5e9fd743ab5dacc88778b282c5017d15aa1c79&=&width=1333&height=993">

- Key Commits

<a href="https://github.com/trevorhuang1/cpt_warmup/commit/9da25de7e4f114a33fdb5028e7b4d3d236659a6e">js color generator</a>

<a href="https://github.com/trevorhuang1/cpt_warmup/commit/2d1eac0c2044606f30e2e8d65da9342d9a673608">python binary colorgen</a>

<a href="https://github.com/trevorhuang1/cpt_warmup/commit/a9aa10d3a696960b662604dc98f4ea624c7f5fe5">sample color input</a>