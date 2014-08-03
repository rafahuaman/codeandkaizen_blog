---
layout: post
title: "Working through two Rails tutorials"
date: 2014-03-01 22:16
comments: true
categories: [blog, web dev, Ruby, Rails, Agile Web Development with Rails 4, Hartl] 
---

### After the first one



A few months ago I completed the Hartl’s rails tutorial. I bragged a little about it on this post right [here](blog/2013/12/24/hartls-rails-tutorial-im-done/).  I felt really good about it; however, I noticed that once I was done with the book I could hardly remember many of the details I had learned at the beginning. I realized that I had a better intuition about how it all went together and was very familiar with the Rails environment but I still had look up a lot of things and go back in the book to remember how to do specific things. All things considered, I couldn't expect more; I was starting out and that had been my first venture with Rails. I considered it successful.

One of the things that made it a succes for me was that the project demystified Rails for me. After I was done, Rails (and full stack web development) didn't seem as scary and on the way I picked up new technologies and techniques. Even though I wasn't a Rails guru, I was pretty confident I could get many things done as long as I looked them up.  

### Now what?

Long before I had finished the Hartl tutorial I had already decided I was going to work on a [second book](http://pragprog.com/book/rails4/agile-web-development-with-rails-4) in pretty much the same way. I wanted the second tutorial to offer a different perspective and at the same time reinforce the things I had learned with the first book. I have to say this worked very well. Not only did working through a second book accomplished what I was looking for but it also showed me my strong and weak areas. Basically if while reading the second book I found myself nodding and thinking *"Yes, this makes sense"*, then I had a good grasp on the concept; on the other hand, if I read something and with a blank stare, thinking *"I have never heard of this before"*, then it was something to which I needed to pay extra attention. 


### Comparing the tutorials

With that little introduction out of the way I will proceed to comment on the differences that jumped out at me.

*Disclaimer*: I have to add the disclaimer that I only worked through part 1 and 2 of the "Agile Web Development with Rails 4" (AWDWR4) these sections essentially walk you through building a sample application like the Hartl tutorial; part 3 of the book covers additional Rails topics more in-depth does not included *code-along* exercises.

#### Testing

One of the main differences I noticed was that the Hartl tutorial is more focused on testing than AWDWR4. Hartl's [red-green-refactor cycle](http://en.wikipedia.org/wiki/Test-driven_development) is present throughout the book and he spends a more time on using tools that help with testing. Hartl works with Rspec and FactoryGirl as opposed to AWDWR4 which uses the Rails out-of-the-box test solution as well as Fixtures to accomplish the same things. AWDWR4 does not test everything and only tests a few big changes and walks the user through one test user story. 

I think Hartl's book does a better job with testing especially since beginners should be exposed to good practices when discovering Rails. 

#### CSS magic
Hartl's tutorial uses [Bootstrap](http://getbootstrap.com/) whereas AWDWR4 does not. The simple introduction of Bootstrap makes Hartl's tutorial project look better than the AWDWR4 counterpart. AWDWR4 does not focus on looks and it shows; the final project ends up looking like a website from the 90s.  However, in order to get Hartl's project to look nice one has to copy and paste a lot of CSS styling. This felt like cheating. On this regard AWDWR4 feels more honest. AWDWR4 does not fool you into thinking that you will be able to create good-looking websites; that's a different topic completely. However, Hartl introduces his readers to front-end frameworks. This might be enough to let his readers know that such tools exist and are freely available.


#### Scaffolding 

For those who don't know, [scaffolding](http://guides.rubyonrails.org/v3.2.13/getting_started.html#getting-up-and-running-quickly-with-scaffolding) is the Rails feature that automates the creation of a lot of necessary files to enable [CRUD](http://en.wikipedia.org/wiki/Create,_read,_update_and_delete) acctions for your data models. Think about it as a button that says "create engine" when building a car, once you press it a working engine appears in front of you ready to be customized for your needs.

Hartl explains his approach early on in the book. In the demo chapter he shows the users how quickly he can build something by using rails scaffolding. After this he proceeds to build everything manually for the rest of his book. Hartl explains that this automation, although powerful and useful, is not conducive to teaching because the automation ends up doing a lot of things for you that rails developers need to learn in order to work effectively with the framework. 

AWDWR4 uses scaffolding right from the beginning. I agree with Hartl here. If Hartl's tutorial had not explained everything that was going on under the hood before trying AWDWR4, I would have been really lost.


#### Sending Mail and Internationalization
AWDWR4 spends the additional time it gains by not focusing on testing and by using scaffolding on exploring additional features. AWDWR4 will walk you through send mail and internationalization. These were neat topics that will come in handy later. 


### Conclusion

After doing this myself, my advice to all Rails beginners out there would be to take the time to work through two different Rails tutorials. This exercise showed me that there are different ways of working with Rails and several ways to reach the same goal. This is extremely valuable for someone (me) who is starting out and may mistakenly believe that the Hartl way is the only correct way of writing Rails application. 

I met someone at a meetup who recommended working through the Rails tutorial twice. I believe this would is helpful too since many of the chapters that were nebulous when first starting will be suddenly clear and make more sense on the second go. Nevertheless, I feel that working through the same book twice without exposure to other methods may delay the realization that there multiple ways of working with Rails.
