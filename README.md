# Unit 1 Review Lab

Before completing any of the review questions below, ensure that you have answered each question in the previous labs.

## Question 1

Given the following excerpt from the Declaration of Independence, find the most frequent word that is longer than 5 characters.

 - use components(separatedBy:) to break up the string into an array.
 - use CharacterSet.punctuationCharacters in union with any other characters you don't want in your array, like spaces and new lines.

```swift
let declarationOfIndependence =

"""
When in the Course of human events, it becomes necessary for one people to dissolve the
political bands which have connected them with another, and to assume among the powers of the
earth, the separate and equal station to which the Laws of Nature and of Nature's God entitle
them, a decent respect to the opinions of mankind requires that they should declare the causes
which impel them to the separation.
We hold these truths to be self-evident, that all men are created equal, that they are endowed by
their Creator with certain unalienable Rights, that among these are Life, Liberty and the pursuit
of Happiness. That to secure these rights, Governments are instituted among Men, deriving
their just powers from the consent of the governed, That whenever any Form of Government
becomes destructive of these ends, it is the Right of the People to alter or to abolish it, and to
institute new Government, laying its foundation on such principles and organizing its powers in
such form, as to them shall seem most likely to effect their Safety and Happiness. Prudence,
indeed, will dictate that Governments long established should not be changed for light and
transient causes; and accordingly all experience hath shewn, that mankind are more disposed to
suffer, while evils are sufferable, than to right themselves by abolishing the forms to which they
are accustomed. But when a long train of abuses and usurpations, pursuing invariably the same
Object evinces a design to reduce them under absolute Despotism, it is their right, it is their duty,
to throw off such Government, and to provide new Guards for their future security. Such has
been the patient sufferance of these Colonies; and such is now the necessity which constrains
them to alter their former Systems of Government. The history of the present King of Great
Britain is a history of repeated injuries and usurpations, all having in direct object the
establishment of an absolute Tyranny over these States. To prove this, let Facts be submitted to a
candid world.
"""
```

```swift
var newArray = [String]()
var array = declarationOfIndependence.components(separatedBy: .punctuationCharacters).joined().components(separatedBy: "\n")
//print(array)
for a in array {
for b in a.components(separatedBy: " ") {
newArray.append(b)
}
}
//print(newArray)
//1. gets rid of punctuation marks
//2 gets rid of the new line character \n
//3 gets rid of spaces

var dictFrequency: [String:Int] = [:]
for a in newArray {
var count = 0
for b in newArray {
if a == b {
count += 1
}
}
dictFrequency[a] = count
}
//print(dictFrequency)
var highestWord = String()
var highestCount = Int()
for (a,b) in dictFrequency where a.count > 5 {
if b > highestCount {
highestWord = a
highestCount = b
}
}
print(highestWord)

```

## Question 2

Make an array that contains all elements that appear more than twice in someRepeatsAgain.


```swift
var someRepeatsAgain = [25,11,30,31,50,28,4,37,13,20,24,38,28,14,44,33,7,43,39,35,36,42,1,40,7,14,23,46,21,39,11,42,12,38,41,48,20,23,29,24,50,41,38,23,11,30,50,13,13,16,10,8,3,43,10,20,28,39,24,36,21,13,40,25,37,39,31,4,46,20,38,2,7,11,11,41,45,9,49,31,38,23,41,16,49,29,14,6,6,11,5,39,13,17,43,1,1,15,25]
```
```swift
var answerQ2 = [Int]()
for a in someRepeatsAgain {
var count = Int()
for b in someRepeatsAgain {
if b == a {
count += 1
}
}
if count > 2 && !answerQ2.contains(a) {
answerQ2.append(a)
}
}
print(answerQ2)
```

## Question 3

Identify if there are 3 integers in the following array that sum to 10. If so, print them. If there are multiple triplets, print all possible triplets.

```swift
var tripleSumArr = [-20,-14, -8,-5,-3,-2,1,2,3,4,9,15,20,30]
```

