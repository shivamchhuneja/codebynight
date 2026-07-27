---
title: "2 Years of Data Science and Machine Learning Made Me Trust These 7 Things Less"
date: 2026-06-17
tags: ["data science", "machine learning", "AI", "career", "learning"]
categories: ["Machine Learning", "Learning"]
draft: true
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
description: "After two years of studying data science and machine learning, I trust clean datasets, metrics, dashboards, model outputs, and AI explanations a lot less blindly than I used to."
---

I wrote a 22 lessons post after my first year of studying data science and machine learning.

At that point I was still working in product marketing at a dev productivity analytics SaaS company. A lot of my learning then felt like trying to become more technical without completely losing my mind.

I was learning Python, pandas, feature engineering, model evaluation, MLOps, math, research papers, and the general horror show of trying to make a notebook behave after midnight.

That first year was about effort. I was trying to prove to myself that I could actually do this stuff.

Now the second year is over. The degree is done. I work in GTM engineering at an AI security and governance startup. My day to day life is closer to systems, workflows, messy GTM data, automation, AI risk, and the strange gap between what a tool says and what a team actually does with it.

So I do not want to write another "22 more lessons" post.

That would be too clean. Also slightly exhausting. For you and for me.

The second year changed something else.

It changed what I trust.

Not in a dramatic "I trust nothing now" way. I am not becoming a data science doomer. But two years of studying data science and machine learning has made me much slower to believe clean outputs, clean dashboards, clean metrics, and clean AI explanations.

Weirdly, that has made me more confident.

I trust fewer things blindly, but I trust my questions more.

## 1. I trust clean datasets less

In my first year, one of my big lessons was that data cleaning is most of the work.

That still feels true.

But now I think there is a slightly more annoying lesson hiding behind it: clean data is not automatically good data.

A dataset can have no missing values, consistent formatting, correct types, beautiful column names, and still be quietly misleading.

That took me a while to properly understand.

When you are new, dirty data is obvious. Missing values, broken dates, weird strings, duplicate rows, random columns that look like someone named them while fighting for their life. You know something is wrong because the dataset looks messy.

Clean data is scarier because it looks official.

The CSV loads properly. The dashboard works. The chart renders. The CRM field has a value. The event exists in the product analytics tool. The number has two decimal places, so obviously it must be serious.

The useful questions are somewhere else.

How was this data created? Who entered it? Was the field required or optional? Did two teams use the same field in different ways? Did the product event fire when the user did the thing, or when the frontend thought the user did the thing? What got filtered before this reached me?

A dataset can be clean and still be lying by omission.

That is a much more useful fear than "oh no, null values."

## 2. I trust metrics less

Accuracy was the first metric that betrayed me.

I think this happens to almost everyone who learns machine learning. You train a model, get a high accuracy score, feel good for six seconds, and then realize the dataset is imbalanced and your model has learned to predict the majority class like a lazy genius.

Year one Shivam learned: accuracy is not enough.

Year two Shivam learned: even the better metric can still be the wrong shortcut.

Precision, recall, F1, ROC-AUC, PR-AUC, log loss, conversion rate, pipeline generated, activation rate, retention rate. Metrics are useful. I am not saying we should stare at vibes and make decisions like cavemen with SaaS subscriptions.

But a metric is not the truth. It is a shortcut someone agreed to use.

Sometimes that shortcut is good. Sometimes it is convenient. Sometimes it quietly changes the behavior of the team using it.

If you optimize for leads, you might get more leads and worse customers. If you optimize for model accuracy, you might ignore the cost of being wrong. If you optimize for dashboard activity, people might do more things that look measurable and fewer things that actually matter.

This is where my current work has changed my thinking. In GTM engineering, metrics are not only numbers you report. They shape workflows. They decide which accounts get attention, which campaigns look successful, which reps get nudged, which automations fire, and which problems stay invisible.

So now when I see a metric, I trust it less quickly.

I ask what it rewards.

I ask what it hides.

I ask who changes behavior because this number exists.

Very annoying questions. Unfortunately useful.

## 3. I trust model outputs less

I still like models.

I should say that clearly before this starts sounding like I spent two years studying machine learning only to conclude that machine learning is bad. That would be a very expensive and roundabout way to become annoying.

Models are useful. Sometimes extremely useful.

I just trust their outputs less casually now.

A prediction is not a fact. A confidence score is not a guarantee. A clean probability is not the same as certainty. A model saying "high risk" does not mean the world has agreed with it.

This sounds obvious when written out, but it is very easy to forget when the output looks polished.

A churn model gives a risk score. A classifier gives a label. An LLM gives a fluent explanation. A forecasting model gives a line that confidently walks into the future like it owns the place.

The UI makes it feel more certain than it is.

Studying ML made me more aware of the machinery underneath. Training data, assumptions, objective functions, thresholds, distributions, evaluation sets, random splits, leakage, drift. All the boring words that make the magic leak out.

I do not mean that in a negative way.

It is better when the magic leaks out.

