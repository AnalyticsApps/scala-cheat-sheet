# Basic Scala tutorials

## Simple Scala Code

Example 1:

	package com.test

	object HelloWorld extends App {
	  println("Hello World")
	}


Example 2:

	package com.test

	object HelloWorld {

	def main(args: Array[String]) {

	    println("Hello World !!")

	  }

	}

### Data Types

	Byte / Short / Int / Long / Float / Double
	String
	Boolean
	Unit
	Null / Nothing / Any / AnyRef


### Control Structure

1) IF Condition:
	```
	If(condition1) {
	  ….
	} else if(condition 2){
	  ….
	} else  {

	}
	```

2) WHILE / Do .. Whille Loop

	```

	while(condition) {
	   …..
	}


	do {
	  …..
	} while(condition)

	```

3) For Loop
	
	```
	var ind = 0
	for (ind <- 6 to 12) { …. }

	for (ind <- 6 until 12) { …. }


	var ind = 0
	var id = 0
	for(ind <- 1 to 100; id <- 1 to 200) { …. }


	val idList = List(2,3,4,5)
	for(id <- idList) { ….. }


	for( id <- idList
	       if id > 3; if id != 11 ) { ….. }


	var res = 	for( id <- idList
	       if id > 3; if id != 11 ) { ….. } yield id

	```

4) Break

	```
	import util.control.Breaks._
    	for (i <- 1 to 10) {
        breakable {
            if (i % 2 == 0) break
            ….
        }
    	}
	```

5) Match operation

	```
	def matchTest(x: Int): String = x match {
	case 1 => "one"
	case 2 => "two"
	case _ => "many"
   	}
	```


### String Operations

	```

	var len = str.length();

	var st = str1.concat(str2)

	var st = str1+ str2

	println("%s %s, %d".format(firstName, lastName, age));

	char charAt(int index)

	String replace(char c1, char c2)

	String[] split(String reg1)

	String substring(int i1)

	String trim()

	String substring(int b1, int e1) 

	boolean startsWith(String prefix)

	boolean matches(String regex) 

	int hashCode()

	String Interpolator
	println(s “Hello, $name”)
	println(s “1 + 1 = ${1 + 1}”)


	println(f"$name is $height%1.2f meters tall")

	```


### Arrays Operations

	```
	var z = new Array[String](3)


	// Print all the array elements
      	for ( x <- myArr ) {
      	   println( x )
      	}



      	for ( i <- 0 to (myArr.length - 1)) {
       	  total += myArr(i);
     	 }



      	var myArr1 = Array(1.9, 2.9, 3.4, 3.5)
      	var myArr2 = Array(8.9, 7.9, 0.4, 1.5)
      	var myArr3 =  concat( myArr1, myArr2)




      	var myList1 = range(10, 20, 2)
      	var myList2 = range(10,20)


	```


### Exception Handling

	```

	import java.io.FileReader
	import java.io.FileNotFoundException
	import java.io.IOException

	object Demo {
	   def main(args: Array[String]) {
	      try {
	         val f = new FileReader("input.txt")
	      } catch {
	         case ex: FileNotFoundException => {
	            println("Missing file exception")
	         }
         
	         case ex: IOException => {
	            println("IO Exception")
	         }
	      } finally {
	         println("Exiting finally...")
	      }
	   }
	}

	```



### Functions

1) Scala function's name can have characters like +, ++, ~, &,-, --, \, /, :, etc.
Scala allows you to define functions inside a function and functions defined inside other functions are called local functions.

	```	
	def functionName ([list of parameters]) : [return type] = {
   	  function body
       return [expr]
	}
	```

Scala allows you to indicate that the last parameter to a function may be repeated. This allows clients to pass variable length argument lists to the function. 

	```
	// “args: String*" is actually Array[String] - Variable Argument / Default values
	def empDetails( id: Int = 50, args:String* ) = { …. }
	```

2) Partly applied function 

	```
	val date = new Date
	val logProcess = logAnalysis(date, _ : String)
	logProcess(“HTTP Message” )
	logProcess(“Apache Msg” )


	def logAnalysis(date: Date, message: String) = { … }

	```

3) Named Argument

	```

	printAB(b = 5, a = 7)

	```

4) Higher-Order Function - take other functions as argument, or whose return type is a function.

	```
	println( apply( getDisp, 10) )

	def apply(f: Int => String, v: Int) = f(v)

	def getDisp[A](x: A) = "[" + x.toString() + "]"

	```

5) Anonymous Functions

	```

	var inc = (x:Int) => x+1
	var x = inc(7)-1

	var userDir = () => { System.getProperty("user.dir") }
	var mul = (x: Int, y: Int) => x*y
	```


