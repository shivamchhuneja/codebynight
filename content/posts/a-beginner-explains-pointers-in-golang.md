---
title: "A Beginner Explains Pointers in Go: The Thing That Made Me Quit Coding (And Why I'm Back Now)"
date: 2025-05-22
tags: ["Golang", "Pointers", "Learning Go", "Dev Life"]
categories: ["Learning Go", "Developer Thoughts"]
draft: false
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
description: "A decade ago, pointers made me quit programming. Now I'm back — still scared of them, but this time with just enough understanding to be dangerous."
---

I learned about pointers 10 years ago… and I hated them. I still hate them. But now at least I can explain them, which, by some strange software industry law, qualifies me for a senior dev role.

---

## Flashback: Engineering School and Existential Dread

Back in electronics engineering, we were handed C++ for one semester and told, “Here, go build your future.” By Day 2, we were doing pointers - not the helpful kind, but the kind that break your code, your compiler, and your soul.

Parallel to that, I was working with an 8085 processor - an experience that felt like coding inside the Matrix, except there was no red pill. I wasn’t writing programs. I was writing memory access violations in multiple languages.

Naturally, I quit programming.

I nearly pivoted into project management… until I opened Jira. That’s when I ran back to engineering.

Flash forward 10 years. I’ve been doing Python for a year and a half now - data science, machine learning, the whole vibe. No semicolons. No manual memory management. No existential crisis. Right?

Right?

Wrong. Because one day I decided, for some reason, to try Golang.

---

## First Week of Go: Guess Who’s Back?

Apparently, real developers don’t use pandas. They build APIs at 3AM and argue about Vim configs on Reddit.

And within the first week: pointers. Again.

---

## So What _Is_ a Pointer?

Let’s break it down.

Imagine you’re a dev with imposter syndrome. You don’t tell people the answer, maybe because you can't - you just give them a reference to Stack Overflow. Congratulations, that’s a pointer.

(**I really do hope you are not sending people to Stack Overflow in 2025.**)

More formally: a pointer doesn’t hold a value, it holds the **address** of a value. Like saying:

> “I won’t give you the actual pizza, but here are the GPS coordinates of where it’s sitting.”

---

## Pointers in Go: Code Time

In Go, you declare a pointer using a `*` and dereference it using `*` again.

```go
a := 10
b := &a   // b is a pointer to a
fmt.Println(b)  // prints something like 0x1400012a008
```

To get the actual value from `b`, you do:

```go
fmt.Println(*b) // prints 10
```

Seems simple? Just wait.

---

## Why Use Pointers?

If you're wondering “Why do I even need pointers?” — congratulations, you're officially a Python developer.

But here’s the thing: pointers let you pass variables around efficiently. Instead of copying data, you just share its address. It’s safe house, but for your variables. Unless someone moves your variables around.

---

## But They’re Dangerous

Pointers are powerful, sure - but also a great way to cause memory leaks, panic-inducing bugs, and passive-aggressive code reviews.

They’re like handing your intern root access and saying “do whatever you want.”

A pointer is like this:

> “Go check drawer #3 in the kitchen.”

Now, if someone moved the knife to drawer #2 and didn’t tell you - congratulations, you just segmentation-faulted in real life.

---

## So Where Am I Now?

I still kind of hate pointers. But now, I understand them. And that’s a milestone.

I'm somewhere between:

- finally learning how async works, and
- giving up on Arch Linux for good.

So if you're currently crying over a dereference error don't panic, don't rage quit, and maybe don’t listen to ThePrimeagen (unless you want to rewrite everything in Rust).

Just remember:

> A pointer is like that weird always high friend who doesn’t give you the answer. They just whisper where to find it.

---

May your dereferences never be nil.