```swift

for a in tripleSumArr {
for b in tripleSumArr {
for c in tripleSumArr {
if a + b + c == 10 {
print(a, b, c)
}
}
}
}
```


## Question 3

```swift
let letterValues = [
"a" : 54,
"b" : 24,
"c" : 42,
"d" : 31,
"e" : 35,
"f" : 14,
"g" : 15,
"h" : 311,
"i" : 312,
"j" : 32,
"k" : 93,
"l" : 203,
"m" : 212,
"n" : 41,
"o" : 102,
"p" : 999,
"q" : 1044,
"r" : 404,
"s" : 649,
"t" : 414,
"u" : 121,
"v" : 838,
"w" : 555,
"x" : 1001,
"y" : 123,
"z" : 432
]
```

a. Sort the string below in descending order according the dictionary letterValues
var codeString = "aldfjaekwjnfaekjnf"
```swift
var codeString = "aldfjaekwjnfaekjnf"
var newCode = Array(codeString)
newCode = newCode.sorted(by: {(a:Character,b:Character) -> Bool in
var boo = Bool()
if let unwrapA = letterValues["\(a)"], let unwrapB = letterValues["\(b)"] {
boo = unwrapA > unwrapB
}
return boo
})
var codeOne = String(newCode)
print(codeOne)
```

b. Sort the string below in ascending order according the dictionary letterValues
var codeStringTwo = "znwemnrfewpiqn"

```swift
var codeStringTwo = "znwemnrfewpiqn"
newCode = Array(codeStringTwo)
newCode = newCode.sorted(by: {(a:Character,b:Character) -> Bool in
var boo = Bool()
if let unwrapA = letterValues["\(a)"], let unwrapB = letterValues["\(b)"] {
boo = unwrapA < unwrapB
}
return boo
})
var codeTwo = String(newCode)
print(codeTwo)
```

## Question 4

Given an Array of Arrays of Ints, write a function that returns the Array of Ints with the largest sum:


```swift
Input: [[2,4,1],[3,0],[9,3]]

Output: [9,3]
```

```swift
var input = [[2,4,1],[3,0],[9,3]]
func largestSum(arrOfArr: [[Int]]) -> [Int] {
var sumOverAll = Int()
var currentArr = [Int]()
for a in arrOfArr {
let sum = a.reduce(0, +)
if sum > sumOverAll {
sumOverAll = sum
currentArr = a
}
}
return currentArr
}
print(largestSum(arrOfArr: input))
```

## Question 5

```swift
struct Receipt {
  let storeName: String
  let items: [ReceiptItem]
}

struct ReceiptItem {
  let name: String
  let price: Double
}
```

a. Given the structs above, add a method to `Receipt` that returns the total cost of all items

b. Write a function that takes in an array of `Receipts` and returns an array of `Receipts` that match a given store name

c. Write a function that takes in an array of `Receipts` and returns an array of those receipts sorted by price

```swift
struct Receipt {
let storeName: String
let items: [ReceiptItem]
//a
func totalCostOfItems() -> Double {
var total = Double()
for a in self.items {
total += a.price
}
return total
}
//b
func sameStore(arr: [Receipt], storeName: String) -> [Receipt] {
let answerArr = arr.filter({(a:Receipt) -> Bool in
return a.storeName == storeName
})
return answerArr
}
//c
func sortedByPrice(arr: [Receipt]) -> [Receipt] {
let sorting = arr.sorted(by: {(a:Receipt,b:Receipt) -> Bool in
return a.totalCostOfItems() < b.totalCostOfItems()
})
return sorting
}
}

struct ReceiptItem {
let name: String
let price: Double
}
```

## Question 6

a. The code below doesn't compile.  Why?  Fix it so that it does compile.

```swift
class Giant {
    var name: String
    var weight: Double
    var homePlanet: String

    init(name: String, weight: Double, homePlanet: String) {
        self.name = name
        self.weight = weight
        self.homePlanet = homePlanet
    }
}

let fred = Giant(name: "Fred", weight: 340.0, homePlanet: "Earth")

fred.name = "Brick"
fred.weight = 999.2
fred.homePlanet = "Mars"
```

