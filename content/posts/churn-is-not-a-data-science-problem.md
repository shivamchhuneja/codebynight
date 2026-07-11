---
title: "Churn Is Not a Data Science Problem"
date: 2026-06-21
tags: ["Churn", "Customer Retention", "Data Science", "Machine Learning"]
categories: ["Machine Learning", "GTM Engineering"]
draft: false
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
description: "Churn prediction looks like a clean data science problem, but useful retention work needs systems, ownership, context, and feedback loops."
---

My old churn analysis capstone post has somehow become one of the most popular posts on this blog over the last year.

I did not expect that.

At the time, churn looked like a neat data science problem to me. You get a dataset, clean it, engineer some features, train a model, check the metrics, maybe explain feature importance, and then recommend a few retention ideas. It is a good project shape. Business problem, dataset, model, metric, interpretation. Very neat, if I may call it that. Very portfolio-friendly.

I still think that kind of project is useful. I am not going to diss on my past self just because I now have slightly better words for the problem. That would be annoying.

But I do think my framing was incomplete.

Churn is not really a data science problem. Or at least, not only just a data science problem.

It is an operating problem that sometimes needs data science.

## Churn prediction feels like success

The tempting thing about churn prediction is that it feels obviously useful.

If a business knows which customers are likely to leave, it can save them. Right?

Well, kind of.

A churn model can tell you that an account looks risky. It can show which variables move along with churn. It can rank customers by probability. It can give you a dashboard with red, yellow, and green labels, and suddenly everyone feels like the company has become more serious about retention.

But then someone asks the next question.

Now what?

Who sees the signal? Sales? Customer success? Product? Support? The founder? Some tableau dashboard that nobody opens after the first week?

What action do they take? Send an email? Schedule a call? Offer a discount? Fix onboarding? Escalate a bug? Do nothing because the account is too small?

When do they act? Immediately? After two bad weeks? Before renewal? After the customer has already emotionally left but is still technically paying?

And how do we know whether the action helped?

This is where this churn work starts getting awkward. The model is treated like the finished thing, when it is usually just one piece of a much larger retention workflow.

A churn score without someone responsible for acting on it is as useless as the tiny pocket inside the big pocket in your jeans.

![A churn score is not a retention system](/images/blog/churn-score-is-not-retention-system.svg)

## Customers are not rows

The other thing I understand better now is that churn is usually a story before it becomes a label.

In a dataset, the customer is a row. There is tenure, spend, complaint count, login frequency, payment method, maybe some product usage events. Then there is a target column: churned or not churned.

That structure is useful because models need structure. But it hides the main thing.

A customer may churn because onboarding was weak. Or because sales promised something the product did not really do. Or because the product solved a problem, but not a painful enough problem. Or because the champion left the company. Or because support was slow at exactly the wrong moment. Or because the buyer and the actual user were two different people living in two different realities.

None of this fits cleanly into a CSV.

You may see clues. Low usage after signup. No teammates invited. No integration connected. Too many support tickets. No return session after the first week. A renewal date coming up with no real engagement.

But the clue is not the story.

I am stressing on this because if you only think in rows, churn becomes a classification exercise. The customer becomes a probability. The business problem becomes a metric. The useful question, which is "what would actually help this customer succeed?", gets pushed.

And by then it is often too late.

## The better question is earlier

If I were thinking about churn today, I would not start with "who is going to churn?"

I would start with something earlier and more irritating:

What does a healthy customer look like before everyone agrees they are healthy?

That question will change how we approach the "hey, we need a churn prediction model because retention is cheaper than acquisition" statement.

Instead of waiting for late churn signals, you start looking for early success signals. Did the customer reach the first useful moment? Did they repeat the workflow? Did they invite other users? Did they connect the integration that makes the product harder to remove? Did they move from curiosity to habit?

This is where my current GTM engineering brain gets more interested than my old data science student brain.

