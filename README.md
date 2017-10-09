# Classes & Structs Quiz

![](http://i.imgur.com/zWBjkea.jpg)  

> Success is not final, failure is not fatal: it is the courage to continue that counts. -[Winston Churchill](https://en.wikipedia.org/wiki/Winston_Churchill)

## Overview

This quiz will give you practice working with both classes and structs. 

## Quiz Time!

In the last few lessons, you've learned a lot about classes and structs in Swift. Now, challenge yourself with a brief quiz to test everything you've learned.

### Question 1

Given this class that represents a giant:

```swift
class Giant {
    var name: String
    var weight: Double
    let homePlanet: String

    init(name: String, weight: Double, homePlanet: String) {
        self.name = name
        self.weight = weight
        self.homePlanet = homePlanet
    }
}
```

And this code that instantiates an instance of `Giant`:

```swift
let fred = Giant(name: "Fred", weight: 340.0, homePlanet: "Earth")
```

Will these three lines of code run? If not, why not?

```swift
fred.name = "Brick"
fred.weight = 999.2
fred.homePlanet = "Mars"
```

The first two lines will work, because 'fred' is a reference variable, meaning that its contents can be mutated.
The variable homePlanet, however, is declard as a constant inside the Giant class, therefore, it can not be mutated.

### Question 2

Can you fix the class definition above so that it _does_ work?
You would just have to change homePlanet to a variable.

### Question 3

Take a look at this struct that represents an alien:

```swift
struct Alien {
    var name: String
    var height: Double
    var homePlanet: String
}
```

And this line of code that instantiates an `Alien`:

```swift
let bilbo = Alien(name: "Bilbo", height: 1.67, homePlanet: "Venus")
```

Will these three lines of code run? If so, why not?

```swift
bilbo.name = "Jake"
bilbo.height = 1.42
bilbo.homePlanet = "Saturn"
```

No, because Alien is a stuct, which is value based, which means that alterations to the contents of an instance of the Alien
struct are alterations to the struct itself. The Alien, 'bilbo' is delcared as a constant, therefore neither it nor its contents may be
edited.


### Question 4

Can you change the declaration of `bilbo` so that the above three lines of code _do_ work?

Yes, change it to a variable.

### Question 5

Consider this bit of code that uses the `Giant` class:

```swift
let edgar = Giant(name: "Edgar", weight: 520.0, homePlanet: "Earth")
let jason = edgar
jason.name = "Jason"
```

What will the value of `edgar.name` be after those three lines of code are run? What will the value of `jason.name` be? Why?

It will be 'Jason', becuase the variable jason is a reference variable set equal to edgar. So the contents of edgar and jason are
exactly the same, an address in memory for our created Giant. As a result, any alteration to edgar or jason is actually an
alteration on the same instance of Giant.

### Question 6

Given this bit of code that uses the `Alien` struct:

```swift
var charles = Alien(name: "Charles", height: 2.25, homePlanet: "Pluto")
var charlesFromJupiter = charles
charlesFromJupiter.homePlanet = "Jupiter"
```

What will the value of `charles.homePlanet` be after the above code run? What about the value of `charlesFromJupiter.homePlanet`? Why?

The value of 'charles.homPlanet' will be 'Pluto', whereas 'charlesFromJupiter' will have a home planet of 'Jupiter'. This is
because structs are value based, so when the variable 'charlesFrom Jupiter' is initialized with 'charles', a new structure is created with values identitical to 'charles'. As a result, any edits made to the new structure don't effect the original structure that was copied.

### Question 7

Here's a struct that represents a bank account:

```swift
struct BankAccount {
    var owner: String
    var balance: Double

    func deposit(_ amount: Double) {
        balance += amount
    }

    func withdraw(_ amount: Double) {
        balance -= amount
    }
}
```

Does this code work? Why or why not?

No, because balance was never initialized.

### Question 8

Can you fix the `BankAccount` struct so it _does_ work?
This could be remedied by adding an initializer that would set base values for owner and balance.

### Question 9

Given this bit of code (which incorporates any fixes you made in Question 8):

```swift
var joeAccount = BankAccount(owner: "Joe", balance: 100.0)
var joeOtherAccount = joeAccount
joeAccount.withdraw(50.0)
```

What will the value of `joeAccount.balance` be after the above code runs? What about the value of `joeOtherAccount.balance`? Why?

'JoeAccount' will have a balance of 50, while 'joeOtherAccount' will have a balance of 100. This is because the bank accounts are structures, so any changes to one account do not effect the other.

### Question 10

Here's a class that can track songs in a music library:

```swift
class MusicLibrary {
    var tracks: [String]

    init() {
        tracks = []
    }

    func add(track: String) {
        tracks.append(track)
    }
}
```

Given this bit of code that uses `MusicLibrary`:

```swift
let library1 = MusicLibrary()
library1.add(track: "Michelle")
library1.add(track: "Voodoo Child")
let library2 = library1
library2.add(track: "Come As You Are")
```

After this code runs, what are the contents of `library1.tracks`? What about the contents of `library2.tracks`? Why?

The contents will be the same. This is becuase classes are referential types, so when 'library2' is created, it is passed the same address as library1, so any changes made with either label actually effect the same instance of 'MusicLibrary' in memory.

<a href='https://learn.co/lessons/ClassesVsStructs' data-visibility='hidden'>View this lesson on Learn.co</a>
