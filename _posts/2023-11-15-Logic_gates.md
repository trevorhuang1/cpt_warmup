---
title: Password Combiner
comments: true
description: Combines two passwords into one with logic gates
type: hacks
courses: { compsci: {week: 1} }
---
<!-- Setting up the form for data entry -->
<form onsubmit="combinePasswords(event)">
    <label for="password1">Enter your first password</label><br>
    <input type="text" id="password1" name="password1"><br>
    <label for="password2">Enter your second password</label><br>
    <input type="text" id="password2" name="password2"><br>
    <input type="radio" id="and" name="gate" value="and">
    <label for="and">And Gate</label><br>
    <img src="https://media.discordapp.net/attachments/1138198617463730330/1181468296747429999/AND.webp?ex=65812b18&is=656eb618&hm=6d0583021058c70d1864ffdcdfb6ca25ba957fa269f64532f7b8b1d10ddc04f3&=&format=webp" alt="AND Gate" width="400" height="200"><br>
    <input type="radio" id="or" name="gate" value="or"><br>
    <label for="or">Or Gate</label><br>
    <img src="https://media.discordapp.net/attachments/1138198617463730330/1181468333263044680/OR.webp?ex=65812b21&is=656eb621&hm=98f9ec24a67731715b3a0126dda747165b4481f8c8013fedbedf55f531963ffd&=&format=webp" alt="OR Gate" width="400" height="200">
    <input type="submit" value="Submit">
</form>
<h2 id="combined"></h2>

<script>
    function combinePasswords(event) {
        // Prevents from refreshing which would refresh the display for combined password
        event.preventDefault();
        //getting elements
        var password1= document.getElementById("password1").value;
        var password2 = document.getElementById("password2").value;
        var gateType = document.querySelector('input[name="gate"]:checked').value;
        // turns into binary using function
        var binary1 = textToBinary(password1);
        var binary2 = textToBinary(password2);
        //combines with and gate
        if (gateType == "and") {
            var combined = andGate(binary1, binary2);
        }
        else if (gateType == "or") {
            var combined = orGate(binary1, binary2);
        }
        console.log(binary1);
        console.log(binary2);
        // displays
        document.getElementById("combined").innerHTML = "Combined password: " + binaryToText(combined);
    }

    //https://stackoverflow.com/questions/14430633/how-to-convert-text-to-binary-code-in-javascript
    function textToBinary(text) {
        var binary = ""; 
        // for every character in the text
        for (var i = 0; i < text.length; i++) {
            var charBinary = "";
            // concat the binary version into the var "binary"
            //charCodeAt(0) retrieves the unicode character code of the character at i
            //.toString(2) converts unicode to binary
            charBinary += text[i].charCodeAt(0).toString(2);

            // pad with leading zeros
            while (charBinary.length < 8) {
                charBinary = "0" + charBinary;
            }

            // concat and adding necessary space
            binary += charBinary;
        }
        return binary.trim();
    }

    function binaryToText(binary) {
        var text = "";
        // Split the binary string into 8-bit chunks
        var binaryChunks = binary.match(/.{1,8}/g);

        // Convert each 8-bit chunk to decimal and then to ASCII
        for (var i = 0; i < binaryChunks.length; i++) {
            var decimalValue = parseInt(binaryChunks[i], 2);

            // Check if the ASCII character is printable
            if (decimalValue >= 32 && decimalValue <= 126) {
                text += String.fromCharCode(decimalValue);
            }
        }

        return text;
    }

    function andGate(binary1, binary2) {
        var result = "";
        var shorter = 0;
        // takes the longer one
        if (binary1.length >= binary2) {
            shorter = binary2;
        }
        else{
            shorter = binary1;
        }
        for (var i = 0; i < shorter.length; i++) {
            //if both 1 then return 1
            if(binary1[i] == "1" && binary2[i] == "1") {
                result += "1";
            }
            //otherwise return 0
            else{
                result += "0";
            }
        }
        return result;
    }
    function orGate(binary1, binary2) {
        var result = "";
        var shorter = 0;
        // takes the longer one
        if (binary1.length >= binary2) {
            shorter = binary2;
        }
        else{
            shorter = binary1;
        }
        for (var i = 0; i < shorter.length; i++) {
            //if both 1 then return 1
            if(binary1[i] == "1" || binary2[i] == "1") {
                result += "1";
            }
            //otherwise return 0
            else{
                result += "0";
            }
        }
        return result;
    }

</script>