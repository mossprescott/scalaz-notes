# Applicative

Typeclassopedia: [Functor](https://wiki.haskell.org/Typeclassopedia#Applicative)

Source: [scalaz.Applicative](https://github.com/scalaz/scalaz/blob/series/7.2.x/core/src/main/scala/scalaz/Applicative.scala)

More powerful than [Functor](Functor.md) which it extends, but less powerful than [Monad](Monad.md).

Encapsulates "effectful" computations, by allowing a function in a context to be applied to a value in the same context. Also provides a way to lift arbitrary values into the context (and that's the only way to get values in).

Examples: most Functors.

Note: some Functors have more than one reasonable Applicative. For example, an `Applicative[List]` could either apply functions "pairwise" to values, or apply each function to each value (the cartesian product). TODO: how does that correspond to the standard `Monad[List]` implementation?

## Operations

```scala
def point[A](a: => A): F[A]
def ap[A,B](fa: => F[A])(f: => F[A => B]): F[B]
```

## Derived:

```scala
def apply2[A, B, C](fa: => F[A], fb: => F[B])(f: (A, B) => C): F[C]
def whenM[A](cond: Boolean)(f: => F[A]): F[Unit]  // also `unlessM`

def ap2[A,B,C](fa: => F[A], fb: => F[B])(f: F[(A,B) => C]): F[C]
... up to ap12

def apply2[A, B, C](fa: => F[A], fb: => F[B])(f: (A, B) => C): F[C]
... up to apply12

def tuple2[A,B](fa: => F[A], fb: => F[B]): F[(A,B)]
def lift2[A, B, C](f: (A, B) => C): (F[A], F[B]) => F[C]
```

## Ops ("syntax")

```scala
point = pure = η
<*> = ap // from Apply

*> is apply2 but discards the result on the left (after running it for its effects)
<* is apply2 but discards the result on the right (after running it for its effects)

|@| = ⊛  is applyN via ApplicativeBuilder

a tuple b = tuple2(a, b)
```