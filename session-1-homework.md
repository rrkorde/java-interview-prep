# Session 1 Homework - JVM Architecture Mastery

**Assigned:** January 11, 2026
**Due:** Before Session 2
**Estimated Time:** 2-3 hours
**Topics Covered:** ClassLoader, Memory Model, JIT Compilation, Metaspace

---

## Instructions

Complete the following assignments to solidify your understanding of Session 1 topics. These exercises are designed to:
1. Reinforce concepts learned in Session 1
2. Apply knowledge to real-world scenarios
3. Prepare you for advanced topics in Session 2

**Submit your answers by:**
- Creating a file: `session-1-homework-answers.md`
- Include code snippets, explanations, and diagrams where helpful

---

## Assignment 1: ClassLoader Deep Dive (45 minutes)

### Task 1.1: Custom ClassLoader Implementation

Create a custom `PluginClassLoader` that:
- Loads plugin JARs from a specific directory
- Implements parent-last delegation (child-first loading)
- Provides a method to unload plugins and release memory

**Requirements:**
```java
public class PluginClassLoader extends URLClassLoader {
    // Implement child-first delegation
    // Add method: void unloadPlugin()
    // Add method: boolean isPluginLoaded(String className)
}
```

**Questions:**
1. Why might you want child-first delegation in a plugin system?
2. How do you ensure the ClassLoader is garbage collected after unloading?
3. What happens if two plugins have the same class name?

---

### Task 1.2: Dependency Conflict Resolution

Given this scenario:
```
Your app uses jackson-databind-2.15.0
Payment-lib-v1 uses jackson-databind-2.12.0
Payment-lib-v2 uses jackson-databind-2.14.0
```

**Questions:**
1. Draw the dependency tree showing which version gets loaded
2. Provide THREE different solutions to handle this conflict
3. Which solution would you recommend for a production fintech application? Why?

---

## Assignment 2: Memory Model Mastery (45 minutes)

### Task 2.1: Memory Layout Analysis

Analyze the following code and answer questions:

```java
public class PaymentService {
    private static final String SERVICE_NAME = "PaymentService";
    private static List<Transaction> transactionCache = new ArrayList<>();
    private static int counter = 0;

    private String merchantId;
    private volatile boolean isActive = true;

    public void processPayment(double amount) {
        final int MAX_RETRIES = 3;
        String transactionId = UUID.randomUUID().toString();

        for (int i = 0; i < MAX_RETRIES; i++) {
            Transaction tx = new Transaction(transactionId, amount);
            transactionCache.add(tx);
            counter++;
        }
    }
}
```

**Questions:**
1. Draw the complete memory layout showing Method Area (Metaspace), Heap, and Stack
2. For EACH variable, specify:
   - Where is the reference/metadata stored?
   - Where is the actual value/object stored?
3. Identify TWO potential memory leaks in this code
4. Explain why `volatile boolean isActive` needs to be on the Heap

---

### Task 2.2: Integer Caching Challenge

What is the output of this code? Explain WHY for each comparison:

```java
public class IntegerCacheTest {
    public static void main(String[] args) {
        Integer a = 100;
        Integer b = 100;
        Integer c = 200;
        Integer d = 200;

        Integer e = new Integer(100);
        Integer f = Integer.valueOf(100);

        System.out.println("a == b: " + (a == b));           // Q1: true or false?
        System.out.println("c == d: " + (c == d));           // Q2: true or false?
        System.out.println("a == e: " + (a == e));           // Q3: true or false?
        System.out.println("a == f: " + (a == f));           // Q4: true or false?
        System.out.println("a.equals(e): " + (a.equals(e))); // Q5: true or false?

        // Bonus: How would you change the caching range?
    }
}
```

---

## Assignment 3: JIT Compilation & Performance (45 minutes)

### Task 3.1: JVM Warm-up Script

Write a production-ready warm-up script for a payment service that:
1. Warms up at least 3 critical paths
2. Reaches 15,000 invocations (for C2 compilation)
3. Prints progress every 1,000 invocations
4. Includes error handling

**Deliverable:**
```java
public class PaymentServiceWarmup {
    public static void main(String[] args) {
        // Your implementation here
    }
}
```

**Additional Questions:**
1. How would you integrate this with Kubernetes readinessProbe?
2. What JVM flags would you add to verify warm-up is working?
3. How long should the warm-up take (estimate)?

---

### Task 3.2: Deoptimization Diagnosis

Given this production log:

```
[15:00:00] made not entrant - PaymentProcessor::process (50 times/minute)
[15:00:00] P99 latency: 300ms (was 40ms)
[15:00:00] CPU: 85% (was 40%)
```

**Questions:**
1. What is the likely root cause?
2. Provide THREE potential code patterns that could cause this
3. Show the code fix for at least ONE of your examples
4. How would you prevent this in the future (code review checklist)?

---

### Task 3.3: Monomorphic vs Polymorphic Performance

