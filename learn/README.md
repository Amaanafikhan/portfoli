# Python revision pages

Eight interactive pages built as a learn-then-drill shelf. Source is here; the
published, shareable versions are linked below.

| Page | What it's for | Live |
|---|---|---|
| `four-boxes.html` | list / tuple / dict / set, explained | https://claude.ai/code/artifact/b42031ed-1c95-44b1-823b-09ae36cd72c2 |
| `set-or-regret.html` | those four, drilled under a timer | https://claude.ai/code/artifact/6f976c55-1230-45fb-bc09-e445b78fcb75 |
| `day-one-explained.html` | the rest of Day 1, explained | https://claude.ai/code/artifact/64f95123-a9ed-4a95-9c5e-3a84b1b73646 |
| `reload-arcade.html` | all of Day 1, drilled + interview lines | https://claude.ai/code/artifact/1c759e0a-4535-4fb9-a223-2dbd0ad42765 |
| `eight-techniques.html` | the 8 patterns, with steppable traces | https://claude.ai/code/artifact/558e35f2-a737-4fa4-9a01-b986ceef0816 |
| `the-plumbing.html` | taking input, returning answers, looping through data | https://claude.ai/code/artifact/eb421301-3ce0-47f3-bab6-01509dbe20f8 |
| `fifteen-pictures.html` | the same 15 ideas as pictures, with spaced repetition | https://claude.ai/code/artifact/216eed8b-f415-431e-b198-b7f131a92606 |
| `type-it-out.html` | **22 exercises you type and run** — real Python in the page | https://claude.ai/code/artifact/dcdf9c06-3259-4d8c-a959-6e2ecc11c67d |

Read order: **Four Boxes → Set or Regret → Day One, Explained → Reload Arcade**
for the language, then **The Plumbing** (how data gets in and answers get out),
then **Type It Out** (write code, don't read it), then **Eight Techniques**
for problem-solving.

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

- Day 1 only (environment, data structures, functions, errors & files).
- Day 2 material (type hints, OOP, decorators, modules) is **not** included.
- No FastAPI / Pydantic / SQLAlchemy content anywhere, by request.

## Where this left off

In `eight-techniques.html`, six of the fifteen problems have full working
implementations with recorded step-by-step traces — all verified to produce
correct output:

| # | Problem | Verified |
|---|---|---|
| 1 | Reverse in place | `ABCDE` → `EDCBA` |
| 3 | Longest substring, no repeats | `"abcabb"` → `3` |
| 11 | Two Sum | `[2,7,11,15]`, target 9 → `[0,1]` |
| 12 | Maximum subarray (Kadane) | `[-2,1,-3,4,-1,2,-5,4]` → `5` |
| 13 | Merge sorted arrays | → `[1,2,3,4,5,6]` |
| 14 | Move zeroes | `[0,1,0,3,12]` → `[1,3,12,0,0]` |

The other nine have a technique label and a one-line trick in the §04 index,
but **no implementation**: #2 palindrome, #4 valid anagram, #5 group anagrams,
#6 FizzBuzz, #7 primes and the sieve, #8 reverse an integer, #9 Fibonacci three
ways, #10 count set bits, #15 missing number.

### Next step, agreed but not started

Add traces for the four with real mechanics worth watching — **#9** Fibonacci
(recursion vs memo vs iteration, showing the call tree explode), **#10** count
set bits (bits vanishing as `n &= n - 1` runs), **#15** missing number (XOR
pairs cancelling), **#5** group anagrams (the canonical key forming) — and give
the remaining five a full worked solution with edge cases, as a plain code block.

Also open: a drill companion for `eight-techniques.html` — timed rounds on
"name the technique from the question" and "which loop does this need", to match
what the Arcade does for Day 1.

## Editing these

Each file is self-contained: one `<title>`, one `<style>`, the markup, one
`<script>`. No build step and no dependencies — open a file in a browser to see
changes. They were authored for an artifact wrapper, so they start at `<title>`
rather than `<!doctype html>`; browsers render them fine as-is.

To republish an updated page to the same URL, hand the file and its artifact URL
back to Claude Code in a session.
