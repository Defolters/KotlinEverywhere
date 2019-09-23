# Functions
```
// 
fun getHelloWorld() = "Hello World!"
//
fun main() {
    assert(getHelloWorld() == "Hello World!")
    println("You are the best!")
}
```
# Extensions
```
// TODO
fun String.reverseAndToCapital(): String = this.reversed().toUpperCase()
//

fun main() {
    
    
    assert("String".reverseAndToCapital() == "GNIRTS")
    
    println("You are the best!")
}
```

# Function + Extension
```
//
fun Int.getAgeEndings(): String {
    var ageEnding = "Лет"
    
    if (this in 10..15) {
        return ageEnding
    }
    
    val yearLastDigit = this % 10
    
    if (yearLastDigit == 1) {
        ageEnding = "Год"
    } else if (yearLastDigit == 2 || yearLastDigit == 3 || yearLastDigit == 4) {
        ageEnding = "Года"
    }
    return ageEnding
}
//
fun main(args: Array<String>) {
    
    assert(1.getAgeEndings() == "Год")
    assert(4.getAgeEndings() == "Года")
    assert(5.getAgeEndings() == "Лет")
    assert(12.getAgeEndings() == "Лет")
    assert(21.getAgeEndings() == "Год")
    assert(42.getAgeEndings() == "Года")
    
    println("You are the best!")
}
```
# Lambda
```
//
fun containsFortyTwo(collection: Collection<Int>): Boolean = collection.any { it == 42 }
//

fun main() {
    
    val list = listOf(1, 5, 42, 99)
    val list2 = listOf(1, 5, 41, 99)
    
    assert(containsFortyTwo(list) == true)
    assert(containsFortyTwo(list2) == false)
    
    println("You are the best!")
}
```
# Object expresions
```
import java.util.Collections

fun getSortedList(list:List<String>): List<String> {
    Collections.sort(list, object : Comparator<String> {
    	override fun compare(x: String, y: String) =  x.first() - y.first()
	})
    
    return list
}

fun main(args: Array<String>) {
    
    val list = listOf("kotlin","java", "apocalypse")
    
    assert(getSortedList(list) == listOf("apocalypse","java", "kotlin"))
    
    println("You are the best!")
}
```
# Getters in class
```
//
class ProblemsMultiplier(){
    var amountOfProblemsBefore: Int = 0
    var multiplier: Int = 0
    val amountOfProblemsNow: Int
        get() {return amountOfProblemsBefore * multiplier }
}
//
fun main(args: Array<String>) {
    
    val pm = ProblemsMultiplier()
    
    pm.multiplier = 2
    pm.amountOfProblemsBefore = 5
    assert(pm.amountOfProblemsNow == 10)
    
    pm.multiplier = 2
    pm.amountOfProblemsBefore = 10
  	assert(pm.amountOfProblemsNow == 20)
    
    println("You are the best!")
}
```
# Constructors
```
//
class Spice(val name: String, val spiciness: String = "mild") {

    val heat: Int
        get() {
            return when (spiciness) {
                "mild" -> 1
                "medium" -> 3
                "spicy" -> 5
                "very spicy" -> 7
                "extremely spicy" -> 10
                else -> 0
            }
        }
}
//

/*
 "mild" = 1
 "medium" = 3
 "spicy" = 5
 "very spicy" = 7
 "extremely spicy" = 10
*/
fun main(args: Array<String>) {
    
    val spicesNotFiltered = listOf(
        Spice("curry", "mild"),
        Spice("pepper", "medium"),
        Spice("cayenne", "spicy"),
        Spice("ginger", "mild"),
        Spice("red curry", "medium"),
        Spice("green curry", "mild"),
        Spice("hot pepper", "extremely spicy")
    )
    
    //
    val spices = spicesNotFiltered.filter { it.heat > 5}
    //
    
    assert(spicesNotFiltered[0].heat == 1)
    assert(spicesNotFiltered[2].heat == 5)
    assert(spicesNotFiltered[6].heat == 10)
    
  	assert(spices.all {it.heat > 5} )
    
    println("You are the best!")
}
```
# Inheritance 
```
//
open class Parent(val name: String, val surname: String) {

    open fun getHobby(): String {
        return "Lying"
    }
}


class Children(val title: String, val author: String, val bestGame: String) : Parent(title, author) {

    override fun getHobby(): String {
        return "Playing $bestGame"
    }
}
//

fun main(args: Array<String>) {
    val game = "cyberpunk"
    val parent = Parent("name", "surname")
    val children = Children("name", "surname", game)
    
    assert(parent.getHobby() == "Lying")
    assert((children as Parent).getHobby() == "Playing $game")
    
    println("You are the best!")
}
```
# Collections

