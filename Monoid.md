# Monoid

Typeclassopedia: [Monoid](https://wiki.haskell.org/Typeclassopedia#Monoid).

Source: [scalaz.Monoid](https://github.com/scalaz/scalaz/blob/series/7.2.x/core/src/main/scala/scalaz/Monoid.scala)

In math: a *semigroup* with an empty value, *e*. In other words, like a *group* but without defining an inverse for each value. Useful whenever values can be combined, and there some default, "empty" value.

Not often used directly, but often defined so that an instance is available to be used with other typeclasses that need to combine the values that inhabit some structure.

What's with the name? Apparently it was named by analogy with Monad, but that correspondence does not seem to be of any practical importance. See http://thread.gmane.org/gmane.comp.lang.haskell.cafe/50590 for the sort of debate this way of naming things inspires.

Pro: 
- precise: ties it clearly to the precisely-defined concept from algebra
- familiar and recognizable to math people
- avoids focus on any particular "concrete" example such appending lists (But note that the method names `append` and `zero` not only undermine that point completely but also are chosen from *different* examples!)

Examples: sequences (including Strings), numeric types (* or +), booleans (`||` or `&&`).

Extends: [Semigroup](Semigroup.md).

## Operations

```scala
def append(f1: F, f2: => F): F  // from Semigroup
def zero: F
```

## Derived:

```scala
def multiply(value: F, n: Int): F

def isMZero      (a: F)                  (implicit eq: Equal[F]): Boolean
def ifEmpty[B]   (a: F)(t: => B)(f: => B)(implicit eq: Equal[F]): B
def onNotEmpty[B](a: F)(v: => B)         (implicit eq: Equal[F], mb: Monoid[B]): B
def onEmpty[B]   (a: F)(v: => B)         (implicit eq: Equal[F], mb: Monoid[B]): B
```

## Ops ("syntax")

```scala
∅ = mzero = zero
```
