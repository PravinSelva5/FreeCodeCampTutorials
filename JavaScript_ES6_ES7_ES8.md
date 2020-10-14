# JavaScript ES6, ES7, ES8: Learn to Code on the Bleeding Edge (Full Course)

1. Introduction
--------------
 2. Template literals 
------
- in the past to concatenate string:
```
 let word1 = 'Dylan'; 
 let word2 = 'Israel'; 
 const fullName = word1 + ' ' + word2; 
 console.log(fullName)
 ```
- But string literals allow us to: 
```
let word1 = 'Dylan'; 
let word2 = 'Israel';
const fullName = `${word1} ${word2}d`; 
```
- Makes it easier to have variables
- `let example = 'Hello \n' + 'world';`
- But now you can use 
```let example = `${word1} ${word2}`;```
- this makes multi-line strings a lot easier

3. Destructuring Objects
------
- `const personalInformation = {
firstName: 'Dylan', lastName: 'Israel', city: 'Austin', state: 'Texas', 'zipCode: 73301};`
- You can now get values from objects like this:
- `const {firstName: fn, lastName: ln} = personalInformation; console.log(`${fn} ${ln}`); `
4. Destructuring Arrays
-------
- Before:
- `let names = ['Dylan', 'Coding God', 'Israel'];`
- Now:
- `let [firstName, middleName, lastName];`
- You can overwrite the values in the array by assigning new values to the variable you assigned to it, such as: `firstName = "Lebron James"`
5. Object Literal
----------
```
function addressMaker(city, state){ 
const newAddress = {newCity:city, newState: state}; 
console.log(newAddress) 
} 
addressMaker('Austin', 'Texas');
```
- You can now do the following:
```
function addressMaker(city, state){ 
const newAddress = {city, state}; 
console.log(newAddress) } 
addressMaker('Austin', 'Texas');
```
6. Object Literal Challenge
-----------
```
function addressMaker(address) { 
const newAddress = { city: address.city, state: address.state, country: 'United States'};
}  
addressMaker({city: 'Austin', state: 'Texas'});
```
- Now after destructing object, the above looks like this:

```
function addressMaker(address) { 
const {city, stake} = address; 
const newAddress = { city, state, country: 'United States'}; 
console.log(`${newAddress.city}, ${newAddress.state}, ${newAddress.country}`)}  

addressMaker({city: 'Austin', state: 'Texas'});
```
7. For of Loop
--------------
```
    let incomes = [62000, 67000,7500];
    let total = 0;
    for (const income of incomes){ total += income;}
    console.log(total);
```

8. For of Loop Challenge
------------------
- Can only iterate through objects, can't iterate and change values of the object

9. Spread Operator
---------------------
- `let example1 = [1,2,3,4,5,6];`
- `let example2 = [...example1];` this will contain example 1's value into example 2
- `console.log(example2);` Ouput will be [1,2,3,4,5,6]
- `example2.push(true);` will only affect example2, not example1
- `console.log(example2);` Output will be [1,2,3,4,5,6,true]

10. Rest Operator
----------------------
- Gives us the ability to get the arguments out of our function
- It's used in the case when we don't know how many inputs are going to be used 
- `function add(nums) { console.log(nums); } add(4)`

11. Arrow Functions
-------------------
- Allows you to remove the unecessary boiler plate of callback functions, it comes with a lot of functionality
```
function add(...nums){ 
        let total = nums.reduce((x, y) => x + y);
        console.log(total);
  }
 add(4,5,7,8,12);
```
12. Default Params
---------------
- Helps aviod errors when parameters not given when functions are called
```
function add(numArray = []) {
    let total = 0;
    numArray.forEach( (element) => {
        total += element;
    });
    console.log(total);
}
add(); //no input given, so function will take the default, empty array as the parameter
```

13. Includes()
--------------------
- includes will return a boolean value of true or false (not supported by internet explorer)
```
let numArray = [1,2,3,4,5];
console.log(numArray.includes(2));
```

14. Let & Const
--------------------
- In javascript, a variable can be used before it is declared, called variable hoisting. This is a reason Let & const was created to avoid
- Let is a stricter verison of var, const makes the variable read-only.
- One exception for const, is an empty array. You can still append values to the array BUT you can't change the type of the array.

