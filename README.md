# Systematically Benchmarking Example-Based Program Transformation Techniques on Bug-Fixing Code Changes

## Description

Example-based program transformation techniques infer transformations from code change examples and apply them to modify programs with similar contexts.
In this work, we systematically evaluate four fully automated example-based program transformation techniques.
We construct a new benchmark to address limitations, e.g., limited scale and noisy data, of the benchmarks used in literature.
Focusing on the use case of inferring bug-fixing transformations, we build a benchmark **FixBench** containing 1,023 code changes from 262 Java projects that fix common types of bugs.
To obtain high quality data, we use a systematic manual labeling process to filter noise.
Using an applicable subset of our benchmark, we evaluate four techniques: **Sydit** and **Genpat**, which learn transformations from a single example, and **Lase** and **Genesis**, which learn from multiple examples. They are evaluated in two aspects: (1) Can they learn bug-fixing transformations and fix buggy programs correctly? (2) Do they extraneously modify bug-free programs?
Prior studies only evaluate techniques in the first aspect but miss out on the second aspect, which is equally critical. For the second, we compute the extraneous transformation rate (ETR).
Our results reveal that there is no technique that outperforms the others in both aspects.
As a whole, we find there is much room for improvement.
We propose a number of directions for future research.


## Benchmark: **FixBench** [[Homepage](https://github.com/Example-based-Program-Transformation/FixBench)]

An Example Code Change for Fixing Null Pointer Dereference in **FixBench** [[Original GitHub](https://github.com/orientechnologies/orientdb/commit/529e81f4211096e6468a51d8bbd8968b60156762)]

```diff
diff --git a/core/src/main/java/com/orientechnologies/orient/core/db/document/ODatabaseDocumentTx.java b/core/src/main/java/com/orientechnologies/orient/core/db/document/ODatabaseDocumentTx.java
index c9ff80d..8b733ad 100755
--- a/core/src/main/java/com/orientechnologies/orient/core/db/document/ODatabaseDocumentTx.java
+++ b/core/src/main/java/com/orientechnologies/orient/core/db/document/ODatabaseDocumentTx.java
@@ -251 +251 @@ public class ODatabaseDocumentTx extends OListenerManger<ODatabaseListener> impl
-        if (!name.equals(iUserName)) {
+        if (name== null || !name.equals(iUserName)) {
```



## Selected Techniques

### Single Example-based Technique

* Sydit [[Code](https://github.com/Example-based-Program-Transformation/Sydit)] [[Virtual Machine]()]
* Genpat [[Code](https://github.com/Example-based-Program-Transformation/Genpat)] [[Virtual Machine]()]


### Multiple Example-based Technique

* Lase [[Code](https://github.com/Example-based-Program-Transformation/Lase)] [[Virtual Machine]()]
* Genesis [[Code](https://github.com/Example-based-Program-Transformation/Genesis)] [[Virtual Machine]()]