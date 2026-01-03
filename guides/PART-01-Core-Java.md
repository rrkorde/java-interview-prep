# PART I: Core Java & Fundamentals

This part covers the foundational Java concepts that every senior backend developer must master.

**Topics Covered:**
1. Java Language Fundamentals
2. Object-Oriented Programming in Java  
3. JVM Internals & Performance
4. Collections Framework Deep Dive
5. Multithreading & Concurrency
6. Java 8+ Modern Features
7. Exception Handling & Error Management
8. Java I/O & NIO
9. Reflection, Annotations & Generics

---

## 1. Java Language Fundamentals

### 1.1 Java Basics & Syntax

**Key Topics:**
- Java history, versions, and JDK releases (Java 8, 11, 17, 21)
- JVM, JRE, JDK differences and architecture
- Java program structure and execution flow
- Main method and command-line arguments
- Primitive data types (byte, short, int, long, float, double, boolean, char)
- Type casting (implicit vs explicit, widening vs narrowing)
- Wrapper classes and autoboxing/unboxing
- Operators (arithmetic, relational, logical, bitwise, shift, ternary)
- Control flow statements (if-else, switch, loops)
- Enhanced switch expressions (Java 14+)
- Variable scopes and lifecycle
- Static vs instance members
- Final keyword (variables, methods, classes)
- Access modifiers (private, default, protected, public)
- Package structure and imports

**Common Questions:**
1. What are the differences between JDK, JRE, and JVM?
2. Explain the difference between primitive types and wrapper classes
3. When does autoboxing/unboxing occur and what are the performance implications?
4. What is the difference between == and equals()?
5. Explain the difference between String, StringBuilder, and StringBuffer
6. What happens if you don't write a main method in a Java class?
7. Can you override static methods? Why or why not?
8. What is the difference between final, finally, and finalize?
9. Explain pass-by-value in Java with examples
10. What are the new features in Java 17 and Java 21?
11. How does Java achieve platform independence?
12. What is the purpose of the 'this' keyword?
13. Explain the concept of String Pool and intern() method
14. What are var types (local variable type inference) in Java 10+?
15. How do switch expressions differ from traditional switch statements?
16. What is the range of byte, short, int, and long data types?
17. Can you have a main method in an interface?
18. What is the difference between & and && operators?
19. What are the different ways to create a String object?
20. How does type casting work between primitive types?

### 1.2 String Manipulation & Immutability

**Key Topics:**
- String immutability and its benefits
- String pool and memory optimization  
- String vs StringBuilder vs StringBuffer
- String methods and common operations
- String formatting and templates (Java 21+)
- Regular expressions in Java
- Character encoding (UTF-8, UTF-16)
- String performance optimization techniques
- String deduplication in JVM
- Text blocks (Java 15+)
- String concatenation performance
- StringJoiner and String.join()
- Locale-sensitive string operations

**Common Questions:**
1. Why are Strings immutable in Java?
2. How does the String pool work internally?
3. When should you use StringBuilder vs StringBuffer?
4. How can you create a mutable String in Java?
5. Explain the intern() method and when to use it
6. What is the time complexity of String concatenation using +?
7. How do you compare strings for equality?
8. What are the performance implications of using + for string concatenation in loops?
9. How do text blocks improve code readability?
10. Explain String deduplication and when it occurs
11. How does String formatting work with %s, %d, etc.?
12. What is the difference between length() and capacity() in StringBuilder?
13. How do you reverse a string efficiently?
14. What are some common string algorithms you should know?
15. How do you handle null strings vs empty strings?
16. What is the difference between String.valueOf() and toString()?
17. How do you split a string in Java?
18. What is the difference between matches() and find() in regex?
19. How do you remove leading and trailing whitespace?
20. What is the StringTokenizer class and when would you use it?

### 1.3 Memory Management Basics

