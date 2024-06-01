---
layout: post
title: "Sprite Animation Generator"
categories: tools
permalink: "/tools/sprite-animation-generator"
date: 2024-05-01
---

## About

When I first started to use Unity, I wanted to create a 2D isometric game. However, when creating animations from spritesheets, I found the workflow to be cumbersome. The steps are as follows:

1. Select the sprites for an animation
2. Create an animation clip from the selected sprites
3. Rename the animation clip
4. Move it into the appropriate folder

[![Animation Generator 1](/assets/sprite-animation-generator/screen1.png)](/assets/sprite-animation-generator/screen1.png)

While there are only 4 steps, each sprite sheet animation had 5 facing directions as a result of the isometric view which has diagonal directional movements. To add to this, each player entity had multiple body parts i.e. hands, legs, body, head, hair etc. Unity also slows down when the project becomes large especially when there are too many assets.

It took me about close to 3 hours to finish one spritesheet with about 10 animations with 5 directions and multiple body parts... which was unacceptable. Imagine the hours spent creating animations from spritesheets manually.

## Solution

What I initially conceived was a tool that would display the split sprite sheet in a window and allow the user to select the sprites for the animation clip. It should also give the user the capability to name the assets quickly and sort them into the appropriate folder. This should in theory, speed the workflow for the user from hours to maybe a minute or two.

[![Animation Generator 2](/assets/sprite-animation-generator/screen2.png)](/assets/sprite-animation-generator/screen2.png)

### Features

- Zooming and panning in the window and selection using the mouse (with dragging)
- Multi-selection of sprites (based on how it is split in the built-in sprite editor)
- Generate multiple animations clips
- Generate clips and groups them by entity/body parts
- Automatically names the assets based on the label and delimeter (based on the default or custom settings)
- Automatically generates folders and subfolders
- Automatically groups different directions into one scriptable object

\* Note the 20 second generation is caused by the video recording, normally it is less than 5 seconds

{% youtube W2uRyfoWNWE %}

## Closing Thoughts

As this was my venture into creating a custom tool in Unity, it took some time to create this tool (2 weeks total) and it wasn't the best but I was happy when I finished it. I should've thought of adding a preview of the animation that will be generated from the sprites but it slipped my mind. I found this is a good starting exercise when creating custom tools for unity as it wasn't too complex but it wasn't also too easy.

I also would recommend for those who can't create their own tools to look into these asset store assets for 2d animation.

- [Power Sprite Animator](https://assetstore.unity.com/packages/tools/sprite-management/powersprite-animator-71177) : A great tool that shows animation clips and enables users to manipulate them

- [Animation Blocks](https://assetstore.unity.com/packages/tools/animation/animation-blocks-233102) : A tool that solve similar problems to my tool but uses the UI Toolkit (may not be compatible with lower versions of Unity)
