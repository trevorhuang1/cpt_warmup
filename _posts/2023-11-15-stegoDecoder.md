---
layouts: base
title: Sheep Counter
comments: true
description: Counts sheep
type: hacks
courses: { compsci: {week: 1} }
---

<h1>Binary Counter</h1>

<img src="https://media.discordapp.net/attachments/1174600696776110080/1174600772340699216/encodedSheep.png?ex=65682f37&is=6555ba37&hm=797bf89aac0eeb10eae3245e7117b93f8adc526026edb734c35d3922dfd20de4&=&width=883&height=662" id="sheep">

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