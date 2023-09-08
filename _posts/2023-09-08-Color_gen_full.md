---
layout: none
title: Pair Plan Project
description: Color Harmony Generator Project
courses: { csa: {week: 2} }
type: hacks
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Color Harmony Generator</title>
</head>
<body>
    <main>
        <h1>Color Harmony Generator</h1>
        <input class="user-input" type="text" id="color-input" placeholder="Enter a color">
        <button class="generate-palette-button" id="generate-palette-button">Generate Palette</button>
        <h4>Generator</h4>
        <div class="colors">
            <div class="color">
                <button></button>
                <input type="text" class="color-input" value="#000000" />
                <button class="copy-hex">Copy</button>
            </div>
            <div class="color">
                <button></button>
                <input type="text" class="color-input" value="#000000" />
                <button class="copy-hex">Copy</button>
            </div>
            <div class="color">
                <button></button>
                <input type="text" class="color-input" value="#000000" />
                <button class="copy-hex">Copy</button>
            </div>
            <div class="color">
                <button></button>
                <input type="text" class="color-input" value="#000000" />
                <button class="copy-hex">Copy</button>
            </div>
        </div>
        <h1>Complementary Color Generator</h1>
        <input type="color" id="inputColor">
        <button id="generateComplementary">Generate Complementary</button>
        <div id="complementaryColor" style="width: 100px; height: 100px;"></div>
    </main>
</body>
</html>
<style>
    :root{
        --primary: #D81E5D;
        --secondary: #8A4FFF;
        --light: #eee;
        --dark: #1e2f42;
        --grey: #aaa
    }

    * {
        box-sizing:border-box;
        margin: 0;
        padding: 0;

        font-family: 'Fira Sans', sans-serif;
    }

    button, input{
        appearance: none;
        border: none;
        outline: none;
        background: none;
        color: inherit;
    }

    button {
        cursor: pointer;
    }

    body{
        background: var(--light);
    }

    main {
        padding: 4rem 2rem;
        max-width: 1200px;
        margin: 0 auto;
    }

    h1{
        color: var(--dark);
        font-size: 2.5rem;
        font-weight: 900;
        margin-bottom: 1rem;
        text-transform: uppercase;
        margin-top: 4rem;
    }

    h4{
        color: var(--grey);
        text-transform: uppercase;
        font-weight: 700;
        font-size: 1.5rem;
        margin-bottom: 1rem;
        margin-top: 3.5rem;
    }

    .colors{
        display: grid;
        grid-template-columns: repeat(1, 1fr);
        grid-gap: 1rem;
    }

    .color{
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 0.5rem 1rem;
        border-radius: 1rem;
        color: #fff;
        background-color: var(--dark);
        transition: 0.4s ease-out;
        border: 2px solid transparent;
    }

    .color.copied{
        border-color: red;
    }

    .color-input{
        text-align: center;
    }

    .generate-palette-button {
        background-color: var(--primary);
        color: #fff;
        font-size: 1rem;
        padding: 0.5rem 1rem;
        border: none;
        border-radius: 0.5rem;
        cursor: pointer;
        margin-top: 2rem;
        transition: background-color 0.3s ease, transform 0.2s ease;
    }

    .generate-palette-button:hover {
        background-color: var(--secondary);
        transform: scale(1.05);
    }

    .generate-palette-button:focus {
        outline: none;
        box-shadow: 0 0 0 2px var(--primary);
    }

    .user-input {
        width: 20%;
        padding: 0.5rem;
        font-size: 1rem;
        border: 2px solid var(--primary);
        border-radius: 0.5rem;
        outline: none;
        transition: border-color 0.3s ease;
    }

    .user-input::placeholder {
        color: var(--grey);
    }

    .user-input:focus {
        border-color: var(--secondary);
    }


    @media (min-width: 768px) {
        h1{
            font-size: 3.5rem;
        }
        .colors{
            grid-template-columns: repeat(2, 1fr);
        }
    }

     @media (min-width: 1024px) {
        .colors{
            grid-template-columns: repeat(4, 1fr);
        }
        .color{
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        .color-input{
            margin-top: 1rem;
            margin-bottom: 1rem;
        }
    }

</style>
<script>
    class Color {
        //class constructor
        constructor (hex, element) {
            this.hex = hex;
            this.element = element;
        }

        //sets the color of the element by changing its background color to the specified hex value. 
        setHex (hex) {
            this.hex = hex;
            this.element
                .style.backgroundColor = hex;

            this.element
                .querySelector('.color-input').value = hex;
        }

        //copies the color code associated with the element to the clipboard.
        copyToClipboard () {
            const input = this.element.querySelector('.color-input');
            input.select();
            document.execCommand('copy');
            input.blur();

            this.element.classList.add('copied');
            setTimeout(() => {
                this.element.classList.remove('copied');
            }, 1000);
        }
    }

    //database
    const colorPalettes = {
        red: ['#FF5733','#FF6B6B','#FF7F50','#FF4B3E','#A33B20','#E25822','#FF5400','#F40000','#F72C25','#92140C'],
        blue: ['#0074D9', '#4192D9', '#30AABC', '#8BCCCC','#0000FF','#6495ED','#4169E1','#1E90FF','#00BFFF','#87CEEB','#87CEFA','#ADD8E6','#B0E0E6','#4682B4','#111D4A','#009DDC'],
        green: [ '#228B22','#008000','#32CD32','#93C48B','#00FF00','#2E8B57','#00FF7F','#ADFF2F','#98FB98','#00FA9A','#B6D369','#898952','#009B72'],
        purple: ['#6761A8','#C455A8','#D1B1CB','#B2ABF2','#805E73','#4E4D5C','#390099','#9E0059','#4C1E4F','#564787','#A09BE7','#8D6B94','#B185A7','#7E52A0','#D295BF','#29274C'],
        yellow: ['#FFFF00','#FFFF99','#FFFF66','#FFD700','#FFDB58','#FFD801','#FFC300','#FFDF00','#F0E68C','#FFED4E','#FAC05E','#E3B505'],
        default: ['#000000', '#333333', '#666666', '#999999'],
    };

    document.getElementById('generate-palette-button').addEventListener('click', () => {
    const colorInput = document.getElementById('color-input').value.toLowerCase();
    const colorPalette = colorPalettes[colorInput] || colorPalettes.default;

    //from the data, randomly selects hexes
    for (let i = 0; i < colors.length; i++) {
        const randomIndex = Math.floor(Math.random() * colorPalette.length);
        colors[i].setHex(colorPalette[randomIndex]);
    }
    });

    //selects all the color elements in the UI and stores them 
    const color_elements = document.querySelectorAll('.colors .color' );
    const colors = [];

    //iterates through each color element in the UI and performs the actions
    for (let i = 0; i < color_elements.length; i++) {
        const color_element = color_elements[i];

        //creating variables with ids from html
        const input = color_element.querySelector('.color-input'); 
        const copy_hex = color_element.querySelector('.copy-hex');

        const hex = input.value;

        const color = new Color(hex, color_element);

        input.addEventListener('input', () => color.setHex(e.target.value));
        copy_hex.addEventListener('click', () => color.copyToClipboard());

        colors.push(color);
    }


</script>
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