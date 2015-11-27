# Traverse

Typeclassopedia: [Traversable](https://wiki.haskell.org/Typeclassopedia#Traversable).

Source: [scalaz.Traverse](https://github.com/scalaz/scalaz/blob/series/7.2.x/core/src/main/scala/scalaz/Traverse.scala)

Extends: [Foldable](Foldable.md), [Functor](Functor.md)

Generalizes Functor, so that `traverse` operates on the elements of a structure (as does `map`), but also captures effects in some new context.

Examples: `Option`, all the standard containers.

Related: [Foldable](Foldable.md)

## Operations

```scala
def traverse[G[_]: Applicative, A,B](fa: F[A])(f: A => G[B]): G[F[B]]
def sequence[G[_]: Applicative, A](fga: F[G[A]]): G[F[A]]
```

## Derived:

```scala
def sequenceU[A](self: F[A])(implicit G: ...): G[F[A]]  // "infers" the nested type constructor
def sequenceS[S, A](fga: F[State[S,A]]): State[S, F[A]]

def reverse[A](fa: F[A]): F[A]  // !

def zipWith[A, B, C](fa: F[A], fb: F[B])(f: (A, Option[B]) => C): (List[B], F[C])
// zipWithL/R, zipL/R

def mapAccumL[S,A,B](fa: F[A], z: S)(f: (S,A) => (S,B)): (S, F[B])
// mapaccumR
```

## Ops ("syntax")

```scala
// nothing notable
```