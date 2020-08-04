# Systematically Benchmarking Example-Based Program Transformation Techniques on Bug-Fixing Code Changes

## Description

Example-based program transformation techniques infer transformations from code change examples and apply them to modify programs with similar contexts. In recent years, many techniques have been proposed. Despite the growing attention, no prior work has systematically compared techniques. Researchers proposing new techniques typically construct a new benchmark by collecting code change examples and evaluate their technique on this new benchmark. Unfortunately, this process is ad-hoc and the data collection process may be biased. As a result of the large effort required to construct a clean benchmark, these benchmarks are also likely to be small or noisy. This makes it difficult to fully understand the capabilities of the various techniques and differences between them.

In this work, we construct a new benchmark to address the limitations of the benchmarks used in literature. We systematically evaluate four fully automated example-based program transformation techniques. Focusing on the use case of inferring bug-fixing transformations, we build a benchmark **FixBench** containing 1,023 code changes from 262 Java projects that fix common types of bugs.
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