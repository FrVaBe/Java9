# Java 9 - Multi-Release Jar Example

Java 9 offers the possibility to build a JAR file with a format that _"allows multiple, Java-release-specific versions of class files to coexist in a single archive"_ ([JEP 238](http://openjdk.java.net/jeps/238): Multi-Release JAR Files).

This is a little sample project that demonstrates how to build such a jar file with Maven. The sample is strongly influenced by the following posts
* [Gunnar Morling](https://twitter.com/gunnarmorling): [Building Multi-Release JARs with Maven](http://in.relation.to/2017/02/13/building-multi-release-jars-with-maven/)
* [David M. Lloyd](https://twitter.com/dmlloyd0): [Generating Multi-Release JARs with Maven](http://word-bits.flurg.com/multrelease-jars/)

## Multi-Release Jar Format

What makes a Jar file a _Multi Jar file_? There are basically two things
* a MANIFEST.MF entry `Multi-Release: true`
* version specific source code in the META-INF directory

In the example provided here there is a `HelloWorld` class that comes with a [Java 8](multi-release-jar/src/main/java/de/frvabe/java9/mrjar/HelloWorld.java) and [Java 9](multi-release-jar-java9/src/main/java/de/frvabe/java9/mrjar/HelloWorld.java) flavour. The final jar file content looks like this:

```
C:.
├───de
│   └───frvabe
│       └───java9
│           └───mrjar
│                   HelloWorld.class
│
└───META-INF
    └───versions
        └───9
            └───de
                └───frvabe
                    └───java9
                        └───mrjar
                                HelloWorld.class
```
JVM versions that do not know the multi release jar file format will pick up the `HelloWorld` that can be found in the root path of the jar file (as usual). A Java 9 VM instead will detect that a specific HelloWorld class for Java 9 exists and will pick up this class.

IMHO a really nice and easy extension of the JAR format to support separated implementations for different java versions.

## Example Code

The example code exists of the following three projects:   
(I did not wrap them into a Maven Multi Module project, thus you have to build them one after another by your own)

### multi-release-jar-parent (needs to be build first)

That is just a parent project to define some plugin versions and a build section which will take care of generating JavaDoc and Source artifacts for the child projects. It is not really needed for the example but a usual setup in my day to day work. Thus I wanted to include it in my demo project. Have a closer look at the [pom.xml](multi-release-jar-parent/pom.xml) for detailed information.

### multi-release-jar-java9 (needs to be build second)

That is the artifact where the Java 9 specific Java Code ([HelloWorld.java](multi-release-jar-java9/src/main/java/de/frvabe/java9/mrjar/HelloWorld.java)) is provided. There is really no magic in this project. The [pom.xml](multi-release-jar-java9/pom.xml) file is nearly empty. Beside the Maven coordinates you will just find the settings to make the compiler produce Java 9 classes.

```xml
<properties>
  <maven.compiler.target>1.9</maven.compiler.target>
  <maven.compiler.source>1.9</maven.compiler.source>
</properties>
```

### multi-release-jar (needs to be build last)

This is the artifact that becomes a Multi-Release Jar. The code in this project ([HelloWorld.java](multi-release-jar/src/main/java/de/frvabe/java9/mrjar/HelloWorld.java)) will be compiled using Java 8 (see the settings in the [parent pom.xml](multi-release-jar-parent/pom.xml)).

But in addition the following steps are made in the projects [pom.xml](multi-release-jar/pom.xml) to make it a Multi Release Jar.

**(1) add the _Multi-Release_ attribute to the MANIFEST.MF (maven-jar-plugin)**

```xml
<plugin>
	<groupId>org.apache.maven.plugins</groupId>
	<artifactId>maven-jar-plugin</artifactId>
	<version>3.0.2</version>
	<configuration>
		<archive>
			<manifestEntries>
				<Specification-Title>${project.artifactId}</Specification-Title>
				<Implementation-Title>${project.artifactId}</Implementation-Title>
				<Implementation-Version>${project.version}</Implementation-Version>
				<Multi-Release>true</Multi-Release>
			</manifestEntries>
		</archive>
	</configuration>
</plugin>
```

**(2) copy the Java 9 classes from the Java 9 artifact to this Multi Module Jar (maven-dependency-plugin)**

```xml
<plugin>
	<artifactId>maven-dependency-plugin</artifactId>
	<version>3.0.0</version>
	<executions>
		<execution>
			<id>add-java9-classes</id>
			<phase>generate-resources</phase>
			<goals>
				<goal>unpack-dependencies</goal>
			</goals>
			<configuration>
				<includeGroupIds>de.frvabe.java9</includeGroupIds>
				<includeArtifactIds>multi-release-jar-java9</includeArtifactIds>
				<excludeTransitives>true</excludeTransitives>
				<outputDirectory>${project.build.directory}/generated-resources/META-INF/versions/9</outputDirectory>
				<includes>**/*.class</includes>
			</configuration>
		</execution>
	</executions>
</plugin>
```

**(3) add the Java 9 classes to the build resources (build-helper-maven-plugin)**

The copied Java 9 classes need to be added as resources to the build. Otherwise they won't be bundled into the jar file. This can be done with different approaches. I use the _build-helper-maven-plugin_ for this.

```xml
<plugin>
	<groupId>org.codehaus.mojo</groupId>
	<artifactId>build-helper-maven-plugin</artifactId>
	<version>3.0.0</version>
	<executions>
		<execution>
			<id>add-resource</id>
			<phase>generate-resources</phase>
			<goals>
				<goal>add-resource</goal>
			</goals>
			<configuration>
				<resources>
					<resource>
						<directory>${project.build.directory}/generated-resources/</directory>
					</resource>
				</resources>
			</configuration>
		</execution>
	</executions>
</plugin>
```

## Finally

That's all. The Multi-Release Jar file is ready.

The execution result in a **Java 8** environment will be

```
...\multi-release-jar>java -cp target\multi-release-jar-0.0.1-SNAPSHOT.jar de.frvabe.java9.mrjar.HelloWorld
Hello World!
```

Whereas in a **Java 9** environment the output is

```
...\multi-release-jar>java -cp target\multi-release-jar-0.0.1-SNAPSHOT.jar de.frvabe.java9.mrjar.HelloWorld
Hello World - Java 9!
```
