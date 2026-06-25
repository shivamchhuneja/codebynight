---
title: "What One Year in AI Security and Governance Changed About How I See AI"
date: 2026-06-18
tags: ["AI security", "AI governance", "GTM engineering", "machine learning", "AI"]
categories: ["AI", "Cyber Security", "Learning"]
draft: false
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
description: "After one year working around AI security and governance, I trust flashy AI demos less and pay more attention to data, permissions, discovery, and the boring systems around AI."
---

I have become the annoying person who asks, “Can I run this locally?”

This is mainly because after working around AI security and governance for a year, I have started noticing how easily data leaves the systems we understand and enters systems we barely think about.

I admit that this is a slightly irritating change in my personality.

A year ago, if I found a tool that helped me automate something, summarize something, enrich some data, or speed up a GTM workflow, my first question was usually: does this work?

Now I still ask that. Obviously. I still like useful tools. I probably use AI more than I did before, not less.

But there is another question I always ask now:

Wait, what did I just give this thing access to?

Okay, this was dramatic, I usually ask that question before giving it permissions, but that wouldn't make it that dramatic for this blog, so deal with it.

Anyways, that question is probably the biggest change.

I still work in marketing and GTM engineering. This is not a “I left marketing and became an engineer” article because that is not true. But over the last year, I have been working in AI security and governance, building more automations, using AI heavily in workflows, and finishing my master’s in data science and machine learning.

That combination changed how I look at AI.

It did not make me anti-AI. It made me less impressed by the shiny part and more interested in the so called boring *(not so boring for me personally though)* questions around it.

Where is AI being used? What data is going into it? Who approved the tool? What can it access? Is anything being stored? Can we prove what happened later?

Annoying questions, basically.

## I thought AI security would be more about security

Before working in this space, I assumed a lot more of AI security would look like security in the obvious sense.

Jailbreaks. Prompt injection. Model abuse. Red teaming. Threats. Demos where someone tricks a chatbot into doing something it should not do.

All of that exists and it matters.

But one thing I did not expect was how much of the work starts before that.

A lot of the problem is just discovering where AI is being used inside an organization.

Which teams are using ChatGPT? Which browser extensions did someone install? Which SaaS tools added AI features without anyone really noticing? Which copilots are approved? Which ones are not? Which internal workflows are sending company data to an LLM? Which AI tools are connected to Slack, Google Drive, GitHub, Salesforce, HubSpot, Notion, or whatever else the company lives inside?

Before you secure AI, you have to find it.

That sounds obvious now but I do not think I fully understood it earlier. I had the more dramatic version of AI security in my head.

In practice, the model is often only one piece of the mess.

The inventory work makes a difference because companies cannot govern or secure something that they don't even know is around them. If employees are using AI tools through personal accounts, random extensions, shadow SaaS, or features bundled into tools they already use, then the company’s AI policy might be very neatly written and still completely detached from reality.

This was one of my first big understandings.

AI security is not only about stopping the weird attack.

Sometimes it starts with asking, “Where is this even happening?”

## The real adoption story is daily-use AI

The riskiest AI use does not always look dramatic.

Most people are not sitting there thinking, “Today I will violate policy and create a compliance headache.”

They are just trying to finish work.

A marketer asks an LLM to summarize last week’s campaign data.

A sales rep pastes customer notes into a chatbot to write a cleaner follow-up.

Someone uploads a CSV to make a quick report.

A support person asks for help summarizing tickets.

A founder throws meeting notes into a tool because the alternative is reading their own handwriting, which is its own separate threat model.

The tasks are small. The intent is normal. The output is useful.

That is exactly why it spreads.

This is also why the governance problem is hard. If AI only showed up in giant, official, expensive enterprise deployments, it would be much easier to track. There would be procurement, review, onboarding, legal, security, some painful spreadsheet somewhere, and at least a chance that someone thought about the risk before the tool went live.

But casual AI does not wait for that.

It enters through convenience.

And because the action feels small, the risk feels small too.

“Summarize this.”

