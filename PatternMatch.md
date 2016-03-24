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
