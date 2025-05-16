---
title: "Day 4 of Learning: Switching Between Golang and Deep Learning"
date: 2025-05-16
tags:
  [
    "Golang",
    "PyTorch",
    "Deep Learning",
    "AI",
    "Developer Journal",
    "Learning Journey",
  ]
categories: ["Learning Go", "AI/ML Journey"]
draft: false
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
description: "Learning Golang structs and pointers while returning to deep learning with PyTorch and prepping for my second year of masters in data science & ML."
---

It’s Day 4, and today was a little different - not heavy on code, but still a strong day of learning. I'm trying to balance two learning paths right now: backend fundamentals with Go and ML + deep learning using PyTorch.

---

## Wrapping My Head Around Pointers and Structs in Go

Most of today’s Go time was spent clarifying how data is passed and accessed when using pointers and structs.

```go
type User struct {
	FirstName string
	LastName  string
	BirthDate string
	createdAt time.Time
}

func Struct_fn() {
	FirstName, _ := helpers.StrUserInput("Please enter your first name: ")
	LastName, _ := helpers.StrUserInput("Please enter your last name: ")
	BirthDate, _ := helpers.StrUserInput("Please enter your birthdate (MM/DD/YYYY): ")

	appUser := User{
		FirstName: FirstName,
		LastName:  LastName,
		BirthDate: BirthDate,
		createdAt: time.Now(),
	}

	outputsUserDetails(&appUser)
}

func outputsUserDetails(u *User) {
	fmt.Println(u.FirstName, u.LastName, u.BirthDate)
}

func (u *User) ClearUserName() {
	u.FirstName = ""
	u.LastName = ""
}
```

Even after completing the basics, I had to go back to ChatGPT, asking follow-up questions like:

- _When does Go actually copy a struct?_
- _What’s the best way to mutate values without triggering memory issues?_
- _Is referencing a pointer enough if my struct has nested fields?_

This kind of back-and-forth learning is slower than a typical tutorial. But the mental model is forming. I’m not rushing to build things - I’m trying to deeply understand how Go works under the hood. Especially when it comes to memory management.

Ten years ago, I would’ve given up on a concept like this. Today, I’m just taking it step by step.

---

## Re-entering the Deep Learning World

Alongside Go, I’ve started brushing up on deep learning - mostly because my second year of the master’s program is around the corner, and it's going to be all about machine learning, MLOps, and system-level thinking.

I’ve started tinkering with PyTorch again. Right now, it's about understanding artificial neural networks (ANNs) from the ground up. Not just watching videos — but opening up a notebook and writing everything manually.

I like PyTorch. Maybe because I’ve touched computer vision before during my internship in Denmark — when I was at Aalborg University. We were working with OpenCV, and although it was research-focused, it gave me an early glimpse into how machines can _see_.

I guess that curiosity never really went away.

---

## A Bit More Structure This Time

I’ve also been thinking about structure — not just in neural networks, but in how I organize my codebases.

Since I’m keeping all my Go learning in a single repository, I had to restructure the project to keep things clean. Instead of one massive file, I split everything into packages: calculators, helpers, pointers, and so on.

That required learning how to export functions properly in Go, how to keep imports clean, and how to avoid circular dependencies. It wasn’t difficult, but it did take a bit of trial and error. And honestly? It’s these small structural lessons that make you feel like you're learning _how to think like a developer_.

_(P.S. I wrote more about this restructuring in [Day 3’s post](/posts/day-3-concurrency-and-go-project-structure-refactor/).)_

---

## What’s Next

Over the coming week, I plan to keep switching tracks — Go for backend fundamentals and PyTorch for deep learning.

- I’ll be diving deeper into **structs, interfaces, and generics** in Go (based on the course I’m following).
- I’ll continue reading **Concurrency in Go**, trying to wrap my head around things like deadlocks, livelocks, and atomic memory access.
- I’ll also keep going with [**Building an Interpreter in Go**](https://github.com/shivamchhuneja/interpreter-in-go) — that repo is where I try to apply my Go learning to something more complex.

On the deep learning side:

- I’ll keep working through **artificial neural networks** using PyTorch — and slowly move toward feedforward networks and autoencoders.
- There’s a **whole MLFlow module** I’m yet to touch — which includes tracking experiments and integrating ML models.
- I’ll also revisit **cross-validation, generalization, and overfitting**, including hands-on experimentation with scikit-learn and PyTorch Dataloaders.

And of course, I’ll continue reading a few chapters of _AI Engineering_ by Chip Huyen — to understand how real-world AI systems are built and deployed.

It's going to be a packed week, but I’m looking forward to it.

---

## That’s All for Day 4

Today wasn’t flashy. I didn’t finish a big project or write hundreds of lines of code.

But I did get clarity. On how Go handles memory. And on how I want to structure my learning going forward.

That’s progress in my book.
