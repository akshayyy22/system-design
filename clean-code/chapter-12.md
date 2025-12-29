Chapter 12 (“Emergence”) explains how good design can **emerge** step by step from simple rules, instead of being fully designed up front.[1]

## Simple Design: 4 rules (in order)

Kent Beck’s four rules of simple design, as presented here, are:[1]

1. **Runs all the tests**  
   - The system must be fully testable and all tests must pass.[1]
   - Pushing for testability naturally leads to small, cohesive, loosely coupled classes (SRP, DIP, DI, etc.).[1]

2. **No duplication**  
   - Duplication is the primary enemy of good design; it increases work, risk, and complexity.[1]
   - Remove duplication at all levels: lines, methods, algorithms, and even conceptually (e.g., `isEmpty()` implemented via `size() == 0`).[1]

3. **Expressive**  
   - Code should clearly express programmer intent: good names, small functions, clear structure, and revealing tests.[1]
   - Well-written unit tests act as documentation-by-example and help describe design at a higher level.[1]

4. **Minimal classes and methods**  
   - Avoid dogmatic explosion of tiny classes/methods (e.g., forced interfaces for every class, over-splitting data/behavior).[1]
   - Keep class/method count low, but only after tests, no duplication, and expressiveness are satisfied (this rule is lowest priority).[1]

## How the rules drive emergent design

- Writing tests first (Rule 1) forces better separation of concerns and drives towards SRP and low coupling.[1]
- Continuous refactoring to remove duplication (Rules 2 & 4) uncovers abstractions, patterns (e.g., TEMPLATE METHOD), and reuse “in the small” that later scales to reuse “in the large.”[1]
- Focusing on expressiveness (Rule 3) pushes you to rename, split, and reorganize until code reads like an explanation of the domain.[1]

## Practical habits from this chapter

- After every small change:  
  1) run tests,  
  2) refactor for duplication and clarity,  
  3) keep functions/classes small but not absurdly fragmented.[1]
- Look for tiny duplicated sequences and extract methods, then possibly move them to better classes as they become reusable.[1]
- Use known patterns (like TEMPLATE METHOD) when you see similar algorithms that differ only in a few steps.[1]

## Interview-style summary

- “Chapter 12 describes emergent design via four rules: pass all tests, eliminate duplication, express intent, and minimize classes/methods (in that priority order). Following these rules while refactoring lets a clean architecture emerge incrementally, without big design up front.”[1]

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/83858393/2188aeab-6f3a-42d2-b093-5de3959a6b88/clean-code.pdf)