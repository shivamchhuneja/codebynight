---
title: "A Primer to Framing Business Problems for Machine Learning"
date: 2025-06-17
description: "Here is how to frame vague business goals into clear machine learning problems using classification, regression, and ranking lenses to make real-world impact."
categories: ["Machine Learning", "Data Science", "Business"]
tags: ["problem framing", "machine learning", "data science", "classification", "regression", "ranking", "real world ML"]
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
draft: false
---

A stakeholder comes to your desk. They're excited. "We need to use AI," they say, "to improve customer retention."

You nod, open your editor, and you start thinking.

Should I use XGBoost? Or maybe a neural network? How will I set up the pipeline?

Stop. Right there.

This is the single biggest mistake many of us make when we're starting out: we jump straight to thinking about solutions and algorithms.

We're so excited to play with the cool, technical thing that we forget to ask the most important question first:

**What problem are we actually trying to solve?**

The most valuable skill for a data scientist isn't knowing every algorithm under the sun.

It's easy, Google has ton of code to help with that, LLMs can help out too. So then what makes a Data Scientist more valuable than the readymade code example anywhere on Google?

Well, it's the ability to translate a vague business goal like "improve retention" into a specific, solvable machine learning problem.

This is called problem framing.

Here is what I'll cover:
* The three main "lenses" for framing almost any ML problem: Classification, Regression, and Ranking.
* Real-world examples and use-case templates for each.
* A practical, 5-step checklist you can use on your next project.

## Why "Framing" is 90% of the Machine Learning Engineering Battle

Let's be clear: getting the framing wrong is a recipe for disaster.

You can spend weeks building a model with 99% accuracy, just to find out that it doesn't actually help anyone make a better decision.

It's a model that's technically correct but practically useless. It answers a question nobody was asking.

Proper framing changes a high-level objective like "increase revenue" into a precise, machine-solvable question like, "What is the predicted purchase value of this specific user in the next 30 days?"

When you get the frame right, you know that the model you build will directly support a business decision.

It provides a clear target for you to aim at and a clear definition of success.

## The Three Core Lenses: Classification, Regression, and Ranking

Think of these as the primary tools in your problem-framing toolkit. Almost every business problem can be viewed through one of these three lenses.

### Classification: Which Category Does This Belong To?

The Core Question: Classification is about predicting a discrete category or a label.

The fundamental question you're asking is: "Is this A or B (or C, or D...)?"

Think of the Sorting Hat from Harry Potter. It takes an input (a new student) and assigns it to a specific, predefined bucket (Gryffindor, Hufflepuff, etc.)

Here are a few examples:

- **Business Problem:** "We're losing too many customers and don't know who to focus our retention efforts on."
- **ML Framing (Binary Classification):** For each active customer, will they churn in the next 30 days? **(Yes/No)**
- **What the Model Outputs:** A probability (e.g., 85% chance of churn) and a final class label ("Yes").

Here are 3 more:

- **Spam Detection:** Is this email spam or not spam?
- **Medical Diagnosis:** Does this medical image show a malignant tumor or a benign one?
- **Lead Scoring:** Based on user actions, is this new sales lead "hot" or "cold"?

For problems like these, you might use algorithms like Logistic Regression, Decision Trees, or Support Vector Machines.

You'd measure success with metrics like Accuracy, Precision, Recall, and F1-Score.

---

### Regression: How Much or How Many?

The Core Question: Regression is all about predicting a continuous numerical value. The question you're asking is: "What is the specific number?"

If classification is a sorting hat, regression is a crystal ball that gives you a precise number, not a category.

Now towards our examples:

- **Business Problem:** "We need to set our budget accurately and manage inventory for the upcoming quarter."
- **ML Framing (Regression):** How much revenue, in dollars, will we generate next month?
- **What the Model Outputs:** A continuous value (e.g., $1,254,300, or 4,521 units sold).

A few more yet again:

- **Real Estate:** What is the predicted market price of this house?
- **Demand Forecasting:** How many units of this product will we sell next week?
- **Customer Value:** What is the estimated lifetime value (LTV) of this new customer?

Here, you'd work with algorithms like Linear Regression or tree-based models like XGBoost and Random Forests.

You'll measure success with metrics like Root Mean Squared Error (RMSE) or Mean Absolute Error (MAE).

---

### Ranking: What's Most Relevant or Important?

The Core Question: Ranking is about predicting an order or a sequence. The question is: "What should I show the user first, second, third...?"

This one is more or less like a hyper-personalized "Top 10" list generator for every single user.

On to our examples now:

- **Business Problem:** "Users are searching on our e-commerce site but aren't finding relevant products and are leaving."
- **ML Framing (Ranking):** Given a user's search query, what is the optimal order to display the available products to maximize the chance of a click or purchase?
- **What the Model Outputs:** An ordered list of items (e.g., `[Product_ID_5, Product_ID_12, Product_ID_2, ...]`).

A few more, here we go:

- **Search Engines:** The order of results on a Google search page.
- **Social Media:** The personalized posts in your Instagram, X, or TikTok feed.
- **Recommendations:** The "Top Picks for You" section on Netflix or Spotify.

This is a more specialized field often called “learning-to-rank,” and depending on the use case, it can use metrics like nDCG, Precision@k, or Hit Rate - each helping measure how well the ordering aligns with what the user actually wants.

---

### Other Important Machine Learning Problem Frames

Not every problem fits perfectly into the big three.

Here are a few more frames to keep an eye out for:

* **Clustering: Finding Groups**
    * **The Question:** "What are the natural segments or groups within our data?" This is an *unsupervised* problem, meaning you don't have a pre-defined "right answer" to predict.
    * **Example:** "Can we group our customers into different personas like 'deal-hunters,' 'loyals,' and 'window-shoppers' based on their behavior?"

* **Forecasting: Predicting a Future Sequence**
    * **The Question:** "What will this value be over the next N time periods?"
    * **Example:** "What will our daily website traffic be for the next 30 days?" This is usually a series of regression predictions, but this one more often is a specialized discipline with its own set of tools (like ARIMA, which I wrote about in the article on [Time Series Analysis](/posts/why-time-series-deserves-comeback-forecasting-with-arima-sarima)

* **Anomaly Detection: Finding the Weird Stuff**
    * **The Question:** "Does this data point look unusual compared to everything else?"
    * **Example:** "Is this credit card transaction fraudulent?" or "Is this server reading indicating an impending system failure?"

---

## Your Practical 5-Step Machine Learning Problem Framing Checklist

Next time you get a vague request, walk through these five steps.

1.  **Start with the Business Decision.**  
    Ask: "What specific action will someone take based on this model's prediction?" If there's no clear action, the model might not really be needed at all.  
    *Example: We will send a 10% discount to customers predicted to churn.*

2.  **Define the Ideal Output.**  
    Ask: "What, specifically, does the decision-maker need to see?" A Yes/No answer? A dollar amount? An ordered list of the top 5 items?  
    *Example: We need a "Yes" or "No" for each customer.*

3.  **Choose Your ML Lens.**  
    Based on the output from Step 2, map it directly to a frame.  
    *Example: A "Yes/No" output means this is a Classification problem.*

4.  **Identify the Unit of Analysis.**  
    Ask: "What, exactly, are we making a prediction *for*?" Is it for a single customer? A product? A transaction? A single day? This defines the rows in your dataset.  
    *Example: We are making one prediction per customer.*

5.  **Determine the Success Metrics (Business & Technical).**  
    Ask: "How will we know if the model is good?" Define both the technical goal (e.g., achieve an F1-score > 0.8) and the business goal (e.g., successfully reduce overall churn by 5%).

---

## Framing in Machine Learning is Where the Real Value is Created

The best algorithm in the world can't save a poorly framed problem.

Our value as a data scientist doesn't just come from our ability to build complex models; it comes from our ability to ask the right questions and structure a problem in a way that leads to a truly useful solution. (LLMs can build these models in seconds these days, but they do fail to ask these business specific questions!)