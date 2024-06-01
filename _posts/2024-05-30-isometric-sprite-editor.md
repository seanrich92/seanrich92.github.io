---
layout: post
title: "Isometric Sprite Editor"
categories: tools
permalink: "/tools/isometric-sprite-editor"
date: 2024-05-02
---

## About

One of the hardest challenges I faced when doing an isometric 2D game was sorting. Making the sprites look coherent in-game when there are hundreds of irregular shaped objects became an issue due to sorting.

So a quick background on sorting. You can set a custom pivot in Unity's settings to do [isometric sorting](https://docs.unity3d.com/Manual/Tilemap-Isometric-CreateIso.html). While this works on regular shaped square sprites, this fails easily on irregular shaped sprites. What do I mean?

[![Isometric Sprite Editor 1](/assets/iso-split-editor/screen3.PNG)](/assets/iso-split-editor/screen3.PNG)

In this sprite you can easily see the red dot in the middle which represents the sorting point of the sprite. This means that anything below the red dot is drawn above it while anything behind the red dot is drawn behind. This works well as you can easily change the sorting point of the sprite in the sprite editor. However how would you sort something like this?

[![Isometric Sprite Editor 2](/assets/iso-split-editor/screen4.png)](/assets/iso-split-editor/screen4.png)[^1]

This is more difficult due to the fact that only a single point of the sprite determines the sorting point of the renderer. It would easily break the illusion of the game when you move around the scene. [This video](https://www.youtube.com/watch?app=desktop&v=yRZlVrinw9I) shows a solution that can solve this issue. They do run-time sorting on the cpu, changing the sorting order based on the location of the objects relative to a point or a line from the object.

[![Isometric Sprite Editor 4](/assets/iso-split-editor/screen6.png)](/assets/iso-split-editor/screen6.png)[^1]

While this works perfectly, it has a large run-time cost as this does the sorting every frame and doesn't scale well when there are many objects. It doesn't also play well with tilemaps since it manipulates the sorting order instead of the sorting point. The only other solution that doesn't have these drawbacks is by subdividing the sprite into multiple sprites and letting the renderer do the sorting.

[![Isometric Sprite Editor 3](/assets/iso-split-editor/screen5.png)](/assets/iso-split-editor/screen5.png)[^1]

So how do I do perfect sprite subdivision without incurring any errors and doing it quickly?

## Solution

By creating a sprite editor similar to Unity's but specifically catered to isometric sprite subdivision, I can easily automate the task after generating the bounds of the sprite. With a bit of math, I can then just use the generated split sprites then place them perfectly in the tilemaps or sprite renderers to make it seem like they are just one sprite.

[![Isometric Sprite Editor 5](/assets/iso-split-editor/screen7.PNG)](/assets/iso-split-editor/screen7.PNG)

### Features

- Zooming and panning in the window and selection using the mouse (with dragging)
- Non-destructive exporting
- Dragging, expanding and locking of sprite bounding box
- Isometric pivot placements
- Isometric collision placements
- Other metadata for the game such as irregular polygon collisions, transparency collision, shadow generation etc

\*This is an old video of the tool

{% youtube hhWQM7UtuvA %}

## Closing Thoughts

This was my second custom tool in Unity and up to now I still find ways to improve it, from adding more features that the game needs, to finding some subtle bugs and fixing it. Without this tool, the isometric sprites would've been limited to a square shaped design which would limit the design of the game.

[![Isometric Sprite Editor 6](/assets/iso-split-editor/screen2.png)](/assets/iso-split-editor/screen2.png)

[^1]: Credits to [Scott Steffes](https://www.youtube.com/watch?app=desktop&v=yRZlVrinw9I) for the screenshots in the article
