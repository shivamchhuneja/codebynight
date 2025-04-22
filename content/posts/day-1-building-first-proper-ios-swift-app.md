---
title: "Day 1 of Building My First Proper iOS Swift App: The Idea, the Plan, the Stack"
date: 2025-04-21
tags: ["Swift", "SwiftUI", "iOS App", "Build in Public", "Learning iOS App Development"]
categories: ["Swift Journal", "iOS Development", "Swift iOS App"]
draft: false
ShowToc: true
TocOpen: false
ShowPostNavLinks: true
description: "I’ve started building my first SwiftUI app from scratch. Here’s what it’s about, who it’s for, and why I’m sharing every step of the journey."
---

I’ve started building a proper iOS app. This is not going to be a resume only project. This one has a purpose.

It’s called *Checklistd* — a to-do list app.

Ewww...another to-do list app? Yuck.

Hear me out, this is not just another random to-do list app. This one’s made for job seekers.

If you’ve followed me on Instagram or YouTube, you know I talk a lot about careers, job searching, switching roles, and figuring stuff out. So it only made sense that my first iOS project would be something that could actually *help* people who are in that messy, sometimes frustrating phase of trying to land their next job.

But here’s the thing: I’m still learning Swift. I’m building this from scratch. It’s not some polished SaaS launch. It’s a learning project. A playground. A chance to take what I’m learning with SwiftUI and SwiftData and actually ship something — however small it starts.

## Why This App?

There are already hundreds of to-do list apps out there. I know that.

But most of them are too broad, too busy, or too boring. None of them are really made for the mindset of a job seeker.

So I thought: what if I created a super clean, black-and-white checklist app that does *just* what you need for job searching?

Something that gives you:

- Prebuilt daily job search checklists  
- A tracker for job applications and follow-ups  
- Little motivators like streaks and progress summaries  
- A layout that doesn’t overwhelm, just helps you move forward

It’s simple. It’s focused. And it’s going to be completely free.

No upsells, no subscriptions, no premium unlocks.

Just a free tool that’s part of my own learning journey — and maybe part of yours too.

## Why I’m Sharing This Publicly

I could build this quietly.

But I’ve decided to document the journey — not just because it keeps me accountable, but because I think there’s real value in learning *out loud*.

I’ll be blogging regularly (maybe almost daily) as I work on *Checklistd*.

Some days will be big — new screens, new features, maybe a win or two.

Some days will be tiny — fixing one bug, figuring out a Swift thing that caught me offguard.

And some days might just be “today I didn’t get anything done, but I’m still here.”

Because that’s what building in public really is.

## What’s Next

Today, I finalized the PRD — the product requirements doc — which lays out the idea, user flow, and core features.

Next, I’ll start working on the onboarding screens and basic navigation. I’ll probably stumble a lot. But that’s kind of the point.

Thanks for reading.

Let’s see where this goes.

---

## Product Requirements for *Checklistd* iOS App

```txt
Product Name: Checklistd: To-Do App for Job Searching

1. Overview

Checklistd is a minimalist, black-and-white productivity app designed specifically for job seekers.

It offers focused checklist functionality, a job application tracker, and motivational progress tracking — all streamlined to reduce friction and keep users consistently moving forward.

2. Target Users

• Job seekers (freshers, experienced professionals, career switchers)
• Career improvers or those passively exploring new opportunities
• Followers from Instagram/YouTube career content

3. Core Value Proposition

Unlike generic to-do apps, Checklistd provides a job-search-specific experience:
• Prebuilt and customizable job search checklists
• Tracker to monitor job applications and follow-ups
• Streaks and daily goals for consistency
• Clean and calming black-and-white UI

4. Key Features & Screens

4.1 Onboarding (3-Step Minimal Flow)

1. Welcome Screen: App name + tagline, CTA: “Get Started”
2. Job Intent Selector: Fresher, Experienced, Switching Careers, Just Exploring (stored via SwiftData)
3. Confirmation Screen: Message + CTA: “Start Organizing”

4.2 Home Dashboard

• Today’s task preview
• Progress summary
• Motivational quote or weekly streaks

4.3 Daily Checklist

• Task list with checkmarks
• Swipe to complete or delete
• Add custom task
• Tap to add notes or due date

4.4 Job Application Tracker

• List view with job title, company, date, status
• Status: Saved, Applied, Interviewing, Offer, Rejected
• Add/edit job entries

4.5 Job Detail View

• Company name, role, JD link
• Date applied, notes, follow-up toggle

4.6 Checklist Templates

• Prebuilt templates (Interview Prep, Networking, etc.)
• Import with one tap, create custom templates

4.7 Settings

• Edit user intent type, toggle reminders
• Export job history (CSV) [Future feature]

4.8 Streaks / Progress (Optional Phase 2)

• Streak calendar, stats (apps/week, interview rate)

5. Data Models (SwiftData)

ChecklistItem: id, title, isCompleted, date, category, notes
JobApplication: id, companyName, roleTitle, status, dateApplied, link, notes
UserType: id, type (Fresher, Experienced, Switching, Exploring)
ChecklistTemplate (optional): id, title, items

6. Design & Style

• Black-and-white only
• Flat icons, no shadows
• Rounded corners, clean sans-serif font
• Calm, open layout with large tap targets

7. Stretch Goals

• AI resume tips
• Interview prep timers
• Application success analytics
• Community checklists and sharing

8. Tech Stack

• SwiftUI, SwiftData
• Notifications framework (reminders)

9. Next Steps

• Define file structure and navigation
• Build onboarding flow
• Implement daily checklist + job tracker MVP
• Match minimalist aesthetic
• Soft launch to followers
```

