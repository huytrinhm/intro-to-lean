<!-- .slide: class="section-slide" -->

<div class="r-vstack justify-center section-flow">
  <h2>Proof terms</h2>
  <p>Propositions in <code>Prop</code>, proofs as terms.</p>
</div>

--

## `Bool` vs `Prop`

### `Bool`

```language-lean
#check true
#check false
```

Computable truth values.
<!-- .element: class="subtitle" -->

### `Prop`

```language-lean
#check True
#check False
```

Theorem statements.
<!-- .element: class="subtitle" -->

`Bool` computes; `Prop` states claims.
<!-- .element: class="subtitle" -->

--

## A theorem is a type

```language-lean
theorem keepFirst (p q : Prop) (hp : p) (hq : q) : p := ?
```

- Assumptions become inputs.
- Goal: produce a term of type `p`.

--

## A proof term

```language-lean
theorem keepFirst (p q : Prop) (hp : p) (hq : q) : p := hp
```

- `hp` already has type `p`.
- The proof is the term `hp`.

--

## Conjunction as data

```language-lean
#check And.intro
#check And.left
#check And.right
```

- `And.intro` builds `p ∧ q`.
- `And.left` and `And.right` project its components.

--

## Composed proof term

```language-lean
theorem and_commutative
    (p q : Prop) (hpq : p ∧ q) : q ∧ p :=
  And.intro (And.right hpq) (And.left hpq)
```

- Extract `q`.
- Extract `p`.
- Build `q ∧ p`.

--

## Tactic script

```language-lean []
theorem and_commutative_tactic
    (p q : Prop) (hpq : p ∧ q) : q ∧ p := by
  apply And.intro
  exact And.right hpq
  exact And.left hpq
```

- `by` starts tactic mode.
- Tactics build the same proof term step by step.

--

## Recursion and induction

### Recursive program on `Nat`

```language-lean []
def f : Nat → ...
  | Nat.zero => ...
  | Nat.succ k => ... f k ...
```

### Induction proof on `Nat`

```language-lean []
theorem h : ∀ n : Nat, P n
  | Nat.zero => ...
  | Nat.succ k => ... h k ...
```

Same inductive structure, different goal.
<!-- .element: class="subtitle" -->
