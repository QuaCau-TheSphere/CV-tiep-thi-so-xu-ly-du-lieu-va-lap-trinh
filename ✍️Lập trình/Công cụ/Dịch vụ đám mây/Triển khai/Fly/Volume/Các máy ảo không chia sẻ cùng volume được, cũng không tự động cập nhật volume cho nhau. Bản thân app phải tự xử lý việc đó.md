---
share: true
updated: 2026-08-14T14:10
created: 2026-08-11T15:42
---
Khái niệm:: 
It’s because whether this auto-syncing works or not depends _a lot_ on your app’s expectations. We can’t assume that a bog-standard userspace program works correctly when multi-homed and only filesystem data is synchronized (mind that this synchronization has its own consistency pitfalls; it probably can’t be immediately consistent). You wouldn’t be able to run any kind of database on this kind of volumes, for example, not even sqlite. So instead of “why volumes can’t be synchronized” we’d be receiving a lot of support requests about horribly broken apps when run on this kind of volumes instead.

This is not just a Fly Volumes limitation, most block storage products probably won’t do what you are describing here, and those that do probably do not function like a standard disk that most filesystems and apps expect of a block device. If your app requires less synchronization than a full block device + a POSIX filesystem on top, the product you’d be looking for is some kind of object storage and possibly a database to go along with it. If you still want something that looks like a local folder, you can use FUSE implementations to mount object storage at a local mountpoint, but then again, it will not look and behave like a block storage device.

There are definitely product discussions to be had about Fly Volumes, but so long as they stay a block storage product, honestly I do not see it offering any kind of auto-synchronization or multi-mount support.

Nguồn:: [Some questions on machine downtime and volume attachment - Questions / Help - Fly.io](https://community.fly.io/t/some-questions-on-machine-downtime-and-volume-attachment/28461/9?u=ooker)