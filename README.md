[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

# java-feature-timeline
* references
    * https://www.techgeeknext.com/java/java15-features
    * https://www.techgeeknext.com/java/java14-features
    * https://mkyong.com/java/what-is-new-in-java-12/
    * https://openjdk.java.net/jeps
    * [Java 9 and Beyond by Venkat Subramaniam](https://www.youtube.com/watch?v=oRcOiGWK9Ts)
    * [Enough java.lang.String to Hang Ourselves... by Heinz Kabutz](https://www.youtube.com/watch?v=DcLQm2EpDI0)
    * [Java Futures, Devoxx 2018 Edition by Brian Goetz](https://www.youtube.com/watch?v=4r2Wg-TY7gU)
    * [JDK11 - Introduction to JDK Flight Recorder](https://www.youtube.com/watch?v=7z_R2Aq-Fl8)
    * https://www.baeldung.com/java-16-new-features
    * https://www.baeldung.com/java-17-new-features
    * https://adevait.com/java/whats-new-with-java-18
    * https://en.wikipedia.org/wiki/Java_version_history
    * https://openjdk.org/jeps

## java8
* Java Date Time API
* Streams
* Functional Interfaces, Lambda expressions
* default & static methods in interfaces
* hashmap implementation (TreeSet in buckets instead of LinkedList)
* CompletableFuture

## java9
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
* JEP 243: Java-Level JVM Compiler Interface
    * Develop a Java based JVM compiler interface (JVMCI) enabling a compiler written in Java to be used 
    by the JVM as a dynamic compiler.
* StringConcatFactory (instead compiling to StringBuilder)
    * https://github.com/mtumilowicz/java9-string-concat
* String LATIN-1 (char[] replaced with byte[])
    * https://github.com/mtumilowicz/java11-string

## java10
* Local-Variable Type Inference
* Enable the HotSpot VM to allocate the Java object heap on an alternative memory device
* List/Set/Map.copyOf() // no null elements
* Experimental Java-based JIT compiler (GraalVM)

## java11
* Local-Variable Syntax for Lambda Parameters
  * @NotNull Integer i -> ... into @NotNull var i ->
  * final Integer i -> ... into final var i
* Remove the Java EE and CORBA Modules
* Optional.isEmpty()
* Predicate.not
* String changes: lines, repeat, isBlank, strip
* JEP 318: Epsilon: A No-Op Garbage Collector
* JEP 321: HTTP Client (Standard)
* ZGC: A Scalable Low-Latency Garbage Collector(Experimental)
* JEP 328: Flight Recorder
    * illuminate the JVM "black box" for key insights
    * unified view over system-wide interactions and relations
    * GC, Monitors, JIT compilations, class loading, I/O, native memory...

## java12
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
* JEP 12: new risk-reduction mechanism: Preview Features 

## java13
* ZGC: Uncommit Unused Memory
* Reimplement the Legacy Socket API
* Switch Expressions (Second Preview)
* Text Blocks (Preview)

## java14
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

## java15
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

## java 16
* InvocationHandler.invokeDefault(prox, method, args)
    * invoking default methods of an interface via a dynamic proxy using reflection
* `.stream().toList() // instead of .collect(Collectors.toList())`
* defining records as class members of inner classes
* instanceof with casting
    ```
    if (obj instanceof String t) {
        // t is a string
    }
    ```

## java 17
* prevent JDK users from accessing internal APIs, except for critical ones like sun.misc.Unsafe
* pattern matching in switch (preview)
    ```
    static String formatterPatternSwitch(Object o) {
        return switch (o) {
            case null      -> System.out.println("Oops");
            case Integer i -> String.format("int %d", i);
            case Long l    -> String.format("long %d", l);
            case Double d  -> String.format("double %f", d);
            case String s  -> String.format("String %s", s);
            default        -> o.toString();
        };
    }
    ```
    instead of
    ```
    static String formatter(Object o) {
        String formatted = "unknown";
        if (o instanceof Integer i) {
            formatted = String.format("int %d", i);
        } else if (o instanceof Long l) {
            formatted = String.format("long %d", l);
        } else if (o instanceof Double d) {
            formatted = String.format("double %f", d);
        } else if (o instanceof String s) {
            formatted = String.format("String %s", s);
        }
        return formatted;
    }
    ```
    and for interfaces
    ```
    static void testTriangle(Shape s) {
        switch (s) {
            case Triangle t && (t.calculateArea() > 100) ->
                System.out.println("Large triangle");
            default ->
                System.out.println("A shape, possibly a small triangle");
        }
    }
    ```
* sealed classes
* remove Ahead-Of-Time (AOT) compilation (JEP 295) and Just-In-Time (JIT) compiler from GraalVM (JEP-317)
* Foreign Function and Memory API allow Java developers to access code from outside the JVM and manage memory out of the heap
    * replace the JNI API and improve the security and performance compared to the old one

## java 18
* default charset for the String and related classes has been updated to UTF-8
    * example
       ```
       // Default charset is UTF-8
       byte[] byteArray = myString.getBytes();
       ```
    * before: JDK determined the default charset based on the runtime environment
* reimplemented core reflection with method handles
    * `java.lang.reflect` implemented using `java.lang.invoke`
    * example
        ```
        import java.lang.reflect.*;

        Method method = MyClass.class.getMethod("myMethod");
        method.invoke(null);
        ```
        under the hood looks like
        ```
        import java.lang.invoke.*;

        MethodHandles.Lookup lookup = MethodHandles.lookup();
        MethodHandle methodHandle = lookup.findStatic(MyClass.class, "myMethod", MethodType.methodType(void.class));
        methodHandle.invoke();
        ```
* finalization mechanism, provided by the `Object.finalize()` method, has been deprecated for removal in a future release

## java 19
* preview
    * record patterns to deconstruct record values
    * foreign function & memory api
        * API by which Java programs can interoperate with code and data outside of the Java runtime
        * example
            ```
            Linker linker          = Linker.nativeLinker();
            SymbolLookup stdlib    = linker.defaultLookup();
            MethodHandle radixsort = linker.downcallHandle(stdlib.find("radixsort"), ...);
            ```
    * virtual threads
    * pattern matching for switch

## java 20
* finals preview for java 19

## java 21
* sequenced collections
    * new interfaces to represent collections with a defined order
    * example
        ```
        interface SequencedCollection<E> extends Collection<E> {
            // new method
            SequencedCollection<E> reversed();
            // methods promoted from Deque
            void addFirst(E);
            void addLast(E);
            E getFirst();
            E getLast();
            E removeFirst();
            E removeLast();
        }
        ```
* generational ZGC
    * extending the Z Garbage Collector (ZGC) to maintain separate generations for young and old objects
* record patterns
    ```
    static void printSum(Object obj) {
        if (obj instanceof Point(int x, int y)) {
            System.out.println(x+y);
        }
    }
    ```
* pattern matching for switch
    ```
    static String formatterPatternSwitch(Object obj) {
        return switch (obj) {
            case Integer i -> String.format("int %d", i);
            case Long l    -> String.format("long %d", l);
            case Double d  -> String.format("double %f", d);
            case String s  -> String.format("String %s", s);
            default        -> obj.toString();
        };
    }
    ```
* virtual threads
* preview
    * string templates
        ```
        String name    = "Joan Smith";
        String phone   = "555-123-4567";
        String address = "1 Maple Drive, Anytown";
        String json = STR."""
            {
                "name":    "\{name}",
                "phone":   "\{phone}",
                "address": "\{address}"
            }
            """;
        ```
    * foreign function & memory api
    * unnamed patterns and variables
        * patterns
            ```
            switch (b) {
                case Box(RedBall _), Box(BlueBall _) -> processBox(b);
                case Box(GreenBall _)                -> stopProcessing();
                case Box(_)                          -> pickAnotherBox();
            }
            ```
        * variables
            ```
            stream.collect(Collectors.toMap(String::toUpperCase, _ -> "NODATA"))
            ```
    * unnamed classes and instance main methods
        * main methods are not static, need not be public, and need not have a String[] parameter
            ```
            class HelloWorld {
                void main() {
                    System.out.println("Hello, World!");
                }
            }
            ```
        * unnamed classes make the class declaration implicit
            ```
            void main() {
                System.out.println("Hello, World!");
            }
            ```
    * scoped values
        * is an implicit method parameter preferred to thread-local variables
        * example
            ```
            private final static ScopedValue<FrameworkContext> CONTEXT
                                    = ScopedValue.newInstance();

            void serve(Request request, Response response) {
                var context = createContext(request);
                ScopedValue.where(CONTEXT, context)            // (2)
                           .run(() -> Application.handle(request, response));
            }
            ```
    * structured concurrency
        ```
        try (var scope = new StructuredTaskScope.ShutdownOnFailure()) {
            List<? extends Supplier<T>> suppliers = tasks.stream().map(scope::fork).toList();
            scope.join()
                 .throwIfFailed();  // Propagate exception if any subtask fails
            // Here, all tasks have succeeded, so compose their results
            return suppliers.stream().map(Supplier::get).toList();
        }
        ```
