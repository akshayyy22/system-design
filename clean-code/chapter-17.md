Chapter 17 is a **reference list of 50+ code smells and heuristics** organized by category, cross-referenced to earlier chapters—use it as a checklist during code reviews and refactoring.[1]

## Top smells by category (most actionable)

### **Comments (C1-C5)**
- **C1**: Inappropriate info (author, dates, tickets → use source control/Jira).[1]
- **C2**: Obsolete comments (update or delete).[1]
- **C3**: Redundant (delete `i++` comments).[1]
- **C4**: Poorly written (grammar matters).[1]
- **C5**: Commented-out code (**DELETE**—git remembers).[1]

### **Environment (E1-E2)**
- **E1**: Build >1 step (`svn up && ant` → single command).[1]
- **E2**: Tests >1 step (one button/one command).[1]

### **Functions (F1-F4)**
- **F1**: >3 args (use objects/lists).[1]
- **F2**: Output args (return new objects).[1]
- **F3**: Flags (`save(force=true)` → `forceSave()`).[1]
- **F4**: Dead functions (delete).[1]

### **General (G1-G36)**
```
G5:  Duplication (DRY) ← #1 smell
G6:  Wrong abstraction level (base knows derivatives)
G9:  Dead code
G14: Feature envy (move methods to data owner)
G15: Selector args (split functions)
G20: Names don't describe side-effects
G28: Don't encapsulate conditionals (extract intent)
G30: Functions do >1 thing
G33: Magic numbers
G34: Mixed abstraction levels
```

### **Java (J1-J3)**
- **J3**: `int` constants → enums (parsing, validation).[1]

### **Names (N1-N7)**
```
N1:  Descriptive names
N4:  Unambiguous (no `doRename` when `renamePage` exists)
N6:  No Hungarian/encodings (`m_count` → `count`)
```

### **Tests (T1-T9)**
```
T1:  Insufficient coverage
T2:  Use coverage tools (Clover)
T3:  Don't skip trivial tests
T5:  Boundary conditions
```

## Quick-review checklist
```
☐ No commented-out code
☐ No duplication (>2 similar blocks)
☐ Functions <3 args, no flags
☐ Single abstraction level
☐ Descriptive names (no i++/temp)
☐ 100% test coverage (or justified gaps)
☐ No magic numbers
☐ Enums > int constants
☐ Single build/test command
```

## Usage tips
- **Daily**: Scan for G5 (duplication), C5 (dead code).[1]
- **Reviews**: Check F1-F3, N1, T1-T2.[1]
- **Refactoring**: G14 (envy), G34 (abstraction).[1]

## Interview summary
"Chapter 17 lists 50+ smells/heursitics (C1 dead comments, F3 flags, G5 duplication, etc.) as a clean code checklist—prioritize eliminating duplication/tests gaps, then names/abstraction violations."[1]

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/83858393/2188aeab-6f3a-42d2-b093-5de3959a6b88/clean-code.pdf)