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
    <input type="submit" value="Submit">
</form>
<p id="combined"></p>

<script>
    function combinePasswords(event) {
        // Prevents from refreshing which would refresh the display for combined password
        event.preventDefault();
        //getting elements
        var password1= document.getElementById("password1").value;
        var password2 = document.getElementById("password2").value;
        // turns into binary using function
        var binary1 = textToBinary(password1);
        var binary2 = textToBinary(password2);
        //combines with and gate
        var combined = andGate(binary1, binary2);
        console.log(binary1);
        console.log(binary2);
        // displays
        document.getElementById("combined").innerHTML = "Combined password: " + combined;
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
            charBinary += text[i].charCodeAt(0).toString(2) + " ";

            // pad with leading zeros
            while (charBinary.length < 9) {
                charBinary = "0" + charBinary;
            }

            // concat and adding necessary space
            binary += charBinary;
        }
        return binary.trim();
    }
    function andGate(binary1, binary2) {
        var result = "";
        var longer = 0;
        // takes the longer one
        if (binary1.length >= binary2) {
            longer = binary1;
        }
        else{
            longer = binary2;
        }
        for (var i = 0; i < longer.length; i++) {
            //if both 1 then return 1
            if(binary1[i] == 1 && binary2[i] == 1) {
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