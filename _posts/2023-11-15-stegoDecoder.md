---
layouts: base
title: Sheep Counter
comments: false
type: tangibles
permalink: /binarycpt/counting-sheep
courses: { compsci: {week: 1} }
---

{% include binarycpt.html %}

<div class="snow_wrap">
    <div class="snow"></div>
</div>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        #sheep {
            opacity: 1;
            /* position: absolute; */
            animation: sheepWalk 5s linear infinite;
            z-index: -1;
        }
        #red {
            color: red;
        }
        #green{
            color: green;
        }
        #blue{
            color: blue;
        }
        #soundBox{
            font-size: 20px;
            color: #fff;
        }
    </style>
    <title>Binary Counter</title>
</head>
<body>


<img src="https://media.discordapp.net/attachments/770342230925246505/1174716992951947316/godSheep.png?ex=65689b74&is=65562674&hm=f3219060d1c61a42c93316bee9865c3fe109fb1b0340ed08c801e21b0d232f37&=&width=375&height=378" id="sheep">

<div id="soundBox"></div>
<button onclick="randomRGB()">Generate Random Color</button>
<div id="binary-display" class="basicChex">Binary Value: 0</div>
<div id="binary-display2" class="basicChex">2nd Binary Value: 0</div>
<div id="binary-display3" class="basicChex">3rd Binary Value: 0</div>
<div id="numSheep" class="basicChex">Number of Sheep Counted: 0</div>

<div id="red">(R)</div>
<input type="text" id="binary-input" placeholder="Enter Binary Value" maxlength=8>

<div class="ButtonContainer">
<button id="increment-button" onclick="incrementBinary()">Confirm</button>
<button id="Add" onclick="add1()">+10</button>
</div>

<div id="green">(G)</div>
<input type="text" id="binary-input2" placeholder="Enter Binary Value" maxlength=8>

<div class="ButtonContainer">
<button id="increment-button2" onclick="incrementBinary2()">Confirm</button>
<button id="Add2" onclick="add2()">+10</button>
</div>

<div id="blue">(B)</div>
<input type="text" id="binary-input3" placeholder="Enter Binary Value" maxlength=8>

<div class="ButtonContainer">
<button id="increment-button3" onclick="incrementBinary3()">Confirm</button>
<button id="Add3" onclick="add3()">+10</button>
</div>
<script>
    let soundEffectCounter = 0;
    let sounds = ["Baaaah","Moo", "Chirp", "Bark", "Meow", "make sure to enter an 8 bit value into color channel", "Keep Counting", "I'm so tired", "My mental health is declining", "SAVE ME", "PLEAse!", "WHY AM I STUCK IN THIS WEBSITe", "AAhhh...."];
    window.onload = function(){
        setTimeout(alert("Mooo. Did you know that colors come in a total of 24 bits(binary value) to represent a color?"),2000);
        setTimeout(alert("Moo. Anyways, I'm tired of being a transparent sheep. Try and play around with those bits!"),3000);
        setTimeout(alert("Cluck Cluck. Remember, you can only enter 8 bits per color channel :)"),3000);
    };
    function getRandomSound() {
        return sounds[soundEffectCounter];
    }
//
    function displayRandomSound() {
        soundEffectCounter++
        if (soundEffectCounter === sounds.length){
            soundEffectCounter = 0;
        }
        var soundBox = document.getElementById("soundBox");
        var randomSound = getRandomSound();
        soundBox.textContent = `The Sheep Says: ${randomSound}`;
    }
//
    // Update the sound every 2 seconds
    setInterval(displayRandomSound, 2000);
    let binaryValue = 0;
    let binaryValue2 = 0;
    let binaryValue3 = 0;
    let numSheep = 0;
    function add1() {
        binaryValue += 10;
        numSheep++
        document.getElementById("binary-input").placeholder = `${(binaryValue & 0xFF).toString(2).padStart(8, '0')}`;
        updateBinaryDisplay();
    }
    function add2(){
        binaryValue2 += 10;
        numSheep++
        document.getElementById("binary-input2").placeholder = `${(binaryValue2 & 0xFF).toString(2).padStart(8, '0')}`;
        updateBinaryDisplay();
    }
    function add3(){
        binaryValue3 += 10;
        numSheep++
        document.getElementById("binary-input3").placeholder = `${(binaryValue3 & 0xFF).toString(2).padStart(8, '0')}`;
        updateBinaryDisplay();
    }
//
    function randomRGB() {
        var red = Math.random()*(255-1) + 1;
        var green = Math.random()*(255-1) + 1;
        var blue = Math.random()*(255-1) + 1;
        numSheep ++;
        binaryValue = red;
        binaryValue2 = green;
        binaryValue3 = blue;
//
        document.getElementById("binary-input").placeholder = `${(binaryValue & 0xFF).toString(2).padStart(8, '0')}`;
        document.getElementById("binary-input2").placeholder = `${(binaryValue2 & 0xFF).toString(2).padStart(8, '0')}`;
        document.getElementById("binary-input3").placeholder = `${(binaryValue3 & 0xFF).toString(2).padStart(8, '0')}`;
        updateBinaryDisplay();
    }
//
    function incrementBinary() {
        const input = document.getElementById("binary-input").value;
        binaryValue += parseInt(input, 2) || 0;
        numSheep++;
        updateBinaryDisplay();
    }
//
    function incrementBinary2() {
        const input = document.getElementById("binary-input2").value;
        binaryValue2 += parseInt(input, 2) || 0;
        numSheep++;
        updateBinaryDisplay();
    }
//
    function incrementBinary3() {
        const input = document.getElementById("binary-input3").value;
        binaryValue3 += parseInt(input, 2) || 0;
        numSheep++;
        updateBinaryDisplay();
    }
//
    let sheep = document.getElementById("sheep");
//
    //function toggleSheepDisplay() {
        // Random position for the sheep
        //const randomLeft = Math.floor(Math.random() * (window.innerWidth - sheep.width));
        //const randomTop = Math.floor(Math.random() * (window.innerHeight - sheep.height));
//
        // Apply the random position
        //sheep.style.left = `${randomLeft}px`;
        //sheep.style.top = `${randomTop}px`;
//
        // Show the sheep
        //sheep.style.opacity = '1';
    //}
//
    //setInterval(toggleSheepDisplay, 2000);
//
    function updateBinaryDisplay() {
        document.getElementById('binary-display').innerText = `Binary Value: ${(binaryValue & 0xFF).toString(2).padStart(8, '0')}`;
        document.getElementById('binary-display2').innerText = `2nd Binary Value: ${(binaryValue2 & 0xFF).toString(2).padStart(8, '0')}`;
        document.getElementById('binary-display3').innerText = `3rd Binary Value: ${(binaryValue3 & 0xFF).toString(2).padStart(8, '0')}`;
//
        document.getElementById('numSheep').innerText = `Number of Sheep Counted: ${numSheep}`;
        let red = parseInt(binaryValue.toString(2), 2);
        let green = parseInt(binaryValue2.toString(2), 2);
        let blue = parseInt(binaryValue3.toString(2), 2);
        sheep.style.backgroundColor = `rgb(${red},${green},${blue})`;
    }
</script>

</body>
</html>
