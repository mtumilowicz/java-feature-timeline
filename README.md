# java-feature-timeline
* references
    * https://www.techgeeknext.com/java/java15-features
    * https://www.techgeeknext.com/java/java14-features

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
  
# java12
# java13
# java14
# java14
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