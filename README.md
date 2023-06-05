
# LeetCode Problems Repository

## Introduction

This repository is created to track my progress in solving LeetCode problems. Each problem that I solve will be listed here, along with the solution and any relevant explanations or insights. This will serve as a record of my problem-solving journey and a resource for others who are interested in learning from my solutions.
[Description](#description) 

## Progress

| Index      | Problem                                      | Solution                                                                           |
| ---------- | -------------------------------------------- | ---------------------------------------------------------------------------------- |
| [#1](#1)   | Roman to Integer                             | [Link](https://leetcode.com/problems/roman-to-integer/)                            |
| [#2](#2)   | Check If Two String Arrays are Equivalent    | [Link](https://leetcode.com/problems/check-if-two-string-arrays-are-equivalent/)   |
| [#3](#3)   | Design Parking System                        | [Link](https://leetcode.com/problems/design-parking-system/)                       |
| [#4](#4)   | Shuffle the Array                            | [Link](https://leetcode.com/problems/shuffle-the-array/)                           |
| [#5](#5)   | Defanging an IP Address                      | [Link](https://leetcode.com/problems/defanging-an-ip-address/)                     |
| [#6](#6)   | Power of Two                                 | [Link](https://leetcode.com/problems/power-of-two/)                                |
| [#7](#7)   | Number of Days Between Two Dates             | [Link](https://leetcode.com/problems/number-of-days-between-two-dates/)            |
| [#8](#8)   | Maximum Product Difference Between Two Pairs | [Link](https://leetcode.com/problems/maximum-product-difference-between-two-pairs/)|
| [#9](#9)   | Merge Strings Alternately                    | [Link](https://leetcode.com/problems/merge-strings-alternately)                    |
| [#10](#10) | Remove Duplicates from Sorted Array          | [Link](https://leetcode.com/problems/remove-duplicates-from-sorted-array)          |

***

### #1
## Problem 1: Roman-To-Integer 

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

### #2
## Problem 2: Check If Two String Arrays are Equivalent

- **Problem Description:**
  Given two string arrays `word1` and `word2`, return `true

` if the two arrays represent the same string, and `false` otherwise. A string is represented by an array if the array elements concatenated in order forms the string.

- **Example:**

```
Input: word1 = ["ab", "c"], word2 = ["a", "bc"]
Output: true
Explanation: Concatenating the elements of word1 in order gives "ab" + "c" = "abc", which is the same as word2.
```

- **Solution:**

```js
var arrayStringsAreEqual = function(word1, word2) {
    const str1 = word1.join("");
    const str2 = word2.join("");
    return str1 === str2;
};
```

- **Explanation:**
  The `arrayStringsAreEqual` function takes two string arrays `word1` and `word2`. It joins the elements of each array into two separate strings `str1` and `str2` using the `join("")` method. It then compares `str1` and `str2` using the strict equality operator `===` to determine if they are equal. The function returns `true` if they are equal and `false` otherwise.

### #3
## Problem 3: Design Parking System

- **Problem Description:**
  Design a parking system for a parking lot. The parking lot has three kinds of parking spaces: big, medium, and small, with a fixed number of slots for each size. Implement the `ParkingSystem` class:

  - `ParkingSystem(int big, int medium, int small)` Initializes an object of the `ParkingSystem` class. The number of slots for each parking space are given as `big`, `medium`, and `small` respectively.
  - `bool addCar(int carType)` Checks whether there is a parking space of `carType` for the car that wants to get into the parking lot. `carType` can be of three kinds: big, medium, or small, which are represented by integers `1`, `2`, and `3` respectively. A car can only park in a parking space of its `carType`. If there is no space available, return `false`, else park the car in that size space and return `true`.

- **Example:**

```
Input
["ParkingSystem", "addCar", "addCar", "addCar", "addCar"]
[[1, 1, 0], [1], [2], [3], [1]]
Output
[null, true, true, false, false]

Explanation
ParkingSystem parkingSystem = new ParkingSystem(1, 1, 0);
parkingSystem.addCar(1); // return true because there is 1 available slot for a big car
parkingSystem.addCar(2); // return true because there is 1 available slot for a medium car
parkingSystem.addCar(3); // return false because there is no available slot for a small car
parkingSystem.addCar(1); // return false because there is no available slot for a big car (no available slots for big or medium cars left)
```

- **Solution:**

```js
/**
 * @param {number} big
 * @param {number} medium
 * @param {number} small
 */
var ParkingSystem = function(big, medium, small) {
    this.spots = [null, big, medium, small];
};

/** 
 * @param {number} carType
 * @return {boolean}
 */
ParkingSystem.prototype.addCar = function(carType) {
    return this.spots[carType] && this.spots[carType]-- > 0;
};
/** 
 * Your ParkingSystem object will be instantiated and called as such:
 * var obj = new ParkingSystem(big, medium, small)
 * var param_1 = obj.addCar(carType)
 */
```

- **Explanation:**
  The `ParkingSystem` class is implemented with a constructor that takes the number of available slots for each car type (`big`, `medium`, and `small`). The `addCar` method checks if there is an available slot for the given `carType`. If there are available slots, it decreases the count for that car type and returns `true`. Otherwise, it returns `false` indicating that there is no available slot for the car type.

### #4
## Problem 4: Shuffle the Array

- **Problem Description:**
  Given the array `nums` consisting of `2n` elements in the form `[x1,x2,...,xn,y1,y2,...,yn]`. Return the array in the form `[x1,y1,x2,y2,...,xn,yn]`.

  **Note:** `n` is a positive integer.

- **Example:**

```
Input: nums = [2,5,1,3,4,7], n = 3
Output: [2,3,5,4,1,7]
Explanation: Since n is 3, we split the array into [2,5,1] and [3,4,7] and shuffle them together to obtain [2,3,5,4,1,7].
```

- **Solution:**

```js
/**
 * @param {number[]} nums
 * @param {number} n
 * @return {number[]}
 */
var shuffle = function(nums, n) {
    const x = nums.slice(0, n);
    const y = nums.slice(n);
    let newArr = [];
    
    for (let i = 0; i < n; i++) {
        newArr.push(x[i], y[i]);
    }
    
    return newArr;
};

```

- **Explanation:**
  The `shuffle` function takes an array `nums` and a positive integer `n` as input. It creates two new arrays `x` and `y` by slicing `nums` into two parts. It then iterates `n` times and pushes the `i`-th element from `x` and `y` into a new array `newArr`. Finally, it returns `newArr` which contains the shuffled elements.

### #5
## Problem 5: Defanging an IP Address

- **Problem Description:**
  Given a valid IP address `address`, return a defanged version of that IP address.

  A defanged IP address replaces every period `"."` with `"[.]"`.

- **Example:**

```
Input: address = "1.1.1.1"
Output: "1[.]1[.]1[.]1"
```

- **Solution:**

```js
/**
 * @param {string} address
 * @return {string}
 */
var defangIPaddr = function(address) {
    return address.replaceAll('.','[.]')
};
```

- **Explanation:**
  The `defangIPaddr` function takes a string `address` as input. It uses the `replaceAll` method to replace all occurrences of a period (`.`) in the address with `"[.]"`. Finally, it returns the defanged IP address.

### #6
## Problem 6: Power of Two

- **Problem Description:**
  Given an integer `n`, return `true` if it is a power of two. Otherwise, return `false`.

  An integer `n` is a power of two, if there exists an integer `x` such that `n == 2^x`.

- **Example:**

```
Input: n = 16
Output: true
Explanation: 2^4 = 16.
```

- **Solution:**

```js
/**
 * @param {number} n
 * @return {boolean}
 */
var isPowerOfTwo = function(n) {    
    return Number.isInteger(Math.log2(n));
};

```

- **Explanation:**
  The `isPowerOfTwo` function takes an integer `n` as input. It checks if the logarithm base 2 of `n` is an integer using `Number.isInteger(Math.log2(n))`. If the logarithm is an integer, it means that `n` is a power of two. The function returns `true` in that case, and `false` otherwise.

### #7
## Problem 7: Number of Days Between Two Dates

- **Problem Description:**
  Write a function `getDaysBetweenDates` to calculate the number of days between two dates. The input dates are given as strings in the format `"YYYY-MM-DD"`.

- **Example:**

```
Input: date1 = "2022-01-01", date2 = "2023-01-01"
Output: 365
```

- **Solution:**

```js
/**
 * @param {string} date1
 * @param {string} date2
 * @return {number}
 */
var daysBetweenDates = function(date1, date2) {
     date1 = new Date(date1)
     date2 = new Date(date2)
    let oneDay = 1000 * 3600 * 24
    
   return Math.abs(Math.round((date1 - date2) / oneDay))

    
    
};
```

- **Explanation:**
  The `daysBetweenDates` function takes two date strings `date1` and `date2` as input. It converts the date strings into `Date` objects and calculates the difference in milliseconds between the two dates. This difference is then divided by the number of milliseconds in a day to obtain the number of days. The function returns the absolute value of the rounded number of days.

### #8
## Problem 8: Maximum Product Difference Between Two Pairs

- **Problem Description:**
  The maximum difference between two elements in an array is defined as the absolute difference between two elements, where the first element is larger than the second element. For example, the maximum difference between `[4, 2, 5, 9]` is `9 - 2 = 7`.

  You are given an integer array `nums` of length `n`. You want to maximize the difference between the product of any two integers in `nums`. Return the maximum difference.

- **Example:**

```
Input: nums = [5,6,2,7,4]
Output: 34
Explanation: We can choose indices 1 and 3 for the first pair (6, 7) and indices 2 and 4 for the second pair (2, 4). The product difference is (6 * 7) - (2 * 4) = 34.
```

- **Solution:**

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxProductDifference = function(nums) {
  nums.sort((a, b) => a - b);
  let n = nums.length;
  let max1 = nums[n - 1];
  let max2 = nums[n - 2];
  let min1 = nums[0];
  let min2 = nums[1];
  
  return (max1 * max2) - (min1 * min2);
};
    /**
    we need 2 max number and 2 min number 

    i think we can make maxnumerArr and minNumberArr

    in nums arr we get the max number split then get max agin .    
    then min number split then min number 

    then implement the equation
     */
```

- **Explanation:**
  The `maxProductDifference` function takes an integer array `nums` as

 input. It first sorts the array in ascending order using the `sort` method with a comparison function `(a, b) => a - b`. After sorting, the maximum difference between the product of two integers can be obtained by subtracting the product of the first two elements from the product of the last two elements. The function returns the calculated difference.

### #9

### Problem 9: Merge Strings Alternately

- **Problem Description:**
  You are given two strings, `word1` and `word2`. Merge the strings by adding letters in alternating order, starting with `word1`. If one of the strings is longer than the other, append the remaining letters of the longer string at the end of the merged string.

  Return the merged string.

- **Example:**

```plaintext
Input: word1 = "abc", word2 = "def"
Output: "adbecf"
Explanation: The merged string will be "a" + "d" + "b" + "e" + "c" + "f".
```

```plaintext
Input: word1 = "ab", word2 = "xyz"
Output: "axbyz"
Explanation: The merged string will be "a" + "x" + "b" + "y" + "z".
```

- **Solution:**

```js
/**
 * @param {string} word1
 * @param {string} word2
 * @return {string}
 */
var mergeAlternately = function(word1, word2) {
    var merged = "";
    var i = 0, j = 0;
    while (i < word1.length && j < word2.length) {
        merged += word1[i] + word2[j];
        i++;
        j++;
    }
    merged += word1.slice(i) + word2.slice(j);
    return merged;
};
```

- **Explanation:**
  The `mergeAlternately` function takes two strings, `word1` and `word2`, as input and merges them alternately. It initializes an empty string `merged` to store the merged result. Then, it uses two pointers `i` and `j` to iterate over `word1` and `word2` respectively.

  Inside the while loop, it appends the characters at the current positions of `i` and `j` to the `merged` string. Then, it increments both `i` and `j` by 1.

  After the while loop, it checks if there are any remaining characters in `word1` or `word2`. If there are, it appends the remaining characters to the `merged` string using `slice` to extract the substrings starting from the current positions of `i` and `j`.

  Finally, it returns the merged string.

This solution effectively merges the strings alternately by iterating over the characters of both strings and appending them to the result string in the desired order.

### #10

### Problem 10 : Remove Duplicates from Sorted Array

- **Problem Description:**
  Given a sorted array `nums`, remove the duplicates in-place such that each element appears only once and returns the new length. Do not allocate extra space for another array; you must do this by modifying the input array in-place with O(1) extra memory.

- **Example:**

```plaintext
Input: nums = [1,1,2]
Output: 2
Explanation: The function should modify the array to return the new length and remove the duplicates. The modified array will be [1, 2], and the length is 2.
```

```plaintext
Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5
Explanation: The function should modify the array to return the new length and remove the duplicates. The modified array will be [0, 1, 2, 3, 4], and the length is 5.
```

- **Solution:**

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
    if (nums.length === 0) {
        return 0;
    }
    
    var i = 0;
    for (var j = 1; j < nums.length; j++) {
        if (nums[j] !== nums[i]) {
            i++;
            nums[i] = nums[j];
        }
    }
    
    return i + 1;
};
```

- **Explanation:**
  The `removeDuplicates` function takes an input array `nums` and removes the duplicates in-place. It uses two pointers, `i` and `j`, where `i` represents the position to store the next non-duplicate element, and `j` iterates over the array.

  Initially, it checks if the length of `nums` is 0. If it is, it means there are no elements, and the function returns 0.

  Inside the for loop, it compares `nums[j]` with `nums[i]` to check for duplicates. If `nums[j]` is different from `nums[i]`, it means a new non-duplicate element is found. In that case, it increments `i`, updates `nums[i]` with the new element, and proceeds to the next iteration.

  The loop continues until all elements are processed. Finally, the function returns `i + 1`, which represents the length of the modified array without duplicates.

This solution effectively removes duplicates from the sorted array in-place by keeping track of two pointers and updating the array elements accordingly.

## Contribution

If you have any suggestions, improvements, or alternative solutions for the listed problems, feel free to contribute by submitting a pull request. Your contributions are highly appreciated.

**Note:** The table above will be updated as I solve more problems.

## License

This project is licensed under the [MIT License](LICENSE).
