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
<a href="https://trevorhuang1.github.io/cpt_warmup//2023/11/14/stego.html">Stego Project Link</a>

```javascript
<script>
    // Function to encode a message into an image
    function encodeMessage() {
        // Get HTML elements
        const imageInput = document.getElementById('imageInput');
        const messageInput = document.getElementById('messageInput');
        const canvas = document.getElementById('canvas');
        const ctx = canvas.getContext('2d');

        // Create a new Image object and load the selected image
        const image = new Image();
        image.src = URL.createObjectURL(imageInput.files[0]);

        // Callback executed when the image is loaded
        image.onload = function () {
            // Set canvas dimensions to match the image
            canvas.width = image.width;
            canvas.height = image.height;

            // Draw the image onto the canvas
            ctx.drawImage(image, 0, 0);

            // Get the message from the input and convert it to binary
            const message = messageInput.value;
            const binaryMessage = stringToBinary(message);

            let binaryIndex = 0;

            // Loop through each pixel of the image
            for (let y = 0; y < image.height; y++) {
                for (let x = 0; x < image.width; x++) {
                    // Get the RGBA data of the current pixel
                    const pixel = ctx.getImageData(x, y, 1, 1);
                    const rgba = pixel.data;

                    // Loop through RGB components (ignoring alpha)
                    for (let i = 0; i < 3; i++) {
                        if (binaryIndex < binaryMessage.length) {
                            // Set the least significant bit of each RGB component to the message bit
                            rgba[i] = (rgba[i] & 0xFE) | parseInt(binaryMessage[binaryIndex], 2);
                            binaryIndex++;
                        }
                    }

                    // Update the pixel data on the canvas
                    ctx.putImageData(new ImageData(new Uint8ClampedArray(rgba), 1, 1), x, y);
                }
            }
            // Store the length of the binary message for decoding
            window.binaryMessageLength = binaryMessage.length;
        };
    }

    // Function to decode a message from an encoded image
    function decodeMessage() {
        // Get HTML elements
        const encodedImageInput = document.getElementById('encodedImageInput');
        const decodedMessageTextarea = document.getElementById('decodedMessage');
        const canvas = document.getElementById('canvas');
        const ctx = canvas.getContext('2d');

        // Create a new Image object and load the encoded image
        const encodedImage = new Image();
        encodedImage.src = URL.createObjectURL(encodedImageInput.files[0]);

        // Callback executed when the encoded image is loaded
        encodedImage.onload = function () {
            // Set canvas dimensions to match the encoded image
            canvas.width = encodedImage.width;
            canvas.height = encodedImage.height;

            // Draw the encoded image onto the canvas
            ctx.drawImage(encodedImage, 0, 0);

            let binaryMessage = '';
            // Loop through each pixel of the encoded image
            for (let y = 0; y < encodedImage.height; y++) {
                for (let x = 0; x < encodedImage.width; x++) {
                    // Get the RGBA data of the current pixel
                    const pixel = ctx.getImageData(x, y, 1, 1).data;
                    if (binaryMessage.length < binaryMessageLength) {
                        // Loop through RGB components (ignoring alpha)
                        for (let i = 0; i < 3; i++) {
                            // Extract the least significant bit from each RGB component
                            binaryMessage += (pixel[i] & 1).toString();
                        }
                    }
                }
            }

            // Convert the binary message to a human-readable string
            const message = binaryToString(binaryMessage);
            // Display the decoded message in the textarea
            decodedMessageTextarea.value = message;
        };
    }

    // Function to convert a string to binary
    function stringToBinary(str) {
        const binary = [];
        for (let i = 0; i < str.length; i++) {
            // Convert each character to its binary representation
            const charCode = str.charCodeAt(i).toString(2);
            // Ensure each binary representation is 8 bits long
            binary.push('0'.repeat(8 - charCode.length) + charCode);
        }
        return binary.join('');
    }

    // Function to convert binary to a string
    function binaryToString(binary) {
        let str = '';
        for (let i = 0; i < binary.length; i += 8) {
            // Convert each 8 bits to a character and concatenate
            const byte = binary.substr(i, 8);
            str += String.fromCharCode(parseInt(byte, 2));
        }
        return str;
    }
</script>
```

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

