# java-feature-timeline
* references
    * https://www.techgeeknext.com/java/java15-features

# java8
# java9
# java10
# java11
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