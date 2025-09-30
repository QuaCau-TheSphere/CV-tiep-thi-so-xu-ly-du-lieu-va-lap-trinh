---
share: true
created: 2023-10-30T14:29
updated: 2025-05-10T15:06
---
This table is labeled CPU Usage (Precise) to distinguish it from the CPU Usage (Sampled) data. The _sampled_ data comes from interrupting the CPU frequently – sampling – and seeing what it is doing. The _precise_ data that is discussed here comes from instrumenting the context switch code in the kernel. Every time a thread starts or stops running the precise time of this activity is recorded, with optional call stacks. This means that the CPU Usage (Precise) data can tell _exactly_ how much CPU time each thread consumes, and what the call stack looked like when a thread lost/gained the CPU. However the CPU Usage (Precise) data can’t tell you what a thread is doing between context switches – that is the job of the CPU Usage (Sampled) data. Understanding this difference is crucial.

Nguồn:: [The Lost Xperf Documentation–CPU Usage (Precise) \| Random ASCII – tech blog of Bruce Dawson](https://randomascii.wordpress.com/2012/05/11/the-lost-xperf-documentationcpu-scheduling/)