#  Catalan numbers

```agda
module elementary-number-theory.catalan-numbers where

open import elementary-number-theory.binomial-coefficients
open import elementary-number-theory.distance-natural-numbers
open import elementary-number-theory.inequality-natural-numbers
open import elementary-number-theory.multiplication-natural-numbers
open import elementary-number-theory.natural-numbers
open import elementary-number-theory.strong-induction-natural-numbers
open import elementary-number-theory.sums-of-natural-numbers

open import foundation.universe-levels

open import univalent-combinatorics.standard-finite-types
```

## Idea

The Catalan numbers are a sequence of natural numbers that occur in several combinatorics problems.

## Definitions

```agda
catalan-numbers : ℕ → ℕ
catalan-numbers =
  strong-ind-ℕ (λ _ → ℕ) (succ-ℕ zero-ℕ)
    ( λ k C →
      sum-Fin-ℕ k
        ( λ i →
          mul-ℕ
            ( C ( nat-Fin k i)
                ( leq-le-ℕ {x = nat-Fin k i} (strict-upper-bound-nat-Fin k i)))
            ( C ( dist-ℕ (nat-Fin k i) k)
                ( leq-dist-ℕ
                  ( nat-Fin k i)
                  ( k)
                  ( leq-le-ℕ
                    { x = nat-Fin k i}
                    ( strict-upper-bound-nat-Fin k i))))))

catalan-numbers-binomial : ℕ → ℕ
catalan-numbers-binomial n =
  dist-ℕ ((mul-ℕ 2 n) choose-ℕ n) ((mul-ℕ 2 n) choose-ℕ (succ-ℕ n))
```
