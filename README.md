Sample project demonstrating that log4j 2.12.1 doesn't work with GraalVM 19.3.0 CE.

`mvn exec:exec` runs the `App` and generates native-image config using native-image-agent

`mvn verify` tries to build the `App` and native-image, but fails with

```$bash
Error: Unsupported features in 11 methods
Detailed message:
Error: Field org.apache.logging.log4j.core.impl.ContextDataFactory.EMPTY_STRING_MAP has declared type org.apache.logging.log4j.util.StringMap which is incompatible with types in state: MTypeMObject<5347:
...
Call path from entry point to org.apache.logging.log4j.core.impl.Log4jLogEvent.<init>(String, Marker, String, Level, Message, Throwable, ThrowableProxy, StringMap, ThreadContext$ContextStack, long, String, int, StackTraceElement, long, int, long, Log4jLogEvent$1): 
	at org.apache.logging.log4j.core.impl.Log4jLogEvent.<init>(Log4jLogEvent.java:53)
```