# Basic Scala tutorials

## Simple Scala Code


Example 1:

	package com.test

	object HelloWorld extends App {
	  	// conditions stated 
    		if (args.length == 1) 
    		{  
        		// Displays this as output if the command line arguments are equal to one 
        		println("Student: ${args(0)}") 
    		} 
	}


Example 2:

	package com.test

	object HelloWorld {

	def main(args: Array[String]) {

	    println("Hello World !!")

	    printf("Age = %d", 24) 

	  }

	}



### Data Types

	Byte / Short / Int / Long / Float / Double
	String
	Boolean
	Unit
	Null / Nothing / 
	Any / AnyVal / AnyRef



	Multiple variable declaration
	val (empId:Int, empName:String) = (1,"John")



1) Scala Option: is referred to a carrier of single or no element for a stated type. When a method returns a value which can even be null then Option is utilized

Example 1:

	```
	scala> val name = Map("Nish" -> "Tester")
	name: scala.collection.immutable.Map[String,String] = Map(Nish -> Tester)

	scala> name.get("Nish")
	res11: Option[String] = Some(Tester)

	scala> name.get("John")
	res12: Option[String] = None

	```

Example 2:

	```
	scala> def ext(n: Option[String]) = n match {
     		| case Some(s) => (s) 
    	 	| case None => ("key not found") 
     		| }
		ext: (n: Option[String])String

	scala> ext(name.get("John"))
		res13: String = key not found

	scala> ext(name.get("Nish"))
		res14: String = Tester
	```



getOrElse(): This method is utilized in returning either a value if it is present or a default value when its not present

	```
	val some:Option[Int] = Some(15) 
  
        // Using None class 
        val none:Option[Int] = None  
  
        // Applying getOrElse method 
        val x = some.getOrElse(0) 
        val y = none.getOrElse(17) 

	```

isEmpty(): This method is utilized to check if the Option has a value or not.
	
	```
	val x = some.isEmpty 
	val y = none.isEmpty 

	```

Other operations on Option


	```

	scala> val some:Option[Int] = Some(30)
	some: Option[Int] = Some(30)


	scala> some.exists(y => {y % 3 == 0})
	res47: Boolean = true

 
	scala> some.filter(y => {y % 3 == 0})
	res48: Option[Int] = Some(30)


	scala> some.filterNot(y => {y % 3 != 0}) 
	res49: Option[Int] = Some(30)


	scala> val some:Option[Int] = Some(30) 
	some: Option[Int] = Some(30)


	scala> val none:Option[Int] = None
	none: Option[Int] = None


	scala> some.isDefined
	res50: Boolean = true


	scala> none.isDefined 
	res51: Boolean = false


	```


2) Scala Casting: 

	```
	val a = 10
        // Casting value of a into float 
        val b = a.asInstanceOf[Float] 

	```

3) Scala Final

	```
	// Final Variable declaration
	// define final variable 
	final val area:Int = 60


	// Final method declaration
	// Define final method 

	final def CalArea(){  .... } 


	// If class is final, it cannot be inherited
	final class Shapes 
	{  .... }


	```


4) StringBuilder is utilized to append input data to the internal buffer. We can perform numerous operations with the support of methods on the StringBuilder. 


	```
       	// Creating StringBuilder  
        val x = new StringBuilder("Author")

        // Appending character  
        val y = (x += 's') 

        // Appending String  
        val y = (x ++= " of GeeksforGeeks") 

	val y = x.append(800)

        // Resetting the content  
        val y = x.clear()  

        // Deleting characters  
        val r = q.delete(1, 3)

        // inserting strings  
        val r = q.insert(4, "is a " )

        // Applying conversion operation  
        val r = q.toString 

	```