```javascript

//Style for black canvas
<style>
   #asciiOutput {
    background-color: black;
    color: white;
   }
</style>

<!-- Input element for selecting an image file -->
<input type="file" id="imageInput" accept="image/*">

<!-- Placeholder for displaying the ASCII art -->
<pre id="asciiOutput"></pre>

<script>

    // Event listener for changes in the selected image file
    document.getElementById('imageInput').addEventListener('change', handleImage);

    // Function to handle the selected image file
    function handleImage() {
        const input = document.getElementById('imageInput');
        const output = document.getElementById('asciiOutput');

        // Create an Image object
        const img = new Image();

        // Event handler when the image is loaded
        img.onload = function() {
            // Generate ASCII art from the image
            const asciiArt = imageToAscii(img);

            // Display ASCII art in the output element
            output.innerHTML = asciiArt;
        };

        // Read the selected file as a data URL and set it as the source of the Image object
        const file = input.files[0];
        const reader = new FileReader();
        reader.onload = function(e) {
            img.src = e.target.result;
        };

        reader.readAsDataURL(file);
    }

    // Function to generate ASCII art from the image
    function imageToAscii(img) {
        // Create a temporary canvas and get its 2D rendering context
        const canvas = document.createElement('canvas');
        const ctx = canvas.getContext('2d');

        // Define the width for the ASCII output
        const outputWidth = 100;

        // Calculate the new width and height based on the original image dimensions
        const aspectRatio = img.width / img.height;
        const newWidth = Math.min(outputWidth, img.width);
        const newHeight = Math.floor(newWidth / aspectRatio);

        // Set the canvas dimensions
        canvas.width = newWidth;
        canvas.height = newHeight;

        // Draw the resized image on the canvas
        ctx.drawImage(img, 0, 0, newWidth, newHeight);

        // Get the pixel data from the canvas
        const imageData = ctx.getImageData(0, 0, newWidth, newHeight).data;

        // Initialize the string for storing ASCII art
        let asciiArt = '';

        // Process each pixel in the image
        for (let i = 0; i < imageData.length; i += 4) {
            // Convert RGB values to binary
            const binaryR = imageData[i].toString(2).padStart(8, '0');
            const binaryG = imageData[i + 1].toString(2).padStart(8, '0');
            const binaryB = imageData[i + 2].toString(2).padStart(8, '0');

            // Combine binary values to form a single binary string
            const binaryValue = binaryR + binaryG + binaryB;

            // Use specific criteria to determine background or foreground
            const char = isForeground(binaryValue) ? '*' : ' ';

            // Append the character to the ASCII art string
            asciiArt += char;

            // Add a line break at the end of each row
            if ((i / 4 + 1) % newWidth === 0) {
                asciiArt += '\n';
            }
        }

        // Return the generated ASCII art
        return asciiArt;
    }

    // Function to determine foreground based on binary value
    function isForeground(binaryValue) {
        // Add your criteria for determining foreground
        // For example, you can check if the binary value starts with '1'
        return binaryValue.startsWith('1');
    }
</script>

```

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

# Counting Sheep
- Key Points:
    * Changing color based on what the user inputs in binary
    * Creating interesting interaction by counting sheep which is also what changes color
- Improvements:
    * Sheep has white background
    * The sudden appearance of the sheep is jarring
    * Sheep Changing Form of Entering Binary -> Entering it rather than pressing on counter
    * The Sheep Counter -> Initial draft of the sheep counter
- <img src= "https://media.discordapp.net/attachments/770342230925246505/1180040866266624080/image.png?ex=657bf9b2&is=656984b2&hm=6ede918bd422f6fa4284e29b6ce15bad5bff7918f41d1f924c9a8b2bd49ce848&=&format=webp&quality=lossless&width=1253&height=662">

# Password Combiner:
<img src="https://media.discordapp.net/attachments/1138198617463730330/1180049472210870322/combiner.png?ex=657c01b6&is=65698cb6&hm=6cad0ca8476ef7b55df49dbaf1449496f9482091759873e0acbe98a7ed97fecd&=&format=webp&quality=lossless">

<a href="https://trevorhuang1.github.io/cpt_warmup/2023/11/15/Logic_gates.html">Link to project (click)</a>

Key Commits:
- <a href="https://github.com/trevorhuang1/cpt_warmup/commit/f96393709dc9e6e1c28a78b33005e64f71fac3ce">Text to binary (favorite)</a>

- <a href="https://github.com/trevorhuang1/cpt_warmup/commit/d87277d8532028dce3c7f84d44060ca2d960ed6b">Option to switch logic gate</a>

- <a href="https://github.com/trevorhuang1/cpt_warmup/commit/9cec1f72dad02c56725916f9b2b95586bec4a8cc">Binary back to text</a>

Key Points:
- Use of binary when the two passwords from the user go from ascii to unicode then to binary
- Logic gates combine the "0"s and "1"s and return one password in binary

Possible Improvements:
- Add much more gates instead of just AND & OR gates
- Suggest a stronger password if the combined one is weak