**Key Topics:**
- Stack vs Heap memory
- Object allocation and deallocation
- Reference types (strong, soft, weak, phantom)
- Memory leaks in Java and how to prevent them
- finalize() method and finalizers (deprecated in Java 9+)
- Cleaner API (Java 9+)
- Memory-efficient coding practices
- Object lifecycle and garbage collection eligibility
- Memory footprint of Java objects
- String pool memory management

**Common Questions:**
1. What is the difference between stack and heap memory?
2. Where are static variables stored?
3. What happens when an object is created with 'new' keyword?
4. How can memory leaks occur in Java if it has automatic garbage collection?
5. What are the different types of references in Java?
6. When would you use WeakReference or SoftReference?
7. Why was finalize() deprecated and what should we use instead?
8. How do you prevent memory leaks in Java applications?
9. What is the difference between shallow copy and deep copy?
10. How does the JVM decide when to garbage collect an object?
11. What is the purpose of SoftReference in caching?
12. How much memory does an empty Object use?
13. What is object retention and how do you detect it?
14. How do you analyze heap dumps?
15. What tools can you use to detect memory leaks?

---

## 2. Object-Oriented Programming in Java

### 2.1 Classes and Objects

**Key Topics:**
- Class definition and structure
- Object creation and initialization
- Constructors (default, parameterized, copy constructor)
- Constructor chaining (this() and super())
- Instance initializer blocks
- Static initializer blocks
- Order of initialization
- Object cloning (shallow vs deep)
- Cloneable interface and clone() method
- Object lifecycle and finalization
- Anonymous classes
- Nested and inner classes
- Local classes
- Member initialization

**Common Questions:**
1. What is the difference between a class and an object?
2. Can you have multiple constructors in a class? (Constructor overloading)
3. What is constructor chaining and how does it work?
4. What happens if you don't define a constructor?
5. In what order are instance variables, constructors, and static blocks executed?
6. How do you create a deep copy of an object?
7. Why is clone() protected in Object class?
8. What is the difference between shallow copy and deep copy?
9. Can constructors be private? What is the use case?
10. What happens when you create an object of a subclass?
11. How many objects are created when you write: String s = new String("hello")?
12. What is the purpose of the default constructor?
13. Can you call one constructor from another?
14. What is the 'super' keyword and when is it used?
15. How do you prevent object creation for a class?
16. What are anonymous classes and when would you use them?
17. What is the difference between static and non-static nested classes?
18. Can you have static methods in an inner class?
19. What is a local class?
20. How does object initialization order work with inheritance?

### 2.2 Encapsulation

**Key Topics:**
- Data hiding and access control
- Getters and setters
- Access modifiers and their scope
- Benefits of encapsulation
- JavaBeans conventions
- Immutable classes and design
- Defensive copying
- Package-private access
- Encapsulation best practices
- Property change listeners

**Common Questions:**
1. What is encapsulation and why is it important?
2. How do you achieve encapsulation in Java?
3. What is the difference between private and protected?
4. Why should instance variables be private?
5. What is the benefit of using getters and setters instead of public fields?
6. How do you create an immutable class in Java?
7. What is defensive copying and when should you use it?
8. Can you access private members of a class from another instance of the same class?
9. What is package-private access?
10. How does encapsulation help in maintaining code?
11. What are JavaBeans and what are their conventions?
12. Should you always create getters and setters for all fields?
13. How do you make a class immutable?
14. What is the Builder pattern and how does it relate to encapsulation?
15. How do you encapsulate collections?

### 2.3 Inheritance

**Key Topics:**
- IS-A relationship
- extends keyword
- Single vs multiple inheritance
- Method overriding
- super keyword
- Covariant return types
- Abstract classes and methods
- final classes and methods
- Protected access in inheritance
- Constructor inheritance
- Object class and its methods
- Method hiding
- Inheritance vs composition
- Fragile base class problem