4) Scala apply/unapply function

	```

	// Example 1
	object Foo {
	  var y = 5
	  def apply (x: Int) = x + y
	}
	Foo (1)



	// Example 2
	class MyAdder(x: Int) {
	  def apply(y: Int) = x + y
	}
	val adder = new MyAdder(2)
	val result = adder(4) // equivalent to x.apply(4)


	// Example 3
	// The apply method is like a constructor which takes arguments and creates an object, whereas 
	// the unapply takes an object and tries to give back the arguments.
	object Foo {
	    def apply(name: String, suffix: String) = name + "." + suffix

 	   def unapply(name: String): Option[(String, String)] = {
 	     //simple argument extractor
	      val parts = name.split("\\.")
	      if (parts.length == 2) Some(parts(0), parts(1)) else None
	    }
	  }
	val file = Foo("test", "txt") // returns test.txt
	val Foo(name) = file // Unapply method is used


	```


### Control Structure

1) IF Condition:

	```

	If(condition1) {
	  ….
	} else if(condition 2){
	  ….
	} else  {

	}

	val max = if (x > y) x else y

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
	// includes 6 to 12
	for (ind <- 6 to 12) { …. }

	// starts from 6 to 11
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
			 ......
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


   	def matchAge(age: Any): Any = age match {
   	case 7 => "Age is Seven"
   	case "eight" => 8
   	case y: Int => "Age is greater than 7"
   	case _ => "Age is greater than 10"
   	}



   	case class Student(id:Int, name: String, age: Int)
   	   	studInstance match {
   	   	   	case Student(1,"Adam", 12) => println("Hello Adam")
   	   	   	case Student(3,"Reena", 16) => println("Hello Reena")
   	   	   	case Student(id,name, age) =>
   	   	   	   	println("Id: " + id + " Age: " + age + " Name: " + name)
   	   	}




    	stock match {
    		case x if (x.symbol == "XYZ" && x.price < 20) => buy(x)
    		case x if (x.symbol == "XYZ" && x.price > 50) => sell(x)
    		case x => doNothing(x)
    	}


	```

6) Enumeration: Defines a finite set of values specific to the enumeration. 


	```

	scala> object Weekday extends Enumeration {
	     |   val Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday = Value
	     | }
	defined object Weekday


	scala> Weekday.Monday
	res33: Weekday.Value = Monday


	scala> Weekday.Monday.toString
	res34: String = Monday


	scala> Weekday.withName("Monday")
	res35: Weekday.Value = Monday


	// Listing all possible values
	scala> Weekday.values
	res36: Weekday.ValueSet = Weekday.ValueSet(Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday)


	// Ordering the values.	
	scala> Weekday.values.toList.sorted
	res37: List[Weekday.Value] = List(Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday)

 

	scala> Weekday.Monday.id
	res41: Int = 0
	scala> Weekday.Sunday.id
	res42: Int = 6

	// Change the id to a specified value
	scala> object ErrorCodes extends Enumeration {
	     | val http_ok = Value(200, "OK")
	     | val internal_error = Value(400, "Server_Error")
	     | }
	defined object ErrorCodes


	scala> ErrorCodes.http_ok.id
	res44: Int = 200


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

	Boolean endsWith(String suffix)

	Boolean equals(Object anObject)

	Boolean equalsIgnoreCase(String anotherString)

	int indexOf(String str)

	String replaceAll(String regex, String replacement)

	String toLowerCase()

	String trim()

	String Interpolator
	println(s “Hello, $name”)
	println(s “1 + 1 = ${1 + 1}”)


	"Hello how are you".split(",").map(_.trim)

	// Process one char at a time
	"hello".filter(_ != 'l').map(_.toUpper)


	println(f"$name is $height%1.2f meters tall")

	toInt, toDouble, toFloat, toLong, toShort etc are used for conversions from string to a type.

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


	import Array.concat
      	var myArr1 = Array(1.9, 2.9, 3.4, 3.5)
      	var myArr2 = Array(8.9, 7.9, 0.4, 1.5)
      	var myArr3 =  concat( myArr1, myArr2)




      	var myList1 = range(10, 20, 2)
      	var myList2 = range(10,20)


	```

