---
layout: ../../layouts/post.astro
title: "CLIXML, have you heard about it?"
pubDate: 2025-05-06
description: "Exploring the integration of TypeScript with PowerShell Remoting."
author: ""
isPinned: true
excerpt: "Exploring the integration of TypeScript with PowerShell Remoting."
image:
  src:
  alt:
tags: ["mcp", "powershell", "integration", "typescript"]
---

You never know which task you will work on next. 

I have two machines that communicate via [**MS-PSRP**] **PowerShell Remoting Protocol.** This protocol allows encoding messages and passing them between different machines. And everything is fine. Everything works as expected. But now I don’t want to use PowerShell on the first machine anymore. I want this machine to be some kind of MCP server and communicate with different machine via the same protocol. I actually can’t change the protocol. Because it is kind of standard. And everyone uses it.

My MCP server is TypeScript-based. The most common runtimes for MCP servers are TypeScript and Python. It makes sense to select between them if you want your server to have a happy and long life. And I choose TypeScript. I have written a lot of code. Now, I need to integrate an API that communicates via `CLIXML` messages and uses PowerShell Remoting Protocol…

It is possible to rebuild an MCP server in C#. But that is a lot of work. And C# is not the best choice for the MCP server. .Net-based MCP server will simplify parsing `CLIXML` a little. But I still need an additional parser for it. There is no chance that AI agents will understand that weird format well. And also, it is quite verbose, which will cause constant AI agent context window size problems…

Rebuilding is not an option. I need to write the implementation of the protocol by myself. It is hard to believe, but there is no NPM package for it. Finally, I was faced with the task that would require writing my own NPM package. I would like it to be more interesting rather than parsing some weird protocol. But it is what it is. You never know which task you will work on next.