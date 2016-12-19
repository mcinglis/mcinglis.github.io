---
layout: default
title: 'Week 9: Scanning and Assignment 2'
updated: '2013-05-02T12:30:00+10:00'
---

In class today, after talking about assignment 2, we used `Scanner` to answer some questions we had about [park data](https://github.com/{{ site.author.github }}/csse2002/blob/master/2013S1/week9/data/) from [data.brisbane.qld.gov.au](http://data.brisbane.qld.gov.au/). In my first tutorial, we wrote a program that would tell us all the playgrounds in a given suburb: [`SuburbPlaygrounds.java`](https://github.com/{{ site.author.github }}/csse2002/blob/master/2013S1/week9/SuburbPlaygrounds.java). In my second tutorial, we wrote a program that would tell us the closest park to some given coordinates: [`ClosestPark.java`](https://github.com/{{ site.author.github }}/csse2002/blob/master/2013S1/week9/ClosestPark.java).

Maybe everyone already knows about them, but the Eclipse Shortcuts of the Week were: `Ctrl+Left/Right` to jump between words, `Shift+Arrow Keys` to select stuff, combining `Ctrl+Shift` for great success, and using `Ctrl+Delete` or `Ctrl+Backspace` to offset RSI. These shortcuts work in most programs, actually.

## Assignment 2

**Update (May 5)**: Some general tips:

* Make sure you're doing `Ctrl+Shift+F` regularly - but checking what it's done. It's not infallible.
* Variable names like `listOfSomethings` when its type is `List` should just be called `somethings` (almost always a plural).
* If you are adding a private class: classes are always named as [nouns, not verbs](http://steve-yegge.blogspot.com.au/2006/03/execution-in-kingdom-of-nouns.html).
* `Iterator` variables are usually named something like `appleIter`.
* When adding helper methods, take heed of the advice in this blog post: [A Responsible Programmer](http://anders.janmyr.com/2013/04/a-responsible-programmer.html), specifically, the "separate commands from queries" bit. Try to minimize side-effects in your functions: they're bug-prone and make code harder to read. In the case of using a private helper class, rather than having methods that assign instance variables somewhere within them, you could try to make it so that every instance variable is only assigned in the constructor, in plain view of people reading the code.

**Update (May 4)**: [`Student.java`](https://github.com/{{ site.author.github }}/csse2002/blob/master/2013S1/week9/Student.java) is a demonstration of how you can abstract a complicated algorithm into its own class. This helps you avoid the problem of helper methods with loads of parameters. It also helps prevent polluting the namespace of a class with helper methods or instance variables for an algorithm. You might find this useful for the assignment. You almost definitely won't get marked down if you don't do this yourself, but if you care about best practice, you might like to do this.

**Update (May 4)**: You don't need to check the preconditions in your implementations. The preconditions are the client's responsibility, and if they violate that, you don't promise anything.

**Update (May 3)**: I posted this link on [Iterators and Iterables](http://blog.dreasgrech.com/2010/03/javas-iterators-and-iterables.html) in Java in week 6 to help with assignment 1, but some students may find it helpful for assignment 2, too.

**Update (May 3)**: when naming the variables in the algorithm, take heed of the official [Java naming conventions](http://www.oracle.com/technetwork/java/javase/documentation/codeconventions-135099.html#367):

> Variable names should be short yet meaningful. The choice of a variable name should be mnemonic- that is, designed to indicate to the casual observer the intent of its use. One-character variable names should be avoided except for temporary "throwaway" variables. Common names for temporary variables are `i`, `j`, `k`, `m`, and `n` for integers; `c`, `d`, and `e` for characters.

I would encourage you to write the algorithm in an understandable, maintainable way. How to best do that comes down to judgement: maybe single-letter variable names are best for that, maybe they're not.

Like in assignment 1, if you can think of a short-but-meaningful name for something (and that meaning would be obvious to others reading the code for the first time), then you should prefer that name over, e.g., `x`. Sometimes, though, maybe `x` does best encapsulate what that variable refers to. I use `x` as a variable name quite often.

Writing comments describing the algorithm is a great idea.

**Update**: on understanding ks in the algorithm and worked example:

> To put the definition of ks into words: *ks is the smallest knowledge state for which its probability in first distribution is different to its probability in the second distribution*.
> Keep in mind that a knowledge distribution technically "contains" every possible knowledge state. That is, it will always have a corresponding probability for any given (valid) knowledge state.
> The knowledge distributions shown in the task sheet's worked examples are only represented by their supports: their knowledge states with non-zero probabilities.

**Update**: with regards to sharing tests:

> As part of the software development process that we're practicing, you're meant to write and test the software on your own, individually. It's preferred that you don't exchange tests.

**Update**: on checking `KnowledgeDistribution`s for equivalence:

> To check if two `KnowledgeDistribution`s are "equivalent", please don't add anything to the `KnowledgeDistribution` class itself (e.g. an `equals` method). Your `SpyMaster` class will be tested against a fresh `KnowledgeDistribution`. Add a helper method in `SpyMaster`. Hint: checking for equivalence can be easy.

On adding helper methods:

> Try to trim down methods longer than 40~ lines. That said, don't turn blocks of code into functions if it would mean that new function has to take >3 parameters (even three is pushing it). Turn stuff into functions if:
>
> * they encapsulate something that would benefit from being repeatable
> * their scope is more or less independent (fancy way of saying that the function shouldn't need lots of parameters)
> * you want to test that bit of functionality as an atomic action (and this is generally a good indicator of the above qualities)
> * it would generally help someone who hasn't seen the code before, or even necessarily read the spec, understand what's going on; they shouldn't have to chase multiple mutable parameters down rabbit holes to work out why or what's going on -- you should aspire to to pick your functions so that the "why" and "what" are obvious.

On development approaches:

> One way to [decide what helper methods to add] would be to just put everything you need into `findAdditionalInformants`, and only start putting stuff into methods when you want to test their parts alone, or if you've got it working and can start making it readable and pretty. Sometimes you can get caught up over-abstracting things.

On how the `readInformants` method should behave, and what you might like to test for (going off my understanding of the specification - I don't know what will be tested for marking):

> * Anything that isn't specified as acceptable by the javadoc comment should throw an error.
> * The javadocs aren't clear on handling whitespace at the start of the line. I would recommend you account for it - it shouldn't be terribly difficult, if you're using the right tools.
> * "Separated by one or more whitespaces" can technically refer to any kind of whitespace, so you might like to account for probabilities being separated by spaces or tabs (`'\t'`)
> * It should throw `FileFormatException` if the line contains more than three probabilities.
> * It should throw `FileFormatException` if the values aren't probabilities, e.g., `2/1`.
> * It should throw `FileFormatException` if the values aren't integers, e.g., `1.5/3.0`.
> * Spaces between fractions like `1 /3` should be a format error.
> * The returned list should be in the same order as the lines in the file.
> * It should throw `IOException` if you give it a file name that doesn't exist.
> * Empty files are acceptable, and it should return an empty list in that case.
> * Going off how [Java's documentation](http://docs.oracle.com/javase/7/docs/api/java/lang/Integer.html) and implementation defines a "valid" format of an integer, something like `8/09` should be accepted as a valid input (and should represent `8/9`), but I doubt it will be tested for.

On sharing test cases or code:

> I've asked Larissa if you're allowed to share test code this time around. I think it should be fine to share test cases, though. That means: hold off on sharing actual test files until we hear something from Larissa, but, if you feel like your `findAdditionalInformants` algorithm is solid, and it's working for the given cases, then I think it should be fine to compare results for other possible inputs with other students.
