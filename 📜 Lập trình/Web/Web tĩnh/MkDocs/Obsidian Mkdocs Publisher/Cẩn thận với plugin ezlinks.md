---
share: true
title: Plugin ezlinks khi gặp [[./a/index]] sẽ ra kết quả sai
created: 2023-10-19T23:29
updated: 2023-10-20T00:11
---
Ezlink là plugin mà Obsidian Publisher sử dụng.

Với `mkdocs.yml`:
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
```

| docs/index.md    | site/index.html                                    | Trỏ đúng |
| ---------------- | -------------------------------------------------- | -------- |
| [[a/index]]      | <a href="a/" title="a/index">a/index</a>           | ✔        |
| [[a/index.md]]   | <a href="a/" title="a/index.md">a/index.md</a>     | ✔        |
| [[./a/index]]    | <a href="a/index" title="./a/index">./a/index</a>  | ❌        |
| [[./a/index.md]] | <a href="a/" title="./a/index.md">./a/index.md</a> | ✔       |

Đồng thời Mkdocs sẽ báo như sau:
```
INFO    -  Doc file 'index.md' contains an
           unrecognized relative link
           'a/index', it was left as is. Did  
           you mean 'a/index.md'?
```

[Expecting `\[\[./a/index\]\]` to returns `<a href="a/"`, get `<a href="a/index"` · Issue #53 · orbikm/mkdocs-ezlinks-plugin](https://github.com/orbikm/mkdocs-ezlinks-plugin/issues/53 "Expecting `[[./a/index]]` to returns `&lt;a href=&quot;a/&quot;`, get `&lt;a href=&quot;a/index&quot;` · Issue #53 · orbikm/mkdocs-ezlinks-plugin")