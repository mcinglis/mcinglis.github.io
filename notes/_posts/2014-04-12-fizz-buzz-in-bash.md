---
layout: default
title: FizzBuzz in Bash
updated: '2014-04-12T00:00:01-07:00'
tags: ['code', 'bash']
---

``` bash
limit=$1
for i in $( seq 1 $limit ); do
    if (( i % 15 == 0 )); then
        echo "FizzBuzz"
    elif (( i % 3 == 0 )); then
        echo "Fizz"
    elif (( i % 5 == 0 )); then
        echo "Buzz"
    else
        echo "$i"
    fi
done
```

Quite readable, no?

The use of `(( ))` alone in the `if` expressions is novel to me, as is the `==
0` and permitted whitespace. [Other examples](http://rosettacode.org/wiki/FizzBuzz#bash) on the Internet use something like:

``` bash
if [ $((i%5)) -eq 0 ]; then
```

