---
share: true
updated: 2026-08-14T00:19
created: 2026-08-09T20:32
---
Khái niệm:: 
Fly Volumes and Fly Machines are meant to be paired together, but they are not always found in pairs. A Fly Volume can be created without a Fly Machine, or a Machine can be destroyed without destroying its volume. In these cases, the volume that’s left is called an “unattached” volume.

A Fly Machine that does not require a volume will never attach itself to one. A Fly Machine that does require a volume will always be attached to one. When a volume is required according to the app or Machine configuration, any method of creating a new Fly Machine will pick up an unattached volume, create a new volume to attach, or it will fail (in the case of `fly machine` commands or create Machine API calls).

Trích từ:: [Fly Volumes overview · Fly Docs](https://fly.io/docs/volumes/overview/)