---
layouts: base
title: Sheep Counter
comments: true
description: Counts sheep
type: hacks
courses: { compsci: {week: 1} }
---
<style>
    #sheepGif {
        position: absolute;
        padding-left: 10px;
        left: 0;
        padding-top: 40px;
    }
    #sheep{
        opacity: 1;
    }
</style>

<h1>Binary Counter</h1>

<img src="https://media.discordapp.net/attachments/770342230925246505/1174716992951947316/godSheep.png?ex=65689b74&is=65562674&hm=f3219060d1c61a42c93316bee9865c3fe109fb1b0340ed08c801e21b0d232f37&=&width=375&height=378" id="sheep">
<div id="sheepContainer">
    <img src = "https://media.discordapp.net/attachments/770342230925246505/1174717359647367168/sheep.gif?ex=65689bcb&is=655626cb&hm=578b09c94ccca31eddeffa7660f277a1ef462768d291886358930ba87a4866d0&=&width=300&height=300" id="sheepGif">
</div>
<div id="binary-display" class="basicChex">Binary Value: 0</div>
<div id="binary-display2" class="basicChex">2nd Binary Value: 0</div>
<div id="binary-display3" class="basicChex">3rd Binary Value: 0</div>
<div id="numSheep" class="basicChex">Number of Sheep Counted: 0</div>

<button id="increment-button" onclick="incrementBinary()">Counter 1</button>
<button id="increment-button2" onclick="incrementBinary2()">Counter 2</button>
<button id="increment-button3" onclick="incrementBinary3()">Counter 3</button>

<script>
    let binaryValue = 0;
    let binaryValue2 = 0;
    let binaryValue3 = 0;
    let numSheep = 0;
    function incrementBinary() {
        binaryValue++;
        numSheep++;
        updateBinaryDisplay();
    }
    function incrementBinary2() {
        binaryValue2++;
        numSheep++;
        updateBinaryDisplay();
    }
    function incrementBinary3() {
        binaryValue3++;
        numSheep++;
        updateBinaryDisplay();
    }
    let sheep = document.getElementById("sheep");
    function toggleSheepDisplay() {
        if (sheep.style.opacity === '0'){
            sheep.style.opacity = '1';
        }
        else {
            sheep.style.opacity = '0';
        }
    }
    setInterval(toggleSheepDisplay,2000);
    function updateBinaryDisplay() {
        document.getElementById('binary-display').innerText = `Binary Value: ${(binaryValue & 0xFF).toString(2).padStart(8, '0')}`;
        document.getElementById('binary-display2').innerText = `2nd Binary Value: ${(binaryValue2 & 0xFF).toString(2).padStart(8, '0')}`;
        document.getElementById('binary-display3').innerText = `3rd Binary Value: ${(binaryValue3 & 0xFF).toString(2).padStart(8, '0')}`;

        document.getElementById('numSheep').innerText = `Number of Sheep Counted: ${numSheep}`
        let red = parseInt(binaryValue.toString(2),2);
        let green = parseInt(binaryValue2.toString(2),2);
        let blue = parseInt(binaryValue3.toString(2),2);
        sheep.style.backgroundColor = `rgb(${red},${green},${blue})`
    }
</script>