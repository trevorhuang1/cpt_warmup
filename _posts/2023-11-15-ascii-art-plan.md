---
toc: true
comments: false
layout: base
title: Aditya's Plans - Ascii Art 
description: Ascii Art Binary Program Code and Updates
type: plans 
courses: { compsci: {week: 1} }
---

# Code for my Feature

```javascript

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
        const newWidth = 100;

        // Calculate the new height while maintaining the aspect ratio
        const aspectRatio = img.height / img.width;
        const newHeight = Math.floor(newWidth * aspectRatio);

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
            // Calculate the grayscale value of the pixel
            const pixelValue = (imageData[i] + imageData[i + 1] + imageData[i + 2]) / 3;

            // Map the grayscale value to a character based on a threshold
            const char = pixelValue < 128 ? ' ' : '*';

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
