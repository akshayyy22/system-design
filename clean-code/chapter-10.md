Core ideas of Chapter 10  
- Classes should be small and focused on **one responsibility** (SRP): one reason to change.[1]
- High **cohesion**: methods should work on the same small set of instance variables.[1]
- Organize classes for change: isolate unstable parts, depend on abstractions, use small classes to minimize modification risk.[1]

## Rules / principles to remember  
- **Single Responsibility Principle (SRP)**: A class should have only one reason to change.[1]
  - If it handles UI + persistence + reporting → split.[1]
- **Classes should be small**: Measure by responsibilities, not lines of code.[1]
  - "God classes" like `SuperDashboard` with 70 methods = smell.[1]
- **High cohesion**:  
  - Few instance variables, each method uses most of them.  
  - Low cohesion → split into multiple classes.[1]
- **Class organization** (Java convention):  
  ```
  public static constants
  private static variables  
  private instance variables
  public functions
  private utility functions (right after public callers)
  ```
- **Encapsulation**: Keep variables private; loosen only for testing (protected/package scope).[1]
- **Organize for change**:  
  - Extract unstable parts into separate classes (`Version` from `SuperDashboard`).[1]
  - Use inheritance/polymorphism: `Sql` → `SelectSql`, `InsertSql`, etc. (Open-Closed Principle).[1]
- **Dependency Inversion**: Depend on abstractions (`StockExchange` interface), not concrete `TokyoStockExchange`.[1]

## What is NOT important / can be skimmed  
- Full `PrintPrimes` → refactored version comparison; retain only the pattern: one big function → `PrimePrinter` + `PrimeGenerator` + `RowColumnPagePrinter`.[1]
- Detailed `Sql` → `SelectSql`/`InsertSql` hierarchy once OCP via inheritance is clear.[1]
- `Stack` cohesion example; grasp that all methods share the same 2 variables.[1]

## Practical takeaways – how this changes your code  
- **Spot SRP violations**:  
  ```
  If class name needs "and/or" → too many responsibilities
  If >5-7 public methods → likely too big
  If private methods only used by subset → extract class
  ```
- **Refactor god classes**: Extract cohesive groups into small classes with descriptive names.[1]
- **Maintain high cohesion**: When breaking functions, promote shared variables → new class fields.[1]
```java
// Before: God class with 20 methods
class OrderProcessor {
    // UI, persistence, reporting, validation...
}

// After: SRP classes
class OrderValidator { }
class OrderPersister { }
class OrderReporter { }
class OrderUI { }
```
- **Design for testability**: Inject dependencies, use interfaces for external collaborators.[1]

## Interview-ready summaries  
- "Chapter 10 of Clean Code emphasizes SRP: classes should have one responsibility, high cohesion, and be organized for change—small, focused classes with few instance variables that depend on abstractions rather than concrete details."[1]
- "Key insight: breaking large classes into many small, single-purpose ones reduces risk of change, improves testability via dependency inversion, and maintains high cohesion where methods share a small set of closely related instance variables."[1]

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/83858393/2188aeab-6f3a-42d2-b093-5de3959a6b88/clean-code.pdf)