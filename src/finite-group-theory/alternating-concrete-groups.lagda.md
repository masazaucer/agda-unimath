#  Alternating concrete groups

```agda
module finite-group-theory.alternating-concrete-groups where

open import elementary-number-theory.natural-numbers

open import finite-group-theory.cartier-delooping-sign-homomorphism
open import finite-group-theory.finite-type-groups

open import foundation.universe-levels

open import group-theory.concrete-groups
open import group-theory.kernels-homomorphisms-concrete-groups
```

## Idea

The alternating concrete groups are the kernels of the concrete sign homomorphism

## Definition

```agda
module _
  (n : ℕ)
  where
  
  alternating-Concrete-Group : Concrete-Group (lsuc (lsuc lzero))
  alternating-Concrete-Group =
    concrete-group-kernel-hom-Concrete-Group
      ( UU-Fin-Group lzero n)
      ( UU-Fin-Group (lsuc lzero) 2)
      ( cartier-delooping-sign n)
```
