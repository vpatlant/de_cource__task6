# Итоговое задание №6

### Задание:
Используя полученные в этом разделе знания, решите следующую задачу. Немного изменим правила.

Теперь код необходимо не написать, а исправить. 

Вам дан фрагмент кода, который выполняет операции над списком строк. Код написан в императивном стиле, использует изменяемые переменные и циклы. Ваша задача — преобразовать этот код в функциональный стиль. 

Как? Решайте сами.

```scala
object StringProcessor {
  def processStrings(strings: List[String]): List[String] = {
    var result = List[String]()
    for (str <- strings) {
      if (str.length > 3) {
        result = result :+ str.toUpperCase
      }
    }
    result
  }

  def main(args: Array[String]): Unit = {
    val strings = List("apple", "cat", "banana", "dog", "elephant")
    val processedStrings = processStrings(strings)
    println(s"Processed strings: $processedStrings")
  }
}
```

### Решение :

Так как, функция StringProcessor используется единожды, заменим ее лямбда-функцией, принимающей на вход список строк.
К полученному списку применим фильтрацию элементов по длине strings.filter(x => x.length>3).
К отфильтрованному списку применим map(x => x.toUpperCase) для преобразования лементов списка  к верхнему регистру
Вызов переменной с присвоенной ей лямбда-функцией и передачу параметров осуществим в функции печати результата ${processedStrings(strings)}

Итоговый код:

```scala
object StringProcessor {
  def main(args: Array[String]): Unit = {
    val strings = List("apple", "cat", "banana", "dog", "elephant")

    val processedStrings  = (strings: List[String]) => strings.filter(x => x.length>3).map(x => x.toUpperCase)

    println(s"Processed strings: ${processedStrings(strings)}")
  }
}
```

Output: Processed strings: List(APPLE, BANANA, ELEPHANT)

