---
title: Dolla Dolla
date: 2019-09-06
published: false
tags: ['coding']
series: false
canonical_url: false
description: "Here's a simple snippet that returns a dollar value (from a raw number)"
---

I work in the Fintech ("_Fin_ ancial" + "_Tech_ nologies") sector, essentially leveraging tech to help facilitate the investment process, and one of the most important pieces of developing frontend is being able to access a number from the database, turn it around with some light formatting, and return a string that has exactly all the bells and whistles that I need to display a currency statement.

While initially, I used to use `parseInt().toFixed(2)` to format the number to display, I was able to use in-built javascript formatters that did the same thing more elegantly:

```javascript
// Converts a raw number value to USD currency.
function toCurrency(val) {
    const formatter = new Intl.NumberFormat("en-US", {
        style: "currency",
        currency: "USD"
    });

    return formatter.format(val);
}

// Examples
toCurrency(100) // $100.00
toCurrency(101.01) // $101.01
toCurrency(102.546) // $102.55
```

This works for small dollar amounts, when you want to include the two decimal places, but what about approximation? What happens if we wanted to display something like, "$2.5M" or "$10k"? How do we go about that?

Fear not! There's a library called [Numeral.js](https://google.com)! The way I use it is as follows:

```javascript
import numeral from "numeral";

function abbrCurrency(val) {
    return numeral(val).format("$0a");
}

// or

const abbrCurrency = val => numeral(val).format("$0a");
```
