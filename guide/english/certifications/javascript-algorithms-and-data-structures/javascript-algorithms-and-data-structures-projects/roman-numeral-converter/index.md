---
title: Roman Numeral Converter
---

# Roman Numeral Converter

---
## Problem Explanation

You will create a program that converts an integer to a Roman Numeral.

#### Relevant Links

*   <a href='http://www.mathsisfun.com/roman-numerals.html' target='_blank' rel='nofollow'>Roman Numerals</a>
*   <a href='http://forum.freecodecamp.com/t/javascript-array-prototype-splice/14307' target='_blank' rel='nofollow'>Array.splice()</a>
*   <a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf' target='_blank' rel='nofollow'>Array.indexOf()</a>
*   <a href='http://forum.freecodecamp.com/t/javascript-array-prototype-join/14292' target='_blank' rel='nofollow'>Array.join()</a>


---
## Hints

### Hint 1

Creating two arrays, one with the Roman Numerals and one with the decimal equivalent for the new forms will be very helpful.


### Hint 2

If you add the numbers to the arrays that go before the new letter is introduced, like values for 4, 9, and 40, it will save you plenty of code.


### Hint 3

You can't have more than three consecutive Roman numerals together.



---
## Solutions

<details><summary>Solution 1 (Click to Show/Hide)</summary>

```javascript
var convertToRoman = function(num) {
  var decimalValue = [1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1];
  var romanNumeral = [
    "M",
    "CM",
    "D",
    "CD",
    "C",
    "XC",
    "L",
    "XL",
    "X",
    "IX",
    "V",
    "IV",
    "I"
  ];

  var romanized = "";

  for (var index = 0; index < decimalValue.length; index++) {
    while (decimalValue[index] <= num) {
      romanized += romanNumeral[index];
      num -= decimalValue[index];
    }
  }

  return romanized;
};

// test here
convertToRoman(36);
```


#### Code Explanation

*   We start off by creating two arrays with default conversion with matching indices. These are called `decimalValue` and `romanNumeral`. We also create an empty string variable, `romanized`, which will house the final roman number.
*   Using a for loop, we loop through the indicies of the `decimalValue` array. We continue to loop until while the value at the current `index` will fit into `num`.
*   Next, we add the roman numeral and decrease `num` by the decimal equivalent.
*   Finally, we return the value of `romanized`.

#### Relevant Links

*   <a href='http://forum.freecodecamp.com/t/javascript-for-loop/14666' target='_blank' rel='nofollow'>For Loops</a>
*   <a>While Loops</a>
</details>


<details><summary>Solution 2 (Click to Show/Hide)</summary>

```javascript
function convertToRoman(num) {
  var romans = ["I", "V", "X", "L", "C", "D", "M"],
    ints = [],
    romanNumber = [],
    numeral = "";
  while (num) {
    ints.push(num % 10);
    num = Math.floor(num / 10);
  }
  for (i = 0; i < ints.length; i++) {
    units(ints[i]);
  }
  function units() {
    numeral = romans[i * 2];
    switch (ints[i]) {
      case 1:
        romanNumber.push(numeral);
        break;
      case 2:
        romanNumber.push(numeral.concat(numeral));
        break;
      case 3:
        romanNumber.push(numeral.concat(numeral).concat(numeral));
        break;
      case 4:
        romanNumber.push(numeral.concat(romans[i * 2 + 1]));
        break;
      case 5:
        romanNumber.push(romans[i * 2 + 1]);
        break;
      case 6:
        romanNumber.push(romans[i * 2 + 1].concat(numeral));
        break;
      case 7:
        romanNumber.push(romans[i * 2 + 1].concat(numeral).concat(numeral));
        break;
      case 8:
        romanNumber.push(
          romans[i * 2 + 1]
            .concat(numeral)
            .concat(numeral)
            .concat(numeral)
        );
        break;
      case 9:
        romanNumber.push(romans[i * 2].concat(romans[i * 2 + 2]));
    }
  }
  return romanNumber
    .reverse()
    .join("")
    .toString();
}

// test here
convertToRoman(97);
```


