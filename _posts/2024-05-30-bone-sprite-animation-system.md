---
layout: post
title: "Bone Sprite Animation System"
categories: tools
permalink: "/tools/bone-sprite-animation-system"
date: 2024-05-03
---

## About

One of goal/feature that we wanted in our 2D isometric game was customizable player characters. We want to have interchangeable cosmetic items from hats, to pants, shorts, shirts, weapons, etc. While this is easier to achieve in 2D top down games or side scrollers, the problem for isometric games are the diagonal directions. This effectively increases the amount of sprites needed from 3 directions (up, down, side) to 5 directions (up, up-side, side, down-side, down). Multiply this by the number of animations you are want, the goal effectively becomes near impossible to achieve in a reasonable amount of dev time. This is due to the artist having to do all the sprites needed for the animations and directions. For top down and side scrollers, they can use rotation, scale and transform to do animations. So how are we able to do this for our isometric game?

[![Bone Sprite Animation System 1](/assets/bone-animation-system/screen1.gif){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/bone-animation-system/screen1.gif)

## Credits

While scrolling in Twitter, I came across the new game of Radical Fish Games called Project Terra. In their posts, they explained they're using a new animation system which uses billboard sprites with 3D bones. This allowed them to iterate quickly on animations as the hand drawn pixels of CrossCode limited them to only a single type of cosmetic for their character Lea. This is it! The solution to our problem was shown to us. Use 3D bones for animations while layering 2D sprites on the characters for the cosmetics. Easier said than done...

Links

1. [Radical Fish Games Blog](https://www.radicalfishgames.com/?p=7230)
2. [Lachsen Twitter](https://x.com/lachsen/status/1388218721433493505)

## Prototype

It was incredibly difficult to get any info on their system, even though they showed some of it on their livestreams. How were they able to achieve it is still a mystery but I had to try to make my own system with my limited knowledge in 3D.

First step was to know how to billboard sprites. While a lot of info was available online, the difficult part is to add perspective distortion based on the camera angle. This was needed to automatically allow some sprite to adjust their scale depending on the distance and angle towards the camera.

[![Bone Sprite Animation System 2](/assets/bone-animation-system/screen2.gif){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/bone-animation-system/screen2.gif)

Next step was to construct some placeholder sprites which I made in aseprite to be similar to the one in the [Project Terra tweet](https://x.com/lachsen/status/1388218721433493505). Assemble it into a heirarchy of bones manually then try to animate it. The billboard shader also was used but without the distortion initially for the prototype. An editor was also needed to be made to facilitate the editing of the animation.

[![Bone Sprite Animation System 3](/assets/bone-animation-system/screen3.gif){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/bone-animation-system/screen3.gif)

[![Bone Sprite Animation System 4](/assets/bone-animation-system/screen4.gif){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/bone-animation-system/screen4.gif)

[![Bone Sprite Animation System 5](/assets/bone-animation-system/screen5.gif){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/bone-animation-system/screen5.gif)

2 weeks in and with a basic editor along the way, the first initial prototype somehow worked. At first I thought, okay this isn't that difficult, probably a few weeks more then we'll be done.

Spoiler: It took about 5 months to finish the whole system...

## Iteration 2

The hardest part of this was to design sprites which worked with the system. Subdividing the body of our character and making it fit nicely on the system was harder than we imaged. Some parts of the character didn't look nice with perspective distortion but for other parts like the legs, arms, weapons etc needed to rotate and bend/scale based on the angle. These sprites needed to be reworked and readjusted in length which took a lot of iteration time.

[![Bone Sprite Animation System 8](/assets/bone-animation-system/screen8.gif){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/bone-animation-system/screen8.gif)

A lot of the visuals here was done in the shader but a lot of tweaking for the numbers was done manually until it looked really convincing.

[![Bone Sprite Animation System 6](/assets/bone-animation-system/screen6.gif){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/bone-animation-system/screen6.gif)

The system also needed to determine what direction the bone/body part was facing relative to the camera. This also needed to be fast and change the sprite of the bone currently is using. Sorting also needed to be determined based on the bone distance from the camera or by the custom sorting order set on the editor.

[![Bone Sprite Animation System 7](/assets/bone-animation-system/screen7.gif){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/bone-animation-system/screen7.gif)

Currently while the system can run in real-time but the values are currently baked in a scriptable object to save computation time. I explored using DOTS for a bit but ran into more issues than I wanted to. Reworking the whole system for DOTS which took me 5 months to make was a big no on my part.

## Other Features

The nice part of this system is that since the bone sprites can be changed anytime during the animation, the character can be made more dynamic. An example is here the character is blinking while the character is running. If you noticed in some GIFs, the hair sprite is also changing during the animation which gives an illusion of movement.

[![Bone Sprite Animation System 9](/assets/bone-animation-system/screen9.gif){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/bone-animation-system/screen9.gif)

Additionally, the goal of customizable cosmetics for characters is achievable as shown here. Weapon switching is also achieved along with additional shader effects.

[![Bone Sprite Animation System 10](/assets/bone-animation-system/screen10.gif){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/bone-animation-system/screen10.gif)

[![Bone Sprite Animation System 11](/assets/bone-animation-system/screen11.gif){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/bone-animation-system/screen11.gif)

[![Bone Sprite Animation System 12](/assets/bone-animation-system/screen12.gif){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/bone-animation-system/screen12.gif)

## Closing Thoughts

This was such a long and difficult journey, from the prototype to the current system. Currently this is the most complicated custom tool I made in Unity and I learned a lot along the way. While the system I made is not the most efficient (0.1 - 0.5ms) update per object in the editor, improvements can still be done. The next step is to have the system run in the GPU through texture skinning.

I also would like to thank [Radical Fish Games](https://x.com/radicalfishgame) for showing their animation system, without them I couldn't have thought of implementing my own system and [Erich](https://x.com/artoferich) who was patient enough to craft and modify the sprites pixel by pixel so we can iterate the system.

[![Bone Sprite Animation System 13](/assets/bone-animation-system/screen13.gif){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/bone-animation-system/screen13.gif)
