# TypeScript Learning Journey

Learning notes, coding exercises, and personal practice projects created while studying TypeScript.

**Author:** Dana Fischer  
**Learning Resource:** [TypeScript for Beginners – Udemy](https://www.udemy.com/course/typescript-for-beginners/)  
**Instructor:** Bharath Thippireddy  
**Repository Type:** Personal Learning Portfolio  

---

## 1. About This Repository

This repository documents my TypeScript learning journey.

It brings together:

- Notes written in my own words.
- Small examples demonstrating language concepts.
- Practical exercises.
- Common mistakes and their solutions.
- Personal projects applying TypeScript to testing-related scenarios.

Progress is tracked through the checklist below. Topics are marked complete only after reviewing the material and completing the associated practice.

## 2. Learning Goals

My goals are to:

- Understand how TypeScript adds type checking to JavaScript.
- Write functions with clear input and return types.
- Model data using types, interfaces, and classes.
- Understand object-oriented programming concepts.
- Recognize and resolve common compiler errors.
- Build a foundation for future test automation work.

## 3. Course Reference

**Course:** TypeScript for Beginners  
**Platform:** Udemy  
**Instructor:** Bharath Thippireddy  

[Open the course](https://www.udemy.com/course/typescript-for-beginners/)

The course is my primary learning resource. The structure of this repository is a personal study plan rather than an exact reproduction of the course sections.

Testing-related exercises are independent practice ideas.

## 4. Learning Roadmap

### TypeScript Foundations

- [ ] Understand the purpose of TypeScript.
- [ ] Understand the relationship between TypeScript and JavaScript.
- [ ] Try examples in the TypeScript Playground.
- [ ] Set up a local development environment.
- [ ] Compile and run a first TypeScript program.

### Variables and Data Types

- [ ] Use `let` and `const`.
- [ ] Work with strings, numbers, and booleans.
- [ ] Understand type annotations and type inference.
- [ ] Define typed arrays.
- [ ] Practice union types.
- [ ] Understand enums.
- [ ] Recognize how `any` reduces type-checking protection.

### Operators and Control Flow

- [ ] Practice arithmetic and comparison operators.
- [ ] Use logical operators.
- [ ] Write `if` / `else` conditions.
- [ ] Use `switch` statements.
- [ ] Practice loops.
- [ ] Use the ternary operator.

### Objects and Arrays

- [ ] Create object literals.
- [ ] Access and update properties.
- [ ] Work with arrays of objects.
- [ ] Practice array methods.
- [ ] Use object and array destructuring.

### Functions

- [ ] Define parameter and return types.
- [ ] Use optional parameters.
- [ ] Use default parameters.
- [ ] Practice rest parameters.
- [ ] Write arrow functions.
- [ ] Pass functions as arguments.
- [ ] Understand function overloads.

### Interfaces and Classes

- [ ] Define interfaces.
- [ ] Use interfaces to describe object structures.
- [ ] Create classes and constructors.
- [ ] Understand access modifiers.
- [ ] Practice encapsulation.
- [ ] Understand inheritance.

### Independent Practice

- [ ] Build a typed test-result summary.
- [ ] Create a small defect-filtering exercise.
- [ ] Calculate test execution metrics.
- [ ] Document compiler errors and lessons learned.
- [ ] Complete a personal mini-project.

## 5. Planned Repository Structure

The following folders will be added as exercises are completed.

```text
typescript-learning/
├── README.md
├── notes/
│   ├── typescript-basics.md
│   ├── functions.md
│   ├── interfaces-and-classes.md
│   └── common-errors.md
├── exercises/
│   ├── 01-variables-and-types/
│   ├── 02-control-flow/
│   ├── 03-objects-and-arrays/
│   ├── 04-functions/
│   └── 05-interfaces-and-classes/
└── projects/
    ├── test-results-summary/
    └── defect-filter/
```

This is the intended organization, not a list of completed deliverables.

## 6. Study Approach

For each topic, I plan to:

1. Study the relevant lesson.
2. Write a short explanation in my own words.
3. Recreate an example without copying the solution.
4. Change the example to explore different inputs.
5. Investigate compiler errors.
6. Save the exercise with a clear description.
7. Update the learning checklist.

Watching a lesson is the starting point. Completing an exercise demonstrates practical understanding.

## 7. Personal Practice Ideas

These exercises connect TypeScript fundamentals with my interest in software quality and testing.

### Exercise 1 – Test Result Model

**Goal:** Describe a test result using an interface and a union type.

```typescript
type TestStatus = "Passed" | "Failed" | "Blocked" | "Not Run";

interface TestResult {
  id: string;
  title: string;
  status: TestStatus;
  critical: boolean;
}

const exampleResult: TestResult = {
  id: "TC-001",
  title: "Validate invoice posting",
  status: "Passed",
  critical: true,
};

console.log(exampleResult);
```

**Practice tasks:**

- Create several test results.
- Filter failed tests.
- Identify critical tests that have not passed.
- Try an invalid status and inspect the compiler error.

### Exercise 2 – Test Execution Metrics

**Goal:** Practice typed functions and calculations.

```typescript
function calculatePassRate(
  passed: number,
  failed: number
): number | null {
  if (
    !Number.isInteger(passed) ||
    !Number.isInteger(failed) ||
    passed < 0 ||
    failed < 0
  ) {
    throw new Error("Test counts must be non-negative integers.");
  }

  const completed = passed + failed;

  if (completed === 0) {
    return null;
  }

  return (passed / completed) * 100;
}

console.log(calculatePassRate(95, 5)); // 95
console.log(calculatePassRate(0, 0));  // null: no completed tests
```

**Practice tasks:**

- Explain the return type.
- Display a rounded percentage.
- Handle the `null` result.
- Try negative and fractional inputs.
- Add a separate execution-completion calculation.

### Exercise 3 – Defect Filtering

**Goal:** Practice arrays, interfaces, and sorting.

Create a defect model containing:

- Defect ID.
- Description.
- Severity.
- Age in days.
- Current status.

Then:

- Filter unresolved defects.
- Group defects by severity.
- Sort by severity first and age second, oldest first.
- Identify defects older than 20 days.

### Exercise 4 – Simple Readiness Check

**Goal:** Practice conditions and boolean expressions.

Create a function that checks whether:

- All critical tests passed.
- No Critical or High defects remain.
- Required business approval is available.

Return a result explaining which checks passed or failed.

This is a programming exercise. It does not replace a real project Go/No-Go assessment.

## 8. Learning Log

Add a row after completing a study session.

| Date | Topic | Practice Completed | What I Learned | Next Step |
|---|---|---|---|---|
| YYYY-MM-DD | Topic studied | Exercise or example | Main takeaway | Follow-up action |

## 9. Common Errors and Lessons Learned

For useful mistakes, document:

- What I expected.
- The compiler error or observed behavior.
- Why the issue occurred.
- How I corrected it.
- What I would do differently next time.

Examples to explore include:

- Assigning the wrong type to a variable.
- Passing an incorrect argument to a function.
- Omitting a required interface property.
- Accessing an optional value without checking it.
- Confusing compile-time checking with runtime validation.

## 10. Definition of Done

A learning exercise is complete when:

- The code compiles using the exercise's documented setup.
- It produces the expected result.
- Relevant alternative inputs have been tried.
- I can explain the main concept in my own words.
- Important mistakes or limitations are documented.

## 11. Future Learning

After completing the fundamentals, possible next steps include:

- Deeper practice with narrowing and generics.
- Asynchronous programming.
- Working with API responses.
- Runtime validation of external data.
- Applying TypeScript in a test automation project.

These are future learning goals, not claims of completed skills or confirmed course coverage.

## 12. Attribution and Disclaimer

This is an independent personal learning repository.

The Udemy course is referenced as a learning resource. This repository is not affiliated with Udemy or the instructor.

Notes should be written in my own words. Paid course videos, slides, downloadable resources, and solution files should not be redistributed without permission.

Testing examples use fictional data and contain no confidential employer or client information.
