Core ideas of Chapter 11  
- System-level cleanliness comes from **separating construction from use**: wiring objects is a different concern from running business logic.[1]
- Keep application code **framework-agnostic and decoupled**, using DI, factories, and composition so architecture can evolve iteratively.[1]
- Cross-cutting concerns (transactions, security, logging, persistence) should be modularized via DI/AOP-like mechanisms, not scattered across code.[1]
- Architectures should **grow incrementally**; avoid big design up front and keep decisions reversible by maintaining low coupling.[1]

## Rules / principles to remember  
- Separate startup from runtime:  
  - All object graph construction and wiring lives in `main` or dedicated composition modules, not in business classes.[1]
- No lazy construction with global knowledge in domain classes (`if (service == null) service = new MyServiceImpl()` is a smell).[1]
- Use **factories** when application must decide *when* to create objects but construction details belong elsewhere.[1]
- Use **Dependency Injection (DI)** to invert control of dependencies:  
  - Classes declare dependencies via constructors/setters.  
  - Container or composition root supplies concrete implementations.[1]
- Keep domain logic in POJOs; framework and infrastructure details (Spring, EJB, AOP) should be thin layers around them.[1]
- Treat cross-cutting concerns as aspects: transactions, security, logging, caching should be configured centrally (AOP, proxies, decorators), not coded everywhere.[1]
- Test-drive architecture:  
  - Drive design of services and wiring via tests using POJOs and injected dependencies.  
  - Avoid architectures that prevent fast, isolated tests (e.g., tightly coupled EJB2-style beans).[1]
- Optimize decision making by modularity: low coupling → local decisions; avoid over-engineered, invasive frameworks that dominate design.[1]

## What is NOT important / can be skimmed  
- Detailed critique of EJB2 vs EJB3; keep only the lesson: invasive frameworks hurt testability and modularity, annotation/POJO-based approaches are better.[1]
- Full Spring XML examples and `Bank` configuration; remember just the idea of DI containers wiring decorators/proxies around POJOs.[1]
- Long city-building analogy; extract “architecture grows iteratively, not perfectly planned upfront.”[1]

## Practical takeaways – impact on how you write code  
- Introduce a **composition root** (e.g., `main`, `AppConfig`) that:  
  - Instantiates services, repositories, controllers.  
  - Wires dependencies (or delegates to DI framework like Spring).  
  - Passes ready objects into the application entrypoint.[1]
- Remove ad-hoc lazy initialization and direct `new` of heavy dependencies from domain classes; inject interfaces instead.[1]
- When you see multiple places doing similar setup (e.g., transaction boundaries, logging), consider extracting an aspect/proxy or using built-in AOP/filters.[1]
- Keep domain services pure: no framework base classes, no annotations that deeply couple behavior; where annotations are necessary, keep them thin (e.g., JPA mappings).[1]
- As stories evolve, refine wiring and infrastructure code rather than changing domain logic to satisfy frameworks.[1]

## Interview-ready summaries  
- “Chapter 11 of Clean Code focuses on system design: separate object construction from use via composition roots and DI, keep domain logic in POJOs, and modularize cross-cutting concerns with factories, proxies, or AOP so architectures can evolve incrementally.”[1]
- “The key message is that a clean architecture minimizes framework coupling and centralizes wiring and cross-cutting concerns, enabling test-driven development of both code and architecture while avoiding big design up front.”[1]

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/83858393/2188aeab-6f3a-42d2-b093-5de3959a6b88/clean-code.pdf)