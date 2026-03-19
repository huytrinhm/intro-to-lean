<!-- .slide: class="section-slide" -->

<div class="r-vstack justify-center section-flow">
  <h2>Functional core</h2>
  <p>Typed definitions, inductive data, structural recursion.</p>
</div>

--

## Basic commands

### `#check`

```language-lean
#check 1
#check true
```

### `#eval`

```language-lean
#eval 1 + 2
```

- `#check` infers a type.
- `#eval` reduces an expression.
- `(1 + 2 : Nat)` adds a type annotation.

--

## A constant

```language-lean
def hello : String := "Hello"
```

- `def` binds a name.
- `:=` gives its value.
- The type annotation can be implicit/omitted.
- Lean offer Hindley-Milner type inference.

--

## A unary function

```language-lean
def add1 (n : Nat) : Nat := n + 1
```

- `(n : Nat)` declares the parameter type.
- `: Nat` declares the return type.
- Type annotation can be omitted.

--

## Multiple parameters

```language-lean
def addTwo (n : Nat) (k : Nat) : Nat := n + k
```

- Each parameter has a type.
- Prefer to be explicit about type.

--

## Inductive data

```language-lean []
inductive Bool where
  | false : Bool
  | true : Bool
```

- Constructors define valid values.
- `Bool` has two cases.

--

## Pattern matching

```language-lean []
def notBool (b : Bool) : Bool :=
  match b with
  | Bool.false => Bool.true
  | Bool.true => Bool.false
```

- Match on constructors.
- Program shape follows data shape.

--

## Inductive naturals

```language-lean []
inductive Nat where
  | zero : Nat
  | succ (n : Nat) : Nat
```

- Beside constant, constructor can also be unintepreted function.
- `succ n` just store `n`, it does compute anything.
- `Nat` is built from `zero` and `succ`.
- Programs over `Nat` follow those constructors.

--

## Structural recursion

```language-lean []
def double (n : Nat) : Nat :=
  match n with
  | Nat.zero => Nat.zero
  | Nat.succ k => Nat.succ (Nat.succ (double k))
```

- Base case: `Nat.zero`.
- Recursive case: smaller `k`.

--

## Functional core summary

- Typed expressions
- Definitions and functions
- Inductive data and recursion

### Type constructors

```language-lean
List : Type → Type
List Nat
List String
```

Next: types indexed by values.

<!-- .element: class="subtitle" -->
