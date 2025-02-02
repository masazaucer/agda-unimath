#  Representations of monoids

```agda
module group-theory.representations-monoids where

open import category-theory.categories
open import category-theory.endomorphisms-of-objects-categories

open import foundation.dependent-pair-types
open import foundation.identity-types
open import foundation.universe-levels

open import group-theory.homomorphisms-monoids
open import group-theory.monoids
```

## Idea

Representations of a monoid `M` in a category `C` consist of an object `V` in `C` equipped with a monoid homomorphism from `M` to the monoid of endomorphisms on `V`.

## Definition

```agda
categorical-representation-Monoid :
  {l1 l2 l3 : Level} (C : Cat l1 l2) (M : Monoid l3) → UU (l1 ⊔ l2 ⊔ l3)
categorical-representation-Monoid C M =
  Σ (obj-Cat C) (λ V → hom-Monoid M (monoid-endo-Cat C V))

module _
  {l1 l2 l3 : Level} (C : Cat l1 l2) (M : Monoid l3)
  (ρ : categorical-representation-Monoid C M)
  where

  obj-categorical-representation-Monoid : obj-Cat C
  obj-categorical-representation-Monoid = pr1 ρ

  hom-action-categorical-representation-Monoid :
    hom-Monoid M (monoid-endo-Cat C obj-categorical-representation-Monoid)
  hom-action-categorical-representation-Monoid = pr2 ρ

  action-categorical-representation-Monoid :
    type-Monoid M → endo-Cat C obj-categorical-representation-Monoid
  action-categorical-representation-Monoid =
    map-hom-Monoid M
      ( monoid-endo-Cat C obj-categorical-representation-Monoid)
      ( hom-action-categorical-representation-Monoid)

  preserves-mul-action-categorical-representation-Monoid :
    (x y : type-Monoid M) →
    ( action-categorical-representation-Monoid (mul-Monoid M x y)) ＝
    ( comp-endo-Cat C
      ( obj-categorical-representation-Monoid)
      ( action-categorical-representation-Monoid x)
      ( action-categorical-representation-Monoid y))
  preserves-mul-action-categorical-representation-Monoid =
    preserves-mul-hom-Monoid M
      ( monoid-endo-Cat C obj-categorical-representation-Monoid)
      ( hom-action-categorical-representation-Monoid)

  preserves-unit-action-categorical-representation-Monoid :
    action-categorical-representation-Monoid (unit-Monoid M) ＝
    id-endo-Cat C obj-categorical-representation-Monoid
  preserves-unit-action-categorical-representation-Monoid =
    preserves-unit-hom-Monoid M
      ( monoid-endo-Cat C obj-categorical-representation-Monoid)
      ( hom-action-categorical-representation-Monoid)
```
