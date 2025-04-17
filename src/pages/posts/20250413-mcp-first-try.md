---
layout: ../../layouts/post.astro
title: "So, I tried MCP"
pubDate: 2025-04-13
description: "Are MCP the breakthrough for AI coding? Or just another hype? My first impressions."
author: ""
isPinned: true
excerpt: "I tried MCP for myself as well. And I am disappointed. At least for now"
image:
  src:
  alt:
tags: ["ai", "mcp", "cursor", "vs code", "copilot", "gpt-4o", "claude", "mcp server", "graphql"]
---

There is a lot of hype about MCP(Model Context Protocol). I tried it for myself as well. And here are my first impressions.

There is nothing special in my idea. My MCP should be a united point for all available API for one CMS. I decided to start my MCP server by being able to run GrahpQL queries. I didn’t use existing GraphQL MCP servers, because I planned more functionality in the future. Much more. And I decided to start with the obvious part, GraphQL, where the MCP server is a wrapper for API, nothing more. 

And currently, I am disappointed.

Neither VS Code + Copilot nor Cursor can’t use the MCP server GraphQL tool efficiently. I tried GPT-4o-mini, GPT-4o, Claude 3.5 Sonnet, Claude 3.7 Sonnet. The results are about the same. AI agents make a loop by making requests to the tool on my MCP server. Yes, they can successfully get the required data. But for some reason, they don’t know what to do with it afterward. And the best that they can think of, they are trying to get this data again. Not useful, and frustrating for now.

I will try to continue finding the solution. But that is not a straightforward process, like everything with AI. If something doesn’t work in your code, you just figure out what is wrong and fix it. If something is wrong with neural networks, or AI, you just try, try, try blindly. Probably something will work. Or probably not, it will depend on how lucky you are and how many attempts have you made.