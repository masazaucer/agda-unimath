#  The infinite complex projective space

```agda
module synthetic-homotopy-theory.infinite-complex-projective-space where

open import foundation.dependent-pair-types
open import foundation.equivalences
open import foundation.set-truncations
open import foundation.universe-levels

open import synthetic-homotopy-theory.circle
```

## Definitions

### ℂP∞ as the 1-connected component of the universe at the circle

```agda
ℂP∞ : UU (lsuc lzero)
ℂP∞ = Σ (UU lzero) (λ X → type-trunc-Set (𝕊¹ ≃ X))

pt-ℂP∞ : ℂP∞
pr1 pt-ℂP∞ = 𝕊¹
pr2 pt-ℂP∞ = unit-trunc-Set id-equiv
```

### ℂP∞ as the 2-truncation of the 2-sphere
