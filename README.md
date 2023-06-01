# LeetCode Problems Repository

## Introduction

This repository is created to track my progress in solving LeetCode problems. Each problem that I solve will be listed here, along with the solution and any relevant explanations or insights. This will serve as a record of my problem-solving journey and a resource for others who are interested in learning from my solutions.

## Problem 1: Roman to Integer

- **Problem Description:**
  Given a roman numeral, convert it to an integer. The input is guaranteed to be within the range from 1 to 3999.

- **Example:**

```
Input: "XIV"
Output: 14
Explanation: The roman numeral "XIV" represents the number 14.
```

- **Solution:**

```js
const romanValues = new Map([
  ["I", 1],
  ["V", 5],
  ["X", 10],
  ["L", 50],
  ["C", 100],
  ["D", 500],
  ["M", 1000],
]);
function romanToInt(str) {
  let total = 0;
  let prevValue = 0;
  let reverseStr = str.split("").reverse();

  reverseStr.forEach((item) => {
    const currentValue = romanValues.get(item);

    if (currentValue >= prevValue) {
      total += currentValue;
    } else {
      total -= currentValue;
    }

    prevValue = currentValue;
  });

  return total;
}
```

- **Explanation:**
  I have implemented a function `romanToInt` in JavaScript that converts a given roman numeral string to its corresponding integer value. I use an object `romanNumerals` to store the values of each roman numeral. Starting from the end of the input string, I iterate through each character and check its corresponding value. If the current value is greater than or equal to the previous value, I add it to the result. Otherwise, I subtract it from the result. Finally, I return the result.

## Contribution

If you have any suggestions, improvements, or alternative solutions for the listed problems, feel free to contribute by submitting a pull request. Your contributions are highly appreciated.

## Progress

| Problem             | Solution                                                |
| ------------------- | ------------------------------------------------------- |
| 1. Roman to Integer | [Link](https://leetcode.com/problems/roman-to-integer/) |

**Note:** The table above will be updated as I solve more problems.

## License

This project is licensed under the [MIT License](LICENSE).
