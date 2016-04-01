#Higher Oder Function 

## 匿名函数

```scala
val triple = (x: Double) => 3 * x
//or
def triple(x: Double) = 3 * x
```


## 快学scala P152 习题
```scala
 
    // 01
    def getValues(f: Int => Int, low: Int, high: Int) = {
      val ks = low to high
      val vs = (low to high).map{f}
      ks.zip(vs)
    }
    var r = getValues(x => x * x, -5, 5)
    // 02
    val nums = List(1, 2, 3, 10, -1, 20, 15)
    val maxNum = nums.reduceLeft { Math.max(_, _) }

//    println(fractorialOfNum(-1))
    // 03
    def fractorialOfNum(x: Int) = {
      if (x < 1) 1 else
      (1 to x).reduceLeft(_ * _)
    }
    // 04
    def fractorialOfNum(x: Int) = {
      (1 to x).foldLeft(1)((a, b) => a * b)
    }

    // 05
    def largest(f: Int => Int, inputs: Seq[Int]) = {
      inputs.map(f).reduceLeft{ Math.max(_, _) }
    }
//    println(largest(x => x * x, 1 to 10))

    // 06
    def largestAt(f: Int => Int, inputs: Seq[Int]) = {
      inputs(inputs.map(f).indexOf(inputs.map(f).reduceLeft({Math.max(_, _)})))
    }
//    println(largestAt(x => x * x, 1 to 10))

    // 07
    def adjustToPair(f: (Int, Int) => Int) = (pair: (Int, Int)) => f(pair._1, pair._2)
    val pairs = (1 to 10).zip(10 to 20).toList
    val result = pairs.map(adjustToPair(_ + _)(_))
//    println(result)

    // 08
    val a = Array("Hello", "World")
    val charLength = Array(5, 4)
    val result0 = a.corresponds(charLength)(_.length == _)
//    println(result0)

    // 09

    // 10
    def unless(condition: => Boolean)(doSomething: => Unit) {
      if (!condition) {
        doSomething
        unless(condition)(doSomething)
      }
    }
    var acc = 20
    unless(acc == 10){
      acc  -= 5
      println (acc)
    }

```