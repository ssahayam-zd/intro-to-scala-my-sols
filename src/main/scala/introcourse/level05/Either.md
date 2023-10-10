# Either Samples

```
def evenE(n: Int): Either[String, Int] = if (n % 2 == 0) Right(n) else Left (s"$n is not even")
```

```
evenE(10)

evenE(11)
```

Constructors:

```
evenE(2) match {
  case Right(v) => s"right: $v"
  case Left(e)  => s"left: $e"
}

evenE(1) match {
  case Right(v) => s"right: $v"
  case Left(e)  => s"left: $e"
}
```

Right-biased:

```
evenE(2).map(n => n + 1)

evenE(1).map(n => n + 1)

evenE(10).flatMap(n1 => evenE(2).map(n2 => n1 + n2))
```

For-comp

```
val e1 =
  for {
    one <- evenE(10)
    two <- evenE(20)
    three <- evenE(30)
  } yield one + two + three
```

```
val e2 =
  for {
    one <- evenE(10)
    two <- evenE(20)
    three <- evenE(31)
  } yield one + two + three
```

```
val e3 =
  for {
    one <- evenE(1)
    two <- evenE(20)
    three <- evenE(30)
  } yield one + two + three
```
