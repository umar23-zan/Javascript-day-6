# Javascript-day-6

## Arrays and Loops part 2

o. Create an array of strings, loop over the array, and check if the string 'search' is inside the array. If it is, console.log() the index of 'search' in in the array. If not, console.log '-1'.
• ['hello', 'world', 'search', 'good'] => console.log(2)
• ['not', 'found'] => console.log(-1)
```
 let words = ['hello', 'world', 'search', 'good'];
  let index = -1;

  for (let i = 0; i < words.length; i++) {
    if (words[i] === 'search') {
      index = i;
    }
  }

  console.log(index);

  words = ['not', 'found'];
  index = -1;

  for (let i = 0; i < words.length; i++) {
    if (words[i] === 'search') {
      index = i;
    }
  }

  console.log(index);
```
11p. Modify 1lo so that if 'search' appears multiple times in the array, it will console.log() the index of the first appearance of 'search'. Use break; • ['hello', 'world', 'search', 'good', 'search'] => console.log(2)
```
let words = ['hello', 'world', 'search', 'good', 'search'];
  let index = -1;

  for (let i = 0; i < words.length; i++) {
    if (words[i] === 'search') {
      index = i;
      break;
    }
  }

  console.log(index);

  words = ['not', 'found'];
  index = -1;

  for (let i = 0; i < words.length; i++) {
    if (words[i] === 'search') {
      index = i;
      break;
    }
  }

  console.log(index);
```
11q. Create a function findIndex(array, word) that searches an array for a string (in the 'word' parameter) and returns the index of the first appearance of the string. If it doesn't exist in the array, return -1.
• findIndex(['green', 'red', 'blue', 'red'], 'red') => 1
• findIndex(['green', 'red', 'blue', 'red'], 'yellow') => -1
```
function findIndex(array, word) {
  for (let i = 0; i < array.length; i++) {
    if (array[i] === word) {
      return i;
    }
  }
  return -1;
```
11r. Create a function removeEgg (foods) that takes an array of strings and returns an array where the string 'egg' is removed. (Hint: loop through the array and check if each string is 'egg'. If it is 'egg', use 'continue;' to skip it. If it's not 'egg', add it to the result).
• removeEgg(['egg', 'apple', 'egg', 'egg', 'ham']) => ['apple', 'ham']
```
function removeEgg(foods) {
    const result = [];

    for (let i = 0; i < foods.length; i++) {

      if (foods[i] === 'egg') {
        continue;
      }
      result.push(foods[i]);
    }

    return result;
  }

  console.log(removeEgg(['egg', 'apple', 'egg', 'egg', 'ham']));
```
11s. Update exercise 11r to only remove the first 2 eggs from the array.
• removeEgg(['egg', 'apple', 'egg', 'egg', 'ham']) => ['apple', 'egg', 'ham']
```
function removeEgg(foods) {
        const result = [];
        let eggsRemoved = 0;

        for (let i = 0; i < foods.length; i++) {
          if (foods[i] === 'egg' && eggsRemoved < 2) {
            eggsRemoved++;
            continue;
          }

          result.push(foods[i]);
        }

        return result;
      }

      console.log(removeEgg(['egg', 'apple', 'egg', 'egg', 'ham']));
```
11t. Arrays have a method called .reverse(), which reverses the order of
the values in the array. Using .reverse(), update exercise 11s to only remove the last 2 eggs from the array.
• removeEgg(['egg', 'apple', 'egg', 'egg', 'ham']) => ['egg', 'apple', 'ham']
```
 function removeEgg(foods) {
        const reversedFoods = foods.reverse();

        const result = [];
        let eggsRemoved = 0;

        for (let i = 0; i < reversedFoods.length; i++) {
          if (reversedFoods[i] === 'egg' && eggsRemoved < 2) {
            eggsRemoved++;
            continue;
          }

          result.push(reversedFoods[i]);
        }
        return result.reverse();
      }

      console.log(removeEgg(['egg', 'apple', 'egg', 'egg', 'ham']));
```
11u. In exercise 11t, one problem with.reverse() is that it doesn't create a copy of the array it is reversing. It modifies the original array. Update the code so the function does not modify the original array. (Hint: use the .slice() method to create a copy of an array's values).
• const foods = ['egg', 'apple', 'egg', 'egg', 'ham']; • console.log(removeEgg(foods)) => ['egg', 'apple', 'ham']
• console.log(foods) => ['egg', 'apple', 'egg', 'egg', 'ham']
```
 function removeEgg(foods) {
        const foodsCopy = foods.slice();
        const reversedFoods = foodsCopy.reverse();
        const result = [];
        let eggsRemoved = 0;

        for (let i = 0; i < reversedFoods.length; i++) {
          if (reversedFoods[i] === 'egg' && eggsRemoved < 2) {
            eggsRemoved++;
            continue;
          }

          result.push(reversedFoods[i]);
        }

        return result.reverse();
      }

      const foods = ['egg', 'apple', 'egg', 'egg', 'ham'];
      console.log(removeEgg(foods));
      console.log(foods);
```

## Advanced Functions

a. Create a variable called 'add' and save a function inside. This function will console.log(2+3); Run the function twice.
```
const add = function() {
        console.log(2 + 3);
      };

      add();
      add();
```
b. Continuing from exercise 12a, create a function runTwice(fun) that takes a function (as a parameter) and runs it twice. runTwice(function() { console.log('12b'); }); => console.log('12b') twice • runTwice(add); => console.log(5) twice
```
 const add = function() {
        console.log(2 + 3);
      };

      add();
      add();

      function runTwice(fun) {
        fun();
        fun();
      }

      runTwice(function() {
        console.log('12b');
      });
      
      runTwice(add);
```
c. Create the button below. When clicking the button, after 1 second, the text inside the button changes to 'Finished!". (Hint: use setTimeout() and the DOM)

Finished!
```
<button class="js-button" onclick="
      updateButton();
    ">Start</button>

    <script>
      function updateButton() {
        const button = document.querySelector('.js-button');

        setTimeout(function() {
          button.innerHTML = 'Finished!';
        }, 1000);
      }
```
d. Continuing from exercise 12c, modify the button so that when we click it, the text immediately changes to 'Loading..., and then after 1 second, it changes to 'Finished!!.

Finished!
```
<button class="js-button" onclick="
      updateButton();
    ">Start</button>

    <script>
      function updateButton() {
        const button = document.querySelector('.js-button');
        
        button.innerHTML = 'Loading...';
        setTimeout(function() {
          button.innerHTML = 'Finished!';
        }, 1000);
      }
```
e. Create the 'Add to cart' button below. When clicking this button, display the message 'Added' below the button. Then, after 2 seconds, remove the message.

Add to cart

```
<button class="js-button" onclick="
      displayMessage();
    ">Add to cart</button>
    
    <p class="js-message"></p>

    <script>
      function displayMessage() {
        const messageElement = document.querySelector('.js-message');
        messageElement.innerHTML = 'Added';

        setTimeout(function() {
          messageElement.innerHTML = '';
        }, 2000);
      }
```
