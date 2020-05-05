---
layout: page
permalink: /guidance/interns-accepted/
title: Advice for interns accepted for GSoC and Outreachy
---

First of all, welcome to InterMine! We're excited to have you working with us this year.

You should go through the GSoC or Outreachy guide based on which program you are selected in.
We'll try to generally adhere to the [Google Manuals](https://developers.google.com/open-source/gsoc/resources/guide) and [Outreachy Internship Guide](https://www.outreachy.org/docs/internship/) to avoid repetition, but here are a few InterMine-specific guidelines which apply for both Google Summer of Code and Outreachy.

## Communication

You'll establish a personal rhythm with your mentor, but please bear the following points in mind:

### Chat

You can come hang at [chat.intermine.org](http://chat.intermine.org) in the various project and outreachy channels, and feel free to ask for help in #support - but remember to make tickets or send emails for any big bugs or design decisions, as chat logs are transient.

For Outreachy, every two weeks, Outreachy interns, mentors, and alums will have an informal chat on the private Outreachy Zulip chat server. The goal of these chats is to encourage the interns to connect with each other. Read more about it [here](https://www.outreachy.org/docs/internship/#chats).

### Videoconferencing

Most of our students met via videoconferencing software, e.g. Skype, once every one or two weeks. You may need to meet more (or less!) often throughout the project life cycle.

## Writing code

### Quality

All code must be to a high standard, documented and well-commented, and accompanied by a unit test (where applicable).

### Source Control

We use GitHub for our source control, with a [Git Flow](http://nvie.com/posts/a-successful-git-branching-model/)-like branching model. New work is done in personal forked repo branches,  periodically merged into the upstream dev branch when it appears stable.  master contains only stable releases merged from dev.

You should follow a similar model - treat `github.com/intermine/yourproject` as upstream and work on a branch your own fork, i.e. `github.com/yourusername/yourproject`, merging (or PRing for existing projects) periodically. Remember, pushed commits (to your own repo or InterMine's) prove you're alive and working on the project! ;)

We'll fork your repo so there will always be an InterMine upstream.

### Licence

If you're starting a brand new project, think about what **licence** you'd like.  It needs to be open source, obviously, but so long as it's a permissive open source licence like Apache, MIT, BSD, or LGPL, we'll probably be happy. Discuss it with your mentor before committing to a licence.

## Project Management

1. It's okay not to use the workplan from your proposal, but you and your mentor will need to agree to any changes.
2. You do need a workplan! Make sure you and your mentor have a good idea of what the deliverables are.
3. You'll want to schedule regular meetings with your mentor.

### Time commitment / Missed days

From the [Google Manual](https://developers.google.com/open-source/gsoc/resources/guide):


>GSoC needs an investment of about 30 hours a week. If you know in advance that you’ll need to take a couple of days of vacation/break during the Summer of Code, you should communicate that with your mentor beforehand and plan to make up for lost days.

From the [Outreachy Internship Guide](https://www.outreachy.org/docs/internship/)

>You should dedicate 40 hours per week to your project for at least 12 weeks of the Outreachy internship's 13 week duration. Please let your mentor know if you are going on a vacation and/or are sick due to which you cannot work on the project for a short period of time.

>Rarely, interns work less than full-time, or cannot work for all 12 weeks. In that case, interns will need to arrange an internship extension with their mentor. Internships cannot be extended for more than 5 weeks.

If you're affected by COVID-19 and have exams or other things going on, reducing your hours is fine, but always make sure your mentors know what to expect. 

## Outreach

We'd love to host blog posts about yourself, the work you're planning to do, or work you have done. Equally, if you're tweeting or blogging on a personal blog and would like us to link to it / mention you / etc., poke your mentor and we'll give you a shout-out.

For Outreachy, Interns are required to blog every two weeks about their internship. Read more about it [here](https://www.outreachy.org/docs/internship/#blog).

## Final Report

Each student/intern will present their project at the end of August at the InterMine Community Call - a friendly teleconference call attended by the InterMine community -- developers and biologists who use InterMine. The presentation will be limited to 5 minutes with a short time available for discussion after. Ideally this will be a live demonstration of your project but can be slides or video demo instead. 

Each student will also write up their project. This will take the form of a short blog post with the following sections:

* Summary of project goals 
  * Briefly restate what was in your project proposal.
* Summary of project achievements
  * What did you achieve?
  * Screenshots and code snippets are a good idea!
  * Acceptable to point to your other blog posts.
  * Link to final tool, GitHub URL etc.
* Self assessment 
  * What could you have done better? Lessons learned?
  * What are you particularly proud of?
* Future work
  * If you could work on your project longer, what features would you like to see added?
  * What's left to do?

This blog post will be "permanent" and for GSoC will be used to submit to Google as your work product.
