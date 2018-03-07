---
layout: post
title: "Lessons in Ruby from Exercism.io"
date: 2014-02-05 23:44
comments: true
categories: [blog, web dev, Ruby, Exercism.io, Hash, Enumerable, feedback, collaboration] 
---
##Exercism.io and Patience
When I started my path of personal development I gathered a lot of information on online resources to improve my skills as a programmer. That's when I first learned about [Exercism.io.](http://exercism.io/) It seemed like a popular and useful resource which would introduce feedback to my learning. I bookmarked and archived it; however, I didn't use it right away. I got more involved with the [Hartl Tutorial](http://ruby.railstutorial.org/), the [Agile Web Development with Rails 4](http://pragprog.com/book/rails4/agile-web-development-with-rails-4) book, and a few more [books](http://www.amazon.com/Design-Patterns-Ruby-Russ-Olsen/dp/0321490452). 

My interested got picked again at the [Nickel City Ruby](http://nickelcityruby.com/) conference where I heard a few people raving about how great Exercism.io was. At first nothing interesting happened, I finished the first exercise and was ready to move on. After a couple of days of not getting any feedback simply advanced to the next exercise. This is how my first two exercises went: "finish, wait, no response? Move on". At this point I was wondering what made Exercism.io so special (whatever it was I was not seeing it). 

I finished the third exercise and forgot about it. A week had passed by the time I remembered I should check on my submission. I logged in and lo and behold... I had one feedback comment! It was a suggestion from a kind stranger on how my code could be improved. This suggestion was so good I was immediately excited. It did make my code better. I finally got it! You should Exercism.io a little time until someone gets around to checking your code. 

The following exercises went much better. I waited patiently for some feedback which would eventually arrive and improve my code and teach me more about the Ruby language. 

##My Lessons
###Adding Elements to a Hash of Arrays
In one of the problems I had to implement a class that could classify students based on their grades. The straight forward solution: a hash where the grade is the key and an array of students is the value. Here's the catch: when looking for the students in a grade with no students assigned I should return and empty array ```[]``` instead of ```null```.

Here's my approach:

{% highlight ruby %}
class School
  attr_reader :db

  def initialize
    @db = Hash.new([])
  end

  def add(name, grade)
    @db[grade].empty? ? @db[grade] = [name] : @db[grade] << name
  end

  def grade(grade)
    @db[grade]
  end
end
{% endhighlight %}

I believe this covered the requirements. ```Hash.new([])``` returns a new, empty hash; if this hash is subsequently accessed by a key that doesn’t correspond to a hash entry, the single object ```[]``` will be used for all default values. So if ```@db``` is empty, then ```@db[wibble]``` will return ```[]```. Looking good!

My biggest problem with my implementation was the add method. Even though it is written in one line (only because I am using ternary notation), it is not very readable. I wrote it that way because simply writing ```@db[grade] << name``` did not work. Somebody suggested I use ```@db[grade] += [name]```, but I didn't think it would work (more on this later). Why would that work when ```@db[grade] << name``` did not?

Turns out using ```@db[grade] += [name]``` was definitely the way to go. I ran a few of tests and discovered why ```@db[grade] << [name]``` was not working. I believe ```@db[grade] += [name]``` works as ```@db[grade] = @db[grade] + [name]```. Since I had defined the default value of the ```@db``` hash to be ```[]```, that expression gets interpreted as ```@db[grade] = [] + [name]``` which successfully performs the desired concatenation. This is pretty neat. I hadn't thought of this approach when I first coded this. I opted for the conditional because when I tried doing concatenation with ```@db[grade] << [name]``` I ran into an interesting problem.

The interesting part was finding out why ```@db[grade] << [name]``` was not working. This expression is essentially ```@db[grade].push([name])```. This statement directly modifies the default value for the hash whenever ```@db[grade]``` has not been assigned a value. This was great find! It showed me difference between ```+=``` and ```<<``` as well how default values for a hash work.

My code looked like this in the end:

{% highlight ruby %}
class School
  attr_reader :db

  def initialize
    @db = Hash.new([])
  end

  def add(name, grade)
    @db[grade] += [name]
  end

  def grade(grade)
    @db[grade]
  end
end
{% endhighlight %}
 
###The Powerful Ruby Library
The second problem I had with my code was the sort method for the same exercise. The sort method was supposed to return a hash with the grades and the names of the students in the grade sorted. I had implemented this method in the following way:

{% highlight ruby %}  
def sort
  sorted = {}
  @db.keys.sort.each { |key| sorted[key] = @db[key].sort }
  sorted
end
{% endhighlight %}

This worked but it didn't seem right to me. Ruby is a very powerful language and I have seen pretty clever of ways of solving problems like this one. My solution seemed like a clunky way of doing things. Luckily someone suggested a different approach. This is the final version of the method. One line! Yey!

{% highlight ruby %}  
def sort
   Hash[@db.sort.map { |grade,name| [grade, name.sort] }]
end
{% endhighlight %}

Let's break it down.

* ```Hash#sort``` is a useful method which returns a hash table sorted by its keys. 
* ```Enumerable#map``` is a method that returns a new array with the results of running a block once for every element in the enumerable. In this case I am passing my sorted hash table and getting back an array in which each element looks like this ```[grade, [name1, name2, ..., nameN]]```. Each element is an Array of length = 2 where the first element is the grade and the second element is a sorted array of student names.
* The ```Hash[]``` method returns a hash. In one of its many forms, this method accepts an array of pairs as an argument (i.e. ```[[key1,value1], [key2, value2],...,[keyN, valueN]]```) and creates a hash table. 

Combining all this methods makes it possible to get the full functionality of the sort method implemented in one very readable line.

### Enumerable to the rescue
I learned my third lesson in a different exercise. This exercise was very straightforward. Given two strings count the differences between them at every position. For example, CAT and CAP have a difference of 1. One condition of the problem was to stop the counting at the end of the shorter string. For instance, CATS and CAP have a difference of 1.  Simple enough. This was first attempt.

{% highlight ruby %}  
class Hamming
  def self.compute(base, test)
    hamming_diff = 0
    [base.size,test.size].min.times do  |i| 
      hamming_diff += 1 if base[i] != test[i]
    end
    hamming_diff
  end
end
{% endhighlight %}

This was effective. However, I was able to improve it by using the special features of the Enumerable class pointed out by another user. In Ruby, most methods that take block return an Enumerable if no block is given. Additionally, one can apply the ```Enumerable#count``` method which takes a block as a parameter to determine when to count an item.  Following these insights my final implementation looked like this.

{% highlight ruby %} 
class Hamming
  def self.compute(base, test)
    max_length_to_compare = [base.size,test.size].min
    max_length_to_compare.times.count { |i| base[i] != test[i] } 
  end
end
{% endhighlight %}

The compute method could have been expressed in one line; however, this way the method separates the two main "ideas" in the code: finding the maximum length for the comparison and the counting loop. I believe that separating the ideas makes it into a very readable implementation.


##Conclusion

[Exercism.io](http://exercism.io/) is not meant for you to plough through all the exercises. It is meant for careful review, collaboration, and revision so that you can learn how to write the best code possible. The users in the site will be helpful but you just have to be a little patient and wait for their input.



