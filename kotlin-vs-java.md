## Null safety

Kotlin adds null safety into into it's type system as a first class
concept. The following would not compile:

```kotlin
val maybe: String = null
```
In Kotlin every type has a corresponding 'optional' type denoted
with a `?`:

```kotlin
val maybe: String? = null
```

If we want to do anything with an optional value we need to convince the compiler that the value really isn't `null`:

```kotlin
val maybe: String? = null

if (maybe != null) {
  println(maybe.length)
}
```

We also have syntactical sugar that makes this easier for us:

```kotlin
val maybe: String? = null
val words: Int? = string?.split(" ")?.length

println("The string contains " + (length :? 0) + " words")
```
This adds significant advantages over Java as it forces us to make decisions over the nullability of our variables and return types. It also forces us to deal with the consequences of nullable value explicitly rather than letting them sneak into production.

## Data classes

Often when building Java applications we want to express data "models" or "entities" using
instances of classes:

```java
class Dog {
  public final String name;

  public Dog(String name) {
    this.name = name;
  }
}
```

We'd then also like to be able to have meaningful equality for these things but
we have to implement this ourselves:

```java
class Dog {
  public final String name;

  public Dog(String name) {
    this.name = name;
  }

  @Override
  public boolean equals(Object obj) {
    if (obj instanceof Dog) {
      Dog otherDog = (Dog) obj;
      return dog.name.equals(otherDog.name);
    } else {
      return false;
    }
  }
}
```

The above implementation can lead to problems as it introduces possible error cases
and forces us to remember to maintain our `equals()` method (such as when we add another field to an entity). Projects like
[Lombok](https://projectlombok.org/) attempt to address this by adding generated
`equals()` implementations but Kotlin adds `data` classes to address this at a language. The following
would be equivalent to the above Java:

```kotlin
data class Dog(val name: String)
```

Equality is probably the largest advantage of data classes in terms of preventing mistakes
as our code evolves but they also add other conveniences such as meaningful `toString()` implementation
and a `copy` function that allows you to build a new instance of an instance of a data class
with modified values.

## Cleaner collections interface

## Similarity to Swift

## Parity with Server on Android
