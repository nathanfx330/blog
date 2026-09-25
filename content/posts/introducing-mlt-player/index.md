---
title: "Introducing MLT Player"
date: 2026-09-25T13:00:00-04:00
draft: false
---

There is a category of media software that almost disappeared.

A normal media player is designed to play a file. An NLE is designed to turn that file into part of a larger editing project. But there used to be something in between: software where the media file itself was the workspace.

QuickTime 7 Pro was probably the clearest example. You could open a video, inspect it frame by frame, make a precise selection, trim it, export a frame or a new file, and close the application. You did not have to build an editing project around the source before you could do useful work with it.

I have missed that kind of software for years.

**MLT Player is my attempt to build it again for Linux.**

The ideas behind an NLE are good. Layering is useful. Project-level organization is useful. Bins are useful. Precise trimming is useful. Being able to combine two pieces of media is useful.

The problem is that those ideas tend to arrive bundled with the entire NLE.

Once you step down to a normal player, nearly all of them disappear.

That is the space I wanted MLT Player to occupy.

Not a timeline with tracks.

**Layered video without tracks.**

Open a video. Look at it closely. Trim it. Put another video or an image over it if you need to. Move it, resize it, export it, and move on.

The application had to remain lightweight enough that opening it did not feel like beginning an editing session.

## The middle disappeared

Media software has become strangely polarized.

On one side are players designed primarily around consumption. Their job is to decode the file reliably, give you transport controls, maybe expose some metadata, and otherwise stay out of the way.

On the other side are editors designed around construction. They assume that the reason you opened the media is because you intend to assemble something larger.

Both approaches make sense. But there is a huge amount of work between those two activities.

Sometimes I am not watching a video for entertainment, and I am not editing a film. I am inspecting something.

I want to find a particular section. I want to know exactly which frame something happened on. I want to cut off the beginning and end. I want to place an image over the video. I want to compare a few moments. I want to mark important points and come back to them later.

None of that should require turning the source into an editing project.

At the same time, a normal player does not give me enough.

That missing middle is what MLT Player is built around.

## Why not Shotcut or LosslessCut?

There are already good tools on either side of the space I am describing.

Shotcut is also built on MLT, and it is a full nonlinear editor. That actually helps clarify what I am trying to do. Shotcut uses MLT to build the timeline-oriented editing environment. MLT Player uses the same underlying media framework for much of the work I want to do before a timeline is necessary.

LosslessCut approaches the problem from another direction. Its great strength is making cuts without unnecessarily re-encoding the media. MLT Player is doing something different: trimming inside the application is non-destructive, while video export renders through MLT into the chosen output format rather than acting as a stream-copy cutter.

MLT Player overlaps with both tools in places, but its center of gravity is different.

I wanted the media itself to remain the workspace.

Find it. Understand it. Mark it. Make the small change. Move on.

The goal is not to replace an NLE or a specialist cutting tool.

It is to make the territory between them useful.

## A file explorer finds files. It does not organize work.

The filesystem is important to me.

I do not want a media application to take a perfectly ordinary file on disk, “import” it, and then act as though the application owns the relationship between me and that file.

The file already has a home.

MLT Player starts there.

Explorer can open an ordinary directory and show the media that is already inside it. The source files remain on the filesystem. There is no mandatory ingest process and no proprietary media store sitting between the application and the source.

That works well until the collection becomes large.

A filesystem is excellent at answering one question:

**Where is this file?**

It is much worse at answering:

**Why do I care about this file?**

Those are not the same problem.

A video might physically live in one folder while being relevant to several different things I am working on. It might belong with a set of interviews, a particular subject, a group of clips I want to review later, and another collection I am preparing for somebody else.

I do not want four copies of the file just because it has four meanings.

This is one of the things larger editing systems get right. Project-level organization is better than pretending directory structure alone can represent the work.

There are also excellent dedicated cataloging applications. I have used software in that general category and often found the organizational machinery cumbersome enough that I began spending too much time managing the system that was supposed to help me manage the media.

MLT Player had to stay lighter than that.

So the media stays on disk exactly where it is, while Projects provide another organizational layer above it.

A Project can contain Catalogs. Catalogs can contain other Catalogs. One media file can belong to several Catalogs without being moved or duplicated.

The filesystem answers where the file is.

The Project answers what I am doing with it.

That distinction became one of the central ideas of the application.

## Organization should not make the browser heavier

I wanted the organization to remain visible and direct.

If a Catalog contains nested Catalogs, I should be able to click the parent and see those child Catalogs in front of me. Not a database tree that only exists in a sidebar, and not an empty screen telling me that the parent contains nothing because it happens to contain no media directly.

The structure itself is something.

A parent Catalog can show its immediate child Catalogs as simple tiles in the same space where media appears. Click one and move deeper.

It is deliberately uncomplicated.

The goal is not to invent a new theory of media asset management. It is to borrow the parts that are actually useful from larger systems without inheriting their weight.

