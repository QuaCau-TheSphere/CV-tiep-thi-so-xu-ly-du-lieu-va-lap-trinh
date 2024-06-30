---
share: true
created: 2023-10-30T14:29
updated: 2024-04-23T01:41
---
Git essentially has 4 main statuses for the files in your local repo:
- **untracked:** The file is new, Git knows nothing about it. If you `git add <file>`, it becomes:
- **staged:** Now Git knows the file (tracked), but also made it part of the next commit batch (called the _index_). If you `git commit`, it becomes:
- **unchanged:** The file has not changed since its last commit. If you _modify it_, it becomes:
- **unstaged:** Modified but not part of the next commit yet. You can stage it again with `git add`

As you can see, a `git add` will **track** untracked files, and **stage** any file.

_Also: You can untrack an uncommited file with `git rm --cached filename` and unstage a staged file with `git reset HEAD <file>`_

Nguồn:: [[✍️Lập trình/Ξ Nguồn và tài nguyên hỗ trợ/Ξ Nguồn/Stack Overflow]], [Concept of git tracking and git staging](https://stackoverflow.com/a/15803429/3416774)