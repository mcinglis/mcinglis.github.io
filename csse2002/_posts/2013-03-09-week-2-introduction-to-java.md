---
layout: default
title: 'Week 2: Introduction to Java'
---

**Update:** [here are my solutions](https://github.com/{{ site.author.github }}/csse2002/tree/master/2013S1/week2) to this week's tutorial questions, and to (some of) my prac challenge. Please note that my solutions aren't authoritative about the course; don't take any of this code to be representative of the content of CSSE2002 in any way. That said, you're more than welcome to contact me if you have questions about this code. Cheers!

The extra problems I gave out this week were taken from the book [Cracking the Coding Interview](https://www.google.com.au/search?q=cracking+the+coding+interview) by [Gayle McDowell](http://www.technologywoman.com/). You can view [Gayle's given solutions](https://code.google.com/p/ctci/source/browse/#svn%2Ftrunk%2FJava%2FChapter%201) to these problems (and find more problems). I don't think the book's solutions are very good. For example, the book's solutions for the problems I gave won't work for unicode characters. However, reading bad code, and understanding why it's bad, is a great way to learn.

---

I ran out of time in both tutorials this week. Sorry about that; I'll try to time things better next week.

I didn't really get to cover static methods or access modifiers. See these links below to read up on those topics and others.

He's some more practice methods to implement (try to do them on paper first!):

* `boolean isUniqueChars(String string)` that returns true if the string contains only unique characters, and false otherwise.
* `void removeDuplicates(char[] chars)` that removes all duplicate characters in `chars`, but retains their ordering
* `boolean areAnagrams(String s1, String s2)` that returns true if the strings are anagrams of one another, and false otherwise

## Links

* [The Java Tutorials](http://docs.oracle.com/javase/tutorial/)
  * [Object-Oriented Programming](http://docs.oracle.com/javase/tutorial/java/concepts/index.html)
  * [Java Language Basics](http://docs.oracle.com/javase/tutorial/java/nutsandbolts/index.html)
  * [Understanding Instance and Class Members](http://docs.oracle.com/javase/tutorial/java/javaOO/classvars.html): also includes details about the `static` keyword
    * Suppose all the methods we wrote in the tutorials were put in a class called `Utility`. Do you think those methods should be declared as `static`? Why or why not?
  * [Controlling Access](http://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html): details about access modifiers like `public` and `private`
    * What access level do you think we should give the methods we wrote in tutorials? (supposing they were in a `Utility` class)
* [Naming conventions in Java](http://www.oracle.com/technetwork/java/javase/documentation/codeconventions-135099.html#367): the Java style conventions as described in the lectures
* [Java virtual machine](http://en.wikipedia.org/wiki/Java_virtual_machine): aka the JVM; how might this relate to Python?
  * [List of JVM languages](http://en.wikipedia.org/wiki/List_of_JVM_languages)
* [Strong typing](http://en.wikipedia.org/wiki/Strong_typing): static typing versus dynamic typing

## Blog posts

* [Programming is an Art](http://ruben.verborgh.org/blog/2013/02/21/programming-is-an-art/): the importance of understanding problems and programming well
* [The Apprentice Programmer](http://tobi.lutke.com/the-apprentice-programmer): why experience is important

