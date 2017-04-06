# Java9

Collected information about Java 9.  
Work in progress...

## General Resources

* Official
  * [JDK 9](http://openjdk.java.net/projects/jdk9/) project page
  * [JSR 379](http://openjdk.java.net/projects/jdk9/spec/), the Platform Umbrella JSR for Java SE 9


* Community
  * [Eugen Baeldung](https://twitter.com/baeldung)
    * [Java 9 Process API (Improvements)](http://www.baeldung.com/java-9-process-api)
  * [Stephen Colebourne](https://twitter.com/jodastephen)
    * [Java Time (JSR-310) enhancements in Java SE 9](http://blog.joda.org/2017/02/java-time-jsr-310-enhancements-java-9.html)
  * [Nicolai Parlog](https://twitter.com/nipafx)
    * [Java 9 Is Coming!](http://slides.codefx.org/java-9/2017-02-23-voxxed-days-zuerich/index.html#/) (talk at #VDZ17)
    * [Java 9 Additions To Optional](http://blog.codefx.org/java/dev/java-9-optional/)
  * **[Mark.Reinhold](https://twitter.com/mreinhold)**
    * [Alternatives for naming automatic modules (#AutomaticModuleNames)](http://mail.openjdk.java.net/pipermail/jpms-spec-experts/2017-April/000666.html)
    * [Proposal: #AutomaticModuleNames](http://mail.openjdk.java.net/pipermail/jpms-spec-experts/2017-April/000667.html)
  * [Arnaud Roger](https://twitter.com/arnaudroger)
    * [Deep Dive into Java 9’s Stack-Walking API](https://www.sitepoint.com/deep-dive-into-java-9s-stack-walking-api/)
  * [Robert Scholte](https://twitter.com/rfscholte)
    * [Why Maven Cannot Generate Your Module Declaration](https://www.sitepoint.com/maven-cannot-generate-module-declaration/)
  * [Venkat Subramaniam](https://twitter.com/venkat_s)
    * Devoxx BE 2016 interview about [Java 9 with Venkat Subramaniam](https://www.youtube.com/watch?v=OjJBau4ZNyA)

## Special features of personal interest
* [JEP 223](http://openjdk.java.net/jeps/223): New Version-String Scheme
* [JEP 238](http://openjdk.java.net/jeps/238): Multi-Release JAR Files
  * Hibernate Blog: [Building Multi-Release JARs with Maven](http://in.relation.to/2017/02/13/building-multi-release-jars-with-maven/)
* [JEP 261](http://openjdk.java.net/jeps/261): Module System
  * Mark Reinhold: [The State of the Module System](http://openjdk.java.net/projects/jigsaw/spec/sotms/)

## Tools

* [ModiTect](https://github.com/moditect/moditect) - Tooling for the Java 9 Module System  
  > The ModiTect project aims at providing productivity tools for working with the Java 9 module system ("Jigsaw"). Currently it allows to add module descriptors to existing JAR files. In future versions functionality may be added to work with tools like jlink, jdeps or jmod under Maven and other dependency management tools in a comfortable manner.
