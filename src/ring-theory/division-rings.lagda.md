#  Division rings

```agda
module ring-theory.division-rings where

open import foundation.cartesian-product-types
open import foundation.identity-types
open import foundation.negation
open import foundation.universe-levels

open import ring-theory.invertible-elements-rings
open import ring-theory.nontrivial-rings
open import ring-theory.rings
```

## Idea

Division rings are nontrivial rings in which all nonzero elements are invertible.

## Definition

```agda
is-division-Ring :
  { l : Level} → Ring l → UU l
is-division-Ring R =
  (is-nontrivial-Ring R) ×
  ((x : type-Ring R) → ¬ (Id (zero-Ring R) x) → is-invertible-element-Ring R x)
```
