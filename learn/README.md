# Python revision pages

Five interactive pages built as a learn-then-drill shelf. Source is here; the
published, shareable versions are linked below.

| Page | What it's for | Live |
|---|---|---|
| `four-boxes.html` | list / tuple / dict / set, explained | https://claude.ai/code/artifact/b42031ed-1c95-44b1-823b-09ae36cd72c2 |
| `set-or-regret.html` | those four, drilled under a timer | https://claude.ai/code/artifact/6f976c55-1230-45fb-bc09-e445b78fcb75 |
| `day-one-explained.html` | the rest of Day 1, explained | https://claude.ai/code/artifact/64f95123-a9ed-4a95-9c5e-3a84b1b73646 |
| `reload-arcade.html` | all of Day 1, drilled + interview lines | https://claude.ai/code/artifact/1c759e0a-4535-4fb9-a223-2dbd0ad42765 |
| `eight-techniques.html` | the 8 patterns, with steppable traces | https://claude.ai/code/artifact/558e35f2-a737-4fa4-9a01-b986ceef0816 |

Read order: **Four Boxes → Set or Regret → Day One, Explained → Reload Arcade**
for the language, then **Eight Techniques** for problem-solving.

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
