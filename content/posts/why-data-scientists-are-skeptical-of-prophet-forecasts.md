---
title: "Why Data Scientists Keep Saying Not To Use Prophet"
date: 2026-07-20
tags: ["Prophet", "forecasting", "time series", "ETS", "model evaluation", "backtesting"]
categories: ["Time Series", "Machine Learning"]
draft: false
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
description: "I tested Prophet against seasonal naive and ETS on two monthly series to see why a clean forecast chart is not enough to trust the model."
---

I understand why Prophet gets picked up so often.

You give it a date column and a value column, fit the model, ask for the future dataframe, and it gives you a chart that looks like somebody has already put it in a planning deck (I'm sure that in the last 30 days you've met at least 1 person who has done this).

Anyways, there is a trend, there are changepoints, there are uncertainty bands. It feels much more finished than a lot of time series work feels in the beginning.

I have definitely looked at those charts and felt like the model had found something important. Then I started spending more time reading about validation and working through forecasting problems, and as you can guess, its outright harder to trust.

It's a different kind of high. A forecast line extending past the data does something strange to the brain. It looks like an answer even when it is really just a model pushing its assumptions into a period it has not seen yet.

That is more or less why people keep telling you to be careful with Prophet. Or atleast everyone on Reddit does lol.

I do not think the useful version of that advice is "never use Prophet." That sounds like the a rule people make after watching somebody use a tool badly once. The better question is, has Prophet earned the confidence we give it when the plot looks convincing enough?

So I ran a small backtest. Yes yes, I know one backtest is not enough to go heads on with every self proclaimed senior data scientist with 25 years of experience on Reddit but bear with me for this couple hours of fun work that kept me entertained this last weekend.

I put one fixed Prophet configuration against seasonal naive and ETS on two public monthly FRED series. ETS won every pooled metric on both series. That sounds clean, maybe too clean.

When I looked at the individual forecast windows, Prophet still had the lowest 12-month MAE once for each series. Then one of the retail windows ran straight into April 2020, and every model made a mess of it. We all know why...and we shall not write that word because we fear the Google SEO gods.

## The experiment was deliberately boring

