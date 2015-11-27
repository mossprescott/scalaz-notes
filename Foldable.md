# Foldable

Typeclassopedia: [Foldable](https://wiki.haskell.org/Typeclassopedia#Foldable).

Source: [scalaz.Foldable](https://github.com/scalaz/scalaz/blob/series/7.2.x/core/src/main/scala/scalaz/Foldable.scala)

Containers which can be "folded" into a summary value. Basically a generalization of containers from which a sequence of values can be extracted, since it's always possible to contruct a list or other sequence by folding. All these operations discard the structure of the container; see [Traversable](Traversable.md) for ways of operating on values within a structure.

Examples: `Option`, all the standard containers.

Related: [Monoid](Monoid.md), [Traversable](Traversable.md)

## Operations

```scala
def foldMap[A, B: Monoid](fa: F[A])(f: A => B): B
def foldRight[A, B](fa: F[A], z: => B)(f: (A, => B) => B): B
```

## Derived:

```scala
def foldMap1Opt[A, B: Semigroup](fa: F[A])(f: A => B): Option[B]
def fold[A: Monoid](t: F[A]): A = foldMap[A, A](t)(x => x)
def foldLeft[A, B](fa: F[A], z: B)(f: (B, A) => B): B
// foldRightM, foldMapM, etc.

def findLeft[A](fa: F[A])(f: A => Boolean): Option[A]
def findRight[A](fa: F[A])(f: A => Boolean): Option[A]

def count[A](fa: F[A]): Int
def length[A](fa: F[A]): Int
def index[A](fa: F[A], i: Int): Option[A]

// toList/Vector/Set/Stream

def all[A](fa: F[A])(p: A => Boolean): Boolean
def any[A](fa: F[A])(p: A => Boolean): Boolean
// allM, anyM

def maximum[A: Order](fa: F[A]): Option[A]
def maximumOf[A, B: Order](fa: F[A])(f: A => B): Option[B]
def maximumBy[A, B: Order](fa: F[A])(f: A => B): Option[A]
// minumim

def sumr[A](fa: F[A])(implicit A: Monoid[A])
def sumr1Opt[A](fa: F[A])(implicit A: Semigroup[A]): Option[A]
// suml

def empty[A](fa: F[A]): Boolean
def element[A: Equal](fa: F[A], a: A): Boolean
def intercalate[A: Monoid](fa: F[A], a: A): A

// splitWith, selectSplit

def distinct[A: Order](fa: F[A]): IList[A]
def distinctE[A: Equal](fa: F[A]): IList[A]
def collapse[X[_]: ApplicativePlus, A](x: F[A]): X[A]
```

## Ops ("syntax")

```scala
∀ = all
∃ = any
```