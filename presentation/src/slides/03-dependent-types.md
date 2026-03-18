<!-- .slide: class="r-vstack justify-center section-slide" -->

## This is where Lean stops feeling ordinary
<!-- .element: class="r-fit-text" -->

Dependent types preserve relationships that ordinary types forget.

--

## Ordinary types are sometimes too weak

```language-lean
List α → List β → List (α × β)
```

Element types are remembered. Equal length is not.
<!-- .element: class="subtitle" -->

- Ignore extra data?
- Raise an error?
- Return an option?
- Or make mismatched inputs unrepresentable?

--

## A return type can depend on the input value

```language-lean
(b : Bool) → if b then Nat else String
```

- The result type itself changes with the input value.
- The familiar `if ... then ... else ...` appears inside the type.

--

## Pattern matching refines the type too

```language-lean []
def natOrStringThree (b : Bool) : if b then Nat else String :=
  match b with
  | true => (3 : Nat)
  | false => "three"
```

- Pattern matching chooses a branch at runtime.
- It also sharpens the static type in each branch.
- Values can refine types.

--

## What if a collection remembered its length?

```language-lean
inductive Vect (α : Type) : Nat → Type where
```

- `Vect α n` is a family of types indexed by a natural number.
- Read it as vectors of `α` with length `n`.

--

## The constructors carry the length story

```language-lean
inductive Vect (α : Type) : Nat → Type where
  | nil : Vect α 0
```

- `nil` can only build a vector of length `0`.
- The invariant is already visible in the constructor.

--

## Adding one element changes the index too

```language-lean []
inductive Vect (α : Type) : Nat → Type where
  | nil : Vect α 0
  | cons : α → {n : Nat} → Vect α n → Vect α (n + 1)
```

- Adding an element changes the type from length `n` to `n + 1`.
- The constructor enforces that change statically.

--

## `Vect.zip` has no mismatched-length cases

```language-lean []
def Vect.zip : Vect α n → Vect β n → Vect (α × β) n
  | Vect.nil, Vect.nil => Vect.nil
  | Vect.cons x xs, Vect.cons y ys =>
      Vect.cons (x, y) (Vect.zip xs ys)
```

- Both inputs share the same length index `n`.
- Unequal-length branches are not missing by accident.
- A runtime check becomes a compile-time guarantee.

--

## The type checker knows more

- **Ordinary function type**: `Nat → Nat`
- **Type constructor**: `List : Type → Type`
- **Indexed family**: `Vect : Type → Nat → Type`
- **Dependent function**: `(b : Bool) → if b then Nat else String`

Once types express richer invariants, theorem proving stops feeling like an unrelated extra.
<!-- .element: class="subtitle" -->
