---
layout: post
title: "Aseprite Isometric Tool"
categories: tools
permalink: "/tools/aseprite-isometric-tool"
date: 2024-05-04
---

## About

Creating isometric sprite sheets that needs to be split into sprites becomes difficult as the number of sprites increases. It doesn't help the artist if the shapes are irregularly shaped i.e. not square. Correct placement in the sheets is even more difficult especially when these objects can be stacked and split from one another for [sorting purposes]({% link _posts/2024-05-30-isometric-sprite-editor.md %}). This has been our experience when creating our isometric game.

What tool can assist the workflow of pixel artists in creating isometric sprite sheets?

## Solution

Luckily, Aseprite is such a great tool for pixel artist that it even has scripting capabilities. While this was the few occassions that I had to use Lua, the [scripting API](https://www.aseprite.org/docs/scripting/) was extensive and easy to understand. This tool however only works with Aseprite 1.3.3 and above because of newly exposed APIs.

### Features

- Isometric Grid Generation
- Object Outline Generation
- Isometric Layer Movement
- Layer Preview

[![Aseprite Isometric Tool](/assets/aseprite-isometric-tool/screen1.gif)](/assets/aseprite-isometric-tool/screen1.gif)

## Closing Thoughts

This tool was able to easily cutdown the manual pixel counting needed by the artist in the game. Generating the outlines also shows a preview how the object could be divided in Unity thus showing if there are any unforseen overlaps in the sprites.
