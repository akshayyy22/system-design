Chapter 16 applies the **"First make it work, then make it right"** principle to `SerialDate` (renamed `DayDate`), a date utility from JCommon library.[1]

## Phase 1: Make it work (add tests, fix bugs)
- **Coverage**: Original tests covered 50%; added comprehensive suite → 92%.[1]
- **Bug fixes** (via failing tests):  
  - `getFollowingDayOfWeek` boundary error (Dec 25 → Dec 25 instead of Jan 1).[1]
  - `getNearestDayOfWeek` always past (fixed adjust logic).[1]
  - Case-insensitive parsing, invalid args throw exceptions.[1]

## Phase 2: Make it right (systematic refactoring)
**Top-down cleanup** (line-by-line, tests always green):[1]

### Names & Structure
```
SerialDate → DayDate (hides ordinal impl) [file:1]
toSerial → getOrdinalDay [file:1]
addDays → plusDays [file:1]
getYYY → getYear [file:1]
```

### Constants → Enums
```
MonthConstants → Month enum [file:1]
Day codes → Day enum [file:1]
Include flags → DateInterval [file:1]
Week ranges → WeekdayRange [file:1]
```

### Extract & Move
```
createInstance → DayDateFactory (ABSTRACT FACTORY) [file:1]
Month funcs → Month enum [file:1]
Day parsing → Day enum [file:1]
DateUtil (static utils) [file:1]
```

### Eliminate duplication & smells
```
G5: Merge duplicate ifs [file:1]
G9: Delete dead/unused code [file:1]
G12: Remove redundant Javadocs, finals [file:1]
G14: FEATURE ENVY → enum methods [file:1]
G19: EXPLAINING TEMPORARIES [file:1]
```

## Key transformations
```
BEFORE: 500+ lines, magic numbers, static methods, int flags
AFTER:  ~250 lines, enums, instance methods, clear names
```

**Factory hides impl**: `DayDateFactory.makeDate()` defaults to `SpreadsheetDateFactory`.[1]

## What to skim
- Full before/after listings; focus on refactor decisions and principles applied.[1]

## Practical takeaways
- **Professional review**: Critique even good code constructively.[1]
- **Test-first fixes**: Write failing tests for expected behavior → fix → refactor.[1]
- **Enums over ints**: Parsing, validation, constants all handled polymorphically.[1]
- **Abstract away impl**: Users see `DayDate`, not ordinal arithmetic.[1]

## Interview summary
"Chapter 16 refactors JCommon's `SerialDate` from working-but-ugly (50% test coverage, magic numbers, static pollution) to clean `DayDate`: adds tests/fixes bugs first, then extracts enums/factory, eliminates duplication, applies all prior principles—shrinking 500→250 lines while improving extensibility."[1]

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/83858393/2188aeab-6f3a-42d2-b093-5de3959a6b88/clean-code.pdf)