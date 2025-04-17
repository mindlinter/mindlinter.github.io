---
layout: ../../layouts/post.astro
title: "So, I tried the MCP server with another AI agent!"
pubDate: 2025-04-17
description: "My second try of the MCP server was successful. I tried Gemini Pro 2.5."
author: ""
isPinned: true
excerpt: "I tried Gemini Pro 2.5 with the MCP server. And it worked!"
image:
  src:
  alt:
tags: ["ai", "mcp", "cursor", "vs code", "copilot", "gpt-4o", "claude", "mcp server", "graphql"]
---

My first try of the Model Context Protocol (MCP) server for AI was not successful. But I didn’t give up. I decided to continue. And all symptoms gave me a hint that the context window is not enough for my case. The MCP server tooling is not great. Neither VS Code nor Cursor told me directly: the context window is not enough. They both did an infinite cycle. I decided to calculate the amount of tokens in my GraphQL scheme. It has 540k tokens. The ChatGPT context window is only 128k. And Claude has about a 200k context window. And it became obvious that it was just impossible to achieve what I wanted with these AIs. I needed to use another agent with a bigger context window. And I tried Gemini Pro 2.5. It should have a 2kk context window. More than enough for me at this point.

And I was surprised. There was even a “wow” moment. The agent did what it should do. Now, I am confident that with MCP servers a lot of chore work could be automized. What I will try to do. Let AI agents work and programmers rest! Will we regret it?