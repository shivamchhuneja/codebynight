---
title: "The More Technical I Get, the Less I Want to Automate Everything"
date: 2026-06-28
tags: ["automation", "GTM engineering", "AI", "AI security", "backend engineering"]
categories: ["AI", "GTM Engineering"]
draft: true
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
description: "AI and automation save me time but they also make it much easier to build small programmes that make life very difficult for me later."
---

I still get excited when I see a boring task and think, "I think I can do something about it, I can build something to automate this."

That is partly the GTM engineering mindset I've been in for a while now. And so much of the work is spread across things that do not really belong together. CRM fields, spreadsheets, call notes, dashboards, Slack messages, enrichment tools, random CSV exports, and someone asking for an update five minutes before a meeting.

If I can turn two hours of this into ten minutes by spending 10 hours to build something, I am interested lol.

Up until a couple years ago that was all I thought. Can I automate it? Great. I'm on it.

Now I pause a bit more.

This is annoying because I still like automation. I still use AI all the time and I do like getting small scripts working. I like seeing a workflow finally run without giving me some completely useless error. Beautiful. I guess I also like the grind of going through the errors and issues in a script step by step to get to the final point.

Anyways, my immediate next thought is who is going to deal with this when it does something weird next month?

## I used to treat automation like a shortcut

A lot of GTM work makes automation feel very obvious to me. You have an account list that needs cleaning, a few hundred companies that need research, calls that need summaries, fields that somehow need to be updated in three different places, and a report that people suddenly need in 20 minutes because apparently the meeting was always going to happen today.

So the manual step starts looking like the problem and you need to make the spreadsheet look less like it was created in a panic at 2 AM.

Sometimes that manual work is genuinely dumb and I think it should disappear. I am very happy to delete a task that is only there because two tools do not talk to each other properly or them talking is behind some stupid $1200 a month enterprise plan.

But I have also started noticing that some of the tiring manual work is where the confusion happens.

A report might take forever because nobody agrees what the number is supposed to mean. A CRM field can be weird because three people use it in three completely different ways. An approval can feel like unnecessary friction until I realise the person doing it is the only one who actually knows the customer context.

You can automate all of that and make the process look much cleaner. The same confusion is still there, it is just moving faster now.

Which is a very satisfying, feel good way to hide a problem, I guess.

## A workflow running does not mean I am done with it

When I finally get a workflow to run after going through the usual errors and weird issues, I want to be done with it almost immediately, especially if I have spent a good amount of time trying to make two tools connect or share outputs with each other. In a couple test runs if nothing has exploded yet my brain immediately starts calling it a success.

But getting it to run is only the first part. The uncomfortable part comes later when somebody else starts using it or when the same workflow has to deal with a change I did not think about while I was building it.

A field might get overwritten even though someone had entered useful context there. An alert might send an update in slack every morning but nobody is really responsible for doing anything with it. An AI summary might drop the one thing an account manager actually needed to see while still looking completely polished and believable. Damn LLMs.

That is just real work I guess. Things change, people use systems differently from how I imagined they would use them, and someone eventually asks why it did that.

This is why I have started thinking of small workflows differently. They can feel like shortcuts while you are building them but once another person depends on them, they have inputs, outputs, permissions, strange edge cases, and a work outside the local session where they were made.

I wrote about something similar while working through a small [AI agent guardrail](/posts/ai-agent-guardrails-look-simple-until-you-code-them/). The task was only a path check, but the exact path being checked decided what an agent could touch and edit. Automation has a lot of those details around it and they decide whether a useful workflow stays useful or becomes a hot potato.

## AI makes this easier in a slightly dangerous way

AI has made it much easier for me to build the first version of something whether I need a script or a better explanation for an error message. I use AI because it helps me get started quickly and helps me move through the annoying parts of building something. Although I do make it a point to not use any sort of AI when learning and going through my backend course on boot.dev or building the rust project in codecrafters.

Anyways, the trouble is that the first version can look finished before I have really thought through the actual work. A script has structure and a workflow has nice boxes and arrows, and an output AI summary comes back in complete sentences with headings so it becomes very easy to feel like the thinking is already done.

Sometimes it is done, but sometimes I have just made something that looks like a system without really understanding the process under it. I have started asking myself whether I want to automate a task because I understand it well and can clearly see the boring part or whether I am mainly irritated by the task and want it out of my face.

Both feelings are normal but they lead to very different things. The irritation is useful because it points at work that feels bad although it does not tell me what I should build to fix it. I wish it did because that would make life much easier.

