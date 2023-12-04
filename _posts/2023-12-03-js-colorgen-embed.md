---
toc: false
comments: true
layout: base
title: Color Translator
description: Color Generator
courses: {compsci: {week: 1}}
type: hacks
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


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Color Mixer</title>
    <style>
        #result {
            margin-top: 20px;
            width: 200px;
            height: 200px;
            border: 1px solid #000;
        }
    </style>
    <script>
        function translateColor(event) {
            event.preventDefault();
            // get input values
            var redValue = document.getElementById("redValue").value;
            var greenValue = document.getElementById("greenValue").value;
            var blueValue = document.getElementById("blueValue").value;
            // validate input values (must be between 0 and 255)
            if (!isValidInput(redValue) || !isValidInput(greenValue) || !isValidInput(blueValue)) {
                alert("Please enter valid numbers between 0 and 255.");
                return;
            }
            // convert inputs to binary
            var redBinary = decimalToBinary(redValue);
            var greenBinary = decimalToBinary(greenValue);
            var blueBinary = decimalToBinary(blueValue);
            // display binary output
            document.getElementById("result").innerHTML = `
                <p>Red: ${redBinary}</p>
                <p>Green: ${greenBinary}</p>
                <p>Blue: ${blueBinary}</p>
            `;
            // calculate the final color
            var finalColor = "rgb(" + redValue + "," + greenValue + "," + blueValue + ")";
            // display the final color
            document.getElementById("result").style.backgroundColor = finalColor;
        }
        function decimalToBinary(decimalValue) {
            return parseInt(decimalValue).toString(2);
        }
        function isValidInput(value) {
            return !isNaN(value) && parseInt(value) >= 0 && parseInt(value) <= 255;
        }
    </script>
</head>
<body>
    <form onsubmit="translateColor(event)">
        <label for="redValue">Number 0-255 for Red</label><br>
        <input type="number" id="redValue" name="redValue" required><br>
        <label for="greenValue">Number 0-255 for Green</label><br>
        <input type="number" id="greenValue" name="greenValue" required><br>
        <label for="blueValue">Number 0-255 for Blue</label><br>
        <input type="number" id="blueValue" name="blueValue" required><br>
        <input type="submit" value="Submit">
    </form>
    <div id="result"></div>

</body>
</html>

    - Key Commits


<a href="https://github.com/trevorhuang1/cpt_warmup/commit/9da25de7e4f114a33fdb5028e7b4d3d236659a6e">js color generator</a>


<a href="https://github.com/trevorhuang1/cpt_warmup/commit/2d1eac0c2044606f30e2e8d65da9342d9a673608">python binary colorgen</a>


<a href="https://github.com/trevorhuang1/cpt_warmup/commit/a9aa10d3a696960b662604dc98f4ea624c7f5fe5">sample color input</a>

</body>
</html>