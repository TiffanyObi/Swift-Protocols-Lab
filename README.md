
## Protocols Lab

## Instructions for lab submission

1. Fork the assignment repo
1. Clone your Fork to your machine
1. Complete the lab
1. Push your changes to your Fork
1. Submit a Pull Request back to the assignment repo
1. Paste a link of the pull request on Canvas and submit


<br>

> Questions adapted from [Swift student lessons: 4 - Tables and Persistence -> 1 - Protocols](https://developer.apple.com/go/?id=app-dev-swift-student)

## Question 1

a. Create a `Human` class with two properties:
- `name` of type String
- `age` of type Int.

Then create an initializer for the class and create two `Human` instances.

b. Make the `Human` class adopt the CustomStringConvertible protocol. Then print both of your previously initialized
`Human` objects.

c. Make the `Human` class adopt the Equatable protocol. Two instances of `Human` should be considered equal
if their names and ages are identical to one another. Print the result of a boolean expression
evaluating whether or not your two previously initialized `Human` objects are equal to eachother
(using ==). Then print the result of a boolean expression evaluating whether or not your two
previously initialized `Human` objects are not equal to eachother (using !=).

d. Make the `Human` class adopt the `Comparable` protocol. One `Human` is greater than another `Human` if its age is bigger. Create another
three instances of a `Human`, then create an array called people of type [`Human`] with all of the
`Human` objects that you have initialized.

Create a new array called sortedPeople of type [`Human`] that is the people array sorted by age.

</br> </br>

ANSWER:

class Human: CustomStringConvertible,Equatable,Comparable{
    static func < (lhs: Human, rhs: Human) -> Bool {
        lhs.age < rhs.age
    }
    static func == (lhs: Human, rhs: Human) -> Bool {
                return lhs.name == rhs.name && lhs.age == rhs.age
    }
    var description: String
    var name: String
    var age: Int
    
init(name: String,
        age: Int) {
        self.age = age
        self.name = name
        self.description = "\(name) is \(age) years old and is helping us while we're, Finding Humans!"
    }
}

var notAnAlien = Human(name: "HumanBeing", age: 35)

var notAnAnimal = Human(name: "HomoSapien", age: 1500)

print(notAnAnimal.description)
print(notAnAlien.description)


if notAnAnimal == notAnAlien {
    print("They're the same")
} else {
    print("They're different")
}

if notAnAnimal < notAnAlien {
    print("\(notAnAnimal.name) is younger")
} else {
    print("\(notAnAlien.name) is younger")
}

var humanThree = Human(name: "HummanThree", age: 487)
var humanFour = Human(name: "HumanFour", age: 5)
var humanFive = Human(name: "HumanFive", age: 23454)

var people :[Human] = [notAnAnimal,notAnAlien,humanThree,humanFour,humanFive]
var sortedPeople = people.sorted()
print(sortedPeople)


## Question 2

a. Create a protocol called `Vehicle` with two requirements:
- a nonsettable `numberOfWheels` property of type Int,
- a function called drive().

b. Define a `Car` struct that implements the `Vehicle` protocol. `numberOfWheels` should return a value of 4,
and drive() should print "Vroom, vroom!" Create an instance of `Car`, print its number of wheels,
then call drive().

c. Define a Bike struct that implements the `Vehicle` protocol. `numberOfWheels` should return a value of 2,
and drive() should print "Begin pedaling!". Create an instance of Bike, print its number of wheels,
then call drive().


</br> </br>

Answer: 

protocol Vehicle {
    var numberOfWheels:Int {get}
    func drive()
}

struct Car: Vehicle {
    var numberOfWheels: Int {
        return 4
    }
    func drive() {
        print("Vroom,Vroom!")
    }
    
}

var newToy = Car()
print(newToy.numberOfWheels)
newToy.drive()

struct Bike: Vehicle {
    var numberOfWheels: Int {
        return 2
    }
    
func drive() {
        print("Begin Pedaling")
    }
    
}

var coolWhip = Bike()
print(coolWhip.numberOfWheels)
coolWhip.drive()


## Question 3
// Given the below two protocols, create a struct for penguin(a flightless bird) and an eagle.

Give your structs some properties and have them conform to the appropriate protocols.

```swift
protocol Bird {
 var name: String { get }
 var canFly: Bool { get }
}

protocol Flyable {
 var airspeedVelocity: Double { get }
}
```
Answer:

protocol Bird {
 var name: String { get }
 var canFly: Bool { get }
}

protocol Flyable {
 var airspeedVelocity: Double { get }
}

struct Penguin: Bird {
    var name: String {
        return "Penny Penguin"
    }
    var color: String = "Black and White"
    var canFly: Bool {
        return false
    }
    
}
var penguin = Penguin()
print("\(penguin.name) is a \(penguin.color) bird that can fly right? \(penguin.canFly)")

struct Eagle: Bird, Flyable {
    var name: String {
        return "Emit the Eagle"
    }
        var canFly: Bool {
        return true
    }
    
var airspeedVelocity: Double {
        return 150.0
    }
    
var color: String = "Golden Brown"
    
}
var eagle = Eagle()

print("\(eagle.name) is a \(eagle.color) bird that cannot fly right? \(penguin.canFly)! In fact, it's speed reaches \(eagle.airspeedVelocity) mph! ")

</br> </br>

## Question 4

a. Create a protocol called `Transformation`.  The protocol should specify a mutating method called transform

b. Make an enum called `SuperHero` that conforms to `Transformation` with cases `notHulk` and `hulk`

c. Create an instance of it named `bruceBanner`. Make it so that when the transform function is called that bruceBanner turns from
`.notHulk` to `.hulk.``

```swift
enum SuperHero: Transformation {
    // write code here.
}

// Example Output:
var bruceBanner = SuperHero.notHulk

bruceBanner.transform() . // hulk

bruceBanner.transform()  // notHulk
```
Answer: 
protocol Transformation {

mutating func transform()
    
}

enum SuperHero: Transformation {
    
case notHulk
    
case hulk
    
    
func transform() {
        if bruceBanner == .hulk {
            bruceBanner = .notHulk
        } else if bruceBanner == .notHulk {
            bruceBanner = .hulk
        }
        
}
    
    
}
    var bruceBanner = SuperHero.notHulk

bruceBanner.transform()  //hulk
bruceBanner.transform() //notHulk
bruceBanner.transform()  //hulk
bruceBanner.transform() //notHulk
</br> </br>


## Question 5

a. Create a protocol called `Communication`

b. Give it a property called `message`, of type String, and assign it an explicit getter.

c. Create three Classes. `Cow`, `Dog`, `Cat`.

d. Have your three classes conform to `Communication`

e. `message` should return a unique message for each animal when talk is called.

f. Put an instance of each of your classes in an array.

g. Iterate over the array and have them print their `message` property


Answer:

protocol Communication {
    var message: String { get }
    
func talk()
}


class Cow: Communication {
    
var message: String
    
init ( message: String ) {
        self.message = message }
    
func talk() {
        print(message)
    }
}



class Dog: Communication {
    var message: String
    
init ( message: String ) {
          self.message = message }
    
func talk() {
        print(message)
    }
}



class Cat: Communication {
    var message: String
    
init ( message: String ) {
          self.message = message }
    
func talk() {
        print(message)
    }
}

 var cow = Cow(message: "Mooo!")
 var dog = Dog(message: "Woof!")
 var cat = Cat(message: "Meow!")

//cow.talk()
//dog.talk()
//cat.talk()

var arrayOfAnimals = ["\(cow)","\(dog)","\(cat)"]

for animal in arrayOfAnimals {
    if animal == "\(cow)" {
        print(cow.message)
    } else if animal == "\(dog)" {
        print(dog.message)
    } else if animal == "\(cat)" {
        print(cat.message)
    }
}

note: im not sure if this is what you meant, but i kept getting a compile error when i didnt string interpolate the instance of the classes, so i tried it this way. hopefull this isnt hard-coding. 

## Question 6

The HeartRateReceiver class below represents a very simplified example of a class dedicated to receiving information from fitness tracking hardware with monitoring heart rate. The function startHeartRateMonitoringExample will generate random heart rates and assign them to currentHR, simulating how an instance of HeartRateReceiver may pick up on new heart rate readings at specific intervals.

HeartRateViewController below is a view controller that will present the heart rate information to the user. Throughout the exercises below you'll use the delegate pattern to pass information from an instance of HeartRateReceiver to the view controller so that anytime new information is obtained it is presented to the user. 

```swift
class HeartRateReceiver {
    var currentHR: Int? {
        didSet {
            if let currentHR = currentHR {
                print("The most recent heart rate reading is \(currentHR).")
            } else {
                print("Looks like we can't pick up a heart rate.")
            }
        }
    }

    func startHeartRateMonitoringExample() {
        for _ in 1...10 {
            let randomHR = 60 + Int.random(in: 0...15)
            currentHR = randomHR
            Thread.sleep(forTimeInterval: 2)
        }
    }
}

class HeartRateViewController: UIViewController {
    var heartRateLabel: UILabel = UILabel()
}
```

First, create an instance of HeartRateReceiver and call startHeartRateMonitoringExample. Notice that every two seconds currentHR get set and prints the new heart rate reading to the console.

In a real app, printing to the console does not show information to the user. You need a way of passing information from the HeartRateReceiver to the HeartRateViewController. To do this, create a protocol called HeartRateReceiverDelegate that requires a method heartRateUpdated(to bpm:) where bpm is of type Int and represents the new rate as beats per minute. Since playgrounds read from top to bottom and the two previously declared classes will need to use this protocol, you'll need to declare this protocol above the declaration of HeartRateReceiver.

Now make HeartRateViewController adopt the protocol you've just created. Inside the body of the required method you should set the text of heartRateLabel and print "The user has been shown a heart rate of <INSERT HEART RATE HERE>."

Now add a property called delegate to HeartRateReceiver that is of type HeartRateReceiverDelegate?. In the didSet of currentHR where currentHR is successfully unwrapped, call heartRateUpdated(to bpm:) on the delegate property.

Finally, return to the line of code just after you initialized an instance of HeartRateReceiver. Initialize an instance of HeartRateViewController. Then, set the delegate property of your instance of HeartRateReceiver to be the instance of HeartRateViewController that you just created. Wait for your code to compile and observe what is printed to the console. Every time that currentHR gets set, you should see both a printout of the most recent heart rate, and the print statement stating that the heart rate was shown to the user.
