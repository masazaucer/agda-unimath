#  Truncated equality

```agda
module foundation.truncated-equality where

open import foundation.identity-types
open import foundation.truncated-types
open import foundation.truncation-levels
open import foundation.truncations
open import foundation.universe-levels
```

## Definition

```agda
trunc-eq : {l : Level} (k : 𝕋) {A : UU l} → A → A → Truncated-Type l k
trunc-eq k x y = trunc k (x ＝ y)
```

## Properties
