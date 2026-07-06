---
title: "AI Agent Guardrails Look Simple Until You Actually Code Them"
date: 2026-07-02
tags: ["AI agents", "AI security", "AI governance", "backend engineering"]
categories: ["AI", "Cyber Security", "Learning"]
draft: false
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
description: "I already understood AI agent guardrails in theory, but writing a tiny path check made me respect the annoying details behind them."
---

I have spent the last year working around [AI security and governance](/posts/one-year-ai-security-governance-see-ai-differently/), so I already understood the high level idea behind guardrails.

Agents should have boundaries. Tools should have scopes. Read access and write access should mean different things. A system that can touch files, APIs, CRMs, Slack, browsers, or internal docs should probably have a stronger plan than "hope it behaves nicely."

Okay, that last sentence already sounds like I am about to sell you a whitepaper.

Anyways, I was doing a Boot.dev module around building an AI agent and the task was simple: let the agent list files from a working directory, but keep it inside the directory it was allowed to use.

It's technically a simple small function that checks if the agent is in the permitted directory, if yes, extract the details of all the items in that directory.

And having worked through that function I came out way more confident in my understanding of what goes behind guardrails, especially when it comes to local file access.

## The annoying part was a path check

The function looked like this at one point:

```python
def get_files_info(working_directory: str, directory: str = ".") -> str:
    try:
        working_dir = os.path.abspath(working_directory)
        full_target_path = os.path.normpath(os.path.join(working_dir, directory))
        if not os.path.commonpath([working_dir, full_target_path]) == working_dir:
            return f'Error: Cannot list "{directory}" as it is outside the permitted working directory'
        elif not os.path.isdir(full_target_path):
            return f'Error: "{directory}" is not a directory'
        else:
            results = []
            for item in os.listdir(full_target_path):                
                full_path = os.path.join(full_target_path, item)
                if os.path.isdir(full_path):
                    isdir = True
                else:
                    isdir = False
                file_size = os.path.getsize(full_path)
                for item in os.listdir(full_target_path):
                    results.append(f"- {item}: file_size={file_size}, is_dir={isdir}")
            return "\n".join(results)
```

There is a bug in the listing part here.

I loop over `os.listdir(full_target_path)` twice, so the size and `is_dir` value can get tied to the wrong item. Very elegant. 10/10 production-grade software lol.

Anyways, the part that I want to share with you is:

```python
working_dir = os.path.abspath(working_directory)
full_target_path = os.path.normpath(os.path.join(working_dir, directory))
if not os.path.commonpath([working_dir, full_target_path]) == working_dir:
    return f'Error: Cannot list "{directory}" as it is outside the permitted working directory'
```

This is the base guardrail.

The agent gets a working directory. The user can ask for a directory. The code builds the real target path and checks whether that target still is inside the allowed working directory or not.

If the target is outside, the function returns an error.

Small thing, very boring, also the whole point.

## I knew the idea, but coding it makes a difference

This is where I felt the difference between understanding a concept and implementing it.

In my head, the rule was:

The agent should only inspect files inside the permitted directory.

I had to keep track of `working_directory`, `working_dir`, `directory`, and `full_target_path`. One is the function argument. One is the absolute version. One is what the user asked for. One is the thing the agent might actually inspect.

Those sound small until you mix them up.

And I did mix them up.

I passed the wrong thing to `abspath`. I confused `working_directory` and `working_dir`. I had to slow down and understand what `commonpath` was comparing. I also checked whether something was a directory using the wrong version of the path at one point.

All this through the process felt like, "why is this test still failing, I swear I understood this five minutes ago."

But in hindsight, the mistake was useful because it showed me where the guardrail actually does its work.

Details are tehcnically in the boring exact-ness.

- Which path is allowed?

- Which path was requested?

- Which path will the tool actually touch?

Those three questions have to line up. If they do not, the guardrail thing is out the window.

## The boundary has to become executable

In AI security and governance, we use a lot of clean words.

Controls. Policies. Permissions. Least privilege. Data boundaries. Tool access. Monitoring. Audit trails.

These words are useful. I am not making fun of them. Okay, some of them do start sounding like a compliance team discovered a thesaurus.

But they are useful.

The problem is that the words can stay at a comfortable distance from the implementation.

"The agent should only access approved resources" sounds fine.

Then you write the code and realize the approved resource is a path, the path can be relative, the filesystem has its own perks, and your variable names can be a part of the security model.

- The boundary eventually has to become executable.

- A function has to say yes or no.

- A tool has to reject the request.

- A path has to be normalized before it gets compared.

The model can be instructed but the tool has to enforce.

## A prompt is a request and code has to become the wall

You can tell an agent, "Only read files inside this folder."

Prompts matter, obviously. Half of the current AI world is people discovering that words have consequences and then pretending this is a new branch of engineering.

But the prompt is still a request.

