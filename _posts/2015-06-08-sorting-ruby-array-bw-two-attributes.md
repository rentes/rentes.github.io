---
layout: post
title:  "Sorting a Ruby Array by two attributes"
date:   2015-06-08 12:43
author: Miguel Rentes
comments: true
---

If you ever need to sort a Ruby array of objects by two of its attributes, very much like using an SQL statement with the Order By keyword: 

```sql
SELECT * from <Table> ORDER BY column1, column2
```

you can get the same results in Ruby with the simple code:

```ruby
array.sort! do |a, b|
    comp = (a.attribute1 <=> b.attribute1)
    if comp.zero?
        a.attribute2 <=> b.attribute2
	end
	comp	
end
```

In this example, array is an array of objects containing several attributes and the sort method matches any two objects on the array, checking first if they have the same *attribute1* attribute. If they are the same, hence resulting in a comparison equal to zero, then the sort is done by the *attribute2*. Hence, we get the "ORDER BY" functionality.

We can even had another sorting criteria, if the two objects have different *attribute1* values:

```ruby
array.sort do |a, b|
    comp = (a.attribute1 <=> b.attribute1)
    if comp.zero?
        a.attribute2 <=> b.attribute2
	else
	    a.attribute3 <=> b.attribute3
    end
	comp
end
```

As a concrete example, imagine we have an array of Bug objects with the following states:

```ruby
irb(main):001:0> class Bug
irb(main):002:1> attr_accessor :status_id, :id, :subject
irb(main):003:1> def initialize status, id, subject
irb(main):004:2> @status_id = status
irb(main):005:2> @id = id
irb(main):006:2> @subject = subject
irb(main):007:2> end
irb(main):008:1> end
=> :initialize
irb(main):009:0> array = [Bug.new(5, 13942, "Crash of component A"), Bug.new(5, 14563, "A nasty bug"), Bug.new(2, 12031, "Another nasty bug found"), Bug.new(2, 57786, "Implement TDD on the code"), Bug.new(1, 987, "Read all about Ruby code")]
=> [#<Bug:0x000000021e50a8 @status_id=5, @id=13942, @subject="Crash of component A">, #<Bug:0x000000021e4fe0 @status_id=5, @id=14563, @subject="A nasty bug">, #<Bug:0x000000021e4f40 @status_id=2, @id=12031, @subject="Another nasty bug found">, #<Bug:0x000000021e4ec8 @status_id=2, @id=57786, @subject="Implement TDD on the code">, #<Bug:0x000000021e4e78 @status_id=1, @id=987, @subject="Read all about Ruby code">]
```

As you can see, our array is at the moment with the following objects:

```ruby
[
 #<Bug:0x000000021e50a8 @status_id=5, @id=13942, @subject="Crash of component A">,
 #<Bug:0x000000021e4fe0 @status_id=5, @id=14563, @subject="A nasty bug">,
 #<Bug:0x000000021e4f40 @status_id=2, @id=12031, @subject="Another nasty bug found">,
 #<Bug:0x000000021e4ec8 @status_id=2, @id=57786, @subject="Implement TDD on the code">,
 #<Bug:0x000000021e4e78 @status_id=1, @id=987, @subject="Read all about Ruby code">
]
```

So let's implement our sorting and see how the array gets sorted:

```ruby
irb(main):010:0> array.sort do |a, b|
irb(main):011:1* comp = (a.status_id <=> b.status_id)
irb(main):012:1> if comp.zero?
irb(main):013:2> a.id <=> b.id
irb(main):014:2> end
irb(main):015:1> comp
irb(main):016:1> end
=> [#<Bug:0x000000021e4e78 @status_id=1, @id=987, @subject="Read all about Ruby code">, #<Bug:0x000000021e4f40 @status_id=2, @id=12031, @subject="Another nasty bug found">, #<Bug:0x000000021e4ec8 @status_id=2, @id=57786, @subject="Implement TDD on the code">, #<Bug:0x000000021e50a8 @status_id=5, @id=13942, @subject="Crash of component A">, #<Bug:0x000000021e4fe0 @status_id=5, @id=14563, @subject="A nasty bug">]
```

As you can see, the array is now sorted like this:

```ruby
[
 #<Bug:0x000000021e4e78 @status_id=1, @id=987, @subject="Read all about Ruby code">,
 #<Bug:0x000000021e4f40 @status_id=2, @id=12031, @subject="Another nasty bug found">,
 #<Bug:0x000000021e4ec8 @status_id=2, @id=57786, @subject="Implement TDD on the code">,
 #<Bug:0x000000021e50a8 @status_id=5, @id=13942, @subject="Crash of component A">,
 #<Bug:0x000000021e4fe0 @status_id=5, @id=14563, @subject="A nasty bug">
]
```

If you want to make the sorting effects stored into the array, replace ```sort``` with ```sort!```.

For larger objects when comparisons can become relatively expensive, an alternative to this code is using the ```sort_by``` method, which has performance improvements over the traditional ```sort```. The above code then simply becomes:

```ruby
irb(main):017:0> array.sort_by do |x|
irb(main):018:1* [x.status_id, x.id]
irb(main):019:1> end
```

Again, if you want to make the sorting stored into the array, replace ```sort_by``` with ```sort_by!```.

I hope this post has helped you in learning how to sort an array of objects using two attributes from the objects contained in the array. To sum everything up, I share with you the links that served as an inspiration for this post.

* [Method of the Month 1: Ruby's sort vs. sort_by](http://brandon.dimcheff.com/2009/11/18/rubys-sort-vs-sort-by.html)
* [sort and sort_by methods for Arrays in Ruby's Core Documentation](http://ruby-doc.org/core-2.2.0/Array.html#method-i-sort)
* [Sort array by two attributes? (like sql "order by A, B")](https://www.ruby-forum.com/topic/162413)


Until next time, have a lot of coding fun!

