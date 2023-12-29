# TypeScript By Hitesh Choudhary

`Introduction:`

- `npm i -g typescript` -> will globally install typescript
- extension is `.ts` or `.tsx`
- To run a .`ts` file, we use the following command -> `tsc filename` -> example: `tsc sample.ts`
- When we run a TypeScript file -> it gets first converted into `JavaScript` file and then gets executed
- For continuous monitoring of `.ts` file we can write the following command -> `tsc filename -w`  -> This command will only watch single file

---

`Different types in TypeScript`

<aside>
💡 number, string, boolean, null, undefined, void, object, array, tuples, any(do not use), never, unknow
</aside>

---

`Syntax:` 

```tsx
let variableName:type=value;
```

---

`Type declaration in TypeScript:`

```tsx
let a:string='thala';
let b:number=7;
let check:boolean=false;

-----------------------------------------------------------------------------------------

let name=<string>"satyam";
let num=<number>45;
```

---

`Functions:`

```tsx
const myFunc=(num1:number, num2:number):number=>{
return num1+num2;
}

//-------using type keyword

type userName = (
	para1: string | number,
	para2: string | number
) => string | number;

const myFunc: userName = (num1, num2) => {
	if (typeof num1 === "number" && typeof num2 === "number") {
		return num1 + num2;
	} else {
		return "failed";
	}
};
```

---

`Array:`

```tsx
const arr1:number[]=[1,2,2,3,4,5]; //array of numbers

const arr2:string[]=["satyam","shivam","shundram"]; // array of strings only

const arr3:(string | number)[]=[1,2,"satyam",3,4,5]; //array of string and numbers
```

```tsx
const arr1:Array<string>=["satyam","ravi"];
const arr2:Array<boolean>=[true,false];
const arr3:Array<string | number>=["hello","world",12];
```

---

`Tuples:`

- Tuples are similar to arrays but have a fixed number of elements, and each element in a tuple can have a specific type.
- You define a tuple by specifying the types of its elements within square brackets **`[].`**
- It is a fixed size array.
- Order of elements matters here.

```tsx
let tUser:[string, number, boolean];
tUser=["Satyam",45,true]; // order matters

type user=[string,string,boolean];

const newUser:user=["satyam",'satyam@gmail.com',true];
```

---

`Objects:`

```tsx
type obj={
    height:number;
    weight:number;
    gender:string;
}

// it is compulsory to initialize all the property in the object that as type obj

const myObj:obj={
    height:45,
    weight:45,
    gender:"male",
}

//if you want to make any property optional then use **?
type obj={
    height:number;
    weight:number;
    gender?:string; // now, it is not compulsory to give the property gender 
}

const myObj:obj={
    height:45,
    weight:45,
}**
```

---

`Enum:` used to restrict somebody choice

```tsx
// Declaration of an enum
enum Direction {
  Up,
  Down,
  Left,
  Right
}

// Using the enum
let playerDirection: Direction = Direction.Right;

// Accessing enum values
console.log(Direction.Up);    // Output: 0
console.log(Direction.Down);  // Output: 1
console.log(Direction.Left);  // Output: 2
console.log(Direction.Right); // Output: 3

// Accessing enum value by its numeric value
console.log(Direction[2]); // Output: Left

// Using enums in conditionals
if (playerDirection === Direction.Right) {
  console.log("Player is moving to the right.");
}
```

---

`never:`

- It represents the type of values that never occur.
- It is a type that indicates functions that never return or variables that are never assigned.
- It is often used to signify unreachable code or conditions that should never happen.

```tsx
function throwError(message: string): never {
    throw new Error(message);
}

function infiniteLoop(): never {
    while (true) {
        // Some logic that never ends
    }
}
```

---

`Void:`

- It is commonly used as the return type of functions that do not explicitly return a value or return **`undefined`**.
- Functions declared with a return type of **`void`** indicate that they do not return any value or explicitly return **`undefined`**.

```tsx
function greet(): void {
    console.log("Hello!");
    // No return statement or returns undefined implicitly
}
```

- Variables of type **`void`** can only be assigned **`undefined`** or **`null`**.

```tsx
let unusable: void = undefined;
let empty: void = null;
// Values can only be undefined or null
```

---

`union:`

- It is used where a variable or parameter might accept more than one data type.

```tsx
// Declaring a union type
let myUnion: string | number;

// Assigning values of different types to the variable
myUnion = "Hello";
console.log(myUnion); // Output: Hello

myUnion = 42;
console.log(myUnion); // Output: 42

// Using union types in function parameters
function displayValue(input: string | number): void {
    console.log(input);
}

displayValue("World"); // Output: World
displayValue(100); // Output: 100
```

---

`Readonly:`

- It ensures that once a property is set, its value cannot be changed thereafter.
- If you want the `variable` to be read-only after initialization and not assignable, using **`readonly`** is appropriate. However, ensure it's initialized in the constructor or when the object is created.

```tsx
const obj: Example = {
    id: 1,
    name: "Example",
};

// This will result in a TypeScript compilation error
obj.id = 2; // Cannot assign to 'id' because it is a read-only property.
```

---

`Interface`

- It is used to define a structure or shape of an object.

```tsx
// Defining an interface for a Car object
interface Car {
    make: string;
    model: string;
    year: number;
    startEngine: () => void;
}

// Creating an object that adheres to the Car interface
let myCar: Car = {
    make: "Toyota",
    model: "Corolla",
    year: 2022,
    startEngine: () => {
        console.log("Engine started");
    }
};

// Accessing properties and methods defined in the interface
console.log(myCar.make); // Output: Toyota
console.log(myCar.model); // Output: Corolla
console.log(myCar.year); // Output: 2022
myCar.startEngine(); // Output: Engine started
```

- The main feature of interface is that it allows to define reusable types.

```tsx
interface obj{
height:number,
weight:number,
}

interface newObj extends obj{
gender:string,
isLoggedIn:boolean,
}

//user object will consist of all the properties from obj and newObj type
const user:newObj={
height:45,
weight:45,
gender:"male",
isLoggedIn:false,
}
```
