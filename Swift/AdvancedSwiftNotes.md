# Advanced Swift Notes

## Computed Properties, Getters, Setters, and Observable Properties

- **Computed Properties** are variables created by code you write within the variable.

```swift
import UIKit

// observed property - monitors the property's value when it is changed.
// This lets you initalize code when a property's value is changed.
// for example we don't the size of the pizza to be unrealistic (33 inches for example)
var pizzInInches: Int = 10 {
    // monitors the value before the property's value is changed.
    willSet {
        // if you want access to the oldValue use:
//        print(pizzInInches) outputs --> 10
//        print(newValue) outputs --> 8
        
    }
    
    
    // monitors the value after the property's value is changed.
    didSet {
        // if you want access to the newValue use:
//        print(pizzInInches) outputs --> 8
//        print(oldValue) outputs --> 10
        
        if pizzInInches >= 18 {
            print("Invalid size specified, pizzaInInches set to 18.")
            pizzInInches = 18
        }
    }
    
}

//pizzInInches = 8
pizzaInInches = 33
print(pizzInInches)

var numberOfPeople: Int = 6
let slicesPerPerson: Int = 4

// computed property - must declare a data type, must have curly braces to intialize code that will affect the variable.
var numberOfSlices: Int {
    // this part of the computed property is called a getter.
    get {
        return pizzaInInches - 4
    }
}

var numberOfPizzas: Int {
    get {
        let numberOfPeopleFedPerPizza = numberOfSlices / slicesPerPerson
        return numberOfPeople / numberOfPeopleFedPerPizza
    }
    // setter will execute whenever this property gets a newValue set to it.
    // the setter will execute the second when the property's value is changed.
    set {
        let totalSlices = numberOfSlices * newValue
        numberOfPeople = totalSlices / slicesPerPerson
    }
}

numberOfPizzas = 4

print(numberOfPeople)
```

- Computed Properties Challenge 

```swift
import UIKit

// Advanced Swift Properites Challenge
// Computed Paint Calculator

var width: Float = 3.6
var height: Float = 2.3

// 1 bucket of paint for 1.5sqm
let paintSquareFootage: Float = 1.5

var bucketsOfPaint: Int {
    get {
        let wallSqaureFootage = width * height
        let numberOfBuckets = wallSqaureFootage / paintSquareFootage
        let roundedNumberOfBuckets = ceilf(numberOfBuckets)
        return Int(roundedNumberOfBuckets)
    }
    set {
        let totalSquareFootageOfPaint = paintSquareFootage * Float(newValue)
        return print("These buckets of paint can cover an area of \(totalSquareFootageOfPaint)sqf.")
    }
}

print(bucketsOfPaint) // --> 6

bucketsOfPaint = 8 // --> These buckets of paint can cover an area of 12.0sqf.
```

## Swift Access Levels

- These are like clearance for the FBI.  
- Swift has 5 different access levels as of Swift 4.0
  
| Swift Access Levels (most restrictive to least restrictive) | Accessibility |
| :--: | :--: |
|  1. private | { only accessible within this block of code }  |
| 2.fileprivate | your method or property is only accessible within the file it is in.  |
| 3. internal | your method or property is accessible within the workspace you've put them in.  This is the **default** access level given to properties and methods. |
| 4. public | this is the access level given to APIs and Cocoapods (for example when you implement a Cocoapod and there are two public files within your workspace). |
| 5. open | is much like a public+ anybody can do anything they want to your properties and methods. |

**NOTE**  Most iOS devs will only work with 1-3, however devs who work on APIs and Cocoapods will use 4 and 5 as well because their module or framework need to be exposed and overridden to other devs.

## Stucts vs Classes

- Struct vs Class - Which one is better?
  - There is no such thing?
  - They are the best when they are used for a certain purpose.
  - For example:
    - If you need inheritance, you need to use a **class**.

- The Stack vs Heap
  - This is what effects your Random Access Memory or RAM.
  - The Stack and Heap are different ways to organize memory in the device's RAM.
  - The Stack = memory that is stacked from top to bottom
  - The Heap =  memory that is piled on with no organization

-  Stack and Heap in Regards to Structs and Classes
   -  Structs live on the Stack in a **First In Last Out** system.
      -  The **first** piece of data that went into the Stack will be the **last** one to be popped off.
      -  Which is important because the latest piece of data will be quick to access when you need it.
      -  Structs are Value Types which mean they store the **actual** data value of the struct.
   - Classes live in the Heap.
     - When they are intialized, they are allocated in memory in the Heap, however they also have a reference in the Stack.
     - Classes are Reference Types which means they store a reference on the Stack that references block of memory in the Heap.

**NOTE** - Value vs Reference Types: Value types makes an exact copy of the value allocated in memory.  Where reference types copy only the reference, or instructions on how to locate the reference in the Heap.

```swift
// example of Value Type vs Reference Type
import Foundation

class ClassHero {
    var name: String
    var universe: String
    
    // initalizes the variables
    init(name: String, universe: String) {
        self.name = name
        self.universe = universe
    }
}

struct StructHero {
    
    var name: String
    var universe: String
    
}

var hero = ClassHero(name: "Iron Man", universe: "Marvel")

var anotherHero = hero
anotherHero.name = " The Hulk"

print("hero name = \(hero.name)") //--> The Hulk
print("anotherHero name = \(anotherHero.name)") //--> The Hulk

// Another example of why you need to be careful with classes:
var avengers = [hero, anotherHero]
avengers[0].name = "Thor"

print("hero name = \(hero.name)") //--> Thor
print("anotherHero name = \(anotherHero.name)") //--> Thor
print("first avengers' name = \(avengers[0].name)") //--> Thor

var hero2 = StructHero(name: "Iron Man", universe: "Marvel")

var anotherHero2 = hero2
anotherHero2.name = "The Hulk"

print("hero2 name = \(hero2.name)") //--> Iron Man
print("anotherHero2 name = \(anotherHero2.name)") //--> The Hulk

```

**NOTE** - This is an advantage of structs.  Structs are more predictable when constructing your code.

- Immutability in Structs and Classes.

```swift
// Classes are mutable even though they are set as a constant.
let hero = ClassHero(name: "Iron Man", universe: "Marvel")

hero.name = "Cat Woman"

print(hero.name) //--> Cat Woman

let hero2 = StructHero(name: "Iron Man", universe: "Marvel")
hero2.name = "Cat Woman" //--> throws an error about about constant being immutable.
```

**NOTE** - Because the class was initialized with variables, the only piece of the above code that is a constant is the hero part, not the actual _ClassHero_.

| Structs | Classes |
| :--: | :--: |
| Simpler | Has inheritance |
| Faster | Works with Objective C code |
| Deep Copies |  |
| True immutability |  |
| No Memory Leaks |  |
| Threadsafe |  |
| Apple's advice: Start with a struct by default, and if you need inheritance from other classes or Objective C then convert over to a class. | Only use classes if you need inheritance from other classes and/or Objective C classes |

## Touples

- Touples are a shorthand way of creating a dictionary.

```swift
import UIKit

let touple1 = ("Taylor", 37)

print(touple1.0)
print(touple1.1)

let touple2 = (name: "Taylor", age: 37)

print(touple2.name)

let touple3: (name: String, age: Int)

touple3 = (name: "Taylor", age: 37)

print(touple3.name)
```