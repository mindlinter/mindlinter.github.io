---
layout: ../../layouts/post.astro
title: "Linux Disk Usage"
pubDate: 2025-04-01
description: "There are tools that show detailed disk usage by folders on Linux. But, be ready that they will not show the whole true. For example, they don't count Docker files for some reason."
author: ""
isPinned: true
excerpt: There are tools that show detailed disk usage by folders on Linux. But, be ready that they will not show the whole true. For example, they don't count Docker files for some reason.
image:
  src:
  alt:
tags: ["linux", "ubuntu", "size", "ncdu"]
---

I am a Windows user. Yes, I use Linux daily. I can’t imagine development without Windows Subsystems Linux(WSL), Linux Docker containers, and Linux hosting, but I am still a Windows user.

From time to time, free space ends on solid-state drives and hard drives. There could be a million reasons for that. Logs, build artifacts, containers, images, downloads, anything. Sometimes, it is obvious to you, what took so much space. Sometimes it is not. I used [WinDirStat](https://windirstat.net/) before. But recently, I switched to the alternative [TreeSize](https://apps.microsoft.com/detail/xp9m26rsclnt88). I don’t know how, but it is much faster.

Today, I am faced with with lack of space on my Linux cloud-hosted VM. `df -h` util showed that 45 of 47 available GB are in use. I looked for TreeSize alternative for Linux. And quickly found [ncdu](https://en.wikipedia.org/wiki/Ncdu). Firstly, I was impressed. Command-line tool showing sizes of different folders. Isn’t that awesome?

But I was happy not for a long time. It didn’t help me. It showed only 14 GB that are in use. But where are another 31 GB? And, I didn’t find a way how to get proper file statistics after trying different recipes from the web.  

The lucky guess `docker system prune` removed old images and now, I have enough space. However, `df -h`, and `ncdu` still show very different results…