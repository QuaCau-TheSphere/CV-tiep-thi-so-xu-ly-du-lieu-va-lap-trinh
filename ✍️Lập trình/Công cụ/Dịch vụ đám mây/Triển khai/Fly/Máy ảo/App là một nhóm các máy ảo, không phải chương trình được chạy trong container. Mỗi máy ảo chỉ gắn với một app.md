---
share: true
updated: 2026-08-14T14:22
created: 2026-08-11T17:46
---
Khái niệm:: 
It seems to me take that because a group of machines serving one same program share the same IP address regardless of their actual regions, Fly decided to name that group as “app”, and provide “volume” to attach to that app. On high-level, this preserves the mental model of how Docker works, and I like it. However, when you uncover the abstraction, then the analogy breaks down:

- In Docker, the app runs inside a container, which runs inside a VM, which runs inside a physical machine. In this scenario, thinking that your volume is always there storing data for your program is reasonable, because it only runs in one physical machine.
- But in Fly, what the app actually do is to control the VMs inside different physical machines, which will then control the containers, which will then run the program. In this scenario, you cannot think that your volume is always available to your program, because it runs on different physical machines.

I guess this is the difference in how we view what app is in the development phase and deployment phase.

Nguồn:: [Some questions on machine downtime and volume attachment - Questions / Help - Fly.io](https://community.fly.io/t/some-questions-on-machine-downtime-and-volume-attachment/28461/7?u=ooker)