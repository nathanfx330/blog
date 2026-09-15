---
title: "The File Is Not the Unit of Thought"
date: 2026-09-14T20:35:00-04:00
draft: false
---

Redleaf and MLT Player were built around the same argument: the file can remain the unit of storage without remaining the unit of thought.

Redleaf approaches that problem through documents, transcripts, entities, passages, and relationships. MLT Player approaches it through media, time, and visual structure. One lets me begin with meaning and descend toward an exact place in a source. The other lets me begin with the source, turn time into something I can see at once, and move back toward meaning.

They are different interfaces built around the same idea. Information should not be trapped by the container it happens to be stored in.

## How we actually learn

Think about learning what an apple is.

At first, an apple is simply a thing. You see it, touch it, taste it, and learn some of its properties. Then you encounter other things that resemble it in some ways and differ in others. Eventually you form a larger abstraction: fruit.

That abstraction gives you somewhere to put new experience. When you encounter a mango for the first time, you do not begin from nothing. You move upward toward what it shares with things you already know, then downward again into what makes this particular thing different.

The movement looks something like this:

specific

similarity

abstraction

comparison

new specific

The abstraction is not the destination. It is how we travel between specifics.

Computers still tend to organize information in almost the opposite order.

Imagine receiving two hundred files you have never seen before. Where do they go?

You can create folders before reading them, but then you are classifying material you do not yet understand. You can read everything before organizing it, but then the organizational system has done nothing to help you learn the collection.

What usually happens is somewhere between the two. You begin reading, make some folders, discover recurring subjects, move things around, and eventually realize that the distinction you thought mattered at the beginning was not actually the important one.

The problem is not that folders are bad. A folder simply asks a question too early:

Where does this belong?

You may not know yet.

## One place is not one meaning

A file normally has one physical location, and that is useful. If I want to know where its bytes live, there should be an answer.

But physical location and conceptual belonging are not the same thing.

One document may concern several people, several places, several subjects, and several events. It may matter for completely different reasons depending on what I am doing. Putting it in one folder does not make those relationships disappear. It simply means the filesystem does not have a particularly rich way to express them.

We already accept this in narrower domains.

A photograph can exist once while appearing in several albums. It can be associated with a person, grouped by date or place, marked as a favorite, and found through search. Nobody expects the image to be physically copied every time it belongs to another collection.

Email labels work similarly. One message can participate in several categories without becoming several messages.

The object has one physical existence and many conceptual relationships.

That idea has appeared repeatedly in desktop computing as well. Tags, attributes, saved searches, and systems such as WinFS all attempted, in different ways, to loosen the connection between where something is stored and what it belongs to.

The difficulty is that richer metadata can easily become another filing job.

If the folder asks, “Where should I put this?” and the metadata system asks, “What should I tag this with?” then the user still has to understand the material first and perform the classification afterward.

That does not solve the original problem.

The interesting change happens when the machine can help expose possible structure while understanding is still taking place.

## Let the structure emerge

This is where Redleaf begins.

If I give Redleaf a collection of documents I have not read, I do not want it to tell me what those documents mean. I want it to give me places to begin.

People recur. Places recur. Organizations recur. Relationships and combinations begin to appear across the material. Some things occur once. Others appear repeatedly.

Those observations provide an intermediate level between the whole file and the individual word.

That level matters.

A file is often too large to be the smallest useful unit of thought. A token or individual word is too small. Human beings naturally work in the middle: passages, scenes, sections, moments, statements, stretches of conversation.

Models benefit from much the same scale. Retrieval becomes more useful when a source can be broken into units large enough to preserve context but small enough to compare, retrieve, and connect.

That intermediate level gives both the person and the machine somewhere to meet.

The apple ladder appears again.

A passage is specific. Recurring entities and relationships expose similarities. Those similarities create abstractions. I can then select one of those abstractions and descend into another specific passage.

If a person appears repeatedly, I can enter through that person rather than through a folder. I can see where the entity occurs, move into the relevant document and passage, read the surrounding material, and then move outward again through another relationship.

The file has not moved. Its folder has not changed.

What has changed is the number of doors into it.

A document can participate in several subjects. A person can connect several documents. A place can join material that would never have shared a directory.

Organization can begin emerging while understanding is still happening.

## The machine can propose structure without owning it

There is an important tension here.

Redleaf derives some of this structure automatically.

That could sound very similar to the direction mobile operating systems have taken, where the system increasingly decides which objects to surface and which categories should matter.

The distinction I care about is not manual organization versus automatic organization.

It is opaque structure versus addressable structure.

If Redleaf finds a person throughout a collection, the result is not merely a recommendation saying that I may be interested in something. It is something I can enter.

I can inspect the occurrences that produced it, reach the original source, read the surrounding passage, move sideways into another relationship, or abandon that abstraction entirely and navigate the material another way.

The machine can propose structure without owning the structure.

Automation should increase the number of paths available to me, not quietly choose the path on my behalf.

## A video is more than one rectangle

Video exposes the same problem from the opposite direction.

A forty minute video may contain hundreds of meaningful changes. People enter and leave. Locations change. Slides appear. Cameras move. Objects appear. Conversations shift.

From the filesystem's perspective, however, the entire sequence is one file.

Often it is represented by one thumbnail.

That thumbnail may be a perfectly good image, but it is a terrible representation of time. Forty minutes of changing visual information have been compressed into one rectangle.

To understand what is there, we normally open the file and let it pass in front of us sequentially. Even a seek bar leaves most of the comparison work to memory.

