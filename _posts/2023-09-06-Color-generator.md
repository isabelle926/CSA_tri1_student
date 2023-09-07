---
toc: true
layout: none
title: Color Harmony Generator
description: Creates a color palette with complementary colors
type: tangibles
courses: { csa: {week: 2} }
categories: [C1.4]
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Complementary Color Generator</title>
</head>
<body>
    <h1>Complementary Color Generator</h1>
    <input type="color" id="inputColor">
    <button id="generateComplementary">Generate Complementary</button>
    <div id="complementaryColor" style="width: 100px; height: 100px;"></div>

    <script>
        const inputColor = document.getElementById('inputColor');
        const generateComplementary = document.getElementById('generateComplementary');
        const complementaryColor = document.getElementById('complementaryColor');

        generateComplementary.addEventListener('click', () => {
            const inputColorValue = inputColor.value;
            const complementaryColorValue = generateComplementaryColor(inputColorValue);
            complementaryColor.style.backgroundColor = complementaryColorValue;
        });

        function generateComplementaryColor(inputColorValue) {
            const hexColor = inputColorValue.slice(1); // Remove the '#' character
            const r = parseInt(hexColor.slice(0, 2), 16);
            const g = parseInt(hexColor.slice(2, 4), 16);
            const b = parseInt(hexColor.slice(4, 6), 16);

            const complementaryR = 255 - r;
            const complementaryG = 255 - g;
            const complementaryB = 255 - b;

            const complementaryHex = `#${complementaryR.toString(16).padStart(2, '0')}${complementaryG.toString(16).padStart(2, '0')}${complementaryB.toString(16).padStart(2, '0')}`;

            return complementaryHex;
        }
    </script>
</body>
</html>

