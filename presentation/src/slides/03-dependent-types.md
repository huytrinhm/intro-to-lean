<!-- .slide: class="section-slide" -->

<div class="r-vstack justify-center section-flow">
  <h2>Dependent types</h2>
  <p>Types can mention values.</p>
</div>

--

## Ordinary types lose information

```language-lean
List α → List β → List (α × β)
```

Element types are preserved. Length is not.
<!-- .element: class="subtitle" -->

- Ignore extra data?
- Raise an error?
- Return an `Option`?
- Or make mismatched inputs unrepresentable?

--

## Value-dependent return types

```language-lean
(b : Bool) → if b then Nat else String
```

- Return type depends on `b`.
- The conditional appears in the type.

--

## Pattern matching refines types

```language-lean []
def natOrStringThree (b : Bool) : if b then Nat else String :=
  match b with
  | true => (3 : Nat)
  | false => "three"
```

- Each branch gets a more specific type.
- Values can refine types.

--

## Length-indexed vectors

```language-lean
inductive Vect (α : Type) : Nat → Type where
```

- `Vect α n` is indexed by length `n`.

--

## Base constructor

```language-lean
inductive Vect (α : Type) : Nat → Type where
  | nil : Vect α 0
```

- `nil : Vect α 0`
- Empty vector has length `0`.

--

## Cons updates the index

```language-lean []
inductive Vect (α : Type) : Nat → Type where
  | nil : Vect α 0
  | cons : α → {n : Nat} → Vect α n → Vect α (n + 1)
```

- `cons` maps length `n` to `n + 1`.
- The constructor enforces that change.

--

## `Vect.zip` rules out mismatch

```language-lean []
def Vect.zip : Vect α n → Vect β n → Vect (α × β) n
  | Vect.nil, Vect.nil => Vect.nil
  | Vect.cons x xs, Vect.cons y ys =>
      Vect.cons (x, y) (Vect.zip xs ys)
```

- Both inputs share index `n`.
- No unequal-length branch is needed.

--

## Dependent types summary

- **Ordinary function type**: `Nat → Nat`
- **Type constructor**: `List : Type → Type`
- **Indexed family**: `Vect : Type → Nat → Type`
- **Dependent function**: `(b : Bool) → if b then Nat else String`

Types can track values and invariants.
<!-- .element: class="subtitle" -->
