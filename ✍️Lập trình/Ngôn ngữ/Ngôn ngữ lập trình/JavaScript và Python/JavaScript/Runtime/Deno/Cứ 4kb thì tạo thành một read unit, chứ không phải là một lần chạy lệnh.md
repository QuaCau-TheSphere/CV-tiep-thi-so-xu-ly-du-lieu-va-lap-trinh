---
share: true
created: 2023-10-30T14:29
updated: 2024-08-24T12:42
---
It's one unit per 4kb of read. If you read a 2kb record this is 1 read unit. If you read 4.1kb record then it's 2 read units. If you use the list function and read 10 records and their total size is 3kb, then this is 1 read unit in total.

Nguồn:: [Deno Deploy Pricing | Deno](https://deno.com/deploy/pricing)