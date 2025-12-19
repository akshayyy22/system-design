Core ideas of Chapter 4  
- Comments are a necessary evil: prefer expressing intent in code; comments exist mainly to cover expressiveness failures.[1]
- Many comments become lies over time; stale or redundant comments are worse than none.[1]
- Use a few precise, high-value comments; most “explanations” should instead be refactoring and better naming.[1]

## Rules / principles to remember  
- “Don’t comment bad code – rewrite it”: fix the code instead of explaining around its weaknesses.[1]
- Prefer self-explanatory code: replace explanation comments with better names, smaller functions, and clearer structure (e.g., `isEligibleForFullBenefits`).[1]
- Treat comments as a last resort: write them only when intent truly cannot be made obvious in code.[1]
- Good comment types:  
  - Legal headers / license notices at file top.[1]
  - Brief, accurate intent or rationale that is not obvious from code (e.g., “SimpleDateFormat is not thread-safe, create per-use”).[1]
  - TODOs for specific, real follow-ups (ideally searchable by tooling).[1]
  - Amplification/warning comments where a subtle detail is critical.[1]
  - Javadoc for public APIs that are used externally.[1]
- Bad/smelly comment types (avoid):  
  - Redundant comments that restate code (“Returns the day of the month.”).[1]
  - “Mumbling” or vague comments that do not clearly state behavior or rationale.[1]
  - Misleading or outdated comments that no longer match code.[1]
  - Mandated per-method/per-field comments that add noise.[1]
  - Journal/change-log comments; use VCS history instead.[1]
  - Noise like “Default constructor.”, “The name.”, or auto-Javadoc for internal code.[1]
  - Commented-out code; delete it and rely on version control.[1]
  - HTML-heavy comments intended for docs; doc tools should add formatting, not developers.[1]
- Never use a comment where a function/variable can express the same idea more clearly; refactor instead.[1]

## What is NOT important / can be skimmed  
- Long historical example modules (like `GeneratePrimes` with heavy comments) beyond grasping what typical comment anti-patterns look like.[1]
- Detailed per-line examples of bad Javadocs from Tomcat/FitNesse; retain the patterns, not the specifics.[1]
- Extended narrative about specific libraries (JUnit 4, old test styles) except the brief rules on when to use or avoid comments.[1]

## Practical takeaways – impact on how you write code  
- In PRs, treat unnecessary comments as smells: ask “Can this be expressed with better naming or a helper?” and push for code changes instead of prose.[1]
- Aggressively remove commented-out code, redundant Javadocs on internal methods, and noise comments when touching a file; rely on Git for history.[1]
- When you *do* write a comment, make it: short, precise, about *why* (rationale, constraints) or non-obvious consequences; avoid restating the “what.”[1]
- Restrict formal Javadoc-style comments to modules that are actual external/public APIs; keep internal services documented mainly via clean code and tests.[1]
- Use TODO comments sparingly and make them actionable (e.g., `TODO: replace O(n^2) search with indexed lookup after feature X ships`).[1]

## Interview-ready summaries  
- “Chapter 4 of Clean Code says comments are a necessary evil: most should be eliminated by making code self-explanatory, and the few that remain must be precise, stable, and focused on intent or constraints rather than restating code.”[1]
- “The chapter’s key idea is that inaccurate, redundant, or noisy comments are harmful; professionals primarily communicate through clear code, using comments only for legal notices, essential rationale, and public API documentation.”[1]

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/83858393/2188aeab-6f3a-42d2-b093-5de3959a6b88/clean-code.pdf)