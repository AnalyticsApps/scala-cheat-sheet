# Setup SBT in eclipse

1) Install SBT in mac ```brew install sbt```


2) Setup the Project

```
(base) nish-mbp:workspace nisanth$ mkdir sbtExample
(base) nish-mbp:workspace nisanth$ 


(base) nish-mbp:workspace nisanth$ cd sbtExample/
(base) nish-mbp:sbtExample nisanth$ 


(base) nish-mbp:project nisanth$ vi build.sbt
(base) nish-mbp:project nisanth$


(base) nish-mbp:project nisanth$ cat build.sbt 
name := "sbtExample"
organization := "SampleOrg"
version := "1.0-SNAPSHOT"
scalaVersion := "2.12.6"


(base) nish-mbp:sbtExample nisanth$ mkdir project
(base) nish-mbp:sbtExample nisanth$ 


(base) nish-mbp:sbtExample nisanth$ cd project/
(base) nish-mbp:sbtExample nisanth$


(base) nish-mbp:sbtExample nisanth$ vi plugin.sbt
(base) nish-mbp:sbtExample nisanth$ 


(base) nish-mbp:sbtExample nisanth$ cat plugin.sbt 
addSbtPlugin("com.typesafe.sbteclipse" % "sbteclipse-plugin" % "5.2.4")
(base) nish-mbp:sbtExample nisanth$ 


(base) nish-mbp:project nisanth$ vi build.properties
(base) nish-mbp:sbtExample nisanth$


(base) nish-mbp:project nisanth$ cat build.properties 
sbt.version=1.1.5
(base) nish-mbp:project nisanth$


(base) nish-mbp:project nisanth$ ls
build.properties	plugin.sbt
(base) nish-mbp:project nisanth$


(base) nish-mbp:project nisanth$ cd ..
(base) nish-mbp:project nisanth$


(base) nish-mbp:sbtExample nisanth$ ls
build.sbt		project
(base) nish-mbp:sbtExample nisanth$ 


(base) nish-mbp:sbtExample nisanth$ 
(base) nish-mbp:sbtExample nisanth$ sbt eclipse
[info] Loading settings from plugin.sbt ...
[info] Loading project definition from /Users/nisanth/workspace/sbtExample/project
[info] Updating ProjectRef(uri("file:/Users/nisanth/workspace/sbtExample/project/"), "sbtexample-build")...
[info] Done updating.
[info] Loading settings from build.sbt ...
[info] Set current project to sbtExample (in build file:/Users/nisanth/workspace/sbtExample/)
[info] About to create Eclipse project files for your project(s).
[info] Updating ...
[info] Done updating.
[info] Successfully created Eclipse project files for project(s):
[info] sbtExample
(base) nish-mbp:sbtExample nisanth$ 

```

**Whenever there is any change to build.sbt or files under project folder run sbt eclipse**


3) Import the project to Eclipse


4) Add the src and test folders

```

(base) nish-mbp:sbtExample nisanth$ 
(base) nish-mbp:sbtExample nisanth$ ls
build.sbt	project		target
(base) nish-mbp:sbtExample nisanth$ 


(base) nish-mbp:sbtExample nisanth$ mkdir -p src/main/scala
(base) nish-mbp:sbtExample nisanth$ 


(base) nish-mbp:sbtExample nisanth$ mkdir -p src/test/scala
(base) nish-mbp:sbtExample nisanth$ 


(base) nish-mbp:sbtExample nisanth$ vi .classpath 
(base) nish-mbp:sbtExample nisanth$ 


(base) nish-mbp:sbtExample nisanth$ cat .classpath 
<classpath>
  <classpathentry output="target/scala-2.12/classes" path="src/main/scala" kind="src"></classpathentry>
  <classpathentry output="target/scala-2.12/test-classes" path="src/test/scala" kind="src"></classpathentry>
  <classpathentry kind="con" path="org.scala-ide.sdt.launching.SCALA_CONTAINER"></classpathentry>
  <classpathentry kind="con" path="org.eclipse.jdt.launching.JRE_CONTAINER"/>
  <classpathentry kind="output" path="bin"/>
</classpath>
(base) nish-mbp:sbtExample nisanth$ 
(base) nish-mbp:sbtExample nisanth$ cat .project 
<projectDescription>
  <name>sbtExample</name>
  <buildSpec>
    <buildCommand>
      <name>org.scala-ide.sdt.core.scalabuilder</name>
    </buildCommand>
  </buildSpec>
  <natures>
    <nature>org.scala-ide.sdt.core.scalanature</nature>
    <nature>org.eclipse.jdt.core.javanature</nature>
  </natures>
  <linkedResources> </linkedResources>
</projectDescription>
(base) nish-mbp:sbtExample nisanth$ 


(base) nish-mbp:sbtExample nisanth$ sbt eclipse
[info] Loading settings from plugin.sbt ...
[info] Loading project definition from /Users/nisanth/workspace/sbtExample/project
[info] Loading settings from build.sbt ...
[info] Set current project to sbtExample (in build file:/Users/nisanth/workspace/sbtExample/)
[info] About to create Eclipse project files for your project(s).
[info] Successfully created Eclipse project files for project(s):
[info] sbtExample
(base) nish-mbp:sbtExample nisanth$ 


```


5) Create a sample scala program under src/main/scala and compile/run/package

```
(base) nish-mbp:sbtExample nisanth$ 
(base) nish-mbp:sbtExample nisanth$ cat src/main/scala/Test.scala


object Test extends App {
  
  println("testing")
  
}
(base) nish-mbp:sbtExample nisanth$ 


(base) nish-mbp:sbtExample nisanth$ sbt compile
[info] Loading settings from plugin.sbt ...
[info] Loading project definition from /Users/nisanth/workspace/sbtExample/project
[info] Loading settings from build.sbt ...
[info] Set current project to sbtExample (in build file:/Users/nisanth/workspace/sbtExample/)
[info] Executing in batch mode. For better performance use sbt's shell
[info] Compiling 1 Scala source to /Users/nisanth/workspace/sbtExample/target/scala-2.12/classes ...
[info] Done compiling.
[success] Total time: 1 s, completed 30/05/2019 2:38:09 PM
(base) nish-mbp:sbtExample nisanth$ 
 

(base) nish-mbp:sbtExample nisanth$ sbt run
[info] Loading settings from plugin.sbt ...
[info] Loading project definition from /Users/nisanth/workspace/sbtExample/project
[info] Loading settings from build.sbt ...
[info] Set current project to sbtExample (in build file:/Users/nisanth/workspace/sbtExample/)
[info] Packaging /Users/nisanth/workspace/sbtExample/target/scala-2.12/sbtexample_2.12-1.0-SNAPSHOT.jar ...
[info] Done packaging.
[info] Running Test 
testing
[success] Total time: 1 s, completed 30/05/2019 2:39:35 PM
(base) nish-mbp:sbtExample nisanth$ 


(base) nish-mbp:sbtExample nisanth$ sbt package
[info] Loading settings from plugin.sbt ...
[info] Loading project definition from /Users/nisanth/workspace/sbtExample/project
[info] Loading settings from build.sbt ...
[info] Set current project to sbtExample (in build file:/Users/nisanth/workspace/sbtExample/)
[info] Packaging /Users/nisanth/workspace/sbtExample/target/scala-2.12/sbtexample_2.12-1.0-SNAPSHOT.jar ...
[info] Done packaging.
[success] Total time: 0 s, completed 30/05/2019 2:39:48 PM
(base) nish-mbp:sbtExample nisanth$ 


(base) nish-mbp:sbtExample nisanth$ scala /Users/nishnish-mbp/workspace/sbtExample/target/scala-2.12/sbtexample_2.12-1.0-SNAPSHOT.jar
testing
(base) nish-mbp:sbtExample nisanth$

```


## Reference:


   https://github.com/sbt/sbteclipse


   https://alvinalexander.com/scala/sbt-how-to-compile-run-package-scala-project


   https://www.scala-sbt.org/release/docs/Command-Line-Reference.html

