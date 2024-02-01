---
share: true
created: 2023-10-19T23:29
updated: 2023-11-15T21:50
---
Ezlink là plugin cho Mkdocs để chuyển từ dạng `[[wikilink]]` sang dạng `[MDlink]()`. Nó được để mặc định trong GitHub Publisher. Nó có nhiều lỗi. Ví dụ, với `mkdocs.yml`:
```yaml
site_name: test
plugins:
  - ezlinks:
        wikilinks: true
```

Và cấu trúc thư mục ban đầu:
```
docs/ 
├── index.md 
└── a/ 
	└── index.md
```

Sau khi dựng ta sẽ có:
```
site/ 
├── index.html
└── a/ 
	└── index.html
```

Nếu trong `docs/index.md` bạn có nội dung sau:
```markdown
[[a/index]]
[[a/index.md]]
[[./a/index]]
[[./a/index.md]]
```
Thì ở `site/index.html` sẽ ra kết quả html như sau:
```html
| docs/index.md    | site/index.html                                    | Trỏ đúng |
| ---------------- | -------------------------------------------------- | -------- |
| [[a/index]]      | <a href="a/" title="a/index">a/index</a>           | ✔        |
| [[a/index.md]]   | <a href="a/" title="a/index.md">a/index.md</a>     | ✔        |
| [[./a/index]]    | <a href="a/index" title="./a/index">./a/index</a>  | ❌        |
| [[./a/index.md]] | <a href="a/" title="./a/index.md">./a/index.md</a> | ✔       |
```

Đồng thời Mkdocs sẽ báo như sau:
```
INFO    -  Doc file 'index.md' contains an
           unrecognized relative link
           'a/index', it was left as is. Did  
           you mean 'a/index.md'?
```

Đây là các bug khác:

- [Incorrect path doesn't stay incorrectly, but automatically is replaced with a different path](https://github.com/Lisandra-dev/mkdocs-ezlinked-plugin/issues/3 "Incorrect path doesn't stay incorrectly, but automatically is replaced with a different path · Issue #3 · Lisandra-dev/mkdocs-ezlinked-plugin")
- [Expecting `[[./a/index]]` to return `<a href="a/"`, get `<a href="a/index"`](https://github.com/Lisandra-dev/mkdocs-ezlinked-plugin/issues/2 "Expecting `[[./a/index]]` to return `&lt;a href=&quot;a/&quot;`, get `&lt;a href=&quot;a/index&quot;` · Issue #2 · Lisandra-dev/mkdocs-ezlinked-plugin")
- [Correct MD path with unicode characters doesn't render correct HTML path](https://github.com/Lisandra-dev/mkdocs-ezlinked-plugin/issues/4 "Correct MD path with unicode characters doesn't render correct HTML path · Issue #4 · Lisandra-dev/mkdocs-ezlinked-plugin")

Tốt nhất là nên đổi wikilink sang mdlink ngay từ trong plugin của Obsidian rồi xoá ezlinks trong `mkdocs.yml`. Hoặc nếu không có thể không dùng Mkdocs Publisher plugin luôn mà dùng [mkdocs-obsidian-bridge](https://github.com/GooRoo/mkdocs-obsidian-bridge "GooRoo/mkdocs-obsidian-bridge: An MkDocs plugin that helps exporting your Obsidian vault as an MkDocs site.").