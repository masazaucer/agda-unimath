#  Involutions

```agda
module foundation.involutions where

open import foundation-core.involutions public

open import foundation-core.automorphisms
open import foundation-core.functions
open import foundation-core.homotopies
open import foundation-core.identity-types
open import foundation-core.injective-maps
open import foundation-core.universe-levels

open import foundation.equivalences
open import foundation.equivalence-extensionality
```

## Idea

An involution on a type `A` is a map (or an equivalence) `f : A → A` such that `(f ∘ f) ~ id`

## Properties

### Involutions are their own inverse

```agda
htpy-own-inverse-is-involution : 
  {l : Level} {A : UU l} {f : Aut A} → is-involution-aut f → map-inv-equiv f ~ map-equiv f 
htpy-own-inverse-is-involution {f = f} is-involution-f x =
      is-injective-map-equiv f
        ( htpy-eq-equiv (right-inverse-law-equiv f) x ∙ inv (is-involution-f x))

own-inverse-is-involution :
  {l : Level} {A : UU l} {f : Aut A} → is-involution-aut f → inv-equiv f ＝ f
own-inverse-is-involution {f = f} =
  eq-htpy-equiv ∘ htpy-own-inverse-is-involution {f = f}
```
