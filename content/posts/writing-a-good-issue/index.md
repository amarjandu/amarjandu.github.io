---
title: "writing a good issue"
date: 2024-08-12T23:38:49-07:00
tags:
	- public
---
## What is it?

Issues are a starting point for a observed problem with software.

## What makes a bad issue?

Bad issues can be incomplete, difficult to follow, or don't clearly express the problem at hand.

## What makes a good issue? 

1. Keep it structured.
2. Give all the details (starting from the top).
3. Make it easier to navigate the issue (use Markdown).
4. Give some attention to formatting text (capitalization, etc).
5. Structure the problem clearly (make it easier to follow).

## Providing clear reports

Don't truncate the output, I repeat DON'T TRUNCATE THE OUTPUT.
You don't have a guarantee of how things are written to STDOUT, it's possible that messages are out of order. If you truncate the log that you are reporting it's possible that the team misses something.

## Utilizing Markdown

You ever scroll into an issue and there is a huge execution log from someone? It makes the issue harder to navigate, use a `details-tag` to hide the long execution log (or provide it as a attached file). If needed use something like [gist](https://gist.github.com) or [pastebin](https://pastebin.com/), and provide a link to the full report.

```
<details><summary>Execution</summary>
<p>
$ make build
...
(600 lines later)
ERROR: YOU BROKE IT
</p>
</details> 
```

e.g 
<details><summary>Execution</summary>
<p>
$ make build
...
(600 lines later)
ERROR: YOU BROKE IT
</p>
</details> 

Consider stashing this into your [`Saved Replies` ](https://github.com/settings/replies) so you don't have to google it. 
