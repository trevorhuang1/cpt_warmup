---
toc: true
comments: false
layout: base
title: Stego Things
description: This is for stego things
type: plans
courses: { compsci: {week: 1} }
---

# Stego things:

<input type="file" id="uploadInput" accept="image/*">
<img id="output" alt="Uploaded Image">
<script>
    document.getElementById('uploadInput').addEventListener('change', function (e) {
        var file = e.target.files[0];
        if (file) {
            var reader = new FileReader();
            reader.onload = function (e) {
                var base64String = e.target.result.split(',')[1];
                var binaryString = atob(base64String);
                console.log(binaryString); // This will log the binary string to the console
            };
            reader.readAsDataURL(file);
        }
    });
</script>
