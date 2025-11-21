---
tags:
  - LLMs
  - public
  - Programming
title: Removing Barriers
date: 2025-11-20T16:20:12-0800
---

One of the nice things about LLMs and their ability to "program" things is that it really make it easier to iterate and test out ideas for small applications. I've been using LLMs on and off in order to figure out where in my workflow these tools have a place (and where to not include them at all). When kept on a short leash, they c16:18an rapidly remove barriers to creating applications for personal use.

#### Warning

<details>

<summary>AIs have really shitty taste (its a reflection of humans)</summary>

I'm a partial skeptic about the whole "AI will replace all programming" thing. I think this boils down to a matter of taste. Often the leash is kept short because the model does something that I'm not asking for, or overcomplicates what I'm doing. But the shit that bugs me the most is the fucking comments that it adds in for no fucking reason at all.

e.g.

```typescript
// Configuration
const CONFIG = { webAclName: "your-web-acl-name", webAclId: "your-web-acl-id", region: "us-east-1", scope: "REGIONAL" as Scope, // or "CLOUDFRONT" };
```

Adding noise in the code with `// Configuration` is a cardinal sin, and if you write with comments like this you deserve to be forced into self-flagellation.

Here is another example, where the comments are not adding anything.

```typescript
} catch (err) {
// Handle fetchConfig errors
 console.error("Failed to fetch config:", err);
 throw err; // or return a default config }
```

Comments should focus on the `why`, the `what` should be apparent in the written language itself.

</details>

#### obsidian

I migrated all my notes, blog-posts, and daily posts into Obsidian after really being amazed with [clipper](https://obsidian.md/clipper). What I really enjoy about it, is that it allows me to move process to the background, and forces the writing and note taking to the forefront of thought. I needed it to become the centralized location for all my notes, including my blog posts (remember those when we did them?)

#### barriers

There were two barriers in my case:

1. The separation of notes and blog posts (artifacts like photos also become fragmented)
2. I wanted to keep Hugo / Github as my publishing platform
   1. [Obsidian Publish ](https://obsidian.md/publish)looks sick! Use it!

The first issue was relatively easy, it just took some massaging of the posts to move them their Hugo template format into something that was playing nice with Obsidian.

The second part was a bit more involved. I was thinking about how to "find / grep" my way into a pipeline with some [Taco Bell Programming](http://widgetsandshit.com/teddziuba/2010/10/taco-bell-programming.html) ... But I think that would have been a bit risky as there are personal notes in this vault, its my diary man common! I ended up with a three step solution.

1. Create a tree of posts / artifacts (explicitly tagged with `public`)
2. Create a [page bundle](https://gohugo.io/content-management/page-bundles/) that can be used with Hugo.
3. Create pipelines so this can be "semi-automated" (don't publish my diary man!)

#### What about the LLMs?

Yeah this was supposed to be a post about how LLMs are cool to build projects, and we are getting to that... The part that I want to highlight is not the fact that the LLM did a good amount of the programming for me, but rather overcoming the barrier of entry to getting this application working was very straightforward. Understanding the constraints of the system, and the direction of where things needed to go was the most important thing. Looking back at commits that created the scripts and the subsequent movement of files we are talking 2-3 hours of prototyping to get a usable system. In my opinion thats pretty fast for custom software that "just works".

```
2025-10-14 13:11:29 -0500 5d591e5 by amar, updates to daily
2025-10-13 11:53:39 -0500 b63f2fe by amar, unix-time-stap because no `:` allowed
2025-10-13 11:49:40 -0500 2345ea9 by amar, iso time for branches
2025-10-13 11:41:46 -0500 30d5afe by amar, draft aws-iam-logging post
2025-10-13 11:41:37 -0500 6f503ed by amar, remove content to simulate deletions
2025-10-12 22:21:26 -0500 e9de8d7 by amar, attempt to fix tags in Blog
2025-10-12 21:49:00 -0500 1c48745 by amar, run prettier before uploading
2025-10-12 21:31:37 -0500 39e4183 by amar, dont post deliberate
2025-10-12 21:31:30 -0500 131a2bb by amar, fix: content dir issue
2025-10-12 17:52:20 -0500 1170bca by amar, update build-and-deploy
2025-10-12 02:16:00 -0500 4742593 by amar, [REDACTED]
2025-10-12 02:11:41 -0500 b28fad7 by amar, ts-node to tsx
2025-10-12 02:06:32 -0500 e9f1115 by amar, add .github/workflow/build-and-upload.yml
2025-10-12 01:56:00 -0500 d3bd96b by amar, oni issues, working bundle exports
2025-10-12 01:50:02 -0500 d496116 by amar, adds scripts
2025-10-12 01:49:29 -0500 0f26b13 by amar, [REDACTED]
```

#### So what?

So nothing, I just wanted to shout out into the dead internet about an idea that I had, and the tooling that I leveraged to materialize the idea into something that works for me. The exercise was interesting, and I think it helped with understanding how to manipulate these LLM / Agent tools in order to be more effective to getting things done.