```
fun main(args: Array<String>) {

    val numbers = listOf(5, -4, 7)
    //
    val filteredNumbers = numbers.filter { it > 0 }
    val squaredNumbers = numbers.map { it * it }
    //
    
    assert(filteredNumbers == listOf(5, 7))
	assert(squaredNumbers == listOf(25, 16, 49))
    
    println("You are the best!")
}
```

```
fun main(args: Array<String>) {
    
    val list = listOf("kotlin", "java", "c++")
    
    val minValue = list.minBy { it.first() }
    
    assert(minValue == "c++")
    
    println("You are the best!")
}
```

```
fun main(args: Array<String>) {
    
    val list = listOf("kotlin", "java", "R")
    
    val sortedList = list.sortedBy { it.length }
    
    assert(sortedList == listOf("R", "java", "kotlin"))
    
    println("You are the best!")
}
```

```
fun main(args: Array<String>) {
    
    val numbers = listOf(1, 3, -4, 2, -11)
	val (positive, negative) = numbers.partition { it > 0 }
    
    assert(positive == listOf(1, 3, 2))
	assert(negative == listOf(-4, -11))
    
    println("You are the best!")
}
```
# Constants
```
class God() {
//
	companion object {
		const val STATIC = "STATIC"
	}
//
}

fun main(){
    assert(God.STATIC == "STATIC")
    
    println("You are the best!")
}
```
# Generics & Generic functions
```
open class BaseBuildingMaterial() {
    open val numberNeeded = 1
}

class Wood : BaseBuildingMaterial() {
    override val numberNeeded = 4
}

class Brick : BaseBuildingMaterial() {
    override val numberNeeded = 8
}
//
class Building<T: BaseBuildingMaterial>(val buildingMaterial: T) {

    val baseMaterialsNeeded = 100
    val actualMaterialsNeeded = buildingMaterial.numberNeeded * baseMaterialsNeeded
}
//

//
fun <T : BaseBuildingMaterial> isSmallBuilding(building: Building<T>): Boolean {
    if (building.actualMaterialsNeeded < 500) return true
    else return false
}
//

fun main(){
    val woodBuilding = Building(Wood())
    val brickBuilding = Building(Brick())
    
    // Generics
    assert(woodBuilding.actualMaterialsNeeded == 400)
    assert(brickBuilding.actualMaterialsNeeded == 800)
    
    // Generic functions
    assert(isSmallBuilding(woodBuilding) == true)
    assert(isSmallBuilding(brickBuilding) == false)
    
    println("You are the best!")
}
```
# High-order functions
```
//
fun List<Int>.divisibleBy(block: (Int) -> Int): List<Int> {
    val result = mutableListOf<Int>()
    for (item in this) {
        if (block(item) == 0) {
            result.add(item)
        }
    }
    return result
}
//

fun main(args: Array<String>) {
    val numbers = listOf<Int>(1, 2, 3, 4, 5, 6, 7, 8, 9, 0)
    
    val answer = numbers.divisibleBy { it.rem(3) }
    
    assert(answer == listOf(3,6,9,0))
    
    println("You are the best!")
}
```
# Extension function literals
```
fun main(args: Array<String>) {
    //
    val isEven: Int.() -> Boolean = { TODO() }
    val isOdd: Int.() -> Boolean = { TODO() }
    //
    assert(42.isEven() == true)
    assert(41.isOdd() == true)
    
    println("You are the best!")
}
```

# Function apply
```
fun <T> T.myApply(f: T.() -> Unit): T { f(); return this }

fun main(args: Array<String>) {
    
    val string = StringBuilder().myApply {
        val list = listOf("You", "are", "the", "best!")
        for (word in list) {
            append(word)
        }
    }.toString()
    
    println(string)
}
```