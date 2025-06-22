---
title: "I Built an Open Source AI Powered SaaS Market Intelligence Tool for Marketing Teams. Here's How"
date: 2025-06-22
description: "A full walkthrough of building and deploying a SaaS Market Intelligence tool using Streamlit + FastAPI + GPT-4. I cover prompt design for clarity vs competitor analysis, scraping dynamic websites with Playwright, deployment lessons using Render, and what’s next for the tool - all from a builder-marketer’s perspective."
tags: ["saas", "streamlit", "fastapi", "technical marketing", "growth engineering", "ai tools"]
categories: ["Projects", "AI Tools", "Growth Engineering"]
draft: false
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
---

So, the idea for this came from a chat I had with Dhruv, the CEO of Middleware.

He pointed out that I should think of myself as a 'builder-marketer,' not just a marketer, and that I should build stuff that proves it.

I thought about it, and he had a point.

So I decided to build a project that would be useful for marketing and growth, but also something I could deploy myself.

Honestly, I was also just tired of having ideas and needing to wait on an engineering team. Plus, it was a good excuse to finally learn how to deploy a small full-stack app.

That’s what this is.

[An AI tool to analyze competitor pages and your own site](https://saasintelligence.streamlit.app/) for offer clarity, blind spots, missed opportunities and emotional resonance with your intended ICP and more.

It's a selfish project that I'm hoping is useful for others too. Hence its also completely open source.

On the surface, it's dead simple: You plug in a SaaS homepage URL, pick an analysis mode, either **"Is our offer clear?"** or **"What are our competitors up to?"** and the tool gives out a structured analysis.

It scrapes the site, runs the text through a custom GPT prompt, and gives you the meat.

The intended users are marketing teams, product marketing people, SEO people and maybe even CMOs and some CEOs who want to get a quick output analysis of their competitor's pages.

The only "techy" thing that you'd need to use this app is to plugin your own OpenAI api key, that's all.

Anyways, getting this thing to work *well*? That was a journey.

Here's a look under the hood at the tool, my thinking, and some minor headaches that almost made me flip a table.

---

## ⚙️ So, How Does It Actually Work?

From your end, it's a four-step process:

1. Enter a SaaS homepage (e.g., `https://vercel.com`).
2. Choose your weapon:
    - Offer Clarity Analyzer: Does your homepage make any sense?
    - Competitor Page Breakdown:** What's the competition's game plan, SEO, ICP, offer focus and missed opportunities?
3. Drop in your OpenAI API key:
    - Don't worry, it's only used for this session and isn't stored anywhere. Your key, your business.
4. Hit "Run Analysis." The magic happens:
    - Playwright scrapes the live site.
    - The text gets fed to GPT with my special sauce prompt.(the repo is open source, you can just copy pasta it and improve upon it boss)
    - You get a clean, structured breakdown in seconds.

![SaaS Market Intelligence Tool](/images/blog/saas_market_intelligence_tool.png)

---

## 🧠 Why These Two Modes? (And Not Another Generic GPT Toy)

The world doesn't need another generic "Summarize this URL" tool.

I wanted something that solves a real, repetitive task for SaaS marketers.

I chose **Offer Clarity** and **Competitor Breakdown** because I do this stuff manually *all the time*, especially when I'm figuring out a go-to-market strategy.

Or the alternative is paid tools that charge $49 to even $99 a month!

I wanted to save time and get more done and the prompts are handcrafted to reflect that.

### The "Offer Clarity" Prompt

I designed this one to be brutally honest.

It answers the questions a first-time visitor would have in their head:

- What does this thing even do?
- Who is this for?
- What's the actual value here?
- What's confusing or missing?
- How would you say it better?

![SaaS Offer Clarity Score AI Tools](/images/blog/saas_offer_clarity_score_ai_tool.png)

The goal is to simulate a sharp product marketer (or a confused prospect) giving your homepage a 15-second scan and telling you what's broken.

### The "Competitor Breakdown" Prompt

This prompt basically lets you spy on your competitors.

It scans a competitor's page and pulls out the info you need for GTM planning:

- Their core value prop.
- The ideal customer profile they're targeting.
- Keywords and product categories they're hitting.
- Any shots they're firing at other companies.
- Any mention of pricing.
- Actionable insights for your own strategy.
- Any missed opportunities or blind spots strategically that you can exploit

It's perfect for quickly sizing up a handful of competitors without spending all day reading their websites.

---

## 🔍 Why I Had to Use Playwright (and not BeautifulSoup)

This part was a pain.

My first attempt did use BeautifulSoup. I've used it before and it works, beautifully, lol.

For this project too it was fast and simple... until it wasn't.

For a lot of modern SaaS sites built with heavy JavaScript frameworks, it just couldn't get to the content.

Try scraping a site like `mixpanel.com` with BeautifulSoup.

You'll get a whole lot of empty utensils.

The text just isn't there in the initial HTML.

So, I switched to Playwright.

It's a headless browser that renders the page just like a real user would, *then* grabs the text.

Yes, it's a bit slower and heavier. But it actually works reliably on the sites that matter.

**Lesson learned:** If you're scraping modern web apps, a headless browser might not be optional.

---

## 🛠️ My Simple Backend + Frontend Setup

To avoid building a messy project since I'm not yet that profienct, I kept the frontend and backend separate.

- FastAPI Backend: A simple API with two endpoints: `/scrape` and `/analyze`. This is the meat.
- Streamlit Frontend: The user-facing app with the input fields and buttons. This is your fork and knife.

The FastAPI backend is on its own server (I used Render), and the Streamlit app just calls it.

This makes it way easier to update one part without breaking the other.

Also I used streamlit because I wanted this done within the weekend, react frontend is still an option but for now if it works, let's not break it.

---

## 🚨 My Deployment Headache on Render

Okay, this is where I hit a wall.

I initially deployed the backend on **Render's free plan**. Seemed like a great deal. It worked... until someone actually tried to use it.

Here's what went wrong:

- The "spin down": Render's free instances go to sleep after 15 minutes of inactivity. The first person to hit the app would have to wait 40-50 seconds for it to wake up. The UX was terrible.
- Timeouts: Sometimes, the cold start was so slow that the frontend would just give up and throw an error.
- Constant wake-ups: I'd test it, drink water, come back, and it would be asleep again.
- This led to weird frontend errors like `Expecting value: line 1 column 1`, which basically means the backend sent back an empty response because it was still booting up.

I finally gave in and upgraded to Render's paid plan.

Problem solved.

The instance stays warm, and the app feels instant.

**My advice:** Start on the free plan to get things working, but if you want anyone to *actually* use your app without rage-quitting or breaking their keyboard, pay the few bucks to keep it live.

---

## 🧪 A Weird Bug: Local vs. Live

I also ran into one of those classic "but it works on my machine!" issues.

My footer, a simple `st.markdown()` with some HTML, showed up perfectly when I ran it locally but was invisible on the deployed Streamlit app.

If you ever need to add a styled link in Streamlit, here's a snippet that works:

```python
st.markdown(
    """<p style='font-size: 1rem; color: white;'>
    Check out more projects on:
    <a href='https://codebynight.dev' target='_blank' style='color: white; text-decoration: underline;'>
    codebynight.dev
    </a></p>""",
    unsafe_allow_html=True,
)

```

---

## 🧠 What's Next?

Now that the thing is stable, all I need to get within next 15 days is to $5M ARR...

Anyways, on a serious note, next steps:

- Tweak the prompt to be more strategic, more business focused. Maybe even ask the user their purpose for the analysis and modify the prompt based on that.
- Scan more than just the homepage: Crawl a few key pages (like pricing and features) for deeper intel.
- Shareable results: Let users export the analysis as a PDF or share it with a link.

I might get to those eventually. For now, it does exactly what I needed it to do.

---

## 🚀 Try It Yourself

- 👉 [Use the live Saas market intelligence tool here](https://saasintelligence.streamlit.app/)
- 👉 [Check out the backend code on GitHub](https://github.com/shivamchhuneja/saas-intel-backend)
- 👉 [And the frontend code here](https://github.com/shivamchhuneja/saas-intel-frontend)

---

## 🧾 Let's Wrap It

Sometimes the best projects are the ones you build for yourself. This was one of them.

Lots to learn and add to my confidence!

If you're a marketer or founder trying to get quick insights on your messaging or your competitors, I literally built this for you.
