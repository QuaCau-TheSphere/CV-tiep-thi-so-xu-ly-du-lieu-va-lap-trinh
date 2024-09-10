---
share: true
created: 2023-10-30T14:29
updated: 2024-09-09T20:53
---
Every processor implements another processor. To create a processor, call another processor. The new processor is configured to work the same as its ancestor. But when the descendant processor is configured in the future it does not affect the ancestral processor.

When processors are exposed from a module (for example, `unified` itself) they should not be configured directly, as that would change their behavior for all module users. Those processors are _[frozen](https://github.com/unifiedjs/unified?tab=readme-ov-file#processorfreeze)_ and they should be called to create a new processor before they are used.

Nguồn:: [GitHub - unifiedjs/unified: ☔️ interface for parsing, inspecting, transforming, and serializing content through syntax trees](https://github.com/unifiedjs/unified?tab=readme-ov-file#processors)