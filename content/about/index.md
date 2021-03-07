---
slug: about
title: Why this separate site?
---
The big question is of course: 

> Why are you not using SharePoint, Confluence, a Teams Wiki or something other provided by Rabobank for publishing these articles? Now they're much harder to find!

A couple of reasons:

- I've been at Rabobank for over 10 years. I've seen content systems come and go. Getting stuff in is easy. Getting stuff out, not so much. Keeping track of what's where is a challenge. Yet I care about the things I publish.
- I prefer plain text and offline work. All my notes are in Markdown in a Git repository on my local machine, and have been for years. I can easily find all the stuff I ever wrote wherever I am, can easily manipulate multiple documents at the same time using simple scripting, and so on. I don't want to lock my content away in a system that I can't control.
- I want complete control over how everything is structured and looks. These are *my* articles, it's up to me to present them how *I* like and give them a distinct appearance.

## How it works (for the techies)

The setup is pretty simple:

- All my notes are in Markdown, in structured folders. Have been for years.
- Next to that I have a [Hugo](https://gohugo.io) configuration that symlinks into my note structure at the appropriate places. I can reuse any of my notes instantly on this site. Updating a note also updates this site. No stale copies.
- Every time I run `hugo` it generates a static website. It does so in milliseconds. It's really, really fast!
- After (re-)generating the static site all that I have left to do is publish it somewhere, for you to find.

## What's with the [[text]]?

In some articles you'll find pieces of text surrounded with [[ and ]]. These are links to other documents. This is supported by several Markdown text editors, but it's not part of Markdown itself. Hugo, the tool I use to generate this site, doesn't understand this syntax. Also, because Hugo sees just a small part of all my notes, most links wouldn't work anyway.

I don't want to remove the internal links from my source documents, because they're an intricate part of my notes. They have meaning.

The best thing to do would be to replace the internal links with their plain text counterparts, only on this site. Unfortunately, I don't think that's possible with Hugo today, and I don't want to complicate the build pipeline by adding additional tools and preprocessing steps.

That's why, at least for now, you see these internal links. The good news is that they're just plain text. Nothing breaks. They just look a little funny. View them as a small glimpse into my world: there's much more where this came from; you're just seeing the tip of the iceberg...