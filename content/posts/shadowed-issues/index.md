---
title: "shadowed issues"
date: 2023-10-30T23:38:49-07:00
tags:
  - public
---

It's always better to know what the issue at hand is, and to turn off the alert
for this issue, so that other issues can be observed. This is true for most
types of engineering, my observations has been with race-cars, and software.

The RSX always had a check engine light for a gas-cap leak (fixed with a new
seal), but I failed address the issue right away. Had I addressed the issue, I
would have known that I was also throwing codes on the racetrack for a VTEC
solenoid (oil probably), and a knock sensor failure (bye-bye motor), when I
was on the race track. Motors really don't like being miss-configured and
hammered on.

It was my comfort in saying,
"Oh it's just the gas-cap".
That masked the new issues.

My boss had mentioned that he turned off tests while doing some week-long
feature building, this same thing came up, and I noticed the parallels. We
disabled `integration` testing of a range of features because their consistent
failure would potentially mask, and make us numb to seeing tests fail. Which
could mask new failures that occur in the system.

Better to know, and address, then it is to allow it to be persistent. Turn off
the tests, create a new issue, or wrap with some type of `expect.failure()`.
But don't let "failures" or "errors" become the norm.

> [!NOTE]
> blew a motor in the Tacoma by not following this advice, detonation caused by the injectors cracked the head near the valve, in our case the spark-plug seized into the head on cylinder 2