b. Using the Giant class. What will the value of `edgar.name` be after the code below runs? How about `jason.name`? Explain why.

```swift
let edgar = Giant(name: "Edgar", weight: 520.0, homePlanet: "Earth")
let jason = edgar
jason.name = "Jason"

//edgar.name will be "Jason", jason.name = "Jason" since class is a reference type both will be changed when jason was changed
```

## Question 7

```
struct BankAccount {
    var owner: String
    var balance: Double

    mutating func deposit(_ amount: Double) {
        balance += amount
    }

    mutating func withdraw(_ amount: Double) {
        balance -= amount
    }
}
```

a. Explain why the code above doesn't compile, then fix it.
```swift
//the func is trying to change a property, in structs it needs the mutating keyword before func
```
b. Add a property called `deposits` of type `[Double]` that stores all of the deposits made to the bank account

c. Add a property called `withdraws` of type `[Double]` that stores all of the withdraws made to the bank account

d. Add a property called `startingBalance`.  Have this property be set to the original balance, and don't allow anyone to change it

e. Add a method called `totalGrowth` that returns a double representing the change in the balance from the starting balance to the current balance

```swift
struct BankAccount {
var owner: String
var balance: Double
private let startingBalance: Double
var deposits: [Double]
var withdraws: [Double]
mutating func deposit(_ amount: Double) {
balance += amount
deposits.append(amount)
}

mutating func withdraw(_ amount: Double) {
balance -= amount
withdraws.append(amount)
}

func totalGrowth() -> Double {
return balance - startingBalance
}
}
```
## Question 8

```swift
enum GameOfThronesHouse: String {
    case stark, lannister, targaryen, baratheon
}
```

a. Write a function that takes an instance of GameOfThronesHouse as input and, using a switch statement, returns the correct house words.

```
House Baratheon - Ours is the Fury

House Stark - Winter is coming

House Targaryen - Fire and Blood

House Lannister - A Lannister always pays his debts
```
```swift
func houseWords(house: GameOfThronesHouse) -> String {
switch house {
case .stark:
return "Winter is coming"
case .lannister:
return "A Lannister always pays his debts"
case .targaryen:
return "Fire and Blood"
case .baratheon:
return "Ours is the Fury"
}
}
```

b. Move that function to inside the enum as a method
```swift
enum GameOfThronesHouse: String {
case stark, lannister, targaryen, baratheon

func houseWords() -> String {
switch self {
case .stark:
return "Winter is coming"
case .lannister:
return "A Lannister always pays his debts"
case .targaryen:
return "Fire and Blood"
case .baratheon:
return "Ours is the Fury"
}
}

}
```
## Question 9

What are the contents of `library1` and `library2`? Explain why.

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

let library1 = MusicLibrary()
library1.add(track: "Michelle")
library1.add(track: "Voodoo Child")
let library2 = library1
library2.add(track: "Come As You Are")

//["Michelle","Voodoo Child","Come As You Are"] is the contents of both libraries because classes are a reference type

```

## Question 10

Make a function that takes in an array of strings and returns an array of strings. The function should determine if the string can be typed out using just one row on the keyboard. If the string can be typed out using just one row, that string should be in the returned array.  

```
Input: ["Hello", "Alaska", "Dad", "Peace", "Power"]

Output: ["Alaska", "Dad", "Power"]
```
```swift
var input2 = ["Hello", "Alaska", "Dad", "Peace", "Power"]

func oneRowOnKeyboard(arr: [String]) -> [String] {
let topRow = Set("qwertyuiop")
let middleRow = Set("asdfghjkl")
let bottomRow = Set("zxcvbnm")
var answer = [String]()
for a in arr {
let setA = Set(a.lowercased())
if setA.isSubset(of: topRow) || setA.isSubset(of: middleRow) || setA.isSubset(of: bottomRow) {
answer.append(a)
}
}
return answer
}

print(oneRowOnKeyboard(arr: input2))
```
