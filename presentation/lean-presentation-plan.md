# Lean Presentation Plan

## Goal

This presentation introduces Lean to beginner CS students.
It should be modular rather than locked to a fixed runtime: the same conceptual path
should still work whether the lecture is shorter, longer, or split across meetings.
It should answer one central question:

> What is the core idea of Lean?

The talk should not try to cover all of Lean. The target outcome is that students leave with one clear mental model:

> Lean is a language in which programs, types, and proofs are all expressions in one unified system, so the type checker can track more meaning than in ordinary programming languages.

Every other learning objective should support that single idea.

## Audience Assumptions

- CS students with basic programming knowledge
- Familiar with variables, functions, recursion, and simple static typing
- No prior background in proof assistants or type theory required

## Core Message

Lean starts like a functional programming language, then gradually reveals its core idea:

- first, types classify programs
- then, dependent types let types express richer information about programs
- finally, propositions are treated as types, so proofs become programs with highly informative types

The presentation is coherent only if the audience sees these as three stages of one idea, not three separate topics.
The formal theory should appear only after the core examples make that story believable.

## One Guiding Question

Use this question throughout the lecture:

> What more can Lean know statically about a program than an ordinary language can know?

That question is the thread connecting functional programming, dependent types, and theorem proving.

## Lecturer's Lens

This should be taught as a Principles of Programming Languages lecture, not as a product tour.

- Keep returning to the difference between syntax, meaning, and guarantees.
- Show how each new Lean feature changes what can be checked statically.
- Present types as a language for expressing invariants, not just labels on values.
- Treat proofs as a natural extension of typed programming, not as a sudden switch into mathematics.
- Emphasize design tradeoffs: stronger guarantees usually require more structure from the programmer.
- Use formal theory to clarify examples after they land, not to replace them.

## Conceptual Spine

The lecture should build around this reasoning chain:

1. Programs are expressions, and Lean can tell us their types and evaluate them.
2. Definitions and functions let us name computations with explicit input and output structure.
3. Inductive types define the legal shapes of data.
4. Pattern matching and recursion are the canonical ways to consume such data.
5. Ordinary types classify values, but often forget relations we care about.
6. Some familiar forms already weaken the wall a little: polymorphic code varies with a type, and type constructors like `List` build new types from types.
7. Dependent types go further by letting types mention values, so some relations are preserved at compile time.
8. Propositions-as-types is the final step: a specification becomes a type, and a proof is a program inhabiting it.

If the audience internalizes that chain, the talk has succeeded.

## Core Idea of Lean

If you have to compress the whole lecture into two sentences, use this:

- In most languages, types classify values but remain somewhat separate from the values themselves.
- In Lean, the boundary is much weaker: values can refine types, and logical claims are also represented as types, so programming and proving become two uses of the same underlying language.

## Motivation Arc

To keep the lecture interesting, organize it around three escalating kinds of mistakes or questions:

1. Wrong kind of thing:
   A language should reject nonsense like applying the wrong operation to the wrong kind of data.
2. Right kind, wrong shape:
   A language should ideally catch mistakes like zipping collections of different lengths or indexing where the bounds story is unclear.
3. Right program shape, but is the claim actually true?
   A language for rigorous reasoning should let us express and check claims about programs and mathematical objects themselves.

That gives the lecture a narrative:

- ordinary types catch "wrong kind"
- dependent types help with "wrong shape" or "missing invariant"
- theorem proving addresses "is this specification or claim actually justified?"

## Running Motivating Problems

Use one or two recurring problems throughout the talk so the audience keeps seeing why the theory matters.

Recommended problems:

- CS problem: `zip` on two collections of unequal length
  Why useful:
  This motivates the move from ordinary types to dependent types.
- CS problem: static vs run-time checking
  Why useful:
  This frames the entire lecture around what can be known before execution.
- Math/logic problem: why should a theorem be checkable by a machine at all?
  Why useful:
  This motivates propositions-as-types without sounding mystical.

Optional supporting examples:

- indexing into a collection with bounds information
- a sorting function whose type does not yet express what "correct" means
- a simple logical statement like `p ∧ q → q ∧ p`

## Wow Moment Strategy

The lecture should have one clear conceptual climax and one smaller secondary surprise.

Primary wow moment:

- Impossible cases disappear in `Vect.zip`.
- This is the best moment to impress both beginners and experienced students.
- Beginners see that the language can prevent a whole class of bugs.
- Experienced students see something deeper: the type indices refine pattern matching so strongly that the missing cases are not "forgotten"; they are genuinely impossible.

Secondary wow moment:

- A theorem can be read as a program, and a proof term can look like an ordinary function.
- This is the moment where "proofs are programs" stops sounding like philosophy and starts feeling concrete.

Rule for wow moments:

- Do not oversell them.
- Build enough context first so the audience can understand why the moment is surprising.
- Pause after the reveal and state explicitly why it is impressive.

## Narration Style

The talk should feel curious, not encyclopedic.

- Start from something familiar, then reveal what is strange about Lean.
- Use contrast often: "In most languages..., but in Lean..."
- Keep definitions short. Let examples do most of the work.
- Ask a few rhetorical questions to keep the room mentally involved.
- Sound like you are discovering the idea with the audience, not reciting notes.
- Avoid making Lean sound magical. It is more convincing when it sounds precise and a little surprising.
- Anchor abstract ideas in small CS or math problems before naming the theory.
- After a major example lands, allow one short formal zoom-out so students can attach the right name to what they just saw.

## Narration Goal

The audience should feel:

- "I know what problem Lean is trying to solve."
- "I can see why dependent types are a big deal."
- "I finally understand why people say proofs are programs."

## Reusable Transition Lines

These are useful if you want the talk to flow more naturally:

- "So far, nothing here is especially mysterious."
- "This is where Lean stops feeling like an ordinary language."
- "That sounds abstract, so let us pin it down with one example."
- "Now the interesting part is what the type checker knows."
- "This is the moment where programming turns into proving."
- "We have seen the example; now we can give it the formal name."

## Pacing Principle

Do not optimize this deck for a fixed runtime.
Optimize it for conceptual continuity.

- Keep the opening short and motivating.
- Spend most of the lecture on the move from ordinary types to dependent types.
- Protect the `Vect.zip` example and the first proof example; cut secondary material before cutting those.
- If you need a shorter version, compress early warm-up slides and keep only one compound proof example.
- If something has to be cut late, cut the tactic slide before cutting the first term-style proof.
- If you have more time, add more pauses, questions, and live evaluation rather than more advanced topics.

## Step-by-Step Teaching Principle

This version should feel like a guided climb, not a data dump.

- Introduce only one new big idea at a time.
- Show concrete code before giving the abstract name for the idea.
- Once a major example has landed, it is fine to pause for one short formal lens.
- Pause twice for short recap slides so the audience can reorganize what they have learned.
- Delay proof language until students already trust Lean as a programming language.
- Delay most theory names until students have already seen the phenomenon those names describe.
- Delay the phrase "Curry-Howard correspondence" until after the audience already understands the practical idea.
- Never show a finished Lean example before the audience has seen each piece of syntax that appears in it.
- Each slide should answer one clear question before the next slide begins.
- If a code snippet has more than one unfamiliar idea, split it into multiple slides.

## Beginner Safety Rules

Use these rules when actually making the slides:

- One new syntax form per slide whenever possible.
- If a line of code uses a keyword or symbol that has not appeared before, introduce it first.
- Build larger examples line by line across slides instead of placing the full code at once.
- Say out loud what each symbol means the first time it appears.
- End each slide with one sentence that closes the question raised by that slide.
- If a slide would make a beginner ask "Wait, what is that syntax?", the slide needs to be split.

## Lecturer's Discipline

These are the habits that make the talk feel coherent and rigorous:

- Do not say "Lean can do X" without also saying what idea makes X possible.
- Do not introduce jargon before the audience has seen the underlying phenomenon.
- Do not treat examples as decoration; each example should establish a conceptual move.
- After each major example, ask what information Lean knows statically that an ordinary language would not know.
- Keep contrasting "checked at compile time" with "checked at run time" when relevant.
- Keep contrasting "data construction" with "data elimination" when teaching inductive types and proofs.
- Keep asking whether the current slide makes the core idea of Lean clearer; if it does not, cut or merge it.

## Slide-by-Slide Plan

This structure is intentionally gradual. Each section should feel like it unlocks the next one.

Important note:

- Many of the slides below are best implemented as progressive reveals.
- In the actual deck, 2 or 3 consecutive micro-slides can live inside one visual slide if each reveal only adds one new idea.
- The point is not to maximize slide count. The point is to keep each step cognitively small.

### Part I: Opening and Orientation

Purpose of this part:

- Establish the single goal of the lecture.
- Tell the audience that the later sections are all different views of one core idea.
- Give the audience a motivating problem ladder they can follow for the whole lecture.

### Slide 1: Title and Hook

Title:
`Lean: From Functional Programming to Theorem Proving`

Goal:
Create curiosity before giving definitions.

Talking points:

- Most languages help us write programs.
- Lean also lets us express and check claims about those programs.
- The central question for the talk is: how can one language do both?

Suggested problem ladder for the opening:

- First problem: can the language reject nonsense before running?
- Second problem: can the language catch "almost correct but structurally wrong" programs?
- Third problem: can the language check a precise claim, not just a program shape?

Suggested hook:

> What if the type checker could help with correctness, not just syntax and basic types?

Suggested narration:

"I want to begin with a question, not a definition. We are used to type checkers telling us obvious things: this is a number, that is a string, this function takes two arguments. But there is a ladder here. First, can the language reject nonsense? Next, can it catch programs that are the right kind of thing but the wrong shape? And finally, can it check a claim about a program or a mathematical statement? Lean becomes interesting because it keeps climbing that ladder."

### Slide 2: Roadmap and Promise

Goal:
Tell the audience exactly how the talk will unfold.

Talking points:

- We will move in three steps, but toward one conclusion.
- First: Lean as an ordinary-looking functional language.
- Second: types that can express more detailed information.
- Third: proofs as programs.
- Only after the dependent-type examples land will we zoom out and name the underlying theory.

Message to land:

- Nothing in the second half should appear from nowhere.
- Each idea should grow out of the previous one.
- We are not studying three topics. We are uncovering one idea in three stages.
- The formal story matters, but it should arrive as a summary of the examples rather than as a wall of theory at the start.

Suggested narration:

"This talk is deliberately step by step. We are not going to jump straight into theorem proving. We will first build a comfortable model of Lean as a programming language, then ask how the type system can retain more information, and then see why theorem proving is the logical endpoint of that same design."

### Slide 3: What Is Lean?

Key points:

- Lean is a functional programming language.
- Lean is also an interactive theorem prover.
- The same core language supports both activities.
- There is one shared typed core underneath both activities, and we will name it more formally later.
- It is used for programming, mathematics, and formal verification.

What to emphasize:

- Lean is interesting because the same core language supports all three.
- This is not "first a language, then a separate proof tool."

Suggested narration:

"Lean sits in an unusual place. If you open it for the first time, it looks like a typed functional language. But the farther you go, the more you realize that the type system is doing much more work than in most languages. That is the thread we will follow for the rest of the talk."

### Part II: Lean as a Functional Programming Language

Purpose of this part:

- Show that Lean begins from familiar typed functional programming.
- Build the baseline from which Lean's stronger notion of static information can be understood.
- Make the audience feel the limitation of ordinary types before dependent types appear.
- Seed just enough vocabulary that a short formal lens later will not feel abrupt.

### Slide 4: First Contact, What Does `#check` Do?

Question this slide answers:

> How do we ask Lean what something is?

Only new idea:

- `#check`

Code to show:

```lean
#check 1
#check true
```

What students should know before moving on:

- Lean can tell us the type of an expression.

PL connection:

- `#check` gives the static view of a program.
- It answers: what kind of thing is this expression?

Suggested narration:

"This is the safest possible start. No functions yet, no syntax overload, just the question: if I write an expression, what does Lean think it is? In PL terms, this is the static view. Before we run a program, what can the language already tell us about it?"

### Slide 5: What Does `#eval` Do?

Question this slide answers:

> Can Lean also run code, not just inspect it?

Only new idea:

- `#eval`

Code to show:

```lean
#eval 1 + 2
```

What students should know before moving on:

- Lean is not only a proof system; it can evaluate programs.

PL connection:

- `#eval` gives the dynamic view of a program.
- It answers: what does this expression compute to?

Suggested narration:

"Now we add the second basic interaction. `#check` asks for the static story. `#eval` asks for the dynamic story. That distinction is worth naming, because the whole lecture will keep moving back and forth between what Lean knows before execution and what only appears during execution."

### Slide 6: Explicit Types with `Nat` and `Int`

Question this slide answers:

> Why do we sometimes write a type explicitly?

Only new idea:

- Type ascription with `:`

Code to show:

```lean
#check (1 + 2 : Nat)
#eval (1 - 2 : Int)
```

What students should know before moving on:

- Expressions have types, and we can sometimes write the intended type ourselves.

PL connection:

- A type annotation is a way of making the static contract explicit.

Suggested narration:

"This is a small but important step. The colon syntax lets us say what type we intend. In a PL course I would stress that this is not decorative syntax. It is an explicit statement of the static interface of an expression."

### Slide 7: Naming Values with `def`

Question this slide answers:

> How do we give a name to an expression?

Only new idea:

- `def`

Code to show:

```lean
def hello : String := "Hello"
```

What students should know before moving on:

- `def` introduces a named definition.
- `:=` means "is defined as."

PL connection:

- We have moved from raw expressions to abstraction and naming.

Suggested narration:

"Before we define functions, I would define one ordinary value. That keeps the new syntax small. Conceptually, we are moving from expressions to a program environment where names stand for typed meanings."

### Slide 8: Building the First Function

Question this slide answers:

> How do we define a function of one argument?

Only new idea:

- Parameters in a definition

Code to show:

```lean
def add1 (n : Nat) : Nat := n + 1
```

What students should know before moving on:

- `(n : Nat)` introduces an argument named `n` of type `Nat`.
- The whole definition is still just a `def`.

PL connection:

- A function type is already a simple specification: given this input, return this kind of output.

Suggested narration:

"This is the first full function, so it deserves its own slide. I would point to every piece: name, parameter, return type, body. Then I would make the conceptual point: a function definition is already a tiny contract between input and output."

### Slide 9: From One Argument to Two

Question this slide answers:

> What changes when a function has more than one argument?

Only new idea:

- Multiple parameters

Code to show:

```lean
def addTwo (n : Nat) (k : Nat) : Nat := n + k
```

What students should know before moving on:

- Lean accepts multiple parameter groups.
- The new idea here is only the extra parameter, not control flow.
- Types already act like a simple contract for what a function expects and returns.

Reasoning link:

- We are still in ordinary typed functional programming.
- The next conceptual jump will not be about programming less; it will be about specifying more.

Suggested narration:

"Now that students already understand one-argument functions, the second argument is easy. I would keep the body as simple as possible so the only real new thing on this slide is the idea of having multiple parameters."

### Slide 10: Data Types, `Bool`

Question this slide answers:

> How does Lean define new kinds of data?

Only new idea:

- `inductive`

Code to show:

```lean
inductive Bool where
  | false : Bool
  | true : Bool
```

What students should know before moving on:

- An inductive type lists the possible shapes of data.
- `Bool` has exactly two constructors.

PL connection:

- Inductive types define the formation rules for data.
- They tell us what values of the type can look like.

Suggested narration:

"I would not introduce `Nat` yet. `Bool` is the cleanest example because it has only two cases and no recursion. In PL terms, this slide is about data formation: what are the legal inhabitants of a type?"

### Slide 11: Using a Data Type with `match`

Question this slide answers:

> Once we have a datatype, how do we use it?

Only new idea:

- `match ... with`

Code to show:

```lean
def notBool (b : Bool) : Bool :=
  match b with
  | Bool.false => Bool.true
  | Bool.true => Bool.false
```

What students should know before moving on:

- Pattern matching chooses a result based on which constructor was used.

PL connection:

- Pattern matching is the elimination principle for inductive data.
- Constructors build data; `match` deconstructs it.

Suggested narration:

"This slide exists to isolate pattern matching before recursion appears. Pedagogically, I would say: the previous slide taught us how data is built; this slide teaches us how data is consumed."

### Slide 12: Natural Numbers as Inductive Data

Question this slide answers:

> Can more complicated data also be defined this way?

Only new idea:

- Recursive inductive definitions

Code to show:

```lean
inductive Nat where
  | zero : Nat
  | succ (n : Nat) : Nat
```

What students should know before moving on:

- `Nat` is built from `zero` and repeated `succ`.
- Inductive definitions can be recursive.

PL connection:

- Recursive data gives rise to recursive programs.

Suggested narration:

"Now the audience is ready for recursion in the data itself. They have already seen constructors on `Bool`, so `Nat` now feels like an extension, not a jump. Conceptually, we are moving from finite case analysis to self-similar structure."

### Slide 13: Case Analysis on `Nat`

Question this slide answers:

> How do we inspect a natural number by cases?

Only new idea:

- Pattern matching on recursive data

Code to show:

```lean
def isZero (n : Nat) : Bool :=
  match n with
  | Nat.zero => true
  | Nat.succ _ => false
```

What students should know before moving on:

- Pattern matching works on recursive data too.
- A recursive datatype can still be used in a non-recursive function.
- The result follows the cases of the data.

Reasoning link:

- The structure of the program mirrors the structure of the data.

Suggested narration:

"This slide should not yet introduce self-reference. I would let the audience get comfortable with case analysis on `Nat` before showing actual recursion."

### Slide 14: A Real Recursive Function

Question this slide answers:

> What does recursion look like in Lean?

Only new idea:

- Self-reference in a structurally smaller case

Code to show:

```lean
def double (n : Nat) : Nat :=
  match n with
  | Nat.zero => Nat.zero
  | Nat.succ k => Nat.succ (Nat.succ (double k))
```

What students should know before moving on:

- Lean programs often follow the structure of the data.
- A recursive call is made on a smaller piece of the input.
- Recursion is central and will matter later when proofs use induction.

PL connection:

- Recursion is the computational counterpart to inductive structure.

Suggested narration:

"Only now do I introduce a recursive call. At this point every part of the syntax has already appeared, so the only new idea is the recursive step itself. Later, induction in proofs will feel natural because recursion on data already does."

### Slide 15: Checkpoint 1, What We Know So Far

Question this slide answers:

> What parts of Lean do we already understand before dependent types appear?

Recap points:

- `#check` and `#eval`
- `def`
- simple function definitions
- ordinary function types such as `Nat → Nat`
- inductive data
- pattern matching
- structural recursion

Transition question:

> If types already guide programs this much, can they express richer facts too?

Suggested narration:

"This checkpoint matters because it tells the audience: you already know a meaningful chunk of Lean. Dependent types are not arriving from another planet. They are the next step from what you already understand."

Checkpoint sentence to say explicitly:

"So far, Lean has shown us how to describe computations over well-typed data. The next question is whether the type system can remember more of the program's intended meaning."

Motivating question to ask aloud:

> Suppose two inputs are both lists, but one computation only makes sense when their lengths agree. Can ordinary types express that?

### Slide 16: A Familiar Generic Type

Question this slide answers:

> Before dependent types, how can types already vary with other types?

Only new idea:

- A type constructor

Code to show:

```lean
List : Type → Type
List Nat
List String
```

What students should know before moving on:

- `List` is not yet a concrete collection type by itself.
- `List Nat` and `List String` are different concrete types.
- This is still ordinary typed programming, not dependent types yet.

Reasoning link:

- We have already seen one mild form of dependence: some type expressions take types as input.
- The next question is whether types can also vary with values.

Suggested narration:

"This is a useful bridge slide because it weakens the wall between values and types a little, but not all the way. `List` behaves like a type-level function: give it an element type and you get back a concrete collection type. That idea is still familiar from generics in ordinary languages. The next step is the unusual one: can the type depend on a value, not just another type?"

### Part III: Lean as a Language with Dependent Types

Purpose of this part:

- Show the precise point where Lean goes beyond ordinary typed functional programming.
- Make dependent types feel like the natural answer to a problem, not a magical feature.
- Use a concrete CS problem so the audience feels why extra type information is worth the added complexity.
- After the payoff lands, add one short formal lens so the theory names attach to familiar examples.

### Slide 17: Why Ordinary Types Are Sometimes Too Weak

Goal:
Motivate dependent types before defining them.

Example to discuss:

- A type such as `List α` already varies with a type argument.
- A type like `List α → List β → List (α × β)` does not say whether the two lists have the same length.
- A sorting function type does not, by itself, say the output is a permutation of the input.

Problem framing:

- If two lists have different lengths, what should `zip` do?
- Ignore extra data?
- Crash?
- Return an error?
- Or make mismatched inputs unrepresentable in the first place?

Teaching points:

- Types are not only categories; they can also serve as partial specifications.
- Even in ordinary typed programming, types can already vary with other types.
- The next step is stronger: let types mention values as well.
- The question is whether the type system can express more useful invariants.

Reasoning link:

- Ordinary types often forget relations between values.
- Dependent types are motivated by this loss of information.

Suggested narration:

"This is the moment where the room should start wanting dependent types before I even name them. A type like `List α` is already useful because it remembers the element type. But it still forgets relationships between values, such as whether two lengths agree. Imagine a `zip` function. If the lists have different lengths, what should happen? Ignore data? Raise an error? Return an option? That missing relationship is exactly the kind of thing dependent types are designed to express."

### Slide 18: A Type That Depends on a Value

Question this slide answers:

> What does it mean for a type to depend on a value?

Only new idea:

- A result type that depends on the input

Code to show:

```lean
(b : Bool) → if b then Nat else String
```

What students should know before moving on:

- In Lean, a function's result type can branch on the input value.
- The `if ... then ... else ...` syntax is familiar; the new part is that it is now appearing inside a function type.
- This is a dependent function type: the result type can change with the input value.

Conceptual move:

- Information is now flowing from the term level into the type level.

Suggested narration:

"I would show just the type first, without the full function body. That isolates the real conceptual shock: the output type itself is reacting to the input value. This is the decisive PL move in Lean: values can refine static information."

### Slide 19: Completing the Tiny Dependent Program

Question this slide answers:

> Once the return type depends on the input, how do we write the function?

Only new idea:

- Matching the program branches to the type branches

Code to show:

```lean
def natOrStringThree (b : Bool) : if b then Nat else String :=
  match b with
  | true => (3 : Nat)
  | false => "three"
```

What students should know before moving on:

- The code in each branch must match the more precise type for that branch.

Reasoning link:

- Once the type depends on the value, case analysis refines what Lean knows statically.

Suggested narration:

"Now the earlier slide pays off. The audience has already seen the strange type, so the function no longer feels like too much at once. The key point is that case analysis is no longer only controlling computation. It is also refining the type information available in each branch."

### Slide 20: From Lists to Length-Aware Lists

Question this slide answers:

> What useful fact might we want a collection type to remember?

Only new idea:

- Motivation for indexing by length

Contrast to explain:

- `List α` remembers the element type.
- It does not remember the length.
- `Vect α n` will remember a length as well.
- Sometimes length matters.

What students should know before moving on:

- Vectors are not a random example; they solve a real expressiveness problem.

Reasoning link:

- We are moving from a toy dependent type to a useful invariant.

Suggested narration:

"Before introducing `Vect`, I would explicitly ask what information a normal list forgets. That way the vector type feels motivated instead of decorative."

### Slide 21: Building `Vect` Step by Step

Question this slide answers:

> How does Lean express "a list with length `n`"?

Only new idea:

- An indexed datatype

Build sequence:

1. Show the header:

```lean
inductive Vect (α : Type) : Nat → Type where
```

2. Then add:

```lean
  | nil : Vect α 0
```

3. Then add:

```lean
  | cons : α → Vect α n → Vect α (n + 1)
```

Full code after the reveal:

```lean
inductive Vect (α : Type) : Nat → Type where
  | nil : Vect α 0
  | cons : α → Vect α n → Vect α (n + 1)
```

What students should know before moving on:

- `Vect α n` means elements of type `α` and exactly `n` of them.
- `nil` can only build length `0`.
- `cons` increases the length by `1`.
- Formally, `Vect` is a family of types indexed by a natural number.
- Hide universe parameters on the slide; they are not part of the beginner-level idea.

PL connection:

- An indexed datatype bakes an invariant into the data definition itself.

Suggested narration:

"This slide must be revealed in pieces. If I show the full datatype immediately, beginners will stare at the symbols instead of the idea. The whole point is to let them watch the invariant move into the type, line by line."

### Slide 22: What the Type Checker Learns from `Vect`

Question this slide answers:

> Why is `Vect` better than `List` for some tasks?

Only new idea:

- The type checker can track length

Code to show:

```lean
def Vect.zip : Vect α n → Vect β n → Vect (α × β) n
  | Vect.nil, Vect.nil => Vect.nil
  | Vect.cons x xs, Vect.cons y ys => Vect.cons (x, y) (Vect.zip xs ys)
```

How to present it safely:

- First say that `α × β` means a pair consisting of an `α` and a `β`.
- First remind the audience that both arguments have the same `n`.
- Then reveal the function cases.
- Then say explicitly that the mismatched-length cases are impossible under this type.

What students should know before moving on:

- Dependent types let Lean enforce invariants that are not naturally expressible with ordinary list types.

Reasoning link:

- A run-time check has been replaced by a static guarantee.

This is the primary wow moment:

- Point out that a list-based `zip` would need extra cases for unequal lengths.
- Then point out that `Vect.zip` does not.
- The audience should notice that Lean is not merely checking more code; it is allowing less invalid code to exist.

Suggested narration:

"This slide should answer one sentence clearly: the type checker knows the lengths match. That is the payoff. In a PL lecture I would explicitly say: we have moved one correctness obligation from run time into compile time. Then I would pause and say the important part out loud: the impossible cases are gone. We did not handle them. We eliminated them by changing the type."

Suggested dramatic beat:

- First ask: "Where are the mismatched-length cases?"
- Let the room notice they are missing.
- Then explain that the type already ruled them out.

### Slide 23: Checkpoint 2, What Changed?

Question this slide answers:

> What exactly became more powerful than in ordinary typed programming?

Recap points:

- Types can depend on values.
- That gives the type checker more information.
- More information means stronger compile-time guarantees.
- We have now seen the phenomenon concretely, so this is the right point to give a little formal vocabulary.

Suggested narration:

"Here is the short version. Dependent types mean the type checker knows more. That is the whole bridge to theorem proving."

Checkpoint sentence to say explicitly:

"Once types can express nontrivial invariants about programs, it becomes much less surprising that they can also express logical specifications."

### Slide 24: Formal Lens, What Kind of Dependence Is This?

Question this slide answers:

> How would a PL or type theory course describe the step we just took?

Only new idea:

- A short taxonomy of dependence

Code to show:

```lean
Nat → Nat
List : Type → Type
Vect : Type → Nat → Type
(b : Bool) → if b then Nat else String
```

How to read it aloud:

- `Nat → Nat` is an ordinary function type.
- `List` is a type constructor: give it a type and it returns a type.
- `Vect` is a family of types indexed by a natural number.
- `(b : Bool) → ...` is a dependent function type: the result type varies with the input value.

Optional vocabulary to mention briefly:

- A dependent function type is often called a `Pi`-type.
- You do not need the name for the talk, but it is useful if students read further.

What students should know before moving on:

- Dependent types are not a disconnected trick.
- We have moved through a small ladder: ordinary function types, types built from types, then types that can vary with values.
- That is the formal reason Lean can express stronger invariants.

How to present it safely:

- Keep this slide short.
- Read each line in plain English.
- Do not open a detour into universes or notation beyond what the audience has already seen.

Suggested narration:

"Now that the main example has landed, I would allow myself one minute of formal theory. `List` already acts like a type-level function: give it an element type and it gives you a collection type. `Vect` goes one step further by also taking a length. And the tiny `natOrStringThree` example showed a dependent function type, where the result type changes with the input. So dependent types are not coming from nowhere. They are the next step in a ladder of increasing dependence."

### Part IV: Lean as a Theorem Prover

Purpose of this part:

- Show that theorem proving is not an unrelated extra.
- Present it as the strongest form of the same idea: types carrying rich meaning and programs serving as evidence.
- Shift from CS invariants to mathematical claims without changing the underlying logic of the lecture.
- Make the jump to proofs feel smaller by reusing the same story: a theorem is another type asking for a term.

### Slide 25: Before Proofs, What Is `Prop`?

Question this slide answers:

> Where do theorem statements live in Lean?

Only new idea:

- `Prop`

Code to show:

```lean
#check True
#check False
```

Then explain:

- These are propositions, not boolean values.
- Say out loud that `True` / `False` live in a different part of the language than `true` / `false`.
- Lean has a dedicated category of expressions for propositions, called `Prop`.

What students should know before moving on:

- Theorem statements are expressions in Lean too.
- We are still inside the same language, not switching to an external proof notation.

PL connection:

- Logic is not entering from outside the language; it is being represented inside the type-theoretic framework.

Suggested narration:

"I would not yet say 'proof term' on the first proof slide. First I would establish that propositions are first-class things in Lean and can themselves be checked. The motivating question here is simple: if a machine can check rich program invariants, why can it not also check a precise mathematical claim expressed in the same language?"

### Slide 26: A Theorem Statement Is Also a Type-Like Goal

Question this slide answers:

> What does Lean want from us when we state a theorem?

Only new idea:

- A theorem needs evidence

Code to show:

```lean
theorem keepFirst (p q : Prop) (hp : p) (hq : q) : p := ?
```

How to explain it:

- `p q : Prop` introduces the propositions we are talking about.
- `hp : p` means "assume we have evidence for `p`."
- The goal after the colon is to produce evidence for `p`.

What students should know before moving on:

- The theorem statement behaves like a very strict function signature.

Reasoning link:

- A theorem asks for evidence, not persuasion.
- From the theory side, the theorem statement behaves like a function type from assumptions to conclusion.

Suggested narration:

"I would first show the hole before I show the finished proof. That makes the task visible. The audience should see what Lean is asking for before seeing how we satisfy it. A proof in Lean is not a rhetorical explanation. It is a value of the required type."

### Slide 27: Finishing the Smallest Theorem

Question this slide answers:

> How do we complete a proof when the needed evidence is already available?

Only new idea:

- Return the available evidence

Code to show:

```lean
theorem keepFirst (p q : Prop) (hp : p) (hq : q) : p := hp
```

What students should know before moving on:

- A proof can look just like a program that returns a value of the required type.
- The whole theorem is self-contained on one slide.

PL connection:

- This is the first clean instance of propositions-as-types without using the jargon yet.

Secondary wow point:

- The theorem is almost embarrassingly small.
- That is precisely why it works as a surprise: the audience expects a proof language, but sees a value being returned.

Suggested narration:

"Now the audience sees the simplest complete proof possible. Because the goal was already in the context, the proof is just to return it. That is exactly why people say proofs are programs."

### Slide 28: What Does `p ∧ q` Give Us?

Question this slide answers:

> If we have evidence for `p ∧ q`, what operations are available?

Only new idea:

- Conjunction has constructors and projections

Code to show:

```lean
#check And.intro
#check And.left
#check And.right
```

How to explain it:

- `And.intro` builds evidence for a conjunction.
- `And.left` and `And.right` extract the two parts.
- This is the proof-level version of building and deconstructing data.

What students should know before moving on:

- Larger proofs are assembled from smaller pieces of evidence.

Reasoning link:

- Proof construction mirrors typed program construction.

Suggested narration:

"Before showing a larger theorem, I would first name the proof operations themselves. That keeps the next slide from introducing both a new theorem and a new proof vocabulary at the same time."

### Slide 29: Reordering a Conjunction

Question this slide answers:

> What does a slightly larger proof look like when we assemble it from smaller pieces?

Only new idea:

- Building a compound proof term

Code to show:

```lean
theorem and_commutative (p q : Prop) (hpq : p ∧ q) : q ∧ p :=
  And.intro (And.right hpq) (And.left hpq)
```

What students should know before moving on:

- Proof code can still look like ordinary functional composition.
- The conjunction proof uses the same "build / extract / reassemble" pattern as typed programming.

PL connection:

- Logical connectives behave like structured data with introduction and elimination rules.

Suggested narration:

"This is where I would go very slowly and read it almost like a recipe. We have evidence for `p ∧ q`. Extract the right part. Extract the left part. Reassemble them in the opposite order."

### Slide 30: The Same Proof in Tactic Mode

Question this slide answers:

> Is there a more interactive way to build the same proof?

Only new idea:

- Tactic mode as a practical proof interface

Code to show:

```lean
theorem and_commutative_tactic (p q : Prop) (hpq : p ∧ q) : q ∧ p := by
  apply And.intro
  exact And.right hpq
  exact And.left hpq
```

How to present it safely:

- First remind the audience that this is the same theorem idea as the previous slide.
- Introduce `by` first as "switch into interactive proof mode."
- Then reveal `apply And.intro`.
- Then reveal the two `exact` lines.

What students should know before moving on:

- Tactics are useful because they let Lean guide proof construction step by step.
- Tactic mode is a different interface to the same underlying proof objects.
- This is a practical feature of Lean, not a second logical foundation.

PL connection:

- The theorem being proved has not changed; only the way we construct the proof has changed.

Suggested narration:

"Up to now, we have written proofs as ordinary terms. That is the cleanest way to see the core idea. But in practice, Lean users also rely on tactic mode because it supports a more interactive workflow. The important point is that the logic has not changed. We are building the same proof, just through a different interface."

### Slide 31: Why Induction Belongs in the Same Story

Question this slide answers:

> Why does proof by induction feel natural in Lean?

Only new idea:

- Induction mirrors recursion

What students should know before moving on:

- The same inductive structure that supports recursive programs also supports induction proofs.
- A recursive program on `Nat` and an induction proof on `Nat` have the same overall shape: a base case and a step case.

Conceptual payoff:

- Recursion and induction are two views of the same structural principle.

Suggested way to present it:

- Show a tiny two-column comparison rather than a new full proof script.
- Left column: recursive program on `Nat`
- Right column: induction proof on `Nat`
- Keep the emphasis on structure, not on adding more tactic syntax.