### Tuple

	```

	val t = new Tuple3(1, "hello",20.2356)
	val t = (1, "hello",20.2356)
	val sum = t._1 + t._3

	// Iterate a tuple
    	val t = (4,3,2,1)
    	t.productIterator.foreach{ i => println("Value = " + i )} 

	// To String
	t.toString()


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
	         case ex: Throwable => {
	            println("unknown exception"+ex)
	         }

	      } finally {
	         println("Exiting finally...")
	      }
	   }
	}

	```

Throwing Exception 

	```

		def person(age:Int){
			if(age!=15)
				throw new Exception("Wait a little")
			else println("Enjoy your quinceanera")
		}

	```


Either : The Either has two children which are named as Right and Left where, Right is similar to the Some class and Left is same as None class. Left is utilized for the failure where, we can return the error occurred inside the child Left of the Either and Right is utilized for Success.


	```

    	// Defining a method and applying Either 
	    def Division(q: Int, r: Int): Either[String, Int] =
	    { 
	        if (q == 0)  
            		// Left child for failure  
            		Left("Division not possible.") 
        	else
            		// Right child for success 
            		Right(q / r) 
    	    } 
  
	
           // Assigning values  
    	   val x = Division(4, 2) 
  
    	  // Applying pattern matching 
   	   x match
   	   { 
   	   	case Left(l) =>      
   	   		// Displays this if the division is not possible 
   	   		println("Left: " + l) 
      
   	   	case Right(r) =>     
   	   		// Displays this if division is possible 
   	   		println("Right: " + r) 
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

2) Scala allows you to indicate that the last parameter to a function may be repeated. This allows clients to pass variable length argument lists to the function. 

	```
	// “args: String*" is actually Array[String] - Variable Argument / Default values
	def empDetails( id: Int = 50, args:String* ) = { …. }


	```


If we have a requirement like we need to use a Scala’s VarArgs method in a Java Program, then we should mark that Scala’s VarArgs method with @varargs annotation


	```

	@varargs 
	def display(str: String*) {
	    str.map(println)
	  }

	In java class, we can call the above method - 	ScalaVarArgsAndNonVarArgsDemo.display("Rams", "Scala")


	```


3) Partly applied function 

	```
	val date = new Date
	val logProcess = logAnalysis(date, _ : String)
	logProcess(“HTTP Message” )
	logProcess(“Apache Msg” )


	def logAnalysis(date: Date, message: String) = { … }

	```

4) Named Argument

	```

	printAB(b = 5, a = 7)

	```

5) Higher-Order Function - take other functions as argument, or whose return type is a function.

	```
	println( apply( getDisp, 10) )

	def apply(f: Int => String, v: Int) = f(v)

	def getDisp[A](x: A) = "[" + x.toString() + "]"

	```

6) Anonymous Functions

	```

	var inc = (x:Int) => x+1
	var x = inc(7)-1

	var userDir = () => { System.getProperty("user.dir") }
	var mul = (x: Int, y: Int) => x*y

	var myfc1 = (str1:String, str2:String) => str1 + str2
	var myfc2 = (_:String) + (_:String)

	```



7) Currying Function - Currying is a means of transforming a function that takes more than one argument into a chain of calls to functions, each of which takes a single argument. 

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

8) Free Variables

The variables that are used in function but are neither local variables nor formal parameters to the function are called free variables.


	```

	class Marks(m1: Int) {

		var marks : Int = m1
	}


	```

9) Field Overriding - You can only override val fields; this won’t work with vars. This is because we can only read vals, but we can both read and write vars. 

	```

	class Vehicle{
		val wheels=0
	}

	class Car extends Vehicle{
		override val wheels=4
		def show(){
			println("The car has "+wheels+" wheels")
		}
	}

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

1) Traits are used to share interfaces and fields between classes. They are similar to Java 8’s interfaces. Classes and objects can extend traits but traits cannot be instantiated and therefore have no parameters. one trait can inherit another trait by using a extends keyword.



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

	trait BaseSoundPlayer {
	  def play
	  def close
	}	

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

4) Trait with multiple inheritance

	```

           trait A{
                   var length:Int= _
                   def action={
                     length=length+5
                  }
             }

           trait B{
                   var height:Int = _
                   def action={
                     height = height + 1
                  }
             }
           class C extends A with B{
                   length=3;
                   height+=6;
                   override def action={
                            super[A].action
                            super[B].action
                   }
              }

	```

