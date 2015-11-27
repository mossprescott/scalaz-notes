# Functor

Typeclassopedia: [Functor](https://wiki.haskell.org/Typeclassopedia#Functor).

Source: [scalaz.Functor](https://github.com/scalaz/scalaz/blob/series/7.2.x/core/src/main/scala/scalaz/Functor.scala)

Apply a function to the values in some context, preserving the context.

Nomenclature: the name was borrowed from linguistics (according to wikipedia).

Examples: any monad, including `\/`, `Task`, `Option`, `List` (and other collections). Also [TODO: good non-monad examples.]

## Operations

```scala
def map[A, B](fa: F[A])(f: A => B): F[B]
```

## Derived:

```scala
def lift[A, B](f: A => B): F[A] => F[B]
def void[A](fa: F[A]): F[Unit]
def strengthL[A, B](a: A, f: F[B]): F[(A, B)]  // also strengthR
def fproduct[A, B](fa: F[A])(f: A => B): F[(A, B)]
```

## Ops ("syntax")

```scala
∘ = map
>| = as = map(_ => b)
```