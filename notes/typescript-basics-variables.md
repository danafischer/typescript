# TypeScript Basics – Learning Notes

**Author:** Dana Fischer  
**Course:** [TypeScript for Beginners – Udemy](https://www.udemy.com/course/typescript-for-beginners/)  
**Section:** Variables and Data Types  
**Document Type:** Personal Learning Notes  

---

## 1. About These Notes

These notes summarize the TypeScript fundamentals covered during my first course exercises.

Topics include:

- Variables and basic data types.
- Compiling TypeScript into JavaScript.
- Running JavaScript with Node.js or in a browser.
- Strings and string methods.
- Booleans.
- The `any` type.
- Homogeneous and heterogeneous arrays.
- Browser dialogs.
- Comments.
- Enums.
- Union types.

The explanations are written in my own words. Examples combine course-related practice with personal exercises.

## 2. What Is TypeScript?

TypeScript adds a type system to JavaScript.

Types help describe which values a variable can hold and allow the compiler or editor to identify certain mistakes before the program runs.

For example:

```typescript
let productPrice: number = 1000;
```

The variable is declared as a `number`. Assigning text to it produces a type-checking error:

```typescript
let productPrice: number = 1000;

// Incorrect: a string cannot be assigned to a number.
// productPrice = "expensive";
```

TypeScript type checking does not replace runtime validation. Data received from users, files, or external systems still needs appropriate checks.

## 3. TypeScript and JavaScript Files

| Extension | Purpose |
|---|---|
| `.ts` | TypeScript source code |
| `.js` | JavaScript code that can be executed |
| `.html` | A web page that can load JavaScript |

For the basic workflow used in these exercises:

1. Write and save the TypeScript file.
2. Compile it into JavaScript.
3. Run the JavaScript file.

```text
variables.ts → TypeScript compiler → variables.js
```

I edit the `.ts` source file. Manual changes to generated `.js` files can be overwritten by the next compilation.

## 4. My Development Workflow

### Tools

- Visual Studio Code for editing.
- PowerShell as the terminal.
- Node.js for running console-based JavaScript.
- npm for installing packages.
- The TypeScript compiler for checking and compiling `.ts` files.

### Compile and Run

From the folder containing the file:

```powershell
tsc.cmd variables.ts
node variables.js
```

On my Windows setup, I use `tsc.cmd` to select the Windows command launcher explicitly. This avoids the PowerShell script-policy error I encountered with `tsc`.

The course instructor uses Bash on macOS. The terminal prompt and some commands look different, but the TypeScript concepts remain the same.

### Important Reminder

After changing TypeScript code:

1. Save with **Ctrl + S**.
2. Compile again.
3. Run the generated JavaScript.

Running an existing `.js` file without recompiling can display results from an earlier version.

A successful compilation commonly returns to the terminal prompt without displaying a success message.

### Prevent JavaScript Output When Errors Exist

For exercises where I want compilation errors to prevent new JavaScript output:

```powershell
tsc.cmd variables.ts --noEmitOnError
```

An existing `.js` file is not deleted by this option. It may still contain an older version of the program.

## 5. Variables and Type Annotations

A variable stores a value.

A type annotation appears after the variable name:

```typescript
let wholeNumber: number = 20;
let decimalNumber: number = 3.14;
let message: string = "Learning TypeScript step by step.";
let isCompleted: boolean = false;
```

The pattern is:

```text
variable name: type = value
```

### Type Inference

TypeScript can often infer the type from the initial value:

```typescript
let score = 100;
let courseName = "TypeScript";
```

Here, TypeScript infers `number` for `score` and `string` for `courseName`.

### `var`, `let`, and `const`

Some course exercises use `var`.

For my own practice:

- I use `const` when the variable will not be reassigned.
- I use `let` when reassignment is needed.
- I recognize `var` when following the course.

```typescript
const courseName: string = "TypeScript";
let completedLessons: number = 0;

completedLessons = 1;
```

`let` and `const` are block-scoped. `var` is function-scoped rather than block-scoped.

`const` prevents reassignment of the variable. It does not automatically make an object or array immutable.

## 6. Numbers

The `number` type represents both whole numbers and decimal values.

```typescript
const wholeNumber: number = 20;
const decimalNumber: number = 3.14;

console.log(wholeNumber);
console.log(decimalNumber);
```

Expected output:

```text
20
3.14
```

For these examples, TypeScript does not use separate `int` and `float` types.

## 7. Strings

A string represents text.

Strings can use single quotes, double quotes, or backticks.

```typescript
const firstMessage: string = "Learning TypeScript";
const secondMessage: string = 'Practicing every day';
const thirdMessage: string = `Building confidence through practice`;
```

### Template Literals

Backticks support embedded expressions:

```typescript
const learnerName: string = "Dana";
const completedLessons: number = 17;

const progressMessage: string =
  `${learnerName} completed ${completedLessons} learning activities.`;

console.log(progressMessage);
```

### Escape Sequences

```typescript
console.log("First line\nSecond line");
console.log("Name:\tDana");
console.log("She said: \"Keep learning.\"");
```

| Sequence | Meaning |
|---|---|
| `\n` | New line |
| `\t` | Tab |
| `\"` | Double quote |
| `\\` | Backslash |

## 8. String Properties and Methods

```typescript
const topic: string = "TypeScript Basics";
```

| Expression | Result |
|---|---|
| `topic.length` | `17` |
| `topic.toUpperCase()` | `"TYPESCRIPT BASICS"` |
| `topic.toLowerCase()` | `"typescript basics"` |
| `topic.charAt(0)` | `"T"` |
| `topic.indexOf("Basics")` | `11` |
| `topic.substring(0, 10)` | `"TypeScript"` |
| `topic.split(" ")` | `["TypeScript", "Basics"]` |

### Property vs. Method

A property is accessed without calling it:

```typescript
console.log(topic.length);
```

A method is called using parentheses:

```typescript
console.log(topic.toUpperCase());
```

String methods such as `toUpperCase()` return a new string. They do not change the original string.

## 9. Booleans

The `boolean` type accepts:

- `true`
- `false`

```typescript
const isAvailable: boolean = true;
const isCompleted: boolean = false;

console.log(isAvailable);
console.log(isCompleted);
```

### Boolean Values Are Different from Strings

```typescript
const correctValue: boolean = false;

// Incorrect: "false" is text, not a boolean.
// const incorrectValue: boolean = "false";
```

The same applies to any other text:

```typescript
// Incorrect: a string cannot be assigned to boolean.
// const isCompleted: boolean = "finished";
```

### What I Learned from the Editor

A red underline can indicate a type error.

To read the explanation in Visual Studio Code:

- Hover over the underlined code.
- Open the **Problems** panel.
- Compile the saved file to see compiler diagnostics.

Displaying output from an existing JavaScript file does not prove that the current TypeScript source has no errors.

## 10. The `any` Type

A variable declared with `any` can hold different kinds of values.

```typescript
let flexibleValue: any = 10;

flexibleValue = "TypeScript";
flexibleValue = true;
```

An object can also be assigned to an `any` variable:

```typescript
const product: any = {
  productId: 1,
  productName: "Phone",
  productPrice: 1000
};

console.log(product);
```

The syntax is:

```typescript
const product: any = {
  productId: 1
};
```

The colon introduces the type. The equals sign assigns the value.

### Limitation

`any` disables much of the type checking for that value.

It is useful to understand the concept, but I aim to use more specific types when I know the expected data structure.

## 11. Homogeneous Arrays

A homogeneous array contains values of one declared element type.

```typescript
const technologies: Array<string> = [
  "AngularJS",
  "ReactJS",
  "NodeJS"
];
```

An equivalent syntax is:

```typescript
const technologies: string[] = [
  "AngularJS",
  "ReactJS",
  "NodeJS"
];
```

### Accessing Elements

Array indexes start at zero.

```typescript
console.log(technologies[0]); // AngularJS
console.log(technologies[1]); // ReactJS
console.log(technologies[2]); // NodeJS
```

### Array Length

```typescript
console.log(technologies.length); // 3
```

### Adding an Element

```typescript
technologies.push("TypeScript");

console.log(technologies.length); // 4
```

The array can be modified even though its variable uses `const`. The variable itself cannot be reassigned to a different array.

### Type Checking

```typescript
// Incorrect: this array accepts strings.
// technologies.push(100);
```

## 12. Heterogeneous Arrays

A heterogeneous array contains different kinds of values.

An introductory example uses `any[]`:

```typescript
const mixedValues: any[] = [
  1,
  2,
  "AngularJS",
  "ReactJS",
  true,
  false
];

console.log(mixedValues);
```

A more specific alternative uses a union type:

```typescript
const mixedValues: (number | string | boolean)[] = [
  1,
  2,
  "AngularJS",
  true
];
```

This allows the listed types while retaining more checking than `any[]`.

## 13. Browser Dialogs

The course introduces three browser functions:

| Function | Purpose | Return Value |
|---|---|---|
| `alert()` | Display a message | `undefined` |
| `confirm()` | Ask for confirmation | `boolean` |
| `prompt()` | Request text input | `string` or `null` |

### Alert

```typescript
alert("Welcome to my TypeScript practice.");
```

### Confirm

```typescript
const wantsToContinue: boolean =
  confirm("Do you want to continue?");

console.log(wantsToContinue);
```

### Prompt

```typescript
const learnerName: string | null =
  prompt("What is your name?");

if (learnerName !== null) {
  console.log(`Hello, ${learnerName}!`);
} else {
  console.log("Input cancelled.");
}
```

`prompt()` returns `null` when the user cancels. Its return value is not always a string.

### Browser vs. Node.js

These dialog functions are browser APIs.

They are not available as built-in browser dialogs when running a normal Node.js script with:

```powershell
node popup.js
```

To practice them, I compile the TypeScript and load the generated JavaScript in an HTML page.

## 14. Loading JavaScript in HTML

For a browser exercise, the files can be organized as:

```text
Variables/
├── popup.ts
├── popup.js
└── variable.html
```

Compile:

```powershell
tsc.cmd popup.ts
```

Load the generated `.js` file in HTML:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>TypeScript Practice</title>
</head>
<body>
  <h1>TypeScript Browser Exercise</h1>

  <script src="./popup.js"></script>
</body>
</html>
```

Open the HTML file in a browser.

The script reference must match the JavaScript filename and its location relative to the HTML file.

For this basic setup, I load `.js`, not the original `.ts` file.

Messages from `console.log()` appear in the browser's developer console when the script runs in the browser.

## 15. Comments

Comments explain code and are not executed.

### Single-Line Comment

```typescript
// Store the number of completed exercises.
const completedExercises: number = 5;
```

### Multi-Line Comment

```typescript
/*
  This example demonstrates a boolean value.
  A boolean can be true or false.
*/
const isReady: boolean = true;
```

I aim to write comments that explain intent or a learning point rather than repeat every line of code.

## 16. Enums

An enum defines a named set of values.

### Numeric Enum

```typescript
enum TestStatus {
  NotRun,
  Passed,
  Failed,
  Blocked
}

console.log(TestStatus.NotRun); // 0
console.log(TestStatus.Passed); // 1
```

Without explicit initializers, the first numeric member starts at zero and the following members increment.

### String Enum

```typescript
enum DaysOfWeek {
  Monday = "Monday",
  Tuesday = "Tuesday",
  Wednesday = "Wednesday",
  Thursday = "Thursday",
  Friday = "Friday",
  Saturday = "Saturday",
  Sunday = "Sunday"
}

console.log(DaysOfWeek.Monday); // Monday
console.log(DaysOfWeek.Friday); // Friday
```

String enums use explicit string values, making the displayed values easy to read.

## 17. Union Types

A union type allows a value to have more than one specified type.

```typescript
let referenceId: number | string = 1001;

referenceId = "TC-1001";
```

Both assignments are valid because the variable permits `number` or `string`.

A boolean is not included:

```typescript
// Incorrect: boolean is not part of this union.
// referenceId = true;
```

### Checking the Current Type

Before using an operation that applies to only one member of the union, I can check the type.

```typescript
function formatReference(reference: number | string): string {
  if (typeof reference === "string") {
    return reference.toUpperCase();
  }

  return reference.toString();
}

console.log(formatReference("tc-1001")); // TC-1001
console.log(formatReference(1001));      // 1001
```

This is an introductory example of type narrowing.

## 18. My First Assignment

My first assignment combined:

- A whole number.
- A decimal number.
- A string.
- A string enum containing the days of the week.
- Console output.

```typescript
// Number and string variables.
const wholeNumber: number = 20;
const decimalNumber: number = 3.14;
const message: string = "Success is the best revenge.";

// Days of the week.
enum DaysOfWeek {
  Monday = "Monday",
  Tuesday = "Tuesday",
  Wednesday = "Wednesday",
  Thursday = "Thursday",
  Friday = "Friday",
  Saturday = "Saturday",
  Sunday = "Sunday"
}

// Display the values.
console.log(wholeNumber);
console.log(decimalNumber);
console.log(message);

console.log(DaysOfWeek.Monday);
console.log(DaysOfWeek.Tuesday);
console.log(DaysOfWeek.Wednesday);
console.log(DaysOfWeek.Thursday);
console.log(DaysOfWeek.Friday);
console.log(DaysOfWeek.Saturday);
console.log(DaysOfWeek.Sunday);
```

### Compile and Run

```powershell
tsc.cmd firstassignment.ts
node firstassignment.js
```

### Expected Output

```text
20
3.14
Success is the best revenge.
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
Sunday
```

The original practice used `var`. This notes version uses `const` because these variables are not reassigned.

## 19. Errors I Encountered and What I Learned

### File Not Found

**Example:**

```text
File 'variables.ts' not found.
```

**Cause in my exercise:** The terminal was in the parent folder, while the file was inside `Variables`.

**Solution:**

```powershell
cd Variables
tsc.cmd variables.ts
```

The terminal must point to the correct folder, or the command must provide the correct file path.

### Compiler Command Not Found

**Example:**

```text
tsc.cmd is not recognized
```

**What I learned:** Installing a tool and making it discoverable in a terminal are separate concerns.

My existing VS Code terminal did not have the required tool locations available.

A temporary PowerShell adjustment used during troubleshooting was:

```powershell
$env:Path += ";C:\Program Files\nodejs;$env:APPDATA\npm"
```

This applied only to that terminal session and matched the installation locations on my computer.

### PowerShell Script Policy Error

**Example:**

```text
tsc.ps1 cannot be loaded because running scripts is disabled
```

**Solution used in my setup:**

```powershell
tsc.cmd variables.ts
```

I did not need to change the script execution policy for this workflow.

### Incorrect Boolean Assignment

```typescript
// Incorrect:
// const isCompleted: boolean = "completed";

// Correct:
const isCompleted: boolean = false;
```

A string does not become a boolean merely because the variable is declared as `boolean`.

### Missing Parenthesis

Incorrect:

```typescript
// console.log technologies[0]);
```

Correct:

```typescript
console.log(technologies[0]);
```

The value to display belongs inside the parentheses of `console.log(...)`.

### Missing Colon Before a Type

Correct declaration:

```typescript
const product: any = {
  productId: 1
};
```

The type annotation uses a colon, followed by the assignment operator for the value.

### Old JavaScript Output

**Problem:** The terminal displayed previous output after I changed the TypeScript file.

**Lesson:** Save and compile before running the JavaScript again.

Also, an existing JavaScript file can still run even when the current TypeScript source contains errors.

## 20. Useful Terminal Commands

These examples are for PowerShell on Windows.

| Command | Purpose |
|---|---|
| `Get-Location` | Show the current folder |
| `dir` | List files and folders |
| `cd Variables` | Enter the Variables subfolder |
| `cd ..` | Move to the parent folder |
| `node --version` | Check the Node.js version |
| `npm.cmd --version` | Check the npm version |
| `tsc.cmd --version` | Check the TypeScript compiler version |
| `tsc.cmd variables.ts` | Compile a TypeScript file |
| `node variables.js` | Run the generated JavaScript |
| `cls` | Clear the terminal display |

Clearing the terminal does not delete source files.

## 21. Key Takeaways

- TypeScript helps identify type-related mistakes before execution.
- Both whole numbers and decimals use the `number` type.
- `boolean` values are `true` and `false`, without quotation marks.
- `any` offers flexibility but reduces type-checking protection.
- Arrays use zero-based indexes.
- `Array<string>` and `string[]` describe arrays of strings.
- Union types allow a defined set of alternative types.
- Enums provide names for related values.
- Browser dialogs require a browser environment.
- TypeScript source and generated JavaScript are different files.
- Saving, compiling, and running are separate steps.
- Compiler errors and runtime output answer different questions.

## 22. Next Learning Steps

- Practice operators.
- Write conditional statements.
- Use loops.
- Explore objects and arrays in more detail.
- Create typed functions.
- Continue recording useful errors and their solutions.

## 23. Attribution

These are independent personal study notes based on my learning experience with the linked Udemy course.

They are not official course documentation and do not reproduce paid lesson materials or downloadable solutions.

All examples use fictional or nonconfidential data.
