# Getting Started With Swift

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

## Structures, Methods, and Properties

- **Remember** prebuilt - basic data types are "Strings", Int, Float, Double, Bool, Array, Dictionary

### But what if we needed a custom data type?

- Structures == Blueprints for objects in Swift where we can plan ahead of what it will be.  
  - Structures are composed of properties and methods:
    - **Properties** are variables created within the structure (What the structure will be like)
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

