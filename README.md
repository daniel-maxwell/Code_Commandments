# Coding Style Rules

## Control Flow

**Use Simple and Explicit Control Flow**

- Avoid complex or implicit control structures.
- Do not use recursion; ensure all executions are bounded.

**Centralize Control Flow and State Manipulation**

- Keep control flow (`if`, `switch`) in parent functions.
- Maintain state in local variables; use helper functions to compute changes.

**Use Positive Assertions and Conditions**

- State invariants positively.
- Break down complex conditions into simple, nested `if`/`else` branches.

**Add Braces to Control Structures**

- Even for single-line statements, use braces to prevent errors during code modifications.

---

## Limits and Bounds

**Limit Everything**

- Set fixed upper bounds on loops and queues to prevent infinite loops or latency spikes.

**Avoid Dynamic Memory Allocation After Initialization**

- Allocate all memory statically at startup to prevent unpredictable behavior.

---

## Type Usage

**Use Explicitly-Sized Types**

- Use types like `uint32_t`; avoid architecture-specific types like `size_t`.

---

## Assertions

**Employ Assertions Generously**

- Assert all function arguments, return values, preconditions, postconditions, and invariants.
- Aim for at least two assertions per function.
- Pair assertions by adding them in multiple code paths.

**Split Compound Assertions**

- Prefer `assert(a); assert(b);` over `assert(a && b);` for clarity and precise error information.

**Assert Compile-Time Relationships**

- Use compile-time assertions to check invariants and type sizes before execution.

---

## Memory Management

**Construct Objects In-Place**

- Initialize large structs in place using pointers to eliminate extra allocations.

**Pass Large Objects by Reference**

- For objects larger than 16 bytes, pass them as `const &` to avoid unnecessary copying.

**Avoid Variable Duplication and Aliasing**

- Do not duplicate variables or create aliases that can cause state inconsistencies.

---

## Variable Scope and Usage

**Declare Variables in the Smallest Possible Scope**

- Minimize the number of variables in scope to reduce misuse.

**Minimize Variable Scope and Lifetime**

- Declare variables close to where they are used.
- Limit their lifetime to reduce errors.

---

## Function Design

**Restrict Function Length**

- Limit functions to a maximum of 70 lines to encourage better structure.

**Design Functions with Clear Shape**

- Functions should have few parameters, a simple return type, and substantial logic within.

**Use Simple Function Signatures**

- Simplify return types to reduce complexity at the call site.

---

## Error Handling

**Handle All Errors**

- Ensure all errors are properly handled and tested to prevent catastrophic failures.

**Heed Compiler Warnings**

- Use the compiler's strictest settings and address all warnings promptly.

---

## Naming Conventions

**Use Meaningful Names**

- Choose names that accurately describe their purpose.
- Use `snake_case` for functions, variables, and files.
- Avoid unnecessary abbreviations.
- Use proper capitalization for acronyms (e.g., `HTTPResponse`, not `HttpResponse`).

**Include Units or Qualifiers in Variable Names**

- Add units like `_ms` for milliseconds at the end of variable names (e.g., `latency_ms`).

**Align Related Variable Names**

- Use names with similar lengths to improve readability and alignment in the code.

**Prefix Helper Functions with Caller Name**

- Name helper functions to reflect their calling function (e.g., `readData()` and `readDataCallback()`).

**Place Callbacks Last in Parameters**

- Position callback functions at the end of parameter lists to mirror control flow.

**Avoid Overloading Names**

- Do not reuse names for different concepts in varying contexts to prevent confusion.

---

## Comments and Documentation

**Write Descriptive Comments and Commit Messages**

- Explain the reasoning behind your code.
- Use comments to document logic and decisions.

**Follow Comment Conventions**

- Write comments as full sentences with proper punctuation.
- Start with a capital letter and end with a period.

---

## Code Formatting

**Format Code Consistently**

- Run your code formatter regularly.
- Use 4 spaces for indentation for better readability.
- Limit all lines to a maximum of 100 characters.
- Always use braces with `if` statements unless the statement fits on one line.

---

## Dependencies and Tooling

**Avoid Unnecessary Dependencies**

- Rely only on essential libraries (e.g., the C++ standard library) to reduce risks.

**Standardize Tooling**

- Use consistent tools (e.g., C++ for scripts) to minimize complexity and improve team efficiency.

---

## General Practices

**Group Resource Allocation and Deallocation**

- Use newlines to separate allocation and deallocation code for clarity.

**Be Cautious with Indexes and Counts**

- Treat indexes, counts, and sizes as distinct types with clear conversion rules.
- Include units in variable names for clarity.

**Express Intent in Division and Rounding**

- Use functions that specify rounding behavior to avoid off-by-one errors.
