---
title: "ARIMA Is Boring, and That Is Why I Still Like It"
date: 2026-07-11
tags: ["ARIMA", "time series", "forecasting", "machine learning", "business analytics"]
categories: ["Machine Learning", "Time Series", "Data Science"]
draft: false
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
description: "ARIMA is old, limited, and a little annoying. I still like it because it makes the assumptions and uncertainty in a forecast harder to ignore."
---

I have been spending a lot of time around AI agents lately.

Agents that can read files, call tools, update things, research things, write things, and generally make you feel like the computer might be about to become a coworker. Which is exciting. Also slightly stressful if you think about what it has access to for more than 30 seconds.

Then there is ARIMA.

ARIMA looks like it was named by someone who wanted to make sure nobody accidentally found statistics too exciting. It does not have a chat interface, cannot browse the web and definitely cannot write a follow-up email with “just circling back” in it. It looks at a sequence of numbers and asks some basic questions.

- What happened before?

- Is there a trend here?

- Do the values repeat in a pattern?

- How much of this is just noise?

Very boring questions, I guess but I still like them.

I wrote about [ARIMA and SARIMA before](/posts/why-time-series-deserves-comeback-forecasting-with-arima-sarima/), mostly from the perspective of why these models still matter for forecasting. This is a slightly different thing. The more time I spend around AI, automation, and people making crazy claims from nice looking charts, the more I appreciate a model that makes its limitations visible.

I believe ARIMA is boring in a useful way.

## The model makes you look at the data first

When I was doing time series work during my master’s, I initially treated ARIMA like a model selection problem.

Pick some values for `(p, d, q)`, run it, compare RMSE and then try another combo. Let `auto_arima` do some searching, look at the forecast plot and of course feel smart for a few minutes.

That is probably a normal way to begin.

But it can also be a bit silly because those three letters are making claims about the data whether you understand them or not.

The autoregressive part says the past may help explain the present. The integrated part says the raw series needs differencing before it behaves in a stable way. The moving average part says past errors can still tell us something about the current value.

You cannot really use ARIMA for long without asking whether those claims make sense.

If sales keep growing because the company is expanding, raw sales numbers might keep moving upward. If you difference the series, you are looking at the change from one period to the next instead. That can make the pattern easier to model, but it also changes the question you are asking.

If your monthly revenue jumps every December, standard ARIMA will not magically understand that Christmas exists. You probably need a seasonal model, which is where SARIMA helps us out. If a pricing change, a product launch, a pandemic, or a competitor doing something weird moved the line, the historical pattern may not be enough anyway.

This is what I mean by boring. The model keeps dragging you back to the actual shape of the data.

Sometimes that is annoying because you want to train a model and move on. I get it. But it is better than treating every chart as an opportunity to summon a magical spell.

## The forecast line is the least interesting part

A forecast chart can look very convincing.

You have the historical line, a future line in a different color, add a confidence interval around it and the dashboard suddenly has authority to teach billion dollar CEOs.

I am making fun of this, but I have absolutely been impressed by my own forecast charts before. A line extending into the future just does something to the brain.

The issue is that the future line is usually the easy part to look at.

The better questions are more irritating.

- Did the model get tested on a period that actually resembles the future decision?
- How wide is the prediction interval?
- Did it miss a seasonal pattern that everyone in the business already knows about?
- Are the errors behaving in a strange way?
- What happens when an external event disrupts the pattern?

A model can have a decent RMSE and still be unhelpful for the thing someone needs to decide. This is part of why I think [business ML should start with the decision](/posts/primer-to-framing-business-problems-for-machine-learning/), instead of treating a decent metric as the finish line. A monthly forecast might look fine on average while being completely wrong during the one month when inventory planning matters. A dashboard can say “forecast is up 8%” while the range around that number is large enough to make the decision obvious only if you look at it properly.

This is why I have become slightly suspicious of clean forecast plots. They are not useless. They just make it easy to stop asking questions too early.

ARIMA does not prevent that mistake. But it gives you more places to notice it.

You see the residuals, differencing, seasonal order, confidence intervals. You see, at least a little more clearly, that a forecast is an estimate built from a particular view of the past.

## Boring models make uncertainty harder to hide

I think the thing I like most about classical time series models is that uncertainty is right there in the output.

You can ignore it, obviously. People ignore things all the time when the main number looks good enough for the slide.

But the interval is sitting next to the forecast, can't ignore that, can we?

If the model says next month’s demand will be 1,000 units, that sounds great. If it says the plausible range is 700 to 1,300, the conversation that you have with your team is going to be a bit different. Maybe the business can tolerate that. Maybe it cannot. Maybe the right move is a smaller inventory bet. Maybe somebody needs to look at context the time series will never know about.

That is a much better conversation than pretending the model gave us the future.

This is also why I do not think forecasting is really prediction. I think its more like planning with an estimate, a range, and some assumptions you should probably write down.

Very glamorous and chic.

## ARIMA has plenty of ways to disappoint you

I do not want to turn this into a “classical models good, AI bad” thing. That would be boring in the bad way.

ARIMA can be a terrible fit.

It can struggle when the data is highly nonlinear. It cannot see a future product launch because it did not happen in the history. It can get confused by structural breaks. It can look better than it is if you validate it badly. It can also make you spend more time than expected wondering if you should difference the series one more time, which is not how I personally want to spend every evening.

There are cases where gradient boosted trees, Prophet, neural networks, or a model with external variables will make more sense. There are cases where the right answer is not a better model but better data, or a human who knows why the sales team changed the process two weeks ago.

The point is not that ARIMA wins every model comparison.

The point is that it makes the comparison more honest.

You have to look at the series, define the horizon and decide what “good” means. You have to check whether the errors are acceptable for the business decision. Those are useful habits even if you eventually use something much fancier.

## I like the model because it does not feel magical

Working around AI security and governance has made me care more about the boring parts of systems.

Permissions. Boundaries. Logs. Inputs. Evaluation setup. All that at times seems secondary until the system is connected to real data and starts doing things you have to explain later.

ARIMA gives me a similar feeling, just with forecasting.

The interesting part is not that it produces a number. Plenty of systems can produce a number. The interesting part is whether I understand where that number came from, what it assumes about the past, how wrong it has been, and what I should do when the range is wider than I hoped.

I think that is why I still like it.

It is old. It is limited. It has a deeply unsexy name. It forces you to think about trend, seasonality, error, and uncertainty when you would maybe rather just ask a bigger model to figure it out.

And honestly, that feels like a pretty good deal.

A boring model will not make forecasting feel magical.
i
It might make you a little less likely to believe magic when you see it.