MLT Player was designed to change that.

Instead of representing the video with one thumbnail, it can produce an array of thumbnails sampled through the timeline. Time becomes spatial.

Now the eye can compare moments directly. A person appears across several images and then disappears. A room changes. A presentation becomes a face. A still section gives way to movement. A camera angle returns later in the recording.

The array is not merely decoration around a seek bar. It is an abstraction of time.

Again the movement is:

specific frame

visual similarity

temporal abstraction

comparison

specific moment

The computer already had every frame. The change is in how those frames are exposed to human perception.

## Meeting at the timestamp

This is where Redleaf and MLT Player meet.

Redleaf was built around synchronized transcript files because a transcript gives semantic information a coordinate in time. A line in an SRT file is not merely a sentence. It is a sentence that happened somewhere in the media.

Redleaf can travel in one direction:

meaning

passage

timestamp

media

I can begin with a person, phrase, or relationship, descend into a transcript passage, and use its timestamp to reach the corresponding moment in the recording.

MLT Player travels in the opposite direction:

media

timestamp

passage

meaning

I can begin with the visual structure of the recording, choose a moment, move through its timestamp into synchronized text, and from there move outward into the semantic relationships Redleaf has derived.

They meet at the timestamp.

That may look like an implementation detail, but I think it exposes something larger.

The transcript and the video are containers.

The things we actually think about are often inside them.

## Smaller than a file

That raises a question about what a computer should consider addressable.

We already have shortcuts, aliases, and symbolic links. They let one file appear somewhere without moving the original.

But they still assume that the file itself is the thing worth pointing at.

Often it is not.

I may care about one passage inside a document, one occurrence of a person, thirty seconds beginning at 04:12, one frame, or the transcript passage synchronized with that frame.

Those things have meaning even though none of them needs to become a separate file.

A normal alias can say:

this file over there

A richer reference can say:

this passage inside that document

this moment inside that video

this occurrence of this entity

this span of text synchronized with this span of media

The file can remain the unit of storage without remaining the unit of thought.

## References are fragile

There is an obvious objection.

Files are convenient addressable objects partly because their boundaries are relatively stable.

A timestamp may cease to identify the same event if a video is trimmed. A paragraph position may move when a document is edited. A frame number may change after transcoding.

Once we begin pointing inside files, references acquire a problem that ordinary paths largely avoid.

That should not be hidden.

A reference can be made more resilient by carrying more than one kind of anchor: source identity, surrounding text, timestamps, hashes, nearby context, or other information that helps the system recognize the intended target again.

But no reference system can make destructive changes disappear. If the source changes enough, the honest result may be that the reference has become stale.

There is also a second problem: portability.

A relationship that exists only as a row in one application's private database may work perfectly until the material leaves that application.

That is why Redleaf has `.rlink`.

An `.rlink` makes the relationship itself portable. The goal is not to duplicate the source but to allow a meaningful reference into the source to travel.

The source is one object.

The relationship to something inside it can be another.

That does not make the reference immune to change. It does mean the relationship does not have to remain invisible state trapped inside the application that created it.

## The desktop as a surface

Once references can point below the level of the file, the desktop starts to look different too.

The desktop does not need to be another permanent place to store things. It makes more sense as a surface.

A physical desk is useful because unrelated things can be placed beside one another temporarily. Their permanent storage locations do not need to change merely because they matter to the same task today.

A digital workspace could work the same way without being constrained to whole files.

The original document can remain in Documents. The original video can remain in Videos. A passage from one, a thirty second span from the other, a note, an entity, and another source could appear together on a temporary working surface.

They would be references, not copies.

Close the workspace and the underlying files remain where they were. Delete it and the source material survives. The workspace records an arrangement of relationships rather than a relocation of storage.

This is more than a collection of symlinks because the things being arranged can be smaller than files.

The workspace can reflect what I am thinking about rather than where the operating system happens to store it.

## The mobile answer is not the only answer

Mobile operating systems recognized a real weakness in traditional file management. Most people do not want to maintain elaborate directory hierarchies on a phone.

Their answer has often been to make physical location less visible. Show recent items. Show generated categories. Surface likely content. Let applications manage much of their own storage.

On a phone, much of that makes sense.

What concerns me is treating that as the inevitable future of desktop computing.

The answer to a rigid folder does not have to be hiding the folder and replacing it with a machine generated list.

There is another possibility.

Keep the filesystem understandable, but let richer forms of organization exist above it.

If the system generates a collection, let me understand what produced it. Let me enter it, leave it, extend it, or follow one of its relationships back to the original material.

The distinction is not whether the computer performs automation.

The distinction is whether automation gives me another navigable structure or substitutes its judgment for structure entirely.

The machine can notice patterns.

The user should retain the map.

## Where something is stored is only the beginning

Files and folders remain useful.

A file should have a real location. A path should mean something. I should be able to copy a directory, back it up, inspect it, and understand where my information lives.

But location should not have to carry the entire burden of meaning.

The filesystem can answer:

Where is this object?

A relational layer can answer:

What does this object belong to?

A semantic layer can answer:

What appears inside it?

A temporal layer can answer:

When does it happen?

And a workspace can ask:

What do I want to see this with?

Redleaf and MLT Player were built as two approaches to that same problem. One begins with meaning and lets me descend toward an exact moment. The other begins with time and lets me climb toward meaning.

Neither requires the filesystem to disappear.

They simply assume that where something is stored is only the beginning of what a computer ought to know about it.