15. Import & Export
-----------------------
- allows you to do dependency injections, follow a lot of object oriented programming, and making the code a lot more modular in nature.
```
// One file
export const data = [1,2,3];

// In another file
import {data, data2} from './example.js';
let updatedData = data;

updatedData.push(5);
console.log(updatedData);
```

16. padStart() & padEnd()
--------------------
- always you to add values to the start & end of the string

```
let example = 'Dylan'

console.log(example.padStart(10,'a');  // Output will be 'aaaaaDylan'
console.log(example.padEnd(10, 'a');  // Output will be 'Dylanaaaaa'
```
17. Classes
--------------------------
```
export class Animal {
    constructor(type, legs) {  // constructor essentially assigns those values to our animal class
        this.type = type;
        this.legs = legs;
    }
    
    makeNoise(sound='Loud Noise') {
        console.log(sound);
    }
    
    // static function allows us to not to create an instance
    
    get metaData() {
        return `Type: ${this.type}, Legs: ${this.legs}`;
    }
    static return10() {
        return 10;
    }
}

// to inherit properties from Animal class
export class Cat extends Animal {
    constructor(type, legs, tail){
        super(type, legs); // super key word to bring inherit Animal's properties.
        this.tail = tail;
    }
    // Overwrites makeNoise method to make it more suitable for Cat class
    makeNoise(sound = "meow"){
        console.log(sound);
    }
}

// Another file

import { Animal } from './animal.js';

let cat = new Animal('Cat', 4);

// To change values
cat.legs = 3;  
cat.MakeNoise();        // will console log Loud Noise
cat.MakeNoise('Meow'); // will console log Meow

console.log(cat.type); // Cat
console.log(cat.legs); // 


// if you were to comment up all the above code and run the following 
console.log(Animal.return10());  
// you will get the output of the function without instatiating an object for it


// you can run the metaData function
// This allows us to call functions in the get function, hide a bit of the class from the user
console.log(cat.metaData);


// Assume above code in other file not present

import { Animal, Cat } from './animal.js';

let cat = new Cat('Cat', 4);

cat.makeNoise(); // the output will be meow not Loud Noise
console.log(cat.metaData) 
// you'll still get an ouptut because you're inheriting the information from the Animal class -> Output will be Type: Cat, Legs: 4
```

18. Trailing Commas
----------------------
- You don't have any issues with trailing commas anymore. The following will still work:
```
function add(param1,){
    const example = {
        name: 'Dylan',
    };
    console.log(example)
};

add(2); // Output will be 'Dylan'
```

19. Aysnc & Await & Promises
-------------------------
```
const apiUrl = 'https://fcctop100.herokuapp.com/api/fccusers/top/alltime';

function getTop100Campers() {
    fetch(apiUrl)
    .then( (r) => r.json())
    .then( (json) => {
        console.log(json[0])
    }).catch( (error) => {
        console.log("failed");
    } );
}

getTop100Campers();
```
- Fetch is returning a promise, when the data is delievered. The .then will take the response and convert it into a json object so that javascript can read it
- catch is used if an error is produced when trying to execute the AJAX call
- Now how can we use LESS CODE by using ASYNC & AWAIT ???
```
const apiUrl = 'https://fcctop100.herokuapp.com/api/fccusers/top/alltime';

async function getTop100Campers() {
    const response = await fetch(apiUrl); // this is basically saying, wait until you get a response whether its a success response or a failed response
    const json = await response.json(); // waits for our response to be turned into json
    
    console.log(json[0]);
}
```

20. Async & Await (Challenge)
-------------------------
```
function resolveAfter3Seconds() {
    return new Promise( resolve => {
    setTimeout( () => {
        resolve('resolved');
    }, 3000);
    });
}
```
- To solve the above challenge
```
resolveAfter3Seconds().then((data) => {
    console.log(data);
});
```
- To resolve the same challenge with async and await
```
async function getAsyncData() {
    const result  = await resolveAfter3Seconds()l
    console.log(result);
}
getAsyncData();
```

21. Sets
-------------
```
const exampleSet = new Set([1,1,1,1,1,1,1,3,3,3,3]);
console.log(exampleSet); // will output the type, which is a set
console.log(exampleSet.size); // will output 2
```
- You can add values to the set with the `add` method, if the value is already in the set, it won't be added
- You can remove the values as well with the `delete` method
- You can check if a value exists in the set with the `has` method
- You can clear an entire set with the `clear` method
- Remember that a set is iterable
