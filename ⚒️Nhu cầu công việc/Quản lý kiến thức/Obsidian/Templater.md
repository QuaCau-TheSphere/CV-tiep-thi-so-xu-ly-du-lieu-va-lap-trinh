---
share: true
created: 2023-10-30T14:29
updated: 2026-08-06T15:36
---
# 
<%* const backlinks = tp.user.getBacklinks(tp) 
const meta = app.metadataCache.getCache(backlinks[0]) 
const value = meta.frontmatter.key 
const template = await tp.file.include("[[" + value + "]]") 
tR += template %>

# 
<%* let dv = app.plugins.plugins.dataview.api
const vande = tp.file.title[0].toLocaleLowerCase()+ tp.file.title.substring(1,);
const lydo= dv.page(tp.file.path(true))["Lý do"];
lydo.forEach(element => 
	tR += "**Cách để không có vấn đề dù "+element+" không biến mất:**\n\n" 
);
%>
