---
layout: post
title: "Sequence Editor"
categories: tools
permalink: "/tools/sequence-editor"
date: 2024-05-05
---

## About

When prototyping our isometric game in Unity, we initially used some asset store tools to develop quickly. However when doing this, you need to stick to the workflow of these assets. One such asset that we used was the [Dialogue System for Unity](https://assetstore.unity.com/packages/tools/behavior-ai/dialogue-system-for-unity-11672).

[![Sequence Editor 2](/assets/sequence-editor/screen3.png){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/sequence-editor/screen3.png)

It's a great asset and used by incredible games such as Disco Elysium and other hit games. I'm not saying this asset is bad, but you need to adopt your workflow and work with any limitations the asset might have. One such workflow is the cutscene system which they call as their Sequences and the Sequencer Commands. You need to use Lua in the inspector without any type checking which is error prone and cumbersome to remember.

[![Sequence Editor 1](/assets/sequence-editor/screen1.PNG){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/sequence-editor/screen1.PNG)

Additionally to view the cutscene, the game needs to played everytime which takes time to start. What I'm looking for is a cutscene system that works in the Editor as well as in Play mode and is easy to edit and modify.

## Credit

When we were search for a nicer way to create our cutscenes or even the just NPC dialogues, we stumbled on the talk of CrossCode developer Felix Klein. He talked about presenting sequences of commands like the same way as the Event Editor in RPG Maker as they used RPG Maker extensively before. In this way, errors can be isolated to individual sequences and these sequences can be turned off/on and reordered on command.

[![Sequence Editor 3](/assets/sequence-editor/screen4.PNG){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/sequence-editor/screen4.PNG)

So the idea of combining the Step/Event Editor to the Sequence and Sequencer Commands was born.

## Sequence Editor

[![Sequence Editor 5](/assets/sequence-editor/screen6.png){:style="display:block; height:400px; margin-left:auto; margin-right:auto"}](/assets/sequence-editor/screen6.png)

A sequence can be added through the sequence searcher. This then adds the sequence to the sequence data scriptable object which is displayed in the editor. Custom sequences can be made by inheriting from the abstract class of Sequence which will be automatically picked up in the sequence searcher.

[![Sequence Editor 4](/assets/sequence-editor/screen7.gif){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/sequence-editor/screen7.gif)

Sequences can also implement their own custom editor which can manipulate the data of the particular sequence. This enables sequences to be easily modified by non-programmers. Similar to the Sequences in the Dialogue System, sequences can block the processing of sequences and wait for messages that other sequences can emit. Additionally, the sequence manager can speed up or slow down the speed/time, can store variables which can be used for programming and can be run in the editor without going into playmode.

Lastly, the sequence editor is great at modifying sequences as it is able to reorder, disable and edit the data in sequences. Additionally, within the editor you can safely create new sequences and sequence data SO through it. Dialogue is also parsed which can be great for looking at branching dialogue and eventually localization support can be added. Lastly, the sequence editor can help debug the sequences by slowing down the playing of sequences, showing what is active and currently running.

[![Sequence Editor 6](/assets/sequence-editor/screen8.gif){:style="display:block; margin-left:auto; margin-right:auto"}](/assets/sequence-editor/screen8.gif)[^1]

## Closing Thoughts

Creating cutscenes became much easier and the workflow became much more robust. Iteration also became quicker and it was easier to integrate other assets like the [Bone Animation System]({% link _posts/2024-05-30-bone-sprite-animation-system.md %}) and the [Text Animator for Unity](https://assetstore.unity.com/packages/tools/gui/text-animator-for-unity-254677). For future improvements, this system can be probably modified for driving other systems such as the AI of the game as well and the custom inspectors could be made automatically.

[^1]: Credits to Radical Fish Games for the placeholder sprite in the dialogue box
