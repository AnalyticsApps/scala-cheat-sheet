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

	If(condition1) {
	  ….
	} else if(condition 2){
	  ….
	} else  {

	}

2) WHILE / Do .. Whille Loop

	while(condition) {
	   …..
	}


	do {
	  …..
	} while(condition)


3) For Loop
	
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


4) Break

    import util.control.Breaks._
    for (i <- 1 to 10) {
        breakable {
            if (i % 2 == 0) break
            ….
        }
    }


### Functions

1) Scala function's name can have characters like +, ++, ~, &,-, --, \, /, :, etc.
Scala allows you to define functions inside a function and functions defined inside other functions are called local functions.

	
	def functionName ([list of parameters]) : [return type] = {
   	  function body
       return [expr]
	}

Scala allows you to indicate that the last parameter to a function may be repeated. This allows clients to pass variable length argument lists to the function. 

	// “args: String*" is actually Array[String] - Variable Argument / Default values
	def empDetails( id: Int = 50, args:String* ) = { …. }

2) Partly applied function 

	val date = new Date
     val logProcess = logAnalysis(date, _ : String)
	logProcess(“HTTP Message” )
	logProcess(“Apache Msg” )


	def logAnalysis(date: Date, message: String) = { … }


3) Named Argument

	printAB(b = 5, a = 7)

4) Higher-Order Function - take other functions as argument, or whose return type is a function.

	println( apply( getDisp, 10) )

	def apply(f: Int => String, v: Int) = f(v)

	def getDisp[A](x: A) = "[" + x.toString() + "]"


5) Anonymous Functions

	var inc = (x:Int) => x+1
	var x = inc(7)-1

	var userDir = () => { System.getProperty("user.dir") }
	var mul = (x: Int, y: Int) => x*y


6) Currying Function - Currying is a means of transforming a function that takes more than one argument into a chain of calls to functions, each of which takes a single argument. 

	We are taking this approach because our vat and serviceCharge will not change very often. So, let's use currying to split our method. 
	We have reduced our method from accepting 3 parameters to accept one parameter. So, we have split our method in such a way that we don't have to provide all the arguments at the same time. 
	I can provide these arguments whenever they are available. This transformation is called currying.

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





