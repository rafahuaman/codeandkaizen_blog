---
layout: post
title: "Ruby and the Koans"
date: 2013-09-19 23:26
comments: true
categories: [blog, web dev, Ruby, Ruby Koans, Koans, Neo Innovation]
---

After finishing CodeAcademy's Web Fundamentals track I immediately started the Ruby track. I knew I wanted to go with Ruby because I had already done plenty of research on the technologies I needed to learn in order to become a web developer. I had used Ruby in the past for a very simple Ride Sharing web application I built while at school; however, I used it simply as a means to work with rails and setup the application quickly. During my student time this was OK; however, now that I have made a serious choice about becoming a web developer I need to master it.
The authors of the book <a href ="http://www.amazon.com/Apprenticeship-Patterns-Guidance-Aspiring-Craftsman/dp/0596518382/ref=sr_1_1?s=books&ie=UTF8&qid=1379649530&sr=1-1">Apprenticeship Patterns</a> point out that "It is important that you carefully weigh the options (between programming languages), as this is the foundation upon which your early career will be built". I have chosen Ruby. I will immerse myself in it, play with it in my free time, solve puzzles and read the documentation until I know it all. It will be a long road but I am ready to take the first steps. 
The Ruby track offered by <a href="codecademy.com">CodeAcademy</a> was very good. It was very simple and easy to understand. It even had a few "projects" to apply the concepts learned. The sections build on each other and it is easy to go back and review previous concepts and exercises in case you forget something along the way. The Ruby track can be finished very quickly since it just a beginner's course.  
My conclusion after CodeAcademy's Ruby Track:
<ul>
<li>This is definitely a beginner's course.</li>
<li>After I was done I felt that I even though I could write classes, methods, procs, lambdas, and loops, there was still a lot to learn.</li> 
</ul>
My initial thoughts on Ruby:
<ul>
<li>I like it.</li> 
<li>It offers a lot of flexibility (There's usually more than one way to do one thing in Ruby)</li>
<li>Ruby offers a few interesting methods and features like "each", the flexible way to write conditions, and passing blocks.</li>
<li>It's very easy to work with hashes.</li>
</ul>

<h2>Achieving Zen with the Ruby Koans </h2>
"If a test runs in the forest, and no one is there to see it. Does it pass?"

OK that's enough for my attempts at programming/Zen puns.

After I finished CodeAcademy's Ruby track I felt that there was a lot more I needed to learn about the language. The CodeAcademy tutorial is definitely a beginner's guide. It's meant to get you started, and walk you through the concepts but it does not go deeper. It doesn't even walk the users through installing Ruby in their machines. 

This bothered me a lot. I felt that had I learned all the Ruby basics but I couldn't do much with them yet. I continued to feel this way until I reached the end of chapter 4 in <a href="http://ruby.railstutorial.org/">Michel Hartl's Rails tutorial</a>  (I will discuss my adventures with rails later). Hidden in the exercise section at the end of chapter four I found the best resource to help me learn ruby to date: <a href="http://rubykoans.com/">The Ruby Koans</a>.

The Ruby Koans brought to you by the nice folks at <a href="http://www.neo.com/">Neo Innovation</a> are a way to learn Ruby through testing. The Koans are structured as a series of exercises. Each exercise includes one or more tests the user needs to make pass. Each time the user runs the Koans, the program shows the first failed test in the terminal. The user then has to find the file and the specific test that is failing in order to fix it. 

The user is not testing a big program in these exercises. The user is testing Ruby! Here is an example of a test in the Koans:
 
This test fails and the user has to fill replace "__" with the expected output

{% codeblock Failing Test lang:ruby %}
def test_creating_arrays
  empty_array = Array.new
  assert_equal __, empty_array.class
  assert_equal __, empty_array.size
end
{% endcodeblock %}
  
These changes will make the tests pass: 

{% codeblock Passing Test lang:ruby %}  
def test_creating_arrays
  empty_array = Array.new
  assert_equal Array, empty_array.class
  assert_equal 0, empty_array.size
end
{% endcodeblock %}


There are basically no hints or answer sheets (you can find solved Koans in <a href="https://github.com/">Github</a>, but why ruin these amazing exercises? This way the user is forced to think about the exercises and internalize the concepts with each test. 

Another reason I liked the Koans is that they emphasize testing. As you advance you will find small projects and bigger exercises to work one that involve more coding than just replacing words in the text. I got so used to testing by this point that I used <a href="http://en.wikipedia.org/wiki/Test-driven_development">TDD</a> in the projects and even in the <a href="http://en.wikipedia.org/wiki/Farkle">Farkle</a> game at the end. 

After finishing the Koans I definitely felt more adept in Ruby and was more confident in my abilities. I would recommend this style of learning to anyone that wants to learn Ruby.
