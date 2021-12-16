# TypeScript Documentation

- prerequisities: Javascript

Chapters:

1. Introduction
2. Environment setup
3. First Typescript program
4. Data Types - built-in

   - number, string, boolean, void, undefined, null

5. Data Types - user-defined

   - union type
   - Array type
   - tuple type
   - enum type
   - any type
   - object type
   - custom type

6. class
7. inheritance
8. interface
9. function overloading

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

### 4. Built-in data types

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

  console.log(userId.toLowerCase()); // error here

  function display(): void {
    console.log("Hi I am display");
  }
  display();
  ```

- inferred Typing
  ```js
  let userName = "anis"; // data type inferred as string
  ```

### 5. User-defined data types

#### 5.1 Union Type

- Union Type - more than one type for variable or function parameter

  ```js
  let userId: string | number;

  // userId = 101; // no error
  // userId = "101"; // no error
  // userId = true; // error

  function userIdDataType(userId: string | number) {
    console.log(typeof userId);
  }

  userIdDataType("123"); // no error
  userIdDataType(123); // no error
  // userIdDataType(true); // error
  ```

#### 5.2 Array

- Array Type- similar data

  ```js
  // let users = ["anis", "rabu", "pinky"];

  // let users: string[];
  // users = ["anis", "rabu", "pinky"];

  let users: Array<string>;
  users = ["anis", "rabu", "pinky"];

  // for (let index = 0; index < users.length; index++) {
  //   const element = users[index];
  //   console.log(element);
  // }

  // users.forEach((element) => {
  //   console.log(element);
  // });

  users.sort();
  console.log(users);

  users.push("limon");
  console.log(users);

  users.pop();
  console.log(users);

  users.unshift("milton");
  console.log(users);

  users.shift();
  console.log(users);

  // multi-types array
  // let users: (number | string)[];
  // users = [10, "anis", 25, 35, "islam"];
  ```

  #### 5.3 Tuple Type

- Tuple Type - Mixed data type

  ```js
  let users: [number, String];
  users = [101, "anis"];

  console.log(users);
  console.log(users[0]);
  console.log(users[1]);

  users.push(102, "sakib");
  console.log(users);
  ```

  #### 5.4 Enum Type

- Enum Type: no duplicate data, helps to store constants

  ```js
  // enum example
  // helps us to store constants

  // numeric enum
  enum UserRequest {
    ReadData,
    // ReadData = 2,
    SaveData,
    UpdateData,
  }

  console.log(UserRequest);
  console.log(UserRequest.ReadData);
  console.log(UserRequest.SaveData);

  // string enum
  enum UserRequest {
    ReadData = "READ_DATA",
    // ReadData = 2,
    SaveData = "SAVE_DATA",
    UpdateData = "UPDATE_DATA",
  }

  console.log(UserRequest);
  console.log(UserRequest.ReadData);
  console.log(UserRequest.SaveData);
  console.log(UserRequest["UpdateData"]);

  // Heterogeneous enum
    enum User {
    id = 101,
    name = "anisul",
    }

  ```

  #### 5.5 any Type

- any Type: if you have no knowledge about the variable type use any type: user input values

  ```js
  let password: any;
  let passwords: any[];
  ```

  #### 5.6 object Type

- object Type: can store value as key value pair

  ```js
  let names: object;
  names = { name1: "anis" };
  console.log(names);

  let users: object[];
  users = [];

  let user1: { userName: string, userId: number };
  user1 = { userName: "anis", userId: 101 };
  users.push(user1);

  let user2: { userName: string, userId: number };
  user2 = { userName: "rabu", userId: 102 };

  users.push(user2);

  for (const key in users) {
    console.log(users[key]["userName"]);
  }
  ```

#### 5.7 Custom Type

- custom Type: you can create your own type

  ```js
  type User = { userName: string, userId: number };

  let users: User[];
  users = [];

  let user1: User;
  user1 = { userName: "anis", userId: 101 };
  users.push(user1);

  let user2: User;
  user2 = { userName: "rabu", userId: 102 };
  users.push(user2);

  let user3: User;
  user3 = { userName: "lucky", userId: 103 };
  users.push(user3);

  // console.log(users);

  type RequestType = "GET" | "POST";
  let getRequest: RequestType;
  getRequest = "GET";

  function requestHandler(requestType: RequestType) {
    console.log(requestType);
  }
  requestHandler("GET");
  ```

### 6. class

- class can have constructor, properties, methods
- create object - let objectName = new className();
- Example

  ```js
  class User {
    // properties, methods, constructor
    userName: string;
    age: number;

    constructor(userName: string, age: number) {
      this.userName = userName;
      this.age = age;
    }

    display(): void {
      console.log(`username: ${this.userName}, age: ${this.age}`);
    }
  }

  let user1 = new User("Anisul Islam", 25);
  user1.display();

  let user2 = new User("Rabeya Islam", 31);
  user2.display();
  ```

### 7. Inheritance

- inheritance helps us to acquire properties of one class to another

```js
class User {
  userName: string;
  age: number;

  constructor(userName: string, age: number) {
    this.userName = userName;
    this.age = age;
  }

  display(): void {
    console.log(`username: ${this.userName}, age: ${this.age}`);
  }
}

class Student extends User {
  studentId: number;

  constructor(userName: string, age: number, studentId: number) {
    super(userName, age);
    this.studentId = studentId;
  }
  display(): void {
    console.log(
      `username: ${this.userName}, age: ${this.age}, id: ${this.studentId}`
    );
  }
}

let student1 = new Student("keya", 31, 1302020015);
student1.display();

let user1 = new User("Anisul Islam", 25);
user1.display();

// let user2 = new User("Rabeya Islam", 31);
// user2.display();
```

### 9. Function Overloading

- we can declare multiple methods with same name but paramter types and return type must be different

#### Example
