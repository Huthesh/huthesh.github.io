---
title: Change Java Version in Maven Eclipse Project
layout: default
description: huthesh.github.io
categories: [Java]
---
<ol class="breadcrumb">
  <li><a href="/Java">Java</a></li>
  <li class="active">Change Java Version in Maven Eclipse Project</li>
</ol>

<div>
        {{ page.date | date: "%-d %B %Y" }}
</div>

## Change Java version to 1.8 in Eclipse Maven Project

When we creare Maven Project in Eclipse, by default java version is set to 1.5. We can point to different version of java through pom.xml

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>io.github.huthesh</groupId>
  <artifactId>Start</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  <build>
  	<plugins>
  		<plugin>
  			<groupId>org.apache.maven.plugins</groupId>
  			<artifactId>maven-compiler-plugin</artifactId>
  			<version>3.2</version>
  			<configuration>
  				<source>1.8</source>
  				<target>1.8</target>
  			</configuration>
  		</plugin>
  	</plugins>
  </build>
</project>
```