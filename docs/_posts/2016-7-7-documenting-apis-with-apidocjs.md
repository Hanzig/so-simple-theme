---
layout: post
title: Documenting APIs with apiDoc
---

When implementing a RESTful API, it is crucial to document it in details **during development**. Trying to use an un-documented API is like operating a complex device without a manual. Nowadays, there are several online platforms and softwares to assist developers with API documentation. Those work fine, indeed, but just did not suit my needs.

You see, when several developers are implementing the same API, it becomes quite tedious to make sure that the documentation is being kept up to date. Switching from the editor to the tool to document new API calls takes time, especially when it's a thick API with several hands into it.

Luckily, someone (Peter Rottmann) came up with a brilliant idea, and created apiDoc, which is a tool that creates documentation from API annotations in the source code. It works well with Javadoc capable languages as well as other languages. If you're familiar with Node.js and Grunt, you can get this up and running in no time, and same a lot of time when documenting your API.

This post is not a tutorial, but a simple example with instructions can be found on <a href="https://github.com/Hanzig/apidocjs_sandbox" target="_blank">https://github.com/Hanzig/apidocjs_sandbox</a> to get started.

More information about this nice tool can of course be found on <a href="http://apidocjs.com/" target="_blank">http://apidocjs.com</a>.
