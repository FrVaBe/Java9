# Java9

Collected information about Java 9.  
Work in progress...

## General Resources

* Official
  * [JDK 9](http://openjdk.java.net/projects/jdk9/) project page
  * [JSR 379](http://openjdk.java.net/projects/jdk9/spec/), the Platform Umbrella JSR for Java SE 9


* Community
  * [Eugen Baeldung](https://twitter.com/baeldung)
    * 2017-03-01: [Java 9 Process API (Improvements)](http://www.baeldung.com/java-9-process-api)
  * [Stephen Colebourne](https://twitter.com/jodastephen)
    * 2017-02-07: [Java Time (JSR-310) enhancements in Java SE 9](http://blog.joda.org/2017/02/java-time-jsr-310-enhancements-java-9.html)
    * 2017-04-17: [Java 9 modules - JPMS basics ](http://blog.joda.org/2017/04/java-9-modules-jpms-basics.html)
    * 2017-04-24: [Java SE 9 - JPMS modules are not artifacts ](http://blog.joda.org/2017/04/java-se-9-jpms-modules-are-not-artifacts.html)
  * [Nicolai Parlog](https://twitter.com/nipafx)
    * [Java 9 Is Coming!](http://slides.codefx.org/java-9/2017-02-23-voxxed-days-zuerich/index.html#/) (talk at #VDZ17)
    * 2016-06-26: [Java 9 Additions To Optional](http://blog.codefx.org/java/dev/java-9-optional/)
  * **[Mark.Reinhold](https://twitter.com/mreinhold)**
    * 2017-02-16: [How to name modules, automatic and otherwise](http://mail.openjdk.java.net/pipermail/jpms-spec-experts/2017-February/000582.html)
    * 2017-04-03: [Alternatives for naming automatic modules (#AutomaticModuleNames)](http://mail.openjdk.java.net/pipermail/jpms-spec-experts/2017-April/000666.html)
    * 2017-04-03: [Proposal: #AutomaticModuleNames](http://mail.openjdk.java.net/pipermail/jpms-spec-experts/2017-April/000667.html)
  * [Arnaud Roger](https://twitter.com/arnaudroger)
    * 2017-03-06: [Deep Dive into Java 9’s Stack-Walking API](https://www.sitepoint.com/deep-dive-into-java-9s-stack-walking-api/)
  * [Robert Scholte](https://twitter.com/rfscholte)
    * 201-04-03: [Why Maven Cannot Generate Your Module Declaration](https://www.sitepoint.com/maven-cannot-generate-module-declaration/)
  * [Venkat Subramaniam](https://twitter.com/venkat_s)
    * 2016-12-09: Devoxx BE 2016 interview about [Java 9 with Venkat Subramaniam](https://www.youtube.com/watch?v=OjJBau4ZNyA)

## Special features of personal interest
* [JEP 223](http://openjdk.java.net/jeps/223): New Version-String Scheme
* [JEP 238](http://openjdk.java.net/jeps/238): Multi-Release JAR Files
  * Hibernate Blog: [Building Multi-Release JARs with Maven](http://in.relation.to/2017/02/13/building-multi-release-jars-with-maven/)
* [JEP 261](http://openjdk.java.net/jeps/261): Module System
  * Mark Reinhold: [The State of the Module System](http://openjdk.java.net/projects/jigsaw/spec/sotms/)

## Tools

* [ModiTect](https://github.com/moditect/moditect) - Tooling for the Java 9 Module System  
  > The ModiTect project aims at providing productivity tools for working with the Java 9 module system ("Jigsaw"). Currently it allows to add module descriptors to existing JAR files. In future versions functionality may be added to work with tools like jlink, jdeps or jmod under Maven and other dependency management tools in a comfortable manner.
