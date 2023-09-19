---
comments: true
layout: post
title: Pair Plan Feedback
description: Feedback from Chat GPT and Peers
courses: { csa: {week: 2} }
type: plans
---

- Chat GPT feedback on code:
    - chat gpt noticed that its possible that when the code randomly chooses a color, repeat colors may occur so it wrote some code to ensure that each hex is unique.
    
```
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
```

- Peer Feedback
    - we talked with Sreeja and Tanisha about each others projects to give each other feedback
    - they told us to make our code a little more sophisticated. At first we only had the colors and the hex numbers show up but there was no way to easily get the color. So they suggested we make that aspect easier. So we added a function which allows the user to automatically copy the hex number when they click 'copy'

- Next steps
    - currently, we have a database of hexes that we access however we would like to make this process even more efficient. So we have found a color picked API which we will hook up and fetch. The only reason we didn't use it in the first place is because we were unsure on how to sort the color hexes in groups so all the reds, oranges, yellows etc. Same with the complimentary colors. 