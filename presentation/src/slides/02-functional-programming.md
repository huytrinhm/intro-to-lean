<!-- .slide: class="section-slide" -->

## Functional core

Typed definitions, inductive data, structural recursion.

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
- The type annotation is explicit.

--

## A unary function

```language-lean
def add1 (n : Nat) : Nat := n + 1
```

- `(n : Nat)` declares the parameter type.
- `: Nat` declares the return type.

--

## Multiple parameters

```language-lean
def addTwo (n : Nat) (k : Nat) : Nat := n + k
```

- Each parameter has a type.
- The return type stays explicit.

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
