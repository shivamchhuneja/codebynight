---
title: "Day 3 of Learning Go: Concurrency & Project Structure Refactor"
date: 2025-05-14
tags: ["Go", "Concurrency", "Project Structure", "Learning to Code"]
categories: ["Learning Go", "Dev Journal"]
draft: false
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
description: "Refactored my Go project structure and started the concurrency book — a short but insightful Day 3."
---

Today wasn’t a big coding day, but it was a good learning day.

---

## Why I Picked an Advanced Go Book

So here’s the thing - I’ve started reading **Concurrency in Go** by Catherine Buday.

Yup, a pretty advanced book for someone who’s still new to the language.

But honestly? It’s working really well for me. If I stuck to just `for` loops and `if` statements all day, I’d get bored fast. I’m not a total beginner in tech - I’ve been working with engineers and devs closely for a while - so this stuff doesn’t feel completely alien.

Here’s what I went through today:

- Race conditions
- Atomicity
- Memory access and synchronization
- Deadlocks
- (Next up: live locks and starvation)

It’s weirdly fun. Like I’m finally getting to peek behind the curtain.

---

## Reorganizing My Go Project Structure

The other thing I did today was restructure my Go project.

I’m doing a Udemy course by Maximilian Schwarzmüller, and he starts a fresh project for every lecture. But I wanted a single repo where I could organize everything cleanly.

That meant:

- Breaking out separate packages
- Exporting functions properly
- Importing and referencing them cleanly
- Making things modular and easy to maintain

Took some trial and error, a bit of help from ChatGPT (like you’d use Stack Overflow), and a couple of YouTube videos. But I finally feel like I understand how Go projects should be structured.

Here’s what it looks like right now:

```go
Go/
├── calculators/
│ ├── bank.go
│ ├── investment_calculator.go
│ └── profit_calculator.go
├── helpers/
│ └── utils.go
├── pointers/
├── structs/
│ └── structs.go
├── go.mod
└── main.go
```

Nothing fancy. But it’s mine, and it’s working.

🔗 [View the repo](https://github.com/shivamchhuneja/learning-go)

---

## A Quick Snippet

```go
package main

import (
    "fmt"
    "os"
    "github.com/shivamchhuneja/learning-go/calculators"
)

func main() {
    runApp()
}

func runApp() {
    var option int

    fmt.Println("Select the calculator")
    fmt.Println("1. Investment Calculator")
    fmt.Println("2. Profit Calculator")
    fmt.Println("3. Bank Service")
    fmt.Println("4. Exit")
    fmt.Print("Your choice: ")

    fmt.Scan(&option)

    switch option {
    case 1:
        calculators.InvestmentCalculator()
    case 2:
        calculators.ProfitCalculator()
    case 3:
        calculators.BankingMode()
    case 4:
        fmt.Println("Exiting now...")
        os.Exit(0)
    default:
        fmt.Println("Try again")
        runApp()
    }
}
```

---

## That’s All For Today

Didn’t write a ton of code, but I walked away with:

- A better grasp on Go project structure
- A stronger mental model of concurrency
- And a cleaner, more usable repo

**Not bad for Day 3.**
