---
title: "My Machine Learning master’s degree made AI feel less magical, and the hype harder to trust"
date: 2026-06-17
tags: ["machine learning", "AI", "data science"]
categories: ["Machine Learning", "Learning"]
draft: false
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
description: "After finishing my data science and machine learning master’s, I feel more confident with AI, but also less willing to accept the vague hype still flowing around."
---

I finished my data science and machine learning master’s a week ago. That sentence feels strange to write because its been a crazy 2 years. Classes, assignments, tests on the weekends and full on work and family life through the week. It feels great to have my weekends back after 2 years.

I should probably have a cleaner feeling about it. Relief, pride, maybe a very professional LinkedIn post with a certificate photo and a stupid caption about growth. Maybe I will do just that after finishing this article. Anyways, I do feel proud, obviously. It was a lot of work. Doing a master’s while working full time is not exactly what I would call a chill hobby.

But the main feeling is a bit weirder than that.

I feel more confident with AI now. More confident with tech in general, actually. I understand more of what is going on under the hood, and I feel less intimidated by systems I do not fully understand yet.

At the same time, I trust AI hype way less than I did before. Maybe some of this also comes from me working in AI Security & Governance and seeing the cluster "you know" of whatever is happening with AI and LLMs in particular across the world.

The degree did not make me anti-AI but made me less patient with stupid and vague AI claims. There is a difference.

## Before the math, AI was easier to mythologize (is this a real word?)

AI is very easy to talk about at the surface. Intelligence. Reasoning. Agents. Autonomy. Disruption. All the usual youtuber, linkedin creator words.

Okay, I agree some of these words are useful. Some are abused so badly that they almost stop meaning anything. The problem is that when you do not understand the mechanism, the empty space gets filled with vibes. See what I did there? "Vibes, as in vibe coding...as in when you don't understand what is going on"

Okay! I need to stop explaining my jokes.

Anyways, a demo looks impressive, so the system must be intelligent. A chatbot gives a confident answer, so it must know what it is saying. A model performs well on some benchmark, so the product must be reliable.

I am not saying I believed all of this blindly. But before going deeper into ML, it was easier to stay at that layer. You can talk about AI products, use cases, workflows, productivity, risk, governance, all of that, without really touching what is happening underneath.

The master’s kept dragging me below that layer.

Sometimes willingly. Sometimes very unwillingly. Definitely on the weekend 9AM classes!

## Doing the operations by hand changes something

One of the hardest modules for me was Math for AI. It was also probably one of the most useful.

There is something genuinely insane about calculating tiny parts of AI systems by hand. Multiplying matrices, working through gradients, following transformations, calculating probabilities like its 10,000 BC and trying to understand how an error turns into an update.

Then you see that real systems do this at a scale that makes your notebook look like a crayon drawing of a 1 year old.

In the moment, it can feel stupidly slow. Like, why am I doing this by hand when libraries exist? Why am I spending this much time on operations that NumPy can do before I finish blinking?

But the slowness is the point.

When you calculate it yourself, the abstraction gets taken away a little. Not fully. I am not pretending one math module makes modern AI transparent. But something does fundamentally change in your mind.

A model stops being one blob called "AI" and starts getting turned into different pieces fit together with potato glue.

Vectors. Matrices. Parameters. Loss. Gradients. Optimization. Probability. Approximation. Error.

The words are not just words anymore. You have suffered through them a bit. That matters.

Matrix operations made it easier for me to understand how messy real world inputs become numerical structure. Gradients made the idea of machine learning feel less mystical. Probability tells me that a model output is not the whole truth, even if the UI makes it look clean and authoritative.

I think this is one of those boring forms of confidence that only comes after hours of slogging. And I wouldn't have gotten that without doing all of this stuff by hand.

## Confidence came from seeing the knobs

This is probably the biggest change for me. I do realize that this heading feels so AI written. But go with me here for a second please.

I feel more confident playing around with AI systems now. I do not think I have mastered them. I definitely have not. But I have a better sense of where to poke.

When something behaves the way it shouldn't, I do not immediately file it under "AI is weird."

I can ask better questions now.

Is this a data issue? Is the metric the truth or just truthy? Is the model overfitting? Is the prompt hiding the actual problem? Is the evaluation setup too convenient? Is the system failing because the input distribution changed? Am I treating a probability as if it is a fact?

