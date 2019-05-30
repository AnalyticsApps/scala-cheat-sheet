# Setup SBT in eclipse

1) Install SBT in mac ```brew install sbt```

2) Setup the Project

```
(base) nish-mbp:workspace nisanth$ mkdir sbtExample
(base) nish-mbp:workspace nisanth$ 
(base) nish-mbp:workspace nisanth$ cd sbtExample/
(base) nish-mbp:sbtExample nisanth$ 
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
(base) nish-mbp:project nisanth$ vi build.sbt
(base) nish-mbp:project nisanth$
(base) nish-mbp:project nisanth$ cat build.sbt 
name := "sbtExample"
organization := "SampleOrg"
version := "1.0-SNAPSHOT"
scalaVersion := "2.12.6"
(base) nish-mbp:project nisanth$
(base) nish-mbp:project nisanth$ ls
build.properties	build.sbt		plugin.sbt
(base) nish-mbp:project nisanth$
(base) nish-mbp:project nisanth$ cd ..
(base) nish-mbp:project nisanth$
(base) nish-mbp:sbtExample nisanth$ ls
project
(base) nish-mbp:sbtExample nisanth$ 
(base) nish-mbp:sbtExample nisanth$ 
(base) nish-mbp:sbtExample nisanth$ sbt eclipse
[info] Loading settings from plugin.sbt,build.sbt ...
[info] Loading project definition from /Users/nisanth/workspace/sbtExample/project
[info] Updating ProjectRef(uri("file:/Users/nisanth/workspace/sbtExample/project/"), "sbtexample-build")...
[info] Done updating.
[info] Set current project to sbtexample (in build file:/Users/nisanth/workspace/sbtExample/)
[info] About to create Eclipse project files for your project(s).
[info] Updating ...
[info] Done updating.
[info] Successfully created Eclipse project files for project(s):
[info] sbtexample
(base) nish-mbp:sbtExample nisanth$

```


