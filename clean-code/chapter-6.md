Core ideas of Chapter 6  
- Objects and data structures are opposites: objects hide data and expose behavior; data structures expose data and have little or no behavior.[1]
- Choosing between objects vs data structures is a design decision that affects how easily you can add new behaviors or new data types.[1]
- Good encapsulation is about abstraction, not just getters/setters; naive getters/setters often just leak representation.[1]
- The Law of Demeter (“talk to friends, not strangers”) helps avoid fragile code that reaches through multiple layers of objects.[1]

## Rules / principles to remember  
- Prefer true data abstraction:  
  - Do not just mirror fields with `getX/setX`; design methods around *meaningful operations* (e.g., `setPolar`, `getPercentFuelRemaining`).[1]
- Objects vs data structures:  
  - Use **objects** when you need to easily add *new types* with fixed operations (polymorphic `area()` on shapes).[1]
  - Use **data structures + functions** when you need to easily add *new operations* on fixed data (procedural `Geometry.area(shape)`, `Geometry.perimeter(shape)`).[1]
- Data/Object anti-symmetry: recognize that OO and procedural styles give opposite tradeoffs; deliberately choose based on expected change axis.[1]
- Avoid hybrids: do not mix rich behavior with public fields or “bean” accessors that expose everything; that gives you the worst of both worlds.[1]
- Apply the Law of Demeter: a method should only call  
  - its own methods,  
  - methods of its fields,  
  - methods of its arguments,  
  - methods on objects it creates.[1]
- Avoid “train wrecks” like `a.getB().getC().doX()`; either:  
  - ask the nearer object to do the whole job (`ctxt.createScratchFileStream(name)`), or  
  - treat those collaborators explicitly as *data* and keep them simple DTOs.[1]
- Use DTOs for data transport: simple structs (possibly with trivial getters/setters) that carry data between layers (DB, network, etc.).[1]
- Treat Active Record as data, not domain objects: keep persistence methods (`save`, `find`) on AR, but move business rules into separate domain services that use them.[1]

## What is NOT important / can be skimmed  
- The detailed point/vehicle examples beyond the core idea: “abstract interface > raw coordinate/gallon fields.”[1]
- Full shape/geometry implementations and all branches; remember just the contrast between procedural `Geometry` with data structs vs polymorphic `Shape.area()`.[1]
- Long Law of Demeter discussion around particular `ctxt.getOptions().getScratchDir()...` snippets; retain only the pattern “train wreck vs tell object to act.”[1]
- Full Address bean listing; it’s only illustrating a DTO/bean with getters/setters.[1]

## Practical takeaways – impact on how you write code  
- When you add a method to a “domain” class, ask: “Am I modeling an operation on this concept, or just exposing data?” Prefer operations that hide representation.[1]
- For application core/domain:  
  - Model rich **objects** with behavior-oriented APIs.  
  - Hide internal state; avoid exposing raw collections and primitive fields when possible.[1]
- For boundaries (persistence, APIs, messaging):  
  - Use **DTOs/records** to carry data; keep them behavior-free and let services handle logic.[1]
- Avoid chained navigation in business code; instead add higher-level methods on aggregates or services that perform the needed action in one call.[1]
- Decide early per module: “Is this predominantly OO or procedural?” and keep it consistent to avoid hybrid designs that are hard to evolve.[1]

## Interview-ready summaries  
- “Chapter 6 of Clean Code contrasts objects and data structures: objects hide data and expose behavior, data structures expose data and have little behavior; this anti-symmetry determines whether it’s easy to add new operations or new types.”[1]
- “The chapter emphasizes real encapsulation and the Law of Demeter: instead of exposing fields via getters and chaining calls, design abstractions where objects perform meaningful operations and use DTOs only at boundaries, avoiding hybrid designs that are hard to change.”[1]

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/83858393/2188aeab-6f3a-42d2-b093-5de3959a6b88/clean-code.pdf)