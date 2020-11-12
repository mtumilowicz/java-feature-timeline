# java-feature-timeline
* references
    * https://www.techgeeknext.com/java/java15-features
    * https://www.techgeeknext.com/java/java14-features
    * https://mkyong.com/java/what-is-new-in-java-12/
    * [Java 9 and Beyond by Venkat Subramaniam](https://www.youtube.com/watch?v=oRcOiGWK9Ts)

# java8
* Java Date Time API
* Streams
* Functional Interfaces, Lambda expressions
* default & static methods in interfaces
* hashmap implementation (TreeSet in buckets instead of LinkedList)
* CompletableFuture

# java9
* module system
  * replace the classpath with graph of dependencies
* factory Methods for Immutable List, Set, Map and Map.Entry
* private methods in Interfaces
* reactive Streams
* `Optional.ifPresentOrElse(Consumer<? super T> action, Runnable emptyAction)`, `Optional.stream()`
* deprecate `finalize()` method
* not valid: underscore _
    * international meaning: I DON'T CARE (scala)
* stream enhancements
    * `takeWhile`, `dropWhile`
    * `iterate(seed, Predicate, Function)` ~ `for(seed, Predicate, Function)`
    * `or(() -> Optional.of(substitute))`
* optional enhancements
    * `Optional.ifPresentOrElse(Consumer<? super T> action, Runnable emptyAction)`
    * is a subset of Stream: `optional.stream()`
        * 0, 1 elem; Stream, 0, 1, many
* collectors: filtering, flatMapping
* CompletableFuture: completeOnTimeout, orTimeout

# java10
* Local-Variable Type Inference
* Enable the HotSpot VM to allocate the Java object heap on an alternative memory device
* List/Set/Map.copyOf() // no null elements

# java11
* Local-Variable Syntax for Lambda Parameters
  * @NotNull Integer i -> ... into @NotNull var i ->
  * final Integer i -> ... into final var i
* Remove the Java EE and CORBA Modules
* Optional.isEmpty()
* Predicate.not
* String changes: lines, repeat, isBlank, strip
* 318: Epsilon: A No-Op Garbage Collector
* 321: HTTP Client (Standard)
* ZGC: A Scalable Low-Latency Garbage Collector(Experimental)
  
# java12
* JEP 189: Shenandoah: A Low-Pause-Time Garbage Collector (Experimental)
* JEP 325: Switch Expressions (Preview)
    ```
    private static String getText(int number) {
            return switch (number) {
                case 1, 2 -> "one or two";
                case 3 -> "three";
                case 4, 5, 6 -> "four or five or six";
                default -> "unknown";
            };
    }
    ```
* JEP 334: JVM Constants API
    * new classes and interfaces to model the key class-file and run-time artifacts, for example, the constant pool
* JEP 344: Abortable Mixed Collections for G1
    * splits the problematic collection set into two parts – mandatory and optional
        * the G1 will abort the optional part if lack of time to handle it
* JEP 346: Promptly Return Unused Committed Memory from G1
    * if the application is low of the activity or idle, G1 periodically trigger a concurrent cycle to 
    determine overall Java heap usage and return unused Java heap memory to the operating system

# java13
* ZGC: Uncommit Unused Memory
* Reimplement the Legacy Socket API
* Switch Expressions (Second Preview)
* Text Blocks (Preview)

# java14
* Text Blocks (Second Preview)
* Remove the Concurrent Mark Sweep (CMS) Garbage Collector
* Records (Preview)
* Switch Expressions (Standard)
* Helpful NullPointerExceptions
    ```
    Exception in thread "main" java.lang.NullPointerException:
            Cannot read field 'c' because 'a.b' is null.
        at Prog.main(Prog.java:5)
    ```
* Pattern Matching for instanceof (Preview)

# java15
* JEP 360: Sealed Classes (Preview)
    ```
    public sealed class Animal 
        permits Dog, Monkey, Leopard {...}
    ```
* JEP 371: Hidden Classes
    * are classes which can not be used directly by the bytecode of other classes
    * intended to be used by frameworks that generates classes at runtime and use them indirectly through reflection
* JEP 375: Pattern Matching for instanceof (Second Preview)
    ```
    if (obj instanceof String) {
        String str = (String) obj;
        ... str.contains(..) ...
    }else{
         ...
    }
    ```
    ```
    if (obj instanceof String str) {
        ... str.contains(..) ... // no need to cast
    } else {
        // str is not in the scope
    }
    ```
* JEP 377: ZGC: A Scalable Low-Latency Garbage Collector
    * production feature
* JEP 379: Shenandoah: A Low-Pause-Time Garbage Collector
    * production feature
* JEP 378: Text Blocks
    ```
    String html = """
        <html>
            <body>
                <p>Hello, world</p>
            </body>
        </html>
        """;
    ```
    * multi-line string literals
    * unlocks HTML, XML, SQL, or JSON snippet into a code
* JEP 383: Foreign-Memory Access API (Second Incubator)
    * an API for Java programs to access foreign memory outside the Java heap in a secure and efficient way
* JEP 384: Records (Second Preview)