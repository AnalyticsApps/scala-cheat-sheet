# Setup Scala multiple project and project dependency



```

(base) nish-mbp:workspace nish$ mkdir ServiceProcessor


(base) nish-mbp:workspace nish$ cd ServiceProcessor


(base) nish-mbp:ServiceProcessor nish$ mkdir -p producer/src/{main,test}/{java,resources,scala}


(base) nish-mbp:ServiceProcessor nish$ mkdir -p consumer-commons/src/{main,test}/{java,resources,scala}


(base) nish-mbp:ServiceProcessor nish$ mkdir -p consumer-billing/src/{main,test}/{java,resources,scala}


(base) nish-mbp:ServiceProcessor nish$ mkdir project

 
(base) nish-mbp:ServiceProcessor nish$ vi build.sbt


(base) nish-mbp:ServiceProcessor nish$ cat build.sbt 
lazy val root = (project in file("."))
  .settings(
    name := "ServiceProcessor",
    commonSettings,
    libraryDependencies ++= commonDependencies
).aggregate( consumerBilling, consumerCommons, producer)

lazy val consumerBilling = (project in file("consumer-billing"))
  .settings(
    name := "ConsumerBilling",
    commonSettings,
    libraryDependencies ++= commonDependencies
  )
  .dependsOn(consumerCommons)

lazy val consumerCommons = (project in file("consumer-commons"))
  .settings(
    name := "ConsumerCommons",
    commonSettings,
    libraryDependencies ++= commonDependencies
  )

lazy val producer = (project in file("producer"))
  .settings(
    name := "Producer",
    commonSettings,
    libraryDependencies ++= commonDependencies
  )

lazy val commonSettings = Seq(
  version := "1.0-SNAPSHOT",
  scalaVersion := "2.12.8"
)

lazy val commonDependencies = Seq(
  "org.scalatest" %% "scalatest" % "3.0.5" % Test
)


(base) nish-mbp:ServiceProcessor nish$ vi project/build.properties


(base) nish-mbp:ServiceProcessor nish$ cat project/build.properties
sbt.version=1.1.5


(base) nish-mbp:ServiceProcessor nish$ mkdir -p producer/src/main/java/com/producer


(base) nish-mbp:ServiceProcessor nish$ vi producer/src/main/java/com/producer/Producer.scala


(base) nish-mbp:ServiceProcessor nish$ cat producer/src/main/java/com/producer/Producer.scala
package com.producer

object Producer extends App {

  println("Producer")

}

 
(base) nish-mbp:ServiceProcessor nish$ mkdir -p consumer-commons/src/main/java/com/commons


(base) nish-mbp:ServiceProcessor nish$ vi consumer-commons/src/main/java/com/commons/Commons.scala


(base) nish-mbp:ServiceProcessor nish$ cat consumer-commons/src/main/java/com/commons/Commons.scala
package com.commons

class Commons(id: Int, name: String) {

override def toString = s"In Commons Id: $id Name: $name"

}


(base) nish-mbp:ServiceProcessor nish$ mkdir -p consumer-billing/src/main/java/com/billing

 
(base) nish-mbp:ServiceProcessor nish$ vi consumer-billing/src/main/java/com/billing/Billing.scala


(base) nish-mbp:ServiceProcessor nish$ cat consumer-billing/src/main/java/com/billing/Billing.scala
package com.billing

import com.commons._

object Billing extends App {

val com = new Commons(2, "James")

println(com)

}



(base) nish-mbp:ServiceProcessor nish$ sbt compile
[info] Loading project definition from /Users/nish/workspace/ServiceProcessor/project
[info] Loading settings from build.sbt ...
[info] Set current project to ServiceProcessor (in build file:/Users/nish/workspace/ServiceProcessor/)
[info] Executing in batch mode. For better performance use sbt's shell
[info] Compiling 1 Scala source to /Users/nish/workspace/ServiceProcessor/consumer-commons/target/scala-2.12/classes ...
[info] Compiling 1 Scala source to /Users/nish/workspace/ServiceProcessor/producer/target/scala-2.12/classes ...
[info] Done compiling.
[info] Done compiling.
[info] Compiling 1 Scala source to /Users/nish/workspace/ServiceProcessor/consumer-billing/target/scala-2.12/classes ...
[info] Done compiling.
[success] Total time: 3 s, completed 31/05/2019 11:49:22 PM



(base) nish-mbp:ServiceProcessor nish$ sbt package
[info] Loading project definition from /Users/nish/workspace/ServiceProcessor/project
[info] Loading settings from build.sbt ...
[info] Set current project to ServiceProcessor (in build file:/Users/nish/workspace/ServiceProcessor/)
[info] Packaging /Users/nish/workspace/ServiceProcessor/target/scala-2.12/serviceprocessor_2.12-1.0-SNAPSHOT.jar ...
[info] Done packaging.
[info] Packaging /Users/nish/workspace/ServiceProcessor/producer/target/scala-2.12/producer_2.12-1.0-SNAPSHOT.jar ...
[info] Packaging /Users/nish/workspace/ServiceProcessor/consumer-commons/target/scala-2.12/consumercommons_2.12-1.0-SNAPSHOT.jar ...
[info] Done packaging.
[info] Done packaging.
[info] Packaging /Users/nish/workspace/ServiceProcessor/consumer-billing/target/scala-2.12/consumerbilling_2.12-1.0-SNAPSHOT.jar ...
[info] Done packaging.
[success] Total time: 0 s, completed 31/05/2019 11:50:19 PM
(base) nish-mbp:ServiceProcessor nish$ 


```

## Reference:


   https://www.scala-sbt.org/0.13/docs/Multi-Project.html



