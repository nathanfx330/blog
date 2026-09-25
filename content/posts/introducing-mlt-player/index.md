---
title: "Introducing MLT Player"
date: 2026-09-25T13:00:00-04:00
draft: false
---

There is a strange gap in modern media software.

At one end, there are players. They open a file, play it, maybe show a few technical details, and then get out of the way.

At the other end, there are nonlinear editors. They want projects, timelines, bins, ingest, media management, proxies, conform decisions, and an entire editing environment before you have really decided what you want to do.

For a long time there was another kind of tool in the middle.

QuickTime 7 Pro is probably the clearest example. You could open a file, inspect it closely, make one precise change, export it, and close the application. It treated the media file itself as something you could work on directly.

That workflow mostly disappeared.

**MLT Player is my attempt to bring it back.**

It is a frame-exact media browser, organizer, and precision player for Linux, built with Flutter on top of [MLT](https://www.mltframework.org/).

It is not an NLE.

It is not trying to become one.

The basic idea is much smaller:

```text
open a directory or media file
  -> browse visually
  -> organize only if useful
  -> inspect precisely
  -> make one surgical change
  -> export
  -> return to the browser
```

That directness is the point.

## Start with the filesystem

One of the decisions I cared about most was not forcing media through an import step.

MLT Player's Explorer is filesystem-first. You can open a normal directory and immediately browse the media that is already there.

The files stay where they are.

Explorer generates representative thumbnails through MLT itself, so the browser and the player are looking at media through the same underlying engine. Instead of blindly sampling one arbitrary frame, thumbnail generation can look for something representative and avoid obvious black leader, slates, or fades.

From there you can filter by filename, sort the directory, change thumbnail density, move through navigation history, save favorite folders, or open a file directly.

And because this is still desktop software, little things matter.

Right-clicking a media thumbnail can now **Reveal in File Explorer**. On Linux, MLT Player uses the Freedesktop `FileManager1` interface so the desktop file manager can open the containing directory and select the exact source file.

That sounds small. It is small.

It is also the kind of operation I use constantly.

I want the application to understand that the filesystem is not an implementation detail hidden behind the interface. It is still where my media actually lives.

## Projects without taking ownership of the media

Filesystem-first does not mean organization is useless.

Once a collection grows, I still want bins, ratings, tags, color labels, favorites, and bookmarks. I just do not want the application to pretend those things require moving the source media into a proprietary project structure.

MLT Player calls its organizational workspaces **Projects**.

A Local Project can contain nested **Catalogs**, which behave like lightweight bins. A media file can belong to several Catalogs at once without being duplicated or moved.

The physical file has one location.

Its organizational meaning can have several.

That distinction matters to me.

A Catalog can contain another Catalog, and parent Catalogs now expose those child bins directly in the main Explorer grid as simple clickable tiles. If a parent contains nested bins but no direct media, MLT Player no longer tells you that the Catalog is empty. The structure itself is visible.

The Project view also summarizes ratings, tags, colors, bookmarks, and Catalogs across the workspace.

This creates two different kinds of organization.

A Catalog is intentional membership: I explicitly put something there.

A smart view is computed from metadata: show me everything rated five stars, everything with a particular tag, everything marked with a color, or every media file that currently contains a bookmark.

The distinction lets organization grow without turning the application into a database that owns the media.

## The Player is where precision starts

Double-click a file and the interface changes from browsing to inspection.

This is the part of MLT Player that most directly comes from the QuickTime 7 Pro idea.

The Player supports frame-exact stepping, J/K/L shuttle, explicit In and Out marks, Play Selection, non-destructive trim with Undo and Redo, embedded source timecode, and deeper technical inspection of the source.

If I need to know the codec, pixel format, colorspace, transfer characteristic, color range, channel layout, bitrate, stream structure, or source timecode, that information should be reachable without leaving the application.

But precision is not only about metadata.

A forty-minute video is still one file on disk, even though it may contain hundreds of meaningful visual changes.

That is why MLT Player has a **Storyboard** view.

Instead of reducing the video to one thumbnail and forcing me to remember everything I saw while scrubbing, Storyboard samples the timeline into a visual array. Time becomes spatial. I can see scene changes, recurring camera angles, long static sections, presentation slides, faces, and breaks in the recording at a glance.

It is a simple idea, but it changes how quickly a long file can be understood.

## Bookmarks are exact moments, not screenshots

Bookmarks work in a similar way.

A bookmark in MLT Player is not an exported image. It is an exact source-frame reference.

I think of them as soft screenshots.

They can carry a generated visual preview, but underneath that preview is still a precise coordinate in the original media. Clicking one takes you back to the exact moment.

That becomes useful very quickly when reviewing long recordings.

And because exporting five, ten, or twenty bookmarks one at a time becomes tedious, the Bookmarks view now has **EXPORT ALL**.

Choose one destination folder and MLT Player creates a per-movie bookmark directory, then exports every bookmarked frame as a composited PNG using the existing frame-export path.

The filenames use exact source-frame numbers, so the bookmark remains unambiguous even if the active trim changes later.

Again, the feature is not large.

The workflow improvement is.

## Small composition, not a timeline

MLT is capable of much more than playback, and it would be easy to keep adding features until MLT Player accidentally became another editor.

I am deliberately resisting that.

There is no NLE timeline.

There is, however, a small three-layer composition system because there are times when inspecting or exporting a media file requires a little more than one flat source.

Each layer can have its own timeline start and end, source In and Out, opacity, visibility, position, scale, anchor, alpha interpretation, and audio gain.

The important part is that this remains bounded.

The Player still feels like a player.

You can make a small compositing decision without entering a completely different editing workflow.

## Export should be separate from playback

Another architectural decision was keeping export separate from the live playback graph.

The preview graph is for interaction.

The export graph is for deterministic output.

MLT Player currently supports H.264 delivery, ProRes 422 HQ master output, WAV, current-frame PNG, bookmark PNGs, and PNG image sequences.

Exports run in the background with progress, cancellation, and partial-file cleanup.

More importantly, preview and export derive composition from shared policy code and are checked against each other in CI. I do not want an effect or layer placement to look correct in the application and then quietly render differently when exported.

That kind of mismatch destroys trust in a media tool very quickly.

## Transcript navigation belongs next to the picture

MLT Player also understands SRT sidecar subtitles.

They can be displayed normally over the image, but they can also be opened as a searchable transcript sidebar.

Search for a phrase, click the result, and the Player seeks to the corresponding time.

This is where MLT Player connects naturally to [Redleaf](https://github.com/nathanfx330/redleaf), my document and transcript research system.

Redleaf can organize meaning: documents, passages, entities, relationships, and transcripts.

MLT Player organizes media and time.

An SRT timestamp is where the two meet.

A Redleaf Project can therefore exist as a first-class workspace inside MLT Player. The application can cache Redleaf Catalog and transcript snapshots, browse them while disconnected, resolve verified local media, and hand an exact transcript into the Player with the corresponding media.

But Redleaf is optional.

MLT Player still works as a normal local media application without it.

That separation is important. Integration should add another path into the media, not turn one application into a hidden dependency of another.

## Flutter owns the application. MLT owns the media.

Underneath all of this is a fairly simple architectural rule.

Flutter owns the application.

MLT owns media.

Flutter handles the interface, project organization, navigation, settings, and interaction. The native bridge gives MLT responsibility for the things it is actually good at: decoding, timing, playback, thumbnails, composition, and export.

That division has taken some work to get right.

Media playback is full of cases where "current frame" can mean several different things depending on whether you are talking about transport position, producer position, the last frame delivered to the texture, or the frame an export graph should resolve.

A player can look simple while hiding a surprising amount of state underneath it.

The goal is to keep that complexity below the surface.

The interface should still feel immediate.

## The kind of software I want to use

MLT Player is still evolving, but the shape of it is much clearer now.

I do not want another application that asks me to reorganize my entire media collection before I can use it.

I do not want a player that treats the source file as a black box with a Play button on top.

And I do not want to launch a full editing suite every time I need to inspect a source closely, mark a few exact moments, trim something, export a frame, or make one small compositing decision.

I want the space in between.

A browser that respects the filesystem.

Projects that organize without taking ownership.

A player that understands frames.

A storyboard that makes time visible.

Bookmarks that point to exact moments.

A small set of editing operations that stay small.

That is what MLT Player is becoming.

The project is open source here:

https://github.com/nathanfx330/MLT-Player
