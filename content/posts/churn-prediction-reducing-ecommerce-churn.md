---
title: "Churn Prediction Is Easy. Reducing E-Commerce Churn Is Hard."
date: 2026-07-11
tags: ["ecommerce churn", "customer retention", "churn prediction", "ecommerce", "machine learning"]
categories: ["Machine Learning", "GTM Engineering"]
draft: true
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
description: "How to reduce e-commerce churn after building a churn prediction model. A practical look at retention workflows, customer context, discounts, and what happens after the score."
---

I have spent around seven years working in e-commerce in one way or another.

I have worked with brands doing a couple hundred thousand dollars a month. I have helped smaller brands that were barely starting up and just trying to get the foundations right. I have run my own e-commerce stores and I have also worked with high-end fashion brands across five countries.

Most of my work was as a technical marketer building websites, marketing workflows, funnels and helping brands sell more stuff. The work also involved looking at people who bought once and never came back, people who abandoned carts halfway through, campaigns that pulled in customers who had no reason to stay, and the general pain of trying to make a store feel worth returning to.

So churn was never only a data science thing for me.

Then I did a [churn analysis capstone](/posts/churn-analysis-capstone-ecommerce-customer-retention/) during my master’s in data science. I cleaned the data, looked at the mess, built segments, tried a bunch of models, and got a tuned Random Forest that looked pretty damn good on the metrics.

And I was proud of it. I still am.

But I had this slightly unsettled feeling afterwards. I had a model that could flag customers who might churn. Okay, Cool.

Who was going to do something about it? Yes, I know that was the scope of my project but its not the first time I saw asystem setup to do something like this but without making sure that there are going to be people who would actively leverage it properly.

## A churn score gives you a list

I think a churn model makes sense once a store has enough customers that nobody can remember every account. It gives you a list that is hopefully more useful than picking people from a spreadsheet with your eyes closed. It can also point at complaints, short tenure, poor service scores, falling engagement, or whatever else the data has managed to pick up.

This can be useful because the model has narrowed down where somebody should look first.

But a customer score does not tell you why the person is on that list. It does not know whether the first order arrived late, whether the product disappointed them, whether support ignored them, or whether they only needed the product once. It also does not know if they are waiting for the next discount because the brand trained them to do that.

So now a person has to look at the account, see what happened, and decide what should happen next. That could mean support following up, a more relevant offer, a better post-purchase message, or leaving the customer alone.

This is more or less where my feelings about churn prediction changed a bit as well. The model can make the problem look very clean, but the work after the score is still people trying to decide what is useful and what is just another sheet in the company's black hole of a shared google drive.

## A discount does not explain why somebody left

A generic discount is usually the easiest thing to do with an at-risk list. Build the segment send a promotional email and see if some revenue comes back. I understand why it happens because it is fast and somebody can say they did something about churn before the next meeting.

The same discount can be a non-answer to what happened. It does not fix a late delivery or a confusing website or a bad return or a sub-par product or support that made the customer feel like getting help was more work than it was worth.

This is why I find retention discussions a little odd sometimes. People talk about predictive models and personalisation while the first order experience is still making customers leave for very normal reasons. I know a churn model sounds more interesting than fixing a mobile checkout or writing less useless email flows, but those boring things are usually closer to the reason somebody comes back.

Working with smaller brands made this pretty obvious. There is often plenty to fix before anybody needs a complicated model. The offer needs to make sense, the website needs to work properly, customers need to know what happens after ordering and the emails need to feel useful instead of promotional noise.

My capstone had complaints, tenure, cashback dependency, and service score showing up as useful churn signals. I liked seeing that because it gave me something to investigate. At the same time I also think feature-importance charts can make people feel like the answer is clearer than it really is.

A complaint can mean a broken product, an unresolved issue, or one bad interaction that did not matter much. More cashback might get another order from a customer, but it can also make the whole relationship look like a discount loop. The model gives you a clue then somebody still has to work out what the clue means for this customer.

## I would decide what happens next before building more models

I would want to know what the brand can actually do for someone who looks likely to leave. If the only answer is one generic email then a few rules around a bad first order or an unresolved complaint may be enough to get started. A complicated model does not make a generic email feel more personal.

It gets more useful when there are real actions available. Support can review an open issue, someone can follow up with a high-value customer, the first-time buyer flow can be changed, or the brand can try a loyalty benefit that does more than offer another coupon.

Then the model can help decide where limited attention should go. That feels like a better use of churn prediction than treating every customer who crosses a threshold the same way.

The result also needs checking afterwards. If a business sends an offer to 1,000 customers and 200 buy again, that number might look great on a slide. It still does not show how many would have returned anyway, how much margin the business gave away, or whether a different action would have worked better. Statisctical Significance!

A holdout group helps with this. Trying different interventions with similar customers helps too. Even a basic comparison between retained revenue and the cost of discounts, support time, or shipping benefits can stop a team from feeling clever because money came in after an email was sent.

I wrote earlier that [churn is not a data science problem](/posts/churn-is-not-a-data-science-problem/), and I still agree with that. The model can tell you something useful, but it cannot decide what a customer needs or prove that the thing you did afterwards was worth the cost.

## What I care about more today

The capstone taught me a lot about imbalanced data, segmentation, feature importance, model evaluation, and the ways a decent accuracy score can still be bogus. The e-commerce work taught me something closer to real world. A returning customer often comes from ordinary things going right before they ever appear in a churn model.

The website made sense, the product did what it said it would do, the order did not become a problem and the customer had some reason to remember the brand later. None of that sounds like exciting machine learning work but I think it matters more than a lot of retention discussionists want to admit.

Some customers will leave anyway. They may have been a bad fit, they may have wanted one thing once, or they may cost more to retain than they are worth. Trying to save every customer can turn into a very expensive and slightly desperate way to run an e-commerce business.

I still think churn prediction is worth doing when there is enough data and somebody can act on the result. I would just start with a few more annoying questions now. What does a healthy customer look like here, what usually goes wrong before they leave, who can do something about it, and how will we know if it helped?

Once those questions have proper answers, the model has a much better chance of helping instead of becoming another useless score to please the boss.
