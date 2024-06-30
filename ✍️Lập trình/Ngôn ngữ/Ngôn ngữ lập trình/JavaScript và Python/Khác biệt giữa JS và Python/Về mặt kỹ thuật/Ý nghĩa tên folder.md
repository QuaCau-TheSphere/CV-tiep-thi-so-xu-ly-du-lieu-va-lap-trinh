---
share: true
created: 2023-10-30T14:29
updated: 2024-05-17T22:09
---
Folder structure varies by build system and programming language. Here are some standard conventions:
- `src/`: "source" files to build and develop the project. This is where the original source files are located, before being compiled into fewer files to `dist/`, `public/` or `build/`.
- `dist/`: "distribution", the compiled code/library, also named `public/` or `build/`. The files meant for production or public use are usually located here.  
   There may be a slight difference between these three:
	- `build/`: is a compiled version of your `src/` but not a production-ready.
	- `dist/`: is a production-ready compiled version of your code.
	- `public/`: usually used as the files runs on the browser. which it may be the server-side JS and also include some HTML and CSS.
- `assets/`: static content like images, video, audio, fonts etc.
- `lib/`: external dependencies (when included directly).
- `test/`: the project's tests scripts, mocks, etc.    
- `node_modules/`: includes libraries and dependencies for JS packages, used by Npm.
- `vendor/`: includes libraries and dependencies for PHP packages, used by Composer.
- `bin/`: files that get added to your PATH when installed.
Nguồn:: [What is the meaning of the /dist directory in open source projects?](https://stackoverflow.com/a/22844164/3416774)