Core ideas of Chapter 2  
- Names are a primary tool for making code readable; good names encode intent, not mechanics.[1]
- Names must be precise, pronounceable, and searchable; avoid noise, ambiguity, and cleverness.[1]
- Consistent naming patterns reduce cognitive load; inconsistent or slightly varied names are active disinformation.[1]

## Rules / principles to remember  
- Use intention-revealing names: a good name lets you infer what the variable/class/function is for without reading implementation.[1]
- Avoid disinformation: do not use names that can be confused with other concepts (e.g., `O` vs `0`, `l` vs `1`, misleading domain terms).[1]
- Make meaningful distinctions: if two names differ, the difference must carry semantic meaning, not just extra numbers or “Info/Data/Object.”[1]
- Avoid noise words: skip redundant suffixes like `Data`, `Info`, `Variable`, `Object`, `Table` unless they convey a real, consistent distinction.[1]
- Use pronounceable names: prefer `generationTimestamp` over `genymdhms`; code is discussed verbally in reviews and design talks.[1]
- Use searchable names: avoid magic numbers and cryptic identifiers; prefer constants like `MAX_CLASSES_PER_STUDENT` over raw `7`.[1]
- Avoid unnecessary encodings: do not use Hungarian notation, member prefixes, or type-encoded names in modern IDE-heavy environments.[1]
- Keep class names as nouns (e.g., `Customer`, `AccountService`) and method names as verbs/verb-phrases (e.g., `calculateTotal`, `saveCustomer`).[1]
- Don’t be cute or punny: avoid jokes, slang, or ambiguous wordplay; favor straightforward business/domain terminology.[1]
- Pick one word per concept across the codebase: if you use `retrieve`, do not randomly mix `get`, `fetch`, `load` for the same operation type.[1]
- Avoid mental mapping: do not force readers to remember that `a1` means “source” and `a2` means “destination”; name things directly.[1]
- Add meaningful context when needed (e.g., `address` → `billingAddress`, `shippingAddress`), but avoid gratuitous prefixes/suffixes that add no real context.[1]

## What is NOT important / can be skimmed  
- The detailed anecdotes about bad names and jokes around mispronunciations; keep only the rule (use pronounceable, clear names).[1]
- Fine-grained commentary on specific Java/IDE habits (e.g., old prefix conventions) beyond the core rule: avoid manual naming encodings today.[1]
- Overly specific examples with contrived classes and methods; you only need 2–3 representative patterns to apply the principles generally.[1]

## Practical takeaways for how you write code  
- When naming, first write what you’d say in plain English, then compress slightly: “maximum classes per student” → `maxClassesPerStudent`.[1]
- Replace magic numbers and cryptic variables with named constants and intention-revealing identifiers whenever you touch legacy code.[1]
- Standardize vocabulary within a codebase: choose `Customer` vs `Client`, `save` vs `persist`, and stick to it across services and modules.[1]
- During reviews, treat poor naming as a correctness issue, not a cosmetic one; request renames that remove ambiguity or noise.[1]
- Use short, single-letter variables only in tiny, obvious scopes (loop counters in 3–5 line loops); otherwise prefer descriptive names.[1]

## 1–2 interview-ready summaries  
- “Chapter 2 of Clean Code emphasizes that meaningful names are the first line of clean code: they must reveal intent, avoid ambiguity and noise, be pronounceable, searchable, and consistently used across the codebase.”[1]
- “The chapter’s core message is that naming is not cosmetic: good names reduce cognitive load and bugs, so developers should systematically use intention-revealing, domain-consistent, and non-encoded names instead of cryptic or cute ones.”[1]

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/83858393/2188aeab-6f3a-42d2-b093-5de3959a6b88/clean-code.pdf)