Ratings, tags, color labels, favorites and bookmarks work the same way. They add ways of finding the media without changing where the media lives.

## A video should not look like one thumbnail

There is another problem that becomes obvious once you start browsing video seriously.

A video is one file.

Visually, it is hundreds or thousands of different moments.

Most file browsers represent all of that time with one thumbnail.

That is an extraordinarily poor compression of what a video actually contains.

A forty-minute recording may contain people entering and leaving, several locations, changing slides, different camera angles, long pauses, screen recordings, graphics, and brief moments that matter more than everything around them.

And the file browser says: here is one rectangle.

To understand the rest, you have to open the video and let time pass.

I wanted a different way to look at it.

MLT Player has a Storyboard view that turns the video into an array of frames sampled across the timeline.

Instead of time moving past you in one dimension, time becomes something you can scan in two dimensions.

A person appears and disappears. A presentation begins. The camera changes. A screen goes dark. A particular room returns later.

A visual pattern that would have taken minutes of scrubbing to discover can become obvious almost immediately.

The computer already had every one of those frames. The important change is exposing them in a form the eye can compare at once.

For me, that is one of the most useful things MLT Player does.

It helps me **look at a video**, rather than only play it.

## Find the phrase. Find the moment.

The same principle applies when the important thing is not visual.

A lot of the media I work with has transcripts. If I remember a phrase from a thirty-minute interview, I should not have to scrub around hoping I recognize the place where it was said.

MLT Player can load an SRT transcript alongside the media and make it searchable.

Search for the phrase, click the result, and go to that moment.

This sounds obvious once it exists, but the difference between searching text and searching time is enormous.

Video normally makes you search sequentially.

A transcript gives time an index.

## The inverse of Redleaf

