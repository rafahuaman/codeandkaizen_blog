---
layout: post
title: "My Ubuntu Laptop"
date: 2013-10-06 00:39
comments: true
categories: [blog, ubuntu, Ruby, Windows] 
---

Windows Woes
------------
When I started playing with Ruby, I didn't even have it on my laptop. With resources like <a href="http://tryruby.org/">tryruby.org</a> and <a href="http://www.codecademy.com/">Codecademy</a> freely available online I did not need install it until I started building small programs. After I finished the tutorials I installed Ruby on my windows machine and since I wasn’t building any complicated projects, everything was fine.

Eventually I started blogging using <a href="http://octopress.org/">Octopress</a>. That's when I encountered my first issue. I had installed version 2.0 and Octopress requires Ruby 1.9.3. The Internet came to my rescue with <a href="https://github.com/vertiginous/pik">Project Pik</a>. Pik is like <a href="https://rvm.io/">RVM</a> for Windows and it allows you switch between different versions of Ruby. At first this worked well. I was able to use Octopress and deploy the first version of my blog with it. However, I ran into problems when I started <a href="http://ruby.railstutorial.org/">Michael Hartl's Rails Tutorials</a>. I was able to go through the initial sections but I got stuck on the advanced configuration chapters. I kept running into issues and nothing seemed to be working. Worst of all, some things would work in one version of ruby and not on the other one. I did extensive research online but nothing seemed to solve my problems completely. As soon as I finished something, a new error would show up. I was getting increasingly frustrated. Eventually I decided to skip the sections that were giving me trouble.

At this point I was feeling a little defeated by these issues. I was just starting out and I had spent too much time and energy on what seemed like obscure configuration problems. It was about this time when I decided to take all the comments I had seen online about using Mac or Linux over Windows seriously. It seemed that every blog or forum I was visiting while troubleshooting had a common theme: "Use Mac or Linux, it is better". I usually ignore the Mac vs. PC; however, this time my problems giving me a big headache and I was ready to try anything that would help me get back to learning instead of fighting hopeless configuration wars.

The Flight of the Phoenix
-------------------------
About a year ago my college laptop died. I turned it on one day to find the following message: "Imminent Hard Drive Failure. Backup your Data". That was a serious message! My laptop was not messing around. I backed up my data and retired my trusty college PC. I saved it because I knew I could probably use the parts later or replace the hard drive, but I had been thinking about getting a new system and this Hard Drive failure gave me an excuse to get a new one.

In the midst of my configuration issues, I found myself browsing the Apple store website and looking at the cheaper options: $999. ಠ_ಠ That was a lot more than what I was expecting. I liked the idea of having a laptop dedicated to web development but I did not like the price of Macs. At this point I remembered that I still had my old college laptop! All I needed was a new hard drive and a copy of Ubuntu and I could be using a UNIX environment which according to the Internet would solve all my problems. Finding the right parts for my laptop was a little difficult, but one cancelled order and returned hard drive later I had Ubuntu 12.04 running on my old machine!

The Miracle
-----------
Everything was just so much easier. Gems worked right out of the box without much configuration, RVM made installing Ruby a breeze, and the best part was the amount of relevant help I was able to find online. Finding answers for a Windows problem was very tedious, but answers for Linux issues were everywhere. Hooray! Not only were they everywhere but they were also clearly explained. Double Hooray! Whenever I fixed an issue on my windows laptop, the solution seemed so obscure and strange that always seemed like magic. It was the opposite with Linux. Every time I solved an issue on my Ubuntu installation I felt wiser. The online community would not only solve your problem but they would also make sure you understood what was going on and as bonus they would give you a link so that you could learn more about the subject.

Needless to say, I was very happy and thrilled. I was able to go back and redo all the initial chapters of Michael Hartl's tutorial and complete all the advanced configuration sections.


My conclusion
-------------
Developing with Ruby on Windows is not a good idea. Use it if it's your only option; however, trying Linux will definitely save a lot of time spent on troubleshooting.