5) You can implement the default methods in Trait.

	```

	trait Pet {
	  def speak { println("Yo") }   // concrete implementation of a speak method
	  def comeToMaster              // abstract
	}

	```

6) Limiting the subclass in a trait

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

7) Adding Trait to an Object Instance: We can also add traits to an object instance. Or in other words, We can directly add a trait in the object of a class without inheriting that trait into the class. 

	```

	class MyClass{} 

	trait MyTrait 
	{ 
	    println("Welcome to MyTrait"); 
	} 

	object Main  
	{ 
      
	    // Main method 
	    def main(args: Array[String]) 
	    { 
          
	        // Here MyTrait is added to the object instance of MyClass 
        	val obj = new MyClass with MyTrait; 
    	    } 
	} 


	```


### Trait Traversable

1) foreach - which can traverse over all the elements of the Collection.

	```
	val x = Array("GEEKS", "FOR", "GEEKS") 
	x.foreach { E => 
			val y = E.toLowerCase
			println(y)
		  }

	```
2) ++ - adds two Traversables together or adds each of the elements of an iterator to a Traversable.

	```

	val x = Set(7, 8, 9, 10) 
        val y = List(1, 5, 8, 18) 
  
        //performing addition operation 
        val s1 = x ++ y 
        val s2 = y ++ x 

	```

3) Map - operations are map, flatMap, and collect. Create a new collection by assigning a few function to the elements of Scala collection.

	```

	 val x = Set(8, 9, 5, 10) 
        // Applying map operation 
        val y = x.map(_ * 9) 



	val q = List(List(7), List(8, 9, 10), List(11, 12, 13))
	// Applying map operation
	val r = q.flatMap(_.map(_ + 3)) 

	
	val f = (i: Int) => List(i - 1, i, i + 1)
	val list = List(5, 6, 7)
	println(list.flatMap(f))
	// prints List(4, 5, 6, 5, 6, 7, 6, 7, 8)



        val x = List(9, 3, 5, 11, 15, 4) 
        // Applying map operation  
        val y = x.collect  
        { 
            // Partial function 
            case z : Int if (z % 3 == 0) => z + 2
        } 



	```

4) Conversion operations - converts toList, toSeq, toArray, toStream, toSet, toMap, toIterable, and toIndexedSeq

	```
	      val q = Set(2, 7, 8, 15, 19)   
              // Converting Set to an Array 
              val r = q.toArray  

	      val x = Set("GfG" -> "CS portal", "Nidhi" -> "a Geek")
	      val y = x.toMap



	```

5) Size info operations are nonEmpty, isEmpty, hasDefiniteSize, and size.

	```

	val x = Map("gfg" -> "cs", "nidhi" -> "geek")

	val y = x.isEmpty 

	val y = x.nonEmpty 

	val r = x.size 

	// hasDefiniteSize is utilized to check if the Traversable collection has finite elements or not
	val r = q.hasDefiniteSize 



	```

6) Element retrieval operations includes last, head, lastOption, headOption, and find. 

	```
	
	val x = Set(12, 13, 14, 15)
	val y = x.lastOption // Output will be Some(15)

	val y = x.last // Output will be 15

	val r = q.head


	val y = x.find(_ % 3 == 0) //Output will be last element that is divisible by 3. Here it is 15


	val p = List(7, 9, 11, 19, 21)  
        val q = List()  
        val r = p.headOption  // Output Some(7)
        val s = q.headOption  // Output None


	```