**Common Questions:**
1. What is inheritance and what are its benefits?
2. Why doesn't Java support multiple inheritance for classes?
3. What is the difference between extends and implements?
4. Can you override a private or static method?
5. What is method overriding and its rules?
6. What is covariant return type in method overriding?
7. When should you use abstract classes?
8. What is the purpose of the final keyword in inheritance?
9. How does constructor work in inheritance hierarchy?
10. What methods does every class inherit from Object?
11. What is the diamond problem and how does Java avoid it?
12. Can you extend multiple classes in Java?
13. What is the difference between inheritance and composition?
14. When should you prefer composition over inheritance?
15. How do you prevent a class from being inherited?
16. What is method hiding?
17. Can you reduce the visibility of an overridden method?
18. What happens if a parent and child class have the same instance variable?
19. How does inheritance affect memory?
20. What is the Liskov Substitution Principle?

### 2.4 Polymorphism

**Key Topics:**
- Compile-time polymorphism (method overloading)
- Runtime polymorphism (method overriding)
- Dynamic method dispatch
- instanceof operator
- Pattern matching for instanceof (Java 16+)
- Upcasting and downcasting
- Polymorphism with interfaces
- Virtual method invocation
- Method resolution
- Covariant return types

**Common Questions:**
1. What is polymorphism and what are its types?
2. What is the difference between overloading and overriding?
3. How does method overloading work?
4. Can you overload methods by changing only the return type?
5. What is dynamic method dispatch?
6. How does the JVM decide which method to call at runtime?
7. What is the use of instanceof operator?
8. When would you use upcasting vs downcasting?
9. Can you override a method with a different return type?
10. What happens if you call an overridden method from a constructor?
11. How does polymorphism work with static methods?
12. Can you achieve polymorphism with private methods?
13. What is the Liskov Substitution Principle?
14. How does pattern matching for instanceof improve code?
15. What are the benefits of polymorphism in software design?
16. Can you overload the main method?
17. What is method hiding and how is it different from overriding?
18. Can constructors be overloaded?
19. How does polymorphism work with generics?
20. What is the difference between static and dynamic binding?

### 2.5 Abstraction

**Key Topics:**
- Abstract classes
- Abstract methods
- Interface definition and implementation
- Default methods in interfaces (Java 8+)
- Static methods in interfaces (Java 8+)
- Private methods in interfaces (Java 9+)
- Functional interfaces
- Multiple interface implementation
- Interface inheritance
- Marker interfaces
- When to use abstract class vs interface
- Interface segregation principle

**Common Questions:**
1. What is abstraction and why is it important?
2. What is the difference between abstract class and interface?
3. Can an abstract class have constructors?
4. Can you instantiate an abstract class?
5. When should you use an abstract class vs an interface?
6. What are default methods in interfaces and why were they introduced?
7. Can interfaces have static methods?
8. What is a functional interface?
9. Can a class implement multiple interfaces?
10. What happens if two interfaces have methods with the same signature?
11. What are marker interfaces? Give examples.
12. Can interfaces extend classes?
13. How many abstract methods can a functional interface have?
14. What is the diamond problem with default methods?
15. Can you have private methods in interfaces?
16. Can abstract classes implement interfaces?
17. Can an interface extend multiple interfaces?
18. What is the purpose of the Cloneable interface?
19. Can you have instance variables in interfaces?
20. How do you resolve conflicts with default methods?

---

## 3. JVM Internals & Performance

### 3.1 JVM Architecture

**Key Topics:**
- ClassLoader subsystem (Bootstrap, Extension, Application)
- Class loading process and delegation model
- Runtime Data Areas (Method Area, Heap, Stack, PC Register, Native Method Stack)
- Execution Engine (Interpreter, JIT Compiler, Garbage Collector)
- Java Native Interface (JNI)
- Method Area and Metaspace (Java 8+)
- String Pool location and management
- Direct memory and off-heap memory
- JVM startup and shutdown process
- Class file structure
- Bytecode basics

**Common Questions:**
1. Explain the JVM architecture in detail
2. What are the different components of JVM?
3. How does the class loading mechanism work?
4. What is the difference between heap and stack memory?
5. Where are static variables stored in JVM?
6. What is Metaspace and how is it different from PermGen?
7. What happens when a class is loaded into JVM?
8. Explain the delegation model in class loading
9. What is the role of the Execution Engine?
10. How does JIT compilation improve performance?
11. What is the difference between client and server JIT compilers?
12. Where is the String Pool located in memory?
13. What is direct memory and when is it used?
14. How do you analyze memory usage in JVM?
15. What tools can you use to inspect JVM internals?
16. What is the Native Method Stack?
17. How does the PC Register work?
18. What is bytecode verification?
19. Can you load a class multiple times?
20. What is the difference between JVM, JRE, and JDK?

### 3.2 Memory Model

**Key Topics:**
- Heap structure (Young Generation, Old Generation)
- Young Generation (Eden, Survivor S0, Survivor S1)
- Object promotion and aging
- Stack frames and local variables
- Method Area and class metadata
- Constant Pool
- Thread stack and stack overflow
- Heap overflow vs stack overflow
- Memory allocation strategies
- Escape analysis and stack allocation
- Compressed OOPs
- Tenuring threshold

**Common Questions:**
1. Explain the Java Memory Model
2. What are the different regions of heap memory?
3. How does object promotion work from Young to Old generation?
4. What causes OutOfMemoryError?
5. What is the difference between heap and non-heap memory?
6. How are objects allocated in Eden space?
7. What is the Survivor space and why do we need two of them?
8. What causes StackOverflowError?
9. How does the JVM decide to promote an object to Old generation?
10. What is escape analysis and how does it optimize memory?
11. Where are primitives stored - stack or heap?
12. How does the JVM handle large objects?
13. What is the purpose of the Constant Pool?
14. How can you increase heap or stack size?
15. What is the Metaspace and how much memory does it use?
16. What are compressed OOPs?
17. What is the tenuring threshold?
18. How much memory does a Java object header consume?
19. What is the difference between committed and reserved memory?
20. How do you detect heap fragmentation?

### 3.3 Garbage Collection

**Key Topics:**
- GC fundamentals and concepts
- Mark and Sweep algorithm
- Generational Garbage Collection
- Minor GC vs Major GC vs Full GC
- GC algorithms:
  - Serial GC
  - Parallel GC  
  - CMS (Concurrent Mark Sweep)
  - G1GC (Garbage First)
  - ZGC (Z Garbage Collector)
  - Shenandoah GC
  - Epsilon GC (No-Op)
- Stop-the-World events
- GC roots and reachability
- Finalization and phantom references
- GC tuning parameters
- GC logs analysis
- When to trigger GC programmatically
- Weak, Soft, and Phantom references

**Common Questions:**
1. How does garbage collection work in Java?
2. What are the different GC algorithms available?
3. When should you use G1GC vs CMS?
4. What is the difference between minor and major GC?
5. How do you tune garbage collection?
6. What are Stop-the-World events?
7. How does the Mark and Sweep algorithm work?
8. What are GC roots?
9. When is an object eligible for garbage collection?
10. Can you force garbage collection in Java?
11. What is the purpose of System.gc()?
12. How do you analyze GC logs?
13. What is the difference between G1GC and ZGC?
14. When would you use ZGC or Shenandoah?
15. What are the tuning parameters for G1GC?
16. How does CMS work and why was it deprecated?
17. What is a remembered set in G1GC?
18. How do you handle memory leaks that survive GC?
19. What is the throughput vs latency trade-off in GC?
20. How do WeakReferences help in memory management?

### 3.4 JIT Compilation

**Key Topics:**
- Just-In-Time compilation concepts
- Interpreter vs JIT compiler
- C1 (Client) vs C2 (Server) compilers
- Tiered compilation
- Hotspot detection
- Method inlining
- Dead code elimination
- Loop unrolling
- Escape analysis
- Code cache
- AOT (Ahead-Of-Time) compilation
- GraalVM and native images
- Deoptimization

**Common Questions:**
1. What is JIT compilation and how does it work?
2. What is the difference between interpreted and compiled code?
3. Explain tiered compilation in Java
4. What is method inlining and when does it occur?
5. How does the JVM decide which methods to compile?
6. What is the code cache and what happens when it's full?
7. What are the benefits of JIT compilation?
8. How does escape analysis optimize code?
9. What is AOT compilation and when would you use it?
10. What is GraalVM and how does it differ from HotSpot?
11. How do you monitor JIT compilation?
12. What are the trade-offs between interpreted and compiled code?
13. Can you disable JIT compilation?
14. What is loop unrolling and how does it improve performance?
15. How does inlining affect method calls?
16. What is deoptimization?
17. How does the JVM handle polymorphic calls?
18. What is the difference between C1 and C2 compilers?
19. How does branch prediction work?
20. What are compiler intrinsics?

### 3.5 Class Loading Mechanism

**Key Topics:**
- Class loading phases (Loading, Linking, Initialization)
- Linking sub-phases (Verification, Preparation, Resolution)
- ClassLoader hierarchy
- Custom ClassLoaders
- Context ClassLoader
- Class loading in web applications
- OSGi and module systems
- Class unloading and memory leaks
- NoClassDefFoundError vs ClassNotFoundException
- ClassLoader delegation principle
- Module system (Java 9+)

**Common Questions:**
1. Explain the class loading process in Java
2. What are the three phases of class loading?
3. What is the difference between ClassNotFoundException and NoClassDefFoundError?
4. How does the parent delegation model work?
5. When would you create a custom ClassLoader?
6. What is the context ClassLoader?
7. Can a class be loaded multiple times by different ClassLoaders?
8. How does class unloading work?
9. What are the different types of ClassLoaders?
10. How do you resolve ClassLoader-related issues?
11. What happens during the verification phase?
12. How does class initialization work?
13. What is the purpose of static initializer blocks?
14. Can you reload a class at runtime?
15. How does module system affect class loading in Java 9+?
16. What is a ClassLoader leak?
17. How do you detect ClassLoader memory leaks?
18. What is the difference between loadClass() and forName()?
19. Can a child ClassLoader see classes loaded by parent?
20. How does OSGi handle class loading?

---

## 4. Collections Framework Deep Dive

### 4.1 Collection Interfaces

**Key Topics:**
- Collection interface hierarchy
- Iterable and Iterator interfaces
- List, Set, Queue, Deque interfaces
- Map interface and its position in hierarchy
- SortedSet and NavigableSet
- SortedMap and NavigableMap
- Collection vs Collections
- Arrays vs Collections
- Immutable collections (Java 9+)
- Collection factory methods
- Spliterator interface
- Collection views

**Common Questions:**
1. What is the Collections Framework hierarchy?
2. What is the difference between Collection and Collections?
3. Why doesn't Map extend Collection?
4. What is the purpose of the Iterator interface?
5. How do you make a collection immutable?
6. What are the factory methods for creating immutable collections?
7. What is the difference between SortedSet and NavigableSet?
8. How do you iterate over a collection?
9. What is the fail-fast behavior of iterators?
10. When would you use Iterable vs Iterator?
11. What is the difference between arrays and collections?
12. How do you convert an array to a collection and vice versa?
13. What is the Spliterator interface?
14. How do streams work with collections?
15. What is the purpose of the ListIterator?
16. What are unmodifiable collections?
17. What is the difference between unmodifiable and immutable?
18. How do you create a synchronized collection?
19. What is the Collections utility class?
20. What are collection views?

(Content continues with sections 4.2 through 9.3, following the same detailed pattern with 15-25 key topics and 15-25 questions each)

---

**Note:** This file contains comprehensive coverage of Core Java topics 1-9. Each topic includes:
- Detailed key topics list (15-25 items)
- Comprehensive questions (15-25 per topic)
- Sub-sections for major topics
- Interview preparation focus

**Total Content Summary:**
- 9 Major Topics
- 42+ Sub-sections
- 380+ Key Topics
- 600+ Interview Questions
- Production-ready preparation material

**Continue to:** [PART-02-Spring-Ecosystem.md](PART-02-Spring-Ecosystem.md)

