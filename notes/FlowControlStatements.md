# Section 4: Flow Control Statements

Personal notes from **Section 4** and the exercises completed in VS Code.

## Conditions

- An `if / else if / else` ladder checks conditions from top to bottom. Only the first matching branch runs.
- `&&` means both conditions must be true; `||` means at least one must be true.
- In `ifelse.ts`, strict comparisons such as `x > y && x > z` find a unique largest value. Ties need separate conditions; a final `else` does not automatically mean all values are equal.
- A `switch` compares one value with its `case` labels. Use `break` to stop at the matched case and `default` for values with no match.

## Input and simple validation

- In a browser, `prompt()` returns text (or `null`), so convert and validate input before using it. `parseInt(value, 10)` converts an integer string; `isNaN()` checks whether conversion failed.
- The remainder operator helps classify numbers: `n % 2 === 0` means even; `n % 5 === 0` means a multiple of 5.
- `indexOf()` returns `-1` when text is not found. The email example checks for `@` and `.`; this is only a basic presence check, not full email validation.
- `charCodeAt(0)` gets the first character's code. Checking codes 65–90 accepts an uppercase English letter, but checks only the first character.

## Loops

- Use a `for` loop when the counter setup, condition, and update fit together. A `while` loop repeats while its condition is true.
- Update the counter on every path through a `while` loop. If using `continue`, update it before continuing or the loop may never end.
- `continue` skips the current iteration; `break` exits the loop.
- In Assignment 3, numbers divisible by 5 are skipped in both loops. Therefore, input `10` is omitted because `10 % 5 === 0` triggers `continue`.

## VS Code setup and running in a browser

- Node.js provides npm. The project uses npm packages (listed in `package.json` and `package-lock.json`; installed files are in `node_modules`). TypeScript can be installed locally with `npm install --save-dev typescript` and compiled with `npx tsc`.
- TypeScript compiles to JavaScript; the browser runs the generated `.js`, not the `.ts` file.
- Runtime matters: browser code can use `window.prompt()`; Node.js code uses APIs such as `readline`. The loop assignment originally used Node's `readline`, so it was changed to browser `prompt()`.
- For the browser build, `tsconfig.json` must emit JavaScript that works as a regular browser script. CommonJS output can reference `exports`, which is unavailable in a plain browser script. Load the generated file from `index.html`, then open the page in a browser.

## Working with AI in VS Code

AI helped adapt the assignment to the browser, update the TypeScript build settings, and explain why `10` was missing. Ask it to explain the condition and trace a specific input before changing code; then rebuild and check the generated JavaScript and browser output.

**Practice files:** `ifelse.ts`, `switch.ts`, `assignment2.ts`, `email.ts`, `pwdvalidator.ts`, `while.ts`, and `assignment3.ts`.
