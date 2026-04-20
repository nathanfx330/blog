---
title: "EchoText Update"
date: 2026-04-20T03:02:47-04:00
draft: false
---
{{< figure src="echotextcover.png" width="750px" >}}

Text-to-speech has taken a massive turn this decade. We went from reading obscure Google Tacotron papers to listening to incredibly natural-sounding neural networks taking the world by storm. 

But there is a catch. Most of the time, the good stuff is locked behind a paywall. 

There are local, open-source alternatives, but they are often difficult for the average user to implement. That was part of the reason I built **EchoText**. I wanted to use [Piper](https://github.com/rhasspy/piper). It isn't the most polished TTS solution, but its vision and local-first ethos strike a solid chord with me. 

EchoText was born out of a specific moment: staring at a massive wall of text and realizing I didn’t just want to scan it with my eyes. I wanted to absorb it.

{{< figure src="echotext1.png" title="The EchoText interface, featuring dynamic voice selection." width="750px" >}}

I have spent the last few weeks ironing out exactly what that experience should look like.

### Streaming Thought
If you are staring at a wall of text, you don't want to wait for a progress bar. You want to start listening immediately. 

In this update, EchoText now streams the document bit-by-bit into the Piper engine. By breaking the text down and piping it sequentially, playback starts almost instantly, generating the next chunk in the background while you listen to the current one. 

As it reads, the text is highlighted sentence-by-sentence. If you want to jump around, you just click a sentence, and the audio instantly follows. 

{{< figure src="echotext2.png" title="Text is highlighted sentence-by-sentence as it reads, allowing for interactive playback." width="750px" >}}

### The Vision: Audiobooks for Redleaf

But the real goal—the vision behind this entire update—was something bigger. 

I wanted a way to create a full document "audiobook" export. Not just a `.wav` file, but a perfectly synced `.srt` subtitle file to go with it. 

To do this, EchoText mathematically calculates exact audio durations from the raw WAV headers, sentence-by-sentence, stitching them together without relying on external transcription tools. 

{{< figure src="echotext3.png" title="Exporting the generated audio alongside a perfectly timed .srt subtitle file." width="750px" >}}

Why go through all that trouble?

Because I wanted to be able to take a massive research document, export it from EchoText as an audiobook, and drop it directly into **Redleaf’s SRT viewer**. 

{{< figure src="echotext4.png" title="The generated audio and perfectly synced SRT file loaded seamlessly into Redleaf's media viewer." width="750px" >}}

Now, the loop is closed. You can generate a private, local AI voiceover of any text, load it into your knowledge engine, and follow along with a perfectly synced transcript.

Absorbing information, rather than just scanning it.

If you paste text from an LLM, there is also a new "Magic Wand" tool that strips out Markdown artifacts (`**bold**`, `### headers`) so Piper reads natural language, not punctuation. And custom voices can now be managed simply by dropping them into folders.

You can find the repository and download the latest release here:  
[https://github.com/nathanfx330/echotext](https://github.com/nathanfx330/echotext)
