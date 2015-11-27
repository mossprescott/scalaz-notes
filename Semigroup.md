# Semigroup

Typeclassopedia: [Semigroup](https://wiki.haskell.org/Typeclassopedia#Semigroup).

Source: [scalaz.Semigroup](https://github.com/scalaz/scalaz/blob/series/7.2.x/core/src/main/scala/scalaz/Semigroup.scala)

In math: a set *S* and a an associative operator ⊕, which combines elemnts from *S*. In FP, just an operator `(F, F) => F`.

See [Monoid](Monoid.md), which adds an identity value, `zero`. Therefore, Semigroup is used when there is a way to combine values, but in general no "empty" value.

Nomenclature: a *group* in math is similar, but has an identity value (`zero`, as in Monoid) and defines an inverse for every value (negation). An *abelian group* is one in which the oprator is also commutative (aka a *commutative group*).

Examples: other than Mondoids, NonEmptyList, numbers under `min` or `max`, many *ad hoc* types have semigroups—especially anything with no "empty" values.

Related: [Monoid](Monoid.md), 

## Operations

```scala
def append(f1: F, f2: => F): F
```

Note: lazy in the second argument.

## Derived:

```scala
def multiply1(value: F, n: Int): F
```

## Ops ("syntax")

```scala
|+| = ⊹ = mappend = append
```

Note: ⊹ is the "Hermitian conjugate matrix" code point.