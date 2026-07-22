# Insecure examples (for Lab 4, Step 6)

These are **deliberately vulnerable** snippets used to see the security gate react to a
bad change. They are stored as `.cs.txt` so they are **not** compiled into the app or
scanned on `main` — you copy one into real code inside a pull request, then replace it
with the fixed version.

- `CommandInjectionExample.cs.txt` — an endpoint that passes user input into a shell
  (a command-injection pattern), plus a fixed version that uses no shell and validates
  input.

## Note on CodeQL coverage

Whether CodeQL flags a given snippet depends on its current C# models and your setup:

- Use **CodeQL Default setup** (Lab 4, Step 1) for the best coverage, or — if you use the
  workflow form — request the **`security-extended`** query suite and analyze `main` on
  `push` so there is a baseline to diff against.
- On a **minimal-API** app like ShipIt, some taint sources are not modeled out of the box,
  so a given example may not always be flagged. That is itself the lesson: a scanner is
  one layer of **defense in depth**, not a guarantee. The gate that *blocks* a dangerous
  change is proven regardless (see the failing-test gate in Lab 2 and push protection in
  Lab 4, Step 5).

Do not ship any of this in a real service.
