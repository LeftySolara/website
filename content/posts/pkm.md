---
title: "Personal Knowledge Management"
description: "A description of my personal knowledgement system"
series: ["Personal Knowledge Management"]
categories: ["productivity"]
tags: ["knowledge management", "productivity", "gtd"]
date: 2022-02-11T21:46:55-05:00
draft: false
---

Recently I've become interested in formalizing my [personal knowledge management](https://en.wikipedia.org/wiki/Personal_knowledge_management) system. Over the years I've tried a number of different methods for gathering and organizing my files, documents, and other various items. The main issue has always been the great deal of time and frustration involved with maintaining everything.

In this post I will give a brief overview of what personal knowledge management is and describe the system I use for this purpose.

## What is Personal Knowledge Management?

Personal Knowledge Management (PKM) is the collection, maintenance, and sharing of knowledge in a person's daily activities. It is a response to the idea that knowledge workers need to be responsible for their own growth and learning.

Basically, it's the process of collecting and documenting everything you know while making it easy to search and share. Think of it as a way of creating your own personal library of information.

## My PKM Solution

### Goals

For me, the most important traits of a good PKM system are cleanliness, searchability, and maintainability. This includes making it easy to store and retrieve information on multiple devices. There must also be a simple way to separate public information (like this blog) from private (bank information, addresses, medical records, etc.).

Essentially, what I need is a system that is:

1. **Easy to maintain**: There should be as little friction as possible when adding, removing, modifying, and moving information. The more work it takes to do any of these things, the less likely I am to actually do it.
2. **Easy to manage in multiple places**: Like most people these days, I have a lot of information stored in various places. This includes my desktop PC, laptop, phone, tablet, and paper notebooks. Being able to organize everything in the same way across devices is extremely useful, as it eliminates the complexity involved with maintaining multiple unique setups. It also helps make file sync much easier.
3. **Searchable**: As more information is stored, it becomes more difficult and time-consuming to manually search through files for the thing I'm looking for. Once a knowledge base reaches a non-trivial size, it can become more work to find things than to use them. There is a balance that can be achieved when the system is set up correctly. For example, in my [public knowledge base](https://wiki.julianneadams.info) it's possible to navigate through sections manually, but it's also possible to get to a specific page quickly by using the search bar.
4. **Well-Organized**: Although I primarily use text search to find things, documents still need to be easy to find manually for those times when I'm using paper or a device with poor search functionality. This also makes it easier to see a complete picture of what's being stored.
5. **Independent of the tools used to maintain it**: In the past there have been times where I've had to uproot my entire system and re-create it somewhere else, all because the software I was using had been discontinued or changed their usage policies. To prevent this from happening again, I've begun keeping all my notes in plain [Markdown](https://en.wikipedia.org/wiki/Markdown) files.

### What I Keep

Theres a variety of things I keep in my PKM system, including:

- Notes
- Documents (PDFs, spreadsheets, paper records, etc.)
- Bookmarks
- "Read later" lists
- Todo lists
- Calendars
- Contacts

Basically, if it's something I'll need to reference in the future or part of a task that takes more than five minutes, then it goes into the system.

### How the System Works

My current system is a modified version of the [PARA Method](https://fortelabs.co/blog/para/), which I call the IPCAR method.

In the original PARA method, all information is stored in four top-level categories: _projects_, _areas of responsibility_, _resources_, and _archives_. I've taken that idea and expanded upon it to fit my own needs.

#### Top-Level Categories

These categories are implemented as directories on my PC and as folders in my filing cabinet.

##### Inbox

This is where things are stored until I have time to sort them into the other categories.

I'm often in situations in which I need to jot something down quickly and don't have time to worry about where to file it. For example, if I'm at the grocery store and suddenly have an idea. Having one central place to store unsorted information makes it easy to process everything during my [daily, weekly, and monthly reviews](https://carl-pullein.medium.com/why-the-daily-mini-review-is-so-important-163d3a8a40b). I also practice [rapid logging](https://help.bulletjournal.com/article/7-rappid-logging) and most of those notes end up in my inbox.

I primarily use my [bullet journal](https://bulletjournal.com/) for this, but also have a note-taking app on my phone for times that my journal isn't accessible. The app is able to access all of my sorted and unsorted notes.

##### Projects

This is where all information for my active projects is stored. I use the [GTD definition](https://gettingthingsdone.com/2017/05/managing-projects-with-gtd/) of "project", which is any task that takes more than one action step to complete.

##### Codex

This is my [public knowledge base](https://wiki.julianneadams.info). It's where I keep any acquired knowledge that I don't consider to be private. It began as a place to [learn in public](https://www.swyx.io/learn-in-public/) and eventually grew info something more, taking inspiration from people such as [Nikita Voloboev](https://wiki.nikitavoloboev.xyz/).

##### Areas of Responsibility

This one is identical to the original PARA version. An Area of Responsibility is a "sphere of activity with a standard to be maintained over time." Basically, it's things that I'm responsible for for an indefinite amount of time. Examples include my home, finances, health, etc.

##### Records

This is also identical to its PARA version. It's a place where inactive things from the other categories are stored. For example, when I finish a project I move those files from the "project" category to here.

I renamed this from "archive" to "records" because I keep all these categories as directories on my PC and wanted to maintain one-letter tab completion in my terminal.

#### Tools and Implementation

I use a number of different tools for maintaining my IPCAR system.

For task management I practice the [GTD methodology](https://gettingthingsdone.com/) and use [taskwarrior](https://taskwarrior.org/) to manage my task list. I also use [timewarrior](https://timewarrior.net/) for time tracking.

For note-taking I use [Visual Studio Code](https://code.visualstudio.com/) on my computers and [Markor](https://github.com/gsantner/markor) on mobile. All of my notes are stored as Markdown files on my computers/phone, which satisfies my goal of avoiding dependency on specific software. I also keep physical notebooks for various projects.

For file synchronization I use [Syncthing](https://syncthing.net/).

My calendar and contacts are stored on a CalDAV/CardDAV server which I sync to my email client (on PC) and calendar app (on mobile).

## Summary

Using the IPCAR method, I'm able to organize all of my life's information in a way that is easy to store and easy to retrieve.

If you decide to use your own version of the IPCAR method, feel free to shoot me an email and let me know. I'd be interested in hearing how well (or poorly) it works for other people.
