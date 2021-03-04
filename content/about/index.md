---
slug: about
title: Why this separate site?
---
The big question is of course: 

> Why are you not using SharePoint, Confluence, a Teams Wiki or something other provided by Rabobank for publishing these articles? Now they're much harder to find!

A couple of reasons:

- I've been at Rabobank for over 10 years. I've seen systems come and go. Sometimes things migrate well, sometimes they migrate barely, sometimes they don't migrate at all. Were I to use Rabobank systems my collection of articles would be spread out across many systems, in different formats. I wouldn't feel in control. You could argue that I shouldn't care about stuff I wrote years ago. But I do.
- I prefer plain text and offline work. All my work notes are in Markdown in a Git repository on my local machine, and have been for years. I can easily find all the stuff I ever wrote wherever I am, can easily manipulate multiple documents at the same time through some scripts, and so on. I don't want to lock my content away in some system that I can't control.
- I want complete control over how everything is structured and looks. These are *my* articles, it's up to me to present them who *I* like and give them a distinct appearance.

## How it works

The setup is pretty simple:

- All my notes are in Markdown, in structured folders. Have been for years.
- Next to that I have a [Hugo](https://gohugo.io) configuration that symlinks into my note structure at the appropriate places. I can reuse any of my notes instantly on this site. Updating a note also updates this site. No stale copies.
- Everytime I run `hugo` it generates a static website. It does so in milliseconds. It's really, really fast!
- After (re-)generating the static site all that I have left to do is publishing it somewhere, for you to find.
