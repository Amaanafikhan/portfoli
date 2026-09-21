# Python revision pages

Fourteen interactive pages built as a learn-then-drill shelf. Source is here; the
published, shareable versions are linked below.

| Page | What it's for | Live |
|---|---|---|
| `every-oop-answer.html` | **the 12 OOP concepts + 69 interview questions**, with a scored drill | https://claude.ai/artifact/1TYw9pdQwCvpqAvK1ptRgj |
| `read-it-first.html` | **why each OOP keyword exists** (without-it vs with-it) + how to *read* code | https://claude.ai/artifact/9daLxZmWSiHHB8c6bj6L67 |
| `five-moves.html` | **where to start on a blank page** — the five moves every function is made of | https://claude.ai/artifact/W9m1jNiqszJaPeKqvap3bh |
| `oop-picture-book.html` | **OOP as nine animated images** — 4 pillars, 5 types of inheritance, every keyword | https://claude.ai/artifact/KohX1ZeUiBSaMnB2zB7kMN |
| `four-boxes.html` | list / tuple / dict / set, explained | https://claude.ai/code/artifact/b42031ed-1c95-44b1-823b-09ae36cd72c2 |
| `set-or-regret.html` | those four, drilled under a timer | https://claude.ai/code/artifact/6f976c55-1230-45fb-bc09-e445b78fcb75 |
| `day-one-explained.html` | the rest of Day 1, explained | https://claude.ai/code/artifact/64f95123-a9ed-4a95-9c5e-3a84b1b73646 |
| `reload-arcade.html` | all of Day 1, drilled + interview lines | https://claude.ai/code/artifact/1c759e0a-4535-4fb9-a223-2dbd0ad42765 |
| `eight-techniques.html` | the 8 patterns — **all 15 problems, each a steppable trace** | https://claude.ai/artifact/BZkrJF7UaTcjSAkB9kv95P |
| `the-plumbing.html` | taking input, returning answers, looping through data | https://claude.ai/code/artifact/eb421301-3ce0-47f3-bab6-01509dbe20f8 |
| `fifteen-pictures.html` | the same 15 ideas as pictures, with spaced repetition | https://claude.ai/code/artifact/216eed8b-f415-431e-b198-b7f131a92606 |
| `type-it-out.html` | **22 exercises you type and run** — real Python in the page | https://claude.ai/code/artifact/dcdf9c06-3259-4d8c-a959-6e2ecc11c67d |
| `fizzbuzz-order.html` | drag-the-rules game for the FizzBuzz condition-order trap | https://claude.ai/code/artifact/40d8012b-c751-4fb3-8916-15f75b83194d |
| `django-machine.html` | Django's request/response cycle, animated, + the `urls.py` order trap | https://claude.ai/artifact/C4Mzd21FUeV37akBdPdjjq |

