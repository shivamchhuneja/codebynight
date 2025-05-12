---
title: "Learning Golang from Scratch: My Day 1 Log of Backend Development with Golang"
date: 2025-05-12
tags:
  [
    "Golang",
    "Go Programming",
    "Backend Development",
    "Code Journal",
    "Learning to Code",
  ]
categories: ["Go Journey", "Learning to Code", "Backend Dev"]
draft: false
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
description: "Documenting my first day of learning Golang from scratch with real projects and tests."
---

I’ve just started my backend development journey - and I’m doing it with Go. Or Golang, if you prefer that name.

Why Go? Honestly, it feels solid. It’s clean. It’s simple. And most importantly, for some weird reason I don't yet understand, it’s _fun_. I’ve worked with Python before (mostly for data science & ML), but this time, I want to learn something from the ground up that’ll help me build real, scalable projects.

So here’s what Day 1 looked like.

---

## The Two Repos I’m Using

### 1. **interpreter-in-go**

This [repo](https://github.com/shivamchhuneja/interpreter-in-go) follows along with [Building an Interpreter in Go](https://interpreterbook.com/) by Thorsten Ball - a book Primagen recommended in one of his reaction videos.

It’s not just about Go. It’s about learning _how_ programming languages work. Parsing. Tokenizing. Lexing. Yes, yes, I have been a nerd all my life. And yes I'm that guy who would open up every electronic device in their house as a kid _(and yes, more often than not I couldn't put them back in original condition)_.

Anyways, I’ve just started, and even with the first few pages, I had to:

- Write a basic lexer
- Understand how to manage positions in strings
- Write tests (yes, real tests)

And speaking of tests…

---

## Writing Tests For the First Time 🤯

I've never written tests before. But I wrote my first Go test today for the lexer. It was weirdly satisfying.

Here's a snippet of the how the test code I wrote looks like:

```go
func TestNextToken(t *testing.T) {
	input := `let five = 5;`
	tests := []struct {
		expectedType    token.TokenType
		expectedLiteral string
	}{
		{token.LET, "let"},
		{token.IDENT, "five"},
		{token.ASSIGN, "="},
		{token.INT, "5"},
		{token.SEMICOLON, ";"},
	}

	l := New(input)

	for i, tt := range tests {
		tok := l.NextToken()
		if tok.Type != tt.expectedType || tok.Literal != tt.expectedLiteral {
			t.Fatalf("test[%d] failed", i)
		}
	}
}
```

It helped me _really_ understand how lexers work. Plus, now I finally get the hype around testing.

---

### 2. **learning-go**

This [repo](https://github.com/shivamchhuneja/learning-go) is where I’m learning Go fundamentals. I’m following a [Udemy course](https://www.udemy.com/course/go-the-complete-guide/) by Maximilian Schwarzmüller.

The course assumes you have a bit of programming background - which works for me, since I’ve used Python before.

But I’m not just following along blindly. I’m tweaking stuff. I’m trying variations.

Here’s a snippet from that:

```go
func bankService(balance float64) {
	var choice int

	fmt.Println("\nWelcome to Go Bank")
	fmt.Println("What do you want to do?")
	fmt.Println("1. Check Balance")
	fmt.Println("2. Deposit Money")
	fmt.Println("3. Withdraw Money")
	fmt.Println("4. Exit")
	fmt.Print("Enter your choice: ")
	fmt.Scan(&choice)

	switch choice {
	case 1:
		checkBalance(balance)
		bankService(balance)
	case 2:
		balance = depositMoney(balance)
		bankService(balance)
	case 3:
		balance = withdrawMoney(balance)
		bankService(balance)
	case 4:
		fmt.Println("Thanks for banking with us!")
		os.Exit(0)
	default:
		fmt.Println("Invalid option. Try again.")
		bankService(balance)
	}
}

func checkBalance(balance float64) {
	fmt.Printf("Current Balance: %.2f\n", balance)
}

func depositMoney(balance float64) float64 {
	var amount float64
	fmt.Printf("Your current balance is %.2f\nHow much would you like to deposit? ", balance)
	fmt.Scan(&amount)
	balance += amount
	fmt.Printf("Done. New Balance is %.2f\n", balance)
	return balance
}
```

It’s basic. But I'm tinkering instead of "Copy Pasta" as Primeagen would say. That’s what counts right now.

---

## Why This Feels Different

This isn’t about “finishing a course.” It’s not even about shipping an app yet.

This is about learning - _really_ learning - how backend systems are built, how programming languages work, and how you go from a blank screen to working code.

And it feels good to document it all.
hugo

---

## What’s Next?

- Keep progressing in the interpreter book
- Finish a few more modules fom the course

More soon.

---

🧠 [Interpreter Repo](https://github.com/shivamchhuneja/interpreter-in-go)
📘 [Learning Go Repo](https://github.com/shivamchhuneja/learning-go)
🎥 [Course: Go - The Complete Guide on Udemy](https://www.udemy.com/course/go-the-complete-guide/)
