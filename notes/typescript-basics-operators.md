# TypeScript Basics – Operators

Personal notes from **Section 3: Operators** of my Udemy TypeScript course.

## Arithmetic

| Operator | Purpose | Example |
|---|---|---|
| `+` | Addition | `10 + 5` → `15` |
| `-` | Subtraction | `10 - 5` → `5` |
| `*` | Multiplication | `10 * 5` → `50` |
| `/` | Division | `10 / 5` → `2` |
| `%` | Remainder | `10 % 5` → `0` |

## Assignment

`=` assigns a value. Compound operators combine an operation with assignment: `+=`, `-=`, `*=`, `/=`, `%=`.

```typescript
let num1: number = 10;
let num3: number = 2;

num3 %= num1; // Equivalent to num3 = num3 % num1
console.log(num3); // 2
```

## Comparison

Comparisons return `true` or `false`.

```typescript
let value: number = 40;

console.log(value === 30); // false: strictly equal
console.log(value !== 30); // true: strictly unequal
console.log(value > 30);   // true
console.log(value < 30);   // false
console.log(value >= 30);  // true
console.log(value <= 30);  // false
```

**Reminder:** `=` assigns; `===` compares without type conversion.

## Logical

For boolean expressions:

- `&&` — AND: both conditions must be true.
- `||` — OR: at least one condition must be true.
- `!` — NOT: reverses the boolean value.

```typescript
console.log((10 > 20) && (20 > 5));    // false
console.log((10 > 20) || (20 > 5));    // true
console.log((10 > 20) || (4 > 5));     // false
console.log(!((10 > 20) && (20 > 5))); // true
```

## Ternary

A compact conditional expression:

```text
condition ? valueIfTrue : valueIfFalse
```

```typescript
let x: number = 20;
let y: number = 10;

console.log(
  x > y ? "x is greater than y" : "x is not greater than y"
);
// x is greater than y
```

## Practice Files

`arithmetic.ts`, `assignment.ts`, `comparison.ts`, `logical.ts`, and `ternary.ts`.

From the exercise folder, compile and run a file:

```powershell
tsc.cmd arithmetic.ts
node arithmetic.js
```

Examples are separate snippets. Save changes before compiling.
