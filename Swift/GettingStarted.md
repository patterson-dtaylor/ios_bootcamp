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
