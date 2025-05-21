---
title: "Day 5–8: Fine-Tuning AI Models, Learning MLOps, and Structuring My Year of Projects"
date: 2025-05-21
tags:
  ["Golang", "AI", "Deep Learning", "MLOps", "Fine-Tuning", "Learning Journal"]
categories: ["Learning Go", "AI/ML Journey"]
draft: false
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
description: "A learning log covering project planning for AI/ML, Go language practice, deep learning theory, MLflow basics, and fine-tuning open-source LLMs across Day 5 to Day 8."
---

It’s been a few days since I posted an update here. Not because I wasn’t learning - in fact, the opposite. I was working through a mix of things, from structuring my year-long learning roadmap to actually fine-tuning large language models for the first time.

---

## Why I Wasn’t Posting Daily

Simple: I needed to zoom out a bit.

I took a couple of days to sketch out **what I want to build** in the next few months — not just random toy apps, but meaningful projects that actually challenge me to grow.

### ✅ I landed on 8 intermediate-to-advanced projects:

- A self-healing machine learning pipeline
- An AI-powered repository health tool
- A reinforcement learning–based warehouse management simulation
- ...and a few others I'll write about soon

I’ll be documenting each one - through blogs, and eventually, YouTube videos.

---

## What I Did During These Days

### 🔧 **Go Language Progress**

I revisited structs, especially:

- Embedded structs
- Package exports
- How nested structs behave and how Go handles memory when things get passed around

Nothing too flashy — just getting the reps in.

---

### ⚙️ **MLOps with MLflow**

- Got my first few **experiments tracked in MLflow**
- Learned how easy it is to get started... and how quickly it can get messy if you don’t think about structure upfront

This was just the start - but it gave me confidence to go deeper. Plus also my classes start soon, so I need to be ready.

---

### 🧠 **Deep Learning Math Refresher**

Even though I’ve been through this before, I wanted to revisit the fundamentals:

- Matrix multiplication
- Logarithms & entropy
- Cross-entropy, min/max, argmin/argmax
- Mean, variance, and a bit of spectral math

It’s amazing how much easier this feels the second time around.

---

### 🔁 **Fine-Tuning Language Models (The Real Work)**

This was the biggest chunk.

I fine-tuned three different models:

- 🐍 **Code LLaMA 13B**
- 🌊 **Mistral 7B**
- 🇨🇳 **Qwen 2.5**

All using LoRA adapters. Some on Google Colab (for GPU), some locally on my MacBook via MLX. The goal was to fine-tune for **long-form generation**, but... let’s just say I have a lot of learnings.

### Key Takeaways:

- Preparing the dataset took **more time** than training.
- Writing the actual training script? Almost boringly simple.
- Results weren’t great - and that’s **good**, because now I know **why**:
  - Wrong model for the job (don’t fine-tune a general base model for structured output)
  - Prompting might’ve been a better route in some cases
  - Fine-tuning ≠ magic - model alignment matters more than you'd think

---

### 🧪 Bonus Lesson: It’s Not Just About the Model — It’s About the Fit

One thing became very clear while fine-tuning these models: the **fit between your goal and your model matters more than anything else**.

At first, I was trying to get long-form, structured outputs using models that were never really trained for that. The results? Pretty underwhelming.

What made a real difference was this realization — **if your model isn’t aligned to your use case, no amount of prompting, training, or tweaking will get you good results**.

I now spend more time upfront asking: _Is this even the right model to fine-tune for this task?_ And in most cases, the answer tells me what I need to fix not the code, not the GPU setup, but the alignment itself.

---

## What’s Next?

Now that I’ve got my 8 projects lined up, the next few weeks will be more focused:

- **Deep Learning** → FFNs, Autoencoders, etc.
- **Go** → Interfaces and modular structure
- **MLOps** → More MLflow, maybe some Docker and Airflow after that
- **Fine-tuning** → Better experiments with task-aligned models

More importantly, I’ll be documenting everything as I go.
