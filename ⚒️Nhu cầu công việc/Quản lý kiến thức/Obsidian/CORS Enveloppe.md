---
share: true
created: 2023-10-30T14:29
updated: 2026-04-21T20:16
---
Khái niệm:: 
This is a CORS error and you don't need to worry about it. The error occurs because Obsidian's web view (app://obsidian.md) is trying to fetch resources from external domains that don't include the `Access-Control-Allow-Origin` header in their responses.

For the GitHub API request, this is expected behavior - GitHub's API has strict CORS policies. For the YouTube link, the error is harmless since it's just a URL being parsed, not an actual API call.

If you want to suppress these errors in your plugin, you can use a proxy server or handle the requests differently. For most use cases, these errors can be safely ignored as they don't affect the plugin's functionality.
Nguồn:: [Access to fetch at '\[URL\]' from origin 'app://obsidian.md' has been blocked by CORS policy · Enveloppe · Discussion #403 · GitHub](https://github.com/orgs/Enveloppe/discussions/403#discussioncomment-16617812)