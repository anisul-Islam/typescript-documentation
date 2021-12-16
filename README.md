# TypeScript Documentation

- prerequisities: Javascript

Chapters:

1. Introduction
2. Environment setup

### 1. Introduction

#### 1.1 What is TypeScript?

- In a simple words, Types + JavaScript = TypeScript
- It is a superset of JS
- developed and maintained by Microsoft

#### 1.2 Why TypeScript?

- JS Check types in run time while typescript add static typing to JS so we can handle errors before running the program.
- increase readability and code quality
- popular JS libraray Angular use TypeScript.
- It can be used in both: client and server side.
- Intellisense IDE Support while coding: code completion, content assist and code hinting

#### 1.3 TS Versions

- earlier versions
- TypeScript 1.0 October 2014
- TypeScript 2.0 September 2016
- TypeScript 3.0 July 2018
- TypeScript 4.0 - latest release August 2020

#### 1.4 Example:

```js
// index.js
// without typescript
function addNumbers(num1, num2) {
  console.log(num1 + num2);
}

addNumbers(20, 30);
addNumbers(20, "30");

// with typescript
// without typescript
function addNumbers(num1: number, num2: number) {
  console.log(num1 + num2);
}

addNumbers(20, 30); // no error
addNumbers(20, "30"); // error

// without typescript
let x;
x = 20; // correct
x = "anisul"; // correct
x = true; // correct
x = [10, 20]; // correct

// with typescript
let x: number;
x = 20; // correct
x = "20"; // Not correct
x = true; // Not correct
x = [10, 20]; // Not correct
```

### 2. Environment setup

#### 2.1 Install and use typescript

- Text Editor: VS Code
- Install node & typescript
  ```js
     npm intsall typescript --save-dev (local)
     npm install -g typescript (global)
     npx tsc fileName.ts
  ```
- check various versions:

  ```js
    node --version
    npm --version
    tsc --version
  ```

#### 2.2 How does it work?

- index.ts -> tsc index.ts -> index.js

### 3. First typescript program

#### 3.1 Example

- typescript file extension is .ts
- Run the following program using `tsc index.ts` command and then `node index.js`

  ```js
  // index.ts

  // without ts
  function addNumbers(num1, num2) {
    console.log(num1 + num2);
  }

  addNumbers(20, 30);
  addNumbers(20, "30");

  // correct one using ts
  function addNumbers(num1: number, num2:number) {
    console.log(num1 + num2);
  }

  addNumbers(20, 30);
  addNumbers(20, "30");


  let num1 = 20;
  console.log(num1);

  let name= "anisul islam";
  name. //intellisense support will be here
  ```

- some compiler flag
  - tsc index.js --watch

### 4. data types

- Any (super type)
  - built in types: number, string, boolean, void, null, undefined etc.
  - user-defined types: Arrays, Enums, Classes, interfaces etc.
- example of built-in types

  ```js
  // string TYPE EXAMPLE
  let firstName: string;
  let lastName: string;
  let fullName: string;
  let occupation: string;

  firstName = "Anisul";
  lastName = " Islam";
  occupation = "student";

  console.log(firstName);
  console.log(lastName);
  console.log(occupation);

  // toUpperCase()
  console.log(firstName.toUpperCase());

  // toLowerCase()
  console.log(firstName.toLowerCase());

  // split([separator[,limit]])
  console.log(fullName.split(" "));

  // concat()
  fullName = firstName.concat(lastName);

  console.log(`User ${fullName} is a ${occupation}`);

  let userName: string;
  let id: number;
  let isLoggedIn: boolean;
  ```

- inferred Typing
  ```js
  let userName = "anis"; // data type inferred as string
  ```
