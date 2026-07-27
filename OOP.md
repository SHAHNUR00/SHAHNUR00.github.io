# OOP Viva Preparation Guide

**For:** Fresher / Entry-level Software Engineer roles
**Target companies:** Bitmorpher and other Bangladeshi software companies (Brain Station 23, Cefalo, SELISE, Tiger IT, Enosis, Kaz Software, DataSoft, Therap, Vivasoft, Astha IT, etc.)

> **Note on scope:** These are the OOP questions that recur across fresher interviews and vivas at Bangladeshi software companies. Company-specific past questions are not published anywhere reliable, but these companies draw from the same standard OOP question bank for freshers — so this coverage represents your viva well. Prepare to *speak* your answers aloud and back each concept with a small code example, because interviewers usually ask "can you give an example?" as a follow-up.

---

## How OOP vivas usually go (read this first)

1. They warm up with definitions ("What is OOP?", "What is a class vs an object?").
2. They test the **four pillars** and expect a real-life example for each.
3. They probe the **tricky pairs**: overloading vs overriding, abstract class vs interface, association vs aggregation vs composition.
4. They ask a **language-specific** question (C++, Java, C#, or Python depending on the JD).
5. They finish with **"why"** questions ("Why use encapsulation?", "Why prefer composition over inheritance?") to see if you understand *reasons*, not just definitions.

**Golden rule:** Always answer with a one-line definition, then a one-line real-world analogy, then (if asked) a tiny code snippet.

---

## 1. OOP Fundamentals

**Q1. What is Object-Oriented Programming (OOP)?**
A programming paradigm that organizes software design around **objects** — self-contained units that bundle **data (attributes)** and **behavior (methods)** together — rather than around functions and logic alone. Its goal is to model real-world entities, improve reusability, and make code easier to maintain and extend.

**Q2. What is a class?**
A class is a **blueprint or template** for creating objects. It defines the attributes (fields) and methods (behaviors) that its objects will have, but it does not itself occupy memory for those objects.

**Q3. What is an object?**
An object is an **instance of a class** — a concrete entity created from the blueprint that occupies memory and holds actual data. Example: `Car` is a class; `myCar = new Car()` is an object.

**Q4. Difference between a class and an object?**
A class is a definition (blueprint); an object is a real, memory-occupying instance built from that definition. One class can produce many objects.

**Q5. What are the main advantages of OOP?**
Reusability (via inheritance), modularity, maintainability, data security (via encapsulation), flexibility (via polymorphism), and closeness to real-world modeling.

**Q6. What is the difference between procedural programming and OOP?**
Procedural programming (e.g., C) structures code as a sequence of functions operating on data, with data and functions kept separate. OOP binds data and functions together into objects, supports inheritance and polymorphism, and hides internal data.

**Q7. What are the four pillars of OOP?**
Encapsulation, Abstraction, Inheritance, and Polymorphism.

---

## 2. The Four Pillars

### Encapsulation

**Q8. What is encapsulation?**
Wrapping data (variables) and the methods that operate on that data into a single unit (a class), and **restricting direct access** to the internal data. It is usually achieved by making fields `private` and exposing controlled access through public getters/setters.

**Q9. Why is encapsulation useful?**
It protects data from unintended modification, allows validation inside setters, hides implementation details, and lets you change internals without breaking outside code.

**Real-life analogy:** A medicine capsule hides the drug inside a shell; you interact with the capsule, not the raw powder. Similarly, a car's accelerator hides the engine mechanics.

```java
class BankAccount {
    private double balance;              // hidden data

    public void deposit(double amount) { // controlled access
        if (amount > 0) balance += amount;
    }
    public double getBalance() { return balance; }
}
```

### Abstraction

**Q10. What is abstraction?**
Hiding **complex implementation details** and exposing only the **essential features** to the user. It focuses on *what* an object does rather than *how* it does it.

**Q11. How is abstraction different from encapsulation?**
Abstraction hides *complexity* (design level — "what to show"); encapsulation hides *data* (implementation level — "how to protect it"). Abstraction is achieved with abstract classes/interfaces; encapsulation with access modifiers.

**Real-life analogy:** When driving a car, you use the steering wheel and pedals (essential interface) without knowing how the engine combustion works (hidden detail).

### Inheritance

**Q12. What is inheritance?**
A mechanism where one class (child/derived/subclass) **acquires the properties and behaviors** of another class (parent/base/superclass), enabling code reuse and hierarchical relationships. It represents an **"is-a"** relationship.

**Q13. What are the types of inheritance?**
Single, Multiple, Multilevel, Hierarchical, and Hybrid inheritance.
- **Single:** B inherits from A.
- **Multilevel:** C inherits from B, which inherits from A.
- **Hierarchical:** B and C both inherit from A.
- **Multiple:** C inherits from both A and B (supported in C++ and Python; **not** with classes in Java/C#, only via interfaces).
- **Hybrid:** a combination of the above.

**Q14. What is the diamond problem?**
An ambiguity in **multiple inheritance** where a class inherits from two classes that both inherit from a common base class — the compiler can't decide which path to use for the shared members. C++ solves it with **virtual inheritance**; Java/C# avoid it by disallowing multiple class inheritance (using interfaces instead).

**Real-life analogy:** A child inherits traits (eye color, height) from parents.

### Polymorphism

**Q15. What is polymorphism?**
"Many forms" — the ability of a single interface/method to behave differently based on the object or arguments. It lets one name represent different behaviors.

**Q16. What are the types of polymorphism?**
- **Compile-time (static) polymorphism:** achieved via **method overloading** (and operator overloading). Resolved at compile time.
- **Run-time (dynamic) polymorphism:** achieved via **method overriding**. Resolved at run time using virtual method dispatch.

**Real-life analogy:** A person behaves as a student in class, a customer in a shop, and a son at home — same person, different behavior by context.

```java
Shape s = new Circle();  // reference of parent type
s.draw();                // calls Circle's draw() at runtime -> dynamic polymorphism
```

---

## 3. Overloading vs Overriding (very common)

**Q17. What is method overloading?**
Defining **multiple methods with the same name but different parameter lists** (different type, number, or order of parameters) within the same class. Return type alone does not distinguish overloads. It is compile-time polymorphism.

**Q18. What is method overriding?**
Redefining a **parent class method in the child class** with the **same signature** to provide a specialized implementation. It is run-time polymorphism.

**Q19. Key differences?**

| Aspect | Overloading | Overriding |
|---|---|---|
| Where | Same class | Parent & child class |
| Signature | Different parameters | Same signature |
| Binding | Compile-time (static) | Run-time (dynamic) |
| Inheritance needed? | No | Yes |
| Polymorphism type | Static | Dynamic |

**Q20. Can we overload the main method?** Yes, but the program entry point remains the standard `main` signature; overloaded versions must be called explicitly.

**Q21. Can we override a static method?** No. Static methods belong to the class, not the instance; redeclaring one in a subclass is **method hiding**, not overriding.

---

## 4. Abstract Class vs Interface (very common)

**Q22. What is an abstract class?**
A class that **cannot be instantiated** and is meant to be a base class. It can have both abstract methods (no body) and concrete methods (with body), constructors, and fields.

**Q23. What is an interface?**
A contract that defines **method signatures** a class must implement. Traditionally it has no implementation (though modern Java/C# allow default methods). A class can implement multiple interfaces.

**Q24. Differences between abstract class and interface?**

| Aspect | Abstract Class | Interface |
|---|---|---|
| Methods | Abstract + concrete | Mostly abstract (default methods allowed in modern versions) |
| Multiple inheritance | No (single) | Yes (a class can implement many) |
| Fields | Instance fields allowed | Constants only (traditionally) |
| Constructor | Yes | No |
| Relationship | "is-a" | "can-do" / capability |
| When to use | Shared base with common code | Common capability across unrelated classes |

**Q25. When would you choose an interface over an abstract class?**
When unrelated classes need to share a **capability** (e.g., `Comparable`, `Serializable`), or when you need multiple inheritance of type. Use an abstract class when related classes share **common code and state**.

---

## 5. Classes, Objects, Constructors

**Q26. What is a constructor?**
A special method called automatically when an object is created, used to initialize the object. It has the same name as the class and no return type.

**Q27. Types of constructors?**
- **Default constructor:** no parameters (provided by compiler if none defined).
- **Parameterized constructor:** takes arguments.
- **Copy constructor:** creates an object by copying another (prominent in C++).

**Q28. What is a destructor?**
A method invoked when an object is destroyed, used to release resources. Explicit in C++ (`~ClassName()`); in Java/C# memory is handled by the garbage collector (finalizers/`Dispose` exist but destructors as such do not).

**Q29. What is constructor overloading?**
Having multiple constructors with different parameter lists in the same class.

**Q30. Can a constructor be private?**
Yes — used in the **Singleton** pattern to prevent external instantiation and in factory methods.

**Q31. What is the `this` keyword?**
A reference to the current object; used to distinguish instance variables from parameters and to call other constructors/methods of the same object.

**Q32. What is the `super` keyword?**
A reference to the immediate parent class; used to call the parent's constructor or access overridden parent methods/fields.

---

## 6. Access Modifiers & Static

**Q33. What are access modifiers?**
Keywords that set the visibility/accessibility of classes, methods, and fields:
- **private:** accessible only within the same class.
- **protected:** accessible within the class and its subclasses (and same package in Java).
- **public:** accessible from anywhere.
- **default/package-private (Java):** accessible within the same package.

**Q34. What does `static` mean?**
A static member belongs to the **class itself, not to any instance** — shared across all objects. Static methods can be called without creating an object and cannot access instance (non-static) members directly.

**Q35. Difference between static and instance members?**
Static members share one copy across all objects and exist for the class's lifetime; instance members get a separate copy per object and exist for that object's lifetime.

**Q36. What is the `final` (Java) / `sealed` (C#) / `const` keyword used for?**
`final` variable → constant; `final` method → cannot be overridden; `final` class → cannot be inherited.

---

## 7. Relationships: Association, Aggregation, Composition

**Q37. What is association?**
A general relationship where objects of one class are connected to objects of another (e.g., a Teacher and a Student). No ownership implied.

**Q38. What is aggregation?**
A **"has-a"** relationship with **weak ownership** — the part can exist independently of the whole. Example: a Department *has* Teachers, but Teachers exist even if the Department is dissolved.

**Q39. What is composition?**
A **"has-a"** relationship with **strong ownership** — the part **cannot exist** without the whole. Example: a House *has* Rooms; destroy the House and the Rooms cease to exist.

**Q40. Aggregation vs Composition in one line?**
Aggregation = weak ownership, independent lifecycle. Composition = strong ownership, dependent lifecycle.

**Q41. Inheritance vs Composition — which is preferred and why?**
Composition is often preferred ("favor composition over inheritance") because it is more flexible, reduces tight coupling, avoids fragile deep inheritance hierarchies, and lets behavior change at runtime.

---

## 8. SOLID Principles (asked at product companies like SELISE, Cefalo, Enosis)

**Q42. What are the SOLID principles?**
Five design principles for maintainable OOP code:
- **S — Single Responsibility:** a class should have only one reason to change (one job).
- **O — Open/Closed:** open for extension, closed for modification.
- **L — Liskov Substitution:** subclasses should be substitutable for their base class without breaking behavior.
- **I — Interface Segregation:** many specific interfaces are better than one large general one; don't force classes to implement unused methods.
- **D — Dependency Inversion:** depend on abstractions, not concrete implementations.

**Q43. What is coupling and cohesion?**
- **Coupling:** degree of dependency between modules. **Low coupling is good.**
- **Cohesion:** how focused a module's responsibilities are. **High cohesion is good.**

**Q44. What is DRY?** "Don't Repeat Yourself" — avoid duplicating logic; extract it into reusable units.

---

## 9. Common Design Patterns (bonus — impresses interviewers)

**Q45. What is a design pattern?**
A reusable, proven solution to a commonly occurring problem in software design.

**Q46. Explain the Singleton pattern.**
Ensures a class has **only one instance** and provides a global access point to it (e.g., a configuration or logging class). Achieved with a private constructor and a static instance.

**Q47. Explain the Factory pattern.**
Provides an interface for creating objects without exposing the exact class being instantiated — the factory decides which concrete type to return.

**Q48. Other patterns worth naming:** Observer, Strategy, Decorator, Adapter, Builder, MVC (as an architectural pattern).

---

## 10. Language-Specific Questions

### Java (Brain Station 23, Therap, many BD product firms)

**Q49. Does Java support multiple inheritance?**
Not through classes (to avoid the diamond problem), but yes through **interfaces**.

**Q50. What is the difference between `==` and `.equals()`?**
`==` compares references (memory addresses) for objects; `.equals()` compares content/values (when overridden).

**Q51. What is the JVM / JRE / JDK?**
JVM runs bytecode; JRE = JVM + libraries to run programs; JDK = JRE + development tools (compiler, etc.).

**Q52. What is garbage collection?**
Automatic reclamation of memory occupied by objects that are no longer reachable.

**Q53. Difference between `String`, `StringBuilder`, `StringBuffer`?**
`String` is immutable; `StringBuilder` is mutable and not thread-safe (faster); `StringBuffer` is mutable and thread-safe.

### C++ (Tiger IT, embedded/systems roles)

**Q54. What is a virtual function?**
A member function declared `virtual` in the base class that can be overridden in derived classes, enabling run-time polymorphism via the vtable.

**Q55. What is a pure virtual function?**
A virtual function with `= 0` and no body, which makes the class **abstract** (cannot be instantiated).

**Q56. What is the difference between a struct and a class in C++?**
Members are `public` by default in a `struct` and `private` by default in a `class`.

**Q57. What is operator overloading?**
Giving special meaning to an operator (e.g., `+`) for user-defined types.

### C# (SELISE, Vivasoft, .NET shops)

**Q58. Difference between an abstract class and an interface in C#?**
Same conceptual difference as above; note C# 8+ interfaces can have default implementations.

**Q59. What are properties in C#?**
Members that provide a flexible mechanism to read/write private fields via `get`/`set` accessors — encapsulation made concise.

**Q60. Value type vs reference type?**
Value types (int, struct) hold data directly on the stack; reference types (class, object) hold a reference to heap data.

### Python (data/AI-leaning teams)

**Q61. How is encapsulation done in Python?**
By convention: single underscore `_x` (protected), double underscore `__x` (name-mangled/private). Python relies on convention rather than strict enforcement.

**Q62. Does Python support method overloading?**
Not natively (later definitions override earlier ones); it's simulated with default arguments or `*args`/`**kwargs`.

**Q63. What is `self` in Python?**
A reference to the current instance, passed automatically as the first parameter of instance methods.

---

## 11. Quick-Fire "Why" Questions (interviewers love these)

- **Why use OOP?** → Reusability, maintainability, real-world modeling, security.
- **Why encapsulation?** → Protect and validate data, hide internals.
- **Why abstraction?** → Reduce complexity, focus on essentials.
- **Why inheritance?** → Reuse code, model "is-a" hierarchies.
- **Why polymorphism?** → Flexibility and extensibility with a single interface.
- **Why prefer composition over inheritance?** → Looser coupling, more flexible, avoids fragile hierarchies.
- **Why interfaces if we have abstract classes?** → Multiple inheritance of type; shared capability across unrelated classes.

---

## 12. Rapid Revision Cheat Sheet

- **4 Pillars:** Encapsulation (hide data), Abstraction (hide complexity), Inheritance (reuse), Polymorphism (many forms).
- **Overloading** = same name, different params, compile-time. **Overriding** = same signature, child redefines parent, run-time.
- **Abstract class** = partial implementation + state, single inheritance. **Interface** = contract, multiple implementation.
- **Association** (uses-a) ⊃ **Aggregation** (weak has-a) ⊃ **Composition** (strong has-a).
- **SOLID** = Single Responsibility, Open/Closed, Liskov, Interface Segregation, Dependency Inversion.
- **Static** = belongs to class. **Instance** = belongs to object.
- **Constructor** initializes; **Destructor** cleans up.

---

## 13. Viva Day Tips

1. **Speak the structure:** definition → analogy → example. Interviewers reward clarity.
2. **Always be ready with a code snippet** for the four pillars and for overloading vs overriding.
3. **Know the JD's language** deeply — revisit Section 10 for it.
4. If you don't know something, say **"I'm not certain, but my understanding is..."** rather than guessing blindly or freezing.
5. **Tie concepts to real code you've written** (your projects) — "In my project I used inheritance for X" scores highly.
6. Stay calm; a viva tests reasoning and communication as much as memorization.

---

*Prepare the concepts, practice saying them aloud, and code a small example for each pillar. Best of luck with your Bitmorpher viva.*
