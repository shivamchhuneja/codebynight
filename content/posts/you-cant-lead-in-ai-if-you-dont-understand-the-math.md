---
title: You Can’t Lead in AI If You Don’t Understand the Math
date: 2025-10-22
draft: false
toc: true
tocOpen: false
showPostNavLinks: true
description: The more abstracted AI becomes, the more valuable it is to understand what’s behind the abstraction. A personal note on why I’m going back to the math behind machine learning.
tags: ["machine learning", "math", "AI engineering", "data science"]
categories: ["Data Science", "AI Engineering", "Mathematics"]
---

## Why I’m Picking Up the Math Now

I come from product & growth marketing and I'm doing my masters in Data Science and Machine Learning. Most of my work has been about making technical products understandable. Shaping go-to-market plans, writing positioning for AI features, and working across teams to make sure what we build actually makes sense to the people we’re building it for.

I’m also on a path to becoming a full-stack machine learning engineer. That means going beyond talking about models. I want to build them. Understand them. Debug them. Know when they’re lying.

So I’ve been slowly going back to the math behind machine learning, and I'm using pencil and paper.

Right now I’m working through:

- *An Introduction to Statistical Learning with Python*  
- *The Elements of Statistical Learning*  
- *Practical Statistics for Data Scientists*  
- *Statistical Inference* by Casella and Berger  
- Books by David Spiegelhalter on probability and risk

Most nights it’s a couple pages, and then on the weekends the goal is to go through a chapter. Sometimes I try to rework a proof. Other times I just sit with a concept until it clicks.

![Intro to Statistical Learning](/images/blog/intro_to_statistical_learning.jpeg)

This all started a few months ago. I was reviewing a machine learning pipeline for a core project I was working on in my coursework for the masters.

Something felt off. We looked closer and found a classic problem: the test set wasn’t independent. Some data leakage had slipped through. A simple mistake, but it went unnoticed because everyone trusted the dashboard.

I'm not sure it connects with the math directly but I simply realized something then: I don’t want to just look at a number and assume it’s right. I want to know how it was calculated. I want to be able to ask: What assumptions are baked in here? What might we be missing?

## Patterns I Keep Seeing

Once I noticed that example, I started spotting similar issues elsewhere. Misused p-values. Confusing correlation for causation. Overconfident interpretations of model metrics.

The problem for me is abstraction. I've seen most people though are happy with this abstraction. It makes life easier. Tools do a lot for us, and that makes it easy to forget what’s under the hood. But if you’re working around machine learning, even indirectly, you need to understand enough to catch the gaps. Otherwise, you’re just repeating what the model tells you whether it’s right or not.

## What I’m Studying and Why

*ISL with Python* is helping me rebuild intuition especially around linear models, decision trees, and basic inference.  

*ESL* is more in-depth. I’m taking it slow, but it’s already helped me see regularization and overfitting much better.  

*Practical Statistics for Data Scientists* is a quick bridge between acedemia and real-world decisions.  

*Casella and Berger* is dense for me, but helpful when I want to understand things like confidence intervals or hypothesis testing more deeply.  

Spiegelhalter’s books are a good reminder that statistics is about making sense of uncertainty not just running calculations.

None of this is just for theory. This helps me in my reports, how I explain metrics, how I think about risk when I'm explaining an AI security issue for my product marketing work even.

## Why I Think This Isn’t Optional Anymore

You don’t need to be a statistician to work in AI. But if you’re involved in shaping products, guiding strategy, or explaining ML systems to customers, in my opinion the math matters. You need to know when something feels off. You need to be able to ask questions that go beyond the surface.

The more AI gets abstracted, the more valuable it is to understand what’s behind the abstraction. That’s where better decisions get made and that’s how trust is earned from your team, your users, and your leadership.

If you work in product, marketing, or data and AI is part of your world carve out some time for the fundamentals. It won’t feel urgent. But it’ll pay off. In how you speak, in how you think and in the quality of the questions you ask.

*This post is part of my ongoing journey into data science, machine learning, and AI engineering. You can follow along here on Code by Night.*
