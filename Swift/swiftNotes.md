# Getting Started With Swift

- [Getting Started With Swift](#getting-started-with-swift)
  - [In Xcode you want to use the ViewController.swift](#in-xcode-you-want-to-use-the-viewcontrollerswift)
  - [Changing the Properties of an Element with Dot.Notation.](#changing-the-properties-of-an-element-with-dotnotation)
  - [Detecting User Interactions](#detecting-user-interactions)
  - [Swift Deep Dive #1](#swift-deep-dive-1)
    - [Naming Conventions](#naming-conventions)
    - [Commenting](#commenting)
  - [Print Statement](#print-statement)
  - [Swift Deep Dive #2](#swift-deep-dive-2)
    - [Variables](#variables)
    - [Constants](#constants)
    - [Lazy Variables](#lazy-variables)
  - [Sandboxing](#sandboxing)
  - [DataBases](#databases)

## In Xcode you want to use the ViewController.swift

- Unlike the **Main.storyboard** file (used for designing your app), the **ViewController.swift** file is used for swift development and implementing swift code.
  - Essentially the **Main.storyboard** is the _design file_ and the **ViewController.swift** is the _code file_.
- Whenever you create an app with Xcode it comes preinstalled with a template in the **ViewController.swift** file.  
  - But how do you get the **ViewController.swift** and the **Main.storyboard** to communicate with each other?
    - Answer the **assistant editor** helps you out.
      - The **assistant editor** puts the **Main.storyboard** and the **ViewController.swift** side by side for you to code while looking at the desing.
- However, to communicate between the UI elements on the app and the swift code, you must create a IBOutlet (Interface Builder = **Main.storyboard**).
- To create an IBOutlet hold control^, click the element, and drag the element to the desired spot in the code.
  - You will then name your variable it will be set as an IBOutlet.
    - All variable names are written in camelcase = myNameApp
  - If you want to change the variable name you need to right click the variable, choose rename, and Xcode will rename all the places your code is written.

## Changing the Properties of an Element with Dot.Notation.

- Syntax for Dot.Notation = Who.What = Value
  - Who = Who needs to be changed?
  - What = What property of Who needs to be changed?
  - Value = To what should What be changed to?

Example:

```swift
// WHO        .WHAT  = VALUE
diceImageView1.image = #imageLiteral(resourceName: "DiceSix")
diceImageView1.alpha = 0.5
diceImageView2.image = #imageLiteral(resourceName: "DiceTwo")
```

## Detecting User Interactions

- Much like creating IBOutlets for elements on the app, creating a IBAction for a button is the same by holding control^, click the element, and drag the element to the desired spot in the code.
  - However, instead of naming the variable with IBOutlet, you are naming a function that will do something when the button is pushed or "Touched Up Inside".

For example:

```swift
@IBAction func rollButtonPressed(_ sender: UIButton) {
        //print function like in Python and console.log() in JS
        print("Button got tapped.") // use double quotes with Text
        diceImageView1.image = #imageLiteral(resourceName: "DiceFour")
        diceImageView2.image = #imageLiteral(resourceName: "DiceFour")
    }
```

## Swift Deep Dive #1

### Naming Conventions

- camelCase / Used in JS and Swift
- kebab-case / web dev
- snake_case / CSS

### Commenting

- Like JS, Swift uses // to begin a comment and comment out a line.
- For multiple lined comments use /* */ like JS

## Print Statement

```swift
print("Hello World!")

//If I want input code into a string use String Interpolation \(some code)
print("Hello \(2+3) World")
// outputs "Hello 5 World\n"

```

**NOTE**: Use _Playground_ to mess around with code before implementing it in your app.

## Swift Deep Dive #2

### Variables

- Data that is associated with a variable or label that is used to reference the data whenever it is needed by the program. 

```swift
var firstName = "taylor"
var lastName = "patterson"

print("My full name is \(firstName) \(lastName)")
//output --> My full name is taylor patterson

//Variable Challenge
var a = 5
var b = 8

//Challenge is to make print(a) = 8 and print(b) = 5 without changing the code and writing new integers

//Solution:


print(a)
print(b)
```

### Constants

- Much like variables, constants associate a label that is used to reference the data whenever it is needed by the program. **However**, constants are immutable which means they cannot be mutated or changed.
- Much like JS, best practice is to use constants unless you know you will mutate the variable later in the code.

```swift
let myName = "Taylor Patterson"

myName = "T.P."

print("myName")
//outputs --> Swift throws an error saying that it cannot be mutated.
```

### Lazy Variables

- Lazy variables are variables that will only be loaded up when the program needs them or when they are called upon which helps with memory. This example is from CoreData

```swift
lazy var persistentContainer: NSPersistentContainer = {
  let container = NSPersistentContainer(name: "DataModel")
        container.loadPersistentStores(completionHandler: { (storeDescription, error) in
            if let error = error as NSError? {
                fatalError("Unresolved error \(error), \(error.userInfo)")
            }
        })
        return container
}()

## Swift Deep Dive #3

### Arrays

- Arrays are data types that hold collections of data.  
  
```swift
//variable for the array
var family = [Carrie, Em, Scout]

//Get the index of 1
print(family[1])
//outputs --> Em

var numbers = [45, 73, 195, 53]

var computedNumbers = [
    numbers[0] * numbers[1],
    numbers[1] * numbers[2],
    numbers[2] * numbers[3],
    numbers[3] * numbers[0]
]

print(computedNumbers)
//outputs --> [3285, 14235, 10335, 2385]
```

### 1D Arrays vs 2D Arrays

- 1D Array: normal array were values are separated by commas placed inside a **single** array.

```swift
let quiz = [
        "Four + Two is equal to Six.",
        "Five - Three is greater than One.",
        "Three + Eight is less than Ten."
    ]

//To access the values inside the array you use the following syntax: array[i]
print(quiz[1])
//outputs the second index
```

- 2D Array: these are nested arrays inside one array:

```swift
let numbers = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
]

//To access certain values inside the array you use the following syntax: array[i][j]
print(numbers[2][2])
//outputs --> 9
```

**NOTE** 2D arrays symboled like this ```[[array]]```.

## Swift Deep Dive #4

### Basic Data Types

- String = "Characters(text)"
- Int(Integer/Whole Number) = 12
- Float (Floating Point Number) = 12.345
- Double (Has double the amount of data than a float/Scientific Calc) = 3.14159265359
- Bool (Boolean) = true / false

### Randomization in Swift

- Two ways to find a Random Int:

```swift
let randomNumber = Int.random(in: 1...3)

print(randomNumber)
```

### Range Operator

- In swift there are open and closed range operators.
    - closed range operator is ```...```
    ```swift
    Int.random(in: 1...3)
    //outputs 1, 2, or 3
    ```
    - half open range operator includes the lower and all of the middle data, but excludes the higher data.
    ```swift
    Int.random(in: 1..<3)
    //outputs 1 or 2, but not 3
    ```
    - If you wanted to change from Int to Float just change the data type!
    ```swift
    Int.random(in: 1..<3)
    Float.random(in: 1...3)
    ```
    - Booleans can also use range operator using ```random()```:
    ```swift
    Bool.random()
    //outputs true or false
    ```
    - Range operators with Arrays:
    ```swift
    array[Int.random(in: 0...5)] /* outputs a random number using 1 through 5 */
    array.randomElement() /* Also outputs a random number between 1 through 5 */
    array.shuffle() /* Randomly shuffles the index of the array as well as the randomly outputs that number */
    ```

## Deep Dive #5 Functions and Scope

### Functions

- You create functions with this syntax:

```swift
func getMilk() { /* do stuff */ }
```

- You then call the function  with this syntax:

```swift
getMilk()
```

- Functions pack a lot of actions together within the block to do something. 

Simple example of function:

```swift
func greeting() {
    print("Hello")
    print("Hello")
    print("Hello")
    print("Hello")
}

greeting()
//outputs hello, hello, hello, hello
```

or 

```swift
func greeting() {
    print("Hello")
}

greeting()
greeting()
greeting()
greeting()
//Will get the same output as above
```

### Scope

- Swift scope is much like JS.  The variables nested inside a function can only be used by that function.  

### Functions with Inputs

- Syntax:

```swift
func myFunction(parameter: DataType) {
  //Do something with input
}

myFunction(parameter: argument)

//Examples:
func greeting(name: String) {
    print("Hello, \(name)!")
}

greeting(name:"Taylor")
//outputs --> Hello, Taylor!

func getMilk(bottles: Int) {
  var cost = bottles * 1.5
  print(cost)
}

getMilk(bottles: 2)
//outputs: 3

// Function Challenge
//Don't change this code:
func calculator() {
  let a = Int(readLine()!)! //First input
  let b = Int(readLine()!)! //Second input
  
  add(n1: a, n2: b)
  subtract(n1: a, n2: b)
  multiply(n1: a, n2: b)
  divide(n1: a, n2: b)


//Write your code below this line to make the above function calls work.

func add(n1: Int, n2: Int) {
  print(n1 + n2)
}

func subtract(n1: Int, n2: Int) {
  print(n1 - n2)
}

func multiply(n1: Int, n2: Int) {
  print(n1 * n2)
}

func divide(n1: Int, n2: Int) {
  /* Could also have done this:
  let decimalN1 = Double(n1)
  let decimalN2 = Double(n2)
  print(decimalN1 / decimalN2) */

  print(Double(n1) / Double(n2))
}

calculator()

//One more example of Double and Int
func getMilk(bottles: Int) {
  // Without converting the int to a double, this code doesn't work.
    print(Double(bottles) * 1.5)
}

getMilk(bottles: 2)
```

### Functions with Outputs

- Syntax:

```swift
//    Name     parameters   Return Arrow    Return Type
func getMilk  (money: Int)       ->             Int {
  let change = money - 2
//Return Keyword   Return Value
      return          change

//Calling a function with outputs
//variable with return value and output (function with argument).
var change = getMilk(4)
}
```
#### 3 Types of Functions

```swift
//Vainlla Function (no input / no output)
func greeting1() {
    print("Hello, Taylor!")
}

greeting1()

//Function with input
func greeting2(name: String) {
    print("Welcome, \(name)! Here's your entry music.")
}

greeting2(name: "Taylor")

//Function with output
func checkingUserEntry(name: String) -> Bool {
    if name == "Taylor" || name == "Carrie" || name == "Em" || name == "Scout" {
        return true
    } else {
        return false
    }
}

var userAccess =  checkingUserEntry(name: "Larry")

func openDoor() {
    if userAccess == true {
        print("Come on in!")
    } else {
        print("Sorry, I don't know you...")
    }
}

openDoor()
```

### Creating DataTypes

- Two ways to create variables with DataTypes in Swift:

```swift
var number =  1234 //Here we let Swift infer the DataType
var number: Int = 1234 //Here we assign the DataType ourselves

var name = "Taylor"
var name: String = "Taylor"
```

### Type Inference

- Swift is pretty smart, like JS, it will infer what data type you are declaring to the variable without having to state the DataType with ```:String``` or ```:Int```.  It looks for clues ("", ., true / false, [], {}) and then infers which DataType you are using.

- Unlike, JS though, Swift cannot and will not infer a DataType.  So, if you reference you have a variable that holds an ```:Int``` DataType, then you can **ONLY** use the ```:Int``` DataType with that variable. Same goes for all DataTypes.

### How to Find the DataType of a Variable?

- Xcode has a neat shortcut:
  - You can find the DataType of a variable by holding the "option" key and click then name of the variable and it will show you the DataType of that variable.

## Deep Dive #6 Conditionals

Conditional statements use conditions to set actions to happen if and when something thing happens.

### If / Else Statments

- If / Else statements are much like JS besides some syntax differences.

```swift
if trafficLight == "green" { 
    go()
  } else if trafficLight == "yellow" {
    useYourJudgement()
  } else { 
    stop()
  }

func loveCalucation() {
    let loveScore = Int.random(in: 0...100)
    
    if loveScore == 100 {
        print("Y'all love each other like Kayne loves Kayne.")
    } else {
        print("Sorry, you'll be forever alone...")
    }
    
    print(loveScore)
}

loveCalucation()
```

#### Comparison Operators

- ```==``` Is **equal** to
- ```!=``` Is **not equal** to
- ```>``` Is **greater** than
- ```<``` Is **lesser** than
- ```>=``` Is **greater or equal** to
- ```<=``` Is **lesser or equal** to

#### Logical Operators

- Logical AND (```a && b```)
- Logical OR (```a || b```)
- Logical NOT (```!a```)

### Switch Statements

- Switch statement syntax:

```swift
switch hardness {
  case "Soft":
    print(5)
  case "Medium":
    print(7)
  case "Hard":
    print(12)
  default:
    print("Error")
}
```

- A switch statement, much like an If/Else statement, matches cases with conditionals.  The default at the end is the "catch-all" if no case it matched then the default will run.

- Conditional operators are different in a swift statement.  Swift statements use **ranged operators**:

- **closed range operator** (```a...b```) defines a range that runs from a to b, including values a and b.
- **half-open range operator** (```a..<b```) defines a range that runs from a to b, including value a but excluding value b.
- **one-sided range operator** (```...a``` or ```a...```) defines a range that starts from from the beginning and stops at a including the value a, or starts with value a and continues for the rest of the range. 

```swift
switch loveScore {
    case 81...100:
        print("Y'all love each other like Kayne loves Kayne.")
    case 41..<81:
        print("You go together like Coke and Mentos.")
    case ...40:
        print("Sorry, you'll be forever alone...")
    default:
        print("Error")
    }
```

#### When to use a Switch Statement or If/Else Statement?

- It is best practice to use If/Else statements when there are less than 5 cases, so as to not search through many conditionals with an if/else.

```swift
if conditions > 5 {
  useSwift()
} else {
  useIfElse()
}
```

## Deep Dive #7 Dictionaries

- Syntax:

```swift
//  Name      Key     :     Value     Pairs
var dict = ["Brewery" : "a place where beer is made",
            "Bar": "a place where beer is sold"]

var contacts : [String : Int ] = ["Taylor" : 3346982212,
                                  "Carrie" : 4567893412]

dict["Angela"] //Provide the key get the value

//Updating and modifying a dictionary:
var stockTickers: [String: String] = [
  "APPL" : "Apple Inc",
	 "HOG" : "Harley-Davidson Inc",
	"BOOM" : "Dynamic Materials",
 "HEINY" : "Heineken",
	 "BEN" : "Franklin Resources Inc"]

func updateMyTickers() {
  stockTickers["WORK"] = "Slack Technologies Inc"
  stockTickers.updateValue("DMC Global Inc", forKey: "BOOM")
}
  
updateMyTickers()

 print(stockTickers["WORK"]!)
 print(stockTickers["BOOM"]!)
```

## Deep Dive #8 Optionals

- There are 3 different optionals: ```!```, ```?```, or ```Nil```

```swift
var hardness : String //--> This variable can only hold a string datatype.

var hardness : String? //--> This variable can hold a string datatype or an optional datatype == Nil

var player1Username: String? = nil //--> Sets the variable as an empty string. However, it cannot be printed as is.

player1Username = "taylorisawesome" //--> Sets the variable string

print(player1Username) //--> outputs Optional("taylorisawesome")
print(player1Username!) //--> ! unpacks the variable and outputs taylorisawesome

//One way to test and make sure you only print with the ! is to use a if statement:
if player1Username != nil{
  print(player1Username!)
}
```

- **NOTE** Dictionaries always output optionals!

### Structures, Methods, and Properties

- **Remember** prebuilt - basic data types are "Strings", Int, Float, Double, Bool, Array, Dictionary

#### But what if we needed a custom data type?

- Structures == Blueprints for objects in Swift where we can plan ahead of what it will be.  
  - Structures are composed of properties and methods:
    - **Properties** are variables created within the structure (What the structure will be like)
      - **Computed Properties** are variables created by code you write within the variable.
  
      ```swift
      <!-- Computed property syntax: -->
      var computedProperty: dataType {
        return someAction
      }
      ```

    - **Methods** are functions created within the structure (What the structure can do)

```swift
//defining a Structures:
//Names must be capitalized!
struct MyStruct{}

struct Town{
    //defining properties
    let name = "Taylorland"
    var citizens = ["Taylor", "Carrie", "Em"]
    var resources = ["Grain": 100, "Ore": 42, "Wool": 75]
    var population = 1000

    // computed properties
    var amountInReserve: String {
      switch population
      case 100...500:
        return "need more people"
      case 501...1500:
        return "just about right"
      case 1501...3000:
        return "need to trim the fat"
    }

    //defining methods (functions inside a structure)
    func fortify() {
      print("Defences increased!")
    }
}

//initializing a Structure:
var myTown = Town()

print(myTown.citizens) //--> Taylor, Carrie, Em
print("\(myTown.name) has \(myTown.resources["Grain"]!) bags of grain.")

//modifying a structure:
myTown.citizens.append("Scout") //.append == adds to the array
print(myTown.citizens.count) //.count == counts the items in an array

//initializing a method
myTown.fortify()

//Using init() to create the blueprint of the Town struct so we can build unique structures from the blueprint.

struct Town{
    // default properties
    var name = String()
    var citizens = [String]()
    var resources = [String: Int]()

    //init syntax for initializing the blueprint
    init(name: String, citizens: [String], resources: [String: Int]) {
        //self refers to the default properties
        self.name = name
        self.citizens = citizens
        self.resources = resources
    }
    
    func fortify() {
      print("Defences increased!")
    }
}

//defining a new town(s)
var anotherTown = Town(name: "Valdosta", citizens: ["Honey", "Dennis"], resources: ["Cotton" : 37])
anotherTown.citizens.append("JP")
print(anotherTown.citizens)

var ghostTown = Town(name: "Ghostville", citizens: [], resources: ["Tumbleweed": 1])
ghostTown.fortify()

//structure exercise:
struct User {
    var name: String
    var email: String?
    var followers: Int
    var isActive: Bool
  
  init(name: String, email: String?, followers: Int, isActive: Bool) {
    self.name = name
    self.email = email
    self.followers = followers
    self.isActive = isActive
  }
  
  func logStatus() {
    if self.isActive == true {
      print("\(self.name) is working hard!")
    } else {
      print("\(self.name) has left earth...")
    }
  }
}

var nixon = User(name: "Richard", email: "", followers: 0, isActive: false)
print(user1)
user1.logStatus()

var musk = User(name: "Elon", email: "elon@tesla.com", followers: 2001, isActive: true)
musk.logStatus()
print("Contacting \(musk.name) on \(musk.email!) ...")
print("\(musk.name) has \(musk.followers) followers")
// sometime later
musk.isActive = false
musk.logStatus()
```

## Deep Dive #9 Immutability

- Remember: variables with the ```let``` keyword are immutable which means they cannot be changed.  If you wanted to modify a ```let``` keyword you would have to destroy the variable and re-construct it.
  - Variable Keywords
    - ```var``` == mutable (can change)
    - ```let``` == immutable (cannot change) or != mutable

Take for instance this code:

```swift
struct Town {
  let name: String
  var citizens: [String]
  var resources: [String : Int]
  
  init(name: String, citizens: [String], resources: [String : Int]) {
      self.name = name.uppercased()
      self.citizens = citizens
      self.resources = resources
    }

  mutating func harvestSnuggles() {
// We use mutating here because in front of resources there is an understood
// let = self.  which makes this variable immutable.  A workaround is to use
// the keyword "mutating" to switch the keyword let to var which will make the
// variable mutable. 
      resources["Snuggles"] = 300
    }
}
 
var myTown = Town(name: "Taylorville", citizens: ["Taylor", "Carrie", "Em"],resources: ["Hug": 100, "Kisses": 200, "Chocolate": 50])

print("Hello people of \(myTown.name)! I am God...")

myTown.citizens.append("Scout")
print(myTown.citizens)

myTown.harvestSnuggles()
print(myTown.resources)
```

**Essentially**: There are two types of methods in a struct

1. Play method = doesn't change anything about the struct

```swift
func battleCry() {
  print("We must protect this town!")
}
```

2. Mutating method = can change something about the struct

```swift
mutating func buidingAxes() {
  resources["axes": 400]
}
```

## Deep Dive #10 Classes

- **Classes** are a lot like structs in that they build the blueprint for objects.

- How to **define** a class?

**NOTE** -  It is common convention to write classes on a separate file, and name that file the same as your class.

```swift
// Basic Example
class MyClass { }

// More appropriate Example
class Enemy {
    var health = 100
    var attackStrength = 10
    
    func move() {
        print("walk forwards.")
    }
    
    func attack() {
        print("Land a hit, does \(attackStrength) damage")
    }
}
```

-  How to **initialize** a class?

**NOTE** - Initializing a class happens on the _main.swift_ file.

```swift
          // Initialized
let skeleton = Enemy()
print(skeleton.health)
skeleton.move()
skeleton.attack()

let skeleton2 = Enemy()
let skeleton3 = Enemy()
```

- Although you might think that **classes** are basically structs, think again. 
  - The big difference between **classes** and structs is the **classes** ability to inherit from a **superclass**.
- Think about the **superclass** like a parent.  The **superclass** will then "teach" what it knows the child or **subclass** where the **subclass** inherits all of the methods and properties of the **superclass**.
  - Hence the idea of inheritance.

```swift
class MyClass: SuperClass { }

// on Dragon.swift file:
// declaring subclass Dragon of superclass Enemy
class Dragon: Enemy {
  // New variable only available to Dragon and it's subclasses.
  var wingSpan = 2
  // New func only available to Dragon and it's subclasses.  
  func talk(speech: String) {
        print("Says: \(speech)")
  }
// The function is from the superclass Enemy, but Dragon is overriding the
// functionality to match Dragon's needs.
  override func move() {
        print("Fly forwards.")
  }
// This function is also from superclass Enemy, but Dragon wants to add to the
// original function.  So, we must add super.nameOfFunctionFromSuperclass() to
  override func attack() {
      //This function will run first
        super.attack()
      //Then this one.
        print("Spits fire, does 40 damage.")
  }
}

// on main.swift file:
// initializing the class
let dragon = Dragon()
dragon.wingSpan = 5
dragon.attackStrength = 15
print(dragon.wingSpan) //--> 15
dragon.talk(speech: "My teeth are swords! My claws are spears! My wings are a hurricane!")
// --> "Says: "My teeth are swords! My claws are spears! My wings are a hurricane!"
dragon.attack()
// Lands a hit and does 15 damage
// Spits fire, does 40 damage.
dragon.move()
// Fly forward.
```

### Inheritance in UIKit

- Following the superclass (most basic) to the subclass (most specific) -->
  - **NSObject** - the most basic
    - **UIResponder** - inherits from NSObject and has it's own capabilities
      - **UIView** - inherits from NSObject and UIResponder
        - **UIControl** - inherits from NSObject, UIResponder, UIView
          - **UIButton** - inherits from NSObject, UIResponder, UIView, and UIControl

### Differences between Classes and Structs

1. One key major difference is classes have the ability to inherit properties and methods from a superclass.
2. Another difference is in **structs** you do not have to ```init()``` for properties that are empty variables, however for **classes** you do.

```swift
//struct
struct Enemy {
    var health: Int
    var attackStrength: Int
 
    func attack() {
        print("Landed strike with \(attackStrength) points.")
    }
}

let skeleton1 = Enemy(health: 100, attackStrength: 10)
skeleton1.attack() //-->Landed strike with 10 points.

//class
struct Enemy {
  var health: Int
  var attackStrength: Int

  init (health: Int, attackStrength: Int) {
    self.health = health
    self.attackStrength = attackStrength
  }

  func attack() {
    print("Landed strike with \(attackStrength) points.")
  }
}

let skeleton1 = Enemy(health: 100, attackStrength: 10)
skeleton1.attack() //-->Landed strike with 10 points.
```

3. **Classes** are passed by **reference** where **Structs** are passed by **value**; this makes **classes** more complex and more error prone.

```swift
//CLASSES ARE PASSED BY REFERENCE
let skeleton1 = Enemy(health: 100, attackStrength: 10)
// Essentially, this is NOT making a copy but another reference to skeleton1
let skeleton2 = skeleton1

skeleton1.takeDamage(amount: 15)

print(skeleton2.health) //--> 90
print(skeleton2.health) //--> 90

//STRUCTS ARE NOT PASSED BY REFERENCE AND ARE COMPLETE COPIES OF EACH OTHER
var skeleton1 = Enemy(health: 100, attackStrength: 10)
let skeleton2 = skeleton1

skeleton1.takeDamage(amount: 15)

print(skeleton2.health) //--> 100
print(skeleton1.health) //--> 85
```

### Choosing Between Structs and Classes

| Structures | Classes |  
| -- | -- |
| ```struct MyStruct { }``` | ```class MyClass: SuperClass { }``` |
| Immutable (Cannot manipulate) | Mutable |
| Passed by Value (can copy the value (data)) | Passed by Reference (more than variable that points to the same object) |
| Cannot inherit properties or methods | Inheritance = SubClasses can inherit properties and methods from SuperClasses |
| By default, Apple suggests you use structures | Use Classes when you need Objective-C interoperability |
| Use Structures along with protocols to adopt behavior by sharing implementations | Use Classes when you need to control the identity of the data you're modeling (**NEED Inheritance**) |

**NOTE** - For more info check out these two documentation:
[Apple Developer](https://developer.apple.com/documentation/swift/choosing_between_structures_and_classes#overview), and [Swift Documentation](https://docs.swift.org/swift-book/LanguageGuide/ClassesAndStructures.html)

## Deep Dive #11 Optional Binding, Chaining, and the Nil Coalescing Operator

### Using Optionals ?

1. Force Unwrapping = ```optional!```
   1. Force unwrapping **optionals** is the simplest way to use **optionals**, however it is also the error prone and takes a lot of concentration to keep tabs on where your **optionals** could return a _nil_ datatype. 
      1. For example:

```swift
let myOptional: String? //Datatype = String? (optional)
myOptional = "Taylor"

//This will throw an error b/c text = String where myOptional = String?
let text: String = myOptional

//To get around this, you force unwrap the optional
let text: String = myOptional!

//However, if at any point the myOptional returns a nil datatype:
myOptional = nil

//Then the app will crash by force unwrapping the optional
let text: String = myOptional!

```

2. Check for nil value = ```if optional != nil { optional! }```
   1. A much safer way (and **VERY** commonly used out in the wild) to force unwrap optionals is by checking if the optional is nil **FIRST** then force unwrapping the optional.
      1. For example:

```swift
let myOptional: String?
myOptional = nil

// We are going to check if the optional is nil before we force unwrap the optional
if myOptional != nil {
  // You must sill force wrap the optional with !
  let text: String = myOptional!
} else {
  print("myOptional was found to be nil, so it was skipped.")
}

//Rather than crashing the app,
//Output --> myOptional was found to be nil, so it was skipped.
```

3. Optional Binding = ```if let safeOptional = optional { safeOptional }```
   1. Because checking for _nil_ value(s) are so common, Swift has built in functionality (aka optional binding) that helps you handle **optionals** with ```if let``` conditional.
      1. For example:

```swift
let myOptional: String?
myOptional = "Taylor"

//Using optional binding to check for nil
if let safeOptional = myOptional {
  // notice how we didn't have to force unwrap the optional.
  let text: String = safeOptional
  print(text) //--> outputs Taylor
  print(safeOptional)//--> Also outputs Taylor
} else {
  print("myOptional was found to be nil, so it was skipped.")
}
```

4. Nil Coalescing Operator = ```optional ?? defaultValue```
   1. What if we wanted to provide a default value where the **optional** is equal to _nil_? In this case we would use the nil coalescing operator ```??```.  This operator checks to see if the **optional** is _nil_ and if it is then sets the **optional** to the the defaultValue
      1. For example:

```swift
let myOptional: String?
myOptional = nil

// this checks to see if the optional is nil, if isn't then myOptional will be set to text
// if myOptional is set to nil, then it will set to the default value
let text: String = myOptional ?? "I am the default value."
print(text)
//Output --> I am the default value.
```

5. Optional Chaining = ```optional?.property``` ```optional?.method()```
   1. For instances when you want an optional ```struct``` or an optional ```class```, you must use optional chaining to check to see if the ```struct``` or ```class``` is nil prior to gaining access to the their properties or methods.
      1. for example:

```swift
struct MyOptional {
  var property = 123
  func method() {
    print("I am the struct's method")
  }
}

// sets the variable to the struct
let myOptional: MyOptional?

// initializes the struct
myOptional = MyOptional()

// checks to see if the struct is nil, 
// if not, then allows access to the struct's properties and methods. 
print(myOptional?.property) //--> Optional(123)
myOptional?.method() //--> I am the struct's method
```

## Swift Deep Dive #12 Protocols

- Protocols are like certifications that have a bunch of requirements.  When methods, functs, structs, or classes meet the requirements, then they are allowed to use the protocols within their code.

To learn more, check out Swift's documentation on protocols [here](https://docs.swift.org/swift-book/LanguageGuide/Protocols.html)

```swift
//Defining the protocol
protocol MyProtocol {
  // Define requirements
}

//Adopting a protocol
struct MyStruct: MyProtocol{}
class MyStruct: MyProtocol{}

//Adopting Multiple Protocols
struct MyStruct: FirstProtocol, AnotherProtocol {
  // struct definition goes here
}

//With classes you must put the SuperClass first...
class MyClass: SuperClass, FirstProtocol, AnotherProtocol {
  // class definition goes here
}

// An example of a protocol

//initializes the protocol and anything inside the protocol wil be the requirements
protocol CanFly {
  func fly()
}

// This struct will be the museum of all things that fly using the CanFly protocol
struct FlyingMuseum {
  func flyingDemo(flyingObject: CanFly) {
    flyingObject.fly()
  }
}

class Bird {
  var isFemale = true

  func layEgg() {
    if isFemale {
      print("The bird makes a new bird in a shell.")
    }
  }
}

class Eagle: Bird, CanFly {
  func fly() {
    print("The eagle flaps its wings and lifts off into the sky.")
  }

  func soar() {
    print("The eagle glides in the air using air currents.")
  }
}

class Penguin: Bird {
  func swim() {
    print("The penguin paddles through the water.")
  }
}

struct Airplane: CanFly {
  func fly() {
    print("The airplane uses it engines to lift off into the sky.")
  }
}

let museum = FlyingMuseum()
let myEagle = Eagle()
let myPenguin = Penguin()
let myAirplane = Airplane()

museum.flyingDemo(flyingObject: myEagle)//-> prints the fly statement
museum.flyingDemo(flyingObject: myAirplane)//-> prints the fly statement
museum.flyingDemo(flyingObject: myPenguin)//-> throws an error b/c Penguin class doesn't have the fly func.
```

## Swift Deep Dive #13 Closures

- Closures are essentially anonymous functions or functions without names.  Closures are a self-contained package of functionality that we can pass around and use.

```swift
//closure syntax
{ (parameter: parameterType) -> returnType in return output }

//normal func with input and output
func functionName(parameter: parameterType) -> returnType {
  // Do something
  return output
}

//How to pass a function as a parameter in swift
                                // This parameter is a function
func calculator (n1: Int, n2: Int, operation: (Int, Int) -> Int) -> Int {
    return operation(n1, n2)
}

func add(no1: Int, no2: Int) -> Int {
    return no1 + no2
}

func subtract(no1: Int, no2: Int) -> Int {
    return no1 - no2
}

calculator(n1: 3, n2: 2, operation: add) //--> 5
calculator(n1: 3, n2: 2, operation: subtract) //--> 1

//Here is how we can use Closures to simplify the add code
{ (no1: Int, no2: Int) -> Int in
    return no1 + no2
}
//However we can simplify more:
// We don't need the -> because Swift knows we are using two numbers, so it already knows to return something
{ (no1: Int, no2: Int) in return no1 + no2 }

//Simplified more:
//We also don't need the return
{ (no1: Int, no2: Int) in no1 + no2 }

//Simplified more:
//We also don't have to use no1 or no2 by using anonymous parameter names.
//Anonymous parameters are labeled as $0, $1, $2, and so on.
{ (no1: Int, no2: Int) in $0 + $1 }

//now to call it
let result = calculator(n1: 20, n2: 5, operation: { $0 + $1 })
print(result)

//However since swift has a rule that if a closure is the last parameter,
//then they can omit the name parameter and become a trailing closure
let result = calculator(n1: 20, n2: 5 ) { $0 + $1 }
print(result)

//A more real-world example:
let array = [6,2,3,9,4,1]

//func before turning into closure
//func addOne(n1: Int) -> Int {
//    return n1 + 1
//}

//maps through (for loops) each index of the array and adds one
//using a closure
print(array.map{$0 + 1})

let newArray = array.map{"\($0)"}
print(newArray)
```

- *NOTE* one advantage is the code become much more simplified.  However, there is the issue of readability, and there is a delicate balance of the two. 

If you want to learn more about closures check out Swift's documentation [here](https://docs.swift.org/swift-book/LanguageGuide/Closures.html)

## Swift Deep Dive #14 Parameter Names

- Swift uses parameter names as way to name functions and their describe their functionality.  However, you can have internal and external parameter names.  Like so:

```swift
//defining a function with internal and external parameters
func myFunc(name eman: dataType) {
  print(eman)
}

//calling the function with internal and external parameters
myFunc(name: dataValue)

//if you want to call the function without the external name, then you would:
func myFunc(_ eman: dataType) {
  print(eman)
}

myfunc(dataValue)
```

## Swift Deep Dive #15 Extensions

- Extensions allows the developer to extend the functionality of funcs, structs, classes, protocols etc.  Why do this?  So devs can add on to their apps.

```swift
// defining the extension
extension SomeType {
  //Add some extension
}

// here we will extend the round() functionality:
import UIKit

extension Double {
    func round(to places: Int) -> Double {
        let percisionNumber = pow(10, Double(places))
        var n = self
        n = n * percisionNumber
        n.round()
        n = n / percisionNumber
        return n
    }
}

var myDouble = 3.14159
myDouble.round(to: 2) //--> 3.14

// you can even extend UI elements.
import UIKit

extension UIButton {
    func makeCircular() {
        self.clipsToBounds = true
        self.layer.cornerRadius = self.frame.size.width / 2
    }
}

let button = UIButton(frame: CGRect(x: 0, y: 0, width: 50, height: 50))
button.backgroundColor = .red
button.makeCircular()

// extending protocols
extension SomeProtocol {
  //Define default behavior
}

protocol CanFly {
    func fly()
}

extension CanFly {
    func fly() {
        print("The object takes off into the air.")
    }
}

struct Airplane: CanFly {
  //you do not need to set the protocol b/c it was set as default.
}

let myAirplane = Airplane()
myAirplane.fly()

// extensions can also help with cleaning up code by adopting protocols
// and separating protocols into sections within your code. 
extension SomeType: SomeProtocol {
  // Add new functionality
}
```

## Swift Deep Dive #16

- Loops are an important construct in general programming.  They loop through datatypes while doing some action.  In swift, there are a few different type of loops.

1. For In Loops

```swift
//for in loops
let names = ["Taylor", "Carrie", "Em", "Scout"]

for name in names {
  print("Hello,\(name)!")
}
// Hello, Taylor!
// Hello, Carrie!
// Hello, Em!
// Hello, Scout!

for number in 1...5 {
  print(number)
}
//1
//2
//3
//4
//5

// Just print the word Hello 5 times?
for _ in 1...5 {
  print("Hello")
}

let fruits: Array = ["apple", "pear", "orange"]
//Set is like an array, but will not print in order like an array. Use set when you don't care about order and want efficentcy
let fruitz: Set = ["apple", "pear", "orange"]
let contacts = ["Adam": 1235678, "Clair": 8675309, "Josh": 4567890]
let word = "supercalifragilisticexpialidocious"
let halfOpenRange = 1..<5
let closedRange = 1...5

for fruit in fruits {
    print(fruit)
}
//apple
//pear
//orange

for fruit in fruitz {
    print(fruit)
}
//pear
//orange
//apple

for person in contacts {
    print(person.key)
    print(person.value)
}
//Adam
//1235678
//Josh
//4567890
//Clair
//8675309

for letter in word {
    print(letter)
}
//s
//u
//p
//e
//r
//c
//a
//l
//i
//f
//r
//a
//g
//i
//l
//i
//s
//t
//i
//c
//e
//x
//p
//i
//a
//l
//i
//d
//o
//c
//i
//o
//u
//s

for num in halfOpenRange {
    print(num)
}
//1
//2
//3
//4

for _ in closedRange {
    print("Loop is running")
}
//Loop is running
//Loop is running
//Loop is running
//Loop is running
//Loop is running

//using funcs in for in loops:
func putCoin() {
    print("Coin dropped.")
}

func move(direction: String, number: Int) {
    print("Move \(direction) \(number) square.")
}

for _ in 1...5 {
    putCoin()
    move(direction: "Right", number: 1)
}
```

2. While Loops - test the condition (true / false) a variable and will run until it his a false.
  - **Remember** while loops can get caught in an infinite loop. 

```swift
while somethingIsTrue {
  doSomething
}

var now = Date().timeIntervalSince1970
let oneSecondFromNow = now + 1

while now < oneSecondFromNow {
    now = Date().timeIntervalSince1970
    print("Waiting...")
}

//loops exercise: Fibonacci's number
func fibonacci(n: Int) {
    
    var numArray: [Int] = [0, ]
    
    var num1 = 0
    var num2 = 1
    
    
    for _ in 0..<n-1 {
        
        let num = num1 + num2
        num1 = num2
        num2 = num
        numArray.append(num1)
    }
    print(numArray)
    print(num2)
}

fibnacci(n: 5)


//more refined way 

func fibonacci(n: Int) {
  var fibArray: [Int] = []

  var n1 = 0
  var n2 = 1

  if n == 0 {
    print("Invalid")
  } if else n == 1 {
    fibArray.append(n1)
    print(fibArray)
  } if else n == 2 {
    fibArray.append(n1)
    fibArray.append(n2)
    print(fibArray)
  } else {
    fibArray = [n1, n2]
    for _ in 2..<n {
      let result = n1 + n2
      fibArray.append(result)
      n1 = n2
      n2 = result
    }
  }
  print(fibArray)
}

//for loop showing how to make text look like it is typing
titleLabel.text = ""
        var charIndex = 0.0
        let titleText = "⚡️FlashChat"
        for letter in titleText {
            print("---")
            print(0.1 * charIndex)
            print(letter)
            Timer.scheduledTimer(withTimeInterval: 0.1 * charIndex, repeats: false) { (timer) in
                self.titleLabel.text?.append(letter)
            }
            charIndex += 1
        }
```

-  To learn more check out the Swift book [here](https://docs.swift.org/swift-book/LanguageGuide/ControlFlow.html)

## Swift Deep Dive #17 Type Casting

- Type casting is when you cast a different data type from the one a variable was created in.  Such as:

```swift
let myDouble = 0.0
let myDoubleAsAnInt = Int(myDouble)
```

- However, there is more with type casting using the following keywords:

```swift
//Example
import Foundation

class Animal {
    var name: String
    
    init(n: String) {
        name = n
    }
}

class Human: Animal {
    func code() {
        print("Typing away...")
    }
}

class Fish: Animal {
    func breatheUnderWater() {
        print("Breathing under water.")
    }
}

let taylor = Human(n: "Taylor")
let carrie = Human(n: "Carrie")
let nemo = Fish(n: "Nemo")

let neighbors = [taylor, carrie, nemo]
```

1. is - allows us to check to see if that the keyword used is of the dataType (conditional).  Also called, **Type Checking!**

```swift
func findNemo(from animals: [Animal]) {
    for animal in animals {
        //checks which animal in the array IS a fish.
        if animal is Fish {
            print(animal.name)
        }
    }
}

findNemo(from: neighbors)
//--> Nemo
```

2. as! - Turns a SuperClass into a SubClass (pretty cool, right!?) Also called, **Forced Downcast!** Check it out:

```swift
func findNemo(from animals: [Animal]) {
    for animal in animals {
        if animal is Fish {
            print(animal.name)
            //B/C animal is of the dataType Animal (class) it cannot take on
            //the functionality of fish, even though Fish is a subclass.  
            //Instead we have to type cast animal to Fish using as! to gain
            //access to it's full functionality. 
            let fish = animal as! Fish
            fish.breatheUnderWater()
        }
    }
}

findNemo(from: neighbors)
//--> Nemo
//--> Breathing under water.
```

**NOTE** - Forced downcasting can be dangerous if you mix dataTypes and will make your app fail at runtime because of it.  A better way is to check the dataType using as?.

3. as? checks to see if dataTypes match and if not will crash the app at run time.  Usually seen with if let statements.  
  
```swift
if let fish = neighbors[1] as? Fish {
    fish.breatheUnderWater()
} else {
    print("Sorry, that is incorrect.")
}
```

4. as - raises an Object from a SubClass to a SuperClass.  Also called, **Up Casting**

```swift
func findNemo(from animals: [Animal]) {
    for animal in animals {
        if animal is Fish {
            print(animal.name)
            let fish = animal as! Fish
            fish.breatheUnderWater()
            let animalFish = fish as Animal
            print(animalFish.name)
        }
    }
}

findNemo(from: neighbors)
```

### Weird Type Casting Data Types

- Any - Can be **All Objects**

Example:
  
  ```swift
  let neighbors: [Any] = [taylor, carrie, nemo, 4]
  ```

  - AnyObjects - Objects derived from classes **not** structs
    - NSObjects - Foundation objects
      - NSString
      - NSNumber
      - NSData
      - NSDate
      - JSONSerialization
      - DataFormalizer
      - FileManager

- To check out more, read this from the Swift documentation [here](https://docs.swift.org/swift-book/LanguageGuide/TypeCasting.html)

## The 5 Step Approach to Solve Any Programming Problem

  1. Google
  2. Stack Overflow
  3. Implement
  4. Docs
  5. Customise

### The question: How to get our app to play sound?

  1. Start with Google.

- Google search structure:
  - [What I want my app to do] + [Which programming language] + [Which resource]
    - So use this to search: [Play sound] [Swift] [StackOverflow]

2. Exploring the Answer with StackOverflow

- Don't just take the first answers...look at the first three answers and take the best one out of those three.

3. Implement the StackOverflow answer into your code.

- Copy the code from StackOverflow into your code.

4. Read the Official Documentation to figure out why they code from StackOverflow works.

- Read and research the official documents.

5. Customize the StackOverflow code to fit with your app.

- This is the hardest part of writing code because I takes more knowledge of the actual language.

## The 5 Step Approach to Debug our App:

1. What did you expect to happen?
2. What happened instead?
3. What does your expectation depend on?
4. How can we test the things our expectations depend on?
5. Fix our code to match expectations.

## Working With APIs

- What is an API (Application Programming Interface)?
  - An API is a set of commands, functions, protocols, and objects that programmers can use to **create software** or **interact with an external system**.
  - It provides developers with **standard commands** for performing **common operations** so they do not have to write the code from scratch.
- Examples of APIs
  - APIs to Create Software
    - Apple Developer Classes such as AVAudioPlayer through the Apple documentation.
  - APIs to Interact with an External System
    - When you log into an app and it asks if you want to login with Facebook and then populates information from Facebook.
- APIs are kind of like contracts between your app and the API Provider.
  - For example: in our weather app, us and OpenWeather enter into an API contract; we promise to abide by the rules Open and use the methods and functionality appropriately, and OpenWeather promises to keep their protocols and delegates the same so it doesn't crash our app.

### API Networking

- Networking is when your app is talking to a web server with queries you've asked the webserver, the webserver then sends you data back in the form of JSON.
- Networking steps:
  - Step 1: Create the URL
  - Step 2: Create the URLSession
  - Step 3: Give URLSession a task
  - Step 4: Start the task

## UITableView

- One of the most used Views in iOS development and a must have for iOS devs.
- It is a view that is made up of a table and prototype cells that have data in each one of them.  iMessage or the Mail app uses these. 


## ViewController Lifecycle Explained

- Much like life on this planet, everything must die...(wow, dramatic much?), the ViewController also has a life cycle. Here is it's lifecycle explained.

1. The view get loaded up! (It's alive!) ```viewDidLoad()```
   1. All of the IBOutlets and actions are connected up and accessible.  
      1. **NOTE** ```viewDidLoad()``` will only be ran 1 when the view is loaded.
2. ```viewWillAppear()``` is loaded next
   1. This is where the developer can start to load objects for the user to see.
3. ```viewDidAppear()``` is loaded next
   1. This is where the code that was loaded in ```viewDidAppear()``` will become visible to the user and detect.
4. ```viewWillDisappear()``` is this wear you want to load objects you want hidden from the user like a task bar or whatnot.
5. ```viewDidDisappear()``` is where the objects you wanted to hid from the user are hidden.  Last moment where the dev can manipulate objects. Although objects are hidden, it doesn't mean the View is dead or decollated.

## Application Lifecycle Explained

1. App Launch
2. App Visible
3. App Recedes into Background
4. Resources Reclaimed...death

- This last part is very important to understand iOS development. Remember, resources (memory, cpu time, etc.) are limited within iOS, and the cpu is always trying to find ways to reclaim resources to make the best user experience for the user. 
- Now, the cpu allocates a majority of the resources to the app that is running on the foreground because that is what the user is interacting with at the time.  
- So, if your app (maybe a game or has a long survey) gets push to the back, and it hasn't save the users data then that data will be reclaimed and lost.
- When's the best time to save your user's data? Well, when you app leaves the forground-active state is the best time to do so.

## User Defaults

- User defaults are a way to store data that is unique to the user such as a name, music on or off, or even arrays and dictionaries. Here are some examples:

```swift
import UIKit

// initializes defaults as the variable for User options.
let defaults = UserDefaults.standard

// A good idea is to create a constant for each of your default keys
let dictionaryKey = "MyDictionary"
// here are some examples of user defaults

// sets the user volue to a float when opening the application
defaults.set(0.24, forKey: "Volume")

// sets the volue to begin when the user opens the application
defaults.set(true, forKey: "MusicOn")

// set player's name
defaults.set("Taylor", forKey: "PlayerName")

// gather data on the user
defaults.set(Date(), forKey: "AppLastOpenedByUser")

// saving collection with defaults

// arrays
let array = [1,2,3]
defaults.set(array, forKey: "MyArray")

// dictionaries
let dictionary = ["name": "Taylor"]
defaults.set(dictionary, forKey: dictionaryKey)
    


let volume = defaults.float(forKey: "Volume")
let music = defaults.bool(forKey: "MusicOn")
let name = defaults.string(forKey: "PlayerName")
let lastDateOpened = defaults.object(forKey: "AppLastOpenedByUser")
let myArray = defaults.array(forKey: "MyArray") as! [Int]
let myDict = defaults.dictionary(forKey: dictionaryKey)
```

- 2 things to remember:
  - a: User defaults should only be used for storing tiny pieces of data such as flipping the music on or off.  They should **NOT** be used for full fledge database because all of the user defaults must be ran and stored in a pList file which if there was a large array or dictionary the app would take a performance hit to retrieve the data.
  - b: User Defaults are special creatures that can be used as a make shift database for user options.  For this reason they are called Singleton objects.  Learn more 👇.

## Singleton Objects

- Is an object that will only be copied once and shared across all of objects of your app.  Examples are:

```swift
let defaults = UserDefaults.standard
let sharedURLSession = URLSession.shared
```

- Here is an example of a class acting normal:

```swift
import UIKit

class Car {
    
    var color = "Red"
    
}

let myCar = Car()
myCar.color = "Blue"

let yourCar = Car()

print(myCar.color) //--> Blue
print(yourCar.color) //--> Red
```

- Here is an example of Singletons in a class:

```swift
import UIKit

class Car {
    
    var color = "Red"
    
    static let singletonCar = Car()
}

let myCar = Car.singletonCar
myCar.color = "Blue"

let yourCar = Car.singletonCar

print(myCar.color) //--> Blue
print(yourCar.color) //--> Blue

class A {
    init() {
        Car.singletonCar.color = "Brown"
    }
}

class B {
    init() {
        print(Car.singletonCar.color)
    }
}

let a = A()
let b = B() //--> Brown
```

## Swift Ternary Operator

- Ternary operator is an operator that checks if a value is true or false:  essentially a conditional statement in an operator. Example syntax:

```value = condition ? valueIfTrue : valueIfFalse```

```swift
cell.acessoryType = items.done ? .checkmark : .none
```

## Sandboxing

- All of your apps live in a sandbox (or prison) on your phone.
- Each sandbox can hold folders that are associated with the apps.
- Which means that the folders on one app do not mess with the folders on another app...think weather app getting data from your BOA app (ouch!).
- Now, when your phone connects to iCloud or iTunes (locally on your laptop), it syncs to the documents folder which is a backup to your app's data safely.  This is important because you don't loose the data from your apps when you get a new phone or update the OS.

## DataBases

- Different types of data bases, tables(UserDefaults, Codable, KeyChain) and DatabaseSolutions(SQLite, Core Data, Realm).

| Method | Use |
|:--:|:--:|
| UserDefaults | Quickly persist small bits of data e.g. top score, playerNickname, music on/off |
| Codable | Flash freeze custom objects |
| Keychain API | Save small bits of data securely |
| SQLite | Persist large amounts of daa and query it |
| Core Data | Object-oriented database |
| Realm | A faster and easier database solution |

- Checkout DataBase notes.