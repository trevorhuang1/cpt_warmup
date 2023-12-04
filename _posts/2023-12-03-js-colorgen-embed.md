---
toc: false
comments: true
layout: base
title: Color Generator
description: Color Generator
courses: {compsci: {week: 1}}
type: tangibles
---

<html>
<head>
    <title>Color Generator</title>
</head>
<body>

- Validate RGB Values
- Convert RGB Decimal to Binary
- Have sample RGB value input (decimal)
- Display color in RGB format
- Displaying converted RGB values in binary

<img src = "https://media.discordapp.net/attachments/1174540464951676969/1174591418451369994/image.png?ex=65682681&is=6555b181&hm=10da97d668d2ce6c0e1dea11fd5e9fd743ab5dacc88778b282c5017d15aa1c79&=&width=1333&height=993">

- Instructions

Change the values (pictured below) in code, then use Console in "Toggle Developer Tools" to go through above process.

<img src="https://media.discordapp.net/attachments/796087225535168512/1181298244056260678/image.png?ex=65808cb8&is=656e17b8&hm=f385b456e57457b6ecccc9adc42052c06ecaa39d8e3cebaff363cd502b0ee56e&=&format=webp&quality=lossless&width=393&height=225">

- Key Commits

<a href="https://github.com/trevorhuang1/cpt_warmup/commit/9da25de7e4f114a33fdb5028e7b4d3d236659a6e">js color generator</a>

<a href="https://github.com/trevorhuang1/cpt_warmup/commit/2d1eac0c2044606f30e2e8d65da9342d9a673608">python binary colorgen</a>

<a href="https://github.com/trevorhuang1/cpt_warmup/commit/a9aa10d3a696960b662604dc98f4ea624c7f5fe5">sample color input</a>


    <script>
        // function to convert binary to hex color
        function binaryToHexColor(binary) {
            var decimalValue = parseInt(binary, 2);
            var hexValue = decimalValue.toString(16).toUpperCase();
            return '#' + '0'.repeat(6 - hexValue.length) + hexValue;
        }

        // display an input prompt and store the user's binary input
        var binaryInput = prompt("Enter a 24-bit binary value:");

        // checks if the input is a valid binary string (0 or 1 input for 24 characters)
        if (!/^[01]{24}$/.test(binaryInput)) {
            alert('Please enter a valid 24-bit binary value.');
        } else {
            // Convert binary input to hex color
            var hexColor = binaryToHexColor(binaryInput);

            // Display the user's input and the generated color
            var outputArea = this.element.parents('.cell').find('.output');
            var outputHTML = '<div style="color: ' + hexColor + ';">Binary Input: ' + binaryInput + '</div>';
            outputArea.append(outputHTML);
        }
    </script>

</body>
</html>