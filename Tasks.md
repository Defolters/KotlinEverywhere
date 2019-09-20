# Functions
```
/* 
напишите простую функцию
*/
main {
    assert(getHelloWorld() == "Hello World!")
    println("You are the best!")
}
```
# Extensions
```
/*
напишите расширение к строке
*/

fun main() {
    
    
    assert("String".reverseAndToCapital() == "GNIRTS")
    
    println("You are the best!")
}
```

# Function + Extension
```
/*
напишите расширение к Int, которое будет возвращать необходимую строку
*/
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
/*
напишите функцию, которая использует функцию any и принимает лямбду
*/

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
	Collections.sort(list, object { создайте анонимный объект })
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
/*
создайте класс, который содержит три поля. Два из них можно менять, а третье равняется произведению первых двух. Используйте Getters.
*/
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
/*
создайте класс Spice, который в конструкторе принимает два значения name и spiciness, а также содержит поле heat, которое зависит от spiciness следующим способом. 
 "mild" = 1
 "medium" = 3
 "spicy" = 5
 "very spicy" = 7
 "extremely spicy" = 10
Используйте Getters
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
    
    /*
    val spices = spicesNotFiltered.filter { it.heat > 5}
    */
    
    assert(spicesNotFiltered[0].heat == 1)
    assert(spicesNotFiltered[2].heat == 5)
    assert(spicesNotFiltered[6].heat == 10)
    
    assert(spices.all {it.heat > 5} )
    
    println("You are the best!")
}
```
# Inheritance 
```
/*
создайте класс Parent c методом getHobby, затем дочерний класс Children, где переопределите метод
*/

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
    /*
    примените методы filter, map к numbers
    */
    
    assert(filteredNumbers == listOf(5, 7))
    assert(squaredNumbers == listOf(25, 16, 49))
    
    println("You are the best!")
}
```

```
fun main(args: Array<String>) {
    
    val list = listOf("kotlin", "java", "c++")
    /*
    найдите минимальный объект по первому символу, используя minBy
    */
    assert(minValue == "c++")
    
    println("You are the best!")
}
```

```
fun main(args: Array<String>) {
    
    val list = listOf("kotlin", "java", "R")
    /*
    отсортируйте с помощью sortedBy
    */
    
    assert(sortedList == listOf("R", "java", "kotlin"))
    
    println("You are the best!")
}
```

```
fun main(args: Array<String>) {
    
    val numbers = listOf(1, 3, -4, 2, -11)  
	val (positive, negative) = // разделите лист на два. Первый содержит положительные, а второй отрицательные
    
    assert(positive == listOf(1, 3, 2))  
	assert(negative == listOf(-4, -11))  
    
    println("You are the best!")  
}
```
# Constants
```
class God() {
/*
добавьте статическое поле к классу
*/
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
/*
напишите класс Building c параметром buildingMaterial, который принимает значения wood и brick. Класс также содержит поле actualMaterialsNeeded, которое возвращает произведение buildingMaterial.numberNeeded на 100.
*/

/*
напишите функцию, которая принимает класс Building и возвращает true, если actualMaterialsNeeded < 500
*/

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
/*
напишите расширение к списку Int, которое возвращает список элементов, которые при приминении функции, которую передают в качестве параметра, дают ноль 
*/

fun main(args: Array<String>) {
    val numbers = listOf<Int>(1, 2, 3, 4, 5, 6, 7, 8, 9, 0)
    
    val answer = numbers.divisibleBy { it.rem(3) } // можно вызвать и так: numbers.divisibleBy({ it.rem(3) })
    
    assert(answer == listOf(3,6,9,0))
    
    println("You are the best!")
}
```
# Extension function literals
```
fun main(args: Array<String>) {
    
    val isEven: //TODO()  
    val isOdd: //TODO()  
    
    assert(42.isEven() == true)
    assert(41.isOdd() == true)
    
    println("You are the best!")
}
```

# Function apply
```
fun <T> T.myApply(f: T.() -> Unit): T { // допишите, чтобы работало :) }

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