“Rewrite this.”

“Make this into a table.”

“Extract insights from this data.”

I hate that last phrase. It sounds like a dashboard trying to become a LinkedIn influencer. But people do this kind of thing all the time.

If you work in GTM, this is especially easy to understand. So much of the work is text, data, context, follow-ups, notes, reports, messaging, positioning, experiments, and half-broken processes stitched together with tools that were definitely not designed to love each other.

AI helps with that.

Sometimes a lot.

So I do not look at casual AI usage and think, “Wow, people are careless.”

I think, “Yeah, of course they are doing this.”

## GTM teams are exactly where this whole thing scales

Working in GTM probably made this easier for me to see.

GTM teams are often fast adopters of AI because the pain is obvious. There are campaigns to ship, accounts to research, CRM fields to clean, calls to summarize, customer segments to understand, email drafts to write, landing pages to test, competitor pages to read, internal reports to prepare, and 400 tabs open for reasons nobody can fully explain.

If a tool saves time, people will try it.

This is not a moral failure. It is incentive design.

Most teams reward speed, output, and responsiveness. If someone can use an AI tool to prepare a report in 15 minutes instead of 2 hours, they are not going to first sit and read the vendor’s retention policy like a monk studying ancient scripture.

They will use the tool.

Honestly, I probably would too, if I had not become this annoying.

This is where working close to AI security and governance changed how I see GTM work. It made me more sympathetic to both sides.

I understand why security and governance teams worry. A normal-looking workflow can involve customer data, sales data, employee data, product usage data, internal strategy, source code, credentials, meeting transcripts, and other things that should not travel into random systems.

But I also understand why GTM teams use these tools anyway.

The work can get messy with deadlines looming and the tools are helpful. And a lot of AI risk does not announce itself at the moment of use. It is not like the chatbot flashes a giant red warning saying, “By the way, this might be a compliance problem.”

It just gives you a nice summary.

That is the trap.

Productivity feels immediate. Risk feels abstract.

Until it is not.

## Building automations changed my instincts

The biggest mental shift happened when I started building more AI-assisted workflows and automations myself.

It is one thing to talk about AI governance as a concept. It is another thing to connect tools together and realize how quickly the permission graph gets weird.

An AI tool connected to nothing is mostly a chatbot.

An AI tool connected to Slack, email, CRM, docs, storage, internal tools, analytics, and a browser is a very different thing.

At that point, the question is not just “is the model good?”

The better questions are:

- What can this thing read?

- What can it write?

- Where does the data go?

- Is anything stored?

- Can the vendor use this data for training?

- Who else has access?

- What happens if the prompt is bad?

- What happens if the output is wrong?

- What happens if the tool does exactly what I asked, but I asked for the wrong thing?

A lot of AI risk is not the machine becoming evil. It is the machine being useful in a system where permissions, context, and judgment are already messy.

This is why I now find myself choosing local or self-hosted tools more often when I can.

Again, this is not a grand philosophy. I am not pretending local-first is always practical or that cloud tools are automatically bad. Sometimes the managed cloud product is clearly the better option. Sometimes self-hosting something is just a cute way to create a new weekend problem for yourself.

Earlier, I used to think about convenience first.

Now I think more about control.

If I can run something locally, I know more about where the data is going. If I self-host a tool, I can at least reason about the storage, logs, permissions, and access. It does not magically make everything secure. Obviously not. My laptop is not a sacred temple of perfect operational security.

But it changes the default.

And defaults matter a lot.

Especially with AI, because these tools are hungry for context. The more useful they become, the more we want to connect them to everything.

Slack. Gmail. Calendar. CRM. Docs. Tickets. Code. Dashboards. Calls. Browsers.

Each connection makes the tool more useful.

Each connection also makes the blast radius more interesting. And by interesting, I mean terrifying if you think about it for more than 30 seconds.

## My ML master’s made the hype harder to trust

In parallel with all of this, I was finishing my master’s in data science and machine learning.

That changed my AI bullshit detector too.

