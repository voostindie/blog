---
title: "How I Manage This Blog"
slug: "how-i-manage-this-blog"
date: 2021-11-25
draft: true
toc: false
cover: "images/hugo-github-pages.svg"
---
## TL;DR

- Markdown files in a Git repository
- Static site generation with Hugo
- Automatic publication to GitHub Pages

If these words make you go woozy, then this is not for you.

## Markdown files in a Git repository

Over a decade ago I settled on [Markdown](https://daringfireball.net/projects/markdown/) for all my writing. Although it has some drawbacks, the benefits easily outweigh them. At least for me. I can edit my writing anywhere, with any text editor, also 30 years in the future. I can run scripts on them to modify them in batch or extract information from them for reports, and so on.

To be honest I don't use "plain" Markdown. I use generally accepted extensions like YAML front matter, code fragments, tables and wiki links. 

So, if I'm going to maintain a blog, there's no question about how I'll do that: in Markdown. To get versioning in place I stick my posts in a [Git](https://git-scm.com) repository.

As a backup, I push my local repository to [GitHub](https://github.com). Having the repository on GitHub means that I can do other nifty things with my content, like publishing it to a website on GitHub Pages. But before we get into that I have to explain how I turn my Markdown files into an actual website.

## Static site generation with Hugo

Since I prefer Markdown, and plain text files on disk, it will not come as a surprise that I prefer static site generators as well. The one I've settled on is [Hugo](https://gohugo.io). It's simple to use, flexible, and as fast as the tagline promises. (And it's not written in JavaScript but in Go, which is a big plus in my book.)

To turn my pieces of text into posts for this blog, all I have to do is move them in the `content/posts` directory of a fresh Hugo site, and sprinkle some YAML Front Matter at the top. I then run `hugo` and presto: out comes a static website.

To spice up the look & feel of this blog I went the extra mile by forking the [Hello Friend NG](https://github.com/rhazdon/hugo-theme-hello-friend-ng) theme and customizing it a bit with different fonts.

## Automatic publication to GitHub Pages

When I'm happy with a post, I commit it to the local Git repository and then push it to the one on GitHub. A few seconds after that it automatically shows up on this site, at <https://voostindie.github.io>. "How does that work?", you might be wondering. Answer: through the magic of [GitHub Actions](https://docs.github.com/en/actions) and [GitHub Pages](https://docs.github.com/en/pages).

In my Git repository I have the following file at `.github/workflows/github-pages.yml`:

```yaml
name: GitHub Pages
on:
  push:
    branches:
      - main
jobs:
  deploy:
    runs-on: ubuntu-20.04
    steps:
      - uses: actions/checkout@v2
        with:
          submodules: true
          fetch-depth: 0
      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'
          extended: true
      - name: Build
        run: hugo --minify
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          external_repository: voostindie/voostindie.github.io
          personal_token: ${{ secrets.ACTION_ACCESS_TOKEN }}
          publish_dir: ./public
          publish_branch: main	
  ```

What this does, on every push to the repository on GitHub, is trigger a fresh build of the static site with Hugo, followed by a push of that build to my public repository [voostindie.github.io](https://github.com/voostindie/voostindie.github.io) at GitHub. That's it! GitHub Pages takes care of serving this site on the URL you're looking at now.

What makes this great is that:

- Once set up, it all happens automatically. I don't have to think about it anymore. Just `git push` and I'm done.
- It's all managed. I don't need to set up a server, apply regular security patches to the underlying OS, replace SSL certificates, configure load balancers and all that stuff.
- It's all free!

## References

- [Cover image courtesy of Michael Schnerring](https://schnerring.net/posts/create-a-hugo-website-with-github-pages-github-actions-and-cloudflare/).
- [GitHub Actions Workflow for Hugo](https://github.com/peaceiris/actions-hugo).