7) Sub-Collection retrieval operations - are slice, drop, dropWhile, filter, filterNot, tail, take, takeWhile, and init. These operations are utilized to return some sub collection.

	```

	val x = List(17, 19, 21, 29, 31)
	// init retrieves all the elements of the Traversable collection except the last element.
	val y = x.init

	// tail retrieves all the elements of the Traversable collection except the first element.
	val y = x.tail 

	// slice will return the elements from the given range of index excluding last index.
	val y = x.slice(2, 5)

	val y = x.take(2)

	// return all the elements of the collection except the first number of elements given in the argument of drop operation. Output List(29, 31)
	val y = x.drop(3) 


	// dropWhile will drop the elements until the given condition is satisfied and returns rest of the left elements.
	val y = x.dropWhile(_ < 10)


	// takeWhile will take the elements until the given condition is satisfied and returns these elements.
	val y = x.takeWhile(_ < 13)


	val y = x.filter(_ < 23)


	// filterNot will return all the elements which does not satisfies the given condition and drops the rest. 
	val y = x.filterNot(_ < 23)

	```

8) Subdivision operations: These operations include span, partition, splitAt, groupBy. These operations are utilized to break the elements of the collection and return some sub-collections.

	```

	val q = List(7, 9, 11, 15, 17, 19, 22)
	// span will split the given Traversable collection of element into two parts
	val r = q.span(_ < 15) // Output (List(7, 9, 11), List(15, 17, 19, 22))

	// partition will divide the collection into two parts
	val r = q.partition(_ < 35) // Output - (List(7, 9, 11),List(15, 17, 19, 22))

	// splitAt will divide the elements of the collection into two parts in the given position
	val r = q.splitAt(4) // Output - (List(7, 9, 11, 15),List(17, 19, 22))

	```
9) Element test methods: These methods include forall, exists, and count.
	```
	
	val x = List(21, 20, 33, 40, 27, 62)
	// Will return true if all the elements of the collection satisfies the given condition
	val y = x forall (_ < 63) // Output true

	// Will return true if some of the elements of the collection satisfies the given condition
	val y = x exists (_ < 30)

	// Will display the number of elements of the collection which satisfies the given condition.
	val y = x count(_ < 40)

	```


10) Fold: reduceRight, reduceLeft, /: or foldLeft, :\ or foldRight.

	```
	val x = List(8, 6, 4, 2) 


	// zero is an initial value. applies binary operation moving from left to right 
	// and starting with the initial value.
        // val y = x.foldLeft(0)(_ - _) or 
        val y = (0 /: x)(_ - _)   
	// expression evaluvates ((((0 - 8) - 6) - 4) - 2) = -20




	// moving from left to right and ending with initial value.
        // val y = x.foldRight(0)(_ - _) or 
        val y = (x :\ 0)(_ - _) 
	// expression evaluvates (8 - (6 - (4 - (2 - 0)))) = 4


	// reduceLeft moves from left to right, initial value will be first item in collection.
	val y = x.reduceLeft(_ - _) 
	// expression evaluvates (((8 - 6) - 4) -2) = -4


	// x.reduceRight moves from right to left, initial value will be first item in collection.
	val y = x.reduceRight(_ - _)
	// expression evaluvates (8 - (6 - (4 - 2))) = 4



	```

11) Specific fold : operations min, max, product, and sum


	```

	val x = List(3, 4, 7, 10)


	val y = x.sum

	val y = x.product

	val y = x.max

	val y = x.min


	```


12) String : operation addString, mkString, stringPrefix.


	```

	scala> val x = List(7, 8, 9, 10, 11)
	x: List[Int] = List(7, 8, 9, 10, 11)
	scala> val B = new StringBuilder("The numbers are: ")
	B: StringBuilder = The numbers are:



	scala> x.mkString(" < ")
	res30: String = 7 < 8 < 9 < 10 < 11



	// Operation where, “B” is a String builder and “, ” is a separator.
	scala> x.addString(B, ", ")
	res31: StringBuilder = The numbers are: 7, 8, 9, 10, 11



	// stringPrefix will return the name of the collection used.
	scala> x.stringPrefix 
	res32: String = List



	```

### Generic Class & Abstract Class

Abstract Classes are used in 'has-a' or 'uses-a' relationships (e.g. a Cow eats Grass) where as generics are usually 'of' relationships (e.g. List of Ints)

