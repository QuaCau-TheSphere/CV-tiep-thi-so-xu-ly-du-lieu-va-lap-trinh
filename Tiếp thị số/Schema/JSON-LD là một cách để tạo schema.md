---
share: true
created: 2023-10-30T14:29
updated: 2024-04-23T01:41
---
![What is Linked Data? - YouTube](https://youtu.be/4x_xzT5eF5Q?si=pKxW5p19YSQkBrxS)
![What is JSON-LD? - YouTube](https://youtu.be/vioCbTo3C-4?si=IIS-mzulM5qAWj3O)
![JSON-LD: Compaction and Expansion - YouTube](https://youtu.be/Tm3fD89dqRE?si=p01fOi2aYxAH6x_J)

### Differences between JSON-LD, Microdata, and RDFa

(in the context of HTML documents)

**Microdata** and **RDFa** are conceptually similar: both syntaxes define attributes that get added to your existing HTML elements.

**JSON-LD** is a syntax that gets added to a `script` element ([used as data block](https://stackoverflow.com/a/30798784/1591669), not as script), separately from your existing markup.

So the primary difference between Microdata/RDFa and JSON-LD is that you have to repeat the content if using JSON-LD, while you can² mark up your existing content if using Microdata/RDFa.

These three snippets convey the same structured data (a [`Person`](http://schema.org/Person) with a [`name`](http://schema.org/name) of "Alice"):

```xml
<!-- Microdata -->

<p itemscope itemtype="http://schema.org/Person">
  Hi, I’m <span itemprop="name">Alice</span>.
</p>
```

```xml
<!-- RDFa -->

<p vocab="http://schema.org/" typeof="Person">
  Hi, I’m <span property="name">Alice</span>.
</p>
```

```xml
<!-- JSON-LD -->

<p>
  Hi, I’m Alice.
</p>

<script type="application/ld+json">
  {
   "@context": "http://schema.org",
   "@type": "Person",
   "name": "Alice"
  }
</script>
```

### Which to use?

**JSON-LD** if you want to add a blob of structured data, without having to care about existing markup. Might be easier for tools that don’t support structured data (and you use other tools to generate/add it), or when copy-pasting ready-made snippets.

**Microdata/RDFa** if you want to make use of your existing markup (so you don’t have to duplicate the content → [DRY](https://en.wikipedia.org/wiki/Don't_repeat_yourself "Don't repeat yourself")). Might be easier if adding it by hand, or when tools already support it (like Drupal).

If deciding between Microdata and RDFa: I [recommend](https://stackoverflow.com/a/14501684/1591669) to use RDFa instead of Microdata, primarily because of the [differences outlined in this answer on Stack Overflow](https://stackoverflow.com/a/25888436/1591669).

RDFa and JSON-LD are both W3C Recommendations and both are RDF serializations.


Do I understand right, JSON-LD can only let you specify general info about whole page, but you can't express which exactly parts of the webpage correspond to which object in JSON-LD? Like, if you have a list of books, you can specify in JSON-LD that this page shows a list of books, but you won't be able to tell which of the books described in the JSON-LD correspond to which exactly element on the webpage? If so, Microdata/RDFa have one more important advantage: providing context to screenreaders used by blind people, but maybe I'm missing something in how JSON+LD works.

Nguồn:: [[✍️Lập trình/Ξ Nguồn và tài nguyên hỗ trợ/Ξ Nguồn/Stack Overflow]], [How does Microdata rdfa compare to JSON-LD? - Software Engineering Stack Exchange](https://softwareengineering.stackexchange.com/questions/328567/how-does-microdata-rdfa-compare-to-json-ld#comment981918_328711)

[[Open Graph chuyên cho việc chia sẻ trên mạng xã hội. Schema chuyên cho việc tìm kiếm trên Google]]

[Schema là gì? Cách thêm Schema Markup tăng sức mạnh website](https://vietnix.vn/schema-la-gi/)