Read order: start at **The Five Moves** (what to type first, on any problem),
then **Four Boxes → Set or Regret → Day One, Explained → Reload Arcade**
for the language, then **The Plumbing** (how data gets in and answers get out),
then **Type It Out** (write code, don't read it), then **Eight Techniques**
for problem-solving. **The Django Machine** is separate — it's for web work,
not for the Python fundamentals.

`five-moves.html` is the answer to "where do I start?". It names the fixed
order every function is written in — door (`def`), box (the accumulator),
walk (the loop), work (the one-item logic), hand back (`return`, at the outer
indent) — then makes you build three functions line by line, picking each move
from three candidates. Wrong picks aren't punished, they're explained with the
actual error Python raises. Covers the three accumulator shapes: a number
(`0`), a list (`[]`), a dict (`{}`). Ends with the indent trap (`return`
inside vs after the loop, both run for real, 3 vs 10) and an eight-question
"name the box" drill.

Verification: all three reference solutions and both indent-trap variants were
run on **real CPython** and then through **Skulpt with the page's exact
harness** — 5/5 match on both. The assembled code was checked to be byte-identical
to the code that actually runs. Every error message quoted in a wrong-answer
explanation was produced by running that wrong code; four claims were corrected
as a result (`UnboundLocalError` not `NameError` for a missing accumulator;
`'int' object is not iterable` for `list += int`; `[0, 2]` not `[1, 3]` for the
`range(len(...))` mistake; and Python's actual `=` vs `==` hint text).

`every-oop-answer.html` is the straight syllabus, built when the learner asked
for the OOP concepts taught properly before anything advanced. Twelve concepts
in teaching order — what OOP is, class and object, `__init__`/`self`, instance
vs class attributes, the three method types, encapsulation and access
modifiers, abstraction, inheritance with all five types plus `super()` and the
MRO, polymorphism and duck typing, magic methods and operator overloading,
composition vs aggregation vs association, and identity vs equality. Each gets
one sentence to say out loud, verified code, and its interview questions
inline. **69 questions**, then the whole bank as a shuffled drill that
self-grades and reports which concepts were weakest.

Two things it deliberately gets right where most sources do not. It does **not**
repeat the `1000 is 1000` myth: running it showed `True`, because equal
constants in one code block get folded, so the page says the answer depends on
how the code is compiled and to never use `is` for values. And it answers the
diamond question with the part usually left out — with cooperative `super()`,
`A.__init__` runs **once**, not twice.

Verification: every code block and error message was run on real Python first.
The page was then driven in headless Chromium — 12 topics, 12 code blocks, all
table-of-contents anchors resolve, all 69 answers are substantial, and the
complete drill was played to the summary screen. That caught a real bug: "just
the ones I missed" was keyed by topic rather than by question, so missing 23
offered 59 back. It now returns exactly the 23.

`read-it-first.html` came from the most useful thing the learner said: *"I am
not understanding the code structure."* Writing was being taught on top of a
reading skill that was never taught. Two halves:

**Ten watch-it-break players — one per rung of the OOP ladder.** Not a toggle
between two code blocks: a stepper that runs the code, with value cells that
change underneath it, so the bug *happens* instead of being described. You
step the broken version until the wrong value appears in red, then the same
steps with the keyword, going green. A keyword only sticks once you have felt
the problem it removes, so the prose was cut to one line each and folded away
under the player. The two strongest: **rung 6** steps the radius from 2 to 10 and the area sits
frozen at `12.56636` when it should be `314.159` — you watch a number refuse
to move. **Rung 4** finds a bug in a copy-pasted `deposit`, fixes the parent,
and shows the child still broken: parent `100`, child `50`. Both numbers came
from running it. Also: `ElectricCar` inheriting `refuel()`, a forgotten
`area()` returning `None` and blowing up 200 lines away, and a flipped `5/9`
giving `122.4` instead of `37.8`.

**How to read a block of code.** The one rule — every line belongs to the
nearest line above it that is less indented — as a tap-a-line explorer that
marks the owner and the owned. A three-pass reader that reveals code by indent
depth instead of by line. "Anatomy of a line", tapping the parts of
`self.balance += amount`. And the game: **which lines actually run?** — tap the
lines whose body does work, in order, over three rounds.

The game's execution orders are not hand-reasoned: they were recorded with a
real Python line tracer (`sys.settrace`). Round 2 is the learner's own
recurring bug — `return` indented under the `for` — and tapping through it
makes the function stop on the first item in front of them, output `3` not `10`.

Verification: every before/after output was produced by running the code. The
finished page was then driven in headless Chromium — all 10 players step through
their 55 frames with exactly one pane visible, exactly one highlighted code
line and values actually changing on every step, the explorer resolves ownership correctly (tapping `return total` marks
the `for` as its owner), the three-pass reader reveals 3 → 6 → 12 → 16 lines,
all three game rounds were played to completion, a wrong tap was confirmed to
explain itself, and there is no horizontal scroll at 420px.

`oop-picture-book.html` exists because reading OOP never stuck — it gives every
concept **one image and one sentence** so it can be recalled under pressure, not
just recognised. Nine stepped animations: the stamp and the prints (class vs
object), the hidden first seat (`self`), one whiteboard vs a notebook each (the
shared-mutable-class-attribute bug), the staircase (`super()`), five family
shapes (the five types of inheritance), the universal remote (polymorphism /
duck typing), the card that covers the card (Python has **no** method
overloading), the glass and the buttons (encapsulation vs abstraction), and the
wall that's really a door (`@property`). Plus the class skeleton — Name, Birth,
State, Show, Do — an 18-row keyword dictionary, and a picture-to-sentence recall
drill.

Scope was set by searching what is actually asked rather than guessing: "types
of OOPs" in these interviews means **two** lists — the four pillars *and* the
five types of inheritance — and overloading-vs-overriding is a trap for anyone
who learned OOP from Java. Both are given dedicated sections.

Verification: every code block and every quoted error message was produced by
running the code on real CPython first — including `TypeError: Calc.add()
missing 1 required positional argument: 'c'`, the `_Acct__hard` name-mangling
result, `D.__mro__`, and the abstract-class `TypeError`. The rendered page was
then stepped through in jsdom: 10/10 animations mount, every frame has a
caption, and all five inheritance diagrams toggle correctly.

`fizzbuzz-order.html` is a focused companion to Type It Out's FizzBuzz
exercise: drag Fizz/Buzz/FizzBuzz into any order and watch a live 1-15 belt
show which numbers break, then a second Skulpt editor to write and run the
real thing with line-15-aware diagnosis. Verified: all four rule orderings
checked programmatically (any order with the both-check last fails only at
15; first, always correct), and both a correct and a deliberately
wrong-order Python solution run through Skulpt to confirm the diagnosis
text matches reality.

`type-it-out.html` runs real Python in the browser via Skulpt (loaded from
jsDelivr; no server). 22 exercises in 5 stages, from `print(8)` up to
two-pointer reversal and FizzBuzz. It checks output, diagnoses failures with
targeted hints, and asks an interview question on each pass.

Verification: every exercise's expected output was produced by running its
reference solution on **real CPython**, then all 22 reference solutions were
re-run through **Skulpt with the page's exact harness** — 22/22 match. The
hint engine was tested against 12 realistic wrong answers; all 12 produced a
correct, specific diagnosis. Skulpt's `execLimit` turns infinite loops into a
TimeLimitError instead of a frozen page.

Known Skulpt gap: `{**a, **b}` dict merging errors out, so it is kept out of
the exercises.

`fifteen-pictures.html` is the memory layer for The Plumbing: one diagram per
idea instead of a paragraph, recall-first (you answer, then reveal), 63
alternative wordings so a reworded question still lands, and Leitner spacing
(1 / 3 / 7 / 21 / 60 days) held in localStorage. Open it daily, not once.

`the-plumbing.html` covers every way to take input (parameters, hardcoded,
`input()`, `split()`, multi-line, files), every form of `return` — including the
`return` vs `print` side-by-side runner — and nine data shapes with the right
loop for each. Every Python claim and error message in it was verified against a
real interpreter.

## Scope

- Day 1 (environment, data structures, functions, errors & files) across the
  original nine pages.
- **OOP was added later**, on request, once Day 1 was solid — it lives in
  `oop-picture-book.html` only. The Day 1 pages stay Day 1.
- Still not included: type hints, decorators beyond `@property` /
  `@classmethod` / `@staticmethod` / `@dataclass`, modules and packaging.
- No FastAPI / Pydantic / SQLAlchemy content anywhere, by request.

## Where this left off

Nothing outstanding. `eight-techniques.html` now has a steppable trace for
**all fifteen** problems, in problem order, so §04 doubles as a table of
contents:

| # | Problem | Technique shown | Verified |
|---|---|---|---|
| 1 | Reverse in place | two pointers | `ABCDE` → `EDCBA` |
| 2 | Valid palindrome | two pointers, skipping junk | `"Ab, Ba"` → `True` |
| 3 | Longest substring, no repeats | sliding window | `"abcabb"` → `3` |
| 4 | Valid anagram | count up, then count down | `listen`/`silent` → `True` |
| 5 | Group anagrams | canonical form as key | 3 buckets from 6 words |
| 6 | FizzBuzz | condition order | 15 slots, `FizzBuzz` last |
| 7 | Primes up to N | the sieve, and the √n bound | → `2,3,5,7,11,13,17,19` |
| 8 | Reverse an integer | `% 10` peel, `// 10` drop | `1234` → `4321` |
| 9 | Fibonacci | running state / DP collapse | `fib(10)` → `55` |
| 10 | Count set bits | `n &= n - 1` | `13` → `3` |
| 11 | Two Sum | hash map | `[2,7,11,15]`, 9 → `[0,1]` |
| 12 | Maximum subarray | Kadane | `[-2,1,-3,4,-1,2,-5,4]` → `5` |
| 13 | Merge sorted arrays | merge step, filled backwards | → `[1,2,3,4,5,6]` |
| 14 | Move zeroes | read / write pointers | `[0,1,0,3,12]` → `[1,3,12,0,0]` |
| 15 | Missing number | XOR pairs cancel | `[3,0,1]` → `2` |

Verification for the nine added: each reference implementation was run on
**real CPython** to fix the expected result, the JS trace builders re-run the
same algorithm to record every frame, and the two were compared
programmatically — 10/10 match, including full intermediate sequences for the
sieve, FizzBuzz and the Fibonacci table. The whole page was then rendered in
**jsdom** and every tracer stepped through every frame: 15/15 mount, no blank
notes, exactly one highlighted code line per frame, cells present throughout.

### Still open, offered but not started

A drill companion for `eight-techniques.html` — timed rounds on "name the
technique from the question" and "which loop does this need", to match what the
Arcade does for Day 1.

## Editing these

Each file is self-contained: one `<title>`, one `<style>`, the markup, one
`<script>`. No build step and no dependencies — open a file in a browser to see
changes. They were authored for an artifact wrapper, so they start at `<title>`
rather than `<!doctype html>`; browsers render them fine as-is.

To republish an updated page to the same URL, hand the file and its artifact URL
back to Claude Code in a session.