6) Currying Function - Currying is a means of transforming a function that takes more than one argument into a chain of calls to functions, each of which takes a single argument. 

	We are taking this approach because our vat and serviceCharge will not change very often. So, let's use currying to split our method. 
	We have reduced our method from accepting 3 parameters to accept one parameter. So, we have split our method in such a way that we don't have to provide all the arguments at the same time. 
	I can provide these arguments whenever they are available. This transformation is called currying.

	```
	scala> def finalPriceCurried(vat: Double)(serviceCharge: Double)(productPrice: Double): Double = {
	     | productPrice + productPrice*serviceCharge/100 + productPrice*vat/100
	     | }
	finalPriceCurried: (vat: Double)(serviceCharge: Double)(productPrice: Double)Double

	scala> val vatApplied = finalPriceCurried(20)_
	vatApplied: Double => (Double => Double) = $$Lambda$1261/79661943@e06ec83

	scala> val serviceChargeApplied = vatApplied(12.5)
	serviceChargeApplied: Double => Double = $$Lambda$1262/1131932964@720c8f80

	scala> val finalProductPrice = serviceChargeApplied(120)
	finalProductPrice: Double = 159.0

	```


### Closure

A closure is a function, whose return value depends on the value of one or more variables declared outside this function.


Example 1:


	```

	var factor = 3
	val multiplier = (i:Int) => i * factor

	```

Example 2:


	```

	scala> var age=22
	age: Int = 22
	scala> val sayhello=(name:String)=>println(s"I am $name and I am $age")
    	scala> def func(f:String=>Unit,s:String){
        	| f(s)
       		| }
    	func: (f: String => Unit, s: String)Unit
    	scala> func(sayhello,"Test")




	scala> val colors=ArrayBuffer("Red","Green","Blue")
	scala> val func=(f:String=>Unit,s:String)=>f(s)
    	scala> for(i<-0 to 2){
       		| func(sayhello,colors(i))
        	| }


	```

### Trait

1) Traits are used to share interfaces and fields between classes. They are similar to Java 8’s interfaces. Classes and objects can extend traits but traits cannot be instantiated and therefore have no parameters.


	```

	trait Iterator[A] {
	  def hasNext: Boolean
	  def next(): A
	}

	class IntIterator(to: Int) extends Iterator[Int] {
	  private var current = 0
	  override def hasNext: Boolean = current < to
	  override def next(): Int =  {
	    if (hasNext) {
	      val t = current
	      current += 1
	      t
	    } else 0
	  }
	}
	

	val iterator = new IntIterator(10)
	iterator.next()  // returns 0
	iterator.next()  // returns 1


	```

2) If a class extends a trait but does not implement the methods defined in that trait, it must be declared abstract:

	```

	// must be declared abstract because it does not implement BaseSoundPlayer methods
	abstract class JavaSoundPlayer extends BaseSoundPlayer {
	  def play   {}
	  def close  {}
	}

	```

3) If a class implements multiple traits, it will extend the first trait (or a class, or abstract class), and then use with for other traits:

	```
	abstract class Animal {
 	 def speak
	}

	trait WaggingTail {
	  def startTail
	  def stopTail
	}

	trait FourLeggedAnimal {
	  def walk
	  def run
	}

	class Dog extends Animal with WaggingTail with FourLeggedAnimal {
	  // implementation code here ...
	}

	```

4) You can implement the default methods in Trait.

	```

	trait Pet {
	  def speak { println("Yo") }   // concrete implementation of a speak method
	  def comeToMaster              // abstract
	}

	```


5) Limiting the subclass in a trait

Solution 1:

	```
	//We have two classes "Tyre" and "Ball"
	class Tyre
	abstract class Ball
 
	//Now Bouncable is restricted to subclasses of Tyre
	trait Bouncable extends Tyre
 
	//This will work perfectly fine
	class TubeTyre extends Tyre with Bouncable
	class TublessTyre extends Tyre with Bouncable
 
	//Will not compile
	class BasketBall extends Ball with Bouncable
	abstract class FootBall extends Ball with Bouncable

	```

Solution 2: you can also write first statement in your trait like “this:<Limiting Base Class Name> =>” which will allow only subclasses of that limiting base class to use this trait.

	```
	trait WarpCore {
	  this: Starship =>
	}

	// Will work
	class Starship
	class Enterprise extends Starship with WarpCore


	// Will not work
	class RomulanShip
	class Warbird extends RomulanShip with WarpCore   // this won't compile

	```



### File I/O


      ```

      print("Please enter your input : " )
      val line = Console.readLine



      import scala.io.Source
      Source.fromFile("Demo.txt" ).foreach { 
         print 
      }


      import java.io._
      val writer = new PrintWriter(new File("test.txt" ))
      writer.write("Hello Scala")
      writer.close()

      ```

## Reference:

	https://alvinalexander.com/scala/
	https://www.tutorialspoint.com/scala


