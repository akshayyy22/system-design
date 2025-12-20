Core ideas of Chapter 7  
- Error handling must not obscure core logic; clean code separates “happy path” from error paths clearly.[1]
- Exceptions are preferred over return codes; they keep callers cleaner and localize error-handling code.[1]
- Use unchecked exceptions in most application code to avoid signature cascades and broken encapsulation.[1]
- Never casually return or pass `null`; it multiplies checks and causes fragile code.[1]

## Rules / principles to remember  
- Use exceptions instead of error codes:  
  - Avoid `if (delete(...) != E_OK) ...` patterns; throw an exception and keep callers focused on business logic.[1]
- Write `try–catch–finally` first:  
  - Define the transactional scope, the cleanup, and the post-error consistent state before filling in the body.[1]
- Keep error handling separate:  
  - A function that handles errors should do only that; if `try` appears, it should usually be the first statement and nothing substantial should follow the `catch/finally`.[1]
- Use unchecked (runtime) exceptions by default:  
  - Checked exceptions cause upward “throws” pollution and break the Open–Closed Principle when low-level code changes.[1]
  - Reserve checked exceptions (if at all) for library boundaries where you want to force handling.[1]
- Provide context in exceptions:  
  - Include operation, key parameters, and cause: e.g., `new StorageException("Failed to retrieve section " + sectionName, e)`.[1]
- Define exception classes to match how callers catch:  
  - Group low-level exceptions behind a wrapper (e.g., `PortDeviceFailure`) when callers handle them the same way.[1]
  - Use distinct types only when you truly need different handling paths.[1]
- Wrap third-party APIs:  
  - Create adapter classes that translate vendor-specific exceptions into your own, minimizing external coupling and easing testing/mocking.[1]
- Define the normal flow:  
  - Use patterns like Special Case (e.g., `PerDiemMealExpenses`) so main logic reads linearly, without embedded “if error” branches.[1]
- Don’t return `null`:  
  - Prefer empty collections (`Collections.emptyList()`), Special Case objects, or throwing exceptions when something truly exceptional happens.[1]
- Don’t pass `null`:  
  - Treat `null` arguments as bugs; avoid APIs that rely on `null` signaling, or wrap them to eliminate `null` from your own surface.[1]

## What is NOT important / can be skimmed  
- Detailed historical discussion of checked vs unchecked exceptions; keep only the conclusion: unchecked in apps, checked rarely at library boundaries.[1]
- Long ACME/LocalPort and file-storage examples once the patterns are clear (wrap third-party APIs, define custom exception, use try-first TDD).[1]
- Verbose tests and incremental TDD story around the file retrieval example; retain only the idea of driving error handling via tests.[1]

## Practical takeaways – how this changes your code  
- For new code, design APIs that:  
  - Throw meaningful unchecked exceptions.  
  - Never require callers to pass or check for `null` in normal use.[1]
- Wrap I/O, DB, and external services in thin adapters that:  
  - Catch vendor/low-level exceptions,  
  - Translate them into a small, coherent set of domain-level exceptions.[1]
- Refactor “error-dominated” methods:  
  - Extract try–catch into small wrapper methods focused on error handling, keeping core logic clean and linear.[1]
- Use Special Case objects instead of sprinkling “if missing → use default” logic everywhere (e.g., per-diem meals, empty lists of employees).[1]
- In reviews, treat returning/passing `null` and large `if (errorCode)` blocks as smells that should be eliminated via exceptions and better abstractions.[1]

## Interview-ready summaries  
- “Chapter 7 of Clean Code argues that error handling is part of clean design: prefer exceptions over return codes, push error detection to boundaries, keep try–catch blocks small and focused, and avoid `null` as a control mechanism.”[1]
- “The chapter’s key message is to design for a clear happy path and robust error handling by using unchecked domain exceptions, wrapping third-party APIs, employing patterns like Special Case, and forbidding casual `null` returns or parameters.”[1]

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/83858393/2188aeab-6f3a-42d2-b093-5de3959a6b88/clean-code.pdf)