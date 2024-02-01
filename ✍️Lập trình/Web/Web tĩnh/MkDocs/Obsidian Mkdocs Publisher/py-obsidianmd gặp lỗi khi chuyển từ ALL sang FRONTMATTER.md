---
share: true
created: 2023-10-20T00:18
updated: 2023-10-31T22:26
---
Chuyển từ frontmatter sang dạng inline thì được:
```python
notes.metadata.move(fr=MetadataType.FRONTMATTER, to=MetadataType.INLINE)
notes.update_content(inline_inplace=False, inline_position="top", inline_tml="standard") #type: ignore
ghi chú.write()
```
Làm ngược lại từ inline sang frontmatter cũng được. Tuy nhiên, `ALL` → `FRONTMATTER` thì không được. `INLINE`→`FRONTMATTER` vẫn hoạt động. 
```python
notes.metadata.move(fr=MetadataType.ALL, to=MetadataType.FRONTMATTER)
notes.update_content(inline_inplace=False, inline_position="top", inline_tml="standard") #type: ignore
ghi chú.write()
```
 https://selimrbd.github.io/py-obsidianmd/examples/
[`ALL` → `INLINE` works, `ALL` → `FRONTMATTER` doesn't. `INLINE`→`FRONTMATTER` still works. · Issue #24 · selimrbd/py-obsidianmd](https://github.com/selimrbd/py-obsidianmd/issues/24 "`ALL` → `INLINE` works, `ALL` → `FRONTMATTER` doesn't. `INLINE`→`FRONTMATTER` still works. · Issue #24 · selimrbd/py-obsidianmd")