Before studying ML more seriously, I could look at benchmarks and product claims and understand them at a decent surface level. Model A scored higher than Model B. This system performs well on some eval. This tool claims to improve productivity by whatever percent. This agent can do some impressive task in a demo.

Cool.

But after spending time with datasets, metrics, model evaluation, probability, optimization, and the general pain of trying to measure things properly, I find these claims harder to accept.

And I do not want to do the lazy contrarian thing where every metric is fake and only vibes are real. That is not serious either.

But a benchmark is not the same thing as your workflow.

A leaderboard score does not tell me what happens when the input is messy, the user is confused, the data is sensitive, the context is incomplete, the output needs judgment, and the system is connected to tools that can actually do things.

That is where real work lives.

The master’s made me more interested in the evaluation setup.

- What was measured?

- What was the dataset?

- What was excluded?

- Was there leakage?

- Does the metric match the thing we actually care about?

- What does failure look like?

- Is the model wrong in a harmless way or a dangerous way?

These questions are not as exciting as “this model beat humans at X.”

But they are better questions.

And once you start asking them, a lot of AI hype starts feeling too smooth.

The benchmark claims. The “LLMs will take every job” claims. The “AI agents will make everyone rich” claims.

I am not saying all of it is fake.

I am saying I trust it less quickly now.

Which is probably healthier.

## Job replacement claims feel..well..you know how they feel

The “AI will take all jobs” conversation feels very different when you spend more time around actual workflows.

I am not saying AI will not change jobs. That would be a ridiculous thing to say. It already is changing work. I use it constantly. I would be lying if I pretended otherwise.

But the clean replacement story feels lazy to me now.

A lot of real work is not one isolated task.

It is context, judgment, permissions, incentives, weird internal systems, customer nuance, follow-up, accountability, and knowing when an output is wrong even though it sounds confident.

It is also knowing what should not be automated.

A demo can make a workflow look simple because demos remove the inconvenient parts. No CRM history. No compliance concern. No unclear ownership. No political context. No customer who said one thing on the call and meant something else. No dashboard field that everyone uses differently. No Slack thread where the actual decision happened 47 replies deep.

Real work has all of that.

So when someone says an AI agent will replace an entire role because it can perform a few tasks inside that role, I now get suspicious.

Maybe it will replace parts of the work.

Maybe it will compress some workflows.

Maybe it will make one person much more productive.

Maybe it will also create new review work, new governance work, new integration work, new failure modes, and new ways for people to confidently ship nonsense faster.

All of these can be true at the same time.

That is what the extreme takes usually miss.

AI is useful enough that ignoring it is stupid.

AI is messy enough that blindly trusting it is also stupid.

Very annoying middle position. Unfortunately, it keeps being true.

## The change is in my judgement not my job title

I do not want this article to sound like a career transition essay.

I still work in marketing. I still work in GTM. I am just much closer to engineering, automation, data, and technical workflows than I used to be.

That has made my GTM work sharper.

I understand the product better. I understand customer anxiety better. I understand why security teams care about things that can sound slow or annoying from the outside. I understand why users bypass policies when the approved workflow is painful. I understand why AI governance is not just a policy problem, and not just a technical problem either.

It sits in the middle.

People want speed.

Companies want control.

AI tools want context.

Security teams want visibility.

Legal teams want compliance.

Leadership wants adoption without a future incident that becomes a very tense meeting.

And users just want the report done before the day ends.

That is the actual shape of the problem.

After one year in AI security and governance, I do not think the most useful question is “is AI good or bad?”

That question is too big and somehow also not useful enough.

The better questions are smaller.

Where is AI being used?

What data is going into it?

What can it access?

Who approved it?

Can we prove what happened?

Is the tool actually helping, or did the demo just look good?

What happens when it fails?

Can I run this locally?

See. Annoying.

But I think this is where my thinking has changed the most.

A year ago, I mostly asked, “Can this help me do the work faster?”

Now I still ask that.

But usually a few seconds later:

“What did I just give it access to?”
