# OOP Interview Questions — Reported at Bangladeshi Companies (Glassdoor)

**Source:** Candidate-reported interview experiences on Glassdoor for **Bitmorpher**, **Bit Mascot**, **Vivasoft**, and **Bdjobs**.
**Scope:** OOP-specific questions only (DSA, DBMS, OS, and networking questions were excluded).

> Note: Glassdoor reviews reflect what individual candidates remembered and chose to post — they are a sample, not an official question bank. Treat this as a strong signal of *themes*, not a guarantee of exact wording.

---

## 1. Bitmorpher

Questions reported by candidates:

- What is Object-Oriented Programming (OOP)?
- What is a Class?
- What is an Object?
- Difference between **Struct** and **Class**.
- Explain the **four pillars of OOP**.
- What is **Inheritance**?
- Explain **Polymorphism**.
- What is the difference between **mutable** and **immutable** objects?
- Explain the **SOLID principles**.
- Basic OOP concepts (general/open-ended).

**Source:** [Bitmorpher Interview Questions – Glassdoor](https://www.glassdoor.com/Interview/Bitmorpher-Interview-Questions-E5318722.htm)

---

## 2. Bit Mascot

Questions reported by candidates:

- Explain **Object-Oriented Programming** with a real-life example.
- Explain the **4 pillars of OOP**.
- What are the **core concepts of OOP**?
- Describe each OOP pillar.
- OOP questions based on your project.
- OOP scenario-based questions.

**Source:** [Bit Mascot Interview Questions – Glassdoor](https://www.glassdoor.com/Interview/Bit-Mascot-Interview-Questions-E1911356.htm)

---

## 3. Vivasoft

Questions reported by candidates:

- What are programming paradigms other than **OOP**?
- Explain the **SOLID principles**.
- OOP theory questions (asked in the written exam).

**Source:** [Vivasoft Interview Questions – Glassdoor](https://www.glassdoor.com/Interview/Vivasoft-Interview-Questions-E5062992.htm)

---

## 4. Bdjobs

Questions reported by candidates:

- Written OOP theory questions.
- OOP-based programming question.
- OOP concepts discussed during the technical interview (general).

**Source:** [Bdjobs.com Interview Questions – Glassdoor](https://www.glassdoor.co.in/Interview/Bdjobs-com-Bangladesh-Interview-Questions-EI_IE730055.0,10_IL.11,21_IN27.htm)

---

## 5. Combined Question List by Topic

These are all the OOP questions above, merged and grouped by topic, plus the closely related sub-questions that tend to follow up on them.

### OOP Basics
- What is OOP?
- Why OOP?
- Advantages of OOP.
- OOP vs Procedural Programming.
- Real-life example of OOP.

### Class & Object
- What is a class?
- What is an object?
- Difference between class and object.
- Difference between object and instance.
- Object lifecycle.

### Encapsulation
- What is encapsulation?
- Advantages of encapsulation.
- How is encapsulation implemented?
- Getter and Setter.
- Why keep data private?

### Abstraction
- What is abstraction?
- Real-life example.
- Difference between abstraction and encapsulation.
- How is abstraction achieved in C++?

### Inheritance
- What is inheritance?
- Why inheritance?
- Types of inheritance.
- Multiple inheritance.
- Multilevel inheritance.
- Hierarchical inheritance.
- Hybrid inheritance.
- Diamond problem.
- Virtual inheritance.

### Polymorphism
- What is polymorphism?
- Static polymorphism.
- Dynamic polymorphism.
- Function overloading.
- Function overriding.
- Compile-time vs runtime polymorphism.
- Real-life example.

### Constructors
- Constructor.
- Default constructor.
- Parameterized constructor.
- Copy constructor.
- Constructor overloading.

### Destructor
- Destructor.
- Why destructor?
- Destructor order.
- Virtual destructor.

### Virtual Functions
- What is a virtual function?
- Why use virtual?
- Pure virtual function.
- Abstract class.
- Interface in C++.

### C++ Specific OOP
- Struct vs Class.
- Friend function.
- Friend class.
- `this` pointer.
- Static member.
- Static member function.
- `const` member function.

### Copying Objects
- Shallow copy.
- Deep copy.
- Copy constructor vs assignment operator.

### Memory
- Stack vs Heap.
- `new` vs `malloc`.
- `delete` vs `free`.
- Dynamic memory allocation.

### SOLID Principles
- What is SOLID?
- Explain all five principles.
- Real-life examples of each principle.

### Project-Based OOP
- Explain how you used OOP in your project.
- Which OOP principles did you use?
- Why did you choose inheritance/composition?
- Which classes did you design?
- How would you redesign your project using better OOP?

---

## 6. Most Frequently Reported Topics

Ranked by how often they appeared across the interview reports above:

1. OOP fundamentals
2. Four pillars of OOP
3. Class vs Object
4. Struct vs Class
5. Inheritance
6. Polymorphism
7. SOLID principles
8. Real-life examples of OOP
9. Project-based OOP questions
10. Scenario-based OOP questions

**→ Priority tip:** If your prep time is limited, master items 1–7 cold (definitions + real-life example + a short code snippet for each), then rehearse how you'd explain OOP usage in *your own* project (items 9–10) — Bitmorpher and Bit Mascot both explicitly ask candidates to connect OOP concepts back to their own work.

---

## 7. Notes on Topics Not Yet Covered in the Main Prep Guide

A few items from the Glassdoor reports weren't in the original OOP viva prep doc. Quick answers for these:

**Mutable vs Immutable objects**
A **mutable** object's internal state can be changed after creation (e.g., a Java `ArrayList`, a Python `list`). An **immutable** object's state cannot change once created — any "modification" produces a new object (e.g., `String` in Java, `str`/`tuple` in Python, `int` in Python). Immutability aids thread-safety and predictability but can cost performance if changed frequently.

**Struct vs Class (C++)**
Members are `public` by default in a `struct` and `private` by default in a `class`. Functionally in C++ they're otherwise identical (both can have methods, constructors, inheritance) — the difference is purely the default access level and, by convention, `struct` is used for simple data containers while `class` is used for objects with behavior and invariants.

**Friend function / Friend class**
A `friend` function or class is granted access to the `private` and `protected` members of the class that declares it as a friend, even though it isn't a member itself. Used sparingly, typically for operator overloading (e.g., overloading `<<` for output streams).

**`this` pointer**
A pointer available inside non-static member functions that points to the calling object itself — used to disambiguate member variables from parameters of the same name, or to return `*this` for method chaining.

**Shallow copy vs Deep copy**
A **shallow copy** copies an object's fields as-is — if a field is a pointer/reference, both the original and copy point to the same underlying data. A **deep copy** recursively copies the actual data being pointed to, so the two objects are fully independent. Shallow copies risk double-free/dangling-pointer bugs; deep copies avoid this at the cost of extra memory/time.

**Copy constructor vs assignment operator**
The copy constructor initializes a **new** object as a copy of an existing one (`ClassName obj2(obj1);`). The assignment operator (`operator=`) copies values into an **already-existing** object (`obj2 = obj1;`), typically requiring you to first release any resources obj2 already owns.

**Stack vs Heap**
The **stack** stores local variables and function call frames; memory is managed automatically (LIFO) and is fast but limited in size. The **heap** stores dynamically allocated memory (`new`/`malloc`); it must be managed manually (or via garbage collection) and is larger but slower to allocate/deallocate.

**`new`/`delete` vs `malloc`/`free`**
`new`/`delete` (C++) are operators that allocate/deallocate memory **and** call the object's constructor/destructor. `malloc`/`free` (C) only allocate/deallocate raw memory with no constructor/destructor calls — mixing the two (e.g., `malloc` with `delete`) causes undefined behavior.

**Virtual destructor**
A destructor declared `virtual` in a base class so that deleting a derived object through a base class pointer correctly calls the derived class's destructor first, preventing resource leaks. Rule of thumb: if a class has any virtual function, its destructor should usually be virtual too.

---

## 8. How to Use This Alongside Your Main Prep Guide

- Use **`OOP_Viva_Prep.md`** (the earlier file) for full definitions, analogies, and code examples of the core pillars, SOLID, and language-specific questions.
- Use **this file** to see exactly which topics real candidates at these companies reported, and to prioritize your revision order using Section 6.
- Before the viva, rehearse a **2–3 minute answer** for "Explain OOP using an example from your project" — this exact framing was reported at Bit Mascot and is very likely at Bitmorpher too.

---

*Good luck with your Bitmorpher viva — these questions, combined with the fuller prep guide, cover both breadth (topics companies actually ask) and depth (how to answer them well).*