The model can follow it, misunderstand it, ignore it in some edge case, or get pulled away from it by some other piece of text. I am not even saying this in a dramatic jailbreak way. Sometimes systems fail because the input is weird, the instruction is vague, or the person using the tool asks for something the builder did not think about.

The tool code is where the request becomes a wall.

This was less obvious when I was staring at `commonpath` and asking myself whether I was comparing the actual path the agent would touch or some nice variable that made me feel safe.

And that is the part that is important when it comes to agents.

A chatbot can be wrong inside the chat window and irritate you. An agent with tools can read files, call APIs, update records, send messages, [browse websites](/posts/why-you-should-not-use-an-ai-browser-today/), or run commands. The error gets a body. It can move around inside your system and do things.

So when people say "we added a guardrail", I now have a much more annoying follow up question in my head.

Where?

In the prompt? In the tool function? In the permissions layer? In the UI? In some policy doc that everyone agrees with and nobody has implemented properly?

Yes, I have become this person.

## Agents make small engineering details matter

This also connects to the automation article I have been writing. (haven't published it yet, will do that soon)

The more a workflow touches real data and real systems, the less it feels like a productivity trick. Its a small system someone has to understand, trust, maintain, debug, and then maybe apologize for in a Slack thread that begins with "quick question."

Agents make this more important because the path is less fixed.

A regular script usually has a shape. And it can still break in absurd ways because computers are deeply committed to comedy, but at least you can usually point to the path through the code.

With an agent, the path can be looser. It can choose the tool. It can choose the argument. It can read a file and then decide the next thing to inspect. It can call the right function with the wrong target and look completely normal while doing it.

That is where boring engineering starts looking less boring.

Path checks, allowlists, read-only modes, write confirmations, logs, dry runs, smaller scopes, clear errors.

I used to think of these things as the furniture around the interesting part.

Now I think they might be the interesting part.

## The main work needs to be done before the actual code

The path check enforces a boundary, but it does not decide the boundary by itself.

Someone has to decide what the agent should be allowed to see.

The whole project? One folder? Only source files? Hidden files? Logs? `.env`? Generated files? Test fixtures? A scratch folder where it can make a mess without ruining anything important?

The same question comes up with writing access. Reading a file is one thing. Editing it is another. Deleting it is a separate category of "please tell me a human approved this before the agent got crazy."

This is where the AI governance side and the software engineering side start becoming the same conversation for me.

A policy can say the agent should only access approved resources. Good. Very adult.

Then the code has to decide what an approved resource is at 11:37 PM when a user passes `../` into a function.

That is the gap I am more interested in now.

The governance sentence and the code path have to meet somewhere. If they do not meet, the boundary is mostly vibes, and I have distrust of "vibes" now.

## What I learnt here

I did not learn that permissions matter. I already knew that.

It was more specific than that.

I started respecting the gap between agreeing with a guardrail and implementing one.

Before writing this function, I could say "restrict the agent to the working directory" and feel like the idea was clear enough. After writing it, I had to care about the exact path being checked, the exact path being used, and the exact point where the tool says no.

Slightly more irritating. Probably more useful.

And honestly, this is becoming a pattern in how I learn technical things now. The concept makes sense at the top level, then the code makes me pay attention to the small details where my understanding was still fuzzy. I hate this process during the process, obviously, because I am a normal person. But after the tests pass and the confusion goes down a bit, that annoying detail usually becomes the part I remember.

In this case, the thing I remember is simple: a guardrail is only as real as the place where the system enforces it.

## The small things I care about more

There are a few questions I now cannot ignore when looking at agents.

- What can the agent read?

- What can it write?

- Where is that enforced?

- Can it touch secrets by accident?

- Can it call an external API?

- Can it write somewhere permanent?

- Can I see what tool calls happened?

- Can I run it in a dry-run mode first?

- What happens when it asks for something outside scope?

- Who owns the mess if the agent does the wrong thing successfully?

A lot of software problems happen because the system did exactly what someone allowed it to do. The risky part is not always failure. Sometimes it is success inside a badly thought out boundary.

This is why I am starting to like boring controls more than I expected.

I still like the agent part. I still like the feeling of giving a system tools and watching it do something useful. I am very much the target audience for this stuff, which is maybe why I am also suspicious of it.

Because the useful version and the dangerous version can look weirdly similar in the beginning.

## Anyways, the guardrail was just a path check

That is the funny thing.

The guardrail was tiny. A few lines around `abspath`, `normpath`, and `commonpath`. It made me scrtch my head at variable names longer than I wanted, which is one of the least glamorous ways to spend your learning time.

And still, it changed how I think about this stuff a little.

AI agent safety often gets discussed through prompts, evals, jailbreaks, model behavior, and governance frameworks. All of that matters. I work around this world, so I know those conversations are necessary.

But once an agent gets tools, safety also becomes ordinary software engineering.

A function decides what the agent can touch. A check decides whether the request goes through. An implementation detail becomes the difference between a boundary and a suggestion.

Now, I respect the annoying code behind the guardrails a lot more.