MLT Player also grew out of another project of mine, [Redleaf](https://github.com/nathanfx330/redleaf), a system I have been building for organizing and navigating documents, transcripts, entities and relationships. But the relationship between the two applications is intentionally backwards.

Redleaf begins with meaning.

You may start with a person, an organization, a phrase, or a relationship. From there you move into a document, then into a transcript passage, then down to the timestamp where that passage occurred.

Its natural direction is:

```text
meaning
  -> document
  -> transcript
  -> timestamp
  -> media
```

MLT Player begins at the opposite end.

You start with the media itself. You scan the video visually, move through time, find an exact frame, inspect a bookmark, or search the attached transcript.

Its direction is:

```text
media
  -> time
  -> frame
  -> transcript
  -> meaning
```

The two applications meet at the timestamp.

That is why I do not want to merge them into one enormous system.

Redleaf is good at indexing and relating information.

MLT Player is good at working with media.

One lets me descend from an idea into the exact moment where it appears. The other lets me begin with the moment and climb back toward what it means.

That inverse relationship is much more important than “Redleaf integration” as a feature bullet.

The point is not that one application can launch the other.

The point is that they approach the same material from opposite directions.

Redleaf moves through meaning.

MLT Player moves through media.

**They meet where meaning becomes time.**

## Bookmarks are soft screenshots

Finding an important moment is only half the problem.

Once I find it, I often need some way to keep it.

A bookmark in MLT Player stores an exact source-frame position. It can show a visual preview, but the important part is that the preview still points back to the media.

I think of bookmarks as **soft screenshots**.

A screenshot is detached from the source. It becomes another file.

A bookmark says: this exact moment matters, and I still know where it came from.

Click it and return to the frame.

This becomes especially useful when reviewing long material. Maybe I have a one-hour recording and I find eight moments that matter. I bookmark them as I go.

Later I can see those moments together instead of scrubbing through the entire recording again.

And sometimes that collection of moments is itself the useful output.

MLT Player can export all of the bookmarked frames as images in one operation.

That means I can review a video, mark the important points, export the bookmark thumbnails, and email them to somebody as a visual summary.

Instead of saying, “Watch this hour-long recording and pay attention to 12:43, 18:02, 26:17…”

I can send the images.

These are the moments.

If you need the context, the bookmark still knows exactly where the moment came from.

That is a much more useful relationship between video and still images than simply taking screenshots while the player happens to be running.

## Trim the video and move on

The editing side follows the same philosophy.

I did not want to create a timeline.

I wanted the operations that are useful before a timeline becomes necessary.

Set an In point. Set an Out point. Play the selection. Trim it. Undo it. Redo it. Export it.

That should feel closer to handling the media directly than building an edit.

The same is true of layering.

There are plenty of situations where I want to put another image or video over the source.

That does not mean I need tracks.

It means I need a layer.

So MLT Player has a small layered composition system. A layer can have its own timing, source range, position, scale, opacity and audio gain.

You can place another video or image over the main video, move it where it belongs, and continue working.

There is no track hierarchy because there is no reason to introduce one until the work actually becomes a timeline.

That is the point of **layered video without tracks**: borrow the useful idea without importing the whole editing model.

## Lightweight does not mean imprecise

The application is supposed to feel lightweight. That does not mean the media handling can be casual.

Playback, decoding and export are built on MLT, while Flutter handles the application interface and organization around it.

The division is intentional.

**Flutter owns the application. MLT owns the media.**

Underneath a simple player interface, however, there can be several different notions of where playback currently is: the transport position, the producer position, the latest frame decoded, the frame currently being presented to the display, and the source frame an export should resolve.

Those distinctions matter because they do not automatically agree.

I learned this the hard way while chasing a playback bug where nearly every diagnostic said the correct frame was loaded, yet the image on screen was visibly wrong. The transport could be at frame 2451, the decoder could report frame 2451, and the image buffer could belong to frame 2451, while another presentation layer was still causing the user to see something else.

That is the complexity hidden underneath a very simple user expectation:

**Show me this frame.**

Preview, presentation, bookmarks, trimming and export all have to agree on what that means.

If I step one frame, I want one frame. If I bookmark a moment, I want the exact source frame. If I export that bookmark later, I want the same frame. And if a layered composition looks one way in preview, I do not want export to quietly interpret it differently.

The user should never have to think about transport positions, decoded frames or presentation state.

“This frame” should have one obvious meaning.

## Export without entering another world

Export is another area where I wanted the application to remain direct.

You should not have to send the media into a separate rendering world just because you made one small change.

MLT Player can export ordinary delivery video, higher-quality master output, audio, still frames and image sequences. Bookmarks can be exported individually or in bulk.

The live preview and export pipeline are deliberately separate internally, because playback and deterministic rendering have different needs. But they derive their decisions from the same composition rules.

The reason is simple: I want to be able to trust what I am looking at.

If the application shows a layer in one position and the export moves it somewhere else, the whole system becomes questionable.

A lightweight tool still has to be predictable.

## The small things matter

Some of my favorite additions to MLT Player are not major features.

Right-click a media thumbnail and reveal the actual source file in the desktop file manager.

Create a nested Catalog and it appears as a tile when you open its parent.

Export every bookmarked frame instead of repeating the same action twenty times.

These are not features you build an entire marketing page around. But they determine whether software feels like something you can actually live in.

Desktop applications are full of tiny transitions between tasks.

The better those transitions are, the less you notice the application itself.

That is what I want.

## The software between the player and the editor

MLT Player is still evolving, but its purpose is much clearer now than when I started it.

I do not want another player that treats video as a rectangle with transport controls underneath it.

I do not want another media catalog that requires me to surrender the filesystem to use it properly.

And I do not want to open a full NLE every time I need to understand, trim, mark, layer or export something from a video.

The ideas inside an NLE are useful.

The mistake would be assuming the NLE is the only place those ideas are allowed to exist.

Project organization is useful without a timeline.

Layers are useful without tracks.

Frame-exact trimming is useful without an edit sequence.

Bookmarks are useful without creating screenshots.

The middle can exist.

That is the software I wanted.

Open the media. See what is there. Find the part that matters. Keep the moments you care about. Make the small change. Export it. Move on.

**That is MLT Player.**

## One more thing

None of this means I have anything against nonlinear editors.

I may eventually make one myself.

I already have the name:

**Spiffy Cuts.**

Joking aside, one of the more interesting things to come out of MLT Player, and out of the work I have been doing on **R3nder, my terminal-style presentation and rendering tool**, is that I am slowly laying down a more understandable path for building custom applications on top of MLT.

MLT is extraordinarily capable, but there is a large gap between proving that something works with `melt` or an MLT graph and turning it into a desktop application with predictable preview, frame timing, thumbnails, compositing, export and a usable interface.

MLT Player approaches that problem from the direction of a lightweight media workspace. R3nder approaches it from a very different presentation and rendering workflow. The applications are different, but a lot of the hard-won knowledge underneath them is transferable.

How do you keep preview and export in agreement?

How do you reason about source frames instead of vague playback positions?

How do you expose MLT through a modern application UI without turning the interface into a thin wrapper around an engine?

How do you make compositing useful without forcing every application into the same timeline metaphor?

Those are useful problems beyond either project.

My hope is that this work eventually makes it easier for other people to build their own MLT experiences rather than assuming there has to be one prescribed interface for the engine.

And if that eventually results in **Spiffy Cuts**, I suppose I will have only myself to blame.

## Try it

MLT Player is open source and actively being developed for Linux.

It is built with Flutter and MLT and released under the MIT license. The current validated baseline is MLT 7.22.x, with development also being exercised against newer MLT builds on my own Linux systems.

This is still evolving software rather than a finished commercial release, but it has reached the point where I am using it for real work, which is why I finally wanted to write this introduction.

MLT Player is a separate project from MLT's own `melt` command-line utility. It uses MLT as its media engine but provides its own Flutter application, project organization, Explorer, Player and workflow.

Build requirements and current Linux setup instructions are maintained in the repository README.

Repository:

**https://github.com/nathanfx330/MLT-Player**
