---
title: Farcebook
layout: single
---

This semester (Fall 2011), I took CPSC 330: Object Oriented Analysis and Design.
To illustrate object oriented principles, a large portion of our grade was a semester long group project, in which we were assigned to produce a social networking site.
We went through an entire design cycle, beginning with writing use cases for different features, designing the architecture of the site and producing UML class and sequence diagrams, and finally implementing the site.
This is my post-mortem of the phenomenal learning experience.

## Background

Most of the class was divided into groups of three, however the class size allowed one group of four.
I had three friends in the class, and we fought successfully to be that four person group.
Since our main text for the semester was the famous [_Design Patterns_](http://en.wikipedia.org/wiki/Design_Patterns) we dubbed ourselves "The Gang of Four", and proceeded to annoy everyone in the class with our team spirit.

I initially proposed that we make our site Ultimate Frisbee themed, however only half of the group played, and the ambitions I had for the site were well beyond the scope of one semester.
We settled on Mike's suggestion of "Farcebook", and tried to think of as many funny features to mock the less-loved parts of the [Book of Faces](http://facebook.com).

## Design

The first phase of the project was to produce Use Cases to flesh out how our features would work for actual users.
It went along smoothly, and our professor reassured us that we were not obligated to implement everything we wrote about.

Next, after spending more time studying various design patterns, came the architecture phase.
We struggled for many long nights, hammering out every detail in our UML class diagrams.
Many jokes, arguments and handfuls of junk food later we had a very solid plan.

## Implementation

Finally, the dreaded implementation.
For this class we were using a Java backend and JSPs running on Apache Tomcat, and using subversion for version control.
We had four weeks to get everything up and functioning.
After some initial floudering, we divided up responsibilities in order to work more efficiently.

After cringing at Kevin's first version of the home page I took over the front-end duties by force.
I used [Twitter's Bootstrap CSS framework](http://twitter.github.com/bootstrap) to make things pretty quickly, and sprinkled in a few bits of JQuery to spice things up.
Ross and Mike worked to implement everything we had designed, and Kevin slaved away at making everything persistent.
A note on persistence: we had not taken a databases class before this, so we had only stray bits and pieces of database knowledge.
Given this, and since the focus of the course was more on OO design, we did everything with file IO rather than SQL.
This was extremely unpleasant to do bug-free, and everyone is thankful that Kevin took care of it.

## Demo Day

In lieu of an in class final, our class was holding a demo day for everyones social networks.
In an example of very poor judgement, we decided to implement one final killer feature the night before.

Every entity in Farcebook has a "Dislike" button.
After sending a verification email, we wanted to tie the dislike button to an email server, spamming the profile's owner.
We required an email address during registration, but only verified that it was legit by checking if there was an @ sign.
Ross did some research and starting incorporating the JavaMail library (which none of us had any experience with) into our program.

Predictably, this was more difficult than anticipated.
We finally got it working, tied in to a throw-away GMail account.
Half an hour before our final started, we were running through a final test, tuning the styling and generally making sure everything worked.
Of course, we spammed each others dislike buttons relentlessly.
Ten minutes to go, as we were about to pile into the car, everything started crashing on an email error.
GMail had banned us for spamming!

As we drove to campus, I furiously registered another throw away GMail account on my phone.
We changed the details and recompiled just in time.
Of course, we were banned as soon as our entire class discovered the feature, but it was well worth it.

## Post-Script

I've pulled the source down from our school's servers, deleted all of the svn and JavaMail, and started a github repo.
Starting from [this](https://github.com/heroku/devcenter-embedded-tomcat) code, I've put it up on a free Heroku account.
In conclusion: [farce-book.net](http://farce-book.net) is live!

Things don't persist, so without any other users there isn't much to see or do, but I encourage you to register an account and hopefully chuckle a little.
Every member of the Gang of Four is signed up for a Database class this semester, so maybe somewhere on down the line we can hook it up to a database.

I learned an enormous amount working on this project.
This course took a waterfall design aproach, and while our design was fairly thorough, it still required significant tweaking as we discovered new information during implementation.
I am excited to try out some agile methodology in a course this coming semester, to compare the two.
