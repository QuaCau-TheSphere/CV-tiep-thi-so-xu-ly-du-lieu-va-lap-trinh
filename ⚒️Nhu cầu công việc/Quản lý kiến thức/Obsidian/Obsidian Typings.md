---
share: true
created: 2023-10-30T14:29
updated: 2025-10-12T13:17
---
Maybe I'm not using the right terms, but I indeed mean "official" as "external and documented". This is the functions and classes that the Obsidian's team decided to make stable so plugin developers can use them without the fear of breaking changes every update.  
On the opposite, "internal" API is the functions and classes a developer chooses to use without knowing if the code will change. To get the internal API, you have to investigate the code by yourself, with a lot of code breaks (stopping the execution of the code to inspect what's going on), reading the minified code app.js, and console logs. The package obsidian-typings is basically a collection of the knowledge that was aquired like that. So it only contains types, yes. But because we need typings from PixiJS to be able to define types of classes using PixiJS (such as the [GraphNode](https://github.com/Fevol/obsidian-typings/blob/release/obsidian-catalyst/1.9.9/src/obsidian/internals/InternalPlugins/Graph/GraphNode.d.ts)), PixiJS is a dependance of obsidian-typings, and therefore imported when you import obsidian-typings.  
So most of the types are internal in obsidian-typings, but not all of them. Some of them redefine existing official types in order to provide a better documentation that is lacking from the official website.

As for the package.json, you need to switch to another branch. It is quite recent, but now the people handling this repo decided to do a branch per Obsidian's version. So every code has been removed from main.

- I mean, isn't that the team doesn't want to release it open source? So it's logical to prevent reverse engineering as much as possible? 

Also, what does the main branch of the type lib serve now?

I can't speak for the team. But as I understood it, it's not because it's undocumented that they don't want people to use it. Each time they document a function or a class and make it official, they lock the code a little bit more because they now took the responsibility to keep this function/class as it is. Or at least, same name, same inputs, same return. So if they were to document everything, they would not be able to modify the code as easily as they want. They found a middle ground between what they documented for the community developers, and what they kept internal so they still have the possibility to change a lot of stuff. If you use the internal API, they are not really against it, as long as you make it clear that it might break. And they highly encourage to use the external API instead when possible. The core graph plugin, as well as other core plugins, is kept internal. But for the core graph, it is also because the code requires a lot of optimization so it is not meant to be used by something else.

As for the obsidian-typings repo new design, I don't know. You can probably ask on their GitHub or on discord if you're curious:)

Nguồn:: [Reddit - The heart of the internet](https://www.reddit.com/r/ObsidianMD/comments/1jlgery/comment/navuv1z/?context=1)

