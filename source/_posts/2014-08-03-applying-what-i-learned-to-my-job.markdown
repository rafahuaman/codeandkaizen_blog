---
layout: post
title: "Applying what I learned to my job"
date: 2014-05-13 23:00
comments: true
categories: [blog, web dev, ORM, Active Record, Teradata, learning] 
---


I am writing this post because I want to document what I consider one of my biggest victories in this learning journey of mine. Additionally, I want to share how learning something new can impact your job even if they are seemingly unrelated. In this post I will briefly explain how I built a custom [ORM](http://en.wikipedia.org/wiki/Object-relational_mapping) solution for [Teradata](http://www.teradata.com/?LangType=1033) in VB.Net. 


### Legacy and when non-coders code

Recently I was a given control of a project at work. This project was a simple automation tool which read and wrote to a database and accepted user input through a GUI. Pretty standard stuff. It was been written by business analysts who knew how to code a little but had no further interest in software development. The lack of good technical direction allowed for a few bad practices. As a result, some of the things that *got the job done* in beginning did not seem acceptable going forward.

One of the areas in which the tool was noticeably weak was communication with the database. Back when there was only one use-case, the developers did not think it was a big deal to duplicate code when connecting to the DB. After all they were only doing this a handful of times.  This means that for each database interaction the developer was defining a connection string, opening the database connection, defining a query, executing it, iterating through the resulting set, and closing the connection. This is a lot of code for just one query.

### Rails and Research

Not too long ago I finished working through two rails tutorials and started working on my own application (more on that later). Since them I have become very familiar with rails.  Rails introduced me to the concept of [Object Relational Mapping](http://en.wikipedia.org/wiki/Object-relational_mapping). As I became better at Rails and learned more about [Active Record](http://guides.rubyonrails.org/active_record_basics.html) (Rails ORM solution) I appreciated it more.

Armed with my recent knowledge about ORM frameworks I started to research open-source solutions that would work with the database we were using. Teradata is not an open source and it is relatively new; consequently there is not a lot of free stuff out there that supports it. After a couple of hours I came up empty handed. 

This is when I decided I was going to build my own ORM framework. It seemed daunting at first, but  I was going to abstract a lot of the connection code anyway in order to make the code [DRY](http://en.wikipedia.org/wiki/Don't_repeat_yourself). After that abstraction, it seemed that I was only a few steps away from having an ORM. SO I decided to give it shot. 

### My first ORM

So here's what I did. 

* First I put all of the connection handling logic in one class. So this class would be in charge of opening and closing connections.
* Then I built a couple of Agent classes to handle queries and non-queries. They would send the queries to the connections, loop through the results; and return them in a standard format. 

These two things combined pretty much solved my initial problem. Instead of writing out all that connection code I mentioned at first I could write QueryAgent.execute("SELECT * FROM Users") and get a standard Datatable object as a result. All the connection opening and closing would be handled automatically. The hassle of connecting to the databse became a one-liner. This was good start.

* The next thing I did was to start working on an Active Record class. At the same time I worked on a queryBuilder class. 

I based my active records class on my knowledge of Rails. This class handled all the generic [CRUD](http://en.wikipedia.org/wiki/Create,_read,_update_and_delete) functionality for all my models and would make a lot of use of my query and non-query agent classes. Essensiattly the AR class provided an API which turned CRUD actions into SQL statements. For example, *create* would become QueryAgent.execute("Insert into ....").  

My AR class used the queryBuilder class to build all the custom queries it needed in order to be able to support several many tables with different schemas. The QueryBuilder class would differentiate between models using some key variables and build the appropriate queries. In other words it was the QueryBuilder's job to produce "INSERT INTO Users..." and "INSERT INTO Products..." correctly.

### Done and done!

So that's the quick explanation. It took a few days to put all of this together. As an added bonus I built this using TDD so all the functionality of my Active Record class was tested and gave me a lot of confidence in the solution I was implemented. 

I was very proud of this. Building my own ORM solution made me feel more like a real hacker, gave me a lot of confidence in my own abilities, and validated the time and effort I spend learning and practicing outside of work.