## Permissions changed my perspective around all this

Working in AI security and governance has made the access angle much harder to ignore. A workflow sounds harmless when I only describe the task like summarising customer calls, updating a CRM field when a lead matches a condition, or sending a weekly report to the team.

Then I think about what it needs to do those things. It might need call recordings, transcripts, CRM data, support tickets, internal notes, an API token, or browser access. Some of that data may be in a place where people assumed it was only being used by one tool.

At that point the small workflow is attached to much more of the business than it seemed in the first sentence.

This is probably the biggest thing I took away from [working around AI security and governance](/posts/one-year-ai-security-governance-see-ai-differently/). I still care whether a tool works because obviously I do, but I also start thinking about what it can read, what it can write, where the data goes, whether it can overwrite something useful, and whether I can still get to the original source when the AI gets something wrong.

I know this makes me sound like the person who ruins fun by asking about permissions, and maybe I have become that person. I still want the automation but I also want to know what I am giving it access to before I connect it to half the company and call it productivity.

## The boring things have started mattering more

For me logs, ownership, dry runs, smaller scopes, keeping the original data, and making it clear who is supposed to act when a workflow runs all used to feel like the decoration. The interesting thing was the AI, the integration, or the workflow that did the clever little thing that saved time.

Now I think the boring stuff is probably what keeps the clever part useful for longer than one week. If an automation changes a CRM field, I want to know whether it can overwrite something a human wrote. If it sends an alert I want to know who will actually do something with it. If it summarises a call I want the transcript to stay there so the summary does not become a fake version of the truth that everyone keeps repeating.

All of this sounds obvious when I write it down but it is much less obvious when I am 4 hours into setting one of these up and tired. I have definitely wanted to feel clever for a few minutes after getting something to work and I probably still will but I trust that feeling less than I used to.

## Some of the boring solutions are better than the fancy ones

The most advanced thing is not always the best thing to build for the problem in front of us.

A saved query can be enough and a spreadsheet formula can be enough too. A simple rule-based alert can be better than an AI classifier that is trying very hard to sound smart. Sometimes a manual review queue with enough context is the better answer because somebody needs to make an actual call instead of pretending the workflow can decide everything by itself.

This is especially true in GTM work because so much of the work is actually somewhere in between structure and judgement. You can automate research, reporting, enrichment, routing, and follow-up, and all of that can help but bad definitions under the system do not become good just because the system runs faster.

Messy lifecycle stages become messy automated lifecycle stages and unclear ownership becomes unclear ownership with Slack notifications. A CRM nobody uses can become a CRM that is now changing itself while nobody runs it which is its own genre of suffering.

I keep coming back to the point I made in [Churn Is Not a Data Science Problem](/posts/churn-is-not-a-data-science-problem/). The model, dashboard or workflow is only one part of the work. Someone still has to decide what the field means, what action should happen, who owns it, and when a human needs to look at it. A useful automation usually has a very boring answer to those questions and that is probably a good sign.

## Learning backend stuff make me focus on the middle part too

I've been learning backend programming and now I notice state, retries, timeouts, data models, permissions, rate limits, error handling, tokens expiring, weird inputs, field names changing, and a vendor changing an API response because apparently nobody enjoys peace. I do not understand all of this deeply yet because I am still learning but I understand enough now to know that connecting two tools is rarely only about connecting two tools.

There is always more going on in the middle and that is where the assumptions are and errors pop up. It is also where I find out whether a workflow can survive someone using it like a normal person instead of the perfect user I had in my head while building it.

This has made me more patient with things I used to skip past like naming fields properly, keeping scope small, writing down assumptions, testing weird inputs, preserving raw data, and giving a workflow fewer permissions than it asks for by default. Nobody wants to watch a 40-minute YouTube video called "Shivam thinks about field ownership before updating the CRM" although maybe there is an audience for that.

But that boring stuff is what makes me trust a workflow more.

## The question is different for me now

I still automate things and I still like AI for the text and data chores. I still get excited when I can take some ugly repetitive work and make it easier.

Earlier I mostly asked whether I could automate the task. Now I also ask whether I am willing to own the little thing I am creating when I do it because that question makes me think about data before the nice demo and permissions before I connect another tool.

Real work has tradeoffs and I am not trying to become the priest of perfect systems design over here.

I am just less relaxed about automation now because I understand a little more of what can go wrong after it starts working.

The more technical I get the less I want to automate everything. I still want to automate the right things but I want to understand what kind of programme I am building before it decides to make life difficult for me later.
