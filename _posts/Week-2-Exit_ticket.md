---
comments: true
layout: post
title: Week 2 Tangibles
description: Exit ticket for week 2 hacks
courses: { csa: {week: 2} }
type: tangibles
---
# Week 2 Exit Ticket
Pair Plan Project
- [Link](https://github.com/nighthawkcoders/student/issues/33) to Pair Plan Project
- [Link](https://github.com/vivianknee/FastPages/issues/49#issue-1881165198) to Pair Plan (Due Monday)
- focus on input output
- focus on data, and utilizing it
- mainly working on html, css, and js
- learn how to make aesthetic UI
- Chat GPT feedback on code:
    - chat gpt noticed that its possible that when the code randomly chooses a color, repeat colors may occur so it wrote some code to ensure that each hex is unique.
<script>
    document.getElementById('generate-palette-button').addEventListener('click', () => {
    const colorInput = document.getElementById('color-input').value.toLowerCase();
    const colorPalette = colorPalettes[colorInput] || colorPalettes.default;
    // Shuffle the colorPalette array to randomize the colors
    const shuffledPalette = shuffleArray(colorPalette);
    // Apply the shuffled colors to the UI elements
    for (let i = 0; i < colors.length; i++) {
        colors[i].setHex(shuffledPalette[i % shuffledPalette.length]);
    }
    });
    // Function to shuffle an array
    function shuffleArray(array) {
        const newArray = [...array];
        for (let i = newArray.length - 1; i > 0; i--) {
            const j = Math.floor(Math.random() * (i + 1));
            [newArray[i], newArray[j]] = [newArray[j], newArray[i]];
        }
        return newArray;
    }
</script>
Java output w/jquery hacks
- [Link](https://isabelle926.github.io/student//c3.0/c3.1/c4.1/2023/09/06/javascript-output-jquery_IPYNB_2_.html) to hacks
- Make your own tables, with data according to your interests.
- Describe a benefit of a markdown table.
- Try to Style the HTML table using w3schools.
- Describe the difference between HTML and JavaScript.
- Describe a benefit of a table that uses JavaScript.
JS Games Hacks
[Link](https://vivianknee.github.io/VivianCSA//2023/09/06/jsGamesHacks.html) to hacks
- improvements to JS Itunes API, JS calculator, JS Game of life