I used two monthly US series from FRED: [CPI, all items, not seasonally adjusted](https://fred.stlouisfed.org/series/CPIAUCNS), and [advance retail trade and food services sales, also not seasonally adjusted](https://fred.stlouisfed.org/series/RSAFSNA). They are not supposed to represent every forecasting problem. They gave me two fairly long monthly series with seasonality, and retail sales also gave the comparison a very inconvenient period to work with.

For each series, I made forecasts from January 2019, 2020, 2021, 2022, 2023, and 2024. At every one of those origins, the models only received the history available up to that month and forecast the next twelve months. That gave me 72 scored observations per model for each series.

I kept the comparison small because I wanted the design to stay understandable. Seasonal naive repeats the value from the same month a year earlier. It can sound embarrassingly basic until it beats something more complicated.

Don't tell me you haven't spent 5 hours on bagging and boosting and what not only to finally settle with a simple regression. Data scientist happy, manager happy, boss happy, client happy.

Alright, let's move on. The classical alternative was additive damped-trend Holt-Winters ETS, fitted again inside each training window. Prophet stayed on the same configuration across both series and all six origins, with linear growth, yearly seasonality, no holidays, and no external regressors.

I did not tune settings after looking at the out numbers. A lot of comparisons become a bit silly when somebody spends days carefully tuning the model they like and lets the other one run on defaults, then calls the result an evaluation. Yep, I am guilty of this and I know you are too!

I also wrote earlier about why I still like [ARIMA](/posts/arima-is-boring-and-that-is-why-i-still-like-it/). ARIMA is not in this test. I wanted a narrower answer: can this one fixed Prophet setup beat a reasonable seasonal baseline and a seasonal ETS model on these two series?

## ETS won the table, but the table is not the whole story

Here are the pooled errors across the six forecast origins. Lower is better for all three metrics.

| Series | Model | MAE | RMSE | MASE |
|---|---|---:|---:|---:|
| CPI | ETS | 5.09 | 6.62 | 1.94 |
| CPI | seasonal naive | 10.51 | 12.37 | 3.95 |
| CPI | Prophet | 14.32 | 18.07 | 5.22 |
| Retail sales | ETS | 24,079.29 | 33,993.04 | 1.42 |
| Retail sales | Prophet | 37,383.62 | 48,859.10 | 2.14 |
| Retail sales | seasonal naive | 39,831.57 | 53,671.23 | 2.32 |

ETS had the lowest pooled MAE, RMSE, and MASE for both series in this run. Read the numbers within each series, though. CPI is measured in index points and retail sales are measured in their own dollar units, so an error from one row does not become bigger or smaller in any way beside an error from the other series.

MAE is the average absolute error. RMSE punishes larger misses. MASE is useful because it scales error against a seasonal-naive in-sample forecast, though mine needs a small warning label. I calculated its seasonal-naive scale separately inside every training window, then averaged the point-level scaled errors across the origins. There is no one shared MASE denominator across all six origins, and I do not want to make it sound more universal than it is.

ETS had lower MAE than the fixed Prophet configuration at every one-to-twelve-month horizon for both series. That is a useful result for this setup, but I would still choose the horizon based on the decision. A model that is fine for next month's plan can be a completely different thing from a model somebody is using for a year of inventory planning.

## The pooled result did hide the parts I actually wanted to see

A pooled score stops me from falling in love with one lucky forecast window. It also turns six different moments in the data into one number which can hide the real truth.

Prophet had the lowest 12-month MAE at the January 2019 CPI origin, with 1.54 against 4.91 for ETS and 4.75 for seasonal naive. It also had the lowest MAE at the January 2020 retail origin, with 25,167.60 against 28,024.09 for ETS and 32,388.33 for seasonal naive.

Then April 2020 arrived inside that retail forecast window.

Actual retail sales for that month were 401,556. Seasonal naive predicted 496,982, ETS predicted 519,757, and Prophet predicted 515,067. Seasonal naive was closest, with an absolute error of 95,426. ETS missed by 118,201 and Prophet missed by 113,511.

I do not think this is where we make fun of Prophet or declare seasonal naive the hero of forecasting. All three models had the series history. None of them had a pandemic variable, a policy timeline, or a useful way to know that retail conditions were about to change at that speed. The more interesting thing is that the pooled winner did not solve that problem either.

This is why I get uneasy when people talk about model evaluation as if one comparison is all that is needed. The average is good although it does not tell me which months mattered to the person using the forecast, if the model missed a seasonal peak, or if a change in the business made the historical pattern temporarily useless.

## Prophet is easy to trust before it is easy to test

I think this is where the scepticism around Prophet comes from.

Prophet makes it easy to produce a plausible _(probably the first and last time I have used this word)_ first forecast. That is useful when you are exploring a new series and I would rather somebody make a rough forecast than stare at a spreadsheet for three weeks waiting for enlightenment.

Prophet still makes assumptions about the future. It models trend and seasonal effects. It can put changepoints where the historical trend appears to have moved. It can use holidays and external regressors if we give them to the model. None of that means it knows why the line moved.

A changepoint in sales could come from a product launch, a price change, a tracking problem, a campaign, or somebody fixing an old spreadsheet mistake. The model sees a change in the numbers. The business still has to work out which story belongs to it. Which btw brings me back to my old article about why each data science problem is a business problem first before it is a DS or ML problem!

I do not think this is a special problem with Prophet either. ARIMA can be treated like magic. ETS can be treated like magic. A seasonal-naive forecast can be treated like magic if it happens to look good for long enough. Forecasting models only know the data we have given them and the patterns they can pull from it. A nice plot just makes it easier to forget that.

## What I would do with a new series now

This little test changed my habits more than it changed my opinion about one library.

If I needed a forecast for a real decision I would start by asking what the decision is and how far ahead it needs to look. Then I would put Prophet beside a baseline that has a fair chance of being useful, along with at least one classical alternative where it makes sense. Every model should get the same history at each origin, the same forecast horizon, and a setup chosen without peeking at the future scores.

After that I would look at the pooled errors but I would also look at the individual forecast windows and the horizons that resemble the actual use case. Promotions, price changes, supply problems, policy changes, and a lot of ordinary business context do not exist in a univariate series unless somebody adds that information and tests whether it helps. A better forecasting model might be useful. Better information can also be the thing the model was missing.

I would also want to know what a bad forecast costs. MAE, RMSE, and MASE are useful, but they do not know whether it hurts more to order too much inventory or too little, whether somebody can adjust later, or whether one month matters far more than the others. That work has to happen outside the metric.

## This is still a very small answer

The data came from current revised FRED observations retrieved on 20 July 2026, which makes this retrospective. A forecaster making decisions at those historical points would have seen earlier data vintages so this is not a real-time-vintage backtest.

The comparison covers two US monthly series, one fixed Prophet configuration, one ETS family, six annual origins, and a twelve-month horizon. I did not compare ARIMA or SARIMA, holidays, external regressors, other Prophet configurations, tuning budgets, or the actual cost of errors for a business.

So I cannot use this to say Prophet is broadly worse than ETS, or that ETS is universally better. I also cannot honestly use two series to explain what every data scientist thinks about Prophet. On these two revised FRED series, under this fixed design, ETS won the pooled metrics and Prophet still had a couple of good windows.

I am wrapping me writing this article with trusting the chart a little less which I think is a decent outcome. A forecast is enough to begin looking at a problem. Before I hand it any real authority I want baselines, a test that respects time and a look at the periods where the data decided to do crazy shit.
