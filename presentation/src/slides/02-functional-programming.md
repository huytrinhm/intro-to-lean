<!-- .slide: class="r-vstack justify-center section-slide" -->

## Lean starts from familiar ground
<!-- .element: class="r-fit-text" -->

Before dependent types and proofs, Lean already looks like a typed functional language.

--

## First contact with Lean

### `#check`

```nohighlight
#check 1
#check true
```

### `#eval`

```nohighlight
#eval 1 + 2
```

- `#check` asks for the type of an expression.
- `#eval` asks Lean to compute the expression.
- `(1 + 2 : Nat)` makes the intended type explicit.

--

## Start with a named value

```nohighlight
def hello : String := "Hello"
```

- `def` introduces a name.
- `:=` defines it by the expression on the right.
- Lean records the result type in the environment.

--

## Turn the definition into a function

```nohighlight
def add1 (n : Nat) : Nat := n + 1
```

- `(n : Nat)` introduces an argument.
- The return type is part of the contract.

--

## Multiple parameters are still ordinary typed programming

```nohighlight
def addTwo (n : Nat) (k : Nat) : Nat := n + k
```

- Functions can take several typed inputs.
- Types already describe useful input and output structure.

--

## Data is defined by its constructors

```nohighlight
inductive Bool where
  | false : Bool
  | true : Bool
```

- Constructors describe the legal shapes of values.
- `Bool` has exactly two constructors.

--

## Constructors build data; `match` consumes it

```nohighlight
def notBool (b : Bool) : Bool :=
  match b with
  | Bool.false => Bool.true
  | Bool.true => Bool.false
```

- Pattern matching branches on the constructor that built the value.
- The structure of the program follows the structure of the data.

--

## Natural numbers are inductive too

```nohighlight
inductive Nat where
  | zero : Nat
  | succ (n : Nat) : Nat
```

- `Nat` is built from `zero` and repeated `succ`.
- Recursive data leads naturally to recursive programs.

--

## Recursive programs follow the same shape

```nohighlight
def double (n : Nat) : Nat :=
  match n with
  | Nat.zero => Nat.zero
  | Nat.succ k => Nat.succ (Nat.succ (double k))
```

- Handle the base case `Nat.zero`.
- Recur on the smaller value `k`.

--

## What ordinary types already give us

- Typed expressions with static and dynamic views
- Definitions and function signatures
- Inductive data, pattern matching, and structural recursion

### Type constructors already vary with types

```nohighlight
List : Type → Type
List Nat
List String
```

Next step: can types vary with values too?
<!-- .element: class="subtitle" -->
