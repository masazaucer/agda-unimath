#  Bracelets

```agda
module univalent-combinatorics.bracelets where

open import elementary-number-theory.natural-numbers

open import foundation.dependent-pair-types
open import foundation.universe-levels

open import graph-theory.polygons

open import univalent-combinatorics.standard-finite-types
```

## Definition

### Bracelets

```agda
bracelet : ℕ → ℕ → UU (lsuc lzero)
bracelet m n = Σ (Polygon m) (λ X → vertex-Polygon m X → Fin n)
```
