Chapter 15 dissects JUnit's `ComparisonCompactor`—a module that highlights string comparison failures (e.g., `ABCDE` vs `ABXDE` → `...BXD...`)—showing how even excellent code can be incrementally improved via the **Boy Scout Rule**.[1]

## Original code analysis
- **Strengths**: 100% test coverage, small functions, clear structure, topological ordering (callers above callees).[1]
- **Minor issues** (`fContextLength` → `contextLength`, redundant `this.expected`, unencapsulated conditionals).[1]
- **Tests as spec**: Comprehensive `ComparisonCompactorTest` covers edge cases (nulls, overlaps, context limits).[1]

## Refactoring steps (iterative improvements)
```
1. Remove Hungarian Notation (fPrefix → prefixLength) [file:1]
2. Extract shouldNotCompact() → Encapsulate early return [file:1]  
3. Rename compact() → formatCompactedComparison() [file:1]
4. Extract compactExpectedAndActual() → Single responsibility [file:1]
5. findCommonPrefixAndSuffix() → Expose temporal coupling [file:1]
6. Eliminate magic "1"s → charFromEnd(), suffixOverlapsPrefix() [file:1]
7. Inline redundant ifs → Simpler compactString() [file:1]
```

## Key clean code applications
- **G28**: Encapsulate conditionals (`shouldBeCompacted()`).[1]
- **N1/N4**: Rename for clarity (`suffixIndex` → `suffixLength`, `compactExpected`).[1]
- **G29**: Prefer positives over negatives (`shouldBeCompacted()`).[1]
- **G31**: Expose temporal coupling (combined prefix/suffix finder).[1]
- **G33**: Eliminate magic numbers (via `charFromEnd()`).[1]
- **G9**: Functions do one thing (`compactString()` composes fragments).[1]

## Final structure
```
Analysis functions (top)
├── shouldBeCompacted()
├── findCommonPrefixAndSuffix()
│   ├── findCommonPrefix()
│   └── suffixOverlapsPrefix()
└── charFromEnd()

Synthesis functions (bottom)
├── formatCompactedComparison()
├── compactString()
├── computeCommonPrefix()
├── deltaString()
├── computeCommonSuffix()
└── endingEllipsis()
```
**Result**: Even cleaner, with analysis → synthesis flow, no magic numbers, explicit intent.[1]

## What to skim
- Full before/after listings; focus on transformation principles and test-driven validation.[1]

## Practical takeaways
- **Even great code improves**: JUnit authors wrote professional code; still worth ~15 micro-refactors.[1]
- **Refactoring is iterative**: Some extractions later inlined; trial/error converges on optimal.[1]
- **Tests enable boldness**: 100% coverage let aggressive changes happen safely.[1]

## Interview summary
"Chapter 15 applies all prior principles to JUnit's already-clean `ComparisonCompactor`: removes encoding, extracts intent-revealing methods, eliminates magic numbers, and topological-sorts analysis before synthesis—proving the Boy Scout Rule works even on excellent code."[1]

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/83858393/2188aeab-6f3a-42d2-b093-5de3959a6b88/clean-code.pdf)