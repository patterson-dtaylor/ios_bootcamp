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


