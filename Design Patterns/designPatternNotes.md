#  MVC Design Patterns

## What is a design pattern

- A design pattern is a proven solution to a common problem.
  - With software, the common problem is usually complexity (usually code within one file).
- There are many different design patterns (VIPER MVVC):
  - And each one of these design patterns provides a architectural blueprint for the specific requirements of the app.
  - Plus there is a style based sources.  
- Examples of pattern and style: "few lines as possible" / "the most readable code in the land"

## MVC (Model View Controller)

- MVC is the most fundamental design patter that you should knwow about and the one Apple uses.
- So, how does it work?
  - You split the project into three main components and they interact with each other in a specific way:

- MVC is split by:
  - Model - data & logic
  - View - User Interface && User Interactions
  - Controller - Mediator or Conductor



Here is how MVC interacts within itself:

1. The _UI_ on the **View** sends input events to the **controller**.
2. The **controller** then makes a request to the **model** for some _data_.
3. The **model** sends the _data_ to the **controller** where it _modifies_ the data 
4. The **controller** sends the _modified_ data to the **view** so that the _UI_ can be updated.  

**NOTE** The **view** and the **model** never interact with each other exclusively, rather they **both** go through the **controller** to make requests.

The reason this design pattern is so good is because if your app gets to where you have many different versions, you would only need to modify the **model** rather than the **view** or **controller**. 

**MVC is really good at reusing code to build on to apps**

## The Delegate Design Pattern

- The problem: whenever Apple develops huge objects like UITextField, the object doesn't know when I develop an app and want to use it functionality with my own methods.  So, Apple is not going to build methods for each of my methods so I can talk with UITextField.  
- Solution: **The Delegate Pattern**
  - The underlining power behind The Delegate Pattern is the **protocol**.

```swift
//All this is under the hood. 
class UITextField {
  var delegate: UITextFieldDelegate
  delegate.textFieldDidBeginEditing()
}

//without this, UITextField and WeatherViewController cannot talk to each other.
protocol UITextFieldDelegate {
  func textFieldDidBeginEditing()
}

class WeatherViewController: UITextField {
  let textField = UITextField() //references UITextField
  textField.delegate = self //the delegate is adopted
  func textFieldDidBeginEditing() { //func is a part of the requirement
    //do something.
  }
}

//Emergency Call Handler Analogy
// this protocol is the must have! to be able to hold the bleep
protocol AdvancedLifeSupport {
    func performCPR()
}

class EmergencyCallHandler {
    // whoever is a delegate must have the AdvancedLifeSupport protocol.
    var delegate: AdvancedLifeSupport?
    
    func assessSituation() {
        print("Can you discribe your emergency?")
    }
    
    func medicalEmergency() {
        //Doesn't care who is working, just so they hold the delegate
        delegate?.performCPR()
    }
}

struct Paramedic: AdvancedLifeSupport {
    // this sets up the connection witht he ECH
    init(handler: EmergencyCallHandler) {
        handler.delegate = self
    }
    
    func performCPR() {
        print("The paramedic does chest compression, 30 per second.")
    }
}

class Doctor: AdvancedLifeSupport {
    
    init(handler: EmergencyCallHandler) {
        handler.delegate = self
    }
    
    func performCPR() {
        print("The doctor does chest compressions, 30 per second.")
    }
    
    func useStehtescope() {
        print("Listening for heart sounds.")
    }
}

class Surgeon: Doctor {
    override func performCPR() {
        super.performCPR()
        print("Sing 'Staying Alive' by the BeeGees.")
    }
    
    func useEletricDrill() {
        print("Whirr....")
    }
}

let emilo = EmergencyCallHandler()
let angela = Surgeon(handler: emilo)

emilo.assessSituation()
emilo.medicalEmergency()

```