None of these questions are magical. They are basic, almost annoying if oyu ask me. But that is exactly why they are useful.

A lot of AI work becomes less confusing when you stop asking whether the system is smart and start asking what happened to the data, the objective, the evaluation, and the assumptions.

This has made me more willing to experiment too.

Earlier, experimenting with models or AI tools could sometimes feel like poking a black box and hoping something interesting happened. Now it feels more like working with a machine whose inner working I partially know about.

## The AI hype gets harder to trust

The more I learned, the less patience I had for claims that treat AI like a magic capability blob.

"AI can do X" is not enough.

Under what conditions? On what data? With what evaluation? Compared to what baseline? What happens when the input is messy? What happens when the user is adversarial? What happens when the model is uncertain but the interface still sounds confident?

It is not that the technology is unimpressive. A lot of it is ridiculously impressive. If anything, studying ML made me respect the field more because I have a better sense of how much work gets done behind a clean interface.

But the same understanding makes vague claims harder to accept.

When someone says a model is accurate, I want to know what accuracy means in that context. When someone says an AI system is safe, I want to know safe against what. When someone says an agent can automate a workflow, I want to know what happens when it sees something unexpected, sensitive, malicious, or just badly formatted.

This is not cynicism. At least I do not think it is.

It is just harder to be casually impressed once you have spent enough time with assumptions, metrics, messy datasets, and failure modes.

## This matters more in governance than I expected

I am not picking up a core data science career right now.

That used to make me wonder, at least a little, if I was moving away from the obvious path. You do a data science and machine learning degree, so the clean narrative is that you become a data scientist or ML engineer.

My work is closer to AI security and governance and as a GTM engineer as of now.

But honestly, that is exactly where the degree helps.

A lot of governance language sounds clean until it touches an actual system. Risk. Safety. Robustness. Fairness. Explainability. Controls. Monitoring. Audits.

All good words. And necessary.

Also very easy to turn into checkbox dance if nobody understands what the system is doing.

Technical intuition changes the conversation. It helps you ask whether a control means anything. It helps you separate a real mitigation from a nice sentence in a policy document. It helps you question vendor claims without sounding like you are objecting for the sake of objecting.

This matters a lot in AI security too.

If a model can leak sensitive data, be manipulated through prompts, produce unsafe outputs, or behave differently under distribution shift, those are not just abstract governance concerns. They are technical problems with business consequences.

The math does not solve those problems by itself. But it gives me a better nose for them.

And in my daily job, that is useful. I can ask sharper questions. I can spot when a claim is too clean.

That last one might be the most useful skill of all.

## The value may show up sideways

I used to think the value of an ML degree would be very direct.

You study ML, then you do ML work. Clean pipeline. Nice and simple.

Real life is messier. And no I will not explain this joke like earlier.

The degree gave me technical depth, but its value is showing up in places I did not fully expect. It shows up when I read about a new AI system and do not immediately get hyped up by the demo. It shows up when I am thinking about risk. It shows up when I am trying to understand whether a metric is meaningful.

It also shows up in how I learn.

Going deeper into the math made me less scared of difficult technical material. That is a big deal for me. If I could survive hand calculating parts of AI systems, I can probably survive a dense systems book, a weird paper.

I am exaggerating slightly, but only slightly.

If someone is starting a similar degree now, I would probably tell them this: do not stay only at the API layer. Learn the math enough to remove some of the magic. Build enough things so the math has somewhere to live. And do not judge the value of the degree only by whether your job title says data scientist at the end.

The knowledge can be useful in a sideways way.

Sometimes that is the best kind.

## Less magical, more useful

So that is where I am a week after finishing.

More confident with AI, but less trusting of vague AI claims.

More impressed by the engineering and math behind the systems, but more annoyed when people talk about them like magic objects.

More willing to experiment, but less willing to accept a clean demo as proof of anything serious.

I think that is a good trade.

The degree made AI feel less magical to me. That sounds like it should make the field less exciting, but it has had the opposite effect. It feels more usable now. More like something I can question, test, break, understand a little better, and then use with better judgment.

I do not want to be the person who believes every impressive demo.

I also do not want to become the person who dismisses useful technology just because the hype around it is annoying.

Somewhere between those two is probably a healthier place to be.

For now, I think the biggest win from the degree is simple: I know how to ask better questions.

That feels like a decent place to start.