#### Code Explanation

*   Create an array of Roman Numerals (`romans`).
*   Use a for loop to create an array of the digits (`ints`) in the number.
*   Loop through the array of digits (base 10) and as you do, increment the Roman Numeral (base 5) index by 2 (`numeral = romans[i*2]`).
*   Within the loop, use Switch Case to push the proper Roman Numerals (backwards) onto that array.
*   Reverse the Roman Numerals array and turn it into a string.

#### Relevant Links

*   <a href='http://forum.freecodecamp.com/t/javascript-for-loop/14666' target='_blank' rel='nofollow'>For Loops</a>
*   <a>While Loops</a>
*   <a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math' target='_blank' rel='nofollow'>Math</a>
</details>

<details><summary>Solution 3 (Click to Show/Hide)</summary>

```javascript
function convertToRoman(num) {
  var romans = [
      // 10^i 10^i*5
      ["I", "V"], // 10^0
      ["X", "L"], // 10^1
      ["C", "D"], // 10^2
      ["M"] // 10^3
    ],
    digits = num
      .toString()
      .split("")
      .reverse()
      .map(function(item, index) {
        return parseInt(item);
      }),
    numeral = "";

  // Loop through each digit, starting with the ones place
  for (var i = 0; i < digits.length; i++) {
    // Make a Roman numeral that ignores 5-multiples and shortening rules
    numeral = romans[i][0].repeat(digits[i]) + numeral;
    // Check for a Roman numeral 5-multiple version
    if (romans[i][1]) {
      numeral = numeral
        // Change occurrences of 5 * 10^i to the corresponding 5-multiple Roman numeral
        .replace(romans[i][0].repeat(5), romans[i][1])
        // Shorten occurrences of 9 * 10^i
        .replace(
          romans[i][1] + romans[i][0].repeat(4),
          romans[i][0] + romans[i + 1][0]
        )
        // Shorten occurrences of 4 * 10^i
        .replace(romans[i][0].repeat(4), romans[i][0] + romans[i][1]);
    }
  }

  return numeral;
}

// test here
convertToRoman(36);
```

#### Code Explanation

*   Use an array (`romans`) to create a matrix containing the Roman numeral for a given power of 10 and, if available, the Roman numeral for that power of 10 times 5.
*   Convert the input number (`num`) to a reversed array of digits (`digits`) so that we can loop through those digits starting with the ones position and going up.
*   Loop through each digit, starting with the ones place, and create a Roman numeral string by adding each higher-power Roman numeral to the start of the `numeral` string a number of times equal to `digit`. This initial string ignores the Roman numerals that are a power of 10 times 5 and also ignores shortening rules.
*   If the relevant power of 10 has a 5-multiple Roman numeral, in `numeral`, replace 5-in-a-row occurrences with the relevant 5-multiple Roman numeral (i.e., V, L, or D) and shorten occurrences of 9 * 10^i (e.g., VIIII to VIX) and 4 * 10^i (e.g., XXXX to XL). Order is important here!
*   Finally, return `numeral`.

#### Relevant Links

*   <a href='http://forum.freecodecamp.com/t/javascript-for-loop/14666' target='_blank' rel='nofollow'>For Loops</a>
*   <a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split' target='_blank' rel='nofollow'>.split()</a>
*   <a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse' target='_blank' rel='nofollow'>.reverse()</a>
*   <a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map' target='_blank' rel='nofollow'>.map()</a>
*   <a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toString' target='_blank' rel='nofollow'>.toString()</a>
*   <a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt' target='_blank' rel='nofollow'>parseInt()</a>
*   <a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace' target='_blank' rel='nofollow'>.replace()</a>
*   <a href='https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/repeat' target='_blank' rel='nofollow'>.repeat()</a>
</details>