The useful work should beyond modeling churn. It would mean building the pipes around retention:

- product events that capture actual usage instead of vanity metrics
- CRM fields that show lifecycle stage and customer context
- health scores that combine usage, support, commercial, and onboarding signals
- alerts that go to the right person instead of rotting in a dashboard
- playbooks that say what action to take
- feedback loops that track whether the action worked

Some of this can use machine learning. Some of it can be simple rules. Some of it is just getting the data model and ownership right.

Honestly, a boring rule-based setup with clear ownership might beat a fancy churn model that nobody acts on.


## From churn model to retention workflow

A useful retention workflow has more moving parts than a model.

It needs signals from product usage, support, CRM, billing, and sometimes plain human notes. It needs some way to decide whether those signals mean "healthy", "needs attention", or "something is off here." It needs routing, because "this account is at risk" is not useful unless someone owns the next step. It needs actual interventions, because prediction without action is just business astrology with nicer charts.

And then it needs measurement.

Did the customer come back? Did they activate? Did the support issue get resolved? Did the expansion conversation happen? Did the intervention reduce risk or just create more noise for the team?

The feedback loop is the part I did not appreciate enough earlier.

In project mode, evaluation usually means model metrics. Accuracy, recall, precision, ROC-AUC, F1, whatever makes sense for the dataset. These matter. Especially with churn, where class imbalance can make accuracy look way better than it deserves to look.

But in business mode, evaluation also means boring operational questions.

Did the alert reach the right person? Did they trust it? Did they act? Was the action useful? Did anything about the customer change after that? Did the team learn anything when the system was wrong?

Churn systems can be wrong in expensive ways. They can waste customer success time. They can annoy healthy customers. They can miss quiet accounts that are on their way to churn. They can overreact to loud signals like complaints and miss silence, which is sometimes the scarier signal.

The model is not the system. The system is what people and tools do around the model.

![A retention system needs ownership and feedback](/images/blog/retention-system-loop.svg)

## This is also why AI systems make me more suspicious now

I think working around AI security and governance has made me more sensitive to this pattern.

A lot of bad AI and data work treats prediction as the finished product. The system produces a score, label, summary, recommendation, or risk rating, and everyone pretends the hard part is done.

But the hard part usually starts after the output.

Who is responsible for it? What context is missing? What happens when the system is wrong? Can a human override it? Is anyone checking what happened after the action was taken? Does the team understand the assumptions, or are they just trusting a clean-looking number because it came from a model?

Churn is a nice example because the business problem is easy to understand. Customers leaving is bad. Keeping good customers is good. No need to make this sound deeper than it is.

But the simplicity is also a trap. It makes you think the goal is to predict churn, when the real goal is to help the right customers succeed early enough that churn becomes less likely in the first place.

That is a very different problem.

## What I believe now

I still think churn analysis is a good data science project. Maybe that is why people keep finding my old post. It has clean ingredients and teaches useful things: exploratory analysis, feature engineering, class imbalance, model evaluation, segmentation, and business interpretation.

I would still recommend it to someone learning data science.

I would just add a warning label now.

Do not confuse the project shape with the real problem.

If I were approaching churn today, I would spend less time asking which algorithm predicts churn best and more time asking:

- What does success look like for this customer?
- What signals tell us they are drifting away?
- Who sees those signals?
- What action do they take?
- How do we know if that action helped?

The model can still matter. I am not saying otherwise.

But churn is not solved when a notebook prints a score. It is not solved when a dashboard goes live. It is not solved when the CMO under the pressure of CEO says "we should do proactive retention" in a meeting and everyone nods like that sentence means anything by itself.

It becomes useful when the business can notice risk, understand what is happening, act at the right time, and learn from the result.

That is the part I did not understand properly one year ago. Well, I technically did since I've been working in marketing but because I had been in a student's project mindeset I did not weight these parts properly.

Churn is not a data science problem. It is a retention workflow problem disguised as a prediction problem.
