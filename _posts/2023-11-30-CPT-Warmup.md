---
toc: false
comments: true
layout: base
title: CPT Warmup
description: CPT Warmup Tangibles
courses: {compsci: {week: 1}}
type: tangibles
---

# Stego

<a href="https://trevorhuang1.github.io/cpt_warmup//2023/11/14/stego.html">Link to project (click)</a><br>
<a href="https://github.com/trevorhuang1/cpt_warmup/blob/main/_posts/2023-11-14-stego.md?plain=1">Link to code (click)</a>

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

# Ascii Art

<a href="https://trevorhuang1.github.io/cpt_warmup//2023/11/15/ascii-art.html">Link to project (click)</a>

<a href="https://trevorhuang1.github.io/cpt_warmup//2023/11/15/ascii-art-plan.html">Link to code (click)</a>

Key Points:

* Binary representation of bits in the image
* *Astrix* and _ for every bit creating the ascii art
* User can apply specific image into program

Possible Improvements:

* Work on sizing of the image to fit perfectly
* Implement black background to make ascii image look better
* Incorporating more elements into feature

Commits:

[Work on Program (click)](https://github.com/trevorhuang1/cpt_warmup/commit/8d2ce0585463927361336e4c41df17ed84b469e7)

[Update on Canvas (click)](https://github.com/trevorhuang1/cpt_warmup/commit/4d3509a5712ab6adcf702b442bc1e325e379a30a)

# Color Generator

<a href="https://trevorhuang1.github.io/cpt_warmup//2023/12/03/js-colorgen-embed.html">Link to project (click)</a><br>
<a href="https://trevorhuang1.github.io/cpt_warmup//2023/11/14/binary-color-generator_IPYNB_2_.html">Link to code (click)</a>

- Input decimal values 0-255 in each box
- Code validates RGB values
- Converts RGB decimal to binary
- Displays converted RGB values in binary
- Displays final color

<img src = "https://media.discordapp.net/attachments/1174540464951676969/1174591418451369994/image.png?ex=65682681&is=6555b181&hm=10da97d668d2ce6c0e1dea11fd5e9fd743ab5dacc88778b282c5017d15aa1c79&=&width=1333&height=993">

## Key Commits

- <a href="https://github.com/trevorhuang1/cpt_warmup/commit/8bf1214933ef5cbe29572b1d4caa4a233b67532a">input-based js color generator</a>
- <a href="https://github.com/trevorhuang1/cpt_warmup/commit/a9aa10d3a696960b662604dc98f4ea624c7f5fe5">sample color input</a>

# Counting Sheep

<a href="https://trevorhuang1.github.io/cpt_warmup//2023/11/15/stegoDecoder.html">Link to project (click)</a><br>
<a href="https://github.com/trevorhuang1/cpt_warmup/blob/main/_posts/2023-11-15-stegoDecoder.md?plain=1">Link to code (click)</a>
- Key Points:
    * Changing color based on what the user inputs in binary
    * Creating interesting interaction by counting sheep which is also what changes color
- Improvements:
    * Sheep has white background
    * add in reindeer 
    * The sudden appearance of the sheep is jarring
    * Sheep Changing Form of Entering Binary -> Entering it rather than pressing on counter
    * The Sheep Counter -> Initial draft of the sheep counter
- <img src= "https://media.discordapp.net/attachments/770342230925246505/1180040866266624080/image.png?ex=657bf9b2&is=656984b2&hm=6ede918bd422f6fa4284e29b6ce15bad5bff7918f41d1f924c9a8b2bd49ce848&=&format=webp&quality=lossless&width=1253&height=662">

# Password Combiner:

<a href="https://trevorhuang1.github.io/cpt_warmup/2023/11/15/Logic_gates.html">Link to project (click)</a> <br>
<a href="https://github.com/trevorhuang1/cpt_warmup/blob/main/_posts/2023-11-15-Logic_gates.md?plain=1">Link to code (click)</a><br>
<img src="https://media.discordapp.net/attachments/1138198617463730330/1180049472210870322/combiner.png?ex=657c01b6&is=65698cb6&hm=6cad0ca8476ef7b55df49dbaf1449496f9482091759873e0acbe98a7ed97fecd&=&format=webp&quality=lossless">


Key Commits:
- <a href="https://github.com/trevorhuang1/cpt_warmup/commit/f96393709dc9e6e1c28a78b33005e64f71fac3ce">Text to binary (favorite)</a>

- <a href="https://github.com/trevorhuang1/cpt_warmup/commit/d87277d8532028dce3c7f84d44060ca2d960ed6b">Option to switch logic gate</a>

- <a href="https://github.com/trevorhuang1/cpt_warmup/commit/9cec1f72dad02c56725916f9b2b95586bec4a8cc">Binary back to text</a>

Key Points:
- Use of binary when the two passwords from the user go from ascii to unicode then to binary
- Logic gates combine the "0"s and "1"s and return one password in binary
- Convert back to ascii however it removes any unreadable characters (only 95 ascii characters are readable ones)

Possible Improvements:
- Add much more gates instead of just AND & OR gates
- Suggest a stronger password if the combined one is weak

<script src="https://utteranc.es/client.js"
        repo="trevorhuang1/cpt_warmup"
        issue-term="pathname"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>