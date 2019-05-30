# Setup Scala Testing


**We use Giter8 template to create the project.**

```

(base) nish:workspace nish$ 
(base) nish:workspace nish$ mkdir TestExample
(base) nish:workspace nish$ 


(base) nish:workspace nish$ cd TestExample/
(base) nish:TestExample nish$ 


(base) nish:TestExample nish$ sbt new scala/scalatest-example.g8
[info] Set current project to testexample (in build file:/Users/nish/workspace/TestExample/)
[info] Set current project to testexample (in build file:/Users/nish/workspace/TestExample/)
[info] downloading https://repo1.maven.org/maven2/org/codehaus/plexus/plexus-archiver/2.7.1/plexus-archiver-2.7.1.jar ...
[info] downloading https://repo1.maven.org/maven2/com/github/scopt/scopt_2.12/3.5.0/scopt_2.12-3.5.0.jar ...
[info] downloading https://repo1.maven.org/maven2/org/clapper/scalasti_2.12/2.1.2/scalasti_2.12-2.1.2.jar ...
[info] downloading https://repo1.maven.org/maven2/commons-logging/commons-logging/1.1.1/commons-logging-1.1.1.jar ...
[info] downloading https://repo1.maven.org/maven2/org/ow2/asm/asm/5.1/asm-5.1.jar ...
[info] 	[SUCCESSFUL ] org.scala-sbt.sbt-giter8-resolver#sbt-giter8-resolver_2.12;0.1.3!sbt-giter8-resolver_2.12.jar (1296ms)
[info] 	[SUCCESSFUL ] org.eclipse.jgit#org.eclipse.jgit.ui;3.7.0.201502260915-r!org.eclipse.jgit.ui.jar (1459ms)
[info] 	[SUCCESSFUL ] org.foundweekends.giter8#giter8_2.12;0.7.2!giter8_2.12.jar (1465ms)
[info] 	[SUCCESSFUL ] org.ow2.asm#asm-tree;5.1!asm-tree.jar (1568ms)
[info] 	[SUCCESSFUL ] org.apache.commons#commons-compress;1.6!commons-compress.jar (1997ms)
[info] 	[SUCCESSFUL ] org.scala-lang.modules#scala-xml_2.12;1.0.5!scala-xml_2.12.jar(bundle) (2501ms)
[info] 	[SUCCESSFUL ] org.slf4j#slf4j-api;1.7.20!slf4j-api.jar (1111ms)

Say something about this template. 
name [My Something Project]: ScalaTestProject
Template applied in ./scalatestproject




(base) nish:TestExample nish$ ls
scalatestproject
(base) nish:TestExample nish$ 


(base) nish:TestExample nish$ cd scalatestproject/
(base) nish:scalatestproject nish$ 


(base) nish:scalatestproject nish$ ls
build.sbt	project		src
(base) nish:scalatestproject nish$ 


(base) nish:scalatestproject nish$ cat build.sbt 
lazy val root = (project in file(".")).
  settings(
    inThisBuild(List(
      organization := "com.example",
      scalaVersion := "2.12.7"
    )),
    name := "scalatest-example"
  )

libraryDependencies += "org.scalatest" %% "scalatest" % "3.0.5" % Test
(base) nish:scalatestproject nish$ 


(base) nish:scalatestproject nish$ ls project/
build.properties
(base) nish:scalatestproject nish$ 


(base) nish:scalatestproject nish$ cat project/build.properties 
sbt.version=0.13.17
(base) nish:scalatestproject nish$ 


(base) nish:scalatestproject nish$ ls src/
main	test
(base) nish:scalatestproject nish$ 


(base) nish:scalatestproject nish$ ls src/main/scala/
CubeCalculator.scala
(base) nish:scalatestproject nish$ 


(base) nish:scalatestproject nish$ cat src/main/scala/CubeCalculator.scala 
object CubeCalculator extends App {
  def cube(x: Int) = {
    x * x * x
  }
}(base) nish:scalatestproject nish$ 


(base) nish:scalatestproject nish$ ls src/test/scala/
CubeCalculatorTest.scala
(base) nish:scalatestproject nish$ 


(base) nish:scalatestproject nish$ cat src/test/scala/CubeCalculatorTest.scala 
class CubeCalculatorTest extends org.scalatest.FunSuite {
  test("CubeCalculator.cube") {
    assert(CubeCalculator.cube(3) === 27)
  }
}
(base) nish:scalatestproject nish$ 


(base) nish:scalatestproject nish$ pwd
/Users/nish/workspace/TestExample/scalatestproject
(base) nish:scalatestproject nish$ 


(base) nish:scalatestproject nish$ sbt test
Getting org.scala-sbt sbt 0.13.17  (this may take some time)...
downloading https://repo.typesafe.com/typesafe/ivy-releases/org.scala-sbt/sbt/0.13.17/jars/sbt.jar ...
	[SUCCESSFUL ] org.scala-sbt#sbt;0.13.17!sbt.jar (5125ms)
downloading https://repo1.maven.org/maven2/org/scala-lang/scala-library/2.10.7/scala-library-2.10.7.jar ...
	[SUCCESSFUL ] org.scala-lang#scala-library;2.10.7!scala-library.jar (7874ms)
downloading https://repo.typesafe.com/typesafe/ivy-releases/org.scala-sbt/main/0.13.17/jars/main.jar ...
	[SUCCESSFUL ] org.scala-sbt#main;0.13.17!main.jar (6246ms)
downloading https://repo.typesafe.com/typesafe/ivy-releases/org.scala-sbt/cache/0.13.17/jars/cache.jar ...
	[SUCCESSFUL ] org.scala-sbt#cache;0.13.17!cache.jar (6287ms)
downloading https://repo.typesafe.com/typesafe/ivy-releases/org.scala-sbt/test-agent/0.13.17/jars/test-agent.jar ...
	[SUCCESSFUL ] org.scala-sbt#test-agent;0.13.17!test-agent.jar (5387ms)
downloading https://repo.typesafe.com/typesafe/ivy-releases/org.scala-sbt/apply-macro/0.13.17/jars/apply-macro.jar ...
	[SUCCESSFUL ] org.scala-sbt#apply-macro;0.13.17!apply-macro.jar (4723ms)
:: retrieving :: org.scala-sbt#boot-app
	confs: [default]
	49 artifacts copied, 0 already retrieved (17577kB/54ms)
Getting Scala 2.10.7 (for sbt)...
downloading https://repo1.maven.org/maven2/org/scala-lang/jline/2.10.7/jline-2.10.7.jar ...
	[SUCCESSFUL ] org.scala-lang#jline;2.10.7!jline.jar (1086ms)
downloading file:////Users/nish/.sbt/preloaded/org.fusesource.jansi/jansi/1.4/jars/jansi.jar ...
	[SUCCESSFUL ] org.fusesource.jansi#jansi;1.4!jansi.jar (4ms)
:: retrieving :: org.scala-sbt#boot-scala
	confs: [default]
	5 artifacts copied, 0 already retrieved (24560kB/27ms)
[info] Loading project definition from /Users/nish/workspace/TestExample/scalatestproject/project
[info] Updating {file:/Users/nish/workspace/TestExample/scalatestproject/project/}scalatestproject-build...
[info] Resolving org.fusesource.jansi#jansi;1.4 ...
[info] Done updating.
[info] Set current project to scalatest-example (in build file:/Users/nish/workspace/TestExample/scalatestproject/)
[info] Updating {file:/Users/nish/workspace/TestExample/scalatestproject/}root...
[info] Resolving jline#jline;2.14.6 ...
[info] downloading https://repo1.maven.org/maven2/org/scala-lang/scala-library/2.12.7/scala-library-2.12.7.jar ...
[info] 	[SUCCESSFUL ] org.scala-lang#scala-library;2.12.7!scala-library.jar (5437ms)
[info] downloading https://repo1.maven.org/maven2/org/scalatest/scalatest_2.12/3.0.5/scalatest_2.12-3.0.5.jar ...
[info] 	[SUCCESSFUL ] org.scalatest#scalatest_2.12;3.0.5!scalatest_2.12.jar(bundle) (3015ms)
[info] downloading https://repo1.maven.org/maven2/org/scalactic/scalactic_2.12/3.0.5/scalactic_2.12-3.0.5.jar ...
[info] 	[SUCCESSFUL ] org.scalactic#scalactic_2.12;3.0.5!scalactic_2.12.jar(bundle) (825ms)
[info] downloading https://repo1.maven.org/maven2/org/scala-lang/scala-reflect/2.12.7/scala-reflect-2.12.7.jar ...
[info] 	[SUCCESSFUL ] org.scala-lang#scala-reflect;2.12.7!scala-reflect.jar (1651ms)
[info] downloading https://repo1.maven.org/maven2/org/scala-lang/scala-compiler/2.12.7/scala-compiler-2.12.7.jar ...
[info] 	[SUCCESSFUL ] org.scala-lang#scala-compiler;2.12.7!scala-compiler.jar (3451ms)
[info] Done updating.
[info] Compiling 1 Scala source to /Users/nish/workspace/TestExample/scalatestproject/target/scala-2.12/classes...
[info] 'compiler-interface' not yet compiled for Scala 2.12.7. Compiling...
[info]   Compilation completed in 6.867 s
[info] Compiling 1 Scala source to /Users/nish/workspace/TestExample/scalatestproject/target/scala-2.12/test-classes...
[info] CubeCalculatorTest:
[info] - CubeCalculator.cube
[info] Run completed in 182 milliseconds.
[info] Total number of tests run: 1
[info] Suites: completed 1, aborted 0
[info] Tests: succeeded 1, failed 0, canceled 0, ignored 0, pending 0
[info] All tests passed.
[success] Total time: 35 s, completed 30/05/2019 4:19:35 PM
(base) nish:scalatestproject nish$ 


```

## Reference:


   https://www.scala-sbt.org/1.0/docs/sbt-new-and-Templates.html



