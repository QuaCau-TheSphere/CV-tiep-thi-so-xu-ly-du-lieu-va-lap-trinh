---
share: true
created: 2023-10-30T14:29
updated: 2024-05-13T22:08
---
When you list from KV it doesn't pull back everything at once. Instead it pulls results in batches (size is configurable). Thus, you iterate over results in an asynchronous manner as some iterations will fetch data. This allows you to process data as you retrieve it and not have to wait until it is all fetched.

In essence, it's not pulling an array but iterating over a remote data source. You could view KV as one giant array and list iterates over a sub section of that. It would be inefficient to have to wait until all data was downloaded before using it. Thus the async iterator to allow downloading AND processing at the same time.
Nguồn:: [How to list all entries in Deno KV?](https://stackoverflow.com/a/78210091/3416774)