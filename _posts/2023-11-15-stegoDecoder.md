---
layouts: base
title: Sheep Counter
comments: true
description: Counts sheep
type: hacks
courses: { compsci: {week: 1} }
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        #sheep {
            opacity: 1;
            position: absolute;
            z-index: -1;
        }
    </style>
    <title>Binary Counter</title>
</head>
<body>


<img src="https://media.discordapp.net/attachments/770342230925246505/1174716992951947316/godSheep.png?ex=65689b74&is=65562674&hm=f3219060d1c61a42c93316bee9865c3fe109fb1b0340ed08c801e21b0d232f37&=&width=375&height=378" id="sheep">
<!-- <div id="sheepContainer">
    <img src="https://media.discordapp.net/attachments/770342230925246505/1174717359647367168/sheep.gif?ex=65689bcb&is=655626cb&hm=578b09c94ccca31eddeffa7660f277a1ef462768d291886358930ba87a4866d0&=&width=300&height=300" id="sheepGif">
</div> -->
<div id="binary-display" class="basicChex">Binary Value: 0</div>
<div id="binary-display2" class="basicChex">2nd Binary Value: 0</div>
<div id="binary-display3" class="basicChex">3rd Binary Value: 0</div>
<div id="numSheep" class="basicChex">Number of Sheep Counted: 0</div>

<input type="text" id="binary-input" placeholder="Enter Binary Value">
<button id="increment-button" onclick="incrementBinary()">Counter 1</button>

<input type="text" id="binary-input2" placeholder="Enter Binary Value">
<button id="increment-button2" onclick="incrementBinary2()">Counter 2</button>

<input type="text" id="binary-input3" placeholder="Enter Binary Value">
<button id="increment-button3" onclick="incrementBinary3()">Counter 3</button>

<script>
    let binaryValue = 0;
    let binaryValue2 = 0;
    let binaryValue3 = 0;
    let numSheep = 0;

    function incrementBinary() {
        const input = document.getElementById("binary-input").value;
        binaryValue += parseInt(input, 2) || 0;
        numSheep++;
        updateBinaryDisplay();
    }

    function incrementBinary2() {
        const input = document.getElementById("binary-input2").value;
        binaryValue2 += parseInt(input, 2) || 0;
        numSheep++;
        updateBinaryDisplay();
    }

    function incrementBinary3() {
        const input = document.getElementById("binary-input3").value;
        binaryValue3 += parseInt(input, 2) || 0;
        numSheep++;
        updateBinaryDisplay();
    }

    let sheep = document.getElementById("sheep");

    function toggleSheepDisplay() {
        // Random position for the sheep
        const randomLeft = Math.floor(Math.random() * (window.innerWidth - sheep.width));
        const randomTop = Math.floor(Math.random() * (window.innerHeight - sheep.height));

        // Apply the random position
        sheep.style.left = `${randomLeft}px`;
        sheep.style.top = `${randomTop}px`;

        // Show the sheep
        sheep.style.opacity = '1';
    }

    setInterval(toggleSheepDisplay, 2000);

    function updateBinaryDisplay() {
        document.getElementById('binary-display').innerText = `Binary Value: ${(binaryValue & 0xFF).toString(2).padStart(8, '0')}`;
        document.getElementById('binary-display2').innerText = `2nd Binary Value: ${(binaryValue2 & 0xFF).toString(2).padStart(8, '0')}`;
        document.getElementById('binary-display3').innerText = `3rd Binary Value: ${(binaryValue3 & 0xFF).toString(2).padStart(8, '0')}`;

        document.getElementById('numSheep').innerText = `Number of Sheep Counted: ${numSheep}`;
        let red = parseInt(binaryValue.toString(2), 2);
        let green = parseInt(binaryValue2.toString(2), 2);
        let blue = parseInt(binaryValue3.toString(2), 2);
        sheep.style.backgroundColor = `rgb(${red},${green},${blue})`;
    }
</script>

</body>
</html>