Generic classes are classes which take a type as a parameter.


	```
	Example 1:

	class Stack[A] {

	  private var elements: List[A] = Nil

	  def push(x: A) { elements = x :: elements }

	  def peek: A = elements.head

	  def pop(): A = {
	    val currentTop = peek
	    elements = elements.tail
	    currentTop
	  }
	}

	val stack = new Stack[Int]
	stack.push(1)



	Example 2:

	class Fruit
	class Apple extends Fruit
	class Banana extends Fruit

	val stack = new Stack[Fruit]
	val apple = new Apple
	val banana = new Banana

	stack.push(apple)
	stack.push(banana)

	```

Abstract Classes

	```
	Example 1:

	trait Foo {
	  type T
	  def value: T
	}

	object FooString extends Foo {
	  type T = String
	  def value: T = "ciao"
	}

	object FooInt extends Foo {
	  type T = Int
	  def value: T = 1
	}

	def getValue(f: Foo): f.T = f.value

	val fs: String = getValue(FooString)
	val fi: Int = getValue(FooInt)


	```


### Class


1) Companion Object: A Scala companion object is an object with the same name as a class. 

	```

	class CompanionClass{
		def greet(){
			println("Hello")
    		}

		override def toString = "overriding the toString"
	}

	object CompanionObject{
		def main(args:Array[String]){
			new CompanionClass().greet()
		}
	}

	```

2) Case Class: Case Class is like a regular class, except it is good for modeling immutable data.

	```
	case class Song(title:String,artist:String,track:Int)

	//Shallow Copy 
	val chandelier1=chandelier.copy()
	val chandelier2=chandelier.copy(title=chandelier.artist,artist="Sia")

	```
3) Abstract Class

	```
	abstract class Person{
		def greet()
		def greethello()
	}

	```

4) Constructor Overloading or Auxiliary Constructor 

	```
	
		class Vehicle(model:String,color:String){

			def this(model:String){
				this(model,"Red")
			}

			def disp(){
				println(s"Model $model Color: $color")
			}
		}
		
		var vec = new Vehicle("Hundai")
		vec.disp()	

	```

5) Implicit class - use Implicit Class to add methods to an object without modifying the source code of the object. 

Implicit class 
a) must be defined inside of another trait/class/object.
b) There may not be any method, member or object in scope with the same name as the implicit class.
c) They may only take one non-implicit argument in their constructor.
   implicit class RichDate(date: java.util.Date) // OK!
   implicit class Indexer[T](collection: Seq[T], index: Int) // BAD!
   implicit class Indexer[T](collection: Seq[T])(implicit index: Index) // OK!

	```
	Ex 1:
	object DonutImplicits {
	 implicit class AugmentedDonut(donut: Donut) {
	  def uuid: String = s"${donut.name} - ${donut.productCode.getOrElse(12345)}"
	 }
	}


	Ex 2:
	object Helpers {
	  implicit class IntWithTimes(x: Int) {
	    def times[A](f: => A): Unit = {
	      def loop(current: Int): Unit =
	        if(current > 0) {
	          f
 	         loop(current - 1)
 	       }
	      loop(x)
	    }
	  }
	}
	
	import Helpers._
	5 times println("HI") This is equivalent to val c = new IntWithTimes(4); c.times(println("hello"))

	

	```

### File I/O


      ```

      print("Please enter your input : " )
      val line = Console.readLine
	val num = Console.readInt;

	val result = scala.io.StdIn.readLine()


      import scala.io.Source
      Source.fromFile("Demo.txt" ).foreach { 
         print 
      }


      import java.io._
      val writer = new PrintWriter(new File("test.txt" ))
      writer.write("Hello Scala")
      writer.close()


      import scala.io.Source	
      val s1 = Source.fromFile("data.txt").mkString


      Source.fromFile("data.txt").getLines.foreach { x => println(x) }


      import scala.io.Source
      val it=Source.fromFile("Demo.txt").getLines()
      while(it.hasNext)
         println(it.next())


      ```

## Reference:

https://alvinalexander.com/scala/

https://www.tutorialspoint.com/scala

https://www.journaldev.com/7497

https://www.geeksforgeeks.org/scala-programming-language/