Suggested narration:

"This is the closing loop. We started with inductive data and recursive functions. Induction belongs here because it follows the same structure: one case for zero, one case for successor. That is not a coincidence. It is the design of Lean."

### Part V: Final Synthesis

### Slide 32: The Core Idea of Lean

Takeaways:

1. Lean begins with ordinary typed functional programming.
2. It then weakens the boundary between values and types, so more program meaning can be tracked statically.
3. Theorem proving is the endpoint of that move: a logical specification is represented as a type, and a proof is a program inhabiting it.

What to name here, finally:

- If you want the theory label after the audience has earned it, say that Lean is based on dependent type theory with inductive types.
- If the room is advanced, you can mention `Calculus of Inductive Constructions` here as a label for the foundation, not as a new topic to unpack.
- At this point it is safe to say that the slogan "proofs are programs" is one expression of the Curry-Howard viewpoint.
- Use the slogan only after the audience has already seen concrete proof terms.

Best final sentence:

> The core idea of Lean is not a list of features. It is the unification of programming, typing, and proving in one language.

Suggested narration:

"If the audience remembers one thing, I want it to be this: Lean is not just a bag of advanced features. Its core idea is that programs, types, and proofs live in one system, and that is why the language can express and check so much. Everything else in the talk was there only to make that one idea visible."

Final motivational close:

- Ordinary languages help us run programs.
- Lean is interesting because it tries to narrow the gap between writing a program and justifying that it behaves the way we intend.

## Suggested Live Demo Flow

If you include a live demo, it should still be tightly controlled and spread across the talk rather than appearing as one long block.

Suggested sequence:

1. In the functional programming section:
   Show `#check`, then `#eval`, then `add1`.
2. In the recursion section:
   Show `isZero` before `double`.
3. In the dependent types section:
   Show `List` as the generic bridge, then the dependent return type, then `natOrStringThree`, then `Vect`, then `Vect.zip`, and only then do the short formal zoom-out.
4. In the theorem proving section:
   Show the theorem statement with a hole first, then the tiny finished proof, then the conjunction example, then the tactic version.

Demo rule:

- Never debug live in this talk.
- Never demo installation or project setup.
- Keep the examples small enough that the audience can still see the main idea after one glance.
- Never reveal the final form of a larger example before the audience has seen its pieces.

## What to Skip

Even without a fixed time limit, this talk should still avoid side roads.

- monads
- type classes
- universes in detail
- full CoC / CIC history
- Church encoding detours
- metaprogramming
- automation-heavy tactic scripts
- library ecosystem tours
- advanced equality engineering

## Teaching Notes

- Do not lead with the underlying theory. Show a concrete dependent type first.
- Add one short bridge slide for `List` as an ordinary generic type before dependent types begin.
- After `Vect.zip`, add one short formal zoom-out that names type constructors, indexed families, and dependent function types.
- Use recap slides to slow the pace down on purpose.
- When you introduce a formal phrase, immediately restate it in plain English.
- Prefer one clear running idea over a long list of disconnected examples.
- Keep coming back to the sentence: "the type checker knows more."
- Keep asking: what has become statically knowable that was not statically knowable one section earlier?
- Keep the lecture organized around conceptual relations: formation/elimination, static/dynamic, recursion/induction, runtime check/static guarantee.
- If you mention `Pi` or `Calculus of Inductive Constructions`, do it only after the audience has already seen the examples those names describe.
- If a slide teaches a feature without helping the audience see Lean's core idea more clearly, revise or remove it.

## Delivery Notes

- Speak like you are unfolding an idea layer by layer.
- After each section, say one sentence that closes that section before moving on.
- Ask small rhetorical questions to keep the audience mentally active.
- Pause after the vector example and after the first theorem example.
- If time starts slipping, cut extra commentary before cutting the core examples.

## Optional Opening Question

You can open with:

> What if the type system could do more than reject obvious mistakes? What if it could also track part of a program's logic?

This sets up the move from ordinary functional programming to dependent types and then to proofs.

## Source Basis from the Local Lean Books

This plan is based on the local books in this directory:

- `fp-lean/book/FPLean/GettingToKnow/Types.lean`
- `fp-lean/book/FPLean/GettingToKnow/FunctionsDefinitions.lean`
- `fp-lean/book/FPLean/GettingToKnow/DatatypesPatterns.lean`
- `fp-lean/book/FPLean/DependentTypes.lean`
- `fp-lean/book/FPLean/DependentTypes/IndexedFamilies.lean`
- `fp-lean/book/FPLean/DependentTypes/Summary.lean`
- `fp-lean/book/FPLean/TacticsInductionProofs.lean`
- `theorem_proving_in_lean4/book/TPiL/Intro.lean`
- `theorem_proving_in_lean4/book/TPiL/DependentTypeTheory.lean`
- `theorem_proving_in_lean4/book/TPiL/PropositionsAndProofs.lean`
- `theorem_proving_in_lean4/book/TPiL/Tactics.lean`
