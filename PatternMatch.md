# PatternMatch

```scala
object PatternMatch {
  def main(args: Array[String]) {
    println(matchTest(10))
  }

  def matchTest(x: Int): String = x match {
    case 1 => "One"
    case 2 => "Two"
    case 3 => "Three"
    case _ => "Unknown"
  }  
}
```

## case class
```scala
  case class Person(val name: String, val age: Int)
  val personList = List(Person("Alice", 10), Person("Boom", 20), Person("Look", 10))
  for (person <- personList) {
    person match {
      case Person("Alice", 10) => println("Alice")
      case Person("Boom", 20) => println("Boom")
      case Person(name, age) => println(s"name = $name, age = $age")
      case _ => print("welll...")
    }
  }  
```

## 嵌套
```scala
  abstract class Item
  case class Article(description: String, price: Double) extends Item
  case class Bundle(description: String, discount: Double, items: Item*) extends Item

  def price(item: Item): Double = item match {
    case Article(des, price) => price
    case Bundle(_, _, Article(_, price), _ *) => price
    case Bundle(_, _, art @ Article(_, _), rest @ _ *) => art.price + rest.map(price _).sum
    case Bundle(_, discount, items @ _ *) => items.map(price _).sum - discount
  }

```

```scala
    case Bundle(_, _, art @ Article(_, _), rest @ _ *) => art.price + rest.map(price _).sum
```

`@`符号是将嵌套的值绑定到前面的变量
