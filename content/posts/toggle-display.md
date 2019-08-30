---
title: How to Show/Hide Elements
date: 2019-09-17
published: false
tags: ['coding']
series: false
canonical_url: false
description: "Here's a simple snippet that shows you how to toggle a display with the click of a button."
---

A friend of mine wanted to know how to simply display text with the click of a button.

And then hide that text when clicking the button again. Simple enough, right?

![Piece of Cake](https://media.giphy.com/media/Vh3eSXqetgyQTt0elB/giphy.gif)

Let's get down to business!

```html
<button onclick="toggleDisplay('text')">Toggle</button>
<p id="text">Hello World!</p>
```

Taking a simple HTML template, I'm following the following procedure:

1. Upon click, DOM select the text element in question.
2. Run a function to check if the display is set to `"block"` or `"none"` and set it to the opposite.
3. Profit.

What would the Javascript look like?

```javascript
/**
 * Generic function to do #1 and #2
 */
function toggleDisplay(id) {
    const el = document.getElementById(id);

    if (el.style.display === "block") {
        el.style.display = "none";
    } else {
        el.style.display = "block";
    }
}
```

If need be, you can replace the if/else statement with a [ternary operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator).