Because then you stop asking "is the model smart?" and start asking better questions.

What data did it learn from? What is it optimizing for? Where does it fail? What does this score actually mean? What happens if someone acts on it and it is wrong?

That last question matters more to me now than it did in year one.

## 4. I trust dashboards less

This one comes directly from moving closer to GTM engineering.

Dashboards are funny. They can make a messy business process look like it has its life together.

There is a chart. There is a trend line. There are filters. Maybe a nice little date picker. Everyone relaxes because now the mess has a UI.

But dashboards inherit every weird thing that happened before the number reached the chart.

CRM fields filled inconsistently. Lifecycle stages that mean different things to different teams. Product events that changed names halfway through the quarter. Lead sources that got overwritten. Account ownership that changed but the reporting logic did not. Manual notes sitting in someone's head because no one entered them anywhere.

Then a dashboard politely turns all of that into a clean number.

I used to think the hard part was building the dashboard.

Now I think the hard part is deciding whether the dashboard deserves trust.

Does the team agree on what the fields mean? Does anyone check the source data? Is the chart answering a real question or just decorating a meeting? If the number changes, does anyone know what action to take?

A dashboard without ownership is basically wall art with filters.

Okay, maybe that is too harsh.

Actually no, I stand by it.

## 5. I trust AI explanations less

This is probably the biggest shift because of where I work now.

AI explanations are dangerous because they sound like explanations even when they are just fluent guesses.

That sentence feels obvious in 2026, but it still catches people. It catches me too if I am tired enough.

LLMs are very good at making uncertainty sound organized. They can take a messy input and produce a clean paragraph with headings, reasons, tradeoffs, and a conclusion. It feels like thinking because it has the shape of thinking.

But shape is not the same thing as substance.

This is where studying machine learning helped, but working around AI security and governance made the lesson sharper.

An explanation needs to be checked against something outside itself.

Can we trace it back to evidence? Does the system know where the information came from? Is it reasoning from the right context or filling gaps with plausible nonsense? Can a human challenge it? Is there a log? Is there a fallback when the system is wrong?

I do not trust an AI explanation because it sounds reasonable.

I trust it more when I can inspect what it used, what it ignored, and what would happen if it is wrong.

That is less exciting than a magical AI demo.

Good.

## 6. I trust isolated models less than workflows

In my first year, the model felt like the main character.

That makes sense. Most learning projects are structured that way. You clean the data, train models, compare metrics, pick the best one, and write the conclusion.

In real work, the model is rarely the full story.

The useful thing is usually the workflow around it.

Who sends the data? Who checks it? Who receives the prediction? What action do they take? What happens when the model is wrong? Does anyone review edge cases? Does the system learn from the outcome? Does the team trust it enough to use it, but not so much that they stop thinking?

That is where I now place more trust.

Not in isolated cleverness.

In boring loops that have inputs, owners, logs, review, and feedback.

This is true for GTM systems. It is true for retention. It is true for AI governance. It is true for internal automations that look small until they quietly start influencing real decisions.

A model in a notebook can be impressive.

A workflow that survives contact with a real team is more impressive.

And much rarer.

## 7. I trust my first interpretation less

This might be the most personal one.

Two years of data science made me less trusting of my first answer.

Not because my first answer is always wrong. Sometimes it is fine. Sometimes it is even useful.

But I am more aware now of how quickly I can create a story around a number.

This metric dropped because users disliked the feature. This model performed better because the algorithm is stronger. This segment churned because pricing was wrong. This AI output is correct because it sounds confident. This dashboard proves the campaign worked.

Maybe.

Or maybe the tracking changed. Maybe the dataset leaked. Maybe the evaluation split was too friendly. Maybe the segment is too small. Maybe the feature is a proxy for something else. Maybe the campaign got credit because attribution is held together with vibes and duct tape.

The more I learn, the more I pause.

I do not think that pause is hesitation. I think it is the beginning of actual judgment.

Earlier, confidence meant having an answer quickly.

Now, confidence feels more like knowing where to poke before believing the answer.

## So what do I trust more now?

This article is about things I trust less, but the point is not cynicism.

I do trust some things more now.

I trust careful problem framing more. I trust boring data checks more. I trust clear ownership more. I trust evaluation that tries to break the system a little. I trust simple models with honest limits more than complicated models with theatrical confidence.

I trust math more, but not because math makes everything objective.

I trust math because it forces me to look at assumptions.

Probability tells me not to confuse a score with truth. Metrics force me to ask what error costs. Distributions remind me that averages hide weirdness. Evaluation teaches me that a model can look good in the lab and become stupid in the real world.

That is not cynicism.

I think it is a better kind of optimism.

The first year of data science made me believe I could learn the tools.

The second year made me less impressed by the tools.

I am more confident now, but less easily convinced. A model output does not feel like magic. A dashboard does not feel like truth. An AI explanation does not feel correct just because it is written in clean English.

And honestly, that might be the most useful thing I got from these two years.

Not that I trust AI more.

I trust my questions more.
