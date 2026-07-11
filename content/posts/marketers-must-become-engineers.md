---
title: "Marketers Must Evolve Into Marketing Engineers To Survive The AI World"
date: 2026-04-19
tags: ["Marketing", "Automation", "AI", "N8n", "Workflows", "GTM Engineering"]
categories: ["Marketing Engineering", "AI", "GTM Engineering"]
draft: false
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
description: "Everyone is building AI-powered marketing workflows right now. Most of them will collect dust. Here is why, and what actually works."
---

So I was watching a video from this creator I follow and something felt off about it. His lips weren't syncing right. Not a huge thing, but enough that I noticed. So I went and checked his profile.

Turns out he hadn't actually shown up in any of his own videos for like six or seven months. The whole feed was Heygen. Or something like it, I'm not totally sure which tool.

Anyways, I wasn't sure if it was just me being weird about it, so I went on Reddit. Lots of people had noticed the exact same thing, and nobody was impressed. It was the opposite. Which is interesting because you'd think AI avatars are the kind of thing that sneak past people if they're done well. They don't.

Plus, if you actually think about what an AI avatar is doing, it's just delivering information with a face on it. Which is fine. But if all you want is info delivered, you can ask Claude directly and save yourself the trouble. The whole point of watching a person is the person. The weird pauses, the off-script stuff, the moments they react to what they just said. That's the thing automation can't fake.

So yeah. Automation is bad at presence and trust. It's genuinely good at a lot of other stuff though, which is kind of the point of this post.

## What actually is worth automating

I think people undersell how much of marketing can actually be automated. A big chunk of it honestly. Data collection, report building, pointing out insights that your dashboards don't flag on their own. The first research pass on a piece of content. First drafts and outlines, if you've built the workflow and prompts properly.

The time you get back from that stuff can make a difference. I've felt it in my own work.

But there's a catch I've hit enough times to just treat as a rule now. Human in the loop is non-negotiable. If you try to fully automate output, it looks fine for a week and then it starts drifting in ways you don't catch until someone points it out. The workflow does the monkey work, you do the judgment. That's the plan. I ran into the code version of this later while building [a tiny AI-agent guardrail](/posts/ai-agent-guardrails-look-simple-until-you-code-them/): a prompt can ask nicely, but the boundary still has to exist in code.

My stack is tools like Clay, n8n, Claude and others in between. And tbh Claude's built-in connectors are underrated. A lot of things people assume need a custom n8n flow can be handled through Claude directly, which saves you a weekend. But some things really do need a proper custom flow and knowing which is which mostly comes from having built a few things and broken them.

## Where people mess this up

The biggest mistake I see, and one I've made myself, is going into a build without any plan. You don't think about who's actually going to use it, what the usual failures are going to be, what happens when a node dies. You just start building. And you end up with something that has bad UX even as an internal tool, which means nobody uses it. Ten hours in the trash.

The other thing is just the technical side. Timeouts are really common, especially with AI nodes doing deep research. The node hangs, times out, flow dies. Connector issues are common too, and those get tough to handle fast if you don't have any engineering background to fall back on. Which is sort of why I think this whole role is changing.

Also, and I wish someone had told me this earlier, you don't always need to build the thing. There are tons of tools out there at like $20 a month and a lot of them already solved the UX problem you're about to spend a weekend on. Try one first. Get a feel for what good automation is supposed to look like. Then decide if your own version is worth building. Sometimes it is. A lot of the time it isn't. The rabbit hole of building stuff you didn't need to build takes its toll.

## Marketers are becoming engineers

I think marketers are becoming more like engineers and I think that's correct. Not software engineers. But enough technical chops to build things, debug things, read an error message, understand what an API actually does. And of course, because this is marketing, combined with the creative side and the communication side.

Funny thing is, this shift has been happening for like 7-8 years already. It's not an AI thing. AI is just making the gap show up faster and more obvious. The marketers who were already comfortable with tools and workflows, who already got their hands dirty, are finding this pretty manageable. The ones who weren't are having a harder time.

I know the hype is a lot and being skeptical is reasonable. CEOs of companies wanting more and more investor money will say their tool is revolutionary. That's just how it is. But the time savings on specific things like manual research, report prep, first drafts, that stuff actually makes a difference. I've felt it.

If you're skeptical and you actually want to test it rather than just sit outside and have opinions, spend 15 or 20 minutes building one tiny workflow for something repetitive you already do. Run it for two months. Iterate. Don't expect a single prompt to give you a finished answer, that's not how any of this works. The ones that work got built and tuned over time.

Honestly I think this is more interesting work than marketing was five years ago. Less powerpoint. More actual building. I'll take it.
