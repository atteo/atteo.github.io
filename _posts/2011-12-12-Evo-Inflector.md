---
layout: post
title: Evo Inflector
author: Sławek
---


Inflector
English words pluralizator

Evo Inflector implements English pluralization algorithm based on Damian Conway's paper "An Algorithmic Approach to English Pluralization".

The tests performed (December 2011) based on data from Wiktionary show perfect results for 1000 basic words and 70% of corrects answers for the entire Wiktionary set of more than 100000 words.
{% highlight java %}
Words checked: 108774 (979 basic words)
Correct: 69.92112% (100.0% basic words)
{% endhighlight %}
(If you are curious this test is part of the unit tests)

Usage:
{% highlight java %}
    System.out.println(English.plural("word"));
{% endhighlight %}
will print "words".
You can download the library from here or use the following Maven dependency:

{% highlight xml %}
<dependency>
    <groupid>org.atteo</groupid>
    <artifactid>evo-inflector</artifactid>
    <version>1.0.1</version>
</dependency>
{% endhighlight %}

Links:
* [Source code](https://github.com/atteo/evo-inflector)
* [Javadoc](http://www.atteo.org/static/evo-inflector/apidocs/index.html)
* [License: Apache License](http://www.apache.org/licenses/LICENSE-2.0.html)

