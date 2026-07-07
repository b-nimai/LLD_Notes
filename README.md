# LLD — Low Level Design Notes & Practice

Part of a 6-month job-switch study plan. This repo holds **Low Level Design** notes and worked problems — applying OOP and SOLID at the class-design altitude that interviews actually test.

## Structure

Each problem gets its own note + code, following the DSA-repo conventions:

- A per-problem note (title, pattern/trigger, problem 1-liner, idea, approach, clean canonical code, pitfalls).
- A pattern/topic `0. Index.md` for 30-second recall.

## Topics (planned)

- OOP design fundamentals (classes, relationships, composition vs inheritance)
- SOLID principles in practice
- Design patterns (Creational / Structural / Behavioral)
- Classic LLD problems (Parking Lot, Splitwise, Elevator, Rate Limiter, BookMyShow, ...)

---

## Pattern Priority — what to actually practice

Don't study all 23 equally. **Interview** = how often it shows up in LLD rounds. **Real-life** = how often you'll genuinely reach for it in production code. Practice **P0 cold** (know the trigger, code the skeleton in <5 min), **P1 well**, **P2 one-liner only**.

| Pattern | Type | Interview | Real-life | Verdict | The one-line trigger |
|---------|------|:---------:|:---------:|---------|----------------------|
| **Strategy** | Behavioral | ⭐⭐⭐ | ⭐⭐⭐ | **P0** | "A behavior/algorithm varies (pricing, payment, sorting, discount) → swap it at runtime instead of `if/else`" |
| **Factory** | Creational | ⭐⭐⭐ | ⭐⭐⭐ | **P0** | "Creating a concrete class by a type-switch in business logic → centralize the `new`" |
| **Singleton** | Creational | ⭐⭐⭐ | ⭐⭐⭐ | **P0** | "Exactly one shared instance (config, logger, connection pool)" |
| **Observer** | Behavioral | ⭐⭐⭐ | ⭐⭐⭐ | **P0** | "One thing changes → many need to be notified (events, pub-sub, notifications)" |
| **State** | Behavioral | ⭐⭐⭐ | ⭐⭐ | **P0** | "Object behaves differently by mode, full of `if(state==)` (vending machine, order lifecycle, elevator)" |
| **Decorator** | Structural | ⭐⭐ | ⭐⭐⭐ | **P0** | "Add responsibilities to an object at runtime without subclass explosion (pizza toppings, I/O streams)" |
| **Builder** | Creational | ⭐⭐ | ⭐⭐⭐ | **P1** | "Object with many optional params → telescoping constructors" |
| **Adapter** | Structural | ⭐⭐ | ⭐⭐⭐ | **P1** | "Third-party class, wrong signature, can't edit it → wrap it" |
| **Facade** | Structural | ⭐⭐ | ⭐⭐⭐ | **P1** | "Hide a messy subsystem behind one simple entry point" |
| **Command** | Behavioral | ⭐⭐ | ⭐⭐ | **P1** | "Turn a request into an object → queue / undo / log it" |
| **Abstract Factory** | Creational | ⭐ | ⭐⭐ | **P1** | "Create a consistent *family* of products that must match (region/theme kit)" |
| **Proxy** | Structural | ⭐ | ⭐⭐ | **P2** | "Same interface, but control access — lazy load, cache, auth, rate-limit" |
| **Composite** | Structural | ⭐ | ⭐⭐ | **P2** | "Tree of part-whole treated uniformly (file system, org chart, UI)" |
| **Template Method** | Behavioral | ⭐ | ⭐⭐ | **P2** | "Fixed algorithm skeleton, subclasses fill in steps" |
| **Chain of Responsibility** | Behavioral | ⭐ | ⭐⭐ | **P2** | "Pass a request along handlers until one handles it (middleware, approval chain)" |
| **Prototype** | Creational | ⭐ | ⭐ | **P2** | "Clone a pre-configured object instead of rebuilding it" |
| Bridge · Flyweight · Mediator · Memento · Visitor · Iterator · Interpreter | mixed | ⚪ | varies | **know the one-liner only** | rarely asked; recognize, don't drill |

**Rule of thumb:** the **6 P0 patterns cover ~80% of what LLD interviews test**, because case-study prompts almost always hide a *"this part varies / this part must stay closed to edits"* requirement — which is exactly Strategy / Factory / State / Observer / Decorator. Master those, and most case studies become assembly.

**Practice order:** finish Structural notes → Behavioral (do **Strategy, Observer, State first** — the P0s) → then case studies, where you'll see 3–4 of these stack in one design.
