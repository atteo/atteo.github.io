---
layout: post
title: Evo Class Index
author: Sławek
---

Evo Class Index is much quicker alternative to every run-time annotation scanning library like [Reflections](http://code.google.com/p/reflections) or [Scannotations](http://scannotation.sourceforge.net/).

Evo Class Index is an annotation processor which at compile-time generates an index of classes implementing given interface, classes annotated by given annotation or placed in a common package.

Java 6 and above automatically [discovers](http://www.jcp.org/en/jsr/detail?id=269) the processor when put on the classpath and executes it during compilation. Download [evo-classindex](http://search.maven.org/remotecontent?filepath=org/atteo/evo-classindex/1.0/evo-classindex-1.0.jar) jar file (also requires [Guava](http://code.google.com/p/guava-libraries/)) or simply put the following dependency in Maven POM file:

{% highlight xml %}
<dependency>
    <groupid>org.atteo</groupid>
    <artifactid>evo-classindex</artifactid>
    <version>1.0</version>
</dependency>
{% endhighlight %}

There are two annotations which trigger the indexing:

* [@IndexSubclasses](http://www.atteo.org/static/evo-framework/apidocs/org/atteo/evo/classindex/IndexSubclasses.html) when placed on interface makes an index of all classes implementing the interface, when placed on class makes an index of its subclasses and finally when placed in package-info.java it creates an index of all classes in that package.

* [@IndexAnnotated](http://www.atteo.org/static/evo-framework/apidocs/org/atteo/evo/classindex/IndexAnnotated.html) when placed on an annotation makes an index of all classes marked with that annotation.

To access the index at run-time use static methods of [ClassIndex](http://www.atteo.org/static/evo-framework/apidocs/org/atteo/evo/classindex/ClassIndex.html) class.

Example:

{% highlight java %}
@IndexAnnotated
public @interface Entity {
}

@Entity
public class Car {
}

...

for (Class<?> klass : ClassIndex.getAnnotated(Entity.class)) {
    System.out.println(klass.getName());
}
{% endhighlight %}

For subclasses of the given class the index file name and format is compatible with what [ServiceLoader](http://docs.oracle.com/javase/7/docs/api/java/util/ServiceLoader.html) expects. Keep in mind that ServiceLoader also requires for the classes to have zero-argument default constructor.

For classes inside given package the index file is named "jaxb.index", it is located inside the package folder and it's format is compatible with what [JAXBContext.newInstance(String)](http://docs.oracle.com/javase/7/docs/api/javax/xml/bind/JAXBContext.html#newInstance(java.lang.String)) expects.

Links:

* [Source code](https://github.com/sentinelt/evo-classindex)
* [Javadoc](http://www.atteo.org/static/evo-classindex/apidocs/index.html)
* [Bugs](https://github.com/sentinelt/evo-classindex/issues)
* License: [Apache License](http://www.apache.org/licenses/LICENSE-2.0.html)
