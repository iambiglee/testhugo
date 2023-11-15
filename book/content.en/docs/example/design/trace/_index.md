---
weight: 5
title: "Trace"
---
# Design of Tracing

## Tracing
For the project's tracing, the internal built-in solution is Meituan's Cat, serving as the project's tracing service. CatMQ's client and server support automatic Cat instrumentation. If your company also uses Cat, simply include cat-client in the pom, and automatic tracing will begin.
If Cat is not used, there's no need to worry. If cat-client is not included, CatMQ will not activate Cat instrumentation. Alternatively, you can use Skywalking (may the force be with you) with the javaagent approach for monitoring the trace.
For other tracing software, due to resource and time constraints, there is no corresponding testing. Contributions of other tracing solutions are welcome.

## Metrics
For performance monitoring, CatMQ automatically integrates with Metrics. Metrics are mainly used in the project to monitor the quantity of messages. If your company has set up Prometheus, just include the micrometer-registry-Influx dependency in the pom, and the Metrics data can be imported.