---
share: true
created: 2023-10-30T14:29
updated: 2025-03-05T11:33
---
The behavior of some of the readers and writers can be adjusted by enabling or disabling various extensions.

An extension can be enabled by adding `+EXTENSION` to the format name and disabled by adding `-EXTENSION`. For example, [`--from markdown_strict+footnotes`](https://pandoc.org/MANUAL.html#option--from) is strict Markdown with footnotes enabled, while [`--from markdown-footnotes-pipe_tables`](https://pandoc.org/MANUAL.html#option--from) is pandoc’s Markdown without footnotes or pipe tables.

The Markdown reader and writer make by far the most use of extensions. Extensions only used by them are therefore covered in the section [Pandoc’s Markdown](https://pandoc.org/MANUAL.html#pandocs-markdown) below (see [Markdown variants](https://pandoc.org/MANUAL.html#markdown-variants) for `commonmark` and `gfm`). In the following, extensions that also work for other formats are covered.

Note that Markdown extensions added to the `ipynb` format affect Markdown cells in Jupyter notebooks (as do command-line options like [`--markdown-headings`](https://pandoc.org/MANUAL.html#option--markdown-headings)).

Nguồn:: [Pandoc - Pandoc User’s Guide](https://pandoc.org/MANUAL.html#extensions)