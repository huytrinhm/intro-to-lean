<!-- .slide: class="r-vstack justify-center section-slide" -->

## Theorem proving is the same story pushed further
<!-- .element: class="r-fit-text" -->

A theorem statement is another typed object inside the same language. A proof is evidence for it.

--

## `Bool` and `Prop` are different

### Boolean values

```nohighlight
#check true
#check false
```

These are values of type `Bool`.
<!-- .element: class="subtitle" -->

### Propositions

```nohighlight
#check True
#check False
```

These live in `Prop`, where theorem statements are expressed.
<!-- .element: class="subtitle" -->

Logic is represented inside the same type-theoretic language.
<!-- .element: class="subtitle" -->

--

## Lean asks for evidence, not persuasion

```nohighlight
theorem keepFirst (p q : Prop) (hp : p) (hq : q) : p := ?
```

- Assume `p`, `q`, `hp : p`, and `hq : q`.
- The goal is to produce a term of type `p`.

--

## The smallest proof looks like returning a value

```nohighlight
theorem keepFirst (p q : Prop) (hp : p) (hq : q) : p := hp
```

- The goal asks for evidence of type `p`.
- `hp` already has that type.
- A proof can be as small as returning the needed value.

--

## Conjunction behaves like structured data

```nohighlight
#check And.intro
#check And.left
#check And.right
```

- `And.intro` builds evidence for `p ∧ q`.
- `And.left` and `And.right` project the two parts back out.
- Proof structure mirrors typed programming structure.

--

## A larger proof is still just composition

```nohighlight
theorem and_commutative (p q : Prop) (hpq : p ∧ q) : q ∧ p :=
  And.intro (And.right hpq) (And.left hpq)
```

- `And.right hpq` extracts the proof of `q`.
- `And.left hpq` extracts the proof of `p`.
- `And.intro` rebuilds them as `q ∧ p`.

--

## The same proof can be built interactively

```nohighlight
theorem and_commutative_tactic (p q : Prop) (hpq : p ∧ q) : q ∧ p := by
  apply And.intro
  exact And.right hpq
  exact And.left hpq
```

- `by` opens tactic mode.
- Lean can guide proof construction step by step.
- The theorem is the same; only the proof style changes.

--

## Recursion and induction have the same shape

### Recursive program on `Nat`

```nohighlight
def f : Nat → ...
  | Nat.zero => ...
  | Nat.succ k => ... f k ...
```

### Induction proof on `Nat`

```nohighlight
theorem h : ∀ n : Nat, P n
  | Nat.zero => ...
  | Nat.succ k => ... h k ...
```

The parallel comes from the same inductive structure introduced in the programming part of the talk.
<!-- .element: class="subtitle" -->
