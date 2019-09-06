---
title: Dolla Dolla
date: 2019-09-06
published: true
tags: ['coding']
series: false
canonical_url: false
description: "Here's a simple snippet that formats a raw number into a dollar value."
---

I work in the Fintech ("_Fin_ ancial" + "_Tech_ nologies") sector, essentially leveraging tech to help facilitate the investment process, whether or not it's something like creating a shopping cart frontend for an eCommerce business, to backend things like drafting an agreement and sending via email, and one of the most important pieces of developing frontend in this environment is being able to access a number from the database, turn it around with some light formatting, and return a string that has exactly everything I need to display a currency statement.

While initially, I used to use `parseInt().toFixed(2)` to format the number to display, I was able to leverage the in-built javascript formatter [`Intl.NumberFormat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NumberFormat) that did the same thing more elegantly:

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

This works when dollar amounts need to be finite/specific (think checkout pages), but what about approximations (especially larger numbers)?

This works for specific dollar amounts or when you want to include the two decimal places, but what about approximation? What happens if we wanted to display something like, "$2.5M" or "$10k"? How do we go about that?

[Someone figured out](https://gist.github.com/tobyjsullivan/96d37ca0216adee20fa95fe1c3eb56ac) a pretty elegant solution.

```javascript
const SYMBOLS = ["", "k", "m", "b", "t"];

function abbreviateNumber(value) {
    let newValue = value;
    const suffixes = ["", "k", "M", "B"];
    let suffixNum = 0;

    while (newValue >= 1000) {
        newValue /= 1000;
        suffixNum++;
    }

    newValue = newValue.toPrecision(3);
    newValue += suffixes[suffixNum];

    return newValue;
}

function moneyFormat(number) {
    return `$${abbreviateNumber(number)}`;
}

// or

// const moneyFormat = number => `$${abbreviateNumber(number)}`;

// Examples
moneyFormat(107000) // $107k
moneyFormat(1070000) // $1.07M
moneyFormat(356555) // $357k
```

You could use libraries already made, such as [Numeral.js](http://numeraljs.com/) - The way I would use it is as follows:

```javascript
import numeral from "numeral";

function abbrCurrency(val) {
    return numeral(val).format("$0a");
}

// or

const abbrCurrency = val => numeral(val).format("$0a");
```
