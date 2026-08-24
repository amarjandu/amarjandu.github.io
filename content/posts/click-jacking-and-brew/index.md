---
title: click-jacking and brew
date: 2026-08-23T21:22:27-0700
tags:
  - software
  - macos
  - brew
  - public
---

I wanted to swap my personal and development laptops, so I started migrating users around in MacOs.

I ran into this strange bug after I moved the `foo-dev` user to the `personal` machine...

`brew` specifies what users are enabled to call for installation of packages which is mentioned [in their docs](<[here](https://docs.brew.sh/Installation)>).

I wanted to reinstall it as the new user onto the machine, I had nuked the other user account, so it seemed "more proper".

Upon attempting to install I ran into a little uBlock origin ClickJack alert (My first time!)

![first-alert!](Attachments/Screenshot%202026-08-23%20at%207.22.25%20PM%201.png)

oh the paranoia started, I ran back to duckduckgo, and checked the search, maybe I in-fact was on the wrong site.

![wut](Attachments/PNG%20image%201.png)

uhhh...

![why](Attachments/PNG%20image%202.png)

Thats a little weird...
This lead me down a rabbit-hole, which one is the real one?

And what triggered the alert?
I ended up in the `ublock origin AD filter` looking at this [commit](https://github.com/uBlockOrigin/uAssets/commit/0e73cbb764c9a6b543cc1fe43ad8f7d8776d7f3a) (that allow-listed another site).

Not sure how developers have not run into this issue, maybe its a race condition with how people are installing stuff to their setup, maybe the brew installer was getting installed (for the first time) before uBlock Origin. `brew.sh` seems big though.