Refactor this code to improve JIT optimization:

```java
public class PaymentProcessor {
    public void processPayments(List<Payment> payments) {
        for (Payment p : payments) {
            PaymentProvider provider = getProvider(p.getType());
            provider.process(p);  // Polymorphic call - 10 different types!
        }
    }
}
```

**Deliverable:**
- Show BEFORE and AFTER code
- Explain why your refactoring is faster
- Estimate the performance improvement (e.g., 2x, 5x)

---

## Assignment 4: Metaspace & Production Issues (30 minutes)

### Task 4.1: Metaspace OOM Prevention

Configure JVM flags for a Spring Boot microservice with these characteristics:
- 50 classes on startup
- Uses Spring Boot, Hibernate, Jackson
- Implements dynamic proxy generation (but limited)
- Runs in Kubernetes with 4 GB memory limit

**Questions:**
1. What `-XX:MetaspaceSize` and `-XX:MaxMetaspaceSize` would you set?
2. What heap size (`-Xms`, `-Xmx`) would you configure?
3. Why is it important to set MaxMetaspaceSize in production?

---

### Task 4.2: ClassLoader Leak Detection

You notice Metaspace growing 50 MB per deployment. Identify the leak:

```java
public class ServiceReloader {
    private static List<Object> services = new ArrayList<>();

    public void reload() {
        URLClassLoader loader = new URLClassLoader(getJars());
        Class<?> clazz = loader.loadClass("PaymentService");
        Object instance = clazz.newInstance();
        services.add(instance);  // Store for later use
    }
}
```

**Questions:**
1. What is leaking and why?
2. Show the corrected code
3. How would you detect this in production before it becomes critical?

---

## Assignment 5: Real-World Fintech Scenario (15 minutes)

### Task 5.1: Share Your Experience

Based on your 8.5 years in fintech, write a short scenario (200-300 words) describing:

1. **A production issue** you encountered related to ANY of these topics:
   - ClassLoader conflicts
   - Memory leaks
   - Performance degradation
   - JVM tuning

2. **Include:**
   - What was the symptom?
   - How did you diagnose it?
   - What was the root cause?
   - How did you fix it?
   - What did you learn?

This will help you prepare STAR method examples for behavioral interviews!

---

## Bonus Challenges (Optional)

### Bonus 1: Performance Benchmark

Write a micro-benchmark comparing:
- ArrayList vs LinkedList (add, get, remove operations)
- HashMap vs TreeMap (put, get operations)
- String concatenation: `+` vs `StringBuilder` vs `String.join()`

Use JMH (Java Microbenchmark Harness) if possible.

---

### Bonus 2: GC Log Analysis

Download GC logs from a running application and analyze:
- How many Minor GC vs Major GC events?
- What is the average GC pause time?
- Is there a memory leak (increasing Old Gen usage)?

---

## Submission Checklist

Before Session 2, ensure you've completed:

- [ ] Assignment 1: Custom ClassLoader (Task 1.1 + 1.2)
- [ ] Assignment 2: Memory Model (Task 2.1 + 2.2)
- [ ] Assignment 3: JIT & Performance (Task 3.1 + 3.2 + 3.3)
- [ ] Assignment 4: Metaspace (Task 4.1 + 4.2)
- [ ] Assignment 5: Real-world scenario
- [ ] Created `session-1-homework-answers.md` file
- [ ] Code compiles and runs (where applicable)

---

## Grading Rubric

**Excellent (90-100%):**
- All assignments completed with detailed explanations
- Code is correct, well-structured, and production-ready
- Deep understanding demonstrated
- Bonus challenges attempted

**Good (75-89%):**
- Most assignments completed correctly
- Some minor errors or missing explanations
- Good understanding demonstrated

**Needs Improvement (<75%):**
- Multiple assignments incomplete
- Significant conceptual errors
- Surface-level understanding

---

## Tips for Success

1. **Don't just memorize** - Understand WHY things work the way they do
2. **Test your code** - Run examples and verify output
3. **Draw diagrams** - Visual memory layouts help understanding
4. **Relate to experience** - Connect concepts to your fintech work
5. **Ask questions** - If stuck, note questions for Session 2

---

## Resources

**For ClassLoader:**
- Oracle Java Documentation: ClassLoader API
- Baeldung: Custom ClassLoader tutorial

**For Memory Model:**
- Java Memory Management (Oracle)
- JVM Specification Chapter 2

**For JIT:**
- JVM flag: `-XX:+PrintCompilation`
- Article: "Understanding JIT Compilation"

**For Metaspace:**
- Java 8 Migration Guide
- JVM Tuning Guide

---

**Good luck!** These exercises will cement your Session 1 knowledge and prepare you for Session 2's deep dive into Garbage Collection!

**Questions?** Note them down and we'll review at the start of Session 2.

---

**Estimated completion time: 2-3 hours**
**Difficulty: Intermediate to Advanced**
**Focus: Practical application and production